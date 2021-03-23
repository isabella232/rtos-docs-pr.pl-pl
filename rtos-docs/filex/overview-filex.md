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
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="763fe-105">Omówienie usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="763fe-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="763fe-106">Usługa Azure RTO FileX Embedded File System to zaawansowane, przemysłowe rozwiązanie do oceny plików Microsoft FAT, zaprojektowane specjalnie pod kątem głęboko osadzonych, w czasie rzeczywistym i aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="763fe-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="763fe-107">Usługa Azure RTO FileX obsługuje wszystkie formaty plików firmy Microsoft, w tym FAT12, FAT16, FAT32 i exFAT.</span><span class="sxs-lookup"><span data-stu-id="763fe-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="763fe-108">Usługa FileX oferuje również opcjonalną odporność na uszkodzenia i możliwość nanoszenia poziomu zużycia w środowisku FLASH za pośrednictwem produktu dodatkowego o nazwie [Azure RTO LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span><span class="sxs-lookup"><span data-stu-id="763fe-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="763fe-109">Wszystkie te połączone z małym wpływem, szybkim wykonywaniem i najbardziej łatwym w obsłużeniu, dzięki czemu usługa Azure RTO FileX idealny wybór dla najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="763fe-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="763fe-110">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="763fe-110">API protocols</span></span>

### <a name="azure-rtos-filex-api"></a><span data-ttu-id="763fe-111">Interfejs API usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="763fe-111">Azure RTOS FileX API</span></span>

- <span data-ttu-id="763fe-112">Intuicyjny i spójny interfejs API</span><span class="sxs-lookup"><span data-stu-id="763fe-112">Intuitive and consistent API</span></span>
- <span data-ttu-id="763fe-113">W konwencji nazewnictwa czasowników</span><span class="sxs-lookup"><span data-stu-id="763fe-113">Noun-verb naming convention</span></span>
- <span data-ttu-id="763fe-114">Wszystkie interfejsy API mają wiodące *fx_* do łatwej identyfikacji jako FileX</span><span class="sxs-lookup"><span data-stu-id="763fe-114">All APIs have leading *fx_* to easily identify as FileX</span></span>
- <span data-ttu-id="763fe-115">Blokowanie interfejsów API ma opcjonalny limit czasu wątku</span><span class="sxs-lookup"><span data-stu-id="763fe-115">Blocking APIs have optional thread timeout</span></span>
- <span data-ttu-id="763fe-116">Opcjonalne wywołania zwrotne powiadomień użytkownika dla operacji multimedialnych i plików</span><span class="sxs-lookup"><span data-stu-id="763fe-116">Optional user-notification callbacks for media and file operations</span></span>
- <span data-ttu-id="763fe-117">Aby uzyskać więcej informacji, zobacz [Podręcznik użytkownika usługi Azure RTO FileX](about-this-guide.md) .</span><span class="sxs-lookup"><span data-stu-id="763fe-117">Please see [Azure RTOS FileX User Guide](about-this-guide.md) for more details</span></span>

### <a name="media-services"></a><span data-ttu-id="763fe-118">Media Services</span><span class="sxs-lookup"><span data-stu-id="763fe-118">Media Services</span></span>

- <span data-ttu-id="763fe-119">Obsługa systemu FAT 12/16/32 i exFAT</span><span class="sxs-lookup"><span data-stu-id="763fe-119">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="763fe-120">Minimalna 6KB FLASH, 2,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="763fe-120">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="763fe-121">Ukończ usługi dostępu do multimediów</span><span class="sxs-lookup"><span data-stu-id="763fe-121">Complete media access services</span></span>
- <span data-ttu-id="763fe-122">Nieograniczona liczba wystąpień multimediów</span><span class="sxs-lookup"><span data-stu-id="763fe-122">Unlimited number of media instance</span></span>
- <span data-ttu-id="763fe-123">Prosty interfejs sterownika sektora logicznego odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="763fe-123">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="763fe-124">Obsługa wielu partycji</span><span class="sxs-lookup"><span data-stu-id="763fe-124">Multiple partition support</span></span>
- <span data-ttu-id="763fe-125">Pamięć podręczna sektora logicznego</span><span class="sxs-lookup"><span data-stu-id="763fe-125">Logical sector cache</span></span>
- <span data-ttu-id="763fe-126">Pamięć podręczna wejścia systemu FAT</span><span class="sxs-lookup"><span data-stu-id="763fe-126">FAT entry cache</span></span>
- <span data-ttu-id="763fe-127">Opcjonalna obsługa odporności na uszkodzenia</span><span class="sxs-lookup"><span data-stu-id="763fe-127">Optional fault tolerance support</span></span>
- <span data-ttu-id="763fe-128">Odroczona aktualizacja dodatkowego systemu FAT</span><span class="sxs-lookup"><span data-stu-id="763fe-128">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="763fe-129">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="763fe-129">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="763fe-130">Intuicyjne interfejsy API dostępu do multimediów, w tym:</span><span class="sxs-lookup"><span data-stu-id="763fe-130">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="763fe-131">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="763fe-131">fx_media_open</span></span>
  - <span data-ttu-id="763fe-132">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="763fe-132">fx_media_close</span></span>
  - <span data-ttu-id="763fe-133">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="763fe-133">fx_media_format</span></span>
  - <span data-ttu-id="763fe-134">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="763fe-134">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="763fe-135">Usługi katalogowe</span><span class="sxs-lookup"><span data-stu-id="763fe-135">Directory Services</span></span>

- <span data-ttu-id="763fe-136">Do 256 ścieżek bajtów</span><span class="sxs-lookup"><span data-stu-id="763fe-136">Up to 256 byte paths</span></span>
- <span data-ttu-id="763fe-137">Liczba obsługiwanych nazw katalogów Long i 8,3</span><span class="sxs-lookup"><span data-stu-id="763fe-137">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="763fe-138">Utwórz katalog & usunąć</span><span class="sxs-lookup"><span data-stu-id="763fe-138">Directory create & delete</span></span>
- <span data-ttu-id="763fe-139">Nawigacja i przechodzenie katalogu</span><span class="sxs-lookup"><span data-stu-id="763fe-139">Directory navigation and traversal</span></span>
- <span data-ttu-id="763fe-140">Zarządzanie atrybutami katalogu</span><span class="sxs-lookup"><span data-stu-id="763fe-140">Directory attributes management</span></span>
- <span data-ttu-id="763fe-141">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="763fe-141">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="763fe-142">Intuicyjne interfejsy API dostępu do katalogów, w tym:</span><span class="sxs-lookup"><span data-stu-id="763fe-142">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="763fe-143">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="763fe-143">fx_directory_create</span></span>
  - <span data-ttu-id="763fe-144">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="763fe-144">fx_directory_delete</span></span>
  - <span data-ttu-id="763fe-145">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="763fe-145">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="763fe-146">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="763fe-146">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="763fe-147">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="763fe-147">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="763fe-148">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="763fe-148">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="763fe-149">Usługi plików</span><span class="sxs-lookup"><span data-stu-id="763fe-149">File Services</span></span>

- <span data-ttu-id="763fe-150">Minimum 3.3 KB FLASH</span><span class="sxs-lookup"><span data-stu-id="763fe-150">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="763fe-151">Nieograniczona liczba otwartych plików</span><span class="sxs-lookup"><span data-stu-id="763fe-151">Unlimited open files</span></span>
- <span data-ttu-id="763fe-152">Pliki tylko do odczytu mogą być otwierane wiele razy</span><span class="sxs-lookup"><span data-stu-id="763fe-152">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="763fe-153">Liczba obsługiwanych nazw katalogów Long i 8,3</span><span class="sxs-lookup"><span data-stu-id="763fe-153">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="763fe-154">Ciągła obsługa plików</span><span class="sxs-lookup"><span data-stu-id="763fe-154">Contiguous file support</span></span>
- <span data-ttu-id="763fe-155">Logika szybkiego wyszukiwania</span><span class="sxs-lookup"><span data-stu-id="763fe-155">Fast seek logic</span></span>
- <span data-ttu-id="763fe-156">Wstępne przydzielanie klastrów</span><span class="sxs-lookup"><span data-stu-id="763fe-156">Pre-allocation of clusters</span></span>
- <span data-ttu-id="763fe-157">Tworzenie, usuwanie i zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="763fe-157">File create, delete, and rename</span></span>
- <span data-ttu-id="763fe-158">Odczyt, zapis i przeglądanie plików</span><span class="sxs-lookup"><span data-stu-id="763fe-158">File read, write, and see</span></span>
- <span data-ttu-id="763fe-159">Zarządzanie atrybutami plików</span><span class="sxs-lookup"><span data-stu-id="763fe-159">File attributes management</span></span>
- <span data-ttu-id="763fe-160">Śledzenie na poziomie systemu za pośrednictwem usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="763fe-160">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="763fe-161">Intuicyjne interfejsy API dostępu do plików, w tym:</span><span class="sxs-lookup"><span data-stu-id="763fe-161">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="763fe-162">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="763fe-162">fx_file_create</span></span>
  - <span data-ttu-id="763fe-163">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="763fe-163">fx_file_delete</span></span>
  - <span data-ttu-id="763fe-164">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="763fe-164">fx_file_attributes_set</span></span>
  - <span data-ttu-id="763fe-165">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="763fe-165">fx_file_attributes_read</span></span>
  - <span data-ttu-id="763fe-166">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="763fe-166">fx_file_read</span></span>
  - <span data-ttu-id="763fe-167">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="763fe-167">fx_file_seek</span></span>
  - <span data-ttu-id="763fe-168">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="763fe-168">fx_file_write</span></span>

## <a name="small-footprint"></a><span data-ttu-id="763fe-169">Niewielkie rozmiary</span><span class="sxs-lookup"><span data-stu-id="763fe-169">Small-footprint</span></span>

<span data-ttu-id="763fe-170">W przypadku usługi Azure RTO FileX Embedded File System istnieje niezwykle mała ilość miejsca na 8,6 KB do 12 KB w przypadku podstawowej obsługi odczytu i zapisu w pliku.</span><span class="sxs-lookup"><span data-stu-id="763fe-170">Azure RTOS FileX embedded file system has a remarkably small minimal footprint of 8.6 KB to 12 KB for basic file read/write support.</span></span> <span data-ttu-id="763fe-171">Minimalne użycie pamięci RAM usługi Azure RTO FileX jest w kolejności od 1,8 KB do jednego wystąpienia nośnika i tylko z pamięcią podręczną "512-Byte" sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="763fe-171">Minimal Azure RTOS FileX RAM usage is on the order of 1.8 KB for one media instance and with only a 512-byte logical sector cache.</span></span> <span data-ttu-id="763fe-172">Podobnie jak w przypadku usługi Azure RTO ThreadX, rozmiar usługi Azure RTO FileX jest automatycznie skalowany w oparciu o usługi używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="763fe-172">Like Azure RTOS ThreadX, the size of Azure RTOS FileX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="763fe-173">To praktycznie eliminuje konieczność skomplikowanej konfiguracji i kompilacji parametrów, co ułatwia deweloperom.</span><span class="sxs-lookup"><span data-stu-id="763fe-173">This virtually eliminates the need for complicated configuration and builds parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="763fe-174">Szybkie wykonywanie</span><span class="sxs-lookup"><span data-stu-id="763fe-174">Fast execution</span></span>

<span data-ttu-id="763fe-175">Usługa Azure RTO FileX udostępnia pamięć podręczną sektora logicznego, a także pamięć podręczną wpisów FAT.</span><span class="sxs-lookup"><span data-stu-id="763fe-175">Azure RTOS FileX provides a logical sector cache as well as a FAT entry cache.</span></span> <span data-ttu-id="763fe-176">Oba te rozmiary są kontrolowane bezpośrednio przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="763fe-176">The sizes of both are under direct control of the application.</span></span> <span data-ttu-id="763fe-177">Ponadto usługa Azure RTO FileX zapewnia ciągłą alokację klastra i bezpośrednie odczytywanie i zapisywanie kolejnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="763fe-177">In addition, Azure RTOS FileX provides contiguous cluster allocation and direct consecutive cluster reading and writing.</span></span> <span data-ttu-id="763fe-178">Żądania odczytu/zapisu całego sektora są wykonywane bezpośrednio między buforem aplikacji a nośnikiem — to oznacza, że nie jest wykonywane pośrednie buforowanie.</span><span class="sxs-lookup"><span data-stu-id="763fe-178">Read/write requests of whole sectors are done directly between the application buffer and the media – that is, no intermediate buffering is done.</span></span> <span data-ttu-id="763fe-179">Wszystkie te i ogólne zasady projektowania zorientowane na wydajność ułatwiają platformie Azure RTO FileX osiąganie najszybszej możliwej wydajności.</span><span class="sxs-lookup"><span data-stu-id="763fe-179">All of this and a general performance-oriented design philosophy helps Azure RTOS FileX achieve the fastest possible performance.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="763fe-180">Technologia zaawansowana</span><span class="sxs-lookup"><span data-stu-id="763fe-180">Advanced technology</span></span>

<span data-ttu-id="763fe-181">Usługa Azure RTO FileX to zaawansowana technologia, w tym następujące.</span><span class="sxs-lookup"><span data-stu-id="763fe-181">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="763fe-182">Obsługa systemu FAT 12/16/32 i exFAT</span><span class="sxs-lookup"><span data-stu-id="763fe-182">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="763fe-183">Obsługa wielu partycji</span><span class="sxs-lookup"><span data-stu-id="763fe-183">Multiple partition support</span></span>
- <span data-ttu-id="763fe-184">Automatyczne skalowanie</span><span class="sxs-lookup"><span data-stu-id="763fe-184">Automatic scaling</span></span>
- <span data-ttu-id="763fe-185">Neutralne</span><span class="sxs-lookup"><span data-stu-id="763fe-185">Endian neutral</span></span>
- <span data-ttu-id="763fe-186">Długa nazwa pliku i obsługa 8,3</span><span class="sxs-lookup"><span data-stu-id="763fe-186">Long file name and 8.3 support</span></span>
- <span data-ttu-id="763fe-187">Opcjonalna obsługa odporności na uszkodzenia</span><span class="sxs-lookup"><span data-stu-id="763fe-187">Optional fault tolerance support</span></span>
- <span data-ttu-id="763fe-188">Pamięć podręczna sektora logicznego</span><span class="sxs-lookup"><span data-stu-id="763fe-188">Logical sector cache</span></span>
- <span data-ttu-id="763fe-189">Pamięć podręczna wejścia systemu FAT</span><span class="sxs-lookup"><span data-stu-id="763fe-189">FAT entry cache</span></span>
- <span data-ttu-id="763fe-190">Wstępne przydzielanie klastrów</span><span class="sxs-lookup"><span data-stu-id="763fe-190">Pre-allocation of clusters</span></span>
- <span data-ttu-id="763fe-191">Ciągła obsługa plików</span><span class="sxs-lookup"><span data-stu-id="763fe-191">Contiguous file support</span></span>
- <span data-ttu-id="763fe-192">Opcjonalne metryki wydajności</span><span class="sxs-lookup"><span data-stu-id="763fe-192">Optional performance metrics</span></span>
- <span data-ttu-id="763fe-193">Obsługa analizy systemu Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="763fe-193">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="763fe-194">NIE NIj na bilansowanie (Azure RTO LevelX)</span><span class="sxs-lookup"><span data-stu-id="763fe-194">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="763fe-195">Usługa Azure RTO LevelX jest produktem firmy Microsoft, a nie ni FLASH.</span><span class="sxs-lookup"><span data-stu-id="763fe-195">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="763fe-196">Usługi Azure RTO LevelX można używać w połączeniu z FileX lub jako autonomiczną, bezpośrednią biblioteką sektora FLASH do odczytu/zapisu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="763fe-196">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="763fe-197">Najszybszy czas wprowadzenia na rynek</span><span class="sxs-lookup"><span data-stu-id="763fe-197">Fastest time-to-market</span></span>

<span data-ttu-id="763fe-198">Usługa Azure RTO FileX umożliwia łatwe instalowanie, uczenie się, używanie, debugowanie, weryfikowanie, certyfikowanie i konserwowanie.</span><span class="sxs-lookup"><span data-stu-id="763fe-198">Azure RTOS FileX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="763fe-199">W związku z tym usługa Azure RTO FileX jest jednym z najpopularniejszych systemów plików FAT dla osadzonych urządzeń IoT.</span><span class="sxs-lookup"><span data-stu-id="763fe-199">As a result, Azure RTOS FileX is one of the most popular FAT file systems for embedded IoT devices.</span></span> <span data-ttu-id="763fe-200">Poniżej przedstawiono kilka powodów, dla których spójny czas wprowadzenia na rynek:</span><span class="sxs-lookup"><span data-stu-id="763fe-200">The following are some reasons for our consistent time-to-market advantage:</span></span>

- <span data-ttu-id="763fe-201">Dokumentacja dotycząca jakości — zapoznaj się z naszym [podręcznikiem użytkownika usługi Azure RTO FileX](about-this-guide.md) i zapoznaj się z Tobą.</span><span class="sxs-lookup"><span data-stu-id="763fe-201">Quality Documentation – please review our [Azure RTOS FileX User Guide](about-this-guide.md) and see for yourself!</span></span>
- <span data-ttu-id="763fe-202">Ukończ dostępność kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="763fe-202">Complete Source Code Availability</span></span>
- <span data-ttu-id="763fe-203">Łatwy w użyciu interfejs API</span><span class="sxs-lookup"><span data-stu-id="763fe-203">Easy-to-use API</span></span>
- <span data-ttu-id="763fe-204">Kompleksowy i zaawansowany zestaw funkcji</span><span class="sxs-lookup"><span data-stu-id="763fe-204">Comprehensive and Advanced Feature Set</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="763fe-205">Wstępnie certyfikowane przez TUV i UL do wielu standardów bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="763fe-205">Pre-certified  by TUV and UL to many safety standards</span></span>

![MOIMI — TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

<span data-ttu-id="763fe-207">Usługa Azure RTO FileX została certyfikowana przez moimi-TUV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC-61508 SIL 4, IEC-62304, Klasa bezpieczeństwa SW, ISO 26262 ASIL D i EN 50128.</span><span class="sxs-lookup"><span data-stu-id="763fe-207">Azure RTOS FileX has been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="763fe-208">Certyfikat potwierdza, że FileX może być używany podczas opracowywania oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności zabezpieczeń IEC-61508, IEC-62304, ISO 26262 i EN 50128 na potrzeby "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem".</span><span class="sxs-lookup"><span data-stu-id="763fe-208">The certification confirms that FileX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="763fe-209">MOIMI-TUV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TUV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, weryfikowania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="763fe-209">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="763fe-210">Standard bezpieczeństwa przemysłowego IEC 61508, a także wszystkie standardy, które są od niego pochodzące, w tym IEC-62304, ISO 26262 i EN 50128, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego urządzenia medycznego związanego z bezpieczeństwem, systemów kontroli procesów, maszyn przemysłowych, samochodów i systemów kontroli szynowej.</span><span class="sxs-lookup"><span data-stu-id="763fe-210">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles, and railway control systems.</span></span>

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="CRU certyfikat UL":::

<span data-ttu-id="763fe-212">Usługa Azure RTO FileX została rozpoznana przez UL w celu zapewnienia zgodności z metodą UL 60730-1 w załączniku H, CSA E60730-1 w załączniku H, IEC 60730-1 w załączniku H, UL 60335-1 załączniku R, IEC 60335-1 w załączniku R i normach bezpieczeństwa UL 1998 dla oprogramowania w składnikach programowalnych.</span><span class="sxs-lookup"><span data-stu-id="763fe-212">Azure RTOS FileX has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="763fe-213">UL to globalna, niezależna firma zajmująca się ochroną bezpieczeństwa, która ma więcej niż wiek fachowych rozwiązań w zakresie bezpieczeństwa, od publicznego wdrożenia energii elektrycznej, aby nawiązać przełom w zakresie trwałości, odnawialnych energii i nanotechnologii.</span><span class="sxs-lookup"><span data-stu-id="763fe-213">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

<span data-ttu-id="763fe-214">Artefakty (certyfikat, Podręcznik bezpieczeństwa, raport testowy itp.) skojarzone z certyfikatami TUV i UL są dostępne do sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="763fe-214">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="763fe-215">W przypadku, gdy aplikacja wymaga dodatkowej certyfikacji, usługa certyfikacji jest dostępna w firmie Microsoft w celu zapewnienia certyfikacji klucza dla różnych standardów przy użyciu rzeczywistej platformy sprzętowej, a nawet w odniesieniu do kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="763fe-215">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="763fe-216">Jedna prosta licencja</span><span class="sxs-lookup"><span data-stu-id="763fe-216">One Simple License</span></span>

<span data-ttu-id="763fe-217">Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.</span><span class="sxs-lookup"><span data-stu-id="763fe-217">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="763fe-218">Pełny kod źródłowy o najwyższej jakości</span><span class="sxs-lookup"><span data-stu-id="763fe-218">Full, highest-quality source code</span></span>

<span data-ttu-id="763fe-219">W ciągu lat FileX kod źródłowy ustawił na pasku jakość i łatwość interpretacji.</span><span class="sxs-lookup"><span data-stu-id="763fe-219">Throughout the years, FileX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="763fe-220">Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.</span><span class="sxs-lookup"><span data-stu-id="763fe-220">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="763fe-221">Obsługuje najpopularniejsze architektury</span><span class="sxs-lookup"><span data-stu-id="763fe-221">Supports most popular architectures</span></span>

<span data-ttu-id="763fe-222">Usługa Azure RTO FileX działa na najpopularniejszych mikroprocesorach 32-bitowych, w pełni przetestowanych i w pełni obsługiwanych, w tym:</span><span class="sxs-lookup"><span data-stu-id="763fe-222">Azure RTOS FileX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="763fe-223">**Urządzenia analogowe**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="763fe-223">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="763fe-224">**Andes rdzeń**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="763fe-224">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="763fe-225">**Ambiqmicro**: Apollo MCUs</span><span class="sxs-lookup"><span data-stu-id="763fe-225">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="763fe-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="763fe-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="763fe-227">**Erze**: Xtensa, romb</span><span class="sxs-lookup"><span data-stu-id="763fe-227">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="763fe-228">**Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="763fe-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="763fe-229">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="763fe-229">**Cypress**: RISC-V</span></span>

<span data-ttu-id="763fe-230">**EnSilica**: ESI-RISC</span><span class="sxs-lookup"><span data-stu-id="763fe-230">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="763fe-231">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="763fe-231">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="763fe-232">**Intel**; **Intel FPGA**: X36/Pentium, XScale, Nios II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="763fe-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="763fe-233">**Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="763fe-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="763fe-234">**Mikrośrednik**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="763fe-234">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="763fe-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, I.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="763fe-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="763fe-236">**Renesas**: sh, HS, V850, RX, rz, synergia</span><span class="sxs-lookup"><span data-stu-id="763fe-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="763fe-237">**Krzem** Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="763fe-237">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="763fe-238">**SynopSYS**: Arc 600, 700, łuk em, łuk HS</span><span class="sxs-lookup"><span data-stu-id="763fe-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="763fe-239">**St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="763fe-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="763fe-240">**: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="763fe-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="763fe-241">**Przetwarzanie Wave**: MIPS32 4K, 24 k, 34 k, 1004 k, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="763fe-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="763fe-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="763fe-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="763fe-243">*Wszystkie wymienione wartości chronometrażu i rozmiaru są szacunkami i mogą być inne na platformie deweloperskiej.*</span><span class="sxs-lookup"><span data-stu-id="763fe-243">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
