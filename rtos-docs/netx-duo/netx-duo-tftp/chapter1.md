---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo TFTP
description: Trivial File Transfer Protocol (TFTP) jest lekkim protokołem przeznaczonym do transferów plików.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4431b23e143d05214090547e7f179a6f5def8217
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821613"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="5b529-103">Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo TFTP</span><span class="sxs-lookup"><span data-stu-id="5b529-103">Chapter 1 - Introduction to Azure RTOS NetX Duo TFTP</span></span> 

<span data-ttu-id="5b529-104">Trivial File Transfer Protocol (TFTP) jest lekkim protokołem przeznaczonym do transferów plików.</span><span class="sxs-lookup"><span data-stu-id="5b529-104">The Trivial File Transfer Protocol (TFTP) is a lightweight protocol designed for file transfers.</span></span> <span data-ttu-id="5b529-105">W przeciwieństwie do bardziej niezawodnych protokołów, TFTP nie wykonuje dokładnego sprawdzania błędów i może również mieć ograniczoną wydajność, ponieważ jest to protokół zatrzymania i oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="5b529-105">Unlike more robust protocols, TFTP does not perform extensive error checking and can also have limited performance because it is a stop-and-wait protocol.</span></span> <span data-ttu-id="5b529-106">Po wysłaniu pakietu danych TFTP nadawca czeka na zwrócenie potwierdzenia przez adresata.</span><span class="sxs-lookup"><span data-stu-id="5b529-106">After a TFTP data packet is sent, the sender waits for an ACK to be returned by the recipient.</span></span> <span data-ttu-id="5b529-107">Chociaż jest to proste, ograniczenie ogólnej przepływności protokołu TFTP jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="5b529-107">Although this is simple, it does limit the overall TFTP throughput.</span></span> <span data-ttu-id="5b529-108">Pakiet TFTP umożliwia hostom używanie protokołu TFTP w sieciach IP.</span><span class="sxs-lookup"><span data-stu-id="5b529-108">The TFTP package enables hosts to use the TFTP protocol over IP networks.</span></span>

## <a name="tftp-requirements"></a><span data-ttu-id="5b529-109">Wymagania dotyczące protokołu TFTP</span><span class="sxs-lookup"><span data-stu-id="5b529-109">TFTP Requirements</span></span>

<span data-ttu-id="5b529-110">Aby zapewnić prawidłowe działanie, część klientów TFTP pakietu TFTP NetX Duo wymaga, aby wystąpienie protokołu IP zostało już utworzone.</span><span class="sxs-lookup"><span data-stu-id="5b529-110">In order to function properly, the TFTP Clients portion of the NetX Duo TFTP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="5b529-111">Ponadto należy włączyć protokół UDP dla tego samego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="5b529-111">In addition, UDP must be enabled on that same IP instance.</span></span> <span data-ttu-id="5b529-112">Część kliencka pakietu TFTP NetX Duo nie ma żadnych dalszych wymagań.</span><span class="sxs-lookup"><span data-stu-id="5b529-112">The Client portion of the NetX Duo TFTP package has no further requirements.</span></span>

<span data-ttu-id="5b529-113">Część serwera TFTP pakietu TFTP NetX Duo ma kilka dodatkowych wymagań.</span><span class="sxs-lookup"><span data-stu-id="5b529-113">The TFTP Server portion of the NetX Duo TFTP package has several additional requirements.</span></span> <span data-ttu-id="5b529-114">Najpierw wymaga pełnego dostępu do *dobrze znanego portu* protokołu UDP 69 do obsługi wszystkich żądań TFTP klienta.</span><span class="sxs-lookup"><span data-stu-id="5b529-114">First, it requires complete access to the UDP *well known port 69* for handling all client TFTP requests.</span></span> <span data-ttu-id="5b529-115">Serwer TFTP jest również przeznaczony do użycia z osadzonym systemem plików FileX.</span><span class="sxs-lookup"><span data-stu-id="5b529-115">The TFTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="5b529-116">Jeśli FileX nie jest dostępna, użytkownik może przenieść fragmenty FileX używane w ich własnym środowisku.</span><span class="sxs-lookup"><span data-stu-id="5b529-116">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="5b529-117">Zostało to omówione w kolejnych sekcjach tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="5b529-117">This is discussed in later sections of this guide.</span></span>

## <a name="tftp-file-names"></a><span data-ttu-id="5b529-118">Nazwy plików TFTP</span><span class="sxs-lookup"><span data-stu-id="5b529-118">TFTP File Names</span></span> 

<span data-ttu-id="5b529-119">Nazwy plików TFTP powinny mieć format docelowego systemu plików.</span><span class="sxs-lookup"><span data-stu-id="5b529-119">TFTP file names should be in the format of the target file system.</span></span> <span data-ttu-id="5b529-120">Powinny to być ciągi ASCII zakończonych znakiem NULL, z pełnymi informacjami o ścieżce, jeśli jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="5b529-120">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="5b529-121">Nie ma określonego limitu rozmiaru nazw plików TFTP w implementacji TFTP NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="5b529-121">There is no specified limit in the size of TFTP file names in the NetX Duo TFTP implementation.</span></span>

## <a name="tftp-messages"></a><span data-ttu-id="5b529-122">Komunikaty TFTP</span><span class="sxs-lookup"><span data-stu-id="5b529-122">TFTP Messages</span></span>

<span data-ttu-id="5b529-123">Protokół TFTP ma bardzo prosty mechanizm otwierania, odczytywania, zapisywania i zamykania plików.</span><span class="sxs-lookup"><span data-stu-id="5b529-123">The TFTP has a very simple mechanism for opening, reading, writing, and closing files.</span></span> <span data-ttu-id="5b529-124">W nagłówku UDP znajduje się zasadniczo 2-4 bajtów nagłówka TFTP.</span><span class="sxs-lookup"><span data-stu-id="5b529-124">There are basically 2-4 bytes of TFTP header underneath the UDP header.</span></span> <span data-ttu-id="5b529-125">Definicja otwartych komunikatów protokołu TFTP ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="5b529-125">The definition of the TFTP file open messages has the following format:</span></span>

<span data-ttu-id="5b529-126">**oooof... f0OCTET0**</span><span class="sxs-lookup"><span data-stu-id="5b529-126">**oooof…f0OCTET0**</span></span>

<span data-ttu-id="5b529-127">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="5b529-127">Where:</span></span>

- <span data-ttu-id="5b529-128">**Oooo** 2-bajtowe pole opcode</span><span class="sxs-lookup"><span data-stu-id="5b529-128">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="5b529-129">0x0001 > Otwórz do odczytu</span><span class="sxs-lookup"><span data-stu-id="5b529-129">0x0001 -> Open for read</span></span>  
<span data-ttu-id="5b529-130">0x0002 > Otwórz do zapisu</span><span class="sxs-lookup"><span data-stu-id="5b529-130">0x0002 -> Open for write</span></span>

- <span data-ttu-id="5b529-131">**f... n-** bajtowe pole filename</span><span class="sxs-lookup"><span data-stu-id="5b529-131">**f…f** n-byte Filename field</span></span>

- <span data-ttu-id="5b529-132">0 1-bajtowy znak zakończenia o wartości NULL</span><span class="sxs-lookup"><span data-stu-id="5b529-132">0  1-byte NULL termination character</span></span>

- <span data-ttu-id="5b529-133">**Oktet** ASCII "OCTET", aby określić transfer binarny</span><span class="sxs-lookup"><span data-stu-id="5b529-133">**OCTET** ASCII “OCTET” to specify binary transfer</span></span>

- <span data-ttu-id="5b529-134">0 1-bajtowy znak zakończenia o wartości NULL</span><span class="sxs-lookup"><span data-stu-id="5b529-134">0  1-byte NULL termination character</span></span>

<span data-ttu-id="5b529-135">Definicje komunikatów Write, ACK i Error protokołu TFTP są nieco inne i są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5b529-135">The definition of the TFTP write, ACK, and error messages are slightly different and are defined as follows:</span></span>

<span data-ttu-id="5b529-136">**oooobbbbd... Wykres**</span><span class="sxs-lookup"><span data-stu-id="5b529-136">**oooobbbbd…d**</span></span>

<span data-ttu-id="5b529-137">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="5b529-137">Where:</span></span>

- <span data-ttu-id="5b529-138">**Oooo** 2-bajtowe pole opcode</span><span class="sxs-lookup"><span data-stu-id="5b529-138">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="5b529-139">0x0003 — pakiet danych ></span><span class="sxs-lookup"><span data-stu-id="5b529-139">0x0003 -> Data packet</span></span>  
<span data-ttu-id="5b529-140">0x0004-> ACK dla ostatniego odczytu</span><span class="sxs-lookup"><span data-stu-id="5b529-140">0x0004 -> ACK for last read</span></span>  
<span data-ttu-id="5b529-141">0x0005 — warunek błędu ></span><span class="sxs-lookup"><span data-stu-id="5b529-141">0x0005 -> Error condition</span></span>  

- <span data-ttu-id="5b529-142">pole **bbbb** 2-bajtowego numeru bloku (1-n)</span><span class="sxs-lookup"><span data-stu-id="5b529-142">**bbbb** 2-byte Block Number field (1-n)</span></span>

- <span data-ttu-id="5b529-143">**d... d** n-bajtowe pole danych</span><span class="sxs-lookup"><span data-stu-id="5b529-143">**d…d** n-byte Data field</span></span>


- <span data-ttu-id="5b529-144">0x0001 (odczyt) nazwa pliku 0, OKTET 0</span><span class="sxs-lookup"><span data-stu-id="5b529-144">0x0001 (read) File Name 0 OCTET 0</span></span>

- <span data-ttu-id="5b529-145">0x0002 (Write) — nazwa pliku 0 OKTET 0</span><span class="sxs-lookup"><span data-stu-id="5b529-145">0x0002 (write) File Name 0 OCTET 0</span></span>

## <a name="tftp-communication"></a><span data-ttu-id="5b529-146">Komunikacja TFTP</span><span class="sxs-lookup"><span data-stu-id="5b529-146">TFTP Communication</span></span>

<span data-ttu-id="5b529-147">Serwery TFTP używają dobrze znanego portu UDP 69 do nasłuchiwania żądań klientów.</span><span class="sxs-lookup"><span data-stu-id="5b529-147">TFTP Servers utilize the well-known UDP port 69 to listen for Client requests.</span></span> <span data-ttu-id="5b529-148">Gniazda klienta TFTP mogą być powiązane z dowolnym dostępnym portem UDP.</span><span class="sxs-lookup"><span data-stu-id="5b529-148">TFTP Client sockets may bind to any available UDP port.</span></span> <span data-ttu-id="5b529-149">Ładunek pakietu danych zawierający plik do przekazania lub pobrania jest wysyłany w 512ych fragmentach bajtów do momentu ostatniego pakietu zawierającego < 512 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5b529-149">Data packet payload containing the file to upload or download is sent in 512 byte chunks, until the last packet containing < 512 bytes.</span></span> <span data-ttu-id="5b529-150">W związku z tym pakiet zawierający mniej niż 512 bajtów sygnalizuje koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="5b529-150">Therefore a packet containing fewer than 512 bytes signals the end of file.</span></span> <span data-ttu-id="5b529-151">Ogólna sekwencja zdarzeń jest następująca:</span><span class="sxs-lookup"><span data-stu-id="5b529-151">The general sequence of events is as follows:</span></span>

<span data-ttu-id="5b529-152">Żądania odczytu pliku TFTP:</span><span class="sxs-lookup"><span data-stu-id="5b529-152">TFTP Read File Requests:</span></span>

1.  <span data-ttu-id="5b529-153">Klient wystawia żądanie "Otwórz do odczytu" z nazwą pliku i czeka na odpowiedź z serwera.</span><span class="sxs-lookup"><span data-stu-id="5b529-153">The Client issues an “Open For Read” request with the file name and waits for a reply from the Server.</span></span>

2.  <span data-ttu-id="5b529-154">Serwer wysyła pierwsze 512 bajtów pliku lub mniej, jeśli rozmiar pliku jest mniejszy niż 512 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5b529-154">The Server sends the first 512 bytes of the file or less if the file size is less than 512 bytes.</span></span>

3.  <span data-ttu-id="5b529-155">Klient odbiera dane, wysyła potwierdzenie i czeka na następny pakiet z serwera dla plików zawierających więcej niż 512 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5b529-155">The Client receives data, sends an ACK, and waits for the next packet from the Server for files containing more than 512 bytes.</span></span>

4.  <span data-ttu-id="5b529-156">Sekwencja zostaje zakończona, gdy klient otrzymuje pakiet zawierający mniej niż 512 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5b529-156">The sequence ends when the Client receives a packet containing fewer than 512 bytes.</span></span>

<span data-ttu-id="5b529-157">Żądania zapisu TFTP:</span><span class="sxs-lookup"><span data-stu-id="5b529-157">TFTP Write Requests:</span></span>

1.  <span data-ttu-id="5b529-158">Klient wystawia żądanie "Otwórz do zapisu" z nazwą pliku i oczekuje na potwierdzenie z numerem bloku 0 z serwera.</span><span class="sxs-lookup"><span data-stu-id="5b529-158">The Client issues an “Open for Write” request with the file name and waits for an ACK with a block number of 0 from the Server.</span></span>

2.  <span data-ttu-id="5b529-159">Gdy serwer jest gotowy do zapisania pliku, wysyła potwierdzenie z numerem bloku równym zero.</span><span class="sxs-lookup"><span data-stu-id="5b529-159">When the Server is ready to write the file, it sends an ACK with a block number of zero.</span></span>

3.  <span data-ttu-id="5b529-160">Klient wysyła pierwsze 512 bajtów pliku (lub mniej dla plików mniejszych niż 512 bajtów) do serwera i czeka na potwierdzenie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="5b529-160">The Client sends the first 512 bytes of the file (or less for files less than 512 bytes) to the Server and waits for an ACK back.</span></span>

4.  <span data-ttu-id="5b529-161">Serwer wysyła potwierdzenie po zapisaniu bajtów.</span><span class="sxs-lookup"><span data-stu-id="5b529-161">The Server sends an ACK after the bytes are written.</span></span>

5.  <span data-ttu-id="5b529-162">Sekwencja kończy się, gdy klient ukończy pisanie pakietu zawierającego mniej niż 512 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5b529-162">The sequence ends when the Client completes writing a packet containing fewer than 512 bytes.</span></span>
 

## <a name="tftp-server-session-timer"></a><span data-ttu-id="5b529-163">Czasomierz sesji serwera TFTP</span><span class="sxs-lookup"><span data-stu-id="5b529-163">TFTP Server Session Timer</span></span>

<span data-ttu-id="5b529-164">Serwer TFTP ma ograniczoną liczbę miejsc żądania klienta.</span><span class="sxs-lookup"><span data-stu-id="5b529-164">The TFTP Server has a limited number of client request slots.</span></span> <span data-ttu-id="5b529-165">Jeśli sesja klienta zostanie porzucona, gniazdo nie może być dostępne do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="5b529-165">If a client session appears to be dropped, that slot cannot be available for re-use.</span></span> <span data-ttu-id="5b529-166">Jeśli jednak opcja NX_TFTP_SERVER_RETRANSMIT_ENABLE jest włączona, serwer TFTP NetX Duo utworzy czasomierz sesji monitorujący limit czasu dla każdej sesji klienta.</span><span class="sxs-lookup"><span data-stu-id="5b529-166">However if the NX_TFTP_SERVER_RETRANSMIT_ENABLE option is enabled, the NetX Duo TFTP Server creates an session timer that monitors the timeout on each of its client sessions.</span></span> <span data-ttu-id="5b529-167">Po upływie limitu czasu sesji zostaje zakończony i wszystkie otwarte pliki są zamknięte.</span><span class="sxs-lookup"><span data-stu-id="5b529-167">When a session timeout expires it is terminated and any open files are closed.</span></span> <span data-ttu-id="5b529-168">W ten sposób "miejsce" staną się dostępne dla innego żądania klienta TFTP.</span><span class="sxs-lookup"><span data-stu-id="5b529-168">Thus the ‘slot’ becomes available for another TFTP Client request.</span></span>

<span data-ttu-id="5b529-169">Aby ustawić limit czasu, Dostosuj opcję konfiguracji NX_TFTP_SERVER_RETRANSMIT_TIMEOUT która domyślnie ma 200 Takty czasomierza.</span><span class="sxs-lookup"><span data-stu-id="5b529-169">To set the timeout, adjust the configuration option NX_TFTP_SERVER_RETRANSMIT_TIMEOUT which by default is 200 timer ticks.</span></span> <span data-ttu-id="5b529-170">Interwał, między jakim są sprawdzane limity czasu sesji, jest ustawiany przez NX_TFTP_SERVER_TIMEOUT_PERIOD, co domyślnie wynosi 20 taktów czasomierza.</span><span class="sxs-lookup"><span data-stu-id="5b529-170">The interval between which session timeouts are checked is set by the NX_TFTP_SERVER_TIMEOUT_PERIOD which is 20 timer ticks by default.</span></span>

<span data-ttu-id="5b529-171">Gdy klient TFTP przekazał (wypisano) pliki na nośniku TFTP FileX, nośnik musi zostać opróżniony, aby dane mogły być zapisywane z dysku RAM serwera TFTP do nośnika bazowego (pamięć dysku klienta TFTP).</span><span class="sxs-lookup"><span data-stu-id="5b529-171">When the TFTP Client has uploaded (written) files to the TFTP FileX media, the media needs to be flushed so that data can be written from the TFTP server ram disk to the underlying media (TFTP Client disk memory).</span></span> <span data-ttu-id="5b529-172">Można to zrobić za pomocą usługi fx_media_flush, jeśli aplikacja nie chce zamykać serwera TFTP.</span><span class="sxs-lookup"><span data-stu-id="5b529-172">This can be done using the fx_media_flush service if the application does not wish to close the TFTP Server.</span></span>

<span data-ttu-id="5b529-173">Jednak po zamknięciu serwera TFTP aplikacja powinna, jeśli nie będzie więcej korzystać z nośnika FileX, a następnie zamknąć nośnik przy użyciu usługi fx_media_close.</span><span class="sxs-lookup"><span data-stu-id="5b529-173">However, after closing the TFTP server, the application should, if it has no further use for the FileX media, then close the media using the fx_media_close service.</span></span> <span data-ttu-id="5b529-174">Spowoduje to opróżnienie danych pliku z powrotem do dysku klienta TFTP, zamknięcie otwartych plików i zaktualizowanie informacji o katalogu na nośniku.</span><span class="sxs-lookup"><span data-stu-id="5b529-174">This will flush the file data back to the TFTP Client disk, close open files, and update the directory information to the media.</span></span>

<span data-ttu-id="5b529-175">W sekcji "mały przykład" w tym rozdziale pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="5b529-175">The “Small Example” section in this chapter demonstrates this.</span></span>

<span data-ttu-id="5b529-176">Trzecią opcją aktualizacji nośnika FileX jest skompilowanie biblioteki FileX z FX_FAULT_TOLERANT lub opcjami FX_FAULT_TOLERANT_DATA zamiast jawnie korzystać z usług FileX Services.</span><span class="sxs-lookup"><span data-stu-id="5b529-176">A third option for updating the FileX media is to compile the FileX library with the FX_FAULT_TOLERANT or the FX_FAULT_TOLERANT_DATA options instead of using FileX services explicitly.</span></span> <span data-ttu-id="5b529-177">Jeśli jest zdefiniowany, FileX automatycznie przekazuje żądania zapisu do sterownika multimediów.</span><span class="sxs-lookup"><span data-stu-id="5b529-177">If defined, FileX automatically passes write requests to the media driver.</span></span> <span data-ttu-id="5b529-178">Te opcje mogą ograniczać wydajność, ale zapewniają lepszą ochronę przed utraconymi danymi plików lub utraconymi klastrami.</span><span class="sxs-lookup"><span data-stu-id="5b529-178">These options may limit performance but offer greater protection from lost file data or lost clusters.</span></span> <span data-ttu-id="5b529-179">Więcej informacji na ten temat i FileX ogólnie można znaleźć w podręczniku użytkownika Express Logic FileX.</span><span class="sxs-lookup"><span data-stu-id="5b529-179">For more information about this and FileX in general, please see the Express Logic FileX User Guide.</span></span>

## <a name="tftp-multi-thread-support"></a><span data-ttu-id="5b529-180">Obsługa wielowątkowości TFTP</span><span class="sxs-lookup"><span data-stu-id="5b529-180">TFTP Multi-Thread Support</span></span>

<span data-ttu-id="5b529-181">Usługi klienta TFTP NetX Duo można wywołać z wielu wątków jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="5b529-181">The NetX Duo TFTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="5b529-182">Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta TFTP powinny być wykonywane w kolejności z tego samego wątku.</span><span class="sxs-lookup"><span data-stu-id="5b529-182">However, read or write requests for a particular TFTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="tftp-rfcs"></a><span data-ttu-id="5b529-183">Specyfikacje RFC protokołu TFTP</span><span class="sxs-lookup"><span data-stu-id="5b529-183">TFTP RFCs</span></span>

<span data-ttu-id="5b529-184">NetX Duo TFTP jest zgodny z RFC1350 i pokrewnymi specyfikacjami RFC.</span><span class="sxs-lookup"><span data-stu-id="5b529-184">NetX Duo TFTP is compliant with RFC1350 and related RFCs.</span></span>

