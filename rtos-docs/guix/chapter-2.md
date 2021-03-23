---
title: Rozdział 2 — Instalowanie i korzystanie z GUIX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem HighPerformance produktu interfejsu użytkownika GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822296"
---
# <a name="chapter-2---installation-and-use-of-guix"></a><span data-ttu-id="23544-103">Rozdział 2 — Instalowanie i korzystanie z GUIX</span><span class="sxs-lookup"><span data-stu-id="23544-103">Chapter 2 - Installation and Use of GUIX</span></span>

<span data-ttu-id="23544-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem HighPerformance produktu interfejsu użytkownika GUIX.</span><span class="sxs-lookup"><span data-stu-id="23544-104">This chapter contains a description of various issues related to installation, setup, and use of the highperformance user interface product GUIX.</span></span>  

## <a name="host-considerations"></a><span data-ttu-id="23544-105">Zagadnienia dotyczące hosta</span><span class="sxs-lookup"><span data-stu-id="23544-105">Host Considerations</span></span>

<span data-ttu-id="23544-106">Projektowanie osadzone jest zwykle wykonywane na komputerach hostów z systemem Windows lub Linux (UNIX).</span><span class="sxs-lookup"><span data-stu-id="23544-106">Embedded development is usually performed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="23544-107">Gdy aplikacja zostanie skompilowana, połączona, a plik wykonywalny jest generowany na hoście, zostanie pobrany na docelowy sprzęt do wykonania.</span><span class="sxs-lookup"><span data-stu-id="23544-107">After the application is compiled, linked, and the executable is generated on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="23544-108">Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzia deweloperskiego.</span><span class="sxs-lookup"><span data-stu-id="23544-108">Usually the target download is done from within the development tool's debugger.</span></span> <span data-ttu-id="23544-109">Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonania (go, zatrzymania, punktu przerwania itp.) oraz dostęp do rejestrów pamięci i procesora.</span><span class="sxs-lookup"><span data-stu-id="23544-109">After download, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="23544-110">Większość debugerów narzędzi programistycznych komunikuje się z sprzętem docelowym za pośrednictwem połączeń OCD (on-Chip Debug), takich jak JTAG (IEEE 1149,1) i tryb debugowania w tle (BDM).</span><span class="sxs-lookup"><span data-stu-id="23544-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="23544-111">Debugery komunikują się również z sprzętem docelowym za pomocą połączeń In-Circuit Emulation (lodem).</span><span class="sxs-lookup"><span data-stu-id="23544-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="23544-112">Połączenia OCD i lód zapewniają niezawodne rozwiązania z minimalnym dostępem do docelowego oprogramowania rezydentnego.</span><span class="sxs-lookup"><span data-stu-id="23544-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="23544-113">Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy dla GUXI jest dostarczany w formacie ASCII i wymaga około 30 MB miejsca na dysku twardym komputera hosta.</span><span class="sxs-lookup"><span data-stu-id="23544-113">As for resources used on the host, the source code for GUXI is delivered in ASCII format and requires approximately 30 Mbytes of space on the host computer’s hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="23544-114">Zagadnienia dotyczące obiektów docelowych</span><span class="sxs-lookup"><span data-stu-id="23544-114">Target Considerations</span></span>

<span data-ttu-id="23544-115">GUIX wymaga od 5 kilobajtów do 80 Read-Only KB pamięci (ROM) w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="23544-115">GUIX requires between 5 KBytes and 80 Kbytes of Read-Only Memory (ROM) on the target.</span></span> <span data-ttu-id="23544-116">Kolejną 10KBytes pamięci (RAM) obiektu docelowego są wymagane dla stosu wątku GUIX i innych struktur danych globalnych.</span><span class="sxs-lookup"><span data-stu-id="23544-116">Another 5 to 10KBytes of the target’s Random Access Memory (RAM) are required for the GUIX thread stack and other global data structures.</span></span>

<span data-ttu-id="23544-117">Ponadto GUIX wymaga użycia czasomierza ThreadX i obiektu mutex ThreadX.</span><span class="sxs-lookup"><span data-stu-id="23544-117">In addition, GUIX requires the use of a ThreadX timer and a ThreadX mutex object.</span></span> <span data-ttu-id="23544-118">Te urządzenia są używane do okresowego przetwarzania i ochrony wątków wewnątrz GUIX.</span><span class="sxs-lookup"><span data-stu-id="23544-118">These facilities are used for periodic processing needs and thread protection inside GUIX.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="23544-119">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="23544-119">Product Distribution</span></span>

<span data-ttu-id="23544-120">Usługę Azure RTO GUIX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/guix/> .</span><span class="sxs-lookup"><span data-stu-id="23544-120">Azure RTOS GUIX can be obtained from our public source code repository at <https://github.com/azure-rtos/guix/>.</span></span>

<span data-ttu-id="23544-121">Poniżej znajduje się lista ważnych plików wspólnych dla większości dystrybucji produktów:</span><span class="sxs-lookup"><span data-stu-id="23544-121">The following is a list of the important files common to most product distributions:</span></span>

| <span data-ttu-id="23544-122">Nazwa pliku&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="23544-122">Filename&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></span>| <span data-ttu-id="23544-123">Opis</span><span class="sxs-lookup"><span data-stu-id="23544-123">Description</span></span>   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="23544-124">gx_api. h</span><span class="sxs-lookup"><span data-stu-id="23544-124">gx_api.h</span></span>        | <span data-ttu-id="23544-125">Ten plik nagłówkowy C zawiera wszystkie równe systemowe, struktury danych i prototypy usługi.</span><span class="sxs-lookup"><span data-stu-id="23544-125">This C header file contains all system equates, data structures, and service prototypes.</span></span> |
| <span data-ttu-id="23544-126">gx_port. h</span><span class="sxs-lookup"><span data-stu-id="23544-126">gx_port.h</span></span>       | <span data-ttu-id="23544-127">Ten plik nagłówkowy C zawiera wszystkie definicje i struktury danych specyficzne dla określonego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="23544-127">This C header file contains all target-specific and development tool-specific data definitions and structures.</span></span>                                                                                                                                         |
| <span data-ttu-id="23544-128">GX. a (lub GX. lib)</span><span class="sxs-lookup"><span data-stu-id="23544-128">gx.a (or gx.lib)</span></span> | <span data-ttu-id="23544-129">Jest to wersja binarna biblioteki GUIX C.</span><span class="sxs-lookup"><span data-stu-id="23544-129">This is the binary version of the GUIX C library.</span></span> <span data-ttu-id="23544-130">Jest to zwykle kompilowane przez kompilowanie i archiwizowanie dostarczonych plików źródłowych biblioteki GUIX, jednak ta biblioteka może być dostępna w wstępnie skompilowanym formularzu, w zależności od docelowego sprzętu i typu licencji.</span><span class="sxs-lookup"><span data-stu-id="23544-130">This is normally built by compiling and archiving the provided GUIX library source files, however this library may be provided in pre-built form depending on your hardware target and license type.</span></span> |
|

> [!IMPORTANT]
> <span data-ttu-id="23544-131">*Wszystkie pliki są w małych przypadkach, co ułatwia konwertowanie poleceń na platformy deweloperskie systemu Linux (UNIX).*</span><span class="sxs-lookup"><span data-stu-id="23544-131">*All files are in lower-case, making it easy to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="guix-installation"></a><span data-ttu-id="23544-132">Instalacja GUIX</span><span class="sxs-lookup"><span data-stu-id="23544-132">GUIX Installation</span></span>

<span data-ttu-id="23544-133">GUIX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="23544-133">GUIX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="23544-134">Poniżej przedstawiono typową składnię tworzenia klonu repozytorium GUIX na komputerze:</span><span class="sxs-lookup"><span data-stu-id="23544-134">The following is typical syntax for creating a clone of the GUIX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/guix
```

<span data-ttu-id="23544-135">Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="23544-135">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="23544-136">Znajdziesz również instrukcje dotyczące tworzenia biblioteki GUIX na stronie frontonu repozytorium online.</span><span class="sxs-lookup"><span data-stu-id="23544-136">You will also find instructions for building the GUIX library on the front page of the online repository.</span></span>

>[!NOTE]  
> <span data-ttu-id="23544-137">*Oprogramowanie aplikacji musi mieć dostęp do pliku biblioteki GUIX, zazwyczaj o nazwie **GX. a** (lub **GX. lib**) i plików dołączanych C **gx_api. h** i **gx_port. h**. W tym celu należy ustawić odpowiednią ścieżkę dla narzędzi programistycznych lub skopiować te pliki do obszaru projektowania aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="23544-137">*Application software needs access to the GUIX library file, usually called **gx.a** (or **gx.lib**), and the C include files **gx_api.h** and **gx_port.h**. This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area.*</span></span>

## <a name="using-guix"></a><span data-ttu-id="23544-138">Korzystanie z GUIX</span><span class="sxs-lookup"><span data-stu-id="23544-138">Using GUIX</span></span>

<span data-ttu-id="23544-139">Korzystanie z GUIX jest łatwe.</span><span class="sxs-lookup"><span data-stu-id="23544-139">Using GUIX is easy.</span></span> <span data-ttu-id="23544-140">Zasadniczo kod aplikacji musi zawierać ***gx_api. h** _ podczas kompilacji i link z biblioteką GUIX _*_GX. a_\*_ (lub _ *_GX. lib_*) \*.</span><span class="sxs-lookup"><span data-stu-id="23544-140">Basically, the application code must include ***gx_api.h** _ during compilation and link with the GUIX library _*_gx.a_*_ (or _ *_gx.lib_*)*.</span></span>

<span data-ttu-id="23544-141">Do kompilowania aplikacji GUIX są wymagane cztery proste kroki:</span><span class="sxs-lookup"><span data-stu-id="23544-141">There are four easy steps required to build a GUIX application:</span></span>

| <span data-ttu-id="23544-142">Kroki</span><span class="sxs-lookup"><span data-stu-id="23544-142">Steps</span></span>   | <span data-ttu-id="23544-143">Opis</span><span class="sxs-lookup"><span data-stu-id="23544-143">Description</span></span>    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="23544-144">Krok &nbsp; 1:</span><span class="sxs-lookup"><span data-stu-id="23544-144">Step&nbsp;1:</span></span> | <span data-ttu-id="23544-145">Uwzględnij plik ***gx_api. h*** we wszystkich plikach aplikacji, które korzystają z usług GUIX Services lub struktur danych.</span><span class="sxs-lookup"><span data-stu-id="23544-145">Include the ***gx_api.h*** file in all application files that use GUIX services or data structures.</span></span>                                                               |
| <span data-ttu-id="23544-146">Krok &nbsp; 2:</span><span class="sxs-lookup"><span data-stu-id="23544-146">Step&nbsp;2:</span></span> | <span data-ttu-id="23544-147">Zainicjuj system GUIX przez wywołanie ***gx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23544-147">Initialize the GUIX system by calling ***gx_system_initialize** _ from the _ *_tx_application_define_** function or an application thread.</span></span>                       |
| <span data-ttu-id="23544-148">Krok &nbsp; 3.</span><span class="sxs-lookup"><span data-stu-id="23544-148">Step&nbsp;3:</span></span> | <span data-ttu-id="23544-149">Utwórz wystąpienie ekranu, utwórz kanwę do wyświetlania i Utwórz okno główne oraz wszystkie inne wymagane okna lub elementy widget.</span><span class="sxs-lookup"><span data-stu-id="23544-149">Create a display instance, create a canvas for the display, and create the root window and any other windows or widgets necessary.</span></span>                                 |
| <span data-ttu-id="23544-150">Krok &nbsp; 4.</span><span class="sxs-lookup"><span data-stu-id="23544-150">Step&nbsp;4:</span></span> | <span data-ttu-id="23544-151">Skompiluj Źródło aplikacji i połącz je z biblioteką uruchomieniową GUIX \***GX. a** _ (lub _ *_GX. lib_* \*).</span><span class="sxs-lookup"><span data-stu-id="23544-151">Compile application source and link with the GUIX runtime library ***gx.a** _ (or _*_gx.lib_\*\*).</span></span> <span data-ttu-id="23544-152">Obraz wyników można pobrać do elementu docelowego i wykonać!</span><span class="sxs-lookup"><span data-stu-id="23544-152">The resulting image can be downloaded to the target and executed!</span></span> |

## <a name="troubleshooting"></a><span data-ttu-id="23544-153">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="23544-153">Troubleshooting</span></span>

<span data-ttu-id="23544-154">Każdy port GUIX jest dostarczany z aplikacją demonstracyjną, która jest wykonywana na określonym sprzęcie ekranu.</span><span class="sxs-lookup"><span data-stu-id="23544-154">Each GUIX port is delivered with a demonstration application that executes on specific display hardware.</span></span> <span data-ttu-id="23544-155">Ta sama Demonstracja podstawowa jest dostarczana ze wszystkimi wersjami programu GUIX.</span><span class="sxs-lookup"><span data-stu-id="23544-155">The same basic demonstration is delivered with all versions of GUIX.</span></span> <span data-ttu-id="23544-156">Zawsze dobrym pomysłem jest rozpoczęcie pierwszego uruchomienia systemu demonstracyjnego.</span><span class="sxs-lookup"><span data-stu-id="23544-156">It is always a good idea to get the demonstration system running first.</span></span>

<span data-ttu-id="23544-157">Jeśli system demonstracyjny nie działa prawidłowo, wykonaj następujące operacje, aby zawęzić ten problem:</span><span class="sxs-lookup"><span data-stu-id="23544-157">If the demonstration system does not run properly, perform the following operations to narrow the problem:</span></span>

1. <span data-ttu-id="23544-158">Określ, jaka część demonstracji jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="23544-158">Determine how much of the demonstration is running.</span></span>

2. <span data-ttu-id="23544-159">Zwiększenie rozmiaru stosu wątku GUIX przez zmianę stałej czasu kompilacji **GX_THREAD_STACK_SIZE** i ponowne skompilowanie biblioteki GUIX</span><span class="sxs-lookup"><span data-stu-id="23544-159">Increase the stack size of the GUIX thread by changing the  compile-time constant **GX_THREAD_STACK_SIZE** and recompiling  the GUIX library</span></span>

3. <span data-ttu-id="23544-160">Ponownie skompiluj bibliotekę GUIX z odpowiednimi opcjami debugowania wymienionymi w sekcji opcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="23544-160">Recompile the GUIX library with the appropriate debug options listed  in the configuration option section.</span></span>

4. <span data-ttu-id="23544-161">Sprawdzanie stanu powrotu ze wszystkich wywołań interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="23544-161">Examine the return status from all API calls.</span></span>

5. <span data-ttu-id="23544-162">Ustal, czy występuje wewnętrzny błąd systemu przez ustawienie punktu przerwania w funkcji ***_gx_system_error_process***.</span><span class="sxs-lookup"><span data-stu-id="23544-162">Determine if there is an internal system error by setting a breakpoint at the function ***_gx_system_error_process***.</span></span> <span data-ttu-id="23544-163">Kod błędu i obiekt wywołujący powinny dać wskazówki co do tego, co może być błędne.</span><span class="sxs-lookup"><span data-stu-id="23544-163">There error code and caller should give clues as to what might be going wrong.</span></span>

6. <span data-ttu-id="23544-164">Tymczasowo Pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub nie ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="23544-164">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="23544-165">Takie informacje powinny być przydatne dla inżynierów pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="23544-165">Such information should prove useful to Microsoft support engineers.</span></span>

<span data-ttu-id="23544-166">Postępuj zgodnie z procedurami opisanymi w sekcji "czego potrzebujemy", aby wysłać informacje zebrane z kroków rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="23544-166">Follow the procedures outlined in the section titled “What We Need From You” to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="23544-167">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="23544-167">Configuration Options</span></span>

<span data-ttu-id="23544-168">Podczas kompilowania biblioteki GUIX i aplikacji przy użyciu GUIX istnieje kilka opcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="23544-168">There are several configuration options when building the GUIX library and the application using GUIX.</span></span> <span data-ttu-id="23544-169">Te opcje służą do dostrajania rozmiaru biblioteki i zestawu funkcji najlepiej dopasowanego do wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23544-169">These options are used to tune the library size and feature set to best fit your application requirements.</span></span> <span data-ttu-id="23544-170">Na przykład, jeśli aplikacja będzie mieć tylko jeden wątek korzystający z usług interfejsu API GUIX, należy zdefiniować **GX_DISABLE_MULTITHREAD_SUPPORT** flagę konfiguracji, aby wyeliminować obciążenie związane z ochroną krytycznych sekcji kodu z wywłaszczania przez wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="23544-170">For example, if your application will have only one thread utilizing the GUIX API services, the configuration flag **GX_DISABLE_MULTITHREAD_SUPPORT** should be defined to eliminate the overhead associated with protecting critical code sections from pre-emption by multiple threads.</span></span> <span data-ttu-id="23544-171">Różne flagi konfiguracji można definiować w źródle aplikacji, w wierszu polecenia lub w pliku **_gx_user. h_** .</span><span class="sxs-lookup"><span data-stu-id="23544-171">The various configuration flags can be defined in the application source, on the command line, or within the **_gx_user.h_** include file.</span></span>

<span data-ttu-id="23544-172">Za każdym razem, gdy flagi konfiguracji biblioteki GUIX są modyfikowane, należy ponownie skompilować bibliotekę GUIX i moduły aplikacji, aby zmiany konfiguracji zaczęły obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="23544-172">Whenever the GUIX library configuration flags are modified, it is required to rebuild both the GUIX library and your application modules for the configuration changes to take effect.</span></span>

<span data-ttu-id="23544-173">Pełna lista flag konfiguracji została udokumentowana w dodatku H: GUIX Build-Time flagi konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="23544-173">The complete list of configuration flags is documented in Appendix H: GUIX Build-Time Configuration Flags.</span></span>

## <a name="guix-version-id"></a><span data-ttu-id="23544-174">Identyfikator wersji GUIX</span><span class="sxs-lookup"><span data-stu-id="23544-174">GUIX Version ID</span></span>

<span data-ttu-id="23544-175">Bieżąca wersja programu GUIX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="23544-175">The current version of GUIX is available to both the user and the application software during runtime.</span></span> <span data-ttu-id="23544-176">Programista może uzyskać wersję GUIX z badania pliku \***gx_port. h** _.</span><span class="sxs-lookup"><span data-stu-id="23544-176">The programmer can obtain the GUIX version from examination of the \***gx_port.h** _ file.</span></span> <span data-ttu-id="23544-177">Ponadto ten plik zawiera również historię wersji odpowiedniego oprogramowania aplikacji portowej może uzyskać wersję GUIX, badając ciąg globalny _ _ *_gx_version_id_* _ w _ *_gx_port. h_* \*.</span><span class="sxs-lookup"><span data-stu-id="23544-177">In addition, this file also contains a version history of the corresponding port Application software can obtain the GUIX version by examining the global string _ *_ _gx_version_id_* _ in _\*_gx_port.h_\*\*.</span></span>

<span data-ttu-id="23544-178">Oprogramowanie aplikacji może również uzyskać informacje o wersji ze stałych przedstawionych poniżej zdefiniowanych w \***gx_api. h**. \* te stałe określają bieżącą wersję produktu według nazwy i wersję główną i pomocniczą produktu.</span><span class="sxs-lookup"><span data-stu-id="23544-178">Application software can also obtain release information from the constants shown below defined in \***gx_api.h**.\* These constants identify the current product release by name and the product major and minor version.</span></span>

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
