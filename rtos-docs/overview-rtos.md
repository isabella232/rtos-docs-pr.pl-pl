---
title: Co to jest Microsoft Azure RTOS?
description: Azure RTOS to system operacyjny w czasie rzeczywistym (RTOS) dla urządzeń IoT i urządzeń brzegowych obsługiwanych przez mikrokontrolery (MCU).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: b099a5f18accfbe467a2a8fa680c0c76666a9ff3
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754917"
---
# <a name="what-is-microsoft-azure-rtos"></a>Co to jest Microsoft Azure RTOS?

Azure RTOS to system operacyjny w czasie rzeczywistym (RTOS) dla urządzeń Internet rzeczy (IoT) i urządzeń brzegowych obsługiwanych przez mikrokontrolery (MCU). Azure RTOS jest przeznaczony do obsługi najbardziej ograniczonych urządzeń (zasilanych z baterii i mających mniej niż 64 KB pamięci flash).

Azure RTOS jest wstępnie certyfikowany dla różnych standardów bezpieczeństwa. Należą do nich certyfikaty IEC 61508 SIL 4, IEC 62304, klasa C i certyfikaty ASIL D ISO 26262. Azure RTOS ThreadX ma również certyfikat DO-178.

Azure RTOS zapewnia certyfikowane środowisko zabezpieczeń EAL4+ Common Criteria, w tym pełne zabezpieczenia warstwy adresów IP za pośrednictwem protokołu IPsec i zabezpieczenia warstwy gniazd za pośrednictwem protokołu TLS i DTLS. Nasza biblioteka kryptograficzna oprogramowania uzyskała certyfikat FIPS 140-2. Korzystamy również ze sprzętowych funkcji kryptograficznych, ochrony pamięci za pośrednictwem modułów ThreadX i obsługi funkcji zabezpieczeń TrustZone ARMv8-M usługi ARM.

## <a name="components-of-azure-rtos"></a>Składniki Azure RTOS

Platforma Azure RTOS to kolekcja rozwiązań w czasie uruchamiania, w tym Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo i Azure RTOS USBX.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

Azure [RTOS ThreadX](threadx/overview-threadx.md) to zaawansowany Real-Time operacyjny (RTOS) zaprojektowany specjalnie z myślą o aplikacjach głęboko osadzonych. Do wielu korzyści zapewnianych przez Azure RTOS ThreadX należą zaawansowane funkcje planowania, przekazywanie komunikatów, zarządzanie przerwań i usługi obsługi komunikatów. Azure RTOS ThreadX ma wiele zaawansowanych funkcji, w tym architekturę picokernel, planowanie progów wywłaszczania, łańcuch zdarzeń i bogaty zestaw usług systemowych.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure [RTOS FileX](filex/overview-filex.md) to system plików zgodny z fat-fat o wysokiej wydajności. Jest ona w pełni zintegrowana z Azure RTOS ThreadX i jest dostępna dla wszystkich obsługiwanych procesorów. Podobnie jak Azure RTOS ThreadX, Azure RTOS FileX został zaprojektowany tak, aby miał niewielkie rozmiary i wysoką wydajność, dzięki czemu idealnie nadaje się do współczesnych głęboko osadzonych aplikacji, które wymagają operacji na plikach. Azure RTOS FileX obsługuje większość nośników fizycznych, w tym dyski RAM, USBX, SD CARD i pamięci flash NAND/NOR za pośrednictwem Azure RTOS LevelX.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure [RTOS GUIX](guix/overview-guix.md) to profesjonalny graficzny pakiet interfejsu użytkownika, który został utworzony w celu spełnienia potrzeb deweloperów systemów osadzonych. W przeciwieństwie do alternatyw, Azure RTOS GUIX jest mały, szybki i łatwo przenoszony do praktycznie dowolnej konfiguracji sprzętowej, która może obsługiwać graficzne dane wyjściowe. Azure RTOS GUIX oferuje również wyjątkowe wizualne możliwości oraz intuicyjny i zaawansowany interfejs API do tworzenia interfejsów użytkownika na poziomie aplikacji.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure [RTOS NetX](netx/overview-netx.md) to implementacja standardów protokołu TCP/IP o wysokiej wydajności. Jest ona w pełni zintegrowana z Azure RTOS ThreadX i jest dostępna dla wszystkich obsługiwanych procesorów. Azure RTOS NetX ma unikatową architekturę Piconet. W połączeniu z interfejsem API bez kopii doskonale nadaje się do współczesnych głęboko osadzonych aplikacji, które wymagają łączności sieciowej.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure [RTOS NetX](netx-duo/overview-netx-duo.md) Duo to zaawansowane stosy sieciowe TCP/IP klasy przemysłowej zaprojektowane specjalnie z myślą o głęboko osadzonych aplikacjach i aplikacjach IoT w czasie rzeczywistym. Azure RTOS NetX Duo to podwójny stos sieciowy IPv4 i IPv6, natomiast NetX jest oryginalnym stosem sieciowym IPv4, zasadniczo podzbiorem aplikacji Azure RTOS NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure [RTOS USBX](usbx/overview-usbx.md) to wysokiej wydajności host USB, urządzenie i osadzony stos on-the-Go (OTG). Jest ona w pełni zintegrowana z threadX i jest dostępna dla wszystkich procesorów obsługiwanych Azure RTOS ThreadX. Podobnie jak Azure RTOS ThreadX, system Azure RTOS USBX został zaprojektowany tak, aby miał niewielkie rozmiary i wysoką wydajność, dzięki czemu idealnie nadaje się do głęboko osadzonych aplikacji wymagających interfejsu z urządzeniami USB.

### <a name="windows-tools"></a>Windows narzędzi

Program Azure [RTOS GUIX Studio](guix/about-guix-studio.md) zapewnia kompletne środowisko projektowe aplikacji z graficznym interfejsem użytkownika, ułatwiające tworzenie i konserwację wszystkich elementów graficznych w graficznym interfejsie użytkownika aplikacji. Azure RTOS GUIX Studio automatycznie generuje kod C zgodny z biblioteką Azure RTOS GUIX, gotowy do skompilowania i uruchomienia na komputerze docelowym.

Azure [RTOS TraceX](tracex/overview-tracex.md) to oparte na hoście narzędzie do analizy, które udostępnia deweloperom graficzny widok zdarzeń systemowych w czasie rzeczywistym oraz umożliwia im wizualizowanie i lepsze zrozumienie zachowania systemów w czasie rzeczywistym.

## <a name="the-azure-rtos-advantage"></a>Zaleta Azure RTOS
Azure RTOS zapewnia następujące korzyści w związku z innymi systemami operacyjnymi czasu rzeczywistego.

### <a name="most-deployed-rtos"></a>Najczęściej wdrożony system RTOS

Azure RTOS ma ponad 6,2 miliarda wdrożeń na całym świecie, zgodnie z wiodącą firmą analizy rynku M2M, VDC Research. Popularność tej Azure RTOS jest ogromną zaletą niezawodności, jakości, rozmiaru, wydajności, zaawansowanych funkcji, łatwości użycia i ogólnych zalet czasu do rynku.

> *"Obserwowaliśmy trajektorię rozwoju THREADX na rynkach bezprzewodowych i IoT od momentu jej rozwoju i jesteśmy coraz bardziej pod wrażeniem powszechnego przyjęcia technologii THREADX w branży".* — Chris Rommel, wiceprezes ds. badań VDC

### <a name="intuitive-and-consistent-api-design"></a>Intuicyjny i spójny projekt interfejsu API

* Intuicyjny i spójny interfejs API.
* Konwencja nazewnictwa rzeczowników.
* Wszystkie interfejsy API mają prefiks wiodący, taki *jak tx_* dla ThreadX i fx_ *dla* FileX, aby łatwo zidentyfikować składnik Azure RTOS, do którego należą.
* Spójność funkcjonalna w interfejsach API. Na przykład wszystkie funkcje interfejsu API, które wstrzymują, mają opcjonalny limit czasu, który działa w identyczny sposób.
* Wiele interfejsów API jest dostępnych bezpośrednio od isr aplikacji.
- Opcjonalne wywołania zwrotne powiadomień użytkownika dla operacji na nośnikach i plikach.
* Model programowania sterowanego zdarzeniami (API).

### <a name="high-efficiency"></a>Wysoka wydajność

- Niewielkie zużycie kodu.
- Skalowalne zużycie kodu na podstawie używanych usług.
- Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304, klasa C, ISO 26262 ASIL D i EN 50128 SW-SIL4.
- Szybkie wykonywanie. Azure RTOS została zaprojektowana pod kątem szybkości i ma minimalne warstwy wywołań funkcji wewnętrznych, aby pomóc w osiągnięciu najszybszej możliwej wydajności.

### <a name="fastest-time-to-market"></a>Najszybszy czas na rynek

Azure RTOS instalować, uczyć się, używać, debugować, weryfikować, certyfikować i konserwować. W związku z tym Azure RTOS jest jednym z najpopularniejszych systemów operacyjnych czasu rzeczywistego dla osadzonych urządzeń IoT, w tym wielu socs z Broadcom, Gainspan itd. Nasza spójna przewaga czasu na rynku jest zbudowana na:

* Pełna dostępność kodu źródłowego.
* Łatwy w użyciu interfejs API.
* Kompleksowy i zaawansowany zestaw funkcji.
* Dokumentacja dotycząca jakości.

### <a name="one-simple-license"></a>Jedna prosta licencja

Nie ma żadnych kosztów użycia i testowania kodu źródłowego ani kosztów licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. Wszystkie inne urządzenia potrzebują prostej rocznej licencji.

### <a name="full-highest-quality-source-code"></a>Pełny kod źródłowy najwyższej jakości

Na przestrzeni lat Azure RTOS kodu źródłowego ustawiał słupki jakości i łatwości zrozumienia. Ponadto konwencja posiadania jednej funkcji na plik zapewnia łatwą nawigację w źródle.

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>Wstępnie certyfikowane przez firmę TUV i UL pod wieloma standardami bezpieczeństwa

Azure RTOS ma certyfikat SGS-TUV Saar do użycia w systemach o krytycznym znaczeniu dla bezpieczeństwa, zgodnie z normami IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D i EN 50128. Certyfikat potwierdza, że system Azure RTOS może być używany podczas opracowywania oprogramowania związanego z bezpieczeństwem dla najwyższych poziomów integralności bezpieczeństwa IEC-61508, IEC-62304, ISO 26262 i EN 50128 dla "Bezpieczeństwa funkcjonalnego systemów elektronicznych, elektronicznych i programowalnych systemów elektronicznych związanych z bezpieczeństwem". Firma SGS-TUV Saar, która została formowana za pośrednictwem wspólnej osady niemieckich firm SGS-Group i TUV Saarland, stała się wiodącą akredytowaną, niezależną firmą do testowania, inspekcji, weryfikowania i certyfikowania osadzonego oprogramowania dla systemów powiązanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które z niego pochodzą, w tym IEC-62304, ISO 26262 i EN 50128, są używane w celu zapewnienia bezpieczeństwa funkcjonalnego urządzeń elektronicznych, elektronicznych i programowalnych urządzeń medycznych związanych z bezpieczeństwem, systemów sterowania procesami, maszyn przemysłowych, samochodów i systemów sterowania urządzeniami mechanicznymi.

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="Certyfikacja SGS-TUV":::

Azure RTOS została uznana przez firmę UL za zgodność z normami UL 60730-1 H, CSA E60730-1, H, IEC 60730-1, H, UL 60335-1 Wan R, IEC 60335-1 Standardy bezpieczeństwa oprogramowania w programowalnych elementach. UL to globalna, niezależna firma z zakresu bezpieczeństwa i nauki, mająca ponad stu lat wiedzy na temat wprowadzania innowacji w rozwiązaniach bezpieczeństwa, od publicznego przyjęcia energii elektrycznej do przełomów w zakresie zrównoważonego rozwoju, energii elektrycznej i energii elektrycznej.

:::image type="content" source="media/cru-logo-certification.png" alt-text="Certyfikacja CRU UL":::

Artifacts (certyfikat, podręcznik bezpieczeństwa, raport testowy itp.) skojarzony z certyfikatami TUV i UL są dostępne do sprzedaży.

W przypadkach, gdy aplikacja wymaga dodatkowej certyfikacji, usługa certyfikacji jest dostępna za pośrednictwem firmy Microsoft w celu zapewnienia kluczowych certyfikatów dla różnych standardów przy użyciu rzeczywistej platformy sprzętowej, a nawet obejmujących kod aplikacji. Skontaktuj się z nami, aby uzyskać więcej informacji na temat naszej usługi certyfikacji.

### <a name="eal4-common-criteria-security-certification"></a>Certyfikacja zabezpieczeń EAL4+ Common Criteria

Azure RTOS uzyskał certyfikat zabezpieczeń EAL4+ Common Criteria. Temat Target of Evaluation (TOE) obejmuje Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS i Azure RTOS NetX MQTT. Reprezentuje to najbardziej typowe protokoły IoT wymagane przez głęboko osadzone czujniki, urządzenia, routery brzegowe i bramy.

:::image type="content" source="media/eal-logo-certification.png" alt-text="Certyfikacja EAL":::

Obiekt oceny zabezpieczeń IT używany do certyfikacji zabezpieczeń Microsoft Azure RTOS SC to Brightsight ISO, a urząd certyfikacji to SERTIT.

### <a name="fips-140-2-validated"></a>Zweryfikowane przez fips 140-2

Azure RTOS Biblioteki kryptograficzne uzyskały certyfikat Federal Information Processing Standardization 140-2 (FIPS 140-2) dla oprogramowania, który określa wymagania dotyczące modułów kryptograficznych. Standard FIPS 140-2 wymaga, aby wszystkie federalne agencje rządowe i działy, które korzystają z zabezpieczeń opartych na kryptografii, spełniały określone standardy związane z siłę i możliwościami szyfrowania. Te kryptograficzne standardy zabezpieczeń są również uznawane w Kanadzie i Unii Europejskiej.

Laboratorium oceny zabezpieczeń informacji używane dla bibliotek kryptograficznych Azure RTOS atsec, a urząd certyfikacji to National [Institute of Standards and Technology (NIST).](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)

### <a name="supports-most-popular-architectures"></a>Obsługuje najpopularniejsze architektury

Azure RTOS na najpopularniejszych 32/64-bitowych mikroprocesorach, które są już w pełni przetestowane i w pełni obsługiwane, w tym następujące architektury zaawansowane.

- **Urządzenia analogiczne:** SHARC, Blackfin, CM4xx

- **Andes Core:** RISC-V

- **Ambiqmicro:** Mikrojądki mcu

- **ARM:** ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitowy/R4/R5, TrustZone ARMv8-M

- **Cadence**: Xtensa, Diamond

- **CZKI:** PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

- **Ksess**: RISC-V

- **EnSilica**: eSi-RISC

- **Infineon:** XMC1000, XMC4000, TriCore

- **Intel; Intel FPGA:** x36/Pentium, XScale, NIOS II, Bystron, Arria 10

- **Microchip:** AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

- **Microsemi**: RISC-V

- **NXP:** LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

- **Renesas**: SH, HS, V850, RX, RZ, Koder

- **Silicon Labs:** EFM32

- **Synopsys:** ARC 600, 700, ARC EM, ARC HS

- **ST:** STM32, ARM7, ARM9, Cortex-M3/M4/M7

- **Tl**: C5xxx, C6xxx, Byris, Sitara, Tiva-C

- **Przetwarzanie** falowe: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

- **Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Wszystkie wymienione wartości chronometrażu i rozmiaru są szacowane i mogą się różnić na platformie dewelopera.*

## <a name="in-the-context-of-azure-iot"></a>W kontekście usługi Azure IoT

Oprócz bezpośredniego łączenia się z usługą Azure IoT lub pośrednio nawiązywania połączenia za pośrednictwem usługi Azure IoT Edge Azure RTOS są również dostępne na Azure Sphere urządzeniach. Połączenie tych Azure RTOS i Azure Sphere zapewnia najlepsze w swojej klasie przetwarzanie i zabezpieczenia w czasie rzeczywistym na jednym urządzeniu.
