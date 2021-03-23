---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO ThreadX
description: Ten rozdział zawiera wprowadzenie do usługi Azure RTO ThreadX oraz opis jej aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83718ddf5469238e2429855908be2ea5d405f874
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822483"
---
# <a name="chapter-1---introduction-to-azure-rtos-threadx"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO ThreadX

Azure RTO ThreadX to jądro w czasie rzeczywistym o wysokiej wydajności zaprojektowane specjalnie dla aplikacji osadzonych. Ten rozdział zawiera wprowadzenie do produktu oraz opis jego aplikacji i korzyści.

## <a name="threadx-unique-features"></a>ThreadX unikatowe funkcje

W przeciwieństwie do innych jądra w czasie rzeczywistym, ThreadX został zaprojektowany jako uniwersalny — można łatwo skalować między aplikacjami opartymi na mikrokontrolerach, korzystając z zaawansowanych procesorów CISC, RISC i DSP.

ThreadX jest skalowalna w oparciu o jego podstawową architekturę. Ponieważ usługi ThreadX są implementowane jako biblioteka C, tylko te usługi, które są używane przez aplikację, są umieszczane w obrazie w czasie wykonywania. W związku z tym rzeczywisty rozmiar ThreadX jest całkowicie określony przez aplikację. W przypadku większości aplikacji obraz instrukcji ThreadX mieści się w zakresie od 2 KB do 15 kilobajtów.

### <a name="picokerneltrade-architecture"></a>*&trade;Architektura picokernel*

Zamiast nakładania się warstwowych funkcji jądra na siebie, takich jak tradycyjne architektury *mikrojądra* , usługa ThreadX Services bezpośrednio do jej rdzenia. Powoduje to najszybsze możliwe przełączenie kontekstu i wydajność wywołania usługi. Nazywamy ten projekt nieoparty na warstwach *picokernel* architekturę.

### <a name="ansi-c-source-code"></a>Kod źródłowy ANSI C

ThreadX jest zapisywana głównie w standardzie ANSI C. Do dostosowywania jądra do bazowego procesora docelowego potrzeba niewielkiej ilości języka asemblera. Dzięki temu projektowi można przenieść ThreadX do nowej rodziny procesorów w bardzo krótkim czasie — zwykle w ciągu kilku tygodni.

### <a name="advanced-technology"></a>Technologia zaawansowana

Poniżej przedstawiono najważniejsze informacje o technologii ThreadX Advanced.
- Prosta architektura *picokernel*
- Skalowanie automatyczne (małe rozmiary)
- Deterministyczne przetwarzanie
- Szybka wydajność w czasie rzeczywistym
- Planowanie zastępujące i wspólne
- Elastyczna obsługa priorytetów wątków
- Tworzenie dynamicznego obiektu systemowego
- Nieograniczona liczba obiektów systemowych
- Zoptymalizowana obsługa przerwań
- Zastępujący — próg&trade;
- Dziedziczenie priorytetów
- Łańcuch zdarzeń&trade;
- Szybkie czasomierze oprogramowania
- Zarządzanie pamięcią w czasie wykonywania
- Monitorowanie wydajności w czasie wykonywania
- Analiza stosu czasu wykonywania
- Wbudowane śledzenie systemu
- Ogromne wsparcie dla procesorów
- Obsługa ogromnych narzędzi programistycznych
- Całkowicie endian neutral

### <a name="not-a-black-box"></a>To nie jest czarne pole

Większość rozkładów ThreadX obejmuje kompletny kod źródłowy C, a także język zestawu specyficzny dla procesora. Eliminuje to problemy "z czarnym pudełkem" występujące z wieloma jądrami komercyjnymi. Dzięki ThreadX, deweloperzy aplikacji mogą zobaczyć dokładnie, co robi jądro — nie ma Mysteries!

Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, korzystne jest, aby mieć możliwość modyfikacji jądra, jeśli jest to absolutnie wymagane.

Te funkcje są szczególnie wygodne dla deweloperów przyzwyczajonych do pracy z własnymi *jądrami* wewnętrznymi. Oczekują one, że kod źródłowy i możliwość modyfikowania jądra. ThreadX to Ultimate jądro dla deweloperów.

### <a name="the-rtos-standard"></a>Standard RTO

Ze względu na uniwersalność, wysoką wydajną architekturę *picokernel* , zaawansowaną technologię i zapewnianie przenośności, ThreadX jest wdrażany na ponad 2 000 000 000 urządzeniach. Dzięki temu ThreadX Standard RTO dla głęboko osadzonych aplikacji.

## <a name="safety-certifications"></a>Certyfikaty bezpieczeństwa

### <a name="tv-certification"></a>Certyfikat TÜV

ThreadX został certyfikowany przez moimi-TÜV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC61508 i IEC-62304. Certyfikat potwierdza, że ThreadX może być używany w rozwoju oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności bezpieczeństwa Międzynarodowa Komisja Elektrotechniczna (IEC) 61508 i IEC 62304 dla "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem". MOIMI-TÜV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGSGroup i TÜV Saarland, stał się wiodącą, niezależną firmą do testowania, inspekcji, sprawdzania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które są od niego pochodzące, w tym IEC 62304, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych i systemów kontroli szynowej.

MOIMI-TÜV Saar ma certyfikowane ThreadX do użycia w systemach samochodowych o krytycznym znaczeniu dla bezpieczeństwa, zgodnie ze standardem ISO 26262. Ponadto ThreadX jest certyfikowany na poziomie integralności infrastruktury bezpieczeństwa motoryzacyjnego (ASIL), który reprezentuje najwyższy poziom certyfikacji ISO 26262.

Dodatkowo moimi-TÜV Saar ma certyfikowane ThreadX, które mają być używane w kluczowych dla bezpieczeństwa aplikacjach szynowych, ze względu na Standard 50128 do SW-SIL 4.

![Certyfikat TÜV](./media/overview-threadx/partener-logo-sgs-tuv-saar-2.png)

* IEC 61508 do SIL 4

* IEC 62304 do klasy bezpieczeństwa oprogramowania SW (C)

* ISO 26262 ASIL D

* EN 50128 SW — SIL 4

> [!NOTE]
> *Skontaktuj się z nami, aby uzyskać więcej informacji na temat wersji ThreadX certyfikowanych przez TÜV lub do dostępności raportów testowych, certyfikatów i powiązanej dokumentacji.*

### <a name="misra-c-compliant"></a>Zgodne z MISRA C

MISRA C to zestaw wytycznych programistycznych dotyczących krytycznych systemów przy użyciu języka programowania C. Oryginalne wytyczne dotyczące języka MISRA C były głównie przeznaczone do aplikacji motoryzacyjnych; jednak MISRA C jest teraz szeroko uznawany za mające zastosowanie do wszystkich aplikacji o krytycznym znaczeniu dla bezpieczeństwa. ThreadX jest zgodna ze wszystkimi regułami "Required" i "obowiązkowy" w przypadku MISRA-C:2004 i MISRA C:2012. ThreadX jest również zgodna ze wszystkimi regułami "doradczym". Aby uzyskać więcej informacji, zapoznaj się z dokumentem ***ThreadX_MISRA_Compliance.pdf*** .

### <a name="ul-certification"></a>Certyfikat UL

ThreadX został certyfikowany przez UL w celu zapewnienia zgodności z metodą UL 60730-1 w załączniku H, CSA E60730-1 załącznik H, IEC 60730-1 w załączniku H, UL 60335-1 Załącznik R, IEC 60335-1 w załączniku R, 1998 a w przypadku oprogramowania w składnikach programowalnych. Wraz z IEC/UL 60730-1, które mają wymagania dotyczące "kontrolek wykorzystujących oprogramowanie" w załączniku H, standard IEC 60335-1 opisuje wymagania dotyczące "programowalnych obwodów elektronicznych" w załączniku R. IEC 60730 załącznik H i IEC 60335-1 Załącznik R dotyczy bezpieczeństwa sprzętu i oprogramowania używanego w urządzeniach, takich jak pralki, zmywarki, Dryers, chłodziarks, zamrażarki i Piece.

![Certyfikat UL](./media/overview-threadx/partener-logo-c-ru-us-2.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!NOTE]
> *Skontaktuj się z firmą Microsoft, aby uzyskać więcej informacji na temat wersji ThreadXch certyfikowanych przez TÜV lub do dostępności raportów testowych, certyfikatów i powiązanej dokumentacji.*

### <a name="certification-pack"></a>Pakiet certyfikacji

Pakiet certyfikacji ThreadX &trade; to 100% całości, gotowe, specyficzny dla branży pakiet autonomiczny, który zapewnia wszystkie dowody ThreadX wymagane do certyfikowania lub pomyślnego przesłania produktu opartego na ThreadX do najwyższej niezawodności i poziomu krytycznego wymaganych dla lotnictwa krytycznego, medycznego i przemysłowego. Obsługiwane certyfikaty obejmują DO-178B, ED-12B, DO-278, FDA510 (k), IEC62304, IEC-60601, ISO-14971, UL-1998, IEC-61508, CENELEC EN50128, BS50128 i 49CFR236. Aby uzyskać więcej informacji na temat pakietu certyfikacji, skontaktuj się z firmą Microsoft.

## <a name="embedded-applications"></a>Aplikacje osadzone

Aplikacje osadzone są wykonywane na mikroprocesorach, które są objęte produktami, takimi jak urządzenia komunikacyjne sieci bezprzewodowej, aparaty samochodów, drukarki laserowe, urządzenia medyczne itp. Innym rozróżnieniem aplikacji osadzonych jest to, że oprogramowanie i sprzęt mają dedykowany cel.

### <a name="real-time-software"></a>Oprogramowanie w czasie rzeczywistym

Po nałożeniu ograniczeń czasowych na oprogramowanie aplikacji jest ono nazywane oprogramowaniem w *czasie rzeczywistym* . Aplikacje osadzone są prawie zawsze w czasie rzeczywistym ze względu na ich nieodłączną interakcję ze zdarzeniami zewnętrznymi.

### <a name="multitasking"></a>Wielozadaniowość

Jak wspomniano, aplikacje osadzone mają dedykowany cel. Aby zrealizować ten cel, oprogramowanie musi wykonać rozmaite *zadania*. Zadanie to częściowo niezależna część aplikacji, która wykonuje określone cło. Jest to również sytuacja, w której niektóre zadania są ważniejsze niż inne. Jednym z głównych trudności w aplikacji osadzonej jest alokacja procesora między różnymi zadaniami aplikacji. Ta alokacja przetwarzania między zadaniami konkurującymi jest głównym celem ThreadX.

### <a name="tasks-vs-threads"></a>Zadania a wątki

Inną rozróżnienie zadań polega na tym, że termin *zadanie* jest używany na wiele sposobów. Czasami oznacza to, że program może być ładowany osobno. W innych przypadkach może odnosić się do wewnętrznego segmentu programu. W związku z tym w współczesnych systemach operacyjnych istnieją dwa warunki, które nie zastąpią użycia zadania: *proces* i *wątek*. *Proces* jest całkowicie niezależnym programem, który ma własną przestrzeń adresową, a *wątek* jest segmentem programu niezależnym, który jest wykonywany w ramach procesu. Wątki współużytkują tę samą przestrzeń adresową procesu. Obciążenie związane z zarządzaniem wątkami jest minimalne.

Większość aplikacji osadzonych nie może zapewnić obciążenia (zarówno pamięci, jak i wydajności) związanego z pełnym rozwiniętą systemem operacyjnym opartym na procesie. Ponadto mniejsze mikroprocesory nie mają architektury sprzętu do obsługi prawdziwego systemu operacyjnego zorientowanego na procesy. Z tego względu ThreadX implementuje model wątku, który jest zarówno niezwykle wydajny, jak i praktyczny w przypadku większości aplikacji osadzonych w czasie rzeczywistym.

Aby uniknąć nieporozumień, ThreadX nie używa *zadania* warunkowego. Zamiast tego jest używany bardziej opisowy i współczesny *wątek* nazw.

## <a name="threadx-benefits"></a>Korzyści z ThreadX

Korzystanie z usługi ThreadX zapewnia wiele korzyści dla aplikacji osadzonych. Oczywiście podstawową korzyścią jest zapełnienie czasu przetwarzania wątków aplikacji osadzonych.

### <a name="improved-responsiveness"></a>Zwiększona czas odpowiedzi

Przed jądrami w czasie rzeczywistym, takimi jak ThreadX, większość osadzonych aplikacji przydzieliła czas przetwarzania z prostą pętlą kontroli, zazwyczaj z poziomu *głównej* funkcji języka C. To podejście jest nadal używane w bardzo małych lub prostych aplikacjach. Jednak w dużych lub złożonych aplikacjach nie jest to praktyczne, ponieważ czas odpowiedzi dla każdego zdarzenia jest funkcją czasu przetwarzania w przypadku najgorszego przechodzenia przez pętlę kontroli. 

W kwestiach niepotrzebnych, charakterystyk chronometrażu aplikacji jest zmieniana za każdym razem, gdy wprowadzane są modyfikacje w pętli kontroli. Sprawia to, że aplikacja jest niestabilna i trudno ją obsługiwać i ulepszać.

ThreadX zapewnia szybkie i deterministyczne czasy odpowiedzi na ważne zdarzenia zewnętrzne. ThreadX wykonuje tę procedurę za pośrednictwem jego przechodzenia, opartego na priorytetach algorytmem planowania, który pozwala na przechodzenie przez wątek o wyższym priorytecie o niższym priorytecie. W efekcie czas odpowiedzi na najgorszy przypadek zbliża się do czasu wymaganego do wykonania przełączenia kontekstu. Jest to nie tylko deterministyczne, ale jest również niezwykle szybka.

### <a name="software-maintenance"></a>Konserwacja oprogramowania

Jądro ThreadX umożliwia deweloperom aplikacji skoncentrowanie się na określonych wymaganiach ich wątków aplikacji bez konieczności zajmowania się zmianami chronometrażu innych obszarów aplikacji. Ta funkcja znacznie ułatwia naprawianie lub ulepszanie aplikacji wykorzystującej ThreadX.

### <a name="increased-throughput"></a>Zwiększona przepływność

Możliwe jest obejście problemu dotyczącego czasu odpowiedzi pętli kontroli w celu dodania większej liczby sondowań. Pozwala to zwiększyć czas odpowiedzi, ale nadal nie gwarantuje stałego czasu reakcji na najgorszą wielkość liter i nie robi nic, aby zwiększyć przyszłą modyfikację aplikacji. Ponadto procesor wykonuje teraz jeszcze więcej niepotrzebnych operacji przetwarzania z powodu dodatkowej sondowania. Wszystkie te niepotrzebne przetwarzanie zmniejsza ogólną przepływność systemu.

Interesujący punkt dotyczący narzutu polega na tym, że wielu deweloperów zakłada, że środowiska wielowątkowe, takie jak ThreadX zwiększają obciążenie i mają negatywny wpływ na łączną przepływność systemu. Jednak w niektórych przypadkach wielowątkowość w rzeczywistości zmniejsza obciążenie, eliminując wszystkie nadmiarowe sondy występujące w środowiskach pętli kontroli. Obciążenie związane z jądrami wielowątkowymi jest zazwyczaj funkcją czasu wymaganego do przełączenia kontekstu. Jeśli czas przełączenia kontekstu jest krótszy niż proces sondowania, ThreadX zapewnia rozwiązanie o możliwości mniejszego obciążenia i większej przepływności. Dzięki temu ThreadX oczywisty wybór dla aplikacji, które mają dowolny stopień złożoności lub rozmiaru.

### <a name="processor-isolation"></a>Izolacja procesora

ThreadX zapewnia niezawodny interfejs niezależny od procesora między aplikacją a podstawowym procesorem. Pozwala to deweloperom skoncentrować się na aplikacji, a nie poświęcać znacznej ilości informacji o sprzęcie.

### <a name="dividing-the-application"></a>Dzielenie aplikacji

W przypadku aplikacji opartych na pętli kontroli każdy Deweloper musi mieć intimateą wiedzę o zachowaniu i wymaganiach dotyczących całej aplikacji. Wynika to z faktu, że logika alokacji procesora jest rozproszeni w całej aplikacji. W miarę zwiększania rozmiaru lub złożoności aplikacji nie jest możliwe, że wszyscy deweloperzy zapamiętają precyzyjne wymagania dotyczące przetwarzania całej aplikacji.

ThreadX zwalnia każdego dewelopera z martw skojarzonego z alokacją procesora i umożliwia im skoncentrowanie się na określonej części aplikacji osadzonej. Ponadto ThreadX wymusza poddzielenie aplikacji na jasno zdefiniowane wątki. Ten podział aplikacji na wątki sprawia, że programowanie znacznie prostsze.

### <a name="ease-of-use"></a>Łatwość użycia

ThreadX jest zaprojektowana z myślą o deweloperu aplikacji. Architektura ThreadX i interfejs wywołania usługi zostały zaprojektowane tak, aby można je było łatwo zrozumieć. W związku z tym ThreadX deweloperzy mogą szybko korzystać z zaawansowanych funkcji.

### <a name="improve-time-to-market"></a>Popraw czas wprowadzenia na rynek

Wszystkie zalety ThreadX przyspieszają proces tworzenia oprogramowania. ThreadX zajmuje się większością problemów z procesorami i najbardziej typowymi certyfikatami bezpieczeństwa, a tym samym usunięciem tego wysiłku z harmonogramu opracowywania. Wszystkie te wyniki są krótszym czasem wprowadzenia na rynek.

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie

Ze względu na jego architekturę ThreadX można łatwo przenieść do nowych środowisk procesora i/lub narzędzi programistycznych. Dzięki temu w połączeniu z faktem, że ThreadX izolowanie aplikacji od szczegółów podstawowych procesorów, sprawia, że aplikacje ThreadX są wysoce przenośne. W związku z tym zagwarantujesz ścieżkę migracji aplikacji, a oryginalne inwestycje programistyczne są chronione.
