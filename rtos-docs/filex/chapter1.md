---
title: Rozdział 1 — Wprowadzenie do Azure RTOS FileX
description: Azure RTOS FileX to kompletny nośnik w formacie FAT i system zarządzania plikami dla aplikacji głęboko osadzonych.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 48fab21d78ede88e84db11a4f30574ce2061d145820b819ec7846203e297f42a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782978"
---
# <a name="chapter-1---introduction-to-azure-rtos-filex"></a>Rozdział 1 — Wprowadzenie do Azure RTOS FileX

Azure RTOS FileX to kompletny nośnik w formacie FAT i system zarządzania plikami dla aplikacji głęboko osadzonych. W tym rozdziale oprowadzono plik FileX, opisujący jego aplikacje i korzyści.

## <a name="filex-unique-features"></a>Unikatowe funkcje pliku FileX

Azure RTOS FileX obsługuje nieograniczoną liczbę urządzeń multimedialnych jednocześnie, w tym dyski RAM, menedżery FLASH i rzeczywiste urządzenia fizyczne. Obsługuje 12-, 16- i 32-bitowe formaty tabeli alokacji plików (FAT), a także obsługuje rozszerzoną tabelę alokacji plików (exFAT), ciągłą alokację plików i jest wysoce zoptymalizowana pod kątem rozmiaru i wydajności. FileX obejmuje również obsługę odporności na uszkodzenia, otwieranie/zamykanie nośnika oraz funkcje wywołania zwrotnego zapisu plików.

Zaprojektowany z myślą o zaspokajania rosnącej potrzeby urządzeń FLASH, plik FileX używa tych samych metod projektowania i kodowania co ThreadX. Podobnie jak wszystkie produkty firmy Microsoft, plik FileX jest dystrybuowany z pełnym kodem źródłowym ANSI C i nie ma żadnych opłat licencyjnych w czasie rzeczywistym.

### <a name="product-highlights"></a>Najważniejsze informacje o produkcie

- Pełna obsługa procesora ThreadX
- Bez opłat licencyjnych
- Uzupełnij kod źródłowy ANSI C
- Wydajność w czasie rzeczywistym
- Elastyczna pomoc techniczna
- Nieograniczona liczba obiektów FileX (nośników, katalogów i plików)
- Dynamiczne tworzenie/usuwanie obiektów FileX
- Elastyczne użycie pamięci
- Rozmiar jest skalowany automatycznie
- Mały rozmiar obszaru instrukcji (do 6 KB): 6–30 000
- Pełna integracja z threadX
- Neutralność endianowa
- Łatwe do zaimplementowania sterowniki We/Wy FileX
- Obsługa 12-, 16-i 32-bitowego fat
- Obsługa exFAT
- Obsługa długich nazw plików
- Wewnętrzna pamięć podręczna wpisów FAT
- Obsługa nazw Unicode
- Ciągła alokacja plików
- Odczyt/zapis kolejnych sektorów i klastra
- Wewnętrzna pamięć podręczna sektora logicznego
- Pokaz dysków PAMIĘCI RAM jest już wytłaniany
- Możliwość formatowania multimediów
- Wykrywanie i odzyskiwanie błędów
- Opcje odporności na uszkodzenia
- Wbudowane statystyki wydajności
- Obsługa autonomiczna (brak Azure RTOS)

## <a name="safety-certifications"></a>Certyfikaty bezpieczeństwa

### <a name="tv-certification"></a>Certyfikacja TÜV

System FileX ma certyfikat SGS-TÜV Saar do użycia w systemach o krytycznym znaczeniu dla bezpieczeństwa, zgodnie z normami IEC-61508 i IEC-62304. Certyfikat potwierdza, że plik FileX może być używany do opracowywania oprogramowania związanego z bezpieczeństwem dla najwyższych poziomów integralności bezpieczeństwa systemów Międzynarodowa Komisja Elektrotechniczna (IEC) 61508 i IEC 62304 dla "bezpieczeństwa funkcjonalnego systemów elektronicznych, elektronicznych i programowalnych systemów związanych z bezpieczeństwem elektronicznym". SGS-TÜV Saar, utworzone za pośrednictwem wspólnej osady niemieckich firm SGS-Group i TÜV Saarland, stała się wiodącą akredytowaną, niezależną firmą do testowania, inspekcji, weryfikowania i certyfikowania osadzonego oprogramowania dla systemów powiązanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które z niego pochodzą, w tym IEC 62304, są używane w celu zapewnienia bezpieczeństwa funkcjonalnego urządzeń elektronicznych, elektronicznych i programowalnych urządzeń medycznych związanych z bezpieczeństwem, systemów sterowania procesami, maszyn przemysłowych i systemów sterowania węzłem.

SGS-TÜV Saar ma certyfikat FileX, który może być używany w krytycznych dla bezpieczeństwa systemach samochodowych zgodnie ze standardem ISO 26262. Ponadto plik FileX ma certyfikat ASIL D (Safety Integrity Level) dla branży samochodowych, który reprezentuje najwyższy poziom certyfikacji ISO 26262.

Ponadto firma SGS-TÜV Saar ma certyfikat FileX, który może być używany w aplikacjach do transportu o krytycznym znaczeniu dla bezpieczeństwa, zgodnie ze standardem EN 50128 i zgodnie ze standardem SW-SIL 4.

![Logo SGS TUV Saar](./media/user-guide/sgs-tuv-saar-logo.png)

- IEC 61508 do SIL 4
- IEC 62304 do bezpieczeństwa SW, klasa C
- ISO 26262 ASIL D
- EN 50128 SW-SIL 4

> [!IMPORTANT]
> Skontaktuj się z nami, aby uzyskać więcej informacji na temat wersji plików FileX certyfikowanych przez firmę TÜV lub dostępności raportów testowych, certyfikatów i skojarzonej dokumentacji.*

### <a name="ul-certification"></a>Certyfikacja UL

FileX został certyfikowany przez firmę UL do zgodności z normami UL 60730-1, CsA E60730-1, H, IEC 60730-1, H, UL 60335-1 Wdowy R, IEC 603351 I UL 1998, standardy bezpieczeństwa oprogramowania w programowalnych elementach. Wraz z IEC/UL 60730-1 który ma wymagania dotyczące "kontrolek korzystających z oprogramowania" w załączniku H, standard IEC 60335-1 opisuje wymagania dotyczące "programowalnych obwodów elektronicznych" w załączniku R. IEC 60730, załącznik H i IEC 60335-1 Dokument R dotyczy bezpieczeństwa sprzętu i oprogramowania MCU używanego w urządzeniach, takich jak maszyny nagie, nagie, lodówki, chłodziarki i pąki.

![C RU US 2](./media/user-guide/c-ru-us-logo.png)

*UL/IEC 60730, UL/IEC 60335, UL 1998*

> [!IMPORTANT]
>*Skontaktuj się z nami, aby uzyskać więcej informacji na temat wersji plików FileX, które zostały certyfikowane przez firmę UL, lub w celu dostępności raportów testowych, certyfikatów i skojarzonej dokumentacji.*

## <a name="powerful-services-of-filex"></a>Zaawansowane usługi FileX

### <a name="multiple-media-management"></a>Zarządzanie wieloma nośnikami

Plik FileX może obsługiwać nieograniczoną liczbę nośników fizycznych. Każde wystąpienie nośnika ma własny odrębny obszar pamięci i skojarzony sterownik określony w ***wywołaniu fx_media_open*** pamięci. Domyślna dystrybucja pliku FileX jest dostarczany z prostym sterownikem multimediów RAM i systemem pokazowym, który używa tego dysku RAM.

### <a name="logical-sector-cache"></a>Pamięć podręczna sektora logicznego

Dzięki zmniejszeniu liczby transferów całych sektorów, zarówno do nośnika, jak i z nośnika, pamięć podręczna sektora logicznego FileX znacznie zwiększa wydajność. Plik FileX utrzymuje pamięć podręczną sektora logicznego dla każdego otwartego nośnika. Głębokość pamięci podręcznej sektora logicznego zależy od ilości pamięci dostarczonej do pliku FileX za pomocą wywołania ***fx_media_open*** API.

### <a name="contiguous-file-support"></a>Obsługa ciągłych plików

Plik FileX oferuje ciągłą obsługę plików za pośrednictwem interfejsu API ***fx_file_allocate,*** aby poprawić i sprawić, że czas dostępu do plików będzie deterministyczny. Ta procedura pobiera żądaną ilość pamięci i wyszukuje serię sąsiednich klastrów w celu spełnienia żądania. Jeśli takie klastry zostaną znalezione, są one wstępnie przydzielane przez ich część łańcucha przydzielonych klastrów w pliku. W przypadku przenoszenia nośnika fizycznego obsługa plików ciągłych FileX znacznie poprawia wydajność i sprawia, że czas dostępu jest deterministyczny.

### <a name="dynamic-creation"></a>Tworzenie dynamiczne

FileX umożliwia dynamiczne tworzenie zasobów systemowych. Jest to szczególnie ważne, jeśli aplikacja ma wiele wymagań dotyczących konfiguracji dynamicznej. Ponadto nie ma wstępnie określonych limitów liczby zasobów FileX, których można użyć (multimediów lub plików). Ponadto liczba obiektów systemowych nie ma żadnego wpływu na wydajność.

## <a name="easy-to-use-api"></a>Łatwy w użyciu interfejs API

FileX zapewnia najlepszą technologię głęboko osadzonego systemu plików w sposób, który jest łatwy do zrozumienia i użycia. Interfejs programowania aplikacji FileX (API) sprawia, że usługi są intuicyjne i spójne. Nie trzeba odszyfrowyć usług "alfabetu", które są zbyt popularne w innych systemach plików.

Aby uzyskać pełną listę usług FileX w wersji 5, zobacz [dodatek A](appendix-a.md).

## <a name="exfat-support"></a>Obsługa exFAT

ExFAT (rozszerzona tabela alokacji plików) to system plików zaprojektowany przez firmę Microsoft w celu umożliwienia przekroczenia 2 GB rozmiaru pliku, czyli limitu narzuconego przez systemy plików FAT32. Jest to domyślny system plików dla kart SD o pojemności ponad 32 GB. Karty SD lub dyski flash sformatowane w formacie FileX exFAT są zgodne z Windows. ExFAT obsługuje rozmiar pliku do jednego eksabajta (EB), czyli około miliarda GB.

Użytkownicy, którzy chcą korzystać z usługi exFAT, muszą ponownie skompilować bibliotekę FileX z symbolem ***FX_ENABLE_EXFAT** _defined. Podczas otwierania nośnika plik FileX wykrywa typ nośnika. Jeśli nośnik jest sformatowany za pomocą exFAT, plik FileX odczytuje i zapisuje system plików zgodnie ze standardem exFAT. Aby sformatować nowy nośnik za pomocą funkcji exFAT, użyj usługi _*_fx_media_exFAT_format_**. Domyślnie funkcja exFAT nie jest włączona.

## <a name="fault-tolerant-support"></a>Obsługa odporności na uszkodzenia

Moduł odporności na błędy FileX zaprojektowano tak, aby zapobiegać uszkodzeniem systemu plików spowodowanym przerwami w działaniu podczas aktualizacji pliku lub katalogu. Na przykład podczas dołączania danych do pliku plik FileX musi zaktualizować zawartość pliku, wpis katalogu i prawdopodobnie wpisy FAT. Jeśli ta sekwencja aktualizacji zostanie przerwana (na przykład przerwy w zasilaniu lub nośnik zostanie wysucony w trakcie aktualizacji), system plików jest w niespójnym stanie, co może mieć wpływ na integralność całego systemu plików, co prowadzi do uszkodzenia innych plików.

Moduł odporności na błędy FileX działa przez rejestrowanie wszystkich kroków wymaganych do zaktualizowania pliku lub katalogu po drodze. Ten wpis dziennika jest przechowywany na nośniku w dedykowanych sektorach (blokach), do których plik FileX może znaleźć plik i uzyskać do niego dostęp. Dostęp do lokalizacji danych dziennika można uzyskać nawet bez odpowiedniego systemu plików. W związku z tym w przypadku uszkodzenia systemu plików fileX nadal może znaleźć wpis dziennika i przywrócić system plików do dobrego stanu.

Podczas aktualizacji pliku lub katalogu FileX tworzone są wpisy dziennika. Po pomyślnym zakończeniu operacji aktualizacji wpisy dziennika są usuwane. Jeśli wpisy dziennika nie zostały prawidłowo usunięte po pomyślnej aktualizacji pliku, jeśli proces odzyskiwania ustali, że zawartość we wpisie dziennika pasuje do systemu plików, nie trzeba nic robić, a wpisy dziennika można wyczyścić.

Jeśli operacja aktualizacji systemu plików została przerwana, przy następnym instalacji nośnika przez plik FileX moduł odporności na uszkodzenia analizuje wpisy dziennika. Informacje we wpisach dziennika umożliwiają plikowi FileX tworzenie kopii zapasowej częściowych zmian już zastosowanych do systemu plików (na wypadek awarii na wczesnym etapie operacji aktualizacji pliku) lub jeśli wpisy dziennika zawierają informacje dotyczące ponownego działania, system FileX może zastosować zmiany wymagane do zakończenia poprzedniej operacji.

Ta funkcja odporności na uszkodzenia jest dostępna dla wszystkich systemów plików FAT obsługiwanych przez system FileX, w tym FAT12, FAT16, FAT32 i exFAT. Domyślnie funkcja odporności na uszkodzenia nie jest włączona w pliku FileX. Aby włączyć funkcję tolerancji błędów, plik FileX musi być sbudowaną z  **FX_ENABLE_FAULT_TOLERANT** i **FX_FAULT_TOLERANT** zdefiniowany. W czasie uruchamiania aplikacja uruchamia usługę tolerancji błędów, wywołując **_fx_fault_tolerant_enable_**.
Po uruchamianiu usługi wszystkie operacje zapisu plików i katalogów są wykonywane w module z tolerancją błędów.

W trakcie uruchamiania usługi z tolerancją błędów najpierw wykrywa, czy nośnik jest chroniony w ramach modułu odporności na uszkodzenia. Jeśli tak nie jest, system FileX zakłada integralność systemu plików i rozpoczyna ochronę przez przydzielenie wolnych bloków z systemu plików do rejestrowania i buforowania. Jeśli dzienniki modułu odporności na błędy zostaną znalezione w systemie plików, przeanalizuje wpisy dziennika. PlikX przywraca poprzednią operację lub przywraca poprzednią operację w zależności od zawartości wpisów dziennika. System plików staje się dostępny po przetworzeniu wszystkich poprzednich wpisów dziennika. Gwarantuje to, że FIleX zaczyna od znanego dobrego stanu.

Gdy nośnik jest chroniony w module odporności na błędy FileX, nośnik nie zostanie zaktualizowany przy użyciu innego systemu plików. Takie zachowanie pozostawi wpisy dziennika w systemie plików niespójne z zawartością w tabeli FAT, wpis katalogu. Jeśli nośnik zostanie zaktualizowany przez inny system plików przed przeniesieniem go z powrotem do pliku FileX z modułem odporności na uszkodzenia, wynik będzie niezdefiniowany.

## <a name="callback-functions"></a>Funkcje wywołania zwrotnego

Następujące trzy funkcje wywołania zwrotnego są dodawane do pliku FileX:

- Wywołanie zwrotne otwierania multimediów
- Wywołanie zwrotne zamknięcia nośnika
- Wywołanie zwrotne zapisu pliku

Po zarejestrowaniu te funkcje powiadomią aplikację, gdy wystąpią takie zdarzenia.

## <a name="easy-integration"></a>Łatwa integracja

Plik FileX można łatwo zintegrować z praktycznie dowolnym urządzeniem FLASH lub urządzeniem multimedialnym. Przenoszenie pliku FileX jest proste. W tym przewodniku szczegółowo opisano proces, a sterownik pamięci RAM systemu demonstracyjnego sprawia, że jest to bardzo dobre miejsce do rozpoczęcia!
