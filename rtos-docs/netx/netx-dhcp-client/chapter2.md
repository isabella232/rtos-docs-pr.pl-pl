---
title: Rozdział 2 — Instalowanie i używanie klienta DHCP usługi Azure RTO NetX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika klienta DHCP usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9224a4df70b8199032066e30108250a3baeb65f5
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822704"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dhcp-client"></a><span data-ttu-id="458a4-103">Rozdział 2 — Instalowanie i używanie klienta DHCP usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="458a4-103">Chapter 2 - Installation and use of Azure RTOS NetX DHCP Client</span></span>

<span data-ttu-id="458a4-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika DHCP usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="458a4-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX DHCP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="458a4-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="458a4-105">Product Distribution</span></span>

<span data-ttu-id="458a4-106">Usługa DHCP dla NetX jest dostępna pod adresem [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="458a4-106">DHCP for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="458a4-107">Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="458a4-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="458a4-108">**nx_dhcp. h** Plik nagłówka dla protokołu DHCP dla NetX</span><span class="sxs-lookup"><span data-stu-id="458a4-108">**nx_dhcp.h** Header file for DHCP for NetX</span></span>

- <span data-ttu-id="458a4-109">**nx_dhcp. c** Plik źródłowy języka C dla usługi DHCP dla NetX</span><span class="sxs-lookup"><span data-stu-id="458a4-109">**nx_dhcp.c** C Source file for DHCP for NetX</span></span>

- <span data-ttu-id="458a4-110">**nx_dhcp.pdf** Opis pliku PDF protokołu DHCP dla usługi NetX</span><span class="sxs-lookup"><span data-stu-id="458a4-110">**nx_dhcp.pdf** PDF description of DHCP for NetX</span></span>

- <span data-ttu-id="458a4-111">**demo_netx_dhcp. c** Demonstracja usługi NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="458a4-111">**demo_netx_dhcp.c** NetX DHCP demonstration</span></span>

- <span data-ttu-id="458a4-112">**demo_netx_multihome_dhcp_client. c** NetX klienta DHCP — Demonstracja DHCP na wielu interfejsach</span><span class="sxs-lookup"><span data-stu-id="458a4-112">**demo_netx_multihome_dhcp_client.c** NetX DHCP Client demonstration of DHCP on multiple interfaces</span></span>

## <a name="dhcp-installation"></a><span data-ttu-id="458a4-113">Instalacja DHCP</span><span class="sxs-lookup"><span data-stu-id="458a4-113">DHCP Installation</span></span>

<span data-ttu-id="458a4-114">Aby można było używać protokołu DHCP do NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="458a4-114">To use DHCP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="458a4-115">Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_dhcp. h* i *nx_dhcp. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="458a4-115">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_dhcp.h* and *nx_dhcp.c* files should be copied into this directory.</span></span>

## <a name="using-dhcp"></a><span data-ttu-id="458a4-116">Korzystanie z protokołu DHCP</span><span class="sxs-lookup"><span data-stu-id="458a4-116">Using DHCP</span></span>

<span data-ttu-id="458a4-117">Korzystanie z protokołu DHCP dla NetX jest proste.</span><span class="sxs-lookup"><span data-stu-id="458a4-117">Using DHCP for NetX is easy.</span></span> <span data-ttu-id="458a4-118">W zasadzie kod aplikacji musi zawierać *nx_dhcp. h* po zawiera *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX.</span><span class="sxs-lookup"><span data-stu-id="458a4-118">Basically, the application code must include *nx_dhcp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="458a4-119">Po dołączeniu *nx_dhcp. h* kod aplikacji będzie następnie mógł określić wywołania funkcji DHCP w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="458a4-119">Once *nx_dhcp.h* is included, the application code is then able to make the DHCP function calls specified later in this guide.</span></span> <span data-ttu-id="458a4-120">Aplikacja musi również zawierać *nx_dhcp. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="458a4-120">The application must also include *nx_dhcp.c* in the build process.</span></span> <span data-ttu-id="458a4-121">Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="458a4-121">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="458a4-122">To wszystko, co jest wymagane do korzystania z protokołu DHCP NetX.</span><span class="sxs-lookup"><span data-stu-id="458a4-122">This is all that is required to use NetX DHCP.</span></span>

<span data-ttu-id="458a4-123">Należy pamiętać, że ponieważ protokół DHCP korzysta z usług NetX UDP, należy włączyć protokół UDP przy użyciu wywołania *nx_udp_enable* przed użyciem protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-123">Note that since DHCP utilizes NetX UDP services, UDP must be enabled with the *nx_udp_enable* call prior to using DHCP.</span></span>

<span data-ttu-id="458a4-124">Aby uzyskać przypisany wcześniej adres IP, klient DHCP może zainicjować proces DHCP z komunikatem żądania i opcją 50 "żądany adres IP" na serwerze DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-124">To obtain a previously assigned IP address, the DHCP Client can initiate the DHCP process with the Request message and Option 50 “Requested IP Address” to the DHCP Server.</span></span> <span data-ttu-id="458a4-125">Serwer DHCP odpowie komunikatem ACK, jeśli adres IP jest przydzielany klientowi lub NACK w przypadku odmowy.</span><span class="sxs-lookup"><span data-stu-id="458a4-125">The DHCP Server will respond with either an ACK message if it grants the IP address to the Client or a NACK if it refuses.</span></span> <span data-ttu-id="458a4-126">W tym drugim przypadku klient DHCP uruchamia ponownie proces DHCP w stanie init z komunikatem odnajdowania i nie ma żądanego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="458a4-126">In the latter case, the DHCP Client restarts the DHCP process at the Init state with a Discover message and no requested IP address.</span></span> <span data-ttu-id="458a4-127">Aplikacja hosta najpierw tworzy klienta DHCP, a następnie wywołuje usługę API *nx_dhcp_request_client_ip* , aby ustawić żądany adres IP przed rozpoczęciem procesu DHCP z *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="458a4-127">The host application first creates the DHCP Client, then calls the *nx_dhcp_request_client_ip* API service to set the requested IP address before starting the DHCP process with *nx_dhcp_start*.</span></span> <span data-ttu-id="458a4-128">Przykładowa aplikacja DHCP została udostępniona w innym miejscu w tym dokumencie, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="458a4-128">An example DHCP application is provided elsewhere in this document for more details.</span></span>

## <a name="in-the-bound-state"></a><span data-ttu-id="458a4-129">W stanie związanym</span><span class="sxs-lookup"><span data-stu-id="458a4-129">In the Bound State</span></span>

<span data-ttu-id="458a4-130">Gdy klient DHCP jest w stanie powiązanym, wątek klienta DHCP przetwarza stan klienta raz na interwał (określony przez NX_DHCP_TIME_INTERVAL) i zmniejsza pozostały czas w dzierżawie IP przypisanym do klienta.</span><span class="sxs-lookup"><span data-stu-id="458a4-130">While the DHCP Client is in the bound state, the DHCP Client thread processes the Client state once per interval (as specified by NX_DHCP_TIME_INTERVAL) and decrements the time remaining on the IP lease assigned to the Client.</span></span> <span data-ttu-id="458a4-131">Po upływie czasu odnowienia stan klienta DHCP zostanie zaktualizowany do stanu ODNOWIENIa, gdy klient zażąda odnowienia z serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-131">When the renewal time has elapsed the DHCP Client state is updated to the RENEW state where the Client will request a renewal from the DHCP Server.</span></span>


## <a name="sending-dhcp-messages-to-the-server"></a><span data-ttu-id="458a4-132">Wysyłanie komunikatów DHCP do serwera</span><span class="sxs-lookup"><span data-stu-id="458a4-132">Sending DHCP Messages To The Server</span></span>

<span data-ttu-id="458a4-133">Klient DHCP ma usługi interfejsu API, które umożliwiają aplikacji hosta wysyłanie komunikatów do serwera DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-133">The DHCP Client has API services that allow the host application to send a message to the DHCP Server.</span></span> <span data-ttu-id="458a4-134">Zwróć uwagę, że te usługi nie są przeznaczone dla aplikacji hosta, aby ręcznie uruchomić protokół klienta DHCP, ponieważ przede wszystkim wysyła komunikat bez konieczności aktualizowania stanu wewnętrznego klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-134">Note these services are NOT intended for the host application to manually run the DHCP Client protocol as they primarily send the message without necessarily updating the DHCP Client internal state.</span></span>

  - <span data-ttu-id="458a4-135">*nx_dhcp_release*: wysyła komunikat o zwolnieniu do serwera, gdy aplikacja hosta opuszcza sieć lub potrzebuje jej adresu IP.</span><span class="sxs-lookup"><span data-stu-id="458a4-135">*nx_dhcp_release*: this sends a RELEASE message to the Server when the host application is either leaving the network or needs relinquish its IP address.</span></span>

  - <span data-ttu-id="458a4-136">*nx_dhcp_decline*: wysyła komunikat o odrzuceniu do serwera, jeśli aplikacja hosta określi niezależnie od klienta DHCP, że jego adres IP jest już używany.</span><span class="sxs-lookup"><span data-stu-id="458a4-136">*nx_dhcp_decline*: this sends a DECLINE message to the Server if the host application determines independently of the DHCP Client that its IP address is already in use.</span></span>

  - <span data-ttu-id="458a4-137">*nx_dhcp_forcerenew*: wysyła komunikat Forcerenew do serwera</span><span class="sxs-lookup"><span data-stu-id="458a4-137">*nx_dhcp_forcerenew*: this sends a FORCERENEW message to the Server</span></span>

  - <span data-ttu-id="458a4-138">*nx_dhcp_send_request*: przyjmuje jako argument typ komunikatu DHCP określony w *nx_dhcp. h* i wysyła komunikat do serwera.</span><span class="sxs-lookup"><span data-stu-id="458a4-138">*nx_dhcp_send_request*: This takes as an argument a DHCP message type, as specified in *nx_dhcp.h*, and sends the message to the Server.</span></span> <span data-ttu-id="458a4-139">Jest to przeznaczone głównie do wysyłania komunikatu o błędzie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-139">This is intended primarily for sending the DHCP INFORM message.</span></span>

<span data-ttu-id="458a4-140">Aby uzyskać więcej informacji na temat tych usług w innym miejscu w tym dokumencie, zobacz "*Opis usług DHCP*".</span><span class="sxs-lookup"><span data-stu-id="458a4-140">See “*Description of DHCP Services*” for more information about these services elsewhere in this document.</span></span>

## <a name="starting-and-stopping-the-dhcp-client"></a><span data-ttu-id="458a4-141">Uruchamianie i zatrzymywanie klienta DHCP</span><span class="sxs-lookup"><span data-stu-id="458a4-141">Starting and Stopping the DHCP Client</span></span>

<span data-ttu-id="458a4-142">Aby zatrzymać klienta DHCP, niezależnie od tego, czy osiągnie on stan związany, aplikacja hosta wywołuje *nx_dhcp_stop*.</span><span class="sxs-lookup"><span data-stu-id="458a4-142">To stop the DHCP Client, regardless if it has achieved a bound state, the host application calls *nx_dhcp_stop*.</span></span>

<span data-ttu-id="458a4-143">Aby ponownie uruchomić klienta DHCP, aplikacja hosta musi najpierw zatrzymać klienta DHCP przy użyciu usługi *nx_dhcp_stop* opisanej powyżej.</span><span class="sxs-lookup"><span data-stu-id="458a4-143">To restart a DHCP client, the host application must first stop the DHCP Client using the *nx_dhcp_stop* service described above.</span></span> <span data-ttu-id="458a4-144">Następnie host może wywoływać *nx_dhcp_start* , aby wznowić działanie klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-144">Then the host can call *nx_dhcp_start* to resume the DHCP Client.</span></span> <span data-ttu-id="458a4-145">Jeśli aplikacja hosta chce wyczyścić poprzedni profil klienta DHCP, na przykład jeden uzyskany przez poprzedni serwer DHCP w innej sieci, aplikacja hosta powinna wywołać *nx_dhcp_reinitialize* , aby wykonać to zadanie wewnętrznie przed wywołaniem nx_dhcp_start.</span><span class="sxs-lookup"><span data-stu-id="458a4-145">If the host application wishes to clear a previous DHCP Client profile, for example, one obtained from a previous DHCP Server on another network, the host application should call *nx_dhcp_reinitialize* to perform this task internally before calling nx_dhcp_start.</span></span>

<span data-ttu-id="458a4-146">Typową sekwencją może być:</span><span class="sxs-lookup"><span data-stu-id="458a4-146">A typical sequence might be:</span></span>

```C
nx_dhcp_stop(&my_dhcp);

nx_dhcp_reinitialize(&my_dhcp);

nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="458a4-147">W przypadku aplikacji DHCP uruchamianych tylko na jednym interfejsie DHCP zatrzymanie klienta DHCP powoduje także dezaktywację czasomierza klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-147">For DHCP applications running on only a single DHCP interface, stopping the DHCP Client also inactivates the DHCP CLIENT timer.</span></span> <span data-ttu-id="458a4-148">W rezultacie nie jest już śledzony czas pozostały w dzierżawie IP.</span><span class="sxs-lookup"><span data-stu-id="458a4-148">Thus it is no longer keeping track of the time remaining on the IP lease.</span></span> <span data-ttu-id="458a4-149">Zatrzymanie klienta DHCP w określonym interfejsie nie spowoduje dezaktywacji czasomierza klienta DHCP, ale spowoduje zatrzymanie aktualizacji czasomierza do czasu pozostałej w dzierżawie IP w tym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="458a4-149">Stopping DHCP Client on a particular interface will not inactivate the DHCP Client timer but will stop timer updates to the time remaining on the IP lease on that interface.</span></span>

<span data-ttu-id="458a4-150">W związku z tym zatrzymanie klienta DHCP nie jest zalecane, chyba że aplikacja hosta wymaga ponownego uruchomienia lub przełączenia sieci.</span><span class="sxs-lookup"><span data-stu-id="458a4-150">Therefore, stopping the DHCP Client is not advised unless the host application requires rebooting or switching networks.</span></span>

## <a name="using-the-dhcp-client-with-auto-ip"></a><span data-ttu-id="458a4-151">Korzystanie z klienta DHCP z opcją AutoIP</span><span class="sxs-lookup"><span data-stu-id="458a4-151">Using the DHCP Client with Auto IP</span></span>

<span data-ttu-id="458a4-152">Klient DHCP NetX działa równolegle z protokołem AutoIP w aplikacjach, w których DHCP i AutoIP gwarantują adres, w którym serwer DHCP nie ma gwarancji, że jest dostępny lub nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="458a4-152">The NetX DHCP Client works concurrently with the Auto IP protocol in applications where DHCP and Auto IP guarantee an address where a DHCP Server is not guaranteed to be available or responding.</span></span> <span data-ttu-id="458a4-153">Jeśli jednak host nie może wykryć serwera lub uzyskać przypisanego adresu IP, może przełączyć się do protokołu automatyczne IP dla lokalnego adresu IP.</span><span class="sxs-lookup"><span data-stu-id="458a4-153">However, If the host is unable to detect a Server or get an IP address assigned, it can switch to the Auto IP protocol for a local IP address.</span></span> <span data-ttu-id="458a4-154">Jednak przed wykonaniem tej czynności zaleca się tymczasowe zatrzymanie klienta DHCP w ramach etapów "sondy" i "Obrona".</span><span class="sxs-lookup"><span data-stu-id="458a4-154">However before doing so, it is advisable to stop the DHCP Client temporarily while Auto IP goes through the “probe” and “defense” stages.</span></span> <span data-ttu-id="458a4-155">Po przypisaniu automatycznie adresu IP do hosta klient DHCP może zostać ponownie uruchomiony, a jeśli serwer DHCP stanie się dostępny, adres IP hosta może akceptować adres IP oferowany przez serwer DHCP, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="458a4-155">Once an Auto IP address is assigned to the host, the DHCP Client can be restarted and if a DHCP Server does become available, the host IP address can accept the IP address offered by the DHCP Server while the application is running.</span></span>

<span data-ttu-id="458a4-156">NetX automatycznie IP ma powiadomienie o zmianie adresu dla hosta, aby monitorować jego działania w przypadku zmiany adresu IP.</span><span class="sxs-lookup"><span data-stu-id="458a4-156">The NetX Auto IP has an address change notification for the host to monitor its activities in the event of an IP address change.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="458a4-157">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="458a4-157">Small Example System</span></span>

<span data-ttu-id="458a4-158">Przykład sposobu użycia NetX został opisany na rysunku 1,1 poniżej.</span><span class="sxs-lookup"><span data-stu-id="458a4-158">An example of how use NetX is described in Figure 1.1 below.</span></span> <span data-ttu-id="458a4-159">Klient DHCP jest tworzony "*my_thread_entry*" w wierszu 101.</span><span class="sxs-lookup"><span data-stu-id="458a4-159">The DHCP Client is created “*my_thread_entry*” at line 101.</span></span> <span data-ttu-id="458a4-160">Po pomyślnym utworzeniu proces DHCP zostanie zainicjowany przy wywołaniu *nx_dhcp_start* w wierszu 108.</span><span class="sxs-lookup"><span data-stu-id="458a4-160">After successful creation, the DHCP process is initiated at the call to *nx_dhcp_start* at line 108.</span></span> <span data-ttu-id="458a4-161">W tym momencie próby klienta DHCP są inicjowane w celu skontaktowania się z serwerem DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-161">At this point the DHCP Client attempts are initiated to contact the DHCP server.</span></span> <span data-ttu-id="458a4-162">W trakcie tego procesu kod aplikacji czeka na zarejestrowanie prawidłowego adresu IP w wystąpieniu IP przy użyciu usługi *nx_ip_status_check* (lub *nx_ip_interface_status_check* dla interfejsu pomocniczego), zaczynając od wiersza 95.</span><span class="sxs-lookup"><span data-stu-id="458a4-162">During this process, the application code waits for a valid IP address to be registered with the IP instance using the *nx_ip_status_check* service (or *nx_ip_interface_status_check* for a secondary interface) starting at line 95.</span></span> <span data-ttu-id="458a4-163">Jest to bardziej często wykonywane w pętli z krótszą opcją oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="458a4-163">This is more commonly done in a loop with a shorter wait option.</span></span>

<span data-ttu-id="458a4-164">Po wierszu 127 usługa DHCP odebrała prawidłowy adres IP, a następnie może działać, wykorzystując NetX usługi TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="458a4-164">After line 127, DHCP has received a valid IP address and the application can then proceed, utilizing NetX TCP/IP services as desired.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
      0xFFFFFF00, &my_pool, my_netx_driver, pointer, 
      DEMO_STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


/* Define my thread. */

void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    actual_status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip, NX_IP_LINK_ENABLED, 
                            &actual_status, 100);

  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="458a4-165">Rysunek 1,1 przykład użycia protokołu DHCP z NetX</span><span class="sxs-lookup"><span data-stu-id="458a4-165">Figure 1.1 Example of DHCP use with NetX</span></span>

## <a name="multi-server-environments"></a><span data-ttu-id="458a4-166">Środowiska z obsługą wielu serwerów</span><span class="sxs-lookup"><span data-stu-id="458a4-166">Multi-Server Environments</span></span>

<span data-ttu-id="458a4-167">W sieciach, w których istnieje więcej niż jeden serwer DHCP, klient DHCP akceptuje pierwszy odebrany komunikat oferty serwera DHCP, postępuje zgodnie ze stanem żądania i ignoruje wszelkie inne odebrane oferty.</span><span class="sxs-lookup"><span data-stu-id="458a4-167">On networks where there is more than one DHCP Server, the DHCP Client accepts the first received DHCP Server Offer message, advances to the Request state, and ignores any other received offers.</span></span>

## <a name="arp-probes"></a><span data-ttu-id="458a4-168">Sondy protokołu ARP</span><span class="sxs-lookup"><span data-stu-id="458a4-168">ARP Probes</span></span>

<span data-ttu-id="458a4-169">Klienta DHCP można skonfigurować tak, aby wysyłał co najmniej jedną sondę protokołu ARP po przypisaniu adresu IP z serwera DHCP w celu sprawdzenia, czy adres IP nie jest jeszcze używany.</span><span class="sxs-lookup"><span data-stu-id="458a4-169">The DHCP Client can be configured to send one or more ARP probes after IP address assignment from the DHCP Server to verify the IP address is not already in use.</span></span> <span data-ttu-id="458a4-170">Krok sondowania ARP jest zalecany przez RFC 2131 i jest szczególnie istotny w środowiskach z więcej niż jednym serwerem DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-170">The ARP probe step is recommended by RFC 2131 and is particularly important in environments with more than one DHCP Server.</span></span> <span data-ttu-id="458a4-171">Jeśli aplikacja hosta włącza opcję NX_DHCP_CLIENT_SEND_ARP_PROBE (zobacz **Opcje konfiguracji** w rozdziale dwa w przypadku dodatkowych opcji sondowania ARP), klient DHCP wyśle sondę ARP "z własnymi żądaniami" i poczeka przez określony czas na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="458a4-171">If the host application enables the NX_DHCP_CLIENT_SEND_ARP_PROBE option (see **Configuration Options** in Chapter Two for additional ARP probe options), the DHCP Client will send a ‘self addressed’ ARP probe and wait for the specified time for a response.</span></span> <span data-ttu-id="458a4-172">Jeśli żaden nie zostanie odebrany, klient DHCP postępuje ze stanem związanym.</span><span class="sxs-lookup"><span data-stu-id="458a4-172">If none is received, the DHCP Client advances to the Bound state.</span></span> <span data-ttu-id="458a4-173">W przypadku odebrania odpowiedzi klient DHCP zakłada, że adres jest już używany.</span><span class="sxs-lookup"><span data-stu-id="458a4-173">If a response is received, the DHCP Client assumes the address is already in use.</span></span> <span data-ttu-id="458a4-174">Automatycznie wysyła komunikat odrzucania do serwera i ponownie inicjuje klienta, aby ponownie uruchomić sondy DHCP ze stanu INIT.</span><span class="sxs-lookup"><span data-stu-id="458a4-174">It automatically sends a DECLINE message to the Server, and reinitializes the Client to restart the DHCP probes again from the INIT state.</span></span> <span data-ttu-id="458a4-175">Spowoduje to ponowne uruchomienie komputera stanu DHCP, a klient wysyła do serwera inny komunikat ODNAJDOWAnia.</span><span class="sxs-lookup"><span data-stu-id="458a4-175">This restarts the DHCP state machine and the Client sends another DISCOVER message to the Server.</span></span>

## <a name="bootp-protocol"></a><span data-ttu-id="458a4-176">Protokół BOOTP</span><span class="sxs-lookup"><span data-stu-id="458a4-176">BOOTP Protocol</span></span>

<span data-ttu-id="458a4-177">Klient DHCP obsługuje również protokół BOOTP.</span><span class="sxs-lookup"><span data-stu-id="458a4-177">The DHCP Client also supports the BOOTP protocol as well the DHCP protocol.</span></span> <span data-ttu-id="458a4-178">Aby włączyć tę opcję i użyć protokołu BOOTP zamiast DHCP, aplikacja hosta musi ustawić opcję konfiguracji NX_DHCP_BOOTP_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="458a4-178">To enable this option and use BOOTP instead of DHCP, the host application must set the NX_DHCP_BOOTP_ENABLE configuration option.</span></span> <span data-ttu-id="458a4-179">Aplikacja hosta może nadal żądać określonych adresów IP w protokole BOOTP.</span><span class="sxs-lookup"><span data-stu-id="458a4-179">The host application can still request specific IP addresses in the BOOTP protocol.</span></span> <span data-ttu-id="458a4-180">Klient DHCP nie obsługuje jednak ładowania systemu operacyjnego hosta, ponieważ protokół BOOTP jest czasami używany do wykonania.</span><span class="sxs-lookup"><span data-stu-id="458a4-180">However, the DHCP Client does not support loading the host operating system as BOOTP is sometimes used to do.</span></span>

## <a name="dhcp-on-a-secondary-interface"></a><span data-ttu-id="458a4-181">Protokół DHCP w interfejsie pomocniczym</span><span class="sxs-lookup"><span data-stu-id="458a4-181">DHCP on a Secondary Interface</span></span>

<span data-ttu-id="458a4-182">Klienta DHCP NetX można uruchomić na interfejsach pomocniczych, a nie w domyślnym interfejsie głównym.</span><span class="sxs-lookup"><span data-stu-id="458a4-182">The NetX DHCP Client can run on secondary interfaces rather than the default primary interface.</span></span>

<span data-ttu-id="458a4-183">Aby uruchomić NetX klienta DHCP w dodatkowym interfejsie sieciowym, aplikacja hosta musi ustawić indeks interfejsu klienta DHCP na pomocniczy interfejs przy użyciu usługi interfejsu API *nx_dhcp_set_interface_index* .</span><span class="sxs-lookup"><span data-stu-id="458a4-183">To run NetX DHCP Client on a secondary network interface, the host application must set the interface index of the DHCP Client to the secondary interface using the *nx_dhcp_set_interface_index* API service.</span></span> <span data-ttu-id="458a4-184">Interfejs musi być już dołączony do podstawowego interfejsu sieciowego przy użyciu usługi *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="458a4-184">The interface must already be attached to the primary network interface using the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="458a4-185">Więcej informacji na temat dołączania interfejsów pomocniczych można znaleźć w podręczniku użytkownika NetX.</span><span class="sxs-lookup"><span data-stu-id="458a4-185">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="458a4-186">1,2 poniżej przedstawiono przykładowy system, w którym aplikacja hosta nawiązuje połączenie z serwerem DHCP w interfejsie pomocniczym.</span><span class="sxs-lookup"><span data-stu-id="458a4-186">Below in Figure 1.2 is an example system on which the host application connects to the DHCP server on its secondary interface.</span></span> <span data-ttu-id="458a4-187">W wierszu 65 pomocniczy interfejs jest dołączany do zadania IP z adresem IP o wartości null.</span><span class="sxs-lookup"><span data-stu-id="458a4-187">On line 65, the secondary interface is attached to the IP task with a null IP address.</span></span> <span data-ttu-id="458a4-188">W wierszu 104 po utworzeniu wystąpienia klienta DHCP indeks interfejsu klienta DHCP jest ustawiony na 1 (np. przesunięcie od podstawowego interfejsu, który sam jest indeksem 0) przez wywołanie *nx_dhcp_set_interface_index*.</span><span class="sxs-lookup"><span data-stu-id="458a4-188">On line 104, after the DHCP Client instance is created, the DHCP Client interface index is set to 1 (e.g. the offset from the primary interface which itself is index 0) by calling *nx_dhcp_set_interface_index*.</span></span> <span data-ttu-id="458a4-189">Następnie klient DHCP jest gotowy do uruchomienia w wierszu 108.</span><span class="sxs-lookup"><span data-stu-id="458a4-189">Then the DHCP Client is ready to be started in line 108.</span></span>

```C
#include  "tx_api.h"
#include  "nx_api.h"
#include  "nx_dhcp.h"

#define   DEMO_STACK_SIZE     4096
TX_THREAD        my_thread;
NX_PACKET_POOL     my_pool;
NX_IP          my_ip;
NX_DHCP         my_dhcp;

/* Define function prototypes. */

void  my_thread_entry(ULONG thread_input);
void  my_netx_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

intmain()
{

  /* Enter the ThreadX kernel. */
  tx_kernel_enter();
}


/* Define what the initial system looks like. */

void  tx_application_define(void *first_unused_memory)
{

CHAR  *pointer;
UINT  status;

  
  /* Setup the working pointer. */
  pointer = (CHAR *) first_unused_memory;

  /* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0, 
            pointer, DEMO_STACK_SIZE, 
            2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Initialize the NetX system. */
  nx_system_initialize();

  /* Create a packet pool. */
  status = nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                     1024, pointer, 64000);
  pointer = pointer + 64000;

  /* Check for pool creation error. */
  if (status)
    error_counter++;

  /* Create an IP instance without an IP address. */
  status = nx_ip_create(&my_ip, "My NetX IP Instance", IP_ADDRESS(0,0,0,0), 
       0xFFFFFF00, &my_pool, my_netx_driver, pointer, STACK_SIZE, 1);
  pointer = pointer + DEMO_STACK_SIZE;

  /* Check for IP create errors. */
  if (status)
    error_counter++;

  status = _nx_ip_interface_attach(&ip_0, "port_2", IP_ADDRESS(0, 0, 0,0), 
                            0xFFFFFF00UL, my_netx_driver);
                            
  /* Enable ARP and supply ARP cache memory for my IP Instance. */
  status = nx_arp_enable(&my_ip, (void *) pointer, 1024);
  pointer = pointer + 1024;

  /* Check for ARP enable errors. */
  if (status)
    error_counter++;

  /* Enable UDP. */
  status = nx_udp_enable(&my_ip);
  if (status)
    error_counter++;
}


void  my_thread_entry(ULONG thread_input)
{

UINT    status;
ULONG    status;
NX_PACKET  *my_packet;

  /* Wait for the link to come up. */
  do
  {

    /* Get the link status. */
    status = nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,& status,100);
  } while (status != NX_SUCCESS);

  /* Create a DHCP instance. */
  status = nx_dhcp_create(&my_dhcp, &my_ip, "My DHCP");

  /* Check for DHCP create error. */
  if (status)
    error_counter++;

  /* Set the DHCP client interface to the secondary interface. 
    status = nx_dhcp_set_interface_index(&my_dhcp, 1);


  /* Start DHCP. */
  nx_dhcp_start(&my_dhcp);

  /* Check for DHCP start error. */
  if (status)
    error_counter++;

  /* Wait for IP address to be resolved through DHCP. */
  nx_ip_status_check(&my_ip, NX_IP_ADDRESS_RESOLVED, 
                        (ULONG *) &status, 100000);

  /* Check to see if we have a valid IP address. */
  if (status)
  {
    error_counter++;
    return;
  }
  else
  {

        /* Yes, a valid IP address is now on lease… All NetX
      services are available.
  }
}
```

<span data-ttu-id="458a4-190">Rysunek 1,2 przykład protokołu DHCP dla NetX z obsługą wielostrony</span><span class="sxs-lookup"><span data-stu-id="458a4-190">Figure 1.2 Example of DHCP for NetX with multihome support</span></span>

## <a name="dhcp-client-on-multiple-interfaces-simultaneously"></a><span data-ttu-id="458a4-191">Klient DHCP w wielu interfejsach jednocześnie</span><span class="sxs-lookup"><span data-stu-id="458a4-191">DHCP Client on Multiple Interfaces Simultaneously</span></span>

<span data-ttu-id="458a4-192">Aby uruchomić klienta DHCP na wielu interfejsach, NX_MAX_PHYSICAL_INTERFACES w *nx_api. h* musi być ustawiona na liczbę fizycznych interfejsów podłączonych do urządzenia.</span><span class="sxs-lookup"><span data-stu-id="458a4-192">To run DHCP Client on multiple interfaces, NX_MAX_PHYSICAL_INTERFACES in *nx_api.h* must be set to the number of physical interfaces connected to the device.</span></span> <span data-ttu-id="458a4-193">Domyślnie ta wartość jest równa 1 (np. podstawowy interfejs).</span><span class="sxs-lookup"><span data-stu-id="458a4-193">By default, this value is 1 (e.g. the primary interface).</span></span> <span data-ttu-id="458a4-194">Aby zarejestrować dodatkowy interfejs w wystąpieniu protokołu IP, Użyj usługi *nx_ip_interface_attach* .</span><span class="sxs-lookup"><span data-stu-id="458a4-194">To register an additional interface to the IP instance use the *nx_ip_interface_attach* service.</span></span> <span data-ttu-id="458a4-195">Więcej informacji na temat dołączania interfejsów pomocniczych można znaleźć w podręczniku użytkownika NetX.</span><span class="sxs-lookup"><span data-stu-id="458a4-195">See the NetX User Guide for more details on attaching secondary interfaces.</span></span>

<span data-ttu-id="458a4-196">Następnym krokiem jest ustawienie NX_DHCP_CLIENT_MAX_RECORDS w *nx_dhcp. h* na maksymalną liczbę interfejsów oczekiwanych na równoczesne uruchomienie protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-196">The next step is to set the NX_DHCP_CLIENT_MAX_RECORDS in *nx_dhcp.h* to the maximum number of interfaces expected to run DHCP simultaneously.</span></span> <span data-ttu-id="458a4-197">Należy pamiętać, że NX_DHCP_CLIENT_MAX_RECORDS nie muszą być równe NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="458a4-197">Note that NX_DHCP_CLIENT_MAX_RECORDS does not have to equal NX_MAX_PHYSICAL_INTERFACES.</span></span> <span data-ttu-id="458a4-198">Na przykład NX_MAX_PHYSICAL_INTERFACES może mieć wartość 3 i NX_DHCP_CLIENT_MAX_RECORDS równe 2.</span><span class="sxs-lookup"><span data-stu-id="458a4-198">For example, NX_MAX_PHYSICAL_INTERFACES can be 3 and NX_DHCP_CLIENT_MAX_RECORDS equal to 2.</span></span> <span data-ttu-id="458a4-199">W tej konfiguracji tylko dwa interfejsy (i mogą być dowolne dwa z trzech interfejsów fizycznych w dowolnym momencie) spośród trzech interfejsów fizycznych można w dowolnym momencie uruchomić usługę DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-199">In this configuration, only two interfaces (and they can be any two of the three physical interfaces at any time) of the three physical interfaces can run DHCP at any one time.</span></span> <span data-ttu-id="458a4-200">Rekordy klienta DHCP nie mają mapowania jeden do jednego do interfejsów sieciowych, np. rekord klienta 1 nie jest automatycznie skorelowany z indeksem interfejsu fizycznego 1.</span><span class="sxs-lookup"><span data-stu-id="458a4-200">DHCP Client Records do not have a one to one mapping to network interfaces e.g. Client Record 1 does not automatically correlate to physical interface index 1.</span></span>

<span data-ttu-id="458a4-201">NX_DHCP_CLIENT_MAX_RECORDS można również ustawić na wartość większą niż NX_MAX_PHYSICAL_INTERFACES, ale spowoduje to utworzenie nieużywanych rekordów klienta i niewydajne użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="458a4-201">NX_DHCP_CLIENT_MAX_RECORDS can also be set to greater than NX_MAX_PHYSICAL_INTERFACES but this would create unused client records and be an inefficient use of memory.</span></span>

<span data-ttu-id="458a4-202">Aby można było uruchomić protokół DHCP w dowolnym interfejsie, aplikacja musi włączyć te interfejsy, wywołując *nx_dhcp_interface_enable*.</span><span class="sxs-lookup"><span data-stu-id="458a4-202">Before it can start DHCP on any interface, the application must enable those interfaces by calling *nx_dhcp_interface_enable*.</span></span> <span data-ttu-id="458a4-203">Należy zauważyć, że wyjątek jest interfejsem podstawowym, który jest automatycznie włączany w wywołaniu *nx_dhcp_create* (i które można wyłączyć za pomocą usługi *nx_dhcp_interface_disable* opisanej poniżej).</span><span class="sxs-lookup"><span data-stu-id="458a4-203">Note that the exception is the primary interface which is automatically enabled in the *nx_dhcp_create* call (and which can be disabled using the *nx_dhcp_interface_disable* service discussed below).</span></span>

<span data-ttu-id="458a4-204">W dowolnym momencie można wyłączyć interfejs DHCP lub można zatrzymać protokół DHCP niezależnie od innych interfejsów z uruchomionym protokołem DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-204">At any time, an interface can be disabled for DHCP or DHCP can be stopped on that interface independently of other interfaces running DHCP.</span></span>

<span data-ttu-id="458a4-205">Jak wspomniano powyżej, aby włączyć określony interfejs dla usługi DHCP, należy użyć usługi *nx_dhcp_interface_enable* i określić indeks interfejsu fizycznego w argumencie wejściowym.</span><span class="sxs-lookup"><span data-stu-id="458a4-205">As mentioned above, to enable a specific interface for DHCP, use the *nx_dhcp_interface_enable* service and specify the physical interface index in the input argument.</span></span> <span data-ttu-id="458a4-206">Można włączyć do NX_DHCP_CLIENT_MAX_RECORDS interfejsów z jedynym ograniczeniem, że argument wejściowy indeksu interfejsu jest krótszy niż NX_MAX_PHYSICAL_INTERFACES.</span><span class="sxs-lookup"><span data-stu-id="458a4-206">Up to NX_DHCP_CLIENT_MAX_RECORDS interfaces can be enabled with the only limitation that the interface index input argument be less than NX_MAX_PHYSICAL_INTERFACES.</span></span>

<span data-ttu-id="458a4-207">Aby uruchomić protokół DHCP w określonym interfejsie, Użyj usługi *nx_dhcp_interface_start* .</span><span class="sxs-lookup"><span data-stu-id="458a4-207">To start DHCP on a specific interface, use the *nx_dhcp_interface_start* service.</span></span> <span data-ttu-id="458a4-208">Aby uruchomić protokół DHCP we wszystkich włączonych interfejsach, Użyj usługi *nx_dhcp_start* .</span><span class="sxs-lookup"><span data-stu-id="458a4-208">To start DHCP on all enabled interfaces, use the *nx_dhcp_start* service.</span></span> <span data-ttu-id="458a4-209">(Interfejsy, które już uruchomiły protokół DHCP, nie będą miały wpływ na *nx_dhcp_start*).</span><span class="sxs-lookup"><span data-stu-id="458a4-209">(Interfaces that have already started DHCP will not be affected by *nx_dhcp_start*.)</span></span>

<span data-ttu-id="458a4-210">Aby zatrzymać usługę DHCP w interfejsie, Użyj usługi *nx_dhcp_interface_stop* .</span><span class="sxs-lookup"><span data-stu-id="458a4-210">To stop DHCP on an interface, use the *nx_dhcp_interface_stop* service.</span></span> <span data-ttu-id="458a4-211">Protokół DHCP musi już być uruchomiony w tym interfejsie lub zwracany jest stan błędu.</span><span class="sxs-lookup"><span data-stu-id="458a4-211">DHCP must already have started on that interface or an error status is returned.</span></span> <span data-ttu-id="458a4-212">Aby zatrzymać protokół DHCP we wszystkich włączonych interfejsach, Użyj usługi *nx_dhcp_stop* .</span><span class="sxs-lookup"><span data-stu-id="458a4-212">To stop DHCP on all enabled interfaces, use the *nx_dhcp_stop* service.</span></span> <span data-ttu-id="458a4-213">Protokół DHCP można zatrzymać niezależnie od innych interfejsów w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="458a4-213">DHCP can be stopped independently of other interfaces at any time.</span></span>

<span data-ttu-id="458a4-214">Większość istniejących usług klienta DHCP ma odpowiednik "Interface", np. *nx_dhcp_interface_release* jest odpowiednikiem określonego interfejsu *nx_dhcp_release.*</span><span class="sxs-lookup"><span data-stu-id="458a4-214">Most of the existing DHCP Client services have an ‘interface’ equivalent e.g. *nx_dhcp_interface_release* is the interface specific equivalent of *nx_dhcp_release.*</span></span> <span data-ttu-id="458a4-215">Jeśli klient DHCP jest skonfigurowany dla jednego interfejsu, wykonuje tę samą akcję.</span><span class="sxs-lookup"><span data-stu-id="458a4-215">If DHCP Client is configured for a single interface, they perform the same action.</span></span>

<span data-ttu-id="458a4-216">Należy pamiętać, że usługi klienta DHCP niezwiązane z interfejsem zwykle mają zastosowanie do wszystkich interfejsów, ale nie wszystkich.</span><span class="sxs-lookup"><span data-stu-id="458a4-216">Note that non-interface specific DHCP Client services typically apply to all interfaces but not all.</span></span> <span data-ttu-id="458a4-217">W tym drugim przypadku usługa niezależna od interfejsu dotyczy pierwszego interfejsu z włączonym protokołem DHCP, który znajduje się w przeszukiwaniu listy klientów DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-217">In the latter case, the non-interface specific service applies to the first DHCP enabled interface found in searching the DHCP Client list of interface records.</span></span> <span data-ttu-id="458a4-218">Zobacz **Opis usług** w rozdziale trzeci, w jaki sposób usługa niezależna od interfejsu jest wykonywana w przypadku włączenia wielu interfejsów dla protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-218">See **Description of Services** in Chapter Three for how a non-interface specific service performs when multiple interfaces are enabled for DHCP.</span></span>

<span data-ttu-id="458a4-219">W przykładowej sekwencji poniżej wystąpienie protokołu IP ma dwa interfejsy sieciowe i najpierw uruchamia DHCP w interfejsie pomocniczym.</span><span class="sxs-lookup"><span data-stu-id="458a4-219">In the example sequence below, the IP instance has two network interfaces and first runs DHCP on the secondary interface.</span></span> <span data-ttu-id="458a4-220">W pewnym momencie później zostanie uruchomiony protokół DHCP w interfejsie podstawowym.</span><span class="sxs-lookup"><span data-stu-id="458a4-220">At some time later, it starts DHCP on the primary interface.</span></span> <span data-ttu-id="458a4-221">Następnie zwalnia adres IP w interfejsie podstawowym i ponownie uruchamia DHCP w interfejsie głównym:</span><span class="sxs-lookup"><span data-stu-id="458a4-221">Then it releases the IP address on the primary interface and restarts DHCP on the primary interface:</span></span>

```C
nx_dhcp_create(&my_dhcp_client);
/* By default this enables primary interface for DHCP. */

nx_dhcp_interface_enable(&my_dhcp_client, 1); 
/* Secondary interface is enabled. */

nx_dhcp_interface_start(&my_dhcp_client, 1); 
/* DHCP is started on secondary interface. */

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is started on primary interface. */

nx_dhcp_interface_release(&my_dhcp_client, 0); 

/* Some time later… */

nx_dhcp_interface_start(&my_dhcp_client, 0); 
/* DHCP is restarted on primary interface. */
```

<span data-ttu-id="458a4-222">Aby uzyskać pełną listę specyficznych dla interfejsu usług, zobacz **Opis usług** w rozdziale 3.</span><span class="sxs-lookup"><span data-stu-id="458a4-222">For a complete list of interface specific services see **Description of Services** in Chapter Three.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="458a4-223">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="458a4-223">Configuration Options</span></span>

<span data-ttu-id="458a4-224">Użytkownik konfigurowalny opcje DHCP w *nx_dhcp. h* zezwala aplikacji hosta na precyzyjne dopasowanie klienta DHCP do określonych wymagań.</span><span class="sxs-lookup"><span data-stu-id="458a4-224">User configurable DHCP options in *nx_dhcp.h* allow the host application to fine tune DHCP Client for its particular requirements.</span></span> <span data-ttu-id="458a4-225">Poniżej znajduje się lista tych parametrów:</span><span class="sxs-lookup"><span data-stu-id="458a4-225">The following is a list of these parameters:</span></span>  
  
- <span data-ttu-id="458a4-226">**NX_DHCP_ENABLE_BOOTP** Zdefiniowana, ta opcja włącza protokół BOOTP zamiast DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-226">**NX_DHCP_ENABLE_BOOTP** Defined, this option enables the BOOTP protocol instead of DHCP.</span></span> <span data-ttu-id="458a4-227">Domyślnie ta opcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="458a4-227">By default this option is disabled.</span></span>

- <span data-ttu-id="458a4-228">**NX_DHCP_CLIENT_RESTORE_STATE** Jeśli ta wartość jest zdefiniowana, umożliwia klientowi DHCP zapisanie bieżącej licencji klienta DHCP, w tym czasu pozostałej w dzierżawie, i przywrócenie tego stanu między ponownymi uruchomieniami aplikacji klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-228">**NX_DHCP_CLIENT_RESTORE_STATE** If defined, this enables the DHCP Client to save its current DHCP Client license ‘state’ including time remaining on the lease, and restore this state between DHCP Client application reboots.</span></span> <span data-ttu-id="458a4-229">Wartość domyślna jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="458a4-229">The default value is disabled.</span></span>

- <span data-ttu-id="458a4-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** W przypadku wybrania tej opcji klient DHCP nie będzie tworzyć własnej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="458a4-230">**NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL** If set, the DHCP Client will not create its own packet pool.</span></span> <span data-ttu-id="458a4-231">Aplikacja hosta musi używać usługi nx_dhcp_packet_pool_set, aby ustawić pulę pakietów klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-231">The host application must use the nx_dhcp_packet_pool_set service to set the DHCP Client packet pool.</span></span> <span data-ttu-id="458a4-232">Wartość domyślna jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="458a4-232">The default value is disabled.</span></span>

- <span data-ttu-id="458a4-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** Zdefiniowane, umożliwia klientowi DHCP wysyłanie sondy ARP po przypisaniu adresów IP w celu sprawdzenia, czy przypisany adres DHCP nie jest własnością innego hosta.</span><span class="sxs-lookup"><span data-stu-id="458a4-233">**NX_DHCP_CLIENT_SEND_ARP_PROBE** Defined, this enables the DHCP Client to send an ARP probe after IP address assignment to verify the assigned DHCP address is not owned by another host.</span></span> <span data-ttu-id="458a4-234">Domyślnie ta opcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="458a4-234">By default, this option is disabled.</span></span>

- <span data-ttu-id="458a4-235">**NX_DHCP_ARP_PROBE_WAIT** Określa czas oczekiwania przez klienta DHCP na odpowiedź po wysłaniu sondy ARP.</span><span class="sxs-lookup"><span data-stu-id="458a4-235">**NX_DHCP_ARP_PROBE_WAIT** Defines the length of time the DHCP Client waits for a response after sending an ARP probe.</span></span> <span data-ttu-id="458a4-236">Wartość domyślna to jedna sekunda (1 \* NX_IP_PERIODIC_RATE)</span><span class="sxs-lookup"><span data-stu-id="458a4-236">The default value is one second (1 \* NX_IP_PERIODIC_RATE)</span></span>

- <span data-ttu-id="458a4-237">**NX_DHCP_ARP_PROBE_MIN** Określa minimalną zmianę interwału między wysłaniem sond protokołu ARP.</span><span class="sxs-lookup"><span data-stu-id="458a4-237">**NX_DHCP_ARP_PROBE_MIN** Defines the minimum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="458a4-238">Wartość jest domyślnie równa 1 sekunda.</span><span class="sxs-lookup"><span data-stu-id="458a4-238">The value is defaulted to 1 second.</span></span>

- <span data-ttu-id="458a4-239">**NX_DHCP_ARP_PROBE_MAX** Definiuje maksymalną zmianę interwału między wysłaniem sond ARP.</span><span class="sxs-lookup"><span data-stu-id="458a4-239">**NX_DHCP_ARP_PROBE_MAX** Defines the maximum variation in the interval between sending ARP probes.</span></span> <span data-ttu-id="458a4-240">Wartość jest domyślnie równa 2 sekund.</span><span class="sxs-lookup"><span data-stu-id="458a4-240">The value is defaulted to 2 seconds.</span></span>

- <span data-ttu-id="458a4-241">**NX_DHCP_ARP_PROBE_NUM** Określa liczbę sond protokołu ARP wysyłanych do określenia, czy adres IP przypisany przez serwer DHCP jest już używany.</span><span class="sxs-lookup"><span data-stu-id="458a4-241">**NX_DHCP_ARP_PROBE_NUM** Defines the number of ARP probes sent for determining if the IP address assigned by the DHCP server is already in use.</span></span> <span data-ttu-id="458a4-242">Wartość jest domyślnie równa 3 sondy.</span><span class="sxs-lookup"><span data-stu-id="458a4-242">The value is defaulted to 3 probes.</span></span>

- <span data-ttu-id="458a4-243">**NX_DHCP_RESTART_WAIT** Określa czas, przez który klient DHCP może ponownie uruchomić usługę DHCP, jeśli adres IP przypisany do klienta DHCP jest już używany.</span><span class="sxs-lookup"><span data-stu-id="458a4-243">**NX_DHCP_RESTART_WAIT** Defines the length of time the DHCP Client waits to restart DHCP if the IP address assigned to the DHCP Client is already in use.</span></span> <span data-ttu-id="458a4-244">Wartość jest domyślnie równa 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="458a4-244">The value is defaulted to 10 seconds.</span></span>

- <span data-ttu-id="458a4-245">**NX_DHCP_CLIENT_MAX_RECORDS** Określa maksymalną liczbę rekordów interfejsów do zapisania w wystąpieniu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-245">**NX_DHCP_CLIENT_MAX_RECORDS** Specifies the maximum number of interface records to save to the DHCP Client instance.</span></span> <span data-ttu-id="458a4-246">Rekord interfejsu klienta DHCP jest rekordem klienta DHCP działającego w określonym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="458a4-246">A DHCP Client interface record is a record of the DHCP Client running on a specific interface.</span></span> <span data-ttu-id="458a4-247">Wartość domyślna jest ustawiana jako liczba interfejsów fizycznych (NX_MAX_PHYSICAL_INTERFACES).</span><span class="sxs-lookup"><span data-stu-id="458a4-247">The default value is set as physical interfaces count(NX_MAX_PHYSICAL_INTERFACES).</span></span>

- <span data-ttu-id="458a4-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Zdefiniowane, dzięki temu Klient DHCP może wysyłać maksymalny rozmiar komunikatu DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-248">**NX_DHCP_CLIENT_SEND_MAX_DHCP_MESSAGE_OPTION** Defined, this enables the DHCP Client to send maximum DHCP message size option.</span></span> <span data-ttu-id="458a4-249">Domyślnie ta opcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="458a4-249">By default, this option is disabled.</span></span>

- <span data-ttu-id="458a4-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Zdefiniowane, umożliwia klientowi DHCP sprawdzenie nazwy wejściowego hosta w wywołaniu nx_dhcp_create w przypadku nieprawidłowych znaków lub długości.</span><span class="sxs-lookup"><span data-stu-id="458a4-250">**NX_DHCP_CLIENT_ENABLE_HOST_NAME_CHECK** Defined, this enables the DHCP Client to check the input host name in the nx_dhcp_create call for invalid characters or length.</span></span> <span data-ttu-id="458a4-251">Domyślnie ta opcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="458a4-251">By default, this option is disabled.</span></span>

- <span data-ttu-id="458a4-252">**NX_DHCP_THREAD_PRIORITY** Priorytet wątku DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-252">**NX_DHCP_THREAD_PRIORITY** Priority of the DHCP thread.</span></span> <span data-ttu-id="458a4-253">Domyślnie ta wartość określa, że wątek DHCP działa z priorytetem 3.</span><span class="sxs-lookup"><span data-stu-id="458a4-253">By default, this value specifies that the DHCP thread runs at priority 3.</span></span>

- <span data-ttu-id="458a4-254">**NX_DHCP_THREAD_STACK_SIZE** Rozmiar stosu wątków DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-254">**NX_DHCP_THREAD_STACK_SIZE** Size of the DHCP thread stack.</span></span> <span data-ttu-id="458a4-255">Domyślnie rozmiar to 2048 bajtów.</span><span class="sxs-lookup"><span data-stu-id="458a4-255">By default, the size is 2048 bytes.</span></span>

- <span data-ttu-id="458a4-256">**NX_DHCP_TIME_INTERVAL** Interwał (w sekundach), po którym jest wykonywana funkcja wygaśnięcia czasomierza klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-256">**NX_DHCP_TIME_INTERVAL** Interval in seconds when the DHCP Client timer expiration function executes.</span></span> <span data-ttu-id="458a4-257">Ta funkcja aktualizuje wszystkie limity czasu w procesie DHCP, np. w przypadku, gdy komunikaty powinny być ponownie przesyłane lub stan klienta DHCP uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="458a4-257">This function updates all the timeouts in the DHCP process e.g. if messages should be retransmitted or DHCP Client state changed.</span></span> <span data-ttu-id="458a4-258">Domyślnie ta wartość jest równa 1 sekunda.</span><span class="sxs-lookup"><span data-stu-id="458a4-258">By default, this value is 1 second.</span></span>

- <span data-ttu-id="458a4-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** Rozmiar buforu opcji DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-259">**NX_DHCP_OPTIONS_BUFFER_SIZE** Size of DHCP options buffer.</span></span> <span data-ttu-id="458a4-260">Wartość domyślna to 312.</span><span class="sxs-lookup"><span data-stu-id="458a4-260">By default, this value is 312.</span></span>

- <span data-ttu-id="458a4-261">**NX_DHCP_PACKET_PAYLOAD** Określa rozmiar w bajtach ładunku pakietu klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-261">**NX_DHCP_PACKET_PAYLOAD** Specifies the size in bytes of the DHCP Client packet payload.</span></span> <span data-ttu-id="458a4-262">Wartość domyślna to NX_DHCP_MINIMUM_IP_DATAGRAM + rozmiar nagłówka fizycznego.</span><span class="sxs-lookup"><span data-stu-id="458a4-262">The default value is NX_DHCP_MINIMUM_IP_DATAGRAM + physical header size.</span></span> <span data-ttu-id="458a4-263">Rozmiar nagłówka fizycznego w sieci wireline jest zwykle rozmiarem ramki sieci Ethernet.</span><span class="sxs-lookup"><span data-stu-id="458a4-263">The physical header size in a wireline network is usually the Ethernet frame size.</span></span>

- <span data-ttu-id="458a4-264">**NX_DHCP_PACKET_POOL_SIZE** Określa rozmiar puli pakietów klienta DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-264">**NX_DHCP_PACKET_POOL_SIZE** Specifies the size of the DHCP Client packet pool.</span></span> <span data-ttu-id="458a4-265">Wartość domyślna to (5 \* NX_DHCP_PACKET_PAYLOAD), która zapewni cztery pakiety Plus pomieszczenie dla obciążenia wewnętrznej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="458a4-265">The default value is (5 \*NX_DHCP_PACKET_PAYLOAD) which will provide four packets plus room for internal packet pool overhead.</span></span>

- <span data-ttu-id="458a4-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** Określa minimalną opcję oczekiwania na odebranie odpowiedzi serwera DHCP na komunikat klienta przed ponownym przesłaniem wiadomości.</span><span class="sxs-lookup"><span data-stu-id="458a4-266">**NX_DHCP_MIN_RETRANS_TIMEOUT** Specifies the minimum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="458a4-267">Wartość domyślna to RFC 2131 zalecane 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="458a4-267">The default value is the RFC 2131 recommended 4 seconds.</span></span>

- <span data-ttu-id="458a4-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** Określa maksymalną opcję oczekiwania na odebranie odpowiedzi serwera DHCP na komunikat klienta przed ponownym przesłaniem wiadomości.</span><span class="sxs-lookup"><span data-stu-id="458a4-268">**NX_DHCP_MAX_RETRANS_TIMEOUT** Specifies the maximum wait option for receiving a DHCP Server reply to client message before retransmitting the message.</span></span> <span data-ttu-id="458a4-269">Wartość domyślna to RFC 2131 zalecane 64 s.</span><span class="sxs-lookup"><span data-stu-id="458a4-269">The default value is the RFC 2131 recommended 64 seconds.</span></span>

- <span data-ttu-id="458a4-270">**NX_DHCP_MIN_RENEW_TIMEOUT** Określa minimalną opcję oczekiwania na odebranie komunikatu serwera DHCP i wysłanie żądania odnowienia po powiązaniu klienta DHCP z adresem IP.</span><span class="sxs-lookup"><span data-stu-id="458a4-270">**NX_DHCP_MIN_RENEW_TIMEOUT** Specifies minimum wait option for receiving a DHCP Server message and sending a renewal request after the DHCP Client is bound to an IP address.</span></span> <span data-ttu-id="458a4-271">Wartość domyślna to 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="458a4-271">The default value is 60 seconds.</span></span> <span data-ttu-id="458a4-272">Jednak klient DHCP używa odnawiania i ponownego powiązania czasu wygaśnięcia z komunikatów serwera DHCP przed ustawieniem minimalny limit czasu odnawiania.</span><span class="sxs-lookup"><span data-stu-id="458a4-272">However, the DHCP Client uses the Renew and Rebind expiration times from the DHCP server message before defaulting to the minimum renew timeout.</span></span>

- <span data-ttu-id="458a4-273">**NX_DHCP_TYPE_OF_SERVICE** Typ usługi wymaganej przez żądania UDP protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-273">**NX_DHCP_TYPE_OF_SERVICE** Type of service required for the DHCP UDP requests.</span></span> <span data-ttu-id="458a4-274">Domyślnie ta wartość jest definiowana jako NX_IP_NORMAL w celu wskazania normalnej usługi pakietów IP.</span><span class="sxs-lookup"><span data-stu-id="458a4-274">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>

- <span data-ttu-id="458a4-275">**NX_DHCP_FRAGMENT_OPTION** Włączono fragment dla żądań UDP protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-275">**NX_DHCP_FRAGMENT_OPTION** Fragment enable for DHCP UDP requests.</span></span> <span data-ttu-id="458a4-276">Domyślnie ta wartość jest NX_DONT_FRAGMENT, aby wyłączyć fragmentację protokołu UDP protokołu DHCP.</span><span class="sxs-lookup"><span data-stu-id="458a4-276">By default, this value is NX_DONT_FRAGMENT to disable DHCP UDP fragmenting.</span></span>

- <span data-ttu-id="458a4-277">**NX_DHCP_TIME_TO_LIVE** Określa liczbę routerów, które ten pakiet może przekazać, zanim zostanie odrzucony.</span><span class="sxs-lookup"><span data-stu-id="458a4-277">**NX_DHCP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="458a4-278">Wartość domyślna to 0x80.</span><span class="sxs-lookup"><span data-stu-id="458a4-278">The default value is set to 0x80.</span></span>

- <span data-ttu-id="458a4-279">**NX_DHCP_QUEUE_DEPTH** Określa maksymalną głębokość kolejki odbioru.</span><span class="sxs-lookup"><span data-stu-id="458a4-279">**NX_DHCP_QUEUE_DEPTH** Specifies the number of maximum depth of receive queue.</span></span> <span data-ttu-id="458a4-280">Wartość domyślna to 4.</span><span class="sxs-lookup"><span data-stu-id="458a4-280">The default value is set to 4.</span></span>
