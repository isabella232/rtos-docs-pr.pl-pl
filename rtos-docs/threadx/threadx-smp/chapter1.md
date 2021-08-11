---
title: Rozdział 1 — Wprowadzenie do Azure RTOS SMP ThreadX
description: Ten rozdział zawiera wprowadzenie do produktu oraz opis jego aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9b9fb7b08691930abcf57df77fff27e619bb7a554a6235d4e234889b7c80945e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802252"
---
# <a name="chapter-1-introduction-to-azure-rtos-threadx-smp"></a>Rozdział 1: Wprowadzenie do Azure RTOS ThreadX SMP

Azure RTOS ThreadX SMP jest jądrem SMP w czasie rzeczywistym o wysokiej wydajności zaprojektowanym specjalnie dla aplikacji osadzonych. Ten rozdział zawiera wprowadzenie do produktu oraz opis jego aplikacji i korzyści.

## <a name="threadx-smp-unique-features"></a>Unikatowe funkcje SMP ThreadX

Technologia SMP ThreadX umożliwia zastosowanie technologii SMP w aplikacjach osadzonych. Wątki aplikacji SMP ThreadX (o różnym priorytecie), które są gotowe do uruchomienia, są dynamicznie przydzielane do dostępnych rdzeni procesora podczas planowania. Powoduje to prawdziwe przetwarzanie SMP, w tym automatyczne równoważenie obciążenia wykonywania wątku aplikacji we wszystkich dostępnych rdzeniach procesora.

W przeciwieństwie do innych jąder czasu rzeczywistego threadX SMP zaprojektowano tak, aby były uniwersalne — łatwe skalowanie między małymi aplikacjami opartymi na mikrokontrolerach za pośrednictwem tych, które korzystają z zaawansowanych procesorów CISC, RISC i DSP.

ThreadX SMP jest skalowalny w oparciu o jego podstawową architekturę. Ponieważ usługi SMP ThreadX są implementowane jako biblioteka języka C, tylko te usługi faktycznie używane przez aplikację są wprowadzane do obrazu w czasie uruchamiania. W związku z tym rzeczywisty rozmiar SMP ThreadX jest całkowicie określany przez aplikację. W przypadku większości aplikacji obraz instrukcji threadX SMP ma rozmiar od 5 KB do 20 KB.

### <a name="picokernel-architecture"></a>picokernel™ Architecture 
Zamiast nakładać na siebie funkcje jądra, takie jak tradycyjne architektury *mikrokernel,* usługi SMP ThreadX są podłączane bezpośrednio do jej rdzeni. Skutkuje to najszybszą możliwą wydajnością przełączania kontekstu i wywołania usługi. Nazywamy to niewarstwowym projektem *architekturę picokernel.*

### <a name="ansi-c-source-code"></a>Kod źródłowy ANSI C 
ThreadX SMP jest napisany głównie w języku ANSI C. Aby dostosować jądro do podstawowego procesora docelowego, potrzebna jest niewielka ilość języka zestawu. Ten projekt umożliwia przenoszenie SMP ThreadX do nowej rodziny procesorów w bardzo krótkim czasie — zwykle w ciągu tygodni!

### <a name="advanced-technology"></a>Zaawansowana technologia 
Poniżej przedstawiono najważniejsze informacje na temat zaawansowanej technologii SMP ThreadX:

  - Prosta *architektura picokernel*
  - Automatyczne równoważenie obciążenia
  - Wykluczenie procesora na wątek
  - Automatyczne skalowanie (małe zużycie)
  - Przetwarzanie deterministyczne
  - Szybka wydajność w czasie rzeczywistym
  - Planowanie wywłaszcze i kooperatywne
  - Elastyczna obsługa priorytetów wątków (32–1024)
  - Dynamiczne tworzenie obiektów systemowych
  - Nieograniczona liczba obiektów systemowych
  - Zoptymalizowana obsługa przerwań
  - Próg wywłaszczenia™
  - Dziedziczenie priorytetów
  - Łańcuch zdarzeń™
  - Szybkie czasomierze oprogramowania
  - Zarządzanie pamięcią w czasie rzeczywistym
  - Monitorowanie wydajności w czasie wykonywania
  - Analiza stosu w czasie rzeczywistym
  - Wbudowane śledzenie systemu
  - Obsługa ogromnych procesorów
  - Ogromna obsługa narzędzi dewelopera
  - Całkowicie neutralna endian

### <a name="not-a-black-box"></a>Nie jest czarną skrzynką
Większość dystrybucji SMP ThreadX obejmuje pełny kod źródłowy C, a także procesorokreślony język zestawu. Eliminuje to problemy "czarnej skrzynki", które występują w przypadku wielu jąder komercyjnych. W przypadku SMP ThreadX deweloperzy aplikacji mogą zobaczyć dokładnie, co robi jądro — nie ma żadnych wątków!

Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji. Chociaż nie jest to zalecane, na pewno korzystne jest, aby mieć możliwość modyfikowania jądra, jeśli jest to absolutnie wymagane.

Te funkcje są szczególnie wygodne dla deweloperów, którzy są przywykli do pracy z własnymi *jądrami typu inhouse.* Oczekują oni kodu źródłowego i możliwości modyfikowania jądra. ThreadX SMP jest ostatecznym jądrem dla takich deweloperów.

### <a name="the-rtos-standard"></a>The RTOS Standard
Ze względu na ich niezawodność, wysoką wydajność, architekturę *rozwiązania Picokernel,* zaawansowaną technologię i zademonstrowany przenośność, technologia ThreadX SMP jest obecnie wdrażana na ponad dwóch miliardach urządzeń. Dzięki temu threadX SMP jest standardem RTOS dla aplikacji głęboko osadzonych.

## <a name="safety-certifications"></a>Certyfikaty bezpieczeństwa

### <a name="tv-certification"></a>Certyfikacja TÜV  
ThreadX SMP ma certyfikat SGS-TÜV Saar do użycia w systemach o krytycznym znaczeniu dla bezpieczeństwa, zgodnie z normami IEC61508 i IEC-62304. Certyfikat potwierdza, że threadX SMP może być używany podczas opracowywania oprogramowania związanego z bezpieczeństwem dla najwyższych poziomów integralności bezpieczeństwa systemów Międzynarodowa Komisja Elektrotechniczna (IEC) 61508 i IEC 62304 dla "bezpieczeństwa funkcjonalnego systemów elektronicznych, elektronicznych i programowalnych systemów związanych z bezpieczeństwem elektronicznym". SGS-TÜV Saar, utworzone za pośrednictwem wspólnej osady niemieckich firm SGS-Group i TÜV Saarland, stała się wiodącą akredytowaną, niezależną firmą do testowania, inspekcji, weryfikowania i certyfikowania osadzonego oprogramowania dla systemów powiązanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które z niego pochodzą, w tym IEC 62304, są używane w celu zapewnienia bezpieczeństwa funkcjonalnego urządzeń elektronicznych, elektronicznych i programowalnych urządzeń medycznych związanych z bezpieczeństwem, systemów sterowania procesami, maszyn przemysłowych i systemów sterowania węzłem.

SGS-TÜV Saar ma certyfikat ThreadX SMP do stosowania w krytycznych dla bezpieczeństwa systemach samochodowych zgodnie ze standardem ISO 26262. Ponadto threadX SMP ma certyfikat ASIL D (Safety Integrity Level) dla samochodów, który reprezentuje najwyższy poziom certyfikacji ISO 26262.

Ponadto firma SGS-TÜV Saar ma certyfikat ThreadX SMP, który może być używany w aplikacjach z krytycznym poziomem bezpieczeństwa, zgodnie ze standardem EN 50128 i z programem SW-SIL 4.

![Certyfikacja TÜV](media/image2.png)

IEC 61508 do SIL 4  
IEC 62304 do bezpieczeństwa SW, klasa C  
ISO 26262 ASIL D  
EN 50128 SW-SIL 4  

> [!IMPORTANT]
> Skontaktuj się z nami, aby uzyskać więcej informacji na temat wersji, które threadX SMP zostały certyfikowane przez TÜV lub dostępności raportów testowych, certyfikatów i [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) skojarzonej dokumentacji.

### <a name="misra-c-compliant"></a>Zgodne ze standardem MISRA C 
MISRA C to zestaw wytycznych programowania dla systemów krytycznych korzystających z języka programowania C. Oryginalne wytyczne MISRA C były przeznaczone głównie dla aplikacji samochodowych. Jednak język MISRA C jest teraz powszechnie uznawany za stosowany do wszystkich aplikacji o krytycznym znaczeniu dla bezpieczeństwa. ThreadX SMP jest zgodny ze wszystkimi "wymaganymi" i "obowiązkowymi" regułami MISRA-C:2004 i MISRA C:2012. ThreadX SMP jest również zgodny ze wszystkimi regułami "porad" oprócz trzech. Zapoznaj się z ***ThreadX_MISRA_Compliance.pdf,*** aby uzyskać więcej szczegółów.

### <a name="ul-certification"></a>Certyfikacja UL 
ThreadX SMP został certyfikowany przez firmę UL do zgodności z normami UL 60730-1 , H, CSA E607301, H, IEC 60730-1, H, UL 60335-1, IEC 60335-1; standardy bezpieczeństwa R i UL 1998 dla oprogramowania w programowalnych elementach. Wraz z IEC/UL 60730-1 który ma wymagania dotyczące "kontrolek korzystających z oprogramowania" w załączniku H, standard IEC 60335-1 opisuje wymagania dotyczące "programowalnych obwodów elektronicznych" w załączniku R. IEC 60730, załącznik H i IEC 60335-1 Dokument R dotyczy bezpieczeństwa sprzętu i oprogramowania MCU używanego w urządzeniach, takich jak maszyny nagie, nagie, lodówki, chłodziarki i pąki.

![Certyfikacja UL](media/image3.png) 

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
> Skontaktuj się z nami, aby uzyskać więcej informacji na temat wersji, które threadX SMP zostały certyfikowane przez TÜV lub dostępności raportów testowych, certyfikatów i [azure-rtos-support@microsoft.com](https://azure-rtos-support@microsoft.com) skojarzonej dokumentacji.

### <a name="certification-pack"></a>Pakiet certyfikacji

Pakiet certyfikacji SMP ThreadX™ jest w 100% kompletnym, gotowego do zastosowania, specyficznym dla branży, autonomicznym pakietem, który zapewnia wszystkie dowód SMP ThreadX potrzebne do certyfikacji lub pomyślnego przesyłania produktu opartego na threadX SMP na najwyższy poziom niezawodności i krytyczności wymagany dla systemów informatycznych, medycznych i przemysłowych o krytycznym znaczeniu dla bezpieczeństwa. Obsługiwane certyfikaty obejmują DO-178B, ED-12B, DO-278, ICH510(k), IEC-62304, IEC-60601, ISO-14971, UL-1998, IEC-61508, CENELEC EN50128, BS50128 i 49CFR236. Aby uzyskać więcej informacji na temat pakietu certyfikacji, skontaktuj się sales@expresslogic.com z nami pod adres .

## <a name="embedded-applications"></a>Aplikacje osadzone

Aplikacje osadzone są wykonywane na mikroprocesorach w produktach, takich jak urządzenia do komunikacji bezprzewodowej, aparaty samochodowy, drukarki laserowe, urządzenia medyczne itp. Innym rozróżnieniem aplikacji osadzonych jest to, że ich oprogramowanie i sprzęt mają specjalne przeznaczenie.

### <a name="real-time-software"></a>Oprogramowanie w czasie rzeczywistym 
Gdy na oprogramowanie aplikacji nakładane są ograniczenia czasowe, jest ono nazywane oprogramowaniem *w czasie* rzeczywistym. Zasadniczo oprogramowanie, które musi wykonywać swoje przetwarzanie w dokładnym czasie, jest nazywane oprogramowaniem *w czasie rzeczywistym.* Aplikacje osadzone prawie zawsze są w czasie rzeczywistym ze względu na ich naturalną interakcję ze zdarzeniami zewnętrznymi.

### <a name="multitasking"></a>Wielozadaniowość  
Jak wspomniano wcześniej, aplikacje osadzone mają specjalne przeznaczenie. Aby zrealizować ten cel, oprogramowanie musi wykonywać różne *zadania.* Zadanie to częściowo niezależna część aplikacji, która wykonuje określone obowiązki. Jest również tak, że niektóre zadania są ważniejsze niż inne. Jedną z głównych trudności w aplikacji osadzonej jest alokacja procesora między różnymi zadaniami aplikacji. Ta alokacja przetwarzania między konkurującymi zadaniami jest głównym celem SMP ThreadX.

### <a name="tasks-vs-threads"></a>Zadania a wątki 
Należy wprowadzić inne rozróżnienie dotyczące zadań. Termin zadanie jest używane na wiele sposobów. Czasami oznacza to oddzielny program z możliwością ładowania. W innych przypadkach może odwoływać się do wewnętrznego segmentu programu.

W najbardziej współczesnym dyskusji o systemie operacyjnym istnieją dwa terminy, które więcej lub mniej zastępują użycie zadania: *proces* i *wątek*. Proces *jest* całkowicie niezależnym programem, który ma własną przestrzeń adresową, *podczas* gdy wątek jest częściowo niezależnym segmentem programu, który jest wykonywany w ramach procesu. Wątki współdzielą tę samą przestrzeń adresową procesu. Obciążenie związane z zarządzaniem wątkami jest minimalne.

Większość aplikacji osadzonych nie może pozwolić sobie na obciążenie (zarówno pamięć, jak i wydajność) związane z w pełni zorientowanym na proces systemem operacyjnym. Ponadto mniejsze mikroprocesory nie mają architektury sprzętowej do obsługi prawdziwego systemu operacyjnego zorientowanego na proces. Z tego powodu threadX SMP implementuje model wątków, który jest bardzo wydajny i praktyczny w przypadku większości aplikacji osadzonych w czasie rzeczywistym.

Aby uniknąć nieporozumień, threadX SMP nie używa terminu *zadanie*. Zamiast tego używany jest bardziej opisowy i bardziej *opisowy wątek* nazwy.

## <a name="threadx-smp-benefits"></a>Korzyści związane z SMP ThreadX

Korzystanie z threadX SMP zapewnia wiele korzyści dla aplikacji osadzonych. Oczywiście główną korzyścią jest przydzielanie czasu przetwarzania osadzonych wątków aplikacji.

### <a name="automatic-load-balancing"></a>Automatyczne równoważenie obciążenia  
SMP ThreadX zapewnia automatyczne równoważenie obciążenia (wykonywanie wątków między dostępnymi rdzeniami), co sprawia, że korzystanie z procesorów wielordzeniowych jest tak proste, jak to możliwe. 

### <a name="improved-responsiveness"></a>Udoskonalony czas odpowiedzi  
Przed jądrami czasu rzeczywistego, takich jak ThreadX SMP, większość osadzonych aplikacji przydzielała czas przetwarzania przy użyciu prostej pętli sterowania, zazwyczaj z poziomu funkcji *main języka* C. To podejście jest nadal stosowane w bardzo małych lub prostych aplikacjach. Jednak w dużych lub złożonych aplikacjach nie jest to praktyczne, ponieważ czas odpowiedzi na dowolne zdarzenie jest funkcją najgorszego czasu przetwarzania jednego przebiegu przez pętlę sterowania.

Co gorsza, charakterystyki chronometrażu aplikacji zmieniają się za każdym razem, gdy w pętli sterowania zostaną wprowadzone modyfikacje. Sprawia to, że aplikacja jest z założenia niestabilna i trudna w konserwacji oraz ulepszana.

SMP ThreadX zapewnia szybkie i deterministyczne czasy odpowiedzi na ważne zdarzenia zewnętrzne. ThreadX SMP realizuje to za pomocą swojego wywłaszczaczego algorytmu planowania opartego na priorytetach, który umożliwia wątkowi o wyższym priorytecie wywłaszczanie wykonywania wątku o niższym priorytecie. W związku z tym czas odpowiedzi w najgorszym przypadku zbliża się do czasu wymaganego do przełączenia kontekstu. Jest to nie tylko deterministyczne, ale również niezwykle szybkie.

### <a name="software-maintenance"></a>Konserwacja oprogramowania  
Jądro SMP ThreadX umożliwia deweloperom aplikacji skoncentrowanie się na określonych wymaganiach swoich wątków aplikacji bez konieczności martwienia się o zmianę czasu innych obszarów aplikacji. Ta funkcja znacznie ułatwia również naprawę lub ulepszanie aplikacji, która korzysta z opcji SMP ThreadX.

### <a name="increased-throughput"></a>Zwiększona przepływność  
Możliwe rozwiązanie problemu czasu odpowiedzi pętli sterowania polega na dodaniu większej liczby sondowania. Poprawia to czas odpowiedzi, ale nadal nie gwarantuje stałego czasu odpowiedzi w najgorszym przypadku i nie robi nic, aby poprawić przyszłe modyfikacje aplikacji. Ponadto procesor wykonuje teraz jeszcze bardziej niepotrzebne przetwarzanie ze względu na dodatkowe sondowanie. Wszystkie te niepotrzebne przetwarzanie zmniejsza ogólną przepływność systemu.

Interesującym punktem w zakresie narzutu jest to, że wielu deweloperów zakłada, że środowiska wielowątkowe, takie jak ThreadX SMP, zwiększają narzut i mają negatywny wpływ na łączną przepływność systemu. Jednak w niektórych przypadkach wielowątkowanie faktycznie zmniejsza obciążenie, eliminując całe nadmiarowe sondowanie, które występuje w środowiskach pętli sterowania. Obciążenie związane z jądrami wielowątkowych jest zwykle funkcją czasu wymaganą do przełączania kontekstu. Jeśli czas przełączania kontekstu jest krótszy niż proces sondowania, SMP ThreadX zapewnia rozwiązanie z potencjalnym mniejszym obciążeniem i większą przepływnością. Dzięki temu SMP ThreadX jest oczywistym wyborem dla aplikacji, które mają dowolny stopień złożoności lub rozmiaru.

### <a name="processor-isolation"></a>Izolacja procesora  
ThreadX SMP zapewnia niezawodny procesorw zależności interfejs między aplikacją a procesorem bazowym. Dzięki temu deweloperzy mogą skoncentrować się na aplikacji, zamiast poświęcać znaczną ilość czasu na uczenie się szczegółów sprzętu. 

### <a name="dividing-the-application"></a>Dzielenie aplikacji  
W aplikacjach opartych na pętli sterowania każdy deweloper musi mieć pełną wiedzę na temat zachowania i wymagań całej aplikacji w czasie działania. Jest to spowodowane rozproszeniem logiki alokacji procesora w całej aplikacji. Wraz ze wzrostem rozmiaru lub złożoności aplikacji wszyscy deweloperzy nie będą w stanie zapamiętać dokładnych wymagań dotyczących przetwarzania całej aplikacji.

ThreadX SMP pozwala każdemu deweloperowi nie martwić się o alokację procesora i pozwala mu skoncentrować się na konkretnym elementie osadzonej aplikacji. Ponadto threadX SMP wymusza podzielenie aplikacji na jasno zdefiniowane wątki. Sam ten podział aplikacji na wątki sprawia, że opracowywanie jest znacznie prostsze.

### <a name="ease-of-use"></a>Łatwość obsługi  
ThreadX SMP został zaprojektowany z myślą o deweloperze aplikacji. Architektura SMP ThreadX i interfejs wywołania usługi zostały zaprojektowane tak, aby można je było łatwo zrozumieć. W związku z tym deweloperzy SMP ThreadX mogą szybko korzystać z jej zaawansowanych funkcji.  

### <a name="improve-time-to-market"></a>Poprawianie czasu przedsieć na rynek  
Wszystkie zalety technologii SMP ThreadX przyspieszają proces tworzenia oprogramowania. ThreadX SMP zajmuje się większość problemów z procesorem i najczęściej spotykane certyfikaty bezpieczeństwa, co pozwala usunąć ten nakład pracy z harmonogramu projektowania. Wszystko to powoduje szybsze wyekserowania!  

### <a name="protecting-the-software-investment"></a>Ochrona inwestycji w oprogramowanie  
Ze względu na architekturę smp ThreadX jest łatwo przenoszony do nowych procesorów i/lub środowisk narzędzi deweloperskich. W połączeniu z tym, że ThreadX SMP odizoluje aplikacje od szczegółów bazowych procesorów, sprawia, że aplikacje ThreadX SMP są wysoce przenośne. W związku z tym ścieżka migracji aplikacji jest gwarantowana, a pierwotna inwestycja w tworzenie aplikacji jest chroniona.