---
title: Rozdział 7 — zdarzenia śledzenia usługi Azure RTO FileX
description: Ten rozdział zawiera opis zdarzeń usługi Azure RTO FileX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823395"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a><span data-ttu-id="4c2f2-103">Rozdział 7 — zdarzenia śledzenia usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="4c2f2-103">Chapter 7 - Azure RTOS FileX trace events</span></span>

<span data-ttu-id="4c2f2-104">Ten rozdział zawiera opis zdarzeń usługi Azure RTO FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-104">This chapter contains a description of the Azure RTOS FileX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="4c2f2-105">Lista zdarzeń i ikon</span><span class="sxs-lookup"><span data-stu-id="4c2f2-105">List of Events and Icons</span></span>

<span data-ttu-id="4c2f2-106">**Poniżej znajduje się lista zdarzeń FileX wyświetlanych przez TraceX.**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-106">**The following is a list of FileX events displayed by TraceX.**</span></span>

<span data-ttu-id="4c2f2-107">Poniżej opisano każde zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="4c2f2-107">The following describes each event:</span></span>

| <span data-ttu-id="4c2f2-108">**Ikona**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-108">**Icon**</span></span>                         | <span data-ttu-id="4c2f2-109">**Znaczenie**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-109">**Meaning**</span></span>                               |
| -------------------------------- | ----------------------------------------- |
| ![Ikona chybień wewnętrznej pamięci podręcznej sektora logicznego](./media/user-guide/fx-events/image1.png)    | <span data-ttu-id="4c2f2-111">Chybienia w pamięci podręcznej wewnętrznego sektora logicznego</span><span class="sxs-lookup"><span data-stu-id="4c2f2-111">Internal Logical Sector Cache Miss</span></span> |
| ![Ikona chybień w pamięci podręcznej katalogów wewnętrznych](./media/user-guide/fx-events/image2.png)    | <span data-ttu-id="4c2f2-113">Chybienia w pamięci podręcznej katalogów wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="4c2f2-113">Internal Directory Cache Miss</span></span> |
| ![Ikona opróżniania nośnika wewnętrznego](./media/user-guide/fx-events/image3.png)    | <span data-ttu-id="4c2f2-115">Wewnętrzne opróżnianie nośnika</span><span class="sxs-lookup"><span data-stu-id="4c2f2-115">Internal Media Flush</span></span> |
| ![Ikona odczytu wpisu katalogu wewnętrznego](./media/user-guide/fx-events/image4.png)    | <span data-ttu-id="4c2f2-117">Odczyt wpisu katalogu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="4c2f2-117">Internal Directory Entry Read</span></span> |
| ![Ikona zapisu w katalogu wewnętrznym](./media/user-guide/fx-events/image5.png)    | <span data-ttu-id="4c2f2-119">Zapis wpisu w katalogu wewnętrznym</span><span class="sxs-lookup"><span data-stu-id="4c2f2-119">Internal Directory Entry Write</span></span> |
| ![Ikona odczytu wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image6.png)    | <span data-ttu-id="4c2f2-121">Odczyt wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-121">Internal I/O Driver Read</span></span> |
| ![Ikona wewnętrznego zapisu sterownika we/wy](./media/user-guide/fx-events/image7.png)    | <span data-ttu-id="4c2f2-123">Zapis wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-123">Internal I/O Driver Write</span></span> |
| ![Ikona opróżniania sterownika wewnętrznego we/wy](./media/user-guide/fx-events/image8.png)    | <span data-ttu-id="4c2f2-125">Wewnętrzny opróżnia sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-125">Internal I/O Driver Flush</span></span> |
| ![Ikona przerwania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image9.png)    | <span data-ttu-id="4c2f2-127">Przerwanie wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-127">Internal I/O Driver Abort</span></span> |
| ![Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image10.png)    | <span data-ttu-id="4c2f2-129">Inicjowanie wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-129">Internal I/O Driver Initialize</span></span> |
| ![Ikona odczytu wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image11.png)    | <span data-ttu-id="4c2f2-131">Odczyt wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-131">Internal I/O Driver Boot Read</span></span> |
| ![Ikona wewnętrznych sektorów sterowników we/wy](./media/user-guide/fx-events/image12.png)    | <span data-ttu-id="4c2f2-133">Sektory wersji wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-133">Internal I/O Driver Release Sectors</span></span> |
| ![Ikona zapisu wewnętrznego rozruchowego sterownika we/wy](./media/user-guide/fx-events/image13.png)    | <span data-ttu-id="4c2f2-135">Zapis rozruchowy wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-135">Internal I/O Driver Boot Write</span></span> |
| ![Ikona cofnięcia inicjalizacji sterownika sterownika wewnętrznego we/wy](./media/user-guide/fx-events/image14.png)    | <span data-ttu-id="4c2f2-137">Wewnętrzny sterownik sterownika we/wy nie został zainicjowany</span><span class="sxs-lookup"><span data-stu-id="4c2f2-137">Internal I / O Driver Driver Un-initialize</span></span> |
| ![Ikona odczytu atrybutów katalogu](./media/user-guide/fx-events/image15.png)    | <span data-ttu-id="4c2f2-139">**Odczyt atrybutów katalogu** (*fx_directory_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-139">**Directory Attributes Read** (*fx_directory_attributes_read*)</span></span> |
| ![Ikona zestawu atrybutów katalogu](./media/user-guide/fx-events/image16.png)    | <span data-ttu-id="4c2f2-141">**Zestaw atrybutów katalogu** (*fx_directory_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-141">**Directory Attributes Set** (*fx_directory_attributes_set*)</span></span> |
| ![Ikona tworzenia katalogu](./media/user-guide/fx-events/image17.png)    | <span data-ttu-id="4c2f2-143">**Tworzenie katalogu** (*fx_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-143">**Directory Create** (*fx_directory_create*)</span></span> |
| ![Ikona pobierania domyślnego katalogu](./media/user-guide/fx-events/image18.png)    | <span data-ttu-id="4c2f2-145">**Domyślne pobieranie katalogu** (*fx_directory_default_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-145">**Directory Default Get** (*fx_directory_default_get*)</span></span> |
| ![Ikona domyślnego zestawu katalogów](./media/user-guide/fx-events/image19.png)    | <span data-ttu-id="4c2f2-147">**Domyślny zestaw katalogów** (*fx_directory_default_set*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-147">**Directory Default Set** (*fx_directory_default_set*)</span></span> |
| ![Ikona usuwania katalogu](./media/user-guide/fx-events/image20.png)    | <span data-ttu-id="4c2f2-149">**Usuwanie katalogu** (*fx_directory_delete*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-149">**Directory Delete** (*fx_directory_delete*)</span></span> |
| ![Ikona wyszukiwania pierwszego wpisu katalogu](./media/user-guide/fx-events/image21.png)    | <span data-ttu-id="4c2f2-151">**Znajdź pierwszy wpis w katalogu** (*fx_directory_first_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-151">**Directory First Entry Find** (*fx_directory_first_entry_find*)</span></span> |
| ![Ikona wyszukiwania pierwszego wpisu katalogu](./media/user-guide/fx-events/image22.png)    | <span data-ttu-id="4c2f2-153">**Znajdowanie pierwszego wpisu katalogu** (*fx_directory_first_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-153">**Directory First Full Entry Find** (*fx_directory_first_full_entry_find*)</span></span> |
| ![Ikona uzyskiwania informacji o katalogu](./media/user-guide/fx-events/image23.png)    | <span data-ttu-id="4c2f2-155">**Pobieranie informacji o katalogu** (*fx_directory_information_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-155">**Directory Information Get** (*fx_directory_information_get*)</span></span> |
| ![Ikona czyszczenia ścieżki lokalnej katalogu](./media/user-guide/fx-events/image24.png)    | <span data-ttu-id="4c2f2-157">**Ścieżka lokalna katalogu jest niezrozumiała** (*fx_directory_local_path_clear*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-157">**Directory Local Path Clear** (*fx_directory_local_path_clear*)</span></span> |
| ![Ikona pobierania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image25.png)    | <span data-ttu-id="4c2f2-159">**Pobieranie ścieżki lokalnej katalogu** (*fx_directory_local_path_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-159">**Directory Local Path Get** (*fx_directory_local_path_get*)</span></span> |
| ![Ikona przywracania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image26.png)    | <span data-ttu-id="4c2f2-161">**Przywracanie ścieżki lokalnej katalogu** (*fx_directory_local_path_restore*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-161">**Directory Local Path Restore** (*fx_directory_local_path_restore*)</span></span> |
| ![Ikona zestawu ścieżek lokalnych katalogu](./media/user-guide/fx-events/image27.png)    | <span data-ttu-id="4c2f2-163">**Zestaw ścieżek lokalnych katalogu** (*fx_directory_local_path_set*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-163">**Directory Local Path Set** (*fx_directory_local_path_set*)</span></span> |
| ![Ikona pobierania długich nazw katalogów](./media/user-guide/fx-events/image28.png)    | <span data-ttu-id="4c2f2-165">**Pobieranie długiej nazwy katalogu** (*fx_directory_long_name_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-165">**Directory Long Name Get** (*fx_directory_long_name_get*)</span></span> |
| ![Ikona testu nazwy katalogu](./media/user-guide/fx-events/image29.png)    | <span data-ttu-id="4c2f2-167">**Test nazwy katalogu** (*fx_directory_name_test*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-167">**Directory Name Test** (*fx_directory_name_test*)</span></span> |
| ![Ikona wyszukiwania następnego wpisu w katalogu](./media/user-guide/fx-events/image30.png)    | <span data-ttu-id="4c2f2-169">**Znajdź wpis w katalogu** (*fx_directory_next_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-169">**Directory Next Entry Find** (*fx_directory_next_entry_find*)</span></span> |
| ![Ikona wyszukiwania następnego wpisu w katalogu](./media/user-guide/fx-events/image31.png)    | <span data-ttu-id="4c2f2-171">**Znajdź następny pełny wpis w katalogu** (*fx_directory_next_full_entry_find*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-171">**Directory Next Full Entry Find** (*fx_directory_next_full_entry_find*)</span></span> |
| ![Ikona zmiany nazwy katalogu](./media/user-guide/fx-events/image32.png)    | <span data-ttu-id="4c2f2-173">**Zmiana nazwy katalogu** (*fx_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-173">**Directory Rename** (*fx_directory_rename*)</span></span> |
| ![Ikona pobierania krótkiej nazwy katalogu](./media/user-guide/fx-events/image33.png)    | <span data-ttu-id="4c2f2-175">**Krótka nazwa katalogu Get** (*fx_directory_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-175">**Directory Short Name Get** (*fx_directory_short_name_get*)</span></span> |
| ![Ikona alokacji plików](./media/user-guide/fx-events/image34.png)    | <span data-ttu-id="4c2f2-177">**Przydzielenie pliku** (*fx_file_allocate*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-177">**File Allocate** (*fx_file_allocate*)</span></span> |
| ![Ikona odczytu atrybutów plików](./media/user-guide/fx-events/image35.png)    | <span data-ttu-id="4c2f2-179">**Odczyt atrybutów pliku** (*fx_file_attributes_read*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-179">**File Attributes Read** (*fx_file_attributes_read*)</span></span> |
| ![Ikona zestawu atrybutów pliku](./media/user-guide/fx-events/image36.png)    | <span data-ttu-id="4c2f2-181">**Zestaw atrybutów pliku** (*fx_file_attributes_set*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-181">**File Attributes Set** (*fx_file_attributes_set*)</span></span> |
| ![Ikona przydziału najlepszego nakładu pracy pliku](./media/user-guide/fx-events/image37.png)    | <span data-ttu-id="4c2f2-183">**Przydział najlepszego nakładu pracy w pliku** (*fx_file_best_effort_allocate*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-183">**File Best Effort Allocate** (*fx_file_best_effort_allocate*)</span></span> |
| ![Ikona zamykania pliku](./media/user-guide/fx-events/image38.png)    | <span data-ttu-id="4c2f2-185">**Zamknij plik** (*fx_file_close*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-185">**File Close** (*fx_file_close*)</span></span> |
| ![Ikona tworzenia pliku](./media/user-guide/fx-events/image39.png)    | <span data-ttu-id="4c2f2-187">**Tworzenie pliku** (*fx_file_create*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-187">**File Create** (*fx_file_create*)</span></span> |
| ![Ikona Ustawienia daty i godziny pliku](./media/user-guide/fx-events/image40.png)    | <span data-ttu-id="4c2f2-189">**Data i godzina ustawienia pliku** (*fx_file_date_time_set*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-189">**File Date Time Set** (*fx_file_date_time_set*)</span></span> |
| ![Ikona usuwania pliku](./media/user-guide/fx-events/image41.png)    | <span data-ttu-id="4c2f2-191">**Usuwanie pliku** (*fx_file_delete*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-191">**File Delete** (*fx_file_delete*)</span></span> |
| ![Ikona otwierania pliku](./media/user-guide/fx-events/image42.png)    | <span data-ttu-id="4c2f2-193">**Otwieranie pliku** (*fx_file_open*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-193">**File Open** (*fx_file_open*)</span></span> |
| ![Ikona odczytu pliku](./media/user-guide/fx-events/image43.png)    | <span data-ttu-id="4c2f2-195">**Odczyt pliku** (*fx_file_read*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-195">**File Read** (*fx_file_read*)</span></span> |
| ![Ikona wyszukiwania względnego pliku](./media/user-guide/fx-events/image44.png)    | <span data-ttu-id="4c2f2-197">**Wyszukiwanie względne plików** (*fx_file_relative_seek*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-197">**File Relative Seek** (*fx_file_relative_seek*)</span></span> |
| ![Ikona zmiany nazwy pliku](./media/user-guide/fx-events/image45.png)    | <span data-ttu-id="4c2f2-199">**Zmiana nazwy pliku** (*fx_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-199">**File Rename** (*fx_file_rename*)</span></span> |
| ![Ikona wyszukiwania plików](./media/user-guide/fx-events/image46.png)    | <span data-ttu-id="4c2f2-201">**Wyszukiwanie plików** (*fx_file_seek*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-201">**File Seek** (*fx_file_seek*)</span></span> |
| ![Ikona obcinania plików](./media/user-guide/fx-events/image47.png)    | <span data-ttu-id="4c2f2-203">**Obcinanie pliku** (*fx_file_truncate*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-203">**File Truncate** (*fx_file_truncate*)</span></span> |
| ![Ikona wycięcia plików](./media/user-guide/fx-events/image48.png)    | <span data-ttu-id="4c2f2-205">**Wydanie obcinania plików** (*fx_file_truncate_release*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-205">**File Truncate Release** (*fx_file_truncate_release*)</span></span> |
| ![Ikona zapisu pliku](./media/user-guide/fx-events/image49.png)    | <span data-ttu-id="4c2f2-207">**Zapis pliku** (*fx_file_write*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-207">**File Write** (*fx_file_write*)</span></span> |
| ![Ikona przerwania nośnika](./media/user-guide/fx-events/image50.png)    | <span data-ttu-id="4c2f2-209">**Przerwanie nośnika** (*fx_media_abort*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-209">**Media Abort** (*fx_media_abort*)</span></span> |
| ![Ikona unieważniania pamięci podręcznej multimediów](./media/user-guide/fx-events/image51.png)    | <span data-ttu-id="4c2f2-211">**Unieważnienie pamięci podręcznej multimediów** (*fx_media_cache_invalidate*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-211">**Media Cache Invalidate** (*fx_media_cache_invalidate*)</span></span> |
| ![Ikona Sprawdź multimedia](./media/user-guide/fx-events/image52.png)    | <span data-ttu-id="4c2f2-213">**Sprawdzenie multimediów** (*fx_media_check*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-213">**Media Check** (*fx_media_check*)</span></span> |
| ![\* Ikona zamykania nośnika](./media/user-guide/fx-events/image53.png)    | <span data-ttu-id="4c2f2-215">**Zamknięcie nośnika** (*fx_media_close*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-215">**Media Close** (*fx_media_close*)</span></span> |
| ![Ikona opróżniania nośnika](./media/user-guide/fx-events/image54.png)    | <span data-ttu-id="4c2f2-217">**Opróżnianie multimediów** (*fx_media_flush*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-217">**Media Flush** (*fx_media_flush*)</span></span> |
| ![Ikona formatu multimediów](./media/user-guide/fx-events/image55.png)    | <span data-ttu-id="4c2f2-219">**Format multimediów** (*fx_media_format*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-219">**Media Format** (*fx_media_format*)</span></span> |
| ![Ikona otwarcia nośnika](./media/user-guide/fx-events/image56.png)    | <span data-ttu-id="4c2f2-221">**Otwarte multimedia** (*fx_media_open*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-221">**Media Open** (*fx_media_open*)</span></span> |
| ![Ikona odczytu multimediów](./media/user-guide/fx-events/image57.png)    | <span data-ttu-id="4c2f2-223">**Odczyt z nośnika** (*fx_media_read*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-223">**Media Read** (*fx_media_read*)</span></span> |
| ![Ikona dostępnego miejsca na multimediach](./media/user-guide/fx-events/image58.png)    | <span data-ttu-id="4c2f2-225">**Dostępne miejsce na nośniku** (*fx_media_space_available*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-225">**Media Space Available** (*fx_media_space_available*)</span></span> |
| ![Ikona pobierania woluminu multimedialnego](./media/user-guide/fx-events/image59.png)    | <span data-ttu-id="4c2f2-227">**Pobieranie woluminu multimedialnego** (*fx_media_volume_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-227">**Media Volume Get** (*fx_media_volume_get*)</span></span> |
| ![Ikona zestawu woluminów multimedialnych](./media/user-guide/fx-events/image60.png)    | <span data-ttu-id="4c2f2-229">**Zestaw woluminów multimedialnych** (*fx_media_volume_set*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-229">**Media Volume Set** (*fx_media_volume_set*)</span></span> |
| ![Ikona zapisu multimediów](./media/user-guide/fx-events/image61.png)    | <span data-ttu-id="4c2f2-231">**Zapis multimediów** (*fx_media_write*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-231">**Media Write** (*fx_media_write*)</span></span> |
| ![Ikona pobierania daty systemu](./media/user-guide/fx-events/image62.png)    | <span data-ttu-id="4c2f2-233">**Data systemu Get** (*fx_system_date_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-233">**System Date Get** (*fx_system_date_get*)</span></span> |
| ![Ikona zestawu dat systemu](./media/user-guide/fx-events/image63.png)    | <span data-ttu-id="4c2f2-235">**Zestaw dat systemu** (*fx_system_date_set*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-235">**System Date Set** (*fx_system_date_set*)</span></span> |
| ![Ikona inicjowania systemu](./media/user-guide/fx-events/image64.png)    | <span data-ttu-id="4c2f2-237">**Inicjowanie systemu** (*fx_system_initialize*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-237">**System Initialize** (*fx_system_initialize*)</span></span> |
| ![Ikona uzyskiwania czasu systemowego](./media/user-guide/fx-events/image65.png)    | <span data-ttu-id="4c2f2-239">**Pobieranie czasu systemu** (*fx_system_time_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-239">**System Time Get** (*fx_system_time_get*)</span></span> |
| ![Ikona Ustawienia czasu systemowego](./media/user-guide/fx-events/image66.png)    | <span data-ttu-id="4c2f2-241">**Zestaw czasu systemu** (*fx_system_time_set*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-241">**System Time Set** (*fx_system_time_set*)</span></span> |
| ![Ikona tworzenia katalogu Unicode](./media/user-guide/fx-events/image67.png)    | <span data-ttu-id="4c2f2-243">**Tworzenie katalogu Unicode** (*fx_unicode_directory_create*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-243">**Unicode Directory Create** (*fx_unicode_directory_create*)</span></span> |
| ![Ikona zmiany nazwy katalogu Unicode](./media/user-guide/fx-events/image68.png)    | <span data-ttu-id="4c2f2-245">**Zmiana nazwy katalogu Unicode** (*fx_unicode_directory_rename*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-245">**Unicode Directory Rename** (*fx_unicode_directory_rename*)</span></span> |
| ![Ikona tworzenia pliku Unicode](./media/user-guide/fx-events/image69.png)    | <span data-ttu-id="4c2f2-247">**Tworzenie pliku Unicode** (*fx_unicode_file_create*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-247">**Unicode File Create** (*fx_unicode_file_create*)</span></span> |
| ![Ikona zmiany nazwy pliku Unicode](./media/user-guide/fx-events/image70.png)    | <span data-ttu-id="4c2f2-249">**Zmiana nazwy pliku Unicode** (*fx_unicode_file_rename*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-249">**Unicode File Rename** (*fx_unicode_file_rename*)</span></span> |
| ![Ikona pobierania Unicode Długość](./media/user-guide/fx-events/image71.png)    | <span data-ttu-id="4c2f2-251">**Długość Unicode — pobieranie** (*fx_unicode_length_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-251">**Unicode Lenght Get** (*fx_unicode_length_get*)</span></span> |
| ![Ikona pobierania nazwy Unicode](./media/user-guide/fx-events/image72.png)    | <span data-ttu-id="4c2f2-253">**Pobieranie nazwy Unicode** (*fx_unicode_name_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-253">**Unicode Name Get** (*fx_unicode_name_get*)</span></span> |
| ![Ikona pobierania krótkiej nazwy Unicode](./media/user-guide/fx-events/image73.png)    | <span data-ttu-id="4c2f2-255">**Pobieranie krótkiej nazwy Unicode** (*fx_unicode_short_name_get*)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-255">**Unicode Short Name Get** (*fx_unicode_short_name_get*)</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="4c2f2-256">Opisy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="4c2f2-256">Event Descriptions</span></span>

<span data-ttu-id="4c2f2-257">Poniżej opisano poszczególne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-257">The following describes each individual event.</span></span>

### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="4c2f2-258">Chybienia w pamięci podręcznej wewnętrznego sektora logicznego</span><span class="sxs-lookup"><span data-stu-id="4c2f2-258">Internal Logical Sector Cache Miss</span></span> 

#### <a name="internal-logical-sector-cache-miss"></a><span data-ttu-id="4c2f2-259">Chybienia w pamięci podręcznej wewnętrznego sektora logicznego</span><span class="sxs-lookup"><span data-stu-id="4c2f2-259">Internal logical sector cache miss</span></span>

<span data-ttu-id="4c2f2-260">**Ikona** ![ Ikona chybień wewnętrznej pamięci podręcznej sektora logicznego](./media/user-guide/fx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-260">**Icon** ![Internal logical sector cache miss icon](./media/user-guide/fx-events/image1.png)</span></span>

<span data-ttu-id="4c2f2-261">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-261">**Description**</span></span>

<span data-ttu-id="4c2f2-262">To zdarzenie reprezentuje błąd wewnętrzny FileX pamięci podręcznej sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-262">This event represents an internal FileX logical sector cache miss.</span></span>

<span data-ttu-id="4c2f2-263">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-263">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-264">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-264">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-265">Pole informacji 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-265">Info Field 2: Sector.</span></span>
- <span data-ttu-id="4c2f2-266">Pole informacji 3: całkowita liczba chybień.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-266">Info Field 3: Total misses.</span></span>
- <span data-ttu-id="4c2f2-267">Pole informacji 4: rozmiar pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-267">Info Field 4: Cache size.</span></span>

### <a name="internal-directory-cache-miss"></a><span data-ttu-id="4c2f2-268">Chybienia w pamięci podręcznej katalogów wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="4c2f2-268">Internal Directory Cache Miss</span></span>

#### <a name="internal-directory-cache-miss"></a><span data-ttu-id="4c2f2-269">Chybienia w pamięci podręcznej katalogów wewnętrznych</span><span class="sxs-lookup"><span data-stu-id="4c2f2-269">Internal directory cache miss</span></span>

<span data-ttu-id="4c2f2-270">**Ikona** ![ Ikona chybień w pamięci podręcznej katalogów wewnętrznych](./media/user-guide/fx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-270">**Icon** ![Internal directory cache miss icon](./media/user-guide/fx-events/image2.png)</span></span>

<span data-ttu-id="4c2f2-271">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-271">**Description**</span></span> 

<span data-ttu-id="4c2f2-272">To zdarzenie reprezentuje wewnętrzny chybień w pamięci podręcznej usługi FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-272">This event represents an internal FileX directory cache miss.</span></span>

<span data-ttu-id="4c2f2-273">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-273">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-274">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-274">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-275">Pole informacji 2: całkowita liczba chybień.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-275">Info Field 2: Total misses.</span></span>
- <span data-ttu-id="4c2f2-276">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-276">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-277">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-277">Info Field 4: Not used.</span></span>

### <a name="internal-media-flush"></a><span data-ttu-id="4c2f2-278">Wewnętrzne opróżnianie nośnika</span><span class="sxs-lookup"><span data-stu-id="4c2f2-278">Internal Media Flush</span></span> 

#### <a name="internal-media-flush"></a><span data-ttu-id="4c2f2-279">Wewnętrzne opróżnianie nośnika</span><span class="sxs-lookup"><span data-stu-id="4c2f2-279">Internal media flush</span></span>

<span data-ttu-id="4c2f2-280">**Ikona** ![ Ikona opróżniania nośnika wewnętrznego](./media/user-guide/fx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-280">**Icon** ![Internal media flush icon](./media/user-guide/fx-events/image3.png)</span></span>

<span data-ttu-id="4c2f2-281">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-281">**Description**</span></span>

<span data-ttu-id="4c2f2-282">To zdarzenie reprezentuje wewnętrzne opróżnianie nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-282">This event represents an internal FileX media flush.</span></span>

<span data-ttu-id="4c2f2-283">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-283">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-284">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-284">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-285">Pole informacji 2: liczba zanieczyszczonych sektorów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-285">Info Field 2: Number of dirty sectors.</span></span>
- <span data-ttu-id="4c2f2-286">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-286">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-287">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-287">Info Field 4: Not used.</span></span>


### <a name="internal-directory-entry-read"></a><span data-ttu-id="4c2f2-288">Odczyt wpisu katalogu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="4c2f2-288">Internal Directory Entry Read</span></span> 

#### <a name="internal-directory-entry-read"></a><span data-ttu-id="4c2f2-289">Odczyt wpisu katalogu wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="4c2f2-289">Internal directory entry read</span></span>

<span data-ttu-id="4c2f2-290">**Ikona** ![ Ikona odczytu wpisu katalogu wewnętrznego](./media/user-guide/fx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-290">**Icon** ![Internal directory entry read icon](./media/user-guide/fx-events/image4.png)</span></span>

<span data-ttu-id="4c2f2-291">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-291">**Description**</span></span>

<span data-ttu-id="4c2f2-292">To zdarzenie reprezentuje zdarzenie odczytu wewnętrznego katalogu FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-292">This event represents an internal FileX directory entry read event.</span></span>

<span data-ttu-id="4c2f2-293">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-293">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-294">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-294">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-295">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-295">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-296">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-296">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-297">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-297">Info Field 4: Not used.</span></span>

### <a name="internal-directory-entry-write"></a><span data-ttu-id="4c2f2-298">Zapis wpisu w katalogu wewnętrznym</span><span class="sxs-lookup"><span data-stu-id="4c2f2-298">Internal Directory Entry Write</span></span>

#### <a name="internal-directory-entry-write"></a><span data-ttu-id="4c2f2-299">Zapis wpisu w katalogu wewnętrznym</span><span class="sxs-lookup"><span data-stu-id="4c2f2-299">Internal directory entry write</span></span>

<span data-ttu-id="4c2f2-300">**Ikona** ![ Ikona zapisu w katalogu wewnętrznym](./media/user-guide/fx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-300">**Icon** ![Internal directory entry write icon](./media/user-guide/fx-events/image5.png)</span></span>

<span data-ttu-id="4c2f2-301">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-301">**Description**</span></span>

<span data-ttu-id="4c2f2-302">To zdarzenie reprezentuje zdarzenie zapisu wewnętrznego wpisu katalogu FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-302">This event represents an internal FileX directory entry write event.</span></span>

<span data-ttu-id="4c2f2-303">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-303">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-304">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-304">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-305">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-305">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-306">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-306">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-307">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-307">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-read"></a><span data-ttu-id="4c2f2-308">Odczyt wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-308">Internal I/O Driver Read</span></span> 

#### <a name="internal-io-driver-read"></a><span data-ttu-id="4c2f2-309">Odczyt wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-309">Internal I/O driver read</span></span> 

<span data-ttu-id="4c2f2-310">**Ikona** ![ Ikona odczytu wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-310">**Icon** ![Internal I / O driver read icon](./media/user-guide/fx-events/image6.png)</span></span>

<span data-ttu-id="4c2f2-311">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-311">**Description**</span></span> 

<span data-ttu-id="4c2f2-312">To zdarzenie reprezentuje zdarzenie odczytu sterownika wewnętrznego FileX we/wy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-312">This event represents an internal FileX I/O driver read event.</span></span>

<span data-ttu-id="4c2f2-313">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-313">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-314">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-314">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-315">Pole informacji 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-315">Info Field 2: Sector.</span></span>
- <span data-ttu-id="4c2f2-316">Pole informacji 3: liczba sektorów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-316">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="4c2f2-317">Pole informacji 4: wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-317">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-write"></a><span data-ttu-id="4c2f2-318">Zapis wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-318">Internal I/O Driver Write</span></span> 

#### <a name="internal-io-driver-write"></a><span data-ttu-id="4c2f2-319">Zapis wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-319">Internal I/O driver write</span></span> 

<span data-ttu-id="4c2f2-320">**Ikona** ![ Ikona wewnętrznego zapisu sterownika we/wy](./media/user-guide/fx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-320">**Icon** ![Internal I / O driver write icon](./media/user-guide/fx-events/image7.png)</span></span>

<span data-ttu-id="4c2f2-321">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-321">**Description**</span></span> 

<span data-ttu-id="4c2f2-322">To zdarzenie reprezentuje zdarzenie zapisu wewnętrznego FileX we/wy sterownika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-322">This event represents an internal FileX I/O driver write event.</span></span>

<span data-ttu-id="4c2f2-323">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-323">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-324">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-324">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-325">Pole informacji 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-325">Info Field 2: Sector.</span></span>
- <span data-ttu-id="4c2f2-326">Pole informacji 3: liczba sektorów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-326">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="4c2f2-327">Pole informacji 4: wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-327">Info Field 4: Buffer pointer.</span></span>

### <a name="internal-io-driver-flush"></a><span data-ttu-id="4c2f2-328">Wewnętrzny opróżnia sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-328">Internal I/O Driver Flush</span></span> 

#### <a name="internal-io-driver-flush"></a><span data-ttu-id="4c2f2-329">Wewnętrzny opróżnia sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-329">Internal I/O driver flush</span></span> 

<span data-ttu-id="4c2f2-330">**Ikona** ![ Ikona opróżniania sterownika wewnętrznego we/wy](./media/user-guide/fx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-330">**Icon** ![Internal I / O driver flush icon](./media/user-guide/fx-events/image8.png)</span></span>

<span data-ttu-id="4c2f2-331">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-331">**Description**</span></span> 

<span data-ttu-id="4c2f2-332">To zdarzenie reprezentuje zdarzenie FileX wewnętrznego opróżniania sterownika we/wy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-332">This event represents an internal FileX I/O driver flush event.</span></span>

<span data-ttu-id="4c2f2-333">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-333">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-334">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-334">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-335">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-335">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-336">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-336">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-337">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-337">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-abort"></a><span data-ttu-id="4c2f2-338">Przerwanie wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-338">Internal I/O Driver Abort</span></span> 

#### <a name="internal-io-dirver-abort"></a><span data-ttu-id="4c2f2-339">Przerwanie wewnętrznego wejścia/wyjścia dirver</span><span class="sxs-lookup"><span data-stu-id="4c2f2-339">Internal I/O dirver abort</span></span>

<span data-ttu-id="4c2f2-340">**Ikona** ![ Ikona przerwania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-340">**Icon** ![Internal I / O driver abort icon](./media/user-guide/fx-events/image9.png)</span></span>

<span data-ttu-id="4c2f2-341">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-341">**Description**</span></span>

<span data-ttu-id="4c2f2-342">To zdarzenie reprezentuje zdarzenie przerwania wewnętrznego sterownika wejścia/wyjścia FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-342">This event represents an internal FileX I/O driver abort event.</span></span>

<span data-ttu-id="4c2f2-343">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-343">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-344">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-344">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-345">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-345">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-346">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-346">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-347">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-347">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-initialize"></a><span data-ttu-id="4c2f2-348">Inicjowanie wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-348">Internal I/O Driver Initialize</span></span> 

#### <a name="internal-io-driver-initialize"></a><span data-ttu-id="4c2f2-349">Inicjowanie wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-349">Internal I/O driver initialize</span></span> 

<span data-ttu-id="4c2f2-350">**Ikona** ![ Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-350">**Icon** ![Internal I / O driver initialize icon](./media/user-guide/fx-events/image10.png)</span></span>

<span data-ttu-id="4c2f2-351">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-351">**Description**</span></span> 

<span data-ttu-id="4c2f2-352">To zdarzenie reprezentuje zdarzenie inicjowania sterownika wewnętrznego FileX we/wy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-352">This event represents an internal FileX I/O driver initialize event.</span></span>

<span data-ttu-id="4c2f2-353">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-353">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-354">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-354">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-355">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-355">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-356">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-356">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-357">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-357">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="4c2f2-358">Odczyt wewnętrznego sektora rozruchowego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-358">Internal I/O Driver Boot Sector Read</span></span> 

#### <a name="internal-io-driver-boot-sector-read"></a><span data-ttu-id="4c2f2-359">Odczyt wewnętrznego sektora rozruchowego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-359">Internal I/O driver boot sector read</span></span> 

<span data-ttu-id="4c2f2-360">**Ikona** ![ Ikona odczytu wewnętrznego sektora rozruchowego sterownika we/wy](./media/user-guide/fx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-360">**Icon** ![Internal I / O driver boot sector read icon](./media/user-guide/fx-events/image11.png)</span></span>

<span data-ttu-id="4c2f2-361">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-361">**Description**</span></span> 

<span data-ttu-id="4c2f2-362">To zdarzenie reprezentuje zdarzenie odczytu sektora rozruchowego wewnętrznego sterownika we/wy FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-362">This event represents an internal FileX I/O driver boot sector read event.</span></span>

<span data-ttu-id="4c2f2-363">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-363">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-364">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-364">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-365">Pole informacji 2: wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-365">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="4c2f2-366">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-366">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-367">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-367">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="4c2f2-368">Sektory wersji wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-368">Internal I/O Driver Release Sectors</span></span> 

#### <a name="internal-io-driver-release-sectors"></a><span data-ttu-id="4c2f2-369">Sektory wersji wewnętrznego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-369">Internal I/O driver release sectors</span></span> 

<span data-ttu-id="4c2f2-370">**Ikona** ![ Ikona wewnętrznych sektorów sterowników we/wy](./media/user-guide/fx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-370">**Icon** ![Internal I / O driver release sectors icon](./media/user-guide/fx-events/image12.png)</span></span>

<span data-ttu-id="4c2f2-371">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-371">**Description**</span></span> 

<span data-ttu-id="4c2f2-372">To zdarzenie reprezentuje zdarzenie wewnętrznego sektora FileX we/wy sterownika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-372">This event represents an internal FileX I/O driver release sectors event.</span></span>

<span data-ttu-id="4c2f2-373">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-373">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-374">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-374">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-375">Pole informacji 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-375">Info Field 2: Sector.</span></span>
- <span data-ttu-id="4c2f2-376">Pole informacji 3: liczba sektorów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-376">Info Field 3: Number of sectors.</span></span>
- <span data-ttu-id="4c2f2-377">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-377">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="4c2f2-378">Zapis wewnętrznego sektora rozruchowego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-378">Internal I/O Driver Boot Sector Write</span></span>

#### <a name="internal-io-driver-boot-sector-write"></a><span data-ttu-id="4c2f2-379">Zapis wewnętrznego sektora rozruchowego sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-379">Internal I/O driver boot sector write</span></span> 

<span data-ttu-id="4c2f2-380">**Ikona** ![ Ikona zapisu wewnętrznego sektora rozruchowego sterownika we/wy](./media/user-guide/fx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-380">**Icon** ![Internal I / O driver boot sector write icon](./media/user-guide/fx-events/image13.png)</span></span>

<span data-ttu-id="4c2f2-381">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-381">**Description**</span></span> 

<span data-ttu-id="4c2f2-382">To zdarzenie reprezentuje zdarzenie zapisu sektora rozruchowego wewnętrznego sterownika we/wy FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-382">This event represents an internal FileX I/O driver boot sector write event.</span></span>

<span data-ttu-id="4c2f2-383">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-383">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-384">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-384">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-385">Pole informacji 2: wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-385">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="4c2f2-386">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-386">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-387">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-387">Info Field 4: Not used.</span></span>

### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="4c2f2-388">Wewnętrzny sterownik we/wy — anulowanie inicjalizacji</span><span class="sxs-lookup"><span data-stu-id="4c2f2-388">Internal I/O Driver Un-initialize</span></span> 

#### <a name="internal-io-driver-un-initialize"></a><span data-ttu-id="4c2f2-389">Wewnętrzny sterownik we/wy — anulowanie inicjalizacji</span><span class="sxs-lookup"><span data-stu-id="4c2f2-389">Internal I/O driver un-initialize</span></span> 

<span data-ttu-id="4c2f2-390">**Ikona** ![ Ikona anulowania inicjowania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-390">**Icon** ![Internal I / O driver un-initialize icon](./media/user-guide/fx-events/image14.png)</span></span>

<span data-ttu-id="4c2f2-391">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-391">**Description**</span></span> 

<span data-ttu-id="4c2f2-392">To zdarzenie reprezentuje zdarzenie anulowania inicjalizacji wewnętrznego sterownika we/wy FileX.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-392">This event represents an internal FileX I/O driver un-initialize event.</span></span>

<span data-ttu-id="4c2f2-393">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-393">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-394">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-394">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-395">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-395">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-396">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-396">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-397">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-397">Info Field 4: Not used.</span></span>
</blockquote></td>

### <a name="directory-attributes-read"></a><span data-ttu-id="4c2f2-398">Odczyt atrybutów katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-398">Directory Attributes Read</span></span> 

#### <a name="fx_directory_attributes_read"></a><span data-ttu-id="4c2f2-399">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="4c2f2-399">fx_directory_attributes_read</span></span> 

<span data-ttu-id="4c2f2-400">**Ikona** ![ Ikona odczytu atrybutów katalogu](./media/user-guide/fx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-400">**Icon** ![Directory attributes read icon](./media/user-guide/fx-events/image15.png)</span></span>

<span data-ttu-id="4c2f2-401">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-401">**Description**</span></span> 

<span data-ttu-id="4c2f2-402">To zdarzenie reprezentuje zdarzenie odczytu atrybutów katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-402">This event represents a directory attributes read event.</span></span>

<span data-ttu-id="4c2f2-403">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-403">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-404">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-404">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-405">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-405">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-406">Pole informacji 3: Mapa bitów atrybutów:</span><span class="sxs-lookup"><span data-stu-id="4c2f2-406">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="4c2f2-407">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4c2f2-407">Attribute</span></span>                         | <span data-ttu-id="4c2f2-408">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c2f2-408">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="4c2f2-409">Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-409">Read Only</span></span>                        | <span data-ttu-id="4c2f2-410">0x01</span><span class="sxs-lookup"><span data-stu-id="4c2f2-410">(0x01)</span></span>  |
  |  <span data-ttu-id="4c2f2-411">Ukryty</span><span class="sxs-lookup"><span data-stu-id="4c2f2-411">Hidden</span></span>                           | <span data-ttu-id="4c2f2-412">0x02</span><span class="sxs-lookup"><span data-stu-id="4c2f2-412">(0x02)</span></span>  |
  |  <span data-ttu-id="4c2f2-413">System</span><span class="sxs-lookup"><span data-stu-id="4c2f2-413">System</span></span>                           | <span data-ttu-id="4c2f2-414">(0x04)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-414">(0x04)</span></span>  |
  |  <span data-ttu-id="4c2f2-415">Wolumin</span><span class="sxs-lookup"><span data-stu-id="4c2f2-415">Volume</span></span>                           | <span data-ttu-id="4c2f2-416">(0x08)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-416">(0x08)</span></span>  |
  |  <span data-ttu-id="4c2f2-417">Katalog</span><span class="sxs-lookup"><span data-stu-id="4c2f2-417">Directory</span></span>                        | <span data-ttu-id="4c2f2-418">0x10</span><span class="sxs-lookup"><span data-stu-id="4c2f2-418">(0x10)</span></span>  |
  |  <span data-ttu-id="4c2f2-419">Archiwum</span><span class="sxs-lookup"><span data-stu-id="4c2f2-419">Archive</span></span>                          | <span data-ttu-id="4c2f2-420">0x20</span><span class="sxs-lookup"><span data-stu-id="4c2f2-420">(0x20)</span></span>  |
- <span data-ttu-id="4c2f2-421">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-421">Info Field 4: Not used.</span></span>

### <a name="directory-attributes-set"></a><span data-ttu-id="4c2f2-422">Zestaw atrybutów katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-422">Directory Attributes Set</span></span> 

#### <a name="fx_directory_attributes_set"></a><span data-ttu-id="4c2f2-423">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="4c2f2-423">fx_directory_attributes_set</span></span> 

<span data-ttu-id="4c2f2-424">**Ikona** ![ Ikona zestawu atrybutów](./media/user-guide/fx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-424">**Icon** ![Attributes set icon](./media/user-guide/fx-events/image16.png)</span></span>

<span data-ttu-id="4c2f2-425">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-425">**Description**</span></span> 

<span data-ttu-id="4c2f2-426">To zdarzenie reprezentuje katalog a zdarzenia zestawu atrybutów katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-426">This event represents a directory a directory attributes set event.</span></span>

<span data-ttu-id="4c2f2-427">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-427">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-428">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-428">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-429">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-429">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-430">Pole informacji 3: Mapa bitów atrybutów:</span><span class="sxs-lookup"><span data-stu-id="4c2f2-430">Info Field 3: Attributes bit map:</span></span>

  |  <span data-ttu-id="4c2f2-431">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4c2f2-431">Attribute</span></span>                        | <span data-ttu-id="4c2f2-432">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c2f2-432">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="4c2f2-433">Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-433">Read Only</span></span>                        | <span data-ttu-id="4c2f2-434">0x01</span><span class="sxs-lookup"><span data-stu-id="4c2f2-434">(0x01)</span></span>  |
  |  <span data-ttu-id="4c2f2-435">Ukryty</span><span class="sxs-lookup"><span data-stu-id="4c2f2-435">Hidden</span></span>                           | <span data-ttu-id="4c2f2-436">0x02</span><span class="sxs-lookup"><span data-stu-id="4c2f2-436">(0x02)</span></span>  |
  |  <span data-ttu-id="4c2f2-437">System</span><span class="sxs-lookup"><span data-stu-id="4c2f2-437">System</span></span>                           | <span data-ttu-id="4c2f2-438">(0x04)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-438">(0x04)</span></span>  |
  |  <span data-ttu-id="4c2f2-439">Archiwum</span><span class="sxs-lookup"><span data-stu-id="4c2f2-439">Archive</span></span>                          | <span data-ttu-id="4c2f2-440">0x20</span><span class="sxs-lookup"><span data-stu-id="4c2f2-440">(0x20)</span></span>  |
- <span data-ttu-id="4c2f2-441">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-441">Info Field 4: Not used.</span></span>

### <a name="directory-create"></a><span data-ttu-id="4c2f2-442">Tworzenie katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-442">Directory Create</span></span> 

#### <a name="fx_directory_create"></a><span data-ttu-id="4c2f2-443">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="4c2f2-443">fx_directory_create</span></span>

<span data-ttu-id="4c2f2-444">**Ikona** ![ Ikona tworzenia katalogu](./media/user-guide/fx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-444">**Icon** ![Directory create icon](./media/user-guide/fx-events/image17.png)</span></span>

<span data-ttu-id="4c2f2-445">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-445">**Description**</span></span> 

<span data-ttu-id="4c2f2-446">To zdarzenie reprezentuje zdarzenie utworzenia katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-446">This event represents a directory create event.</span></span>

<span data-ttu-id="4c2f2-447">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-447">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-448">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-448">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-449">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-449">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-450">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-451">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-451">Info Field 4: Not used.</span></span>

### <a name="directory-default-get"></a><span data-ttu-id="4c2f2-452">Domyślne pobieranie katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-452">Directory Default Get</span></span> 

#### <a name="fx_directory_default_get"></a><span data-ttu-id="4c2f2-453">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-453">fx_directory_default_get</span></span> 

<span data-ttu-id="4c2f2-454">**Ikona** ![ Ikona pobierania domyślnego katalogu](./media/user-guide/fx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-454">**Icon** ![Directory default get icon](./media/user-guide/fx-events/image18.png)</span></span>

<span data-ttu-id="4c2f2-455">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-455">**Description**</span></span> 

<span data-ttu-id="4c2f2-456">To zdarzenie reprezentuje zdarzenie domyślnego zestawu katalogów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-456">This event represents a directory default set event.</span></span>

<span data-ttu-id="4c2f2-457">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-457">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-458">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-458">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-459">Pole informacji 2: wskaźnik do zwrócenia nazwy ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-459">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="4c2f2-460">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-461">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-461">Info Field 4: Not used.</span></span>

### <a name="directory-default-set"></a><span data-ttu-id="4c2f2-462">Domyślny zestaw katalogów</span><span class="sxs-lookup"><span data-stu-id="4c2f2-462">Directory Default Set</span></span> 

#### <a name="fx_directory_default_set"></a><span data-ttu-id="4c2f2-463">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="4c2f2-463">fx_directory_default_set</span></span> 

<span data-ttu-id="4c2f2-464">**Ikona** ![ Ikona domyślnego zestawu katalogów](./media/user-guide/fx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-464">**Icon** ![Directory default set icon](./media/user-guide/fx-events/image19.png)</span></span>

<span data-ttu-id="4c2f2-465">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-465">**Description**</span></span> 

<span data-ttu-id="4c2f2-466">To zdarzenie reprezentuje zdarzenie domyślnego zestawu katalogów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-466">This event represents a directory default set event.</span></span>

<span data-ttu-id="4c2f2-467">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-467">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-468">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-468">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-469">Pole informacji 2: wskaźnik do nowej nazwy ścieżki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-469">Info Field 2: Pointer to new default path name.</span></span>
- <span data-ttu-id="4c2f2-470">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-471">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-471">Info Field 4: Not used.</span></span>

### <a name="directory-delete"></a><span data-ttu-id="4c2f2-472">Usuwanie katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-472">Directory Delete</span></span> 

#### <a name="fx_directory_delete"></a><span data-ttu-id="4c2f2-473">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="4c2f2-473">fx_directory_delete</span></span>

<span data-ttu-id="4c2f2-474">**Ikona** ![ Ikona usuwania katalogu](./media/user-guide/fx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-474">**Icon** ![Directory delete icon](./media/user-guide/fx-events/image20.png)</span></span>

<span data-ttu-id="4c2f2-475">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-475">**Description**</span></span> 

<span data-ttu-id="4c2f2-476">To zdarzenie reprezentuje zdarzenie usunięcia katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-476">This event represents a directory delete event.</span></span>

<span data-ttu-id="4c2f2-477">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-477">**Information Fields**</span></span>
- <span data-ttu-id="4c2f2-478">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-478">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-479">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-479">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-480">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-481">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-481">Info Field 4: Not used.</span></span>

### <a name="directory-first-entry-find"></a><span data-ttu-id="4c2f2-482">Znajdowanie pierwszego wpisu katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-482">Directory First Entry Find</span></span> 

#### <a name="fx_directory_first_entry_find"></a><span data-ttu-id="4c2f2-483">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="4c2f2-483">fx_directory_first_entry_find</span></span>

<span data-ttu-id="4c2f2-484">**Ikona** ![ Ikona wyszukiwania pierwszego wpisu katalogu](./media/user-guide/fx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-484">**Icon** ![Directory first entry find icon](./media/user-guide/fx-events/image21.png)</span></span>

<span data-ttu-id="4c2f2-485">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-485">**Description**</span></span> 

<span data-ttu-id="4c2f2-486">To zdarzenie reprezentuje zdarzenie Find pierwszego wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-486">This event represents a directory first entry find event.</span></span>

<span data-ttu-id="4c2f2-487">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-487">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-488">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-488">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-489">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-489">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-490">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-491">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-491">Info Field 4: Not used.</span></span>

### <a name="directory-first-full-entry-find"></a><span data-ttu-id="4c2f2-492">Znajdź pierwszy pełny wpis w katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-492">Directory First Full Entry Find</span></span> 

#### <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="4c2f2-493">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="4c2f2-493">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="4c2f2-494">**Ikona** ![ Ikona wyszukiwania pierwszego wpisu katalogu](./media/user-guide/fx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-494">**Icon** ![Directory first full entry find icon](./media/user-guide/fx-events/image22.png)</span></span>

<span data-ttu-id="4c2f2-495">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-495">**Description**</span></span> 

<span data-ttu-id="4c2f2-496">To zdarzenie reprezentuje zdarzenie znajdowania pierwszego pełnego wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-496">This event represents a directory first full entry find event.</span></span>

<span data-ttu-id="4c2f2-497">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-497">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-498">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-498">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-499">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-499">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-500">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-501">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-501">Info Field 4: Not used.</span></span>

### <a name="directory-information-get"></a><span data-ttu-id="4c2f2-502">Pobieranie informacji o katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-502">Directory Information Get</span></span> 

#### <a name="fx_directory_information_get"></a><span data-ttu-id="4c2f2-503">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-503">fx_directory_information_get</span></span>

<span data-ttu-id="4c2f2-504">**Ikona** ![ Ikona uzyskiwania informacji o katalogu](./media/user-guide/fx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-504">**Icon** ![Directory information get icon](./media/user-guide/fx-events/image23.png)</span></span>

<span data-ttu-id="4c2f2-505">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-505">**Description**</span></span> 

<span data-ttu-id="4c2f2-506">To zdarzenie reprezentuje zdarzenie pobrania informacji o katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-506">This event represents a directory information get event.</span></span>

<span data-ttu-id="4c2f2-507">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-507">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-508">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-508">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-509">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-509">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-510">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-510">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-511">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-511">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-clear"></a><span data-ttu-id="4c2f2-512">Ścieżka lokalna katalogu jest niezrozumiała</span><span class="sxs-lookup"><span data-stu-id="4c2f2-512">Directory Local Path Clear</span></span> 

#### <a name="fx_directory_local_path_clear"></a><span data-ttu-id="4c2f2-513">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="4c2f2-513">fx_directory_local_path_clear</span></span>

<span data-ttu-id="4c2f2-514">**Ikona** ![ Ikona czyszczenia ścieżki lokalnej katalogu](./media/user-guide/fx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-514">**Icon** ![Directory local path clear icon](./media/user-guide/fx-events/image24.png)</span></span>

<span data-ttu-id="4c2f2-515">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-515">**Description**</span></span> 

<span data-ttu-id="4c2f2-516">To zdarzenie reprezentuje zdarzenie czyszczenia ścieżki lokalnej dla katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-516">This event represents a directory local path clear event.</span></span>

<span data-ttu-id="4c2f2-517">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-517">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-518">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-518">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-519">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-520">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-521">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-521">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-get"></a><span data-ttu-id="4c2f2-522">Pobieranie ścieżki lokalnej katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-522">Directory Local Path Get</span></span> 

#### <a name="fx_directory_local_path_get"></a><span data-ttu-id="4c2f2-523">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-523">fx_directory_local_path_get</span></span>

<span data-ttu-id="4c2f2-524">**Ikona** ![ Ikona pobierania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-524">**Icon** ![Directory local path get icon](./media/user-guide/fx-events/image25.png)</span></span>

<span data-ttu-id="4c2f2-525">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-525">**Description**</span></span> 

<span data-ttu-id="4c2f2-526">To zdarzenie reprezentuje zdarzenie pobrania ścieżki lokalnej katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-526">This event represents a directory local path get event.</span></span>

<span data-ttu-id="4c2f2-527">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-527">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-528">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-528">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-529">Pole informacji 2: wskaźnik do zwrócenia nazwy ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-529">Info Field 2: Pointer to return path name.</span></span>
- <span data-ttu-id="4c2f2-530">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-531">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-531">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-restore"></a><span data-ttu-id="4c2f2-532">Przywracanie ścieżki lokalnej katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-532">Directory Local Path Restore</span></span> 

#### <a name="fx_directory_local_path_restore"></a><span data-ttu-id="4c2f2-533">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="4c2f2-533">fx_directory_local_path_restore</span></span>

<span data-ttu-id="4c2f2-534">**Ikona** ![ Ikona przywracania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-534">**Icon** ![Directory local path restore icon](./media/user-guide/fx-events/image26.png)</span></span>

<span data-ttu-id="4c2f2-535">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-535">**Description**</span></span> 

<span data-ttu-id="4c2f2-536">To zdarzenie reprezentuje zdarzenie przywracania ścieżki lokalnej katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-536">This event represents a directory local path restore event.</span></span>

<span data-ttu-id="4c2f2-537">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-537">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-538">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-538">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-539">Pole informacji 2: wskaźnik do struktury ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-539">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="4c2f2-540">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-540">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-541">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-541">Info Field 4: Not used.</span></span>

### <a name="directory-local-path-set"></a><span data-ttu-id="4c2f2-542">Ustawiona ścieżka lokalna katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-542">Directory Local Path Set</span></span> 

#### <a name="fx_directory_local_path_set"></a><span data-ttu-id="4c2f2-543">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="4c2f2-543">fx_directory_local_path_set</span></span>

<span data-ttu-id="4c2f2-544">**Ikona** ![ Ikona zestawu ścieżek lokalnych katalogu](./media/user-guide/fx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-544">**Icon** ![Directory local path set icon](./media/user-guide/fx-events/image27.png)</span></span>

<span data-ttu-id="4c2f2-545">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-545">**Description**</span></span> 

<span data-ttu-id="4c2f2-546">To zdarzenie reprezentuje zdarzenie lokalnego ustawienia ścieżki katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-546">This event represents a directory local path set event.</span></span>

<span data-ttu-id="4c2f2-547">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-547">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-548">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-548">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-549">Pole informacji 2: wskaźnik do struktury ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-549">Info Field 2: Pointer to local path structure.</span></span>
- <span data-ttu-id="4c2f2-550">Pole informacji 3: wskaźnik do nowej nazwy ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-550">Info Field 3: Pointer to new path name.</span></span>
- <span data-ttu-id="4c2f2-551">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-551">Info Field 4: Not used.</span></span>

### <a name="directory-long-name-get"></a><span data-ttu-id="4c2f2-552">Pobieranie długiej nazwy katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-552">Directory Long Name Get</span></span> 

#### <a name="fx_directory_long_name_get"></a><span data-ttu-id="4c2f2-553">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-553">fx_directory_long_name_get</span></span>

<span data-ttu-id="4c2f2-554">**Ikona** ![ Ikona pobierania długich nazw katalogów](./media/user-guide/fx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-554">**Icon** ![Directory long name get icon](./media/user-guide/fx-events/image28.png)</span></span>

<span data-ttu-id="4c2f2-555">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-555">**Description**</span></span> 

<span data-ttu-id="4c2f2-556">To zdarzenie reprezentuje zdarzenie pobrania długich nazw katalogów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-556">This event represents a directory long name get event.</span></span>

<span data-ttu-id="4c2f2-557">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-557">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-558">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-558">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-559">Pole informacji 2: wskaźnik do krótkiej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-559">Info Field 2: Pointer to short file name.</span></span>
- <span data-ttu-id="4c2f2-560">Pole informacji 3: wskaźnik do długiej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-560">Info Field 3: Pointer to long file name.</span></span>
- <span data-ttu-id="4c2f2-561">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-561">Info Field 4: Not used.</span></span>

### <a name="directory-name-test"></a><span data-ttu-id="4c2f2-562">Test nazwy katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-562">Directory Name Test</span></span> 

#### <a name="fx_directory_name_test"></a><span data-ttu-id="4c2f2-563">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="4c2f2-563">fx_directory_name_test</span></span>

<span data-ttu-id="4c2f2-564">**Ikona** ![ Ikona testu nazwy katalogu](./media/user-guide/fx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-564">**Icon** ![Directory name test icon](./media/user-guide/fx-events/image29.png)</span></span>

<span data-ttu-id="4c2f2-565">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-565">**Description**</span></span> 

<span data-ttu-id="4c2f2-566">To zdarzenie reprezentuje zdarzenie testowe nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-566">This event represents a directory name test event.</span></span>

<span data-ttu-id="4c2f2-567">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-567">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-568">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-568">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-569">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-569">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-570">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-570">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-571">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-571">Info Field 4: Not used.</span></span>

### <a name="directory-next-entry-find"></a><span data-ttu-id="4c2f2-572">Znajdowanie wpisu w katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-572">Directory Next Entry Find</span></span> 

#### <a name="fx_directory_next_entry_find"></a><span data-ttu-id="4c2f2-573">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="4c2f2-573">fx_directory_next_entry_find</span></span>

<span data-ttu-id="4c2f2-574">**Ikona** ![ Ikona wyszukiwania następnego wpisu w katalogu](./media/user-guide/fx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-574">**Icon** ![Directory next entry find icon](./media/user-guide/fx-events/image30.png)</span></span>

<span data-ttu-id="4c2f2-575">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-575">**Description**</span></span> 

<span data-ttu-id="4c2f2-576">To zdarzenie reprezentuje zdarzenie znajdowania następnego wpisu w katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-576">This event represents a directory next entry find event.</span></span>

<span data-ttu-id="4c2f2-577">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-577">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-578">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-578">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-579">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-579">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-580">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-580">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-581">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-581">Info Field 4: Not used.</span></span>

### <a name="directory-next-full-entry-find"></a><span data-ttu-id="4c2f2-582">Znajdź następny pełny wpis w katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-582">Directory Next Full Entry Find</span></span> 

#### <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="4c2f2-583">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="4c2f2-583">fx_directory_next_full_entry_find</span></span>

<span data-ttu-id="4c2f2-584">**Ikona** ![ Ikona wyszukiwania następnego wpisu w katalogu](./media/user-guide/fx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-584">**Icon** ![Directory next full entry find icon](./media/user-guide/fx-events/image31.png)</span></span>

<span data-ttu-id="4c2f2-585">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-585">**Description**</span></span>

<span data-ttu-id="4c2f2-586">To zdarzenie reprezentuje zdarzenie Znajdź następny pełny wpis w katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-586">This event represents a directory next full entry find event.</span></span>

<span data-ttu-id="4c2f2-587">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-587">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-588">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-588">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-589">Pole informacji 2: wskaźnik do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-589">Info Field 2: Pointer to directory name.</span></span>
- <span data-ttu-id="4c2f2-590">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-590">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-591">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-591">Info Field 4: Not used.</span></span>

### <a name="directory-rename"></a><span data-ttu-id="4c2f2-592">Zmiana nazwy katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-592">Directory Rename</span></span> 

#### <a name="fx_directory_rename-event"></a><span data-ttu-id="4c2f2-593">zdarzenie fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="4c2f2-593">fx_directory_rename event</span></span>

<span data-ttu-id="4c2f2-594">**Ikona** ![ Ikona zmiany nazwy katalogu](./media/user-guide/fx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-594">**Icon** ![Directory rename icon](./media/user-guide/fx-events/image32.png)</span></span>

<span data-ttu-id="4c2f2-595">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-595">**Description**</span></span>

<span data-ttu-id="4c2f2-596">To zdarzenie reprezentuje zdarzenie zmiany nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-596">This event represents a directory rename event.</span></span>

<span data-ttu-id="4c2f2-597">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-597">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-598">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-598">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-599">Pole informacji 2: wskaźnik do starej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-599">Info Field 2: Pointer to old directory name.</span></span>
- <span data-ttu-id="4c2f2-600">Pole informacji 3: wskaźnik do nowej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-600">Info Field 3: Pointer to new directory name.</span></span>
- <span data-ttu-id="4c2f2-601">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-601">Info Field 4: Not used.</span></span>

### <a name="directory-short-name-get"></a><span data-ttu-id="4c2f2-602">Krótka nazwa katalogu Get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-602">Directory Short Name Get</span></span> 

#### <a name="fx_directory_short_name_get"></a><span data-ttu-id="4c2f2-603">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-603">fx_directory_short_name_get</span></span>

<span data-ttu-id="4c2f2-604">**Ikona** ![ Ikona pobierania krótkiej nazwy katalogu](./media/user-guide/fx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-604">**Icon** ![Directory short name get icon](./media/user-guide/fx-events/image33.png)</span></span>

<span data-ttu-id="4c2f2-605">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-605">**Description**</span></span>

<span data-ttu-id="4c2f2-606">To zdarzenie reprezentuje zdarzenie pobrania krótkiej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-606">This event represents a directory short name get event.</span></span>

<span data-ttu-id="4c2f2-607">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-607">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-608">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-608">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-609">Pole informacji 2: wskaźnik do długiej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-609">Info Field 2: Pointer to long file name.</span></span>
- <span data-ttu-id="4c2f2-610">Pole informacji 3: wskaźnik do krótkiej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-610">Info Field 3: Pointer to short file name.</span></span>
- <span data-ttu-id="4c2f2-611">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-611">Info Field 4: Not used.</span></span>

### <a name="file-allocate"></a><span data-ttu-id="4c2f2-612">Przydział pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-612">File Allocate</span></span> 

#### <a name="fx_file_allocate"></a><span data-ttu-id="4c2f2-613">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="4c2f2-613">fx_file_allocate</span></span>

<span data-ttu-id="4c2f2-614">**Ikona** ![ Ikona alokacji plików](./media/user-guide/fx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-614">**Icon** ![File allocate icon](./media/user-guide/fx-events/image34.png)</span></span>

<span data-ttu-id="4c2f2-615">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-615">**Description**</span></span>

<span data-ttu-id="4c2f2-616">To zdarzenie reprezentuje zdarzenie przydzielenia pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-616">This event represents a file allocate event.</span></span>

<span data-ttu-id="4c2f2-617">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-617">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-618">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-618">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-619">Pole informacji 2: żądany rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-619">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="4c2f2-620">Pole informacji 3: bieżący rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-620">Info Field 3: Current size.</span></span>
- <span data-ttu-id="4c2f2-621">Pole informacji 4: nowy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-621">Info Field 4: New size.</span></span>

### <a name="file-attributes-read"></a><span data-ttu-id="4c2f2-622">Odczyt atrybutów pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-622">File Attributes Read</span></span> 

#### <a name="fx_file_attributes_read"></a><span data-ttu-id="4c2f2-623">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="4c2f2-623">fx_file_attributes_read</span></span>

<span data-ttu-id="4c2f2-624">**Ikona** ![ Ikona odczytu atrybutów plików](./media/user-guide/fx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-624">**Icon** ![File attributes read icon](./media/user-guide/fx-events/image35.png)</span></span>

<span data-ttu-id="4c2f2-625">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-625">**Description**</span></span>

<span data-ttu-id="4c2f2-626">To zdarzenie reprezentuje zdarzenie odczytu atrybutów pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-626">This event represents a file attributes read event.</span></span>

<span data-ttu-id="4c2f2-627">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-627">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-628">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-628">Info Field 1: Pointer to the media.</span></span> 
- <span data-ttu-id="4c2f2-629">Pole informacji 2: Mapa bitów atrybutów:</span><span class="sxs-lookup"><span data-stu-id="4c2f2-629">Info Field 2: Attributes bit map:</span></span>

  |  <span data-ttu-id="4c2f2-630">Stanowiąc</span><span class="sxs-lookup"><span data-stu-id="4c2f2-630">Attribut</span></span>                         | <span data-ttu-id="4c2f2-631">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c2f2-631">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="4c2f2-632">Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-632">Read Only</span></span>                        | <span data-ttu-id="4c2f2-633">0x01</span><span class="sxs-lookup"><span data-stu-id="4c2f2-633">(0x01)</span></span>  |
  |  <span data-ttu-id="4c2f2-634">Ukryty</span><span class="sxs-lookup"><span data-stu-id="4c2f2-634">Hidden</span></span>                           | <span data-ttu-id="4c2f2-635">0x02</span><span class="sxs-lookup"><span data-stu-id="4c2f2-635">(0x02)</span></span>  |
  |  <span data-ttu-id="4c2f2-636">System</span><span class="sxs-lookup"><span data-stu-id="4c2f2-636">System</span></span>                           | <span data-ttu-id="4c2f2-637">(0x04)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-637">(0x04)</span></span>  |
  |  <span data-ttu-id="4c2f2-638">Wolumin</span><span class="sxs-lookup"><span data-stu-id="4c2f2-638">Volume</span></span>                           | <span data-ttu-id="4c2f2-639">(0x08)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-639">(0x08)</span></span>  |
  |  <span data-ttu-id="4c2f2-640">Katalog</span><span class="sxs-lookup"><span data-stu-id="4c2f2-640">Directory</span></span>                        | <span data-ttu-id="4c2f2-641">0x10</span><span class="sxs-lookup"><span data-stu-id="4c2f2-641">(0x10)</span></span>  |
  |  <span data-ttu-id="4c2f2-642">Archiwum</span><span class="sxs-lookup"><span data-stu-id="4c2f2-642">Archive</span></span>                          | <span data-ttu-id="4c2f2-643">0x20</span><span class="sxs-lookup"><span data-stu-id="4c2f2-643">(0x20)</span></span>  |
- <span data-ttu-id="4c2f2-644">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-644">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-645">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-645">Info Field 4: Not used.</span></span>

### <a name="file-attributes-set"></a><span data-ttu-id="4c2f2-646">Zestaw atrybutów pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-646">File Attributes Set</span></span> 

#### <a name="fx_file_attributes_set"></a><span data-ttu-id="4c2f2-647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="4c2f2-647">fx_file_attributes_set</span></span>

<span data-ttu-id="4c2f2-648">**Ikona** ![ Ikona zestawu atrybutów pliku](./media/user-guide/fx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-648">**Icon** ![File attributes set icon](./media/user-guide/fx-events/image36.png)</span></span>

<span data-ttu-id="4c2f2-649">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-649">**Description**</span></span> 

<span data-ttu-id="4c2f2-650">To zdarzenie reprezentuje zdarzenie zestawu atrybutów pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-650">This event represents a file attributes set event.</span></span>

<span data-ttu-id="4c2f2-651">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-651">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-652">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-652">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-653">Pole informacji 2: wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-653">Info Field 2: Pointer to file name.</span></span> 
- <span data-ttu-id="4c2f2-654">Pole informacji 3: Mapa bitów atrybutów:</span><span class="sxs-lookup"><span data-stu-id="4c2f2-654">Info Field 3: Attributes bit map:</span></span>

  | <span data-ttu-id="4c2f2-655">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4c2f2-655">Attribute</span></span>                         | <span data-ttu-id="4c2f2-656">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c2f2-656">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="4c2f2-657">Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-657">Read Only</span></span>                        | <span data-ttu-id="4c2f2-658">0x01</span><span class="sxs-lookup"><span data-stu-id="4c2f2-658">(0x01)</span></span>  |
  |  <span data-ttu-id="4c2f2-659">Ukryty</span><span class="sxs-lookup"><span data-stu-id="4c2f2-659">Hidden</span></span>                           | <span data-ttu-id="4c2f2-660">0x02</span><span class="sxs-lookup"><span data-stu-id="4c2f2-660">(0x02)</span></span>  |
  |  <span data-ttu-id="4c2f2-661">System</span><span class="sxs-lookup"><span data-stu-id="4c2f2-661">System</span></span>                           | <span data-ttu-id="4c2f2-662">(0x04)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-662">(0x04)</span></span>  |
  |  <span data-ttu-id="4c2f2-663">Archiwum</span><span class="sxs-lookup"><span data-stu-id="4c2f2-663">Archive</span></span>                          | <span data-ttu-id="4c2f2-664">0x20</span><span class="sxs-lookup"><span data-stu-id="4c2f2-664">(0x20)</span></span>  |
- <span data-ttu-id="4c2f2-665">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-665">Info Field 4: Not used.</span></span>

### <a name="file-best-effort-allocate"></a><span data-ttu-id="4c2f2-666">Przydział najlepszego nakładu pracy pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-666">File Best Effort Allocate</span></span> 

#### <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="4c2f2-667">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="4c2f2-667">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="4c2f2-668">**Ikona** ![ Ikona przydziału najlepszego nakładu pracy pliku](./media/user-guide/fx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-668">**Icon** ![File best effort allocate icon](./media/user-guide/fx-events/image37.png)</span></span>

<span data-ttu-id="4c2f2-669">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-669">**Description**</span></span> 

<span data-ttu-id="4c2f2-670">To zdarzenie reprezentuje zdarzenie dotyczące przydziału najlepszego nakładu pracy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-670">This event represents a file best effort allocate event.</span></span>

<span data-ttu-id="4c2f2-671">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-671">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-672">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-672">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-673">Pole informacji 2: żądany rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-673">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="4c2f2-674">Pole informacji 3: przydzielono rzeczywisty rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-674">Info Field 3: Actual size allocated.</span></span>
- <span data-ttu-id="4c2f2-675">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-675">Info Field 4: Not used.</span></span>

### <a name="file-close"></a><span data-ttu-id="4c2f2-676">Zamknij plik</span><span class="sxs-lookup"><span data-stu-id="4c2f2-676">File Close</span></span> 

#### <a name="fx_file_close"></a><span data-ttu-id="4c2f2-677">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="4c2f2-677">fx_file_close</span></span>

<span data-ttu-id="4c2f2-678">**Ikona** ![ Ikona zamykania pliku](./media/user-guide/fx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-678">**Icon** ![File close icon](./media/user-guide/fx-events/image38.png)</span></span>

<span data-ttu-id="4c2f2-679">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-679">**Description**</span></span> 

<span data-ttu-id="4c2f2-680">To zdarzenie reprezentuje zdarzenie zamknięcia pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-680">This event represents a file close event.</span></span>

<span data-ttu-id="4c2f2-681">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-681">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-682">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-682">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-683">Pole informacji 2: rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-683">Info Field 2: File size.</span></span>
- <span data-ttu-id="4c2f2-684">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-684">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-685">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-685">Info Field 4: Not used.</span></span>

### <a name="file-create"></a><span data-ttu-id="4c2f2-686">Tworzenie pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-686">File Create</span></span>

#### <a name="fx_file_create"></a><span data-ttu-id="4c2f2-687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="4c2f2-687">fx_file_create</span></span>

<span data-ttu-id="4c2f2-688">**Ikona** ![ Ikona tworzenia pliku](./media/user-guide/fx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-688">**Icon** ![File create icon](./media/user-guide/fx-events/image39.png)</span></span>

<span data-ttu-id="4c2f2-689">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-689">**Description**</span></span>

<span data-ttu-id="4c2f2-690">To zdarzenie reprezentuje zdarzenie tworzenia pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-690">This event represents a file create event.</span></span>

<span data-ttu-id="4c2f2-691">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-691">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-692">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-692">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-693">Pole informacji 2: wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-693">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="4c2f2-694">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-694">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-695">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-695">Info Field 4: Not used.</span></span>

### <a name="file-date-time-set"></a><span data-ttu-id="4c2f2-696">Ustawiono datę i godzinę pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-696">File Date Time Set</span></span> 

#### <a name="fx_file_date_time_set"></a><span data-ttu-id="4c2f2-697">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="4c2f2-697">fx_file_date_time_set</span></span>

<span data-ttu-id="4c2f2-698">**Ikona** ![ Ikona Ustawienia daty i godziny pliku](./media/user-guide/fx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-698">**Icon** ![File date time set icon](./media/user-guide/fx-events/image40.png)</span></span>

<span data-ttu-id="4c2f2-699">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-699">**Description**</span></span>

<span data-ttu-id="4c2f2-700">To zdarzenie reprezentuje zdarzenie ustawienia daty/godziny pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-700">This event represents a file date/time set event.</span></span>

<span data-ttu-id="4c2f2-701">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-701">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-702">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-702">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-703">Pole informacji 2: wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-703">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="4c2f2-704">Pole informacji 3: rok.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-704">Info Field 3: Year.</span></span>
- <span data-ttu-id="4c2f2-705">Pole informacji 4: miesiąc.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-705">Info Field 4: Month.</span></span>

### <a name="file-delete"></a><span data-ttu-id="4c2f2-706">Usuwanie pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-706">File Delete</span></span> 

#### <a name="fx_file_delete"></a><span data-ttu-id="4c2f2-707">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="4c2f2-707">fx_file_delete</span></span>

<span data-ttu-id="4c2f2-708">**Ikona** ![ Ikona usuwania pliku](./media/user-guide/fx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-708">**Icon** ![File delete icon](./media/user-guide/fx-events/image41.png)</span></span>

<span data-ttu-id="4c2f2-709">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-709">**Description**</span></span>

<span data-ttu-id="4c2f2-710">To zdarzenie reprezentuje zdarzenie usunięcia pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-710">This event represents a file delete event.</span></span>

<span data-ttu-id="4c2f2-711">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-711">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-712">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-712">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-713">Pole informacji 2: wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-713">Info Field 2: Pointer to file name.</span></span>
- <span data-ttu-id="4c2f2-714">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-714">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-715">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-715">Info Field 4: Not used.</span></span>

### <a name="file-open"></a><span data-ttu-id="4c2f2-716">Otwieranie pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-716">File Open</span></span> 

#### <a name="fx_file_open"></a><span data-ttu-id="4c2f2-717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="4c2f2-717">fx_file_open</span></span>

<span data-ttu-id="4c2f2-718">**Ikona** ![ Ikona otwierania pliku](./media/user-guide/fx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-718">**Icon** ![File open icon](./media/user-guide/fx-events/image42.png)</span></span>

<span data-ttu-id="4c2f2-719">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-719">**Description**</span></span>

<span data-ttu-id="4c2f2-720">To zdarzenie reprezentuje zdarzenie otwierania pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-720">This event represents a file open event.</span></span>

<span data-ttu-id="4c2f2-721">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-721">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-722">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-722">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-723">Pole informacji 2: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-723">Info Field 2: Pointer to the file control block.</span></span>
- <span data-ttu-id="4c2f2-724">Pole informacji 3: wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-724">Info Field 3: Pointer to file name.</span></span>
- <span data-ttu-id="4c2f2-725">Pole informacji 4: typ otwarty:</span><span class="sxs-lookup"><span data-stu-id="4c2f2-725">Info Field 4: Open type:</span></span>

  |  <span data-ttu-id="4c2f2-726">Typ otwarcia</span><span class="sxs-lookup"><span data-stu-id="4c2f2-726">Open Type</span></span>                        | <span data-ttu-id="4c2f2-727">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c2f2-727">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="4c2f2-728">Otwórz do odczytu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-728">Open for Read</span></span>                    | <span data-ttu-id="4c2f2-729">0x00</span><span class="sxs-lookup"><span data-stu-id="4c2f2-729">(0x00)</span></span>  |
  |  <span data-ttu-id="4c2f2-730">Otwórz do zapisu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-730">Open for Write</span></span>                   | <span data-ttu-id="4c2f2-731">0x01</span><span class="sxs-lookup"><span data-stu-id="4c2f2-731">(0x01)</span></span>  |
  |  <span data-ttu-id="4c2f2-732">Szybkie otwieranie dla odczytu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-732">Fast Open for Read</span></span>               | <span data-ttu-id="4c2f2-733">0x02</span><span class="sxs-lookup"><span data-stu-id="4c2f2-733">(0x02)</span></span>  |

### <a name="file-read"></a><span data-ttu-id="4c2f2-734">Odczyt pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-734">File Read</span></span> 

#### <a name="fx_file_read"></a><span data-ttu-id="4c2f2-735">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="4c2f2-735">fx_file_read</span></span>

<span data-ttu-id="4c2f2-736">**Ikona** ![ Ikona odczytu pliku](./media/user-guide/fx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-736">**Icon** ![File read icon](./media/user-guide/fx-events/image43.png)</span></span>

<span data-ttu-id="4c2f2-737">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-737">**Description**</span></span>

<span data-ttu-id="4c2f2-738">To zdarzenie reprezentuje zdarzenie odczytu pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-738">This event represents a file read event.</span></span>

<span data-ttu-id="4c2f2-739">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-739">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-740">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-740">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-741">Pole informacji 2: wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-741">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="4c2f2-742">Pole informacji 3: rozmiar żądania.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-742">Info Field 3: Request size.</span></span>
- <span data-ttu-id="4c2f2-743">Pole informacji 4: rzeczywisty rozmiar odczytywany.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-743">Info Field 4: Actual size read.</span></span>

### <a name="file-relative-seek"></a><span data-ttu-id="4c2f2-744">Wyszukiwanie względem pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-744">File Relative Seek</span></span> 

#### <a name="fx_file_relative_seek"></a><span data-ttu-id="4c2f2-745">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="4c2f2-745">fx_file_relative_seek</span></span>

<span data-ttu-id="4c2f2-746">**Ikona** ![ Ikona wyszukiwania względnego pliku](./media/user-guide/fx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-746">**Icon** ![File relative seek icon](./media/user-guide/fx-events/image44.png)</span></span>

<span data-ttu-id="4c2f2-747">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-747">**Description**</span></span>

<span data-ttu-id="4c2f2-748">To zdarzenie reprezentuje względne dla pliku zdarzenie wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-748">This event represents a file relative seek event.</span></span>

<span data-ttu-id="4c2f2-749">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-749">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-750">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-750">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-751">Pole informacji 2: przesunięcie bajtu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-751">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="4c2f2-752">Pole informacji 3: wyszukiwanie:</span><span class="sxs-lookup"><span data-stu-id="4c2f2-752">Info Field 3: Seek from:</span></span>

  | <span data-ttu-id="4c2f2-753">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="4c2f2-753">Event</span></span>                             | <span data-ttu-id="4c2f2-754">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c2f2-754">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="4c2f2-755">Od początku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-755">From Beginning</span></span>                   | <span data-ttu-id="4c2f2-756">0x00</span><span class="sxs-lookup"><span data-stu-id="4c2f2-756">(0x00)</span></span>  |
  |  <span data-ttu-id="4c2f2-757">Od końca</span><span class="sxs-lookup"><span data-stu-id="4c2f2-757">From End</span></span>                         | <span data-ttu-id="4c2f2-758">0x01</span><span class="sxs-lookup"><span data-stu-id="4c2f2-758">(0x01)</span></span>  | 
  |  <span data-ttu-id="4c2f2-759">do przodu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-759">Forward</span></span>                          | <span data-ttu-id="4c2f2-760">0x02</span><span class="sxs-lookup"><span data-stu-id="4c2f2-760">(0x02)</span></span>  |
  |  <span data-ttu-id="4c2f2-761">do tyłu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-761">Backward</span></span>                         | <span data-ttu-id="4c2f2-762">(0x03)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-762">(0x03)</span></span>  |
- <span data-ttu-id="4c2f2-763">Pole informacji 4: poprzednie przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-763">Info Field 4: Previous offset.</span></span>

### <a name="file-rename"></a><span data-ttu-id="4c2f2-764">Zmiana nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-764">File Rename</span></span> 

#### <a name="fx_file_rename"></a><span data-ttu-id="4c2f2-765">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="4c2f2-765">fx_file_rename</span></span>

<span data-ttu-id="4c2f2-766">**Ikona** ![ Ikona zmiany nazwy pliku](./media/user-guide/fx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-766">**Icon** ![File rename icon](./media/user-guide/fx-events/image45.png)</span></span>

<span data-ttu-id="4c2f2-767">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-767">**Description**</span></span>

<span data-ttu-id="4c2f2-768">To zdarzenie reprezentuje zdarzenie zmiany nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-768">This event represents a file rename event.</span></span>

<span data-ttu-id="4c2f2-769">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-769">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-770">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-770">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-771">Pole informacji 2: wskaźnik do starej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-771">Info Field 2: Pointer to old file name.</span></span>
- <span data-ttu-id="4c2f2-772">Pole informacji 3: wskaźnik do nowej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-772">Info Field 3: Pointer to new file name.</span></span>
- <span data-ttu-id="4c2f2-773">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-773">Info Field 4: Not used.</span></span>

### <a name="file-seek"></a><span data-ttu-id="4c2f2-774">Wyszukiwanie plików</span><span class="sxs-lookup"><span data-stu-id="4c2f2-774">File Seek</span></span> 

#### <a name="fx_file_seek"></a><span data-ttu-id="4c2f2-775">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="4c2f2-775">fx_file_seek</span></span>

<span data-ttu-id="4c2f2-776">**Ikona** ![ Ikona wyszukiwania plików](./media/user-guide/fx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-776">**Icon** ![File seek icon](./media/user-guide/fx-events/image46.png)</span></span>

<span data-ttu-id="4c2f2-777">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-777">**Description**</span></span>

<span data-ttu-id="4c2f2-778">To zdarzenie reprezentuje zdarzenie wyszukiwania plików.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-778">This event represents a file seek event.</span></span>

<span data-ttu-id="4c2f2-779">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-779">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-780">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-780">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-781">Pole informacji 2: przesunięcie bajtu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-781">Info Field 2: Byte offset.</span></span>
- <span data-ttu-id="4c2f2-782">Pole informacji 3: poprzednie przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-782">Info Field 3: Previous offset.</span></span>
- <span data-ttu-id="4c2f2-783">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-783">Info Field 4: Not used.</span></span>

### <a name="file-truncate"></a><span data-ttu-id="4c2f2-784">Obcinanie pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-784">File Truncate</span></span> 

#### <a name="fx_file_truncate"></a><span data-ttu-id="4c2f2-785">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="4c2f2-785">fx_file_truncate</span></span>

<span data-ttu-id="4c2f2-786">**Ikona** ![ Ikona obcinania plików](./media/user-guide/fx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-786">**Icon** ![File truncate icon](./media/user-guide/fx-events/image47.png)</span></span>

<span data-ttu-id="4c2f2-787">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-787">**Description**</span></span>

<span data-ttu-id="4c2f2-788">To zdarzenie reprezentuje zdarzenie obcinania pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-788">This event represents a file truncate event.</span></span>

<span data-ttu-id="4c2f2-789">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-789">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-790">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-790">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-791">Pole informacji 2: żądany rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-791">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="4c2f2-792">Pole informacji 3: Poprzedni rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-792">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="4c2f2-793">Pole informacji 4: nowy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-793">Info Field 4: New size.</span></span>

### <a name="file-truncate-release"></a><span data-ttu-id="4c2f2-794">Wydanie obcinania plików</span><span class="sxs-lookup"><span data-stu-id="4c2f2-794">File Truncate Release</span></span> 

#### <a name="fx_file_truncate_release"></a><span data-ttu-id="4c2f2-795">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="4c2f2-795">fx_file_truncate_release</span></span> 

<span data-ttu-id="4c2f2-796">**Ikona** ![ Ikona wycięcia plików](./media/user-guide/fx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-796">**Icon** ![File truncate release icon](./media/user-guide/fx-events/image48.png)</span></span>

<span data-ttu-id="4c2f2-797">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-797">**Description**</span></span>

<span data-ttu-id="4c2f2-798">To zdarzenie reprezentuje zdarzenie zwolnienia obcinania plików.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-798">This event represents a file truncate release event.</span></span>

<span data-ttu-id="4c2f2-799">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-799">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-800">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-800">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-801">Pole informacji 2: żądany rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-801">Info Field 2: Requested size.</span></span>
- <span data-ttu-id="4c2f2-802">Pole informacji 3: Poprzedni rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-802">Info Field 3: Previous size.</span></span>
- <span data-ttu-id="4c2f2-803">Pole informacji 4: nowy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-803">Info Field 4: New size.</span></span>

### <a name="file-write"></a><span data-ttu-id="4c2f2-804">Zapis pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-804">File Write</span></span> 

#### <a name="fx_file_write"></a><span data-ttu-id="4c2f2-805">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="4c2f2-805">fx_file_write</span></span> 

<span data-ttu-id="4c2f2-806">**Ikona** ![ Ikona zapisu pliku](./media/user-guide/fx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-806">**Icon** ![File write icon](./media/user-guide/fx-events/image49.png)</span></span>

<span data-ttu-id="4c2f2-807">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-807">**Description**</span></span>

<span data-ttu-id="4c2f2-808">To zdarzenie reprezentuje zdarzenie zapisu pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-808">This event represents a file write event.</span></span>

<span data-ttu-id="4c2f2-809">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-809">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-810">Pole informacji 1: wskaźnik do pliku.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-810">Info Field 1: Pointer to the file.</span></span>
- <span data-ttu-id="4c2f2-811">Pole informacji 2: wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-811">Info Field 2: Buffer pointer.</span></span>
- <span data-ttu-id="4c2f2-812">Pole informacji 3: rozmiar żądania.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-812">Info Field 3: Request size.</span></span>
- <span data-ttu-id="4c2f2-813">Pole informacji 4: rzeczywisty rozmiar zapisany.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-813">Info Field 4: Actual size written.</span></span>

### <a name="media-abort"></a><span data-ttu-id="4c2f2-814">Przerwanie nośnika</span><span class="sxs-lookup"><span data-stu-id="4c2f2-814">Media Abort</span></span> 

#### <a name="fx_media_abort"></a><span data-ttu-id="4c2f2-815">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="4c2f2-815">fx_media_abort</span></span> 

<span data-ttu-id="4c2f2-816">**Ikona** ![ Ikona przerwania nośnika](./media/user-guide/fx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-816">**Icon** ![Media abort icon](./media/user-guide/fx-events/image50.png)</span></span>

<span data-ttu-id="4c2f2-817">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-817">**Description**</span></span>

<span data-ttu-id="4c2f2-818">To zdarzenie reprezentuje zdarzenie przerwania nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-818">This event represents a media abort event.</span></span>

<span data-ttu-id="4c2f2-819">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-819">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-820">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-820">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-821">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-821">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-822">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-822">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-823">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-823">Info Field 4: Not used.</span></span>

### <a name="media-cache-invalidate"></a><span data-ttu-id="4c2f2-824">Unieważnienie pamięci podręcznej multimediów</span><span class="sxs-lookup"><span data-stu-id="4c2f2-824">Media Cache Invalidate</span></span>

#### <a name="fx_media_cache_invalidate"></a><span data-ttu-id="4c2f2-825">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="4c2f2-825">fx_media_cache_invalidate</span></span>

<span data-ttu-id="4c2f2-826">**Ikona** ![ Ikona unieważniania pamięci podręcznej multimediów](./media/user-guide/fx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-826">**Icon** ![Media cache invalidate icon](./media/user-guide/fx-events/image51.png)</span></span>

<span data-ttu-id="4c2f2-827">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-827">**Description**</span></span>

<span data-ttu-id="4c2f2-828">To zdarzenie reprezentuje zdarzenie unieważnienia pamięci podręcznej multimediów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-828">This event represents a media cache invalidate event.</span></span>

<span data-ttu-id="4c2f2-829">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-829">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-830">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-830">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-831">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-831">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-832">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-832">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-833">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-833">Info Field 4: Not used.</span></span>

### <a name="media-check"></a><span data-ttu-id="4c2f2-834">Sprawdzenie nośnika</span><span class="sxs-lookup"><span data-stu-id="4c2f2-834">Media Check</span></span> 

#### <a name="fx_media_check"></a><span data-ttu-id="4c2f2-835">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="4c2f2-835">fx_media_check</span></span>

<span data-ttu-id="4c2f2-836">**Ikona** ![ Ikona Sprawdź multimedia](./media/user-guide/fx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-836">**Icon** ![Media check icon](./media/user-guide/fx-events/image52.png)</span></span>

<span data-ttu-id="4c2f2-837">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-837">**Description**</span></span>

<span data-ttu-id="4c2f2-838">To zdarzenie reprezentuje zdarzenie sprawdzania nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-838">This event represents a media check event.</span></span>

<span data-ttu-id="4c2f2-839">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-839">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-840">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-840">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-841">Pole informacji 2: wskaźnik pamięci tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-841">Info Field 2: Scratch memory pointer.</span></span>
- <span data-ttu-id="4c2f2-842">Pole informacji 3: rozmiar pamięci tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-842">Info Field 3: Scratch memory size.</span></span>
- <span data-ttu-id="4c2f2-843">Pole informacyjne 4: Błędy mapy bitowej:</span><span class="sxs-lookup"><span data-stu-id="4c2f2-843">Info Field 4: Errors bit map:</span></span>

  | <span data-ttu-id="4c2f2-844">Typ błędu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-844">Error type</span></span>                        | <span data-ttu-id="4c2f2-845">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c2f2-845">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="4c2f2-846">Błąd łańcucha FAT</span><span class="sxs-lookup"><span data-stu-id="4c2f2-846">FAT Chain Error</span></span>                  | <span data-ttu-id="4c2f2-847">0x01</span><span class="sxs-lookup"><span data-stu-id="4c2f2-847">(0x01)</span></span>  |
  |  <span data-ttu-id="4c2f2-848">Błąd katalogu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-848">Directory Error</span></span>                  | <span data-ttu-id="4c2f2-849">0x02</span><span class="sxs-lookup"><span data-stu-id="4c2f2-849">(0x02)</span></span>  |
  |  <span data-ttu-id="4c2f2-850">Utracony błąd klastra</span><span class="sxs-lookup"><span data-stu-id="4c2f2-850">Lost Cluster Error</span></span>               | <span data-ttu-id="4c2f2-851">(0x04)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-851">(0x04)</span></span>  |
  |  <span data-ttu-id="4c2f2-852">Błąd rozmiaru pliku</span><span class="sxs-lookup"><span data-stu-id="4c2f2-852">File Size Error</span></span>                  | <span data-ttu-id="4c2f2-853">(0x08)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-853">(0x08)</span></span>  |

### <a name="media-close"></a><span data-ttu-id="4c2f2-854">Zamknij nośnik</span><span class="sxs-lookup"><span data-stu-id="4c2f2-854">Media Close</span></span> 

#### <a name="fx_media_close"></a><span data-ttu-id="4c2f2-855">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="4c2f2-855">fx_media_close</span></span>

<span data-ttu-id="4c2f2-856">**Ikona** ![ Ikona zamykania nośnika](./media/user-guide/fx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-856">**Icon** ![Media Close icon](./media/user-guide/fx-events/image53.png)</span></span>

<span data-ttu-id="4c2f2-857">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-857">**Description**</span></span>

<span data-ttu-id="4c2f2-858">To zdarzenie reprezentuje zdarzenie zamknięcia nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-858">This event represents a media close event.</span></span>

<span data-ttu-id="4c2f2-859">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-859">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-860">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-860">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-861">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-861">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-862">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-862">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-863">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-863">Info Field 4: Not used.</span></span>

### <a name="media-flush"></a><span data-ttu-id="4c2f2-864">Opróżnianie multimediów</span><span class="sxs-lookup"><span data-stu-id="4c2f2-864">Media Flush</span></span> 

#### <a name="fx_media_flush"></a><span data-ttu-id="4c2f2-865">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="4c2f2-865">fx_media_flush</span></span>

<span data-ttu-id="4c2f2-866">**Ikona** ![ Ikona opróżniania nośnika](./media/user-guide/fx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-866">**Icon** ![Media flush icon](./media/user-guide/fx-events/image54.png)</span></span>

<span data-ttu-id="4c2f2-867">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-867">**Description**</span></span>

<span data-ttu-id="4c2f2-868">To zdarzenie reprezentuje zdarzenie opróżniania nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-868">This event represents a media flush event.</span></span>

<span data-ttu-id="4c2f2-869">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-869">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-870">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-870">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-871">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-871">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-872">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-872">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-873">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-873">Info Field 4: Not used.</span></span>

### <a name="media-format"></a><span data-ttu-id="4c2f2-874">Format multimediów</span><span class="sxs-lookup"><span data-stu-id="4c2f2-874">Media Format</span></span> 

#### <a name="fx_media_format"></a><span data-ttu-id="4c2f2-875">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="4c2f2-875">fx_media_format</span></span>

<span data-ttu-id="4c2f2-876">**Ikona** ![ Ikona formatu multimediów](./media/user-guide/fx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-876">**Icon** ![Media format icon](./media/user-guide/fx-events/image55.png)</span></span>

<span data-ttu-id="4c2f2-877">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-877">**Description**</span></span>

<span data-ttu-id="4c2f2-878">To zdarzenie reprezentuje zdarzenie w formacie nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-878">This event represents a media format event.</span></span>

<span data-ttu-id="4c2f2-879">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-879">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-880">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-880">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-881">Pole informacji 2: liczba wpisów głównych.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-881">Info Field 2: Number of root entries.</span></span>
- <span data-ttu-id="4c2f2-882">Pole informacji 3: sektory.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-882">Info Field 3: Sectors.</span></span>
- <span data-ttu-id="4c2f2-883">Pole informacji 4: sektory na klaster.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-883">Info Field 4: Sectors per cluster.</span></span>

### <a name="media-open"></a><span data-ttu-id="4c2f2-884">Otwarte multimedia</span><span class="sxs-lookup"><span data-stu-id="4c2f2-884">Media Open</span></span> 

#### <a name="fx_media_open"></a><span data-ttu-id="4c2f2-885">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="4c2f2-885">fx_media_open</span></span>

<span data-ttu-id="4c2f2-886">**Ikona** ![ Ikona otwarcia nośnika](./media/user-guide/fx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-886">**Icon** ![Media open icon](./media/user-guide/fx-events/image56.png)</span></span>

<span data-ttu-id="4c2f2-887">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-887">**Description**</span></span>

<span data-ttu-id="4c2f2-888">To zdarzenie reprezentuje zdarzenie otwarcia nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-888">This event represents a media open event.</span></span>

<span data-ttu-id="4c2f2-889">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-889">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-890">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-890">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-891">Pole informacji 2: wskaźnik do wpisu sterownika nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-891">Info Field 2: Pointer to media driver entry.</span></span>
- <span data-ttu-id="4c2f2-892">Pole informacji 3: wskaźnik pamięci.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-892">Info Field 3: Memory pointer.</span></span>
- <span data-ttu-id="4c2f2-893">Pole informacji 4: rozmiar pamięci.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-893">Info Field 4: Memory size.</span></span>

### <a name="media-read-media-read"></a><span data-ttu-id="4c2f2-894">Odczyt nośnika odczytu multimediów</span><span class="sxs-lookup"><span data-stu-id="4c2f2-894">Media Read Media Read</span></span> 

#### <a name="fx_media_read"></a><span data-ttu-id="4c2f2-895">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="4c2f2-895">fx_media_read</span></span>

<span data-ttu-id="4c2f2-896">**Ikona** ![ Ikona odczytu multimediów](./media/user-guide/fx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-896">**Icon** ![Media read icon](./media/user-guide/fx-events/image57.png)</span></span>

<span data-ttu-id="4c2f2-897">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-897">**Description**</span></span>

<span data-ttu-id="4c2f2-898">To zdarzenie reprezentuje zdarzenie odczytu nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-898">This event represents a media read event.</span></span>

<span data-ttu-id="4c2f2-899">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-899">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-900">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-900">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-901">Pole informacji 2: sektor logiczny.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-901">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="4c2f2-902">Pole informacji 3: wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-902">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="4c2f2-903">Pole informacji 4: Bajty odczytane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-903">Info Field 4: Bytes read.</span></span>

### <a name="media-space-available"></a><span data-ttu-id="4c2f2-904">Dostępne miejsce na multimediach</span><span class="sxs-lookup"><span data-stu-id="4c2f2-904">Media Space Available</span></span> 

#### <a name="fx_media_space_available"></a><span data-ttu-id="4c2f2-905">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="4c2f2-905">fx_media_space_available</span></span>

<span data-ttu-id="4c2f2-906">**Ikona** ![ Ikona dostępnego miejsca na multimediach](./media/user-guide/fx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-906">**Icon** ![Media space available icon](./media/user-guide/fx-events/image58.png)</span></span>

<span data-ttu-id="4c2f2-907">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-907">**Description**</span></span>

<span data-ttu-id="4c2f2-908">To zdarzenie reprezentuje zdarzenie dostępne w obszarze nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-908">This event represents a media space available event.</span></span>

<span data-ttu-id="4c2f2-909">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-909">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-910">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-910">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-911">Pole informacji 2: wskaźnik dostępnych bajtów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-911">Info Field 2: Available bytes pointer.</span></span>
- <span data-ttu-id="4c2f2-912">Pole informacji 3: liczba wolnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-912">Info Field 3: Number of free clusters.</span></span>
- <span data-ttu-id="4c2f2-913">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-913">Info Field 4: Not used.</span></span>

### <a name="media-volume-get"></a><span data-ttu-id="4c2f2-914">Pobieranie woluminu multimedialnego</span><span class="sxs-lookup"><span data-stu-id="4c2f2-914">Media Volume Get</span></span> 

#### <a name="fx_media_volume_get"></a><span data-ttu-id="4c2f2-915">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-915">fx_media_volume_get</span></span>

<span data-ttu-id="4c2f2-916">**Ikona** ![ Ikona pobierania woluminu multimedialnego](./media/user-guide/fx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-916">**Icon** ![Media volume get icon](./media/user-guide/fx-events/image59.png)</span></span>

<span data-ttu-id="4c2f2-917">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-917">**Description**</span></span>

<span data-ttu-id="4c2f2-918">To zdarzenie reprezentuje zdarzenie pobrania woluminu multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-918">This event represents a media volume get event.</span></span>

<span data-ttu-id="4c2f2-919">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-919">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-920">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-920">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-921">Pole informacji 2: wskaźnik do nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-921">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="4c2f2-922">Pole informacji 3: Źródło woluminu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-922">Info Field 3: Volume source.</span></span>
- <span data-ttu-id="4c2f2-923">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-923">Info Field 4: Not used.</span></span>

### <a name="media-volume-set"></a><span data-ttu-id="4c2f2-924">Zestaw woluminów multimedialnych</span><span class="sxs-lookup"><span data-stu-id="4c2f2-924">Media Volume Set</span></span> 

#### <a name="fx_media_volume_set"></a><span data-ttu-id="4c2f2-925">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="4c2f2-925">fx_media_volume_set</span></span>

<span data-ttu-id="4c2f2-926">**Ikona** ![ Ikona zestawu woluminów multimedialnych](./media/user-guide/fx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-926">**Icon** ![Media volume set icon](./media/user-guide/fx-events/image60.png)</span></span>

<span data-ttu-id="4c2f2-927">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-927">**Description**</span></span>

<span data-ttu-id="4c2f2-928">To zdarzenie reprezentuje zdarzenie zestawu woluminu multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-928">This event represents a media volume set event.</span></span>

<span data-ttu-id="4c2f2-929">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-929">**Information Fields**</span></span> 
- <span data-ttu-id="4c2f2-930">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-930">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-931">Pole informacji 2: wskaźnik do nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-931">Info Field 2: Pointer to volume name.</span></span>
- <span data-ttu-id="4c2f2-932">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-932">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-933">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-933">Info Field 4: Not used.</span></span>

### <a name="media-write"></a><span data-ttu-id="4c2f2-934">Zapis nośnika</span><span class="sxs-lookup"><span data-stu-id="4c2f2-934">Media Write</span></span> 

#### <a name="fx_media_write"></a><span data-ttu-id="4c2f2-935">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="4c2f2-935">fx_media_write</span></span>

<span data-ttu-id="4c2f2-936">**Ikona** ![ Ikona zapisu multimediów](./media/user-guide/fx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-936">**Icon** ![Media write icon](./media/user-guide/fx-events/image61.png)</span></span>

<span data-ttu-id="4c2f2-937">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-937">**Description**</span></span>

<span data-ttu-id="4c2f2-938">To zdarzenie reprezentuje zdarzenie zapisu nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-938">This event represents a media write event.</span></span>

<span data-ttu-id="4c2f2-939">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-939">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-940">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-940">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-941">Pole informacji 2: sektor logiczny.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-941">Info Field 2: Logical sector.</span></span>
- <span data-ttu-id="4c2f2-942">Pole informacji 3: wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-942">Info Field 3: Buffer pointer.</span></span>
- <span data-ttu-id="4c2f2-943">Pole informacji 4: bajty zapisywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-943">Info Field 4: Bytes written.</span></span>

### <a name="system-date-get"></a><span data-ttu-id="4c2f2-944">Data systemu Get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-944">System Date Get</span></span> 

#### <a name="fx_system_date_get"></a><span data-ttu-id="4c2f2-945">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-945">fx_system_date_get</span></span> 

<span data-ttu-id="4c2f2-946">**Ikona** ![ Ikona pobierania daty systemu](./media/user-guide/fx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-946">**Icon** ![System date get icon](./media/user-guide/fx-events/image62.png)</span></span>

<span data-ttu-id="4c2f2-947">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-947">**Description**</span></span>

<span data-ttu-id="4c2f2-948">To zdarzenie reprezentuje zdarzenie pobrania daty systemowej.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-948">This event represents a system date get event.</span></span>

<span data-ttu-id="4c2f2-949">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-949">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-950">Pole informacji 1: rok.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-950">Info Field 1: Year.</span></span>
- <span data-ttu-id="4c2f2-951">Pole informacji 2: miesiąc.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-951">Info Field 2: Month.</span></span>
- <span data-ttu-id="4c2f2-952">Pole informacji 3: dzień.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-952">Info Field 3: Day.</span></span>
- <span data-ttu-id="4c2f2-953">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-953">Info Field 4: Not used.</span></span>

### <a name="system-date-set"></a><span data-ttu-id="4c2f2-954">Systemowy zestaw dat</span><span class="sxs-lookup"><span data-stu-id="4c2f2-954">System Date Set</span></span> 

#### <a name="fx_system_date_set"></a><span data-ttu-id="4c2f2-955">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="4c2f2-955">fx_system_date_set</span></span> 

<span data-ttu-id="4c2f2-956">**Ikona** ![ Ikona zestawu dat systemu](./media/user-guide/fx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-956">**Icon** ![System date set icon](./media/user-guide/fx-events/image63.png)</span></span>

<span data-ttu-id="4c2f2-957">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-957">**Description**</span></span>

<span data-ttu-id="4c2f2-958">To zdarzenie reprezentuje zdarzenie systemowego ustawiania daty.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-958">This event represents a system date set event.</span></span>

<span data-ttu-id="4c2f2-959">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-959">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-960">Pole informacji 1: rok.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-960">Info Field 1: Year.</span></span>
- <span data-ttu-id="4c2f2-961">Pole informacji 2: miesiąc.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-961">Info Field 2: Month.</span></span>
- <span data-ttu-id="4c2f2-962">Pole informacji 3: dzień.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-962">Info Field 3: Day.</span></span>
- <span data-ttu-id="4c2f2-963">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-963">Info Field 4: Not used.</span></span>

### <a name="system-initialize"></a><span data-ttu-id="4c2f2-964">Inicjowanie systemu</span><span class="sxs-lookup"><span data-stu-id="4c2f2-964">System Initialize</span></span> 

#### <a name="fx_system_initialize"></a><span data-ttu-id="4c2f2-965">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="4c2f2-965">fx_system_initialize</span></span> 

<span data-ttu-id="4c2f2-966">**Ikona** ![ Ikona inicjowania systemu](./media/user-guide/fx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-966">**Icon** ![System initialize icon](./media/user-guide/fx-events/image64.png)</span></span>

<span data-ttu-id="4c2f2-967">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-967">**Description**</span></span>

<span data-ttu-id="4c2f2-968">To zdarzenie reprezentuje zdarzenie inicjowania systemu.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-968">This event represents a system initialize event.</span></span>

<span data-ttu-id="4c2f2-969">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-969">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-970">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-970">Info Field 1: Not used.</span></span>
- <span data-ttu-id="4c2f2-971">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-971">Info Field 2: Not used.</span></span>
- <span data-ttu-id="4c2f2-972">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-972">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-973">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-973">Info Field 4: Not used.</span></span>

### <a name="system-time-get"></a><span data-ttu-id="4c2f2-974">Pobieranie czasu systemowego</span><span class="sxs-lookup"><span data-stu-id="4c2f2-974">System Time Get</span></span> 

#### <a name="fx_system_time_get"></a><span data-ttu-id="4c2f2-975">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-975">fx_system_time_get</span></span> 

<span data-ttu-id="4c2f2-976">**Ikona** ![ Ikona uzyskiwania czasu systemowego](./media/user-guide/fx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-976">**Icon** ![System time get icon](./media/user-guide/fx-events/image65.png)</span></span>

<span data-ttu-id="4c2f2-977">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-977">**Description**</span></span>

<span data-ttu-id="4c2f2-978">To zdarzenie reprezentuje zdarzenie Get Time system.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-978">This event represents a system time get event.</span></span>

<span data-ttu-id="4c2f2-979">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-979">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-980">Pole informacji 1: godzina.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-980">Info Field 1: Hour.</span></span>
- <span data-ttu-id="4c2f2-981">Pole informacji 2: minuta.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-981">Info Field 2: Minute.</span></span>
- <span data-ttu-id="4c2f2-982">Pole informacyjne 3: Second.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-982">Info Field 3: Second.</span></span>
- <span data-ttu-id="4c2f2-983">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-983">Info Field 4: Not used.</span></span>

### <a name="system-time-set"></a><span data-ttu-id="4c2f2-984">Ustawiony czas systemowy</span><span class="sxs-lookup"><span data-stu-id="4c2f2-984">System Time Set</span></span> 

#### <a name="fx_system_time_set"></a><span data-ttu-id="4c2f2-985">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="4c2f2-985">fx_system_time_set</span></span> 

<span data-ttu-id="4c2f2-986">**Ikona** ![ Ikona Ustawienia czasu systemowego](./media/user-guide/fx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-986">**Icon** ![System time set icon](./media/user-guide/fx-events/image66.png)</span></span>

<span data-ttu-id="4c2f2-987">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-987">**Description**</span></span>

<span data-ttu-id="4c2f2-988">To zdarzenie reprezentuje zdarzenie ustawienia czasu systemowego.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-988">This event represents a system time set event.</span></span>

<span data-ttu-id="4c2f2-989">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-989">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-990">Pole informacji 1: godzina.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-990">Info Field 1: Hour.</span></span>
- <span data-ttu-id="4c2f2-991">Pole informacji 2: minuta.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-991">Info Field 2: Minute.</span></span>
- <span data-ttu-id="4c2f2-992">Pole informacyjne 3: Second.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-992">Info Field 3: Second.</span></span>
- <span data-ttu-id="4c2f2-993">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-993">Info Field 4: Not used.</span></span>

### <a name="unicode-directory-create"></a><span data-ttu-id="4c2f2-994">Tworzenie katalogu Unicode</span><span class="sxs-lookup"><span data-stu-id="4c2f2-994">Unicode Directory Create</span></span> 

#### <a name="fx_unicode_directory_create"></a><span data-ttu-id="4c2f2-995">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="4c2f2-995">fx_unicode_directory_create</span></span> 

<span data-ttu-id="4c2f2-996">**Ikona** ![ Ikona tworzenia katalogu Unicode](./media/user-guide/fx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-996">**Icon** ![Unicode directory create icon](./media/user-guide/fx-events/image67.png)</span></span>

<span data-ttu-id="4c2f2-997">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-997">**Description**</span></span>

<span data-ttu-id="4c2f2-998">To zdarzenie reprezentuje zdarzenie tworzenia katalogu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-998">This event represents a Unicode directory create event.</span></span>

<span data-ttu-id="4c2f2-999">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-999">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-1000">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1000">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-1001">Pole informacji 2: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1001">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1002">Pole informacji 3: rozmiar nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1002">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1003">Pole informacji 4: wskaźnik do krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1003">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-directory-rename"></a><span data-ttu-id="4c2f2-1004">Zmiana nazwy katalogu Unicode</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1004">Unicode Directory Rename</span></span> 

#### <a name="fx_unicode_directory_rename"></a><span data-ttu-id="4c2f2-1005">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1005">fx_unicode_directory_rename</span></span>

<span data-ttu-id="4c2f2-1006">**Ikona** ![ Ikona zmiany nazwy katalogu Unicode](./media/user-guide/fx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1006">**Icon** ![Unicode directory rename icon](./media/user-guide/fx-events/image68.png)</span></span>

<span data-ttu-id="4c2f2-1007">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1007">**Description**</span></span>

<span data-ttu-id="4c2f2-1008">To zdarzenie reprezentuje zdarzenie zmiany nazwy katalogu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1008">This event represents a Unicode directory rename event.</span></span>

<span data-ttu-id="4c2f2-1009">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1009">**Information Fields**</span></span> 

- <span data-ttu-id="4c2f2-1010">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1010">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-1011">Pole informacji 2: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1011">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1012">Pole informacji 3: rozmiar nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1012">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1013">Pole informacji 4: wskaźnik do krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1013">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-create"></a><span data-ttu-id="4c2f2-1014">Tworzenie pliku Unicode</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1014">Unicode File Create</span></span> 

#### <a name="fx_unicode_file_create"></a><span data-ttu-id="4c2f2-1015">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1015">fx_unicode_file_create</span></span>

<span data-ttu-id="4c2f2-1016">**Ikona** ![ Ikona tworzenia pliku Unicode](./media/user-guide/fx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1016">**Icon** ![Unicode file create icon](./media/user-guide/fx-events/image69.png)</span></span>

<span data-ttu-id="4c2f2-1017">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1017">**Description**</span></span>

<span data-ttu-id="4c2f2-1018">To zdarzenie reprezentuje zdarzenie tworzenia pliku w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1018">This event represents a Unicode file create event.</span></span>

<span data-ttu-id="4c2f2-1019">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1019">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-1020">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1020">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-1021">Pole informacji 2: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1021">Info Field 2: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1022">Pole informacji 3: rozmiar nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1022">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1023">Pole informacji 4: wskaźnik do krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1023">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-file-rename"></a><span data-ttu-id="4c2f2-1024">Zmiana nazwy pliku Unicode</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1024">Unicode File Rename</span></span> 

#### <a name="fx_unicode_file_rename"></a><span data-ttu-id="4c2f2-1025">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1025">fx_unicode_file_rename</span></span>

<span data-ttu-id="4c2f2-1026">**Ikona** ![ Ikona zmiany nazwy pliku Unicode](./media/user-guide/fx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1026">**Icon** ![Unicode file rename icon](./media/user-guide/fx-events/image70.png)</span></span>

<span data-ttu-id="4c2f2-1027">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1027">**Description**</span></span>

<span data-ttu-id="4c2f2-1028">To zdarzenie reprezentuje zdarzenie zmiany nazwy pliku w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1028">This event represents a Unicode file rename event.</span></span>

<span data-ttu-id="4c2f2-1029">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1029">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-1030">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1030">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-1031">Pole informacji 2: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1031">Info Field 2: Pointer to Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1032">Pole informacji 3: rozmiar nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1032">Info Field 3: Size of Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1033">Pole informacji 4: wskaźnik do krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1033">Info Field 4: Pointer to short name.</span></span>

### <a name="unicode-length-get"></a><span data-ttu-id="4c2f2-1034">Pobieranie długości Unicode</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1034">Unicode Length Get</span></span> 

#### <a name="fx_unicode_length_get"></a><span data-ttu-id="4c2f2-1035">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1035">fx_unicode_length_get</span></span>

<span data-ttu-id="4c2f2-1036">**Ikona** ![ Ikona pobierania długości Unicode](./media/user-guide/fx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1036">**Icon** ![Unicode length get icon](./media/user-guide/fx-events/image71.png)</span></span>

<span data-ttu-id="4c2f2-1037">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1037">**Description**</span></span>

<span data-ttu-id="4c2f2-1038">To zdarzenie reprezentuje zdarzenie pobrania długości Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1038">This event represents a Unicode length get event.</span></span>

<span data-ttu-id="4c2f2-1039">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1039">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-1040">Pole informacji 1: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1040">Info Field 1: Pointer to the Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1041">Pole informacji 2: długość.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1041">Info Field 2: Length.</span></span>
- <span data-ttu-id="4c2f2-1042">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1042">Info Field 3: Not used.</span></span>
- <span data-ttu-id="4c2f2-1043">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1043">Info Field 4: Not used.</span></span>

### <a name="unicode-name-get"></a><span data-ttu-id="4c2f2-1044">Pobieranie nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1044">Unicode Name Get</span></span> 

#### <a name="fx_unicode_name_get"></a><span data-ttu-id="4c2f2-1045">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1045">fx_unicode_name_get</span></span>

<span data-ttu-id="4c2f2-1046">**Ikona** ![ Ikona pobierania nazwy Unicode](./media/user-guide/fx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1046">**Icon** ![Unicode name get icon](./media/user-guide/fx-events/image72.png)</span></span>

<span data-ttu-id="4c2f2-1047">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1047">**Description**</span></span>

<span data-ttu-id="4c2f2-1048">To zdarzenie reprezentuje zdarzenie pobrania nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1048">This event represents a Unicode name get event.</span></span>

<span data-ttu-id="4c2f2-1049">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1049">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-1050">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1050">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-1051">Pole informacji 2: krótka nazwa źródła.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1051">Info Field 2: Source short name.</span></span>
- <span data-ttu-id="4c2f2-1052">Pole informacji 3: docelowy wskaźnik nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1052">Info Field 3: Destination Unicode name pointer.</span></span>
- <span data-ttu-id="4c2f2-1053">Pole informacji 4: docelowa długość nazwy w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1053">Info Field 4: Destination Unicode name length.</span></span>

### <a name="unicode-short-name-get"></a><span data-ttu-id="4c2f2-1054">Pobieranie krótkiej nazwy w formacie Unicode</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1054">Unicode Short Name Get</span></span> 

#### <a name="fx_unicode_short_name_get"></a><span data-ttu-id="4c2f2-1055">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1055">fx_unicode_short_name_get</span></span>

<span data-ttu-id="4c2f2-1056">**Ikona** ![ Ikona pobierania krótkiej nazwy Unicode](./media/user-guide/fx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1056">**Icon** ![Unicode short name get icon](./media/user-guide/fx-events/image73.png)</span></span>

<span data-ttu-id="4c2f2-1057">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1057">**Description**</span></span>

<span data-ttu-id="4c2f2-1058">To zdarzenie reprezentuje zdarzenie pobrania krótkiej nazwy w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1058">This event represents a Unicode short name get event.</span></span>

<span data-ttu-id="4c2f2-1059">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1059">**Information Fields**</span></span>

- <span data-ttu-id="4c2f2-1060">Pole informacji 1: wskaźnik do nośnika.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1060">Info Field 1: Pointer to the media.</span></span>
- <span data-ttu-id="4c2f2-1061">Pole informacji 2: wskaźnik do źródłowej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1061">Info Field 2: Pointer to source Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1062">Pole informacji 3: długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1062">Info Field 3: Length of Unicode name.</span></span>
- <span data-ttu-id="4c2f2-1063">Pole informacji 4: wskaźnik do krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4c2f2-1063">Info Field 4: Pointer to short name.</span></span>