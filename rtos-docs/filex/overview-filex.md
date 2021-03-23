---
title: Opis usługi Azure RTO FileX
description: Usługa Azure RTO FileX to system plików zgodny z tabelą alokacji plików (FAT), który jest w pełni zintegrowany z platformą Azure RTO ThreadX i jest dostępny dla wszystkich obsługiwanych procesorów. Podobnie jak w przypadku platformy Azure RTO ThreadX, usługa Azure RTO FileX została zaprojektowana tak, aby miała niewielki rozmiar i wysoką wydajność, dzięki czemu jest idealnym rozwiązaniem dla współczesnych aplikacji, które wymagają operacji zarządzania plikami. Usługa FileX obsługuje większość nośników fizycznych, w tym pamięci RAM, Azure RTO USBX, SD CARD i ni/lub Flash pamiątk za pośrednictwem platformy Azure RTO LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823226"
---
# <a name="overview-of-azure-rtos-filex"></a>Omówienie usługi Azure RTO FileX

Usługa Azure RTO FileX Embedded File System to zaawansowane, przemysłowe rozwiązanie do oceny plików Microsoft FAT, zaprojektowane specjalnie pod kątem głęboko osadzonych, w czasie rzeczywistym i aplikacji IoT. Usługa Azure RTO FileX obsługuje wszystkie formaty plików firmy Microsoft, w tym FAT12, FAT16, FAT32 i exFAT. Usługa FileX oferuje również opcjonalną odporność na uszkodzenia i możliwość nanoszenia poziomu zużycia w środowisku FLASH za pośrednictwem produktu dodatkowego o nazwie [Azure RTO LevelX](https://docs.microsoft.com/azure/rtos/levelx/). Wszystkie te połączone z małym wpływem, szybkim wykonywaniem i najbardziej łatwym w obsłużeniu, dzięki czemu usługa Azure RTO FileX idealny wybór dla najbardziej wymagających osadzonych aplikacji IoT.

## <a name="api-protocols"></a>Protokoły interfejsu API

### <a name="azure-rtos-filex-api"></a>Interfejs API usługi Azure RTO FileX

- Intuicyjny i spójny interfejs API
- W konwencji nazewnictwa czasowników
- Wszystkie interfejsy API mają wiodące *fx_* do łatwej identyfikacji jako FileX
- Blokowanie interfejsów API ma opcjonalny limit czasu wątku
- Opcjonalne wywołania zwrotne powiadomień użytkownika dla operacji multimedialnych i plików
- Aby uzyskać więcej informacji, zobacz [Podręcznik użytkownika usługi Azure RTO FileX](about-this-guide.md) .

### <a name="media-services"></a>Media Services

- Obsługa systemu FAT 12/16/32 i exFAT
- Minimalna 6KB FLASH, 2,5 KB pamięci RAM
- Ukończ usługi dostępu do multimediów
- Nieograniczona liczba wystąpień multimediów
- Prosty interfejs sterownika sektora logicznego odczytu/zapisu
- Obsługa wielu partycji
- Pamięć podręczna sektora logicznego
- Pamięć podręczna wejścia systemu FAT
- Opcjonalna obsługa odporności na uszkodzenia
- Odroczona aktualizacja dodatkowego systemu FAT
- Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
- Intuicyjne interfejsy API dostępu do multimediów, w tym:
  - fx_media_open
  - fx_media_close
  - fx_media_format
  - fx_media_space_available

### <a name="directory-services"></a>Usługi katalogowe

- Do 256 ścieżek bajtów
- Liczba obsługiwanych nazw katalogów Long i 8,3
- Utwórz katalog & usunąć
- Nawigacja i przechodzenie katalogu
- Zarządzanie atrybutami katalogu
- Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
- Intuicyjne interfejsy API dostępu do katalogów, w tym:
  - fx_directory_create
  - fx_directory_delete
  - fx_directory_attributes_set
  - fx_directory_attributes_read
  - fx_directory_first_entry_find
  - fx_directory_next_entry_find

### <a name="file-services"></a>Usługi plików

- Minimum 3.3 KB FLASH
- Nieograniczona liczba otwartych plików
- Pliki tylko do odczytu mogą być otwierane wiele razy
- Liczba obsługiwanych nazw katalogów Long i 8,3
- Ciągła obsługa plików
- Logika szybkiego wyszukiwania
- Wstępne przydzielanie klastrów
- Tworzenie, usuwanie i zmienianie nazwy pliku
- Odczyt, zapis i przeglądanie plików
- Zarządzanie atrybutami plików
- Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX
- Intuicyjne interfejsy API dostępu do plików, w tym:
  - fx_file_create
  - fx_file_delete
  - fx_file_attributes_set
  - fx_file_attributes_read
  - fx_file_read
  - fx_file_seek
  - fx_file_write

## <a name="small-footprint"></a>Niewielkie rozmiary

W przypadku usługi Azure RTO FileX Embedded File System istnieje niezwykle mała ilość miejsca na 8,6 KB do 12 KB w przypadku podstawowej obsługi odczytu i zapisu w pliku. Minimalne użycie pamięci RAM usługi Azure RTO FileX jest w kolejności od 1,8 KB do jednego wystąpienia nośnika i tylko z pamięcią podręczną "512-Byte" sektora logicznego. Podobnie jak w przypadku usługi Azure RTO ThreadX, rozmiar usługi Azure RTO FileX jest automatycznie skalowany w oparciu o usługi używane przez aplikację. To praktycznie eliminuje konieczność skomplikowanej konfiguracji i kompilacji parametrów, co ułatwia deweloperom.

## <a name="fast-execution"></a>Szybkie wykonywanie

Usługa Azure RTO FileX udostępnia pamięć podręczną sektora logicznego, a także pamięć podręczną wpisów FAT. Oba te rozmiary są kontrolowane bezpośrednio przez aplikację. Ponadto usługa Azure RTO FileX zapewnia ciągłą alokację klastra i bezpośrednie odczytywanie i zapisywanie kolejnych klastrów. Żądania odczytu/zapisu całego sektora są wykonywane bezpośrednio między buforem aplikacji a nośnikiem — to oznacza, że nie jest wykonywane pośrednie buforowanie. Wszystkie te i ogólne zasady projektowania zorientowane na wydajność ułatwiają platformie Azure RTO FileX osiąganie najszybszej możliwej wydajności.

## <a name="advanced-technology"></a>Technologia zaawansowana

Usługa Azure RTO FileX to zaawansowana technologia, w tym następujące.

- Obsługa systemu FAT 12/16/32 i exFAT
- Obsługa wielu partycji
- Automatyczne skalowanie
- Neutralne
- Długa nazwa pliku i obsługa 8,3
- Opcjonalna obsługa odporności na uszkodzenia
- Pamięć podręczna sektora logicznego
- Pamięć podręczna wejścia systemu FAT
- Wstępne przydzielanie klastrów
- Ciągła obsługa plików
- Opcjonalne metryki wydajności
- Obsługa analizy systemu Azure RTO TraceX

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a>NIE NIj na bilansowanie (Azure RTO LevelX)

Usługa Azure RTO LevelX jest produktem firmy Microsoft, a nie ni FLASH. Usługi Azure RTO LevelX można używać w połączeniu z FileX lub jako autonomiczną, bezpośrednią biblioteką sektora FLASH do odczytu/zapisu dla aplikacji.

## <a name="fastest-time-to-market"></a>Najszybszy czas wprowadzenia na rynek

Usługa Azure RTO FileX umożliwia łatwe instalowanie, uczenie się, używanie, debugowanie, weryfikowanie, certyfikowanie i konserwowanie. W związku z tym usługa Azure RTO FileX jest jednym z najpopularniejszych systemów plików FAT dla osadzonych urządzeń IoT. Poniżej przedstawiono kilka powodów, dla których spójny czas wprowadzenia na rynek:

- Dokumentacja dotycząca jakości — zapoznaj się z naszym [podręcznikiem użytkownika usługi Azure RTO FileX](about-this-guide.md) i zapoznaj się z Tobą.
- Ukończ dostępność kodu źródłowego
- Łatwy w użyciu interfejs API
- Kompleksowy i zaawansowany zestaw funkcji

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a>Wstępnie certyfikowane przez TUV i UL do wielu standardów bezpieczeństwa

![MOIMI — TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

Usługa Azure RTO FileX została certyfikowana przez moimi-TUV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC-61508 SIL 4, IEC-62304, Klasa bezpieczeństwa SW, ISO 26262 ASIL D i EN 50128. Certyfikat potwierdza, że FileX może być używany podczas opracowywania oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności zabezpieczeń IEC-61508, IEC-62304, ISO 26262 i EN 50128 na potrzeby "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem". MOIMI-TUV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TUV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, weryfikowania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508, a także wszystkie standardy, które są od niego pochodzące, w tym IEC-62304, ISO 26262 i EN 50128, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego urządzenia medycznego związanego z bezpieczeństwem, systemów kontroli procesów, maszyn przemysłowych, samochodów i systemów kontroli szynowej.

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="CRU certyfikat UL":::

Usługa Azure RTO FileX została rozpoznana przez UL w celu zapewnienia zgodności z metodą UL 60730-1 w załączniku H, CSA E60730-1 w załączniku H, IEC 60730-1 w załączniku H, UL 60335-1 załączniku R, IEC 60335-1 w załączniku R i normach bezpieczeństwa UL 1998 dla oprogramowania w składnikach programowalnych. UL to globalna, niezależna firma zajmująca się ochroną bezpieczeństwa, która ma więcej niż wiek fachowych rozwiązań w zakresie bezpieczeństwa, od publicznego wdrożenia energii elektrycznej, aby nawiązać przełom w zakresie trwałości, odnawialnych energii i nanotechnologii.

Artefakty (certyfikat, Podręcznik bezpieczeństwa, raport testowy itp.) skojarzone z certyfikatami TUV i UL są dostępne do sprzedaży.

W przypadku, gdy aplikacja wymaga dodatkowej certyfikacji, usługa certyfikacji jest dostępna w firmie Microsoft w celu zapewnienia certyfikacji klucza dla różnych standardów przy użyciu rzeczywistej platformy sprzętowej, a nawet w odniesieniu do kodu aplikacji.

## <a name="one-simple-license"></a>Jedna prosta licencja

Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.

## <a name="full-highest-quality-source-code"></a>Pełny kod źródłowy o najwyższej jakości

W ciągu lat FileX kod źródłowy ustawił na pasku jakość i łatwość interpretacji. Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.

## <a name="supports-most-popular-architectures"></a>Obsługuje najpopularniejsze architektury

Usługa Azure RTO FileX działa na najpopularniejszych mikroprocesorach 32-bitowych, w pełni przetestowanych i w pełni obsługiwanych, w tym:

**Urządzenia analogowe**: SHARC, Blackfin, CM4xx

**Andes rdzeń**: RISC-V

**Ambiqmicro**: Apollo MCUs

**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Erze**: Xtensa, romb

**Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi

**Cypress**: RISC-V

**EnSilica**: ESI-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel**; **Intel FPGA**: X36/Pentium, XScale, Nios II, Cyclone, Arria 10

**Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32

**Mikrośrednik**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: sh, HS, V850, RX, rz, synergia

**Krzem** Labs: EFM32

**SynopSYS**: Arc 600, 700, łuk em, łuk HS

**St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C

**Przetwarzanie Wave**: MIPS32 4K, 24 k, 34 k, 1004 k, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Wszystkie wymienione wartości chronometrażu i rozmiaru są szacunkami i mogą być inne na platformie deweloperskiej.*
