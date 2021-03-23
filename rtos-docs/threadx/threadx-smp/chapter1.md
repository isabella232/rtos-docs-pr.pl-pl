---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO ThreadX SMP
description: Ten rozdział zawiera wprowadzenie do produktu oraz opis jego aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 67bdb9076272fa3671ec9321baec609b291c04b8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822476"
---
# <a name="chapter-1-introduction-to-azure-rtos-threadx-smp"></a>Rozdział 1: wprowadzenie do usługi Azure RTO ThreadX SMP

Azure RTO ThreadX SMP to jądro SMP o wysokiej wydajności w czasie rzeczywistym zaprojektowane specjalnie dla aplikacji osadzonych. Ten rozdział zawiera wprowadzenie do produktu oraz opis jego aplikacji i korzyści.

## <a name="threadx-smp-unique-features"></a>ThreadX unikatowe funkcje SMP

ThreadX SMP zapewnia symetrycznej technologii przetwarzania wieloprocesowego (SMP) do aplikacji osadzonych. Wątki aplikacji SMP ThreadX (o różnym priorytecie), które są "gotowe" do uruchomienia, są przydzielane dynamicznie do dostępnych rdzeni procesora podczas planowania. Powoduje to prawdziwe przetwarzanie SMP, w tym automatyczne równoważenie obciążenia wykonywania wątków aplikacji na wszystkich dostępnych rdzeni procesora.

W przeciwieństwie do innych jądra w czasie rzeczywistym, ThreadX SMP została zaprojektowana jako uniwersalna — łatwe skalowanie między małymi aplikacjami opartymi na kontrolerach za pośrednictwem tych, które używają zaawansowanych procesorów CISC, RISC i DSP.

ThreadX SMP jest skalowalna w oparciu o jego podstawową architekturę. Ponieważ usługi SMP ThreadX są implementowane jako biblioteka C, tylko te usługi, które są używane przez aplikację, są umieszczane w obrazie w czasie wykonywania. W związku z tym rzeczywisty rozmiar ThreadX SMP jest całkowicie określony przez aplikację. W przypadku większości aplikacji obraz instrukcji ThreadX SMP mieści się w zakresie od 5 kilobajtów do 20 kilobajtów.

### <a name="picokernel-architecture"></a>Architektura™ picokernel 
Zamiast warstwowych funkcji jądra na siebie, takich jak tradycyjne architektury *mikrojądra* , THREADX usługi SMP bezpośrednio do jej rdzenia. Powoduje to najszybsze możliwe przełączenie kontekstu i wydajność wywołania usługi. Nazywamy ten projekt nienakładający się na architekturę *picokernel* .

### <a name="ansi-c-source-code"></a>Kod źródłowy ANSI C 
ThreadX SMP jest zapisywana głównie w standardzie ANSI C. Do dostosowywania jądra do bazowego procesora docelowego potrzeba niewielkiej ilości języka asemblera. Ten projekt umożliwia przenoszenie ThreadX SMP do nowej rodziny procesorów w bardzo krótkim czasie — zwykle w ciągu kilku tygodni.

### <a name="advanced-technology"></a>Technologia zaawansowana 
Poniżej przedstawiono najważniejsze informacje o technologii ThreadX SMP Advanced:

  - Prosta architektura *picokernel*
  - Automatyczne równoważenie obciążenia
  - Wykluczenie procesora dla wątku
  - Skalowanie automatyczne (małe rozmiary)
  - Deterministyczne przetwarzanie
  - Szybka wydajność w czasie rzeczywistym
  - Planowanie zastępujące i wspólne
  - Elastyczna obsługa priorytetów wątków (32-1024)
  - Tworzenie dynamicznego obiektu systemowego
  - Nieograniczona liczba obiektów systemowych
  - Zoptymalizowana obsługa przerwań
  - ™ Progu zastępujący
  - Dziedziczenie priorytetów
  - ™ Łańcucha zdarzeń
  - Szybkie czasomierze oprogramowania
  - Zarządzanie pamięcią w czasie wykonywania
  - Monitorowanie wydajności w czasie wykonywania
  - Analiza stosu czasu wykonywania
  - Wbudowane śledzenie systemu
  - Ogromne wsparcie dla procesorów
  - Obsługa ogromnych narzędzi programistycznych
  - Całkowicie endian neutral

### <a name="not-a-black-box"></a>To nie jest czarne pole
Większość dystrybucji ThreadX SMP obejmuje kompletny kod źródłowy C, a także język zestawu processorspecific. Eliminuje to problemy "z czarnym pudełkem" występujące z wieloma jądrami komercyjnymi. Dzięki ThreadX SMP deweloperzy aplikacji mogą zobaczyć dokładnie, co robi jądro — nie ma Mysteries!

Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, korzystne jest, aby mieć możliwość modyfikacji jądra, jeśli jest to absolutnie wymagane.

Te funkcje są szczególnie wygodne dla deweloperów przyzwyczajonych do pracy z własnymi *jądrami*. Oczekują one, że kod źródłowy i możliwość modyfikowania jądra. ThreadX SMP to ostateczne jądro dla deweloperów.

### <a name="the-rtos-standard"></a>Standard RTO
Ze względu na uniwersalność, architekturę *picokernel* o wysokiej wydajności, zaawansowaną technologię i możliwością przenośności ThreadX SMP została wdrożona na ponad 2 000 000 000 urządzeniach. Dzięki temu ThreadX SMP RTO Standard dla głęboko osadzonych aplikacji.

## <a name="safety-certifications"></a>Certyfikaty bezpieczeństwa

### <a name="tv-certification"></a>Certyfikat TÜV  
ThreadX SMP został certyfikowany przez moimi-TÜV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC61508 i IEC-62304. Certyfikat potwierdza, że ThreadX SMP może być używany w rozwoju oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności bezpieczeństwa Międzynarodowa Komisja Elektrotechniczna (IEC) 61508 i IEC 62304 dla "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem". MOIMI-TÜV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TÜV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, weryfikowania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które są od niego pochodzące, w tym IEC 62304, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych i systemów kontroli szynowej.

MOIMI-TÜV Saar ma certyfikowaną ThreadX SMP do użycia w systemach samochodowych o krytycznym znaczeniu dla bezpieczeństwa, zgodnie ze standardem ISO 26262. Ponadto ThreadX SMP jest certyfikowany do poziomu integralności infrastruktury bezpieczeństwa motoryzacyjnego (ASIL) D, który reprezentuje najwyższy poziom certyfikacji ISO 26262.

Dodatkowo moimi-TÜV Saar ma certyfikowaną ThreadX SMP do użycia w aplikacjach do kolei o krytycznym znaczeniu dla bezpieczeństwa, a także ze standardem 50128 do SW-SIL 4.

![Certyfikat TÜV](media/image2.png)

IEC 61508 do SIL 4  
IEC 62304 do klasy bezpieczeństwa oprogramowania SW (C)  
ISO 26262 ASIL D  
EN 50128 SW — SIL 4  

> [!IMPORTANT]
> Skontaktuj się z nami, [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Aby uzyskać więcej informacji na temat wersji THREADX SMP certyfikowanych przez TÜV lub do dostępności raportów testowych, certyfikatów i powiązanej dokumentacji.

### <a name="misra-c-compliant"></a>Zgodne z MISRA C 
MISRA C to zestaw wytycznych programistycznych dotyczących krytycznych systemów przy użyciu języka programowania C. Oryginalne wytyczne dotyczące języka MISRA C były głównie przeznaczone do aplikacji motoryzacyjnych; jednak MISRA C jest teraz szeroko uznawany za mające zastosowanie do wszystkich aplikacji o krytycznym znaczeniu dla bezpieczeństwa. ThreadX SMP jest zgodna ze wszystkimi regułami "wymagane" i "obowiązkowymi" w przypadku MISRA-C:2004 i MISRA C:2012. ThreadX SMP jest również zgodna ze wszystkimi regułami "poradników". Aby uzyskać więcej informacji, zapoznaj się z dokumentem ***ThreadX_MISRA_Compliance.pdf*** .

### <a name="ul-certification"></a>Certyfikat UL 
ThreadX SMP został certyfikowany przez UL w celu zapewnienia zgodności z UL 60730-1 w załączniku h, CSA E607301 załącznik H, IEC 60730-1 załącznik H, UL 60335-1 Załącznik R, IEC 60335-1 Załącznik R i standardy bezpieczeństwa UL 1998 dla oprogramowania w składnikach programowalnych. Wraz z IEC/UL 60730-1, które mają wymagania dotyczące "kontrolek wykorzystujących oprogramowanie" w załączniku H, standard IEC 60335-1 opisuje wymagania dotyczące "programowalnych obwodów elektronicznych" w załączniku R. IEC 60730 załącznik H i IEC 60335-1 Załącznik R dotyczy bezpieczeństwa sprzętu i oprogramowania używanego w urządzeniach, takich jak pralki, zmywarki, Dryers, chłodziarks, zamrażarki i Piece.

![Certyfikat UL](media/image3.png) 

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
> Skontaktuj się z nami, [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) Aby uzyskać więcej informacji na temat wersji THREADX SMP certyfikowanych przez TÜV lub do dostępności raportów testowych, certyfikatów i powiązanej dokumentacji.

### <a name="certification-pack"></a>Pakiet certyfikacji

Pakiet certyfikacji SMP ThreadX™ to 100% całości, gotowe, specyficzny dla branży pakiet autonomiczny, który zapewnia wszystkie dowody ThreadX SMP wymagane do certyfikowania lub pomyślnego przesłania przez ThreadX produkt oparty na SMP, do najwyższej niezawodności i poziomu krytycznego wymaganych w przypadku lotnictwa krytycznego dla bezpieczeństwa, medycznego i systemów przemysłowych. Obsługiwane certyfikaty obejmują DO-178B, ED-12B, DO-278, FDA510 (k), IEC-62304, IEC-60601, ISO-14971, UL-1998, IEC-61508, CENELEC EN50128, BS50128 i 49CFR236. Skontaktuj się z nami, sales@expresslogic.com Aby uzyskać więcej informacji na temat pakietu certyfikacji.

## <a name="embedded-applications"></a>Aplikacje osadzone

Aplikacje osadzone są wykonywane na mikroprocesorach, które są objęte produktami, takimi jak urządzenia komunikacyjne sieci bezprzewodowej, aparaty samochodów, drukarki laserowe, urządzenia medyczne itp. Innym rozróżnieniem aplikacji osadzonych jest to, że oprogramowanie i sprzęt mają dedykowany cel.

### <a name="real-time-software"></a>Oprogramowanie w czasie rzeczywistym 
Po nałożeniu ograniczeń czasowych na oprogramowanie aplikacji jest ono nazywane oprogramowaniem w *czasie rzeczywistym* . Zasadniczo oprogramowanie, które musi wykonać przetwarzanie w określonym czasie, jest nazywane oprogramowaniem w *czasie rzeczywistym* . Aplikacje osadzone są prawie zawsze w czasie rzeczywistym ze względu na ich nieodłączną interakcję ze zdarzeniami zewnętrznymi.

### <a name="multitasking"></a>Wielozadaniowość  
Jak wspomniano, aplikacje osadzone mają dedykowany cel. Aby zrealizować ten cel, oprogramowanie musi wykonać rozmaite *zadania*. Zadanie to częściowo niezależna część aplikacji, która wykonuje określone cło. Jest to również sytuacja, w której niektóre zadania są ważniejsze niż inne. Jednym z głównych trudności w aplikacji osadzonej jest alokacja procesora między różnymi zadaniami aplikacji. Ta alokacja przetwarzania między zadaniami konkurującymi jest głównym celem ThreadX SMP.

### <a name="tasks-vs-threads"></a>Zadania a wątki 
Należy wprowadzić inne rozróżnienie dotyczące zadań. Termin zadanie jest używany na różne sposoby. Czasami oznacza to, że program może być ładowany osobno. W innych przypadkach może odnosić się do wewnętrznego segmentu programu.

W współczesnej dyskusji z systemami operacyjnymi istnieją dwa warunki, które zastępują w tym przypadku zadania: *proces* i *wątek*. *Proces* jest całkowicie niezależnym programem, który ma własną przestrzeń adresową, a *wątek* jest segmentem programu niezależnym, który jest wykonywany w ramach procesu. Wątki współużytkują tę samą przestrzeń adresową procesu. Obciążenie związane z zarządzaniem wątkami jest minimalne.

Większość aplikacji osadzonych nie może zapewnić obciążenia (zarówno pamięci, jak i wydajności) związanego z pełnym rozwiniętą systemem operacyjnym opartym na procesie. Ponadto mniejsze mikroprocesory nie mają architektury sprzętu do obsługi prawdziwego systemu operacyjnego zorientowanego na procesy. Z tego względu ThreadX SMP implementuje model wątku, który jest zarówno niezwykle wydajny, jak i praktyczny dla większości aplikacji osadzonych w czasie rzeczywistym.

Aby uniknąć nieporozumień, ThreadX SMP nie korzysta z terminu *zadanie*. Zamiast tego jest używany bardziej opisowy i współczesny *wątek* nazw.

## <a name="threadx-smp-benefits"></a>Korzyści z ThreadX SMP

Korzystanie z ThreadX SMP zapewnia wiele korzyści dla aplikacji osadzonych. Oczywiście podstawową korzyścią jest zapełnienie czasu przetwarzania wątków aplikacji osadzonych.

### <a name="automatic-load-balancing"></a>Automatyczne równoważenie obciążenia  
ThreadX SMP zapewnia automatyczne równoważenie obciążenia (wykonywanie wątków między dostępnymi rdzeniami), dzięki czemu można łatwo jak najłatwiej korzystać z procesorów wielordzeniowych. 

### <a name="improved-responsiveness"></a>Zwiększona czas odpowiedzi  
Przed jądrami w czasie rzeczywistym, takimi jak ThreadX SMP, większość osadzonych aplikacji przydzieliła czas przetwarzania z prostą pętlą kontroli, zazwyczaj z poziomu *głównej* funkcji języka C. To podejście jest nadal używane w bardzo małych lub prostych aplikacjach. Jednak w dużych lub złożonych aplikacjach nie jest to praktyczne, ponieważ czas odpowiedzi dla każdego zdarzenia jest funkcją czasu przetwarzania worstcase jednego przebiegu przez pętlę kontroli.

W kwestiach niepotrzebnych, charakterystyk chronometrażu aplikacji jest zmieniana za każdym razem, gdy wprowadzane są modyfikacje w pętli kontroli. Sprawia to, że aplikacja jest niestabilna i trudno ją obsługiwać i ulepszać.

ThreadX SMP zapewnia szybkie i deterministyczne czasy odpowiedzi na ważne zdarzenia zewnętrzne. ThreadX SMP jest realizowana za pośrednictwem jego zastępujący priorytetowego algorytmu planowania, który umożliwia wątkowi o wyższym priorytecie przechodzenie przez wykonywanie wątku niższego priorytetu. W efekcie czas odpowiedzi na najgorszy przypadek zbliża się do czasu wymaganego do wykonania przełączenia kontekstu. Jest to nie tylko deterministyczne, ale jest również niezwykle szybka.

### <a name="software-maintenance"></a>Konserwacja oprogramowania  
Jądro SMP ThreadX umożliwia deweloperom aplikacji skoncentrowanie się na określonych wymaganiach wątków aplikacji bez konieczności zajmowania się zmianami chronometrażu innych obszarów aplikacji. Ta funkcja znacznie ułatwia naprawianie lub ulepszanie aplikacji, która wykorzystuje ThreadX SMP.

### <a name="increased-throughput"></a>Zwiększona przepływność  
Możliwe jest obejście problemu dotyczącego czasu odpowiedzi pętli kontroli w celu dodania większej liczby sondowań. Pozwala to zwiększyć czas odpowiedzi, ale nadal nie gwarantuje stałego czasu reakcji na najgorszą wielkość liter i nie robi nic, aby zwiększyć przyszłą modyfikację aplikacji. Ponadto procesor wykonuje teraz jeszcze więcej niepotrzebnych operacji przetwarzania z powodu dodatkowej sondowania. Wszystkie te niepotrzebne przetwarzanie zmniejsza ogólną przepływność systemu.

Interesujący punkt dotyczący narzutu polega na tym, że wielu deweloperów zakłada, że środowiska wielowątkowe, takie jak ThreadX SMP, zwiększają obciążenie i mają negatywny wpływ na łączną przepływność systemu. Jednak w niektórych przypadkach wielowątkowość w rzeczywistości zmniejsza obciążenie, eliminując wszystkie nadmiarowe sondy występujące w środowiskach pętli kontroli. Obciążenie związane z jądrami wielowątkowymi jest zazwyczaj funkcją czasu wymaganego do przełączenia kontekstu. Jeśli czas przełączenia kontekstu jest mniejszy niż proces sondowania, ThreadX SMP zapewnia rozwiązanie o możliwości mniejszego obciążenia i większej przepływności. Dzięki temu ThreadX SMP oczywisty wybór dla aplikacji, które mają dowolny stopień złożoności lub rozmiaru.

### <a name="processor-isolation"></a>Izolacja procesora  
ThreadX SMP zapewnia niezawodny interfejs processorindependent między aplikacją a podstawowym procesorem. Pozwala to deweloperom skoncentrować się na aplikacji, a nie poświęcać znacznej ilości informacji o sprzęcie. 

### <a name="dividing-the-application"></a>Dzielenie aplikacji  
W przypadku aplikacji opartych na pętli kontroli każdy Deweloper musi mieć intimateą wiedzę o zachowaniu i wymaganiach dotyczących całej aplikacji. Wynika to z faktu, że logika alokacji procesora jest rozproszeni w całej aplikacji. W miarę zwiększania rozmiaru lub złożoności aplikacji nie jest możliwe, że wszyscy deweloperzy zapamiętają precyzyjne wymagania dotyczące przetwarzania całej aplikacji.

ThreadX SMP zwalnia każdego dewelopera z martw skojarzonego z alokacją procesora i umożliwia im skoncentrowanie się na określonej części aplikacji osadzonej. Ponadto ThreadX SMP wymusza podział aplikacji na jasno zdefiniowane wątki. Ten podział aplikacji na wątki sprawia, że programowanie znacznie prostsze.

### <a name="ease-of-use"></a>Łatwość użycia  
ThreadX SMP został zaprojektowany z myślą o deweloperu aplikacji. Architektura SMP ThreadX i interfejs wywołania usługi zostały zaprojektowane tak, aby można je było łatwo zrozumieć. W efekcie deweloperzy SMP ThreadX mogą szybko korzystać z zaawansowanych funkcji.  

### <a name="improve-time-to-market"></a>Popraw czas wprowadzenia na rynek  
Wszystkie zalety ThreadX SMP przyspieszają proces tworzenia oprogramowania. ThreadX SMP zajmuje się większością problemów z procesorami i najbardziej typowymi certyfikatami bezpieczeństwa, a tym samym usunięciem tego wysiłku z harmonogramu opracowywania. Wszystkie te wyniki są krótszym czasem wprowadzenia na rynek.  

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie  
Ze względu na jego architekturę ThreadX SMP jest łatwo przeprojektowana do nowych środowisk procesora i/lub narzędzi programistycznych. Jest to powiązane z faktem, że ThreadX SMP izolowanie aplikacji ze szczegółowych procesorów, sprawia, że aplikacje ThreadX SMP są wysoce przenośne. W związku z tym zagwarantujesz ścieżkę migracji aplikacji, a oryginalne inwestycje programistyczne są chronione.