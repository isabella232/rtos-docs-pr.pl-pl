---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO ThreadX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem jądra usługi Azure RTO ThreadX o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1bf85d363b07c81f226d494107eae9ba18114a7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821360"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a><span data-ttu-id="4d9d7-103">Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="4d9d7-103">Chapter 2 - Installation and Use of Azure RTOS ThreadX</span></span>

<span data-ttu-id="4d9d7-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem jądra usługi Azure RTO ThreadX o wysokiej wydajności.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-104">This chapter contains a description of various issues related to installation, setup, and usage of the high-performance Azure RTOS ThreadX kernel.</span></span>

## <a name="host-considerations"></a><span data-ttu-id="4d9d7-105">Zagadnienia dotyczące hosta</span><span class="sxs-lookup"><span data-stu-id="4d9d7-105">Host Considerations</span></span>

<span data-ttu-id="4d9d7-106">Oprogramowanie osadzone jest zazwyczaj opracowywane na komputerach hostów z systemem Windows lub Linux (UNIX).</span><span class="sxs-lookup"><span data-stu-id="4d9d7-106">Embedded software is usually developed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="4d9d7-107">Gdy aplikacja zostanie skompilowana, połączona i umieszczona na hoście, zostanie pobrana na docelowy sprzęt do wykonania.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="4d9d7-108">Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzi programistycznych.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-108">Usually the target download is done from within the development tool debugger.</span></span> <span data-ttu-id="4d9d7-109">Po zakończeniu pobierania debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonywania (go, zatrzymania, punktu przerwania itp.) oraz dostęp do rejestrów pamięci i procesora.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-109">After the download has completed, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="4d9d7-110">Większość debugerów narzędzi programistycznych komunikuje się z sprzętem docelowym za pośrednictwem połączeń OCD (on-Chip Debug), takich jak JTAG (IEEE 1149,1) i tryb debugowania w tle (BDM).</span><span class="sxs-lookup"><span data-stu-id="4d9d7-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="4d9d7-111">Debugery komunikują się również z sprzętem docelowym za pomocą połączeń In-Circuit Emulation (lodem).</span><span class="sxs-lookup"><span data-stu-id="4d9d7-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="4d9d7-112">Połączenia OCD i lód zapewniają niezawodne rozwiązania z minimalnym dostępem do docelowego oprogramowania rezydentnego.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="4d9d7-113">Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy dla ThreadX jest dostarczany w formacie ASCII i wymaga około 1 MB miejsca na dysku twardym komputera hosta.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-113">As for resources used on the host, the source code for ThreadX is delivered in ASCII format and requires approximately 1 MByte of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="4d9d7-114">Zagadnienia dotyczące obiektów docelowych</span><span class="sxs-lookup"><span data-stu-id="4d9d7-114">Target Considerations</span></span>

<span data-ttu-id="4d9d7-115">ThreadX wymaga od 2 kilobajtów do 20 kilobajtów pamięci tylko do odczytu (ROM) w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-115">ThreadX requires between 2 KBytes and 20 KBytes of Read Only Memory (ROM) on the target.</span></span> <span data-ttu-id="4d9d7-116">Wymaga również od 1 do 2 KB pamięci RAM docelowego (Random Access Memory) dla stosu systemu ThreadX i innych globalnych struktur danych.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-116">It also requires another 1 to 2 KBytes of the target's Random Access Memory (RAM) for the ThreadX system stack and other global data structures.</span></span>

<span data-ttu-id="4d9d7-117">W przypadku funkcji związanych z czasomierzem, takich jak limity czasu wywołań usługi, wyróżnianie czasu i czasomierze aplikacji do działania, podstawowy sprzęt docelowy musi dostarczyć okresowe Źródło przerwań.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-117">For timer-related functions like service call time-outs, time-slicing, and application timers to function, the underlying target hardware must provide a periodic interrupt source.</span></span> <span data-ttu-id="4d9d7-118">Jeśli procesor ma tę możliwość, jest używany przez ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-118">If the processor has this capability, it is utilized by ThreadX.</span></span> <span data-ttu-id="4d9d7-119">W przeciwnym razie, jeśli procesor docelowy nie ma możliwości wygenerowania okresowego przerwania, sprzęt użytkownika musi go udostępnić.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-119">Otherwise, if the target processor does not have the ability to generate a periodic interrupt, the user's hardware must provide it.</span></span> <span data-ttu-id="4d9d7-120">Instalacja i konfiguracja przerwania czasomierza zwykle znajduje się w pliku zestawu ***tx_initialize_low_level*** w dystrybucji ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-120">Setup and configuration of the timer interrupt is typically located in the ***tx_initialize_low_level*** assembly file in the ThreadX distribution.</span></span>

> [!NOTE]
> <span data-ttu-id="4d9d7-121">*ThreadX nadal działa nawet wtedy, gdy nie jest dostępne żadne okresowe Źródło przerwań czasomierza. Jednak żadna z usług związanych z czasomierzem nie działa.*</span><span class="sxs-lookup"><span data-stu-id="4d9d7-121">*ThreadX is still functional even if no periodic timer interrupt source is available. However, none of the timer-related services are functional.*</span></span>

## <a name="product-distribution"></a><span data-ttu-id="4d9d7-122">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="4d9d7-122">Product Distribution</span></span>

<span data-ttu-id="4d9d7-123">Usługę Azure RTO ThreadX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/threadx/> .</span><span class="sxs-lookup"><span data-stu-id="4d9d7-123">Azure RTOS ThreadX can be obtained from our public source code repository at <https://github.com/azure-rtos/threadx/>.</span></span>

<span data-ttu-id="4d9d7-124">Poniżej znajduje się lista kilku ważnych plików w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-124">The following is a list of several important files in the repository.</span></span>

| <span data-ttu-id="4d9d7-125">Nazwa pliku</span><span class="sxs-lookup"><span data-stu-id="4d9d7-125">Filename</span></span> | <span data-ttu-id="4d9d7-126">Opis</span><span class="sxs-lookup"><span data-stu-id="4d9d7-126">Description</span></span> |
|------------------- | ----------- |
| <span data-ttu-id="4d9d7-127">**tx_api. h**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-127">**tx_api.h**</span></span>                      | <span data-ttu-id="4d9d7-128">Plik nagłówkowy języka C zawierający wszystkie równe systemowe, struktury danych i prototypy usługi.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-128">C header file containing all system equates, data structures, and service prototypes.</span></span>                                                             |
| <span data-ttu-id="4d9d7-129">**tx_port. h**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-129">**tx_port.h**</span></span>                     | <span data-ttu-id="4d9d7-130">Plik nagłówkowy języka C zawierający wszystkie definicje i targetspecific danych.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-130">C header file containing all development-tool and targetspecific data definitions and structures.</span></span>                                                 |
| <span data-ttu-id="4d9d7-131">**demo_threadx. c**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-131">**demo_threadx.c**</span></span>                | <span data-ttu-id="4d9d7-132">Plik C zawierający małą aplikację demonstracyjną.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-132">C file containing a small demo application.</span></span>                                                                                                       |
| <span data-ttu-id="4d9d7-133">**TX. a (lub TX. lib)**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-133">**tx.a (or tx.lib)**</span></span>              | <span data-ttu-id="4d9d7-134">Wersja binarna biblioteki ThreadX C, która jest dystrybuowana z pakietem *standardowym* .</span><span class="sxs-lookup"><span data-stu-id="4d9d7-134">Binary version of the ThreadX C library that is distributed with the *standard* package.</span></span>                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
><span data-ttu-id="4d9d7-135">*Wszystkie nazwy plików są w małych przypadkach. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy deweloperskie systemu Linux (UNIX).*</span><span class="sxs-lookup"><span data-stu-id="4d9d7-135">*All file names are in lower-case. This naming convention makes it easier to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="threadx-installation"></a><span data-ttu-id="4d9d7-136">Instalacja ThreadX</span><span class="sxs-lookup"><span data-stu-id="4d9d7-136">ThreadX Installation</span></span>

<span data-ttu-id="4d9d7-137">ThreadX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-137">ThreadX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="4d9d7-138">Poniżej przedstawiono typową składnię tworzenia klonu repozytorium ThreadX na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-138">The following is typical syntax for creating a clone of the ThreadX repository on your PC.</span></span>

```c
    git clone https://github.com/azure-rtos/threadx
```

<span data-ttu-id="4d9d7-139">Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-139">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="4d9d7-140">Znajdziesz również instrukcje dotyczące tworzenia biblioteki ThreadX na stronie frontonu repozytorium online.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-140">You will also find instructions for building the ThreadX library on the front page of the online repository.</span></span>

> [!NOTE]
> <span data-ttu-id="4d9d7-141">\* Oprogramowanie aplikacji wymaga dostępu do pliku biblioteki ThreadX (zazwyczaj **TX. a** lub **TX. lib**) oraz plików C include **_tx_api. h_* _ i _*_tx_port. h_\*_.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-141">*Application software needs access to the ThreadX library file (usually **tx.a** or **tx.lib**) and the C include files **_tx_api.h_* _ and _*_tx_port.h_*_.</span></span> <span data-ttu-id="4d9d7-142">W tym celu należy ustawić odpowiednią ścieżkę dla narzędzi programistycznych lub skopiować te pliki do area._ tworzenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="4d9d7-142">This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area._</span></span>

## <a name="using-threadx"></a><span data-ttu-id="4d9d7-143">Korzystanie z ThreadX</span><span class="sxs-lookup"><span data-stu-id="4d9d7-143">Using ThreadX</span></span>

<span data-ttu-id="4d9d7-144">Aby użyć ThreadX, kod aplikacji musi zawierać znak ***tx_api. h** _ podczas kompilacji i link do biblioteki wykonawczej ThreadX _*_TX. a_\*_ (lub _ *_TX. lib_* \*).</span><span class="sxs-lookup"><span data-stu-id="4d9d7-144">To use ThreadX, the application code must include ***tx_api.h** _ during compilation and link with the ThreadX run-time library _*_tx.a_*_ (or _*_tx.lib_\*\*).</span></span>

<span data-ttu-id="4d9d7-145">Do skompilowania aplikacji ThreadX wymagane są cztery kroki.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-145">There are four steps required to build a ThreadX application.</span></span>

1. <span data-ttu-id="4d9d7-146">Uwzględnij plik ***tx_api. h*** we wszystkich plikach aplikacji, które korzystają z usług ThreadX Services lub struktur danych.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-146">Include the ***tx_api.h*** file in all application files that use ThreadX services or data structures.</span></span>

1. <span data-ttu-id="4d9d7-147">Utwórz funkcję standard C \***Main** _.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-147">Create the standard C \***main** _ function.</span></span> <span data-ttu-id="4d9d7-148">Ta funkcja musi ostatecznie wywołać _ \*_tx_kernel_enter_\*\*, aby rozpocząć ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-148">This function must eventually call _ *_tx_kernel_enter_*\* to start ThreadX.</span></span> <span data-ttu-id="4d9d7-149">Przed wprowadzeniem jądra można dodać inicjalizację specyficzną dla aplikacji, która nie obejmuje ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-149">Application-specific initialization that does not involve ThreadX may be added prior to entering the kernel.</span></span>

      > [!IMPORTANT]
      > <span data-ttu-id="4d9d7-150">\* Funkcja ThreadX entry \***tx_kernel_enter** _ nie zwraca.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-150">\*The ThreadX entry function \***tx_kernel_enter** _ does not return.</span></span> <span data-ttu-id="4d9d7-151">Dlatego nie należy umieszczać żadnego wywołania ani wywołań funkcji po it._</span><span class="sxs-lookup"><span data-stu-id="4d9d7-151">So be sure not to place any processing or function calls after it._</span></span>

1. <span data-ttu-id="4d9d7-152">Utwórz funkcję ***tx_application_define*** .</span><span class="sxs-lookup"><span data-stu-id="4d9d7-152">Create the ***tx_application_define*** function.</span></span> <span data-ttu-id="4d9d7-153">Jest to miejsce, w którym są tworzone początkowe zasoby systemowe.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-153">This is where the initial system resources are created.</span></span> <span data-ttu-id="4d9d7-154">Przykładami zasobów systemowych są wątki, kolejki, Pule pamięci, grupy flag zdarzeń, muteksy i semafory.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-154">Examples of system resources include threads, queues, memory pools, event flags groups, mutexes, and semaphores.</span></span>

1. <span data-ttu-id="4d9d7-155">Skompiluj Źródło aplikacji i połącz ją z biblioteką wykonawczą ThreadX. ***lib***.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-155">Compile application source and link with the ThreadX run-time library ***tx.lib***.</span></span> <span data-ttu-id="4d9d7-156">Obraz wyników można pobrać do elementu docelowego i wykonać!</span><span class="sxs-lookup"><span data-stu-id="4d9d7-156">The resulting image can be downloaded to the target and executed!</span></span>

## <a name="small-example-system"></a><span data-ttu-id="4d9d7-157">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="4d9d7-157">Small Example System</span></span>

<span data-ttu-id="4d9d7-158">Mały przykładowy system na rysunku 1 pokazuje tworzenie pojedynczego wątku z priorytetem 3.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-158">The small example system in Figure 1 shows the creation of a single thread with a priority of 3.</span></span> <span data-ttu-id="4d9d7-159">Wątek wykonuje, zwiększa licznik, a następnie uśpienia dla jednego zegara.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-159">The thread executes, increments a counter, then sleeps for one clock tick.</span></span>
<span data-ttu-id="4d9d7-160">Ten proces kontynuuje się bez ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-160">This process continues forever.</span></span>

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

<span data-ttu-id="4d9d7-161">**RYSUNEK 1. Szablon opracowywania aplikacji**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-161">**FIGURE 1. Template for Application Development**</span></span>

<span data-ttu-id="4d9d7-162">Chociaż jest to prosty przykład, zapewnia dobry szablon do rzeczywistego opracowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-162">Although this is a simple example, it provides a good template for real application development.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="4d9d7-163">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="4d9d7-163">Troubleshooting</span></span>

<span data-ttu-id="4d9d7-164">Każdy port ThreadX jest dostarczany z aplikacją demonstracyjną.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-164">Each ThreadX port is delivered with a demonstration application.</span></span> <span data-ttu-id="4d9d7-165">Zawsze dobrym pomysłem jest uzyskanie uruchomionego systemu demonstracyjnego — na rzeczywistym sprzęcie docelowym lub symulowanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-165">It is always a good idea to first get the demonstration system running—either on actual target hardware or simulated environment.</span></span>

<span data-ttu-id="4d9d7-166">Jeśli system demonstracyjny nie działa prawidłowo, poniżej przedstawiono niektóre wskazówki dotyczące rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-166">If the demonstration system does not execute properly, the following are some troubleshooting tips.</span></span>

1. <span data-ttu-id="4d9d7-167">Określ, jaka część demonstracji jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-167">Determine how much of the demonstration is running.</span></span>
1. <span data-ttu-id="4d9d7-168">Zwiększ rozmiary stosu (jest to ważniejsze w rzeczywistym kodzie aplikacji niż w przypadku pokazu).</span><span class="sxs-lookup"><span data-stu-id="4d9d7-168">Increase stack sizes (this is more important in actual application code than it is for the demonstration).</span></span>
1. <span data-ttu-id="4d9d7-169">Skompiluj ponownie bibliotekę ThreadX z definicją TX_ENABLE_STACK_CHECKING.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-169">Rebuild the ThreadX library with TX_ENABLE_STACK_CHECKING defined.</span></span> <span data-ttu-id="4d9d7-170">Umożliwia to wbudowaną kontrolę stosu ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-170">This enables the built-in ThreadX stack checking.</span></span>
1. <span data-ttu-id="4d9d7-171">Tymczasowo Pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub nie ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-171">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="4d9d7-172">Takie informacje powinny być przydatne do obsługi inżynierów.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-172">Such information should prove useful to support engineers.</span></span>

<span data-ttu-id="4d9d7-173">Postępuj zgodnie z procedurami przedstawionymi w[centrum pomocy technicznej](about-this-guide.md#customer-support-center), aby wysłać informacje zebrane z kroków rozwiązywania problemów.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-173">Follow the procedures outlined in "[Customer Support Center](about-this-guide.md#customer-support-center)" to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="4d9d7-174">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4d9d7-174">Configuration Options</span></span>

<span data-ttu-id="4d9d7-175">Podczas kompilowania biblioteki ThreadX i aplikacji przy użyciu ThreadX istnieje kilka opcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-175">There are several configuration options when building the ThreadX library and the application using ThreadX.</span></span> <span data-ttu-id="4d9d7-176">Poniższe opcje można zdefiniować w źródle aplikacji, w wierszu polecenia lub w pliku ***tx_user. h*** .</span><span class="sxs-lookup"><span data-stu-id="4d9d7-176">The options below can be defined in the application source, on the command line, or within the ***tx_user.h*** include file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d9d7-177">\* Opcje zdefiniowane w ***tx_user. h** _ są stosowane tylko wtedy, gdy aplikacja i Biblioteka ThreadX zostały skompilowane przy użyciu _ *TX_INCLUDE_USER_DEFINE_FILE** zdefiniowanej.\*</span><span class="sxs-lookup"><span data-stu-id="4d9d7-177">*Options defined in ***tx_user.h** _ are applied only if the application and ThreadX library are built with _ *TX_INCLUDE_USER_DEFINE_FILE** defined.*</span></span>

### <a name="smallest-configuration"></a><span data-ttu-id="4d9d7-178">Najmniejsza konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4d9d7-178">Smallest Configuration</span></span>

<span data-ttu-id="4d9d7-179">W przypadku najmniejszego rozmiaru kodu należy wziąć pod uwagę następujące opcje konfiguracji ThreadX (w przypadku braku wszystkich innych opcji).</span><span class="sxs-lookup"><span data-stu-id="4d9d7-179">For the smallest code size, the following ThreadX configuration options should be considered (in absence of all other options).</span></span>

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a><span data-ttu-id="4d9d7-180">Najszybsza konfiguracja</span><span class="sxs-lookup"><span data-stu-id="4d9d7-180">Fastest Configuration</span></span>

<span data-ttu-id="4d9d7-181">Dla najszybszych wykonań te same opcje konfiguracji, które są używane dla najmniejszej konfiguracji wcześniej, ale z tymi opcjami również są brane pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-181">For the fastest execution, the same configuration options used for the Smallest Configuration previously, but with these options also considered.</span></span>

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

<span data-ttu-id="4d9d7-182">Opisano [szczegółowe opcje konfiguracji](#detailed-configuration-options) .</span><span class="sxs-lookup"><span data-stu-id="4d9d7-182">[Detailed configuration options](#detailed-configuration-options) are described.</span></span>

### <a name="global-time-source"></a><span data-ttu-id="4d9d7-183">Globalne źródło czasu</span><span class="sxs-lookup"><span data-stu-id="4d9d7-183">Global Time Source</span></span>

<span data-ttu-id="4d9d7-184">W przypadku innych Microsoft Azure produktów RTO (FileX, NetX, GUIX, USBX itp.), ThreadX definiuje liczbę cykli czasomierza ThreadX, które reprezentują jedną sekundę.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-184">For other Microsoft Azure RTOS products (FileX, NetX, GUIX, USBX, etc.), ThreadX defines the number of ThreadX timer ticks that represents one second.</span></span> <span data-ttu-id="4d9d7-185">Inne korzystają z własnych wymagań czasowych na podstawie tej stałej.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-185">Others derive their time requirements based on this constant.</span></span> <span data-ttu-id="4d9d7-186">Wartością domyślną jest 100, przy założeniu, że 10 ms okresowe przerwanie.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-186">By default, the value is 100, assuming a 10ms periodic interrupt.</span></span> <span data-ttu-id="4d9d7-187">Użytkownik może zastąpić tę wartość, definiując TX_TIMER_TICKS_PER_SECOND przy użyciu żądanej wartości w ***tx_port. h*** lub w środowisku IDE lub w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-187">The user may override this value by defining TX_TIMER_TICKS_PER_SECOND with the desired value in ***tx_port.h*** or within the IDE or command line.</span></span>

### <a name="detailed-configuration-options"></a><span data-ttu-id="4d9d7-188">Szczegółowe opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4d9d7-188">Detailed Configuration Options</span></span>

<span data-ttu-id="4d9d7-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="4d9d7-190">Po zdefiniowaniu ta opcja umożliwia gromadzenie informacji o wydajności w pulach bajtów.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-190">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="4d9d7-191">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-191">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="4d9d7-193">Po zdefiniowaniu ta opcja umożliwia gromadzenie informacji o wydajności w pulach bajtów.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-193">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="4d9d7-194">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-194">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-195">**TX_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-195">**TX_DISABLE_ERROR_CHECKING**</span></span>

<span data-ttu-id="4d9d7-196">Pomija sprawdzanie błędów wywołania usługi podstawowej.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-196">Bypasses basic service call error checking.</span></span> <span data-ttu-id="4d9d7-197">W przypadku zdefiniowania w źródle aplikacji wszystkie podstawowe sprawdzanie błędów parametrów jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-197">When defined in the application source, all basic parameter error checking is disabled.</span></span> <span data-ttu-id="4d9d7-198">Może to zwiększyć wydajność o nawet 30% i może również zmniejszyć rozmiar obrazu.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-198">This may improve performance by as much as 30% and may also reduce the image size.</span></span>

> [!NOTE]
> <span data-ttu-id="4d9d7-199">*Wyłączenie sprawdzania błędów jest możliwe tylko wtedy, gdy aplikacja może całkowicie zagwarantować, że wszystkie parametry wejściowe są zawsze ważne we wszystkich okolicznościach, włącznie z parametrami wejściowymi pochodzącymi z zewnętrznych danych wejściowych. Jeśli do interfejsu API dostarczono nieprawidłowe dane wejściowe z wyłączonym sprawdzaniem błędów, Wynikowe zachowanie jest niezdefiniowane i może skutkować uszkodzeniem pamięci lub awarią systemu.*</span><span class="sxs-lookup"><span data-stu-id="4d9d7-199">*It is only safe to disable error checking if the application can absolutely guarantee all input parameters are always valid under all circumstances, including input parameters derived from external input. If invalid input is supplied to the API with error checking disabled, the resulting behavior is undefined and could result in memory corruption or system crash.*</span></span>

> [!NOTE]
> <span data-ttu-id="4d9d7-200">*Wartości zwracane przez interfejs API ThreadX nie wpływają na wyłączanie sprawdzania błędów są wyświetlane pogrubione w sekcji "wartości zwracane" w opisie interfejsu API w rozdziale 4. Wartości zwrotne Niepogrubione są puste, jeśli sprawdzanie błędów jest wyłączone przy użyciu opcji TX_DISABLE_ERROR_CHECKING.*</span><span class="sxs-lookup"><span data-stu-id="4d9d7-200">*ThreadX API return values not affected by disabling error checking are listed in bold in the “Return Values” section of each API description in Chapter 4. The nonbold return values are void if error checking is disabled by using the TX_DISABLE_ERROR_CHECKING option.*</span></span>

<span data-ttu-id="4d9d7-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span></span>

<span data-ttu-id="4d9d7-202">Po zdefiniowaniu program wyłącza powiadomienia zwrotne dla różnych obiektów ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-202">When defined, disables the notify callbacks for various ThreadX objects.</span></span> <span data-ttu-id="4d9d7-203">Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-203">Using this option slightly reduces code size and improves performance.</span></span> <span data-ttu-id="4d9d7-204">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-204">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span></span>

<span data-ttu-id="4d9d7-206">Po zdefiniowaniu program wyłącza funkcję progu zastępują i nieco zmniejsza rozmiar kodu i zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-206">When defined, disables the preemption-threshold feature and slightly reduces code size and improves performance.</span></span> <span data-ttu-id="4d9d7-207">Oczywiście funkcje progu zastępujące nie są już dostępne.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-207">Of course, the preemption-threshold capabilities are no longer available.</span></span> <span data-ttu-id="4d9d7-208">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-208">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-209">**TX_DISABLE_REDUNDANT_CLEARING**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-209">**TX_DISABLE_REDUNDANT_CLEARING**</span></span>

<span data-ttu-id="4d9d7-210">Po zdefiniowaniu program usuwa logikę do inicjowania ThreadX globalnych C struktur danych w wartości zero.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-210">When defined, removes the logic for initializing ThreadX global C data structures to zero.</span></span> <span data-ttu-id="4d9d7-211">Ta wartość powinna być używana tylko wtedy, gdy kod inicjalizacji kompilatora ustawi wszystkie niezainicjowane dane globalne języka C na zero.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-211">This should only be used if the compiler's initialization code sets all un-initialized C global data to zero.</span></span> <span data-ttu-id="4d9d7-212">Użycie tej opcji nieco zmniejsza rozmiar kodu i zwiększa wydajność podczas inicjacji.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-212">Using this option slightly reduces code size and improves performance during initialization.</span></span> <span data-ttu-id="4d9d7-213">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-213">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-214">**TX_DISABLE_STACK_FILLING**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-214">**TX_DISABLE_STACK_FILLING**</span></span>

<span data-ttu-id="4d9d7-215">Gdy jest zdefiniowany, wyłącza umieszczanie wartości 0xEF w każdym bajcie stosu każdego wątku po utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-215">When defined, disables placing the 0xEF value in each byte of each thread's stack when created.</span></span> <span data-ttu-id="4d9d7-216">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-216">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-217">**TX_ENABLE_EVENT_TRACE**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-217">**TX_ENABLE_EVENT_TRACE**</span></span>

<span data-ttu-id="4d9d7-218">Po zdefiniowaniu ThreadX włącza kod zbierający zdarzenia do tworzenia buforu śledzenia TraceX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-218">When defined, ThreadX enables the event gathering code for creating a TraceX trace buffer.</span></span>

<span data-ttu-id="4d9d7-219">**TX_ENABLE_STACK_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-219">**TX_ENABLE_STACK_CHECKING**</span></span>

<span data-ttu-id="4d9d7-220">Gdy jest zdefiniowany, umożliwia sprawdzanie sterty czasu wykonywania ThreadX, w tym analizę ilości stosu i badanie wzorców danych "ogrodzenia" przed i po obszarze stosu.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-220">When defined, enables ThreadX run-time stack checking, which includes analysis of how much stack has been used and examination of data pattern "fences" before and after the stack area.</span></span> <span data-ttu-id="4d9d7-221">W przypadku wykrycia błędu stosu zostanie wywołana zarejestrowana procedura obsługi błędów stosu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-221">If a stack error is detected, the registered application stack error handler is called.</span></span> <span data-ttu-id="4d9d7-222">Ta opcja powoduje nieco zwiększone obciążenie i rozmiar kodu.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-222">This option does result in slightly increased overhead and code size.</span></span> <span data-ttu-id="4d9d7-223">Aby uzyskać więcej informacji, przejrzyj funkcję API ***tx_thread_stack_error_notify*** .</span><span class="sxs-lookup"><span data-stu-id="4d9d7-223">Review the ***tx_thread_stack_error_notify*** API function for more information.</span></span> <span data-ttu-id="4d9d7-224">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-224">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="4d9d7-226">Po zdefiniowaniu program włącza zbieranie informacji o wydajności w grupach flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-226">When defined, enables the gathering of performance information on event flags groups.</span></span> <span data-ttu-id="4d9d7-227">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-227">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span></span>

<span data-ttu-id="4d9d7-229">Po zdefiniowaniu ThreadX ulepsza wywołania interfejsu API ***tx_thread_resume** _ i _ *_tx_thread_suspend_** za pośrednictwem kodu w wierszu.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-229">When defined, ThreadX improves the ***tx_thread_resume** _ and _ *_tx_thread_suspend_** API calls via in-line code.</span></span> <span data-ttu-id="4d9d7-230">Zwiększa to rozmiar kodu, ale zwiększa wydajność tych dwóch wywołań interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-230">This increases code size but enhances performance of these two API calls.</span></span>

<span data-ttu-id="4d9d7-231">**TX_MAX_PRIORITIES**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-231">**TX_MAX_PRIORITIES**</span></span>

<span data-ttu-id="4d9d7-232">Definiuje poziomy priorytetów dla ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-232">Defines the priority levels for ThreadX.</span></span> <span data-ttu-id="4d9d7-233">Wartości prawne mieszczą się w zakresie od 32 do 1024 (włącznie) i *muszą* być równo widoczne przez 32.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-233">Legal values range from 32 through 1024 (inclusive) and *must* be evenly divisible by 32.</span></span> <span data-ttu-id="4d9d7-234">Zwiększenie liczby obsługiwanych poziomów priorytetów zwiększa użycie pamięci RAM o 128 bajtów dla każdej grupy priorytetów 32.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-234">Increasing the number of priority levels supported increases the RAM usage by 128 bytes for every group of 32 priorities.</span></span> <span data-ttu-id="4d9d7-235">Istnieje jednak tylko znaczący wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-235">However, there is only a negligible effect on performance.</span></span> <span data-ttu-id="4d9d7-236">Domyślnie ta wartość jest ustawiana na 32 poziomów priorytetów.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-236">By default, this value is set to 32 priority levels.</span></span>

<span data-ttu-id="4d9d7-237">**TX_MINIMUM_STACK**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-237">**TX_MINIMUM_STACK**</span></span>

<span data-ttu-id="4d9d7-238">Określa minimalny rozmiar stosu (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="4d9d7-238">Defines the minimum stack size (in bytes).</span></span> <span data-ttu-id="4d9d7-239">Służy do sprawdzania błędów podczas tworzenia wątków.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-239">It is used for error checking when threads are created.</span></span> <span data-ttu-id="4d9d7-240">Wartość domyślna to specyficzny dla portu i znajduje się w ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-240">The default value is port-specific and is found in ***tx_port.h***.</span></span>

<span data-ttu-id="4d9d7-241">**TX_MISRA_ENABLE**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-241">**TX_MISRA_ENABLE**</span></span>

<span data-ttu-id="4d9d7-242">Po zdefiniowaniu ThreadX wykorzystuje konwencje zgodne z MISRA C.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-242">When defined, ThreadX utilizes MISRA C compliant conventions.</span></span> <span data-ttu-id="4d9d7-243">Aby uzyskać szczegółowe informacje, zobacz  ***ThreadX_MISRA_Compliance.pdf*** .</span><span class="sxs-lookup"><span data-stu-id="4d9d7-243">Refer to  ***ThreadX_MISRA_Compliance.pdf*** for details.</span></span>

<span data-ttu-id="4d9d7-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="4d9d7-245">Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności dla muteksów.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-245">When defined, enables the gathering of performance information on mutexes.</span></span> <span data-ttu-id="4d9d7-246">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-246">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-247">**TX_NO_TIMER**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-247">**TX_NO_TIMER**</span></span>

<span data-ttu-id="4d9d7-248">Po zdefiniowaniu logika czasomierza ThreadX jest całkowicie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-248">When defined, the ThreadX timer logic is completely disabled.</span></span> <span data-ttu-id="4d9d7-249">Jest to przydatne w przypadku, gdy funkcje czasomierza ThreadX (uśpienia wątku, przekroczenia limitu czasu interfejsu API, wyróżniania czasu i przetwarzania aplikacji) nie są używane.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-249">This is useful in cases where the ThreadX timer features (thread sleep, API timeouts, time-slicing, and application timers) are not utilized.</span></span> <span data-ttu-id="4d9d7-250">Jeśli określono **TX_NO_TIMER** , należy również zdefiniować opcję **TX_TIMER_PROCESS_IN_ISR** .</span><span class="sxs-lookup"><span data-stu-id="4d9d7-250">If **TX_NO_TIMER** is specified, the option **TX_TIMER_PROCESS_IN_ISR** must also be defined.</span></span>

<span data-ttu-id="4d9d7-251">**TX_NOT_INTERRUPTABLE**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-251">**TX_NOT_INTERRUPTABLE**</span></span>

<span data-ttu-id="4d9d7-252">Po zdefiniowaniu ThreadX nie podejmuje próby zminimalizowania czasu blokady przerwań.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-252">When defined, ThreadX does not attempt to minimize interrupt lockout time.</span></span> <span data-ttu-id="4d9d7-253">Powoduje to szybsze wykonywanie, ale nieco wydłuża czas blokady przerwań.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-253">This results in faster execution but does slightly increase interrupt lockout time.</span></span>

<span data-ttu-id="4d9d7-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="4d9d7-255">Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności w kolejkach.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-255">When defined, enables the gathering of performance information on queues.</span></span> <span data-ttu-id="4d9d7-256">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-256">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-257">**TX_REACTIVATE_INLINE**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-257">**TX_REACTIVATE_INLINE**</span></span>

<span data-ttu-id="4d9d7-258">Po zdefiniowaniu program wykonuje ponowną aktywację ThreadX czasomierzy wbudowane zamiast używania wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-258">When defined, performs reactivation of ThreadX timers inline instead of using a function call.</span></span> <span data-ttu-id="4d9d7-259">Poprawia to wydajność, ale nieco zwiększa rozmiar kodu.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-259">This improves performance but slightly increases code size.</span></span> <span data-ttu-id="4d9d7-260">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-260">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="4d9d7-262">Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności dla semaforów.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-262">When defined, enables the gathering of performance information on semaphores.</span></span> <span data-ttu-id="4d9d7-263">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-263">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="4d9d7-265">Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności w wątkach.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-265">When defined, enables the gathering of performance information on threads.</span></span> <span data-ttu-id="4d9d7-266">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-266">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="4d9d7-268">Gdy jest zdefiniowany, umożliwia gromadzenie informacji o wydajności na czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-268">When defined, enables the gathering of performance information on timers.</span></span> <span data-ttu-id="4d9d7-269">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-269">By default, this option is not defined.</span></span>

<span data-ttu-id="4d9d7-270">**TX_TIMER_PROCESS_IN_ISR**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-270">**TX_TIMER_PROCESS_IN_ISR**</span></span>

<span data-ttu-id="4d9d7-271">Po zdefiniowaniu eliminuje wewnętrzny wątek czasomierza systemu dla ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-271">When defined, eliminates the internal system timer thread for ThreadX.</span></span> <span data-ttu-id="4d9d7-272">Powoduje to zwiększenie wydajności zdarzeń czasomierza i mniejszych wymagań dotyczących pamięci RAM, ponieważ stos czasomierzy i blok sterowania nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-272">This results in improved performance on timer events and smaller RAM requirements because the timer stack and control block are no longer needed.</span></span> <span data-ttu-id="4d9d7-273">Jednak użycie tej opcji przenosi wszystkie operacje przetwarzania wygaśnięcia czasomierza do poziomu ISR czasomierza.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-273">However, using this option moves all the timer expiration processing to the timer ISR level.</span></span> <span data-ttu-id="4d9d7-274">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-274">By default, this option is not defined.</span></span>

> [!NOTE]
> <span data-ttu-id="4d9d7-275">*Usługi dozwolone z czasomierzy mogą nie być dozwolone z procedury ISR i w ten sposób mogą być niedozwolone w przypadku korzystania z tej opcji.*</span><span class="sxs-lookup"><span data-stu-id="4d9d7-275">*Services allowed from timers may not be allowed from ISRs and thus might not be allowed when using this option.*</span></span>

<span data-ttu-id="4d9d7-276">**TX_TIMER_THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-276">**TX_TIMER_THREAD_PRIORITY**</span></span>

<span data-ttu-id="4d9d7-277">Definiuje priorytet wewnętrznego wątku czasomierza systemu ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-277">Defines the priority of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="4d9d7-278">Wartość domyślna to priorytet 0 — najwyższy priorytet w ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-278">The default value is priority 0—the highest priority in ThreadX.</span></span> <span data-ttu-id="4d9d7-279">Wartość domyślna jest definiowana w ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-279">The default value is defined in ***tx_port.h***.</span></span>

<span data-ttu-id="4d9d7-280">**TX_TIMER_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="4d9d7-280">**TX_TIMER_THREAD_STACK_SIZE**</span></span>

<span data-ttu-id="4d9d7-281">Określa rozmiar stosu (w bajtach) wewnętrznego wątku czasomierza systemu ThreadX.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-281">Defines the stack size (in bytes) of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="4d9d7-282">Ten wątek przetwarza wszystkie żądania uśpienia wątku, a także wszystkie limity czasu wywołań usługi.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-282">This thread processes all thread sleep requests as well as all service call timeouts.</span></span> <span data-ttu-id="4d9d7-283">Ponadto wszystkie procedury wywołania zwrotnego czasomierza aplikacji są wywoływane z tego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-283">In addition, all application timer callback routines are invoked from this context.</span></span> <span data-ttu-id="4d9d7-284">Wartość domyślna to specyficzny dla portu i znajduje się w ***tx_port. h***.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-284">The default value is port-specific and is found in ***tx_port.h***.</span></span>

## <a name="threadx-version-id"></a><span data-ttu-id="4d9d7-285">Identyfikator wersji ThreadX</span><span class="sxs-lookup"><span data-stu-id="4d9d7-285">ThreadX Version ID</span></span>

<span data-ttu-id="4d9d7-286">Programista może uzyskać wersję ThreadX z badania pliku \***tx_port. h** _.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-286">The programmer can obtain the ThreadX version from examination of the \***tx_port.h** _ file.</span></span> <span data-ttu-id="4d9d7-287">Ponadto ten plik zawiera również historię wersji odpowiedniego portu.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-287">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="4d9d7-288">Oprogramowanie aplikacji może uzyskać wersję ThreadX, badając ciąg globalny _ \* _tx_version_id \* \*.</span><span class="sxs-lookup"><span data-stu-id="4d9d7-288">Application software can obtain the ThreadX version by examining the global string _\*_tx_version_id\*\*.</span></span>
