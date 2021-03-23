---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO FileX
description: Usługa Azure RTO FileX to kompletny system zarządzania plikami w formacie FAT i w przypadku aplikacji głęboko osadzonych.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be7e6f9cd9fbc69ac0908d1de733dac1c4f73bf6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821421"
---
# <a name="chapter-1---introduction-to-azure-rtos-filex"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO FileX

Usługa Azure RTO FileX to kompletny system zarządzania plikami w formacie FAT i w przypadku aplikacji głęboko osadzonych. W tym rozdziale wprowadzono FileX opisujące swoje aplikacje i korzyści.

## <a name="filex-unique-features"></a>FileX unikatowe funkcje

Usługa Azure RTO FileX obsługuje nieograniczoną liczbę urządzeń multimedialnych, w tym dysków RAM, menedżerów i urządzeń fizycznych. Obsługuje 12-, 16-i 32-bitowe formaty tabeli alokacji plików (FAT), a także obsługuje rozszerzone tabele alokacji plików (exFAT), ciągłą alokację plików i są wysoce zoptymalizowane pod kątem rozmiaru i wydajności. FileX obejmuje również obsługę odporną na uszkodzenia, otwarcie/zamknięcie nośnika i funkcje wywołania zwrotnego.

Zaprojektowana w celu spełnienia rosnącej potrzeby dla urządzeń z programem FLASH FileX korzysta z tych samych metod projektowania i kodowania jak ThreadX. Podobnie jak w przypadku wszystkich produktów firmy Microsoft, FileX jest dystrybuowany z pełnym kodem źródłowym ANSI C i nie ma opłat za czas wykonywania.

### <a name="product-highlights"></a>Najważniejsze informacje o produkcie

- Ukończ obsługę procesora ThreadX
- Bez opłat
- Pełny kod źródłowy ANSI C
- Wydajność w czasie rzeczywistym
- Reagowanie na pomoc techniczną
- Nieograniczone obiekty FileX (nośniki, katalogi i pliki)
- Dynamiczne tworzenie/usuwanie obiektów FileX
- Elastyczne użycie pamięci
- Automatyczne skalowanie rozmiaru
- Niewielkie rozmiary obszaru instrukcji (o niskim rozmiarze 6 kilobajtów): 6-30K
- Pełna integracja z usługą ThreadX
- Neutralne
- Łatwe w obsłudze sterowniki we/wy FileX
- Obsługa 12-, 16-i 32-bitowego systemu plików FAT
- Obsługa exFAT
- Obsługa długich nazw plików
- Wewnętrzna pamięć podręczna wpisów systemu FAT
- Obsługa nazw Unicode
- Ciągła alokacja plików
- Kolejny sektor i odczyt/zapis w klastrze
- Pamięć podręczna wewnętrznego sektora logicznego
- Prezentacja na dysku pamięci RAM jest uruchamiana jako wbudowana
- Możliwość formatowania multimediów
- Wykrywanie i odzyskiwanie błędów
- Opcje odporne na uszkodzenia
- Wbudowane statystyki wydajności
- Obsługa autonomiczna (bez usługi Azure RTO)

## <a name="safety-certifications"></a>Certyfikaty bezpieczeństwa

### <a name="tv-certification"></a>Certyfikat TÜV

FileX został certyfikowany przez moimi-TÜV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC-61508 i IEC-62304. Certyfikat potwierdza, że FileX może być używany w rozwoju oprogramowania związanego z bezpieczeństwem dla najwyższych poziomów integralności bezpieczeństwa Międzynarodowa Komisja Elektrotechniczna (IEC) 61508 i IEC 62304 dla "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem". MOIMI-TÜV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TÜV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, weryfikowania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które są od niego pochodzące, w tym IEC 62304, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych i systemów kontroli szynowej.

MOIMI-TÜV Saar ma certyfikowane FileX do użycia w systemach samochodowych o krytycznym znaczeniu dla bezpieczeństwa, zgodnie ze standardem ISO 26262. Ponadto FileX jest certyfikowany na poziomie integralności infrastruktury bezpieczeństwa motoryzacyjnego (ASIL), który reprezentuje najwyższy poziom certyfikacji ISO 26262.

Dodatkowo moimi-TÜV Saar ma certyfikowane FileX, które mają być używane w kluczowych dla bezpieczeństwa aplikacjach szynowych, ze względu na Standard 50128 do SW-SIL 4.

![Logo moimi TUV Saar](./media/user-guide/sgs-tuv-saar-logo.png)

- IEC 61508 do SIL 4
- IEC 62304 do klasy bezpieczeństwa oprogramowania SW (C)
- ISO 26262 ASIL D
- EN 50128 SW — SIL 4

> [!IMPORTANT]
> Skontaktuj się z nami, aby uzyskać więcej informacji na temat wersji FileX certyfikowanych przez TÜV lub do dostępności raportów testowych, certyfikatów i powiązanej dokumentacji. *

### <a name="ul-certification"></a>Certyfikat UL

FileX został certyfikowany przez UL w celu zapewnienia zgodności z metodą UL 60730-1 w załączniku H, CSA E60730-1 załącznik H, IEC 60730-1 w załączniku H, UL 60335-1 Załącznik R, IEC 603351 w załączniku R, 1998 a w przypadku oprogramowania w składnikach programowalnych. Wraz z IEC/UL 60730-1, które mają wymagania dotyczące "kontrolek wykorzystujących oprogramowanie" w załączniku H, standard IEC 60335-1 opisuje wymagania dotyczące "programowalnych obwodów elektronicznych" w załączniku R. IEC 60730 załącznik H i IEC 60335-1 Załącznik R dotyczy bezpieczeństwa sprzętu i oprogramowania używanego w urządzeniach, takich jak pralki, zmywarki, Dryers, chłodziarks, zamrażarki i Piece.

![C RU US 2](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
>*Skontaktuj się z nami, aby uzyskać więcej informacji na temat wersji FileX zakwalifikowanych przez UL lub do dostępności raportów testowych, certyfikatów i powiązanej dokumentacji.*

## <a name="powerful-services-of-filex"></a>Zaawansowane usługi FileX

### <a name="multiple-media-management"></a>Zarządzanie wieloma nośnikami

FileX może obsługiwać nieograniczoną liczbę nośników fizycznych. Każde wystąpienie nośnika ma własny odrębny obszar pamięci i skojarzony sterownik określony w wywołaniu ***fx_media_open*** . Domyślna dystrybucja FileX odbywa się przy użyciu prostego sterownika nośnika pamięci RAM i systemu demonstracyjnego, który używa tego dysku pamięci RAM.

### <a name="logical-sector-cache"></a>Pamięć podręczna sektora logicznego

Zmniejszając liczbę transferów całego sektora, zarówno do, jak i z nośnika, pamięć podręczna sektora logicznego FileX znacznie zwiększa wydajność. FileX przechowuje pamięć podręczną sektora logicznego dla każdego otwartego nośnika. Głębokość pamięci podręcznej sektora logicznego jest określana na podstawie ilości pamięci dostarczonej do FileX z wywołaniem interfejsu API ***fx_media_open*** .

### <a name="contiguous-file-support"></a>Ciągła obsługa plików

FileX oferuje ciągłą obsługę plików za pomocą usługi interfejsu API ***fx_file_allocate*** w celu usprawnienia i naprawienia czasu dostępu do pliku. Ta procedura pobiera żądaną ilość pamięci i wyszukuje serię sąsiednich klastrów w celu spełnienia żądania. Jeśli takie klastry zostaną znalezione, są wstępnie przydzielone przez nadanie im części łańcucha przyznanych klastrów. Po przeniesieniu nośnika fizycznego FileX obsłudze plików ciągłych skutkuje znaczącym ulepszeniem wydajności i sprawia, że czas dostępu jest deterministyczny.

### <a name="dynamic-creation"></a>Tworzenie dynamiczne

FileX umożliwia dynamiczne tworzenie zasobów systemowych. Jest to szczególnie ważne, jeśli aplikacja ma liczne lub dynamiczne wymagania konfiguracyjne. Ponadto nie ma żadnych ustalonych limitów liczby zasobów FileX, których można użyć (multimediów lub plików). Ponadto liczba obiektów systemu nie ma żadnego wpływu na wydajność.

## <a name="easy-to-use-api"></a>Łatwy w użyciu interfejs API

FileX zapewnia bardzo najlepszą technologię głębokiego systemu plików w sposób łatwy do zrozumienia i łatwego w użyciu. Interfejs programowania aplikacji (API) FileX zapewnia intuicyjną i spójność usług. Nie trzeba odszyfrować usług "zup alfabetów", które są zbyt popularne w przypadku innych systemów plików.

Aby uzyskać pełną listę usług FileX w wersji 5, zobacz [dodatek a](appendix-a.md).

## <a name="exfat-support"></a>Obsługa exFAT

exFAT (rozszerzona tabela alokacji plików) to system plików zaprojektowany przez firmę Microsoft w celu zezwalania na rozmiar pliku na przekroczenie 2 GB, limitu narzuconego przez systemy plików FAT32. Jest to domyślny system plików dla kart SD o pojemności ponad 32 GB. Karty SD lub dyski flash sformatowane przy użyciu formatu FileX exFAT są zgodne z systemem Windows. exFAT obsługuje rozmiar pliku do jednego rozmiaru Exabyte (EB), czyli około 1 000 000 000 GB.

Użytkownicy chcący korzystać z exFAT muszą ponownie skompilować bibliotekę FileX z symbolem ***FX_ENABLE_EXFAT** _ zdefiniowanym. Podczas otwierania nośnika FileX wykrywa typ nośnika. Jeśli nośnik jest sformatowany przy użyciu exFAT, FileX odczytuje i zapisuje system plików zgodnie z normą exFAT. Aby sformatować nowy nośnik przy użyciu exFAT, Użyj usługi _ *_fx_media_exFAT_format_* *. Domyślnie exFAT nie jest włączona.

## <a name="fault-tolerant-support"></a>Obsługa odporna na uszkodzenia

Moduł odporny na uszkodzenia FileX został zaprojektowany, aby zapobiec uszkodzeniu systemu plików spowodowanym przerwami podczas aktualizacji pliku lub katalogu. Na przykład podczas dołączania danych do pliku FileX musi zaktualizować zawartość pliku, wpisu katalogu i prawdopodobnie wpisów FAT. Jeśli ta sekwencja aktualizacji zostanie przerwana (na przykład błąd lub nośnik zostanie wysunięty w trakcie aktualizacji), system plików jest w stanie niespójnym, co może mieć wpływ na integralność całego systemu plików, co prowadzi do uszkodzenia innych plików.

Moduł odporny na uszkodzenia FileX działa przez zapisanie wszystkich kroków wymaganych do zaktualizowania pliku lub katalogu w sposób. Ten wpis dziennika jest przechowywany na nośniku w dedykowanych sektorach (blokach), które FileX mogą znajdować i uzyskiwać dostęp do nich. Dostęp do lokalizacji danych dziennika można uzyskać nawet bez prawidłowego systemu plików. W związku z tym, w przypadku uszkodzenia systemu plików, FileX nadal może znaleźć wpis dziennika i przywrócić system plików z powrotem do dobrego stanu.

Jako plik lub katalog aktualizacji FileX są tworzone wpisy dziennika. Po pomyślnym zakończeniu operacji aktualizacji wpisy dziennika zostaną usunięte. Jeśli wpisy dziennika nie zostały prawidłowo usunięte po pomyślnym zaktualizowaniu pliku, jeśli proces odzyskiwania ustali, że zawartość wpisu dziennika jest zgodna z systemem plików, nic nie musi być gotowe i można oczyścić wpisy dziennika.

W przypadku przerwania operacji aktualizacji systemu plików po następnym zainstalowaniu nośnika przez FileX moduł odporny na błędy analizuje wpisy dziennika. Informacje w wpisach dziennika umożliwiają FileX do wycofania częściowych zmian, które zostały już zastosowane do systemu plików (w przypadku awarii na wczesnym etapie operacji aktualizacji plików) lub jeśli wpisy dziennika zawierają informacje dotyczące ponownego wykonywania, FileX może zastosować zmiany wymagane do ukończenia poprzedniej operacji.

Ta funkcja odporna na błędy jest dostępna dla wszystkich systemów plików FAT obsługiwanych przez FileX, w tym FAT12, FAT16, FAT32 i exFAT. Domyślnie odporny na uszkodzenia nie są włączone w FileX. Aby włączyć funkcję odporną na uszkodzenia, FileX musi być skompilowany przy użyciu symbolu  **FX_ENABLE_FAULT_TOLERANT** i **FX_FAULT_TOLERANT** zdefiniowane. W czasie wykonywania aplikacja uruchamia usługę odporną na uszkodzenia, wywołując **_fx_fault_tolerant_enable_**.
Po uruchomieniu usługi wszystkie operacje zapisu plików i katalogów przechodzą przez moduł odporny na błędy.

Gdy usługa jest odporna na uszkodzenia, najpierw wykrywa, czy nośnik jest chroniony za pomocą modułu odpornego na błędy. Jeśli tak nie jest, FileX zakłada integralność systemu plików i uruchamia ochronę przez przydzielenie bezpłatnych bloków z systemu plików, który ma być używany do rejestrowania i buforowania. W przypadku znalezienia dzienników modułu odpornego na błędy w systemie plików analizowane są wpisy dziennika. FileX przywraca poprzednią operację lub ponownie wykonuje poprzednią operację, w zależności od zawartości wpisów dziennika. System plików jest dostępny po przetworzeniu wszystkich poprzednich wpisów dziennika. Dzięki temu FIleX się od znanego dobrego stanu.

Gdy nośnik jest chroniony za pomocą modułu odpornego na błędy FileX, nośnik nie zostanie zaktualizowany w innym systemie plików. Wykonanie tej operacji spowodowałoby pozostawienie wpisów dziennika w systemie plików, które są niespójne z zawartością w tabeli FAT, wpisu katalogu. Jeśli nośnik został zaktualizowany przez inny system plików przed przeniesieniem go z powrotem do FileX przy użyciu modułu odpornego na błędy, wynik jest niezdefiniowany.

## <a name="callback-functions"></a>Funkcje wywołania zwrotnego

Następujące trzy funkcje wywołania zwrotnego są dodawane do FileX:

- Otwarte wywołanie zwrotne nośnika
- Wywołanie zwrotne zamknięcia nośnika
- Wywołanie zwrotne zapisu pliku

Po zarejestrowaniu funkcje te będą powiadamiać aplikację o wystąpieniu takich zdarzeń.

## <a name="easy-integration"></a>Łatwa integracja

FileX można łatwo zintegrować z praktycznie dowolnym urządzeniem FLASH lub Media. Przenoszenie FileX jest proste. Ten przewodnik zawiera szczegółowy opis procesu, a sterownik pamięci RAM systemu demonstracyjnego sprawia, że jest to bardzo dobre miejsce do uruchomienia.
