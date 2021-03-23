---
title: Rozdział 1 — wprowadzenie do NetX HTTP
description: W tym dokumencie wyjaśniono, jak protokół HTTP jest protokołem przeznaczonym do przesyłania zawartości w sieci Web.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822621"
---
# <a name="chapter-1---introduction-to-netx-http"></a><span data-ttu-id="1cff4-103">Rozdział 1 — wprowadzenie do NetX HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-103">Chapter 1 - Introduction to NetX HTTP</span></span>

<span data-ttu-id="1cff4-104">Protokół HTTP (Hypertext Transfer Protocol) to protokół przeznaczony do przesyłania zawartości w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1cff4-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="1cff4-105">HTTP to prosty protokół, który wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu zawartości.</span><span class="sxs-lookup"><span data-stu-id="1cff4-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="1cff4-106">W związku z tym protokół HTTP jest wysoce niezawodnym protokołem transferu zawartości.</span><span class="sxs-lookup"><span data-stu-id="1cff4-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="1cff4-107">Protokół HTTP jest jednym z najczęściej używanych protokołów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1cff4-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="1cff4-108">Wszystkie operacje w sieci Web korzystają z protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-108">All operations on the Web utilize the HTTP protocol.</span></span>

## <a name="http-requirements"></a><span data-ttu-id="1cff4-109">Wymagania dotyczące protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-109">HTTP Requirements</span></span>

<span data-ttu-id="1cff4-110">Aby zapewnić prawidłowe działanie, pakiet HTTP NetX wymaga zainstalowania NetX (wersja 5,2 lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="1cff4-110">In order to function properly, the NetX HTTP package requires that a NetX (version 5.2 or later) is installed.</span></span> <span data-ttu-id="1cff4-111">Ponadto należy już utworzyć wystąpienie adresu IP, a dla tego samego wystąpienia IP musi być włączony protokół TCP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-111">In addition, an IP instance must already be created and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="1cff4-112">Plik demonstracyjny w sekcji "mały przykładowy system" w **rozdziale 2** pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="1cff4-112">The demo file in section “Small Example System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="1cff4-113">Część klienta HTTP NetX pakietu HTTP nie ma żadnych dalszych wymagań.</span><span class="sxs-lookup"><span data-stu-id="1cff4-113">The HTTP Client portion of the NetX HTTP package has no further requirements.</span></span>

<span data-ttu-id="1cff4-114">Część serwera HTTP NetX pakietu HTTP ma kilka dodatkowych wymagań.</span><span class="sxs-lookup"><span data-stu-id="1cff4-114">The HTTP Server portion of the NetX HTTP package has several additional requirements.</span></span> <span data-ttu-id="1cff4-115">Najpierw wymaga pełnego dostępu do *dobrze znanego portu TCP 80* do obsługi wszystkich żądań HTTP klienta.</span><span class="sxs-lookup"><span data-stu-id="1cff4-115">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests.</span></span> <span data-ttu-id="1cff4-116">Serwer HTTP jest również przeznaczony do użycia z osadzonym systemem plików FileX.</span><span class="sxs-lookup"><span data-stu-id="1cff4-116">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="1cff4-117">Jeśli FileX nie jest dostępna, użytkownik może przenieść fragmenty FileX używane w ich własnym środowisku.</span><span class="sxs-lookup"><span data-stu-id="1cff4-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="1cff4-118">Zostało to omówione w kolejnych sekcjach tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="1cff4-118">This is discussed in later sections of this guide.</span></span>

## <a name="http-constraints"></a><span data-ttu-id="1cff4-119">Ograniczenia HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-119">HTTP Constraints</span></span> 

<span data-ttu-id="1cff4-120">Protokół HTTP NetX implementuje Standard HTTP 1,0.</span><span class="sxs-lookup"><span data-stu-id="1cff4-120">The NetX HTTP protocol implements the HTTP 1.0 standard.</span></span> <span data-ttu-id="1cff4-121">Istnieją jednak następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="1cff4-121">However, there are following constraints:</span></span>

1.  <span data-ttu-id="1cff4-122">Połączenia trwałe nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="1cff4-122">Persistent connections are not supported</span></span>

2.  <span data-ttu-id="1cff4-123">Przetwarzanie potokowe żądań nie jest obsługiwane</span><span class="sxs-lookup"><span data-stu-id="1cff4-123">Request pipelining is not supported</span></span>

3.  <span data-ttu-id="1cff4-124">Serwer HTTP obsługuje zarówno uwierzytelnianie podstawowe, jak i MD5 szyfrowanego, ale nie MD5-sess.</span><span class="sxs-lookup"><span data-stu-id="1cff4-124">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="1cff4-125">W tej chwili klient HTTP obsługuje tylko uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="1cff4-125">At present, the HTTP Client supports only basic authentication.</span></span>

4.  <span data-ttu-id="1cff4-126">Kompresja zawartości nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="1cff4-126">No content compression is supported.</span></span>

5.  <span data-ttu-id="1cff4-127">ŚLEDZENIE, opcje i żądania połączenia nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="1cff4-127">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>

6.  <span data-ttu-id="1cff4-128">Pula pakietów skojarzona z serwerem HTTP lub klientem musi być wystarczająco duża, aby można było przechowywać kompletny nagłówek HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-128">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>

7.  <span data-ttu-id="1cff4-129">Usługi klienta HTTP są przeznaczone tylko do transferu zawartości — w tym pakiecie nie ma dostępnych narzędzi do wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="1cff4-129">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="1cff4-130">Adres URL HTTP (nazwy zasobów)</span><span class="sxs-lookup"><span data-stu-id="1cff4-130">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="1cff4-131">Protokół HTTP jest przeznaczony do przesyłania zawartości w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1cff4-131">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="1cff4-132">Żądana zawartość jest określana przez adres URL (Universal Resource Locator).</span><span class="sxs-lookup"><span data-stu-id="1cff4-132">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="1cff4-133">Jest to podstawowy składnik każdego żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-133">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="1cff4-134">Adresy URL zawsze zaczynają się od znaku "/" i zwykle odpowiadają plikom na serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-134">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="1cff4-135">Poniżej przedstawiono typowe rozszerzenia plików HTTP:</span><span class="sxs-lookup"><span data-stu-id="1cff4-135">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="1cff4-136">**. htm (lub. html)** HTML (HTML)</span><span class="sxs-lookup"><span data-stu-id="1cff4-136">**.htm (or .html)** Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="1cff4-137">**. txt** Zwykły tekst ASCII</span><span class="sxs-lookup"><span data-stu-id="1cff4-137">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="1cff4-138">**. gif** Binarny obraz GIF</span><span class="sxs-lookup"><span data-stu-id="1cff4-138">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="1cff4-139">**. XBM** Binarny obraz Xbitmap</span><span class="sxs-lookup"><span data-stu-id="1cff4-139">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="1cff4-140">Żądania klientów HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-140">HTTP Client Requests</span></span>

<span data-ttu-id="1cff4-141">Protokół HTTP ma prosty mechanizm do żądania zawartości sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1cff4-141">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="1cff4-142">Istnieje zasadniczo zestaw standardowych poleceń HTTP, które są wydawane przez klienta po pomyślnym nawiązaniu połączenia z *dobrze znanym portem TCP 80*.</span><span class="sxs-lookup"><span data-stu-id="1cff4-142">There is basically a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80*.</span></span> <span data-ttu-id="1cff4-143">Poniżej przedstawiono niektóre z podstawowych poleceń HTTP:</span><span class="sxs-lookup"><span data-stu-id="1cff4-143">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="1cff4-144">Pobieranie zasobu HTTP/1.0 *pobieranie określonego zasobu*</span><span class="sxs-lookup"><span data-stu-id="1cff4-144">GET resource HTTP/1.0 *Get the specified resource*</span></span>
- <span data-ttu-id="1cff4-145">Zaksięguj zasób HTTP/1.0 *Pobierz określony zasób i przekaż dołączone dane wejściowe do serwera http*</span><span class="sxs-lookup"><span data-stu-id="1cff4-145">POST resource HTTP/1.0 *Get the specified resource and pass attached input to the HTTP Server*</span></span>
- <span data-ttu-id="1cff4-146">Zasób główny HTTP/1.0 *traktowany jak GET, ale nie zawartość jest zwracany przez serwer http*</span><span class="sxs-lookup"><span data-stu-id="1cff4-146">HEAD resource HTTP/1.0 *Treated like a GET but not content is returned by the HTTP Server*</span></span>
- <span data-ttu-id="1cff4-147">Umieść zasób miejsca HTTP/1.0 *na serwerze HTTP*</span><span class="sxs-lookup"><span data-stu-id="1cff4-147">PUT resource HTTP/1.0 *Place resource on HTTP Server*</span></span>
- <span data-ttu-id="1cff4-148">Usuń zasób HTTP/1.0 *usuwanie zasobu na serwerze*</span><span class="sxs-lookup"><span data-stu-id="1cff4-148">DELETE resource HTTP/1.0 *Delete resource on the Server*</span></span>

<span data-ttu-id="1cff4-149">Te polecenia ASCII są generowane wewnętrznie przez przeglądarki sieci Web i usługi klienta HTTP NetX do wykonywania operacji HTTP przy użyciu serwera HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-149">These ASCII commands are generated internally by Web browsers and the NetX HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

>[!NOTE] 
> <span data-ttu-id="1cff4-150">Aplikacja kliencka HTTP domyślnie jest portem Connect 80.</span><span class="sxs-lookup"><span data-stu-id="1cff4-150">The HTTP Client application default to the connect port of 80.</span></span> <span data-ttu-id="1cff4-151">Można jednak zmienić port połączenia na serwer HTTP w środowisku uruchomieniowym przy użyciu usługi *nx_http_client_set_connect_port* .</span><span class="sxs-lookup"><span data-stu-id="1cff4-151">However, it can change the connect port to the HTTP Server at runtime using the *nx_http_client_set_connect_port* service.</span></span> <span data-ttu-id="1cff4-152">Aby uzyskać szczegółowe informacje o tej usłudze, zobacz rozdział 4.</span><span class="sxs-lookup"><span data-stu-id="1cff4-152">See Chapter 4 for more details of this service.</span></span> <span data-ttu-id="1cff4-153">Ma to na celu uwzględnienie serwerów sieci Web, które czasami używają alternatywnych portów do połączeń klienckich.</span><span class="sxs-lookup"><span data-stu-id="1cff4-153">This is to accommodate web servers that occasionally use alternate ports for Client connections.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="1cff4-154">Odpowiedzi serwera HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-154">HTTP Server Responses</span></span>

<span data-ttu-id="1cff4-155">Serwer HTTP używa tego samego *dobrze znanego portu TCP 80* do wysyłania odpowiedzi na polecenie klienta.</span><span class="sxs-lookup"><span data-stu-id="1cff4-155">The HTTP Server utilizes the same *well-known TCP port 80* to send Client command responses.</span></span> <span data-ttu-id="1cff4-156">Gdy serwer HTTP przetwarza polecenie klienta, zwraca ciąg odpowiedzi ASCII, który zawiera 3-cyfrowy kod stanu numerycznego.</span><span class="sxs-lookup"><span data-stu-id="1cff4-156">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="1cff4-157">Odpowiedź numeryczna jest używana przez oprogramowanie klienckie HTTP do określenia, czy operacja zakończyła się powodzeniem, czy niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1cff4-157">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="1cff4-158">Poniżej znajduje się lista różnych odpowiedzi serwera HTTP do poleceń klienta:</span><span class="sxs-lookup"><span data-stu-id="1cff4-158">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="1cff4-159">200 *żądanie powiodło* się</span><span class="sxs-lookup"><span data-stu-id="1cff4-159">200 *Request was successful*</span></span>
- <span data-ttu-id="1cff4-160">400 *żądanie nie zostało poprawnie sformułowane*</span><span class="sxs-lookup"><span data-stu-id="1cff4-160">400 *Request was not formed properly*</span></span>
- <span data-ttu-id="1cff4-161">401 *żądanie nieautoryzowane, klient musi wysłać uwierzytelnianie*</span><span class="sxs-lookup"><span data-stu-id="1cff4-161">401 *Unauthorized request, client needs to send authentication*</span></span>
- <span data-ttu-id="1cff4-162">404 *nie znaleziono określonego zasobu w żądaniu*</span><span class="sxs-lookup"><span data-stu-id="1cff4-162">404 *Specified resource in request was not found*</span></span>
- <span data-ttu-id="1cff4-163">500 *wewnętrzny błąd serwera http*</span><span class="sxs-lookup"><span data-stu-id="1cff4-163">500 *Internal HTTP Server error*</span></span>
- <span data-ttu-id="1cff4-164">501 *żądanie niezaimplementowane przez serwer http*</span><span class="sxs-lookup"><span data-stu-id="1cff4-164">501 *Request not implemented by HTTP Server*</span></span>
- <span data-ttu-id="1cff4-165">*usługa 502 jest niedostępna*</span><span class="sxs-lookup"><span data-stu-id="1cff4-165">502 *Service is not available*</span></span>

<span data-ttu-id="1cff4-166">Na przykład pomyślne żądanie klienta dotyczące umieszczenia pliku "test.htm" jest odpowiedzią na komunikat "HTTP/1.0 200 OK".</span><span class="sxs-lookup"><span data-stu-id="1cff4-166">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.0 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="1cff4-167">Komunikacja HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-167">HTTP Communication</span></span>

<span data-ttu-id="1cff4-168">Jak wspomniano wcześniej, serwer HTTP korzysta z *dobrze znanego portu TCP 80* do pól żądań klientów.</span><span class="sxs-lookup"><span data-stu-id="1cff4-168">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80* to field Client requests.</span></span> <span data-ttu-id="1cff4-169">Klienci HTTP mogą korzystać z dowolnego dostępnego portu TCP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-169">HTTP Clients may use any available TCP port.</span></span> <span data-ttu-id="1cff4-170">Ogólna sekwencja zdarzeń HTTP jest następująca:</span><span class="sxs-lookup"><span data-stu-id="1cff4-170">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="1cff4-171">**Żądanie HTTP GET**:</span><span class="sxs-lookup"><span data-stu-id="1cff4-171">**HTTP GET Request**:</span></span>

1.  <span data-ttu-id="1cff4-172">Problemy z klientem połączenia TCP z portem serwera 80.</span><span class="sxs-lookup"><span data-stu-id="1cff4-172">Client issues TCP connect to Server port 80.</span></span>

2.  <span data-ttu-id="1cff4-173">Klient wysyła żądanie "**Pobierz zasób http/1.0**" (wraz z innymi informacjami nagłówka).</span><span class="sxs-lookup"><span data-stu-id="1cff4-173">Client sends “**GET resource HTTP/1.0**” request (along with other header information).</span></span>

3.  <span data-ttu-id="1cff4-174">Serwer kompiluje komunikat "**http/1.0 200 OK**" z dodatkowymi informacjami, a następnie bezpośrednio przez zawartość zasobu (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="1cff4-174">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>

4.  <span data-ttu-id="1cff4-175">Serwer wykonuje odłączenie.</span><span class="sxs-lookup"><span data-stu-id="1cff4-175">Server performs a disconnection.</span></span>

5.  <span data-ttu-id="1cff4-176">Klient wykonuje odłączenie.</span><span class="sxs-lookup"><span data-stu-id="1cff4-176">Client performs a disconnection.</span></span>

<span data-ttu-id="1cff4-177">**Żądanie HTTP Put**:</span><span class="sxs-lookup"><span data-stu-id="1cff4-177">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="1cff4-178">Problemy z klientem połączenia TCP z portem serwera 80.</span><span class="sxs-lookup"><span data-stu-id="1cff4-178">Client issues TCP connect to Server port 80.</span></span>

2. <span data-ttu-id="1cff4-179">Klient wysyła żądanie "**Umieść zasób http/1.0**" wraz z innymi informacjami nagłówka, a następnie zawartość zasobu.</span><span class="sxs-lookup"><span data-stu-id="1cff4-179">Client sends “**PUT resource HTTP/1.0**” request, along with other header information, and followed by the resource content.</span></span>

3. <span data-ttu-id="1cff4-180">Serwer kompiluje komunikat "**http/1.0 200 OK**" z dodatkowymi informacjami, a następnie bezpośrednio przez zawartość zasobów.</span><span class="sxs-lookup"><span data-stu-id="1cff4-180">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content.</span></span>

4. <span data-ttu-id="1cff4-181">Serwer wykonuje odłączenie.</span><span class="sxs-lookup"><span data-stu-id="1cff4-181">Server performs a disconnection.</span></span>

5. <span data-ttu-id="1cff4-182">Klient wykonuje odłączenie.</span><span class="sxs-lookup"><span data-stu-id="1cff4-182">Client performs a disconnection.</span></span>

>[!NOTE] 
> <span data-ttu-id="1cff4-183">Jak wspomniano wcześniej, klient HTTP może zmienić domyślny port Connect z 80 na inny port przy użyciu *nx_http_client_set_connect_port* dla serwerów sieci Web, które używają alternatywnych portów do łączenia się z klientami.</span><span class="sxs-lookup"><span data-stu-id="1cff4-183">As mentioned previously, the HTTP Client can change the default connect port from 80 to another port using the *nx_http_client_set_connect_port* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="1cff4-184">Uwierzytelnianie HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-184">HTTP Authentication</span></span>

<span data-ttu-id="1cff4-185">Uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich żądań sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1cff4-185">HTTP authentication is optional and isn’t required for all Web requests.</span></span> <span data-ttu-id="1cff4-186">Istnieją dwa typy uwierzytelniania, czyli *podstawowe* i *szyfrowane*.</span><span class="sxs-lookup"><span data-stu-id="1cff4-186">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="1cff4-187">Uwierzytelnianie podstawowe jest równoważne z *nazwą* i *hasłem* uwierzytelnianiem w wielu protokołach.</span><span class="sxs-lookup"><span data-stu-id="1cff4-187">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="1cff4-188">W podstawowym uwierzytelnianiu HTTP Nazwa i hasła są łączone i kodowane w formacie base64.</span><span class="sxs-lookup"><span data-stu-id="1cff4-188">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="1cff4-189">Główną wadą uwierzytelniania podstawowego jest nazwa i hasło, które są przesyłane w ramach żądania w sposób otwarty.</span><span class="sxs-lookup"><span data-stu-id="1cff4-189">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="1cff4-190">Sprawia to, że jest nieco łatwe do kradzieży nazwy i hasła.</span><span class="sxs-lookup"><span data-stu-id="1cff4-190">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="1cff4-191">Uwierzytelnianie szyfrowane rozwiązuje ten problem, przez co nigdy nie przesyłamy nazwy i hasła w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="1cff4-191">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="1cff4-192">Zamiast tego algorytm służy do wyprowadzania klucza 128-bitowego lub skrótu z nazwy, hasła i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="1cff4-192">Instead, an algorithm is used to derive a 128-bit key or digest from the name, password, and other information.</span></span> <span data-ttu-id="1cff4-193">Serwer HTTP NetX obsługuje standardowy algorytm MD5.</span><span class="sxs-lookup"><span data-stu-id="1cff4-193">The NetX HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="1cff4-194">Kiedy jest wymagane uwierzytelnianie?</span><span class="sxs-lookup"><span data-stu-id="1cff4-194">When is authentication required?</span></span> <span data-ttu-id="1cff4-195">W zasadzie serwer HTTP decyduje, czy żądany zasób wymaga uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="1cff4-195">Basically, the HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="1cff4-196">Jeśli uwierzytelnianie jest wymagane, a żądanie klienta nie zawierało odpowiedniego uwierzytelniania, odpowiedź "HTTP/1.0 401 bez autoryzacji" z typem wymaganego uwierzytelniania jest wysyłana do klienta.</span><span class="sxs-lookup"><span data-stu-id="1cff4-196">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.0 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="1cff4-197">Klient powinien następnie utworzyć nowe żądanie z właściwym uwierzytelnianiem.</span><span class="sxs-lookup"><span data-stu-id="1cff4-197">The Client is then expected to form a new request with the proper authentication.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="1cff4-198">Wywołanie zwrotne uwierzytelniania HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-198">HTTP Authentication Callback</span></span>

<span data-ttu-id="1cff4-199">Jak wspomniano wcześniej, uwierzytelnianie HTTP jest opcjonalne i nie jest wymagane dla wszystkich transferów w sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1cff4-199">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="1cff4-200">Ponadto uwierzytelnianie jest zwykle zależne od zasobów.</span><span class="sxs-lookup"><span data-stu-id="1cff4-200">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="1cff4-201">Dostęp do niektórych zasobów na serwerze wymaga uwierzytelnienia, a inne nie.</span><span class="sxs-lookup"><span data-stu-id="1cff4-201">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="1cff4-202">Pakiet serwera HTTP NetX umożliwia aplikacji określenie (za pośrednictwem wywołania ***nx_http_server_create*** ) procedury wywołania zwrotnego uwierzytelniania, która jest wywoływana na początku obsługi każdego żądania klienta http.</span><span class="sxs-lookup"><span data-stu-id="1cff4-202">The NetX HTTP Server package allows the application to specify (via the ***nx_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="1cff4-203">Procedura wywołania zwrotnego udostępnia serwer HTTP NetX z nazwami użytkowników, hasła i obszarów skojarzonych z zasobem i zwracają wymagany typ uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1cff4-203">The callback routine provides the NetX HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="1cff4-204">Jeśli dla zasobu nie jest wymagane żadne uwierzytelnianie, wywołanie zwrotne uwierzytelniania powinno zwrócić wartość **NX_HTTP_DONT_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="1cff4-204">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="1cff4-205">W przeciwnym razie, jeśli dla określonego zasobu jest wymagane uwierzytelnianie podstawowe, procedura powinna zwrócić **NX_HTTP_BASIC_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="1cff4-205">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="1cff4-206">A wreszcie, jeśli wymagane jest uwierzytelnianie MD5 Digest, procedura wywołania zwrotnego powinna zwracać **NX_HTTP_DIGEST_AUTHENTICATE**.</span><span class="sxs-lookup"><span data-stu-id="1cff4-206">And finally, if MD5 digest authentication is required, the callback routine should return **NX_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="1cff4-207">Jeśli nie jest wymagane żadne uwierzytelnianie dla żadnego zasobu dostarczonego przez serwer HTTP, wywołanie zwrotne nie jest wymagane, a do utworzenia wywołania serwera HTTP można dostarczyć wskaźnik o wartości NULL.</span><span class="sxs-lookup"><span data-stu-id="1cff4-207">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="1cff4-208">Format procedury wywołania zwrotnego uwierzytelniania aplikacji jest bardzo prosty i został zdefiniowany poniżej:</span><span class="sxs-lookup"><span data-stu-id="1cff4-208">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

<span data-ttu-id="1cff4-209">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1cff4-209">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="1cff4-210">*request_type* Określa żądanie klienta HTTP, prawidłowe żądania są zdefiniowane jako:</span><span class="sxs-lookup"><span data-stu-id="1cff4-210">*request_type* Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="1cff4-211">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-211">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="1cff4-212">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-212">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="1cff4-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="1cff4-214">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-214">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="1cff4-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="1cff4-216">*zasób* Zażądano określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="1cff4-216">*resource* Specific resource requested.</span></span>
- <span data-ttu-id="1cff4-217">*Nazwa* Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1cff4-217">*name* Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="1cff4-218">*hasło* Miejsce docelowe wskaźnika do wymaganego hasła.</span><span class="sxs-lookup"><span data-stu-id="1cff4-218">*password* Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="1cff4-219">*obszar* Miejsce docelowe wskaźnika w obszarze dla tego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1cff4-219">*realm* Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="1cff4-220">Wartość zwracana przez procedurę uwierzytelniania określa, czy jest wymagane uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="1cff4-220">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="1cff4-221">nazwy, hasła i wskaźniki obszaru nie są używane, jeśli **NX_HTTP_DONT_AUTHENTICATE** jest zwracany przez procedurę wywołania zwrotnego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1cff4-221">name, password, and realm pointers are not used if **NX_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="1cff4-222">W przeciwnym razie deweloper serwera HTTP musi upewnić się, że **NX_HTTP_MAX_USERNAME** i **NX_HTTP_MAX_PASSWORD** zdefiniowane w *nx_http_server. h* są wystarczająco duże dla nazwy użytkownika i hasła określonych w wywołaniu wywołania zwrotnego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="1cff4-222">Otherwise the HTTP server developer must ensure that **NX_HTTP_MAX_USERNAME** and **NX_HTTP_MAX_PASSWORD** defined in *nx_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="1cff4-223">Są one domyślnie przyłączone do rozmiaru 20 znaków.</span><span class="sxs-lookup"><span data-stu-id="1cff4-223">These are both defaulted to size 20 chars.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="1cff4-224">Nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-224">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="1cff4-225">Opcjonalne nieprawidłowe wywołanie zwrotne nazwy użytkownika/hasła w NetX serwerze HTTP jest wywoływane, jeśli serwer HTTP odbiera nieprawidłową kombinację nazwy użytkownika i hasła w żądaniu klienta.</span><span class="sxs-lookup"><span data-stu-id="1cff4-225">The optional invalid username/password callback in NetX HTTP Server is invoked if HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="1cff4-226">Jeśli aplikacja serwera HTTP rejestruje wywołanie zwrotne z serwerem HTTP, zostanie wywołane w przypadku niepowodzenia uwierzytelniania podstawowego lub szyfrowanego *w nx_http_server_get_process*, w *nx_http_server_put_process* lub *w nx_http_server_delete_process.*</span><span class="sxs-lookup"><span data-stu-id="1cff4-226">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_http_server_get_process*, in *nx_http_server_put_process,* or *in nx_http_server_delete_process.*</span></span>

<span data-ttu-id="1cff4-227">W celu zarejestrowania wywołania zwrotnego z serwerem HTTP następująca usługa jest definiowana w NetX serwerze HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-227">To register a callback with the HTTP server, the following service is defined in NetX HTTP Server.</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
<span data-ttu-id="1cff4-228">Typy żądań są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1cff4-228">The request types are defined as follows:</span></span>

- <span data-ttu-id="1cff4-229">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-229">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="1cff4-230">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-230">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="1cff4-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="1cff4-232">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-232">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="1cff4-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="1cff4-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="1cff4-234">Wywołanie zwrotne nagłówka daty GMT w protokole HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-234">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="1cff4-235">Istnieje opcjonalne wywołanie zwrotne w NetX serwerze HTTP, aby wstawić nagłówek daty w komunikatach odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1cff4-235">There is an optional callback in NetX HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="1cff4-236">To wywołanie zwrotne jest wywoływane, gdy serwer HTTP odpowiada na żądanie Put lub Get</span><span class="sxs-lookup"><span data-stu-id="1cff4-236">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="1cff4-237">Aby zarejestrować wywołanie zwrotne daty GMT z serwerem HTTP, następująca usługa jest zdefiniowana na serwerze HTTP NetX.</span><span class="sxs-lookup"><span data-stu-id="1cff4-237">To register a GMT date callback with the HTTP server, the following service is defined in the NetX HTTP Server.</span></span>

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="1cff4-238">Typ danych NX_HTTP_SERVER_DATE jest zdefiniowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1cff4-238">The NX_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="1cff4-239">Wywołanie zwrotne informacji o pamięci podręcznej HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-239">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="1cff4-240">Serwer HTTP ma wywołanie zwrotne, aby zażądać maksymalnego wieku i daty z aplikacji HTTP dla określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="1cff4-240">The HTTP Server has a callback to request the max age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="1cff4-241">Te informacje służą do określenia, czy serwer HTTP wysyła całą stronę w odpowiedzi na żądanie Get klienta.</span><span class="sxs-lookup"><span data-stu-id="1cff4-241">This information is used to determine if the HTTP server sends the entire page in response to a Client Get request.</span></span> <span data-ttu-id="1cff4-242">Jeśli wartość "If Modified" w żądaniu klienta nie zostanie znaleziona lub nie jest zgodna z datą "Ostatnia modyfikacja" zwracaną przez wywołanie zwrotne pobierania pamięci podręcznej, zostanie wysłana cała strona.</span><span class="sxs-lookup"><span data-stu-id="1cff4-242">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="1cff4-243">W celu zarejestrowania wywołania zwrotnego z serwerem HTTP jest definiowana następująca usługa:</span><span class="sxs-lookup"><span data-stu-id="1cff4-243">To register the callback with the HTTP server the following service is defined:</span></span>

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a><span data-ttu-id="1cff4-244">Obsługa wieloczęściowego protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-244">HTTP Multipart Support</span></span>

<span data-ttu-id="1cff4-245">Rozszerzenia Multipurpose Internet Mail Extensions (MIME) zostały pierwotnie zamierzone dla protokołu SMTP, ale jego użycie ma rozproszenie do protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cff4-245">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="1cff4-246">Kodowanie MIME umożliwia komunikatów zawierających mieszane typy wiadomości (np. Image/jpg i Text/zwykły) w obrębie tego samego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1cff4-246">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="1cff4-247">Serwer HTTP NetX dodał usługi do określenia typu zawartości w komunikatach HTTP zawierających MIME z klienta.</span><span class="sxs-lookup"><span data-stu-id="1cff4-247">NetX HTTP Server has added services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="1cff4-248">Aby włączyć obsługę wieloczęściowego protokołu HTTP i korzystać z tych usług, należy zdefiniować **NX_HTTP_MULTIPART_ENABLE** opcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1cff4-248">To enable HTTP multipart support and use these services, the configuration option **NX_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="1cff4-249">Aby uzyskać więcej informacji na temat korzystania z tych usług, zobacz opis w rozdziale 3 "Opis usług HTTP".</span><span class="sxs-lookup"><span data-stu-id="1cff4-249">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="1cff4-250">Obsługa wielowątkowości HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-250">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="1cff4-251">Usługi klienta HTTP NetX można wywoływać z wielu wątków jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="1cff4-251">The NetX HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="1cff4-252">Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta HTTP powinny być wykonywane w kolejności z tego samego wątku.</span><span class="sxs-lookup"><span data-stu-id="1cff4-252">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="1cff4-253">Specyfikacje RFC protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="1cff4-253">HTTP RFCs</span></span>

<span data-ttu-id="1cff4-254">NetX HTTP jest zgodny z RFC1945 "Hypertext Transfer Protocol/1.0", RFC 2581 "kontrola przeciążenia TCP", RFC 1122 "wymagania dotyczące hostów internetowych" i powiązane dokumenty RFC.</span><span class="sxs-lookup"><span data-stu-id="1cff4-254">NetX HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>