---
title: Co to jest Microsoft Azure RTOS?
description: Azure RTOS to system operacyjny w czasie rzeczywistym (RTOS) dla urządzeń IoT i urządzeń brzegowych obsługiwanych przez mikrokontrolery (MCU).
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: c902289b487c439da4ef5138319fe09d74a2347f
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171279"
---
# <a name="what-is-microsoft-azure-rtos"></a>Co to jest Microsoft Azure RTOS?

Azure RTOS to system operacyjny w czasie rzeczywistym (RTOS) dla urządzeń Internet rzeczy (IoT) i urządzeń brzegowych obsługiwanych przez mikrokontrolery (MCU). Azure RTOS jest przeznaczony do obsługi najbardziej ograniczonych urządzeń (zasilanych z baterii i mających mniej niż 64 KB pamięci flash).

Azure RTOS jest wstępnie certyfikowany dla różnych standardów bezpieczeństwa. Należą do nich certyfikaty IEC 61508 SIL 4, IEC 62304, klasa C i certyfikaty ASIL D ISO 26262. Azure RTOS ThreadX ma również certyfikat DO-178.

Azure RTOS zapewnia certyfikowane środowisko zabezpieczeń EAL4+ Common Criteria, w tym pełne zabezpieczenia warstwy adresów IP za pośrednictwem protokołu IPsec i zabezpieczenia warstwy gniazd za pośrednictwem protokołu TLS i DTLS. Nasza biblioteka kryptograficzna oprogramowania uzyskała certyfikat FIPS 140-2. Korzystamy również ze sprzętowych funkcji kryptograficznych, ochrony pamięci za pośrednictwem modułów ThreadX i obsługi funkcji zabezpieczeń TrustZone ARMv8-M usługi ARM.

## <a name="components-of-azure-rtos"></a>Składniki Azure RTOS

Platforma Azure RTOS to kolekcja rozwiązań w czasie uruchamiania, w tym Azure RTOS ThreadX, Azure RTOS FileX, Azure RTOS GUIX, Azure RTOS NetX, Azure RTOS NetX Duo i Azure RTOS USBX.

### <a name="azure-rtos-threadx"></a>Azure RTOS ThreadX

System ThreadX usługi Azure RTOS to zaawansowany system operacyjny czasu rzeczywistego zaprojektowany specjalnie pod kątem głęboko osadzonych aplikacji. Do wielu korzyści zapewnianych przez Azure RTOS ThreadX należą zaawansowane funkcje planowania, przekazywanie komunikatów, zarządzanie przerwań i usługi obsługi komunikatów. Azure RTOS ThreadX ma wiele zaawansowanych funkcji, w tym architekturę picokernel, planowanie progów wywłaszczania, łańcuch zdarzeń i bogaty zestaw usług systemowych.

### <a name="azure-rtos-filex"></a>Azure RTOS FileX

Azure RTOS FileX to system plików zgodny z fat-fat o wysokiej wydajności. Jest ona w pełni zintegrowana z Azure RTOS ThreadX i jest dostępna dla wszystkich obsługiwanych procesorów. Podobnie jak Azure RTOS ThreadX, Azure RTOS FileX został zaprojektowany tak, aby miał niewielkie rozmiary i wysoką wydajność, dzięki czemu idealnie nadaje się do współczesnych głęboko osadzonych aplikacji, które wymagają operacji na plikach. Azure RTOS FileX obsługuje większość nośników fizycznych, w tym pamięci RAM, USBX, SD CARD i pamięci flash NAND/NOR za pośrednictwem Azure RTOS LevelX.

### <a name="azure-rtos-guix"></a>Azure RTOS GUIX

Azure RTOS GUIX to profesjonalny graficzny pakiet interfejsu użytkownika, utworzony w celu spełnienia potrzeb deweloperów systemów osadzonych. W przeciwieństwie do alternatyw, Azure RTOS GUIX jest mały, szybki i łatwo przenoszony do praktycznie dowolnej konfiguracji sprzętowej, która może obsługiwać graficzne dane wyjściowe. Azure RTOS GUIX oferuje również wyjątkowe wizualne możliwości oraz intuicyjny i zaawansowany interfejs API do tworzenia interfejsów użytkownika na poziomie aplikacji.

### <a name="azure-rtos-netx"></a>Azure RTOS NetX

Azure RTOS NetX to implementacja standardów protokołu TCP/IP o wysokiej wydajności. Jest w pełni zintegrowany z Azure RTOS ThreadX i jest dostępny dla wszystkich obsługiwanych procesorów. Azure RTOS NetX ma unikatową architekturę Piconet. W połączeniu z interfejsem API bez kopii doskonale nadaje się do współczesnych głęboko osadzonych aplikacji, które wymagają łączności sieciowej.

### <a name="azure-rtos-netx-duo"></a>Azure RTOS NetX Duo

Azure RTOS NetX Duo to zaawansowane stosy sieciowe TCP/IP klasy przemysłowej zaprojektowane specjalnie z myślą o głęboko osadzonych aplikacjach i aplikacjach IoT w czasie rzeczywistym. Azure RTOS NetX Duo to podwójny stos sieciowy IPv4 i IPv6, a NetX jest oryginalnym stosem sieciowym IPv4, zasadniczo podzbiorem aplikacji Azure RTOS NetX Duo.

### <a name="azure-rtos-usbx"></a>Azure RTOS USBX

Azure RTOS USBX to wysokiej wydajności host USB, urządzenie i osadzony stos on-the-Go (OTG). Jest w pełni zintegrowany z ThreadX i jest dostępny dla wszystkich procesorów obsługiwanych Azure RTOS ThreadX. Podobnie jak Azure RTOS ThreadX, Azure RTOS USBX został zaprojektowany tak, aby mieć niewielkie rozmiary i wysoką wydajność, dzięki czemu idealnie nadaje się do głęboko osadzonych aplikacji wymagających interfejsu z urządzeniami USB.

### <a name="windows-tools"></a>Narzędzia systemu Windows

Azure RTOS GUIX Studio zapewnia kompletne środowisko projektowe aplikacji z graficznym interfejsem użytkownika, ułatwiające tworzenie i konserwację wszystkich elementów graficznych w graficznym interfejsie użytkownika aplikacji. Azure RTOS GUIX Studio automatycznie generuje kod C zgodny z biblioteką Azure RTOS GUIX, gotowy do skompilowania i uruchomienia na komputerze docelowym.

Azure RTOS TraceX to oparte na hoście narzędzie do analizy, które udostępnia deweloperom graficzny widok zdarzeń systemowych w czasie rzeczywistym oraz umożliwia im wizualizowanie i lepsze zrozumienie zachowania systemów w czasie rzeczywistym.

## <a name="the-azure-rtos-advantage"></a>Zaleta Azure RTOS
Azure RTOS zapewnia następujące korzyści w związku z innymi systemami operacyjnymi czasu rzeczywistego.

### <a name="intuitive-and-consistent-api-design"></a>Intuicyjny i spójny projekt interfejsu API

* Intuicyjny i spójny interfejs API.
* Konwencja nazewnictwa rzeczowników.
* Wszystkie interfejsy API mają prefiks wiodący, taki *jak tx_* dla ThreadX i nx_ *dla* FileX, aby łatwo zidentyfikować Azure RTOS, do którego należą.
* Interfejsy API blokowania mają opcjonalny limit czasu wątku
* Wiele interfejsów API jest dostępnych bezpośrednio od isr aplikacji.
- Opcjonalne wywołania zwrotne powiadomień użytkownika dla operacji na nośnikach i plikach.
* Model programowania sterowanego zdarzeniami (API).

### <a name="high-efficiency"></a>Wysoka wydajność

- Niewielkie zużycie kodu.
- Skalowalne zużycie kodu na podstawie używanych usług.
- Wstępnie certyfikowane przez TUV i UL do IEC 61508 SIL 4, IEC 62304, klasa C, ISO 26262 ASIL D i EN 50128 SW-SIL4.
- Szybkie wykonywanie.

### <a name="fastest-time-to-market"></a>Najszybszy czas na rynek

Azure RTOS instalować, uczyć się, używać, debugować, weryfikować, certyfikować i konserwować. W związku z tym Azure RTOS jest jednym z najpopularniejszych systemów operacyjnych czasu rzeczywistego dla osadzonych urządzeń IoT, w tym wielu socs z Broadcom, Gainspan itd. Nasza spójna przewaga czasu na rynku jest zbudowana na:

* Pełna dostępność kodu źródłowego.
* Łatwy w użyciu interfejs API.
* Kompleksowy i zaawansowany zestaw funkcji.

### <a name="one-simple-license"></a>Jedna prosta licencja

Nie ma żadnych kosztów używania i testowania kodu źródłowego ani kosztów licencji produkcyjnych w przypadku wdrożenia na wstępnie licencjonowanych urządzeniach. Wszystkie inne urządzenia potrzebują prostej rocznej licencji.

### <a name="full-highest-quality-source-code"></a>Pełny kod źródłowy najwyższej jakości

Na przestrzeni lat Azure RTOS kodu źródłowego ustawiła poprzegę jakości i łatwości zrozumienia. Ponadto konwencja posiadania jednej funkcji na plik zapewnia łatwą nawigację źródła.

### <a name="pre-certified-by-tuv-and-ul-to-many-safety-standards"></a>Wstępnie certyfikowane przez tuv i UL według wielu standardów bezpieczeństwa

Azure RTOS ma certyfikat SGS-TUV Saar do użycia w systemach krytycznych pod względami bezpieczeństwa, zgodnie z normami IEC-61508 SIL 4, IEC-62304 SW Safety Class C, ISO 26262 ASIL D i EN 50128. Certyfikat potwierdza, że system Azure RTOS może być używany w rozwoju oprogramowania związanego z bezpieczeństwem dla najwyższych poziomów integralności bezpieczeństwa IEC-61508, IEC-62304, ISO 26262 i EN 50128 dla "Bezpieczeństwa funkcjonalnego systemów elektronicznych, elektronicznych i programowalnych systemów elektronicznych". Firma SGS-TUV Saar, która została uformowana za pośrednictwem wspólnej firmy SGS-Group i TuV Saarland w Niemczech, stała się wiodącą akredytowaną, niezależną firmą do testowania, inspekcji, weryfikowania i certyfikowania osadzonego oprogramowania dla systemów powiązanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508 i wszystkie standardy, które z niego pochodzą, w tym IEC-62304, ISO 26262 i EN 50128, są używane w celu zapewnienia bezpieczeństwa funkcjonalnego urządzeń elektronicznych, elektronicznych i programowalnych elektronicznych urządzeń medycznych, systemów sterowania procesami, maszyn przemysłowych, samochodów i systemów sterujących.

:::image type="content" source="media/partener-logo-sgs-tuv-saar.png" alt-text="Certyfikacja SGS-TUV":::

Azure RTOS przez firmę UL za zgodność z normami UL 60730-1 (H, CSA E60730-1) H, IEC 60730-1, H, UL 60335-1 Wmów R, IEC 60335-1 i UL 1998, standardy bezpieczeństwa oprogramowania w programowalnych elementach. UL to globalna, niezależna firma z zakresu bezpieczeństwa i nauki, mająca ponad stu lat wiedzy na temat wprowadzania innowacji w rozwiązaniach bezpieczeństwa, od publicznego przyjęcia energii elektrycznej po przełomy w zakresie trwałości, energii elektrycznej i energii elektrycznej.

:::image type="content" source="media/cru-logo-certification.png" alt-text="Certyfikacja CRU UL":::

Artefakty (certyfikat, podręcznik bezpieczeństwa, raport testowy itp.) skojarzone z certyfikatami TUV i UL są dostępne do sprzedaży.

W przypadkach, gdy aplikacja wymaga dodatkowej certyfikacji, za pośrednictwem firmy Microsoft jest dostępna usługa certyfikacji, która zapewnia kluczową certyfikację dla różnych standardów przy użyciu rzeczywistej platformy sprzętowej, a nawet obejmuje kod aplikacji. Skontaktuj się z nami, aby uzyskać więcej informacji na temat naszej usługi certyfikacji.

### <a name="eal4-common-criteria-security-certification"></a>Certyfikacja zabezpieczeń EAL4+ Common Criteria

Azure RTOS uzyskał certyfikat zabezpieczeń EAL4+ Common Criteria. Temat Target of Evaluation (TOE) obejmuje Azure RTOS ThreadX, Azure RTOS NetX Duo, Azure RTOS NetX Secure TLS i Azure RTOS NetX MQTT. To najbardziej typowe protokoły IoT wymagane przez głęboko osadzone czujniki, urządzenia, routery brzegowe i bramy.

:::image type="content" source="media/eal-logo-certification.png" alt-text="Certyfikacja EAL":::

Obiekt oceny zabezpieczeń IT używany na Microsoft Azure zabezpieczeń RTOS SC to Brightsight JEDNOSTKI, a urząd certyfikacji to SERTIT.

### <a name="fips-140-2-validated"></a>Zweryfikowane w fips 140-2

Azure RTOS bibliotek kryptograficznych uzyskały certyfikat Federal Information Processing Standardization 140-2 (FIPS 140-2) dla oprogramowania, który określa wymagania dotyczące modułów kryptograficznych. Standard FIPS 140-2 wymaga, aby wszystkie federalne agencje rządowe i działy, które używają zabezpieczeń opartych na kryptografii, spełniały określone standardy dotyczące siły i możliwości szyfrowania. Te kryptograficzne standardy zabezpieczeń są również uznawane w Kanadzie i Unii Europejskiej.

Laboratorium oceny zabezpieczeń informacji używane dla bibliotek Azure RTOS Crypto było atsec, a urząd certyfikacji to National [Institute of Standards and Technology (NIST).](https://csrc.nist.gov/projects/cryptographic-module-validation-program/Certificate/3394)

### <a name="supports-most-popular-architectures"></a>Obsługuje najpopularniejsze architektury

Azure RTOS na najpopularniejszych 32/64-bitowych mikroprocesorach, które są już w pełni przetestowane i w pełni obsługiwane, w tym następujące architektury zaawansowane:

**Urządzenia analogiczne:** SHARC, Blackfin, CM4xx

**Andes Core:** RISC-V

**Ambiqmicro:** Mikrojądki mcu

**ARM:** ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitowy/R4/R5, TrustZone ARMv8-M

**Cadence**: Xtensa, Diamond

**CZKI:** PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi

**Ksess**: RISC-V

**EnSilica**: eSi-RISC

**Infineon:** XMC1000, XMC4000, TriCore

**Intel; Intel FPGA:** x36/Pentium, XScale, NIOS II, Bystron, Arria 10

**Microchip:** AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32

**Microsemi**: RISC-V

**NXP:** LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: SH, HS, V850, RX, RZ, Koder

**Silicon Labs:** EFM32

**Synopsys:** ARC 600, 700, ARC EM, ARC HS

**ST:** STM32, ARM7, ARM9, Cortex-M3/M4/M7

**Tl**: C5xxx, C6xxx, Byris, Sitara, Tiva-C

**Przetwarzanie** falowe: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class

**Xilinx:** MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE

*Wszystkie wymienione wartości chronometrażu i rozmiaru są szacowane i mogą się różnić na platformie dewelopera.*

## <a name="in-the-context-of-azure-iot"></a>W kontekście usługi Azure IoT

Oprócz bezpośredniego łączenia się z usługą Azure IoT lub pośredniego nawiązywania połączenia za pośrednictwem Azure IoT Edge Azure RTOS są również dostępne na Azure Sphere urządzeniach. Połączenie tych Azure RTOS i Azure Sphere zapewnia najlepsze w swojej klasie przetwarzanie i zabezpieczenia w czasie rzeczywistym na jednym urządzeniu.
