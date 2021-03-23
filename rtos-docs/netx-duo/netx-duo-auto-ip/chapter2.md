---
title: Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo AutoIP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTO NetX Duo AutoIP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 42c58a4cdec34a03eda9f42315438e5fbe2ea594
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822074"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-autoip"></a><span data-ttu-id="a49a1-103">Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo AutoIP</span><span class="sxs-lookup"><span data-stu-id="a49a1-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo AutoIP</span></span>

<span data-ttu-id="a49a1-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTO NetX Duo AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a49a1-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo AutoIP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="a49a1-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="a49a1-105">Product Distribution</span></span>

<span data-ttu-id="a49a1-106">Usługę Azure RTO NetX AutoIP można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) .</span><span class="sxs-lookup"><span data-stu-id="a49a1-106">Azure RTOS NetX AutoIP can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="a49a1-107">Pakiet zawiera trzy pliki źródłowe, jedno dołączane pliki i plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a49a1-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="a49a1-108">**nx_auto_ip. h**: plik nagłówkowy dla NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="a49a1-108">**nx_auto_ip.h**: Header file for NetX AutoIP</span></span>
- <span data-ttu-id="a49a1-109">plik źródłowy **nx_auto_ip. c**: c dla NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="a49a1-109">**nx_auto_ip.c**: C Source file for NetX AutoIP</span></span>
- <span data-ttu-id="a49a1-110">plik źródłowy **demo_netx_auto_ip. c**: c dla demonstracji NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="a49a1-110">**demo_netx_auto_ip.c**: C Source file for NetX AutoIP Demo</span></span>
- <span data-ttu-id="a49a1-111">**nx_auto_ip.pdf**: Opis pliku PDF NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="a49a1-111">**nx_auto_ip.pdf**: PDF description of NetX AutoIP</span></span>

## <a name="autoip-installation"></a><span data-ttu-id="a49a1-112">Instalacja AutoIP</span><span class="sxs-lookup"><span data-stu-id="a49a1-112">AutoIP Installation</span></span>

<span data-ttu-id="a49a1-113">Aby można było korzystać z programu NetX AutoIP, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="a49a1-113">In order to use NetX AutoIP, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="a49a1-114">Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_auto_ip. h*, *nx_auto_ip. c* i *demo_netx_auto_ip. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a49a1-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_auto_ip.h*, *nx_auto_ip.c*, and *demo_netx_auto_ip.c* files should be copied into this directory.</span></span>

## <a name="using-autoip"></a><span data-ttu-id="a49a1-115">Korzystanie z AutoIP</span><span class="sxs-lookup"><span data-stu-id="a49a1-115">Using AutoIP</span></span>

<span data-ttu-id="a49a1-116">Korzystanie z programu NetX AutoIP jest proste.</span><span class="sxs-lookup"><span data-stu-id="a49a1-116">Using NetX AutoIP is easy.</span></span> <span data-ttu-id="a49a1-117">W zasadzie kod aplikacji musi zawierać *nx_auto_ip. h* po zawiera *tx_api. h* i *nx_api. h*, aby można było użyć ThreadX i NetX.</span><span class="sxs-lookup"><span data-stu-id="a49a1-117">Basically, the application code must include *nx_auto_ip.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="a49a1-118">Po dołączeniu *nx_auto_ip. h* kod aplikacji jest następnie w stanie umożliwić wywoływanie funkcji AutoIP w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a49a1-118">Once *nx_auto_ip.h* is included, the application code is then able to make the AutoIP function calls specified later in this guide.</span></span> <span data-ttu-id="a49a1-119">Aplikacja musi również zawierać *nx_auto_ip. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a49a1-119">The application must also include *nx_auto_ip.c* in the build process.</span></span> <span data-ttu-id="a49a1-120">Te pliki muszą być kompilowane w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a49a1-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="a49a1-121">To wszystko, co jest wymagane do korzystania z NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a49a1-121">This is all that is required to use NetX AutoIP.</span></span>

> [!NOTE]
> <span data-ttu-id="a49a1-122">Ponieważ AutoIP korzysta z usług NetX ARP, należy włączyć protokół ARP z wywołaniem *nx_arp_enable* przed użyciem AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a49a1-122">Since AutoIP utilizes NetX ARP services, ARP must be enabled with the *nx_arp_enable* call prior to using AutoIP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="a49a1-123">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="a49a1-123">Small Example System</span></span>

<span data-ttu-id="a49a1-124">Przykład, jak łatwo jest używać NetX AutoIP jest opisany na rysunku 1,1, który jest widoczny poniżej.</span><span class="sxs-lookup"><span data-stu-id="a49a1-124">An example of how easy it is to use NetX AutoIP is described in Figure 1.1, which appears below.</span></span> <span data-ttu-id="a49a1-125">W tym przykładzie AutoIP dołączenia pliku *nx_auto_ip. h* jest w wierszu 002.</span><span class="sxs-lookup"><span data-stu-id="a49a1-125">In this example, the AutoIP include file *nx_auto_ip.h* is brought in at line 002.</span></span> <span data-ttu-id="a49a1-126">Następnie wystąpienie NetX AutoIP jest tworzone w lokalizacji "*tx_application_define*" w wierszu 090.</span><span class="sxs-lookup"><span data-stu-id="a49a1-126">Next, the NetX AutoIP instance is created in "*tx_application_define*" at line 090.</span></span> <span data-ttu-id="a49a1-127">Należy zauważyć, że blok sterujący NetX AutoIP "auto_ip_0" został wcześniej zdefiniowany jako zmienna globalna w wierszu 015.</span><span class="sxs-lookup"><span data-stu-id="a49a1-127">Note that the NetX AutoIP control block "auto_ip_0" was defined previously as a global variable at line 015.</span></span> <span data-ttu-id="a49a1-128">Po pomyślnym utworzeniu NetX AutoIP jest uruchamiany w wierszu 098.</span><span class="sxs-lookup"><span data-stu-id="a49a1-128">After successful creation, an NetX AutoIP is started at line 098.</span></span> <span data-ttu-id="a49a1-129">Przetwarzanie funkcji wywołania zwrotnego zmiany adresu IP zaczyna się w wierszu 105, który jest używany do obsługi kolejnych konfliktów lub rozpoznawania adresów DHCP.</span><span class="sxs-lookup"><span data-stu-id="a49a1-129">The IP address change callback function processing starts at line 105, which is used to handle subsequent conflicts or possible DHCP address resolution.</span></span>

> [!NOTE]
> <span data-ttu-id="a49a1-130">W poniższym przykładzie przyjęto założenie, że urządzenie hosta jest urządzeniem pojedynczym.</span><span class="sxs-lookup"><span data-stu-id="a49a1-130">The example below assumes the host device is a single-homed device.</span></span> <span data-ttu-id="a49a1-131">W przypadku urządzenia wieloadresowego aplikacja hosta może korzystać z *nx_auto_ip_interface_* usługi NetX AutoIP, aby określić pomocniczy interfejs sieciowy do sondowania adresu IP.</span><span class="sxs-lookup"><span data-stu-id="a49a1-131">For a multihomed device, the host application can use the NetX AutoIP service *nx_auto_ip_interface_* set to specify a secondary network interface to probe for an IP address.</span></span> <span data-ttu-id="a49a1-132">Więcej informacji na temat konfigurowania aplikacji wieloadresowych można znaleźć w [podręczniku użytkownika NetX](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) .</span><span class="sxs-lookup"><span data-stu-id="a49a1-132">See the [NetX User Guide](https://docs.microsoft.com/azure/rtos/netx/about-this-guide) for more details on setting up multihomed applications.</span></span> <span data-ttu-id="a49a1-133">Zwróć uwagę na to, że aplikacja hosta powinna używać interfejsu API NetX *nx_status_ip_interface_check* , aby zweryfikować, że AutoIP uzyskała adres IP.</span><span class="sxs-lookup"><span data-stu-id="a49a1-133">Note further that the host application should use the NetX API *nx_status_ip_interface_check* to verify AutoIP has obtained an IP address.</span></span>

```c
#include "tx_api.h"
#include "nx_api.h"
#include "nx_auto_ip.h"

#define     DEMO_STACK_SIZE     4096

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD              thread_0;
NX_PACKET_POOL         pool_0;
NX_IP                  ip_0;

/* Define the AUTO IP structures for the IP instance. */

NX_AUTO_IP             auto_ip_0;

/* Define the counters used in the demo application... */

ULONG                 thread_0_counter;
ULONG                 address_changes;
ULONG                 error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);
void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void     tx_application_define(void *first_unused_memory)
{

CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    16, 16, 1, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
                                    pointer, 4096);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Create an IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);
    pointer = pointer + 4096;

    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for IP Instance 0. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
        error_counter++;

    /* Create the AutoIP instance for IP Instance 0. */
    status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Check AutoIP create status. */
    if (status)
        error_counter++;

    /* Start AutoIP instances. */
    status = **nx_auto_ip_start**(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);

    /* Check AutoIP start status. */
    if (status)
        error_counter++;

    /* Register an IP address change function for IP Instance 0. */
    status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
                                        (void *) &auto_ip_0);

    /* Check IP address change notify status. */
    if (status)
        error_counter++;
}

/* Define the test thread. */

void     thread_0_entry(ULONG thread_input)
{

UINT     status;
ULONG    actual_status;

    /* Wait for IP address to be resolved. */
    do
    {

        /* Call IP status check routine. */
        status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
            &actual_status, 10000);

    } while (status != NX_SUCCESS);

    /* Since the IP address is resolved at this point, the application can now fully utilize NetX! */

    while(1)
    {

        /* Increment thread 0's counter. */
        thread_0_counter++;

        /* Sleep... */
        tx_thread_sleep(10);
    }
}

void          ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
{

ULONG         ip_address;
ULONG         network_mask;
NX_AUTO_IP    *auto_ip_ptr;

    /* Setup pointer to auto IP instance. */
    auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;

    /* Pickup the current IP address. */
    nx_ip_address_get(ip_ptr, &ip_address, &network_mask);

    /* Determine if the IP address has changed back to zero. If so, make sure the AutoIP instance is started. */
    if (ip_address == 0)
    {

        /* Get the last AutoIP address for this node. */
        nx_auto_ip_get_address(auto_ip_ptr, &ip_address);

        /* Start this AutoIP instance. */
        nx_auto_ip_start(auto_ip_ptr, ip_address);
        }

    /* Determine if IP address has transitioned to a non local IP address. */
    else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
    {

        /* Stop the AutoIP processing. */
        nx_auto_ip_stop(auto_ip_ptr);
    }

    /* Increment a counter. */
    address_changes++;
}
```

<span data-ttu-id="a49a1-134">Rysunek 1,1 przykład użycia AutoIP z NetX</span><span class="sxs-lookup"><span data-stu-id="a49a1-134">Figure 1.1 Example of AutoIP use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="a49a1-135">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a49a1-135">Configuration Options</span></span>

<span data-ttu-id="a49a1-136">Istnieje kilka opcji konfiguracji do kompilowania NetX AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a49a1-136">There are several configuration options for building NetX AutoIP.</span></span> <span data-ttu-id="a49a1-137">Poniżej znajduje się lista wszystkich opcji, w których szczegóły są szczegółowo opisane:</span><span class="sxs-lookup"><span data-stu-id="a49a1-137">Following is a list of all options, where each is described in detail:</span></span>

- <span data-ttu-id="a49a1-138">**NX_DISABLE_ERROR_CHECKING**: zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a49a1-138">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic AutoIP error checking.</span></span> <span data-ttu-id="a49a1-139">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a49a1-139">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="a49a1-140">**NX_AUTO_IP_PROBE_WAIT**: liczba sekund oczekiwania przed wysłaniem pierwszej sondy.</span><span class="sxs-lookup"><span data-stu-id="a49a1-140">**NX_AUTO_IP_PROBE_WAIT**: The number of seconds to wait before sending first probe.</span></span> <span data-ttu-id="a49a1-141">Domyślnie ta wartość jest definiowana jako 1.</span><span class="sxs-lookup"><span data-stu-id="a49a1-141">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="a49a1-142">**NX_AUTO_IP_PROBE_NUM**: liczba sond protokołu ARP do wysłania.</span><span class="sxs-lookup"><span data-stu-id="a49a1-142">**NX_AUTO_IP_PROBE_NUM**: The number of ARP probes to send.</span></span> <span data-ttu-id="a49a1-143">Domyślnie ta wartość jest definiowana jako 3.</span><span class="sxs-lookup"><span data-stu-id="a49a1-143">By default, this value is defined as 3.</span></span>
- <span data-ttu-id="a49a1-144">**NX_AUTO_IP_PROBE_MIN**: minimalna liczba sekund oczekiwania między wysłaniem sond.</span><span class="sxs-lookup"><span data-stu-id="a49a1-144">**NX_AUTO_IP_PROBE_MIN**: The minimum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="a49a1-145">Domyślnie ta wartość jest definiowana jako 1.</span><span class="sxs-lookup"><span data-stu-id="a49a1-145">By default, this value is defined as 1.</span></span>
- <span data-ttu-id="a49a1-146">**NX_AUTO_IP_PROBE_MAX**: Maksymalna liczba sekund oczekiwania między wysłaniem sond.</span><span class="sxs-lookup"><span data-stu-id="a49a1-146">**NX_AUTO_IP_PROBE_MAX**: The maximum number of seconds to wait between sending probes.</span></span> <span data-ttu-id="a49a1-147">Domyślnie ta wartość jest definiowana jako 2.</span><span class="sxs-lookup"><span data-stu-id="a49a1-147">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="a49a1-148">**NX_AUTO_IP_MAX_CONFLICTS**: liczba konfliktów AutoIP przed zwiększeniem opóźnień przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a49a1-148">**NX_AUTO_IP_MAX_CONFLICTS**: The number of AutoIP conflicts before increasing processing delays.</span></span> <span data-ttu-id="a49a1-149">Domyślnie ta wartość jest definiowana jako 10.</span><span class="sxs-lookup"><span data-stu-id="a49a1-149">By default, this value is defined as 10.</span></span>
- <span data-ttu-id="a49a1-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: liczba sekund określająca czas oczekiwania w przypadku przekroczenia całkowitej liczby konfliktów.</span><span class="sxs-lookup"><span data-stu-id="a49a1-150">**NX_AUTO_IP_RATE_LIMIT_INTERVAL**: The number of seconds to extend the wait period when the total number of conflicts is exceeded.</span></span> <span data-ttu-id="a49a1-151">Domyślnie ta wartość jest definiowana jako 60.</span><span class="sxs-lookup"><span data-stu-id="a49a1-151">By default, this value is defined as 60.</span></span>
- <span data-ttu-id="a49a1-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: liczba sekund oczekiwania przed wysłaniem anonsu.</span><span class="sxs-lookup"><span data-stu-id="a49a1-152">**NX_AUTO_IP_ANNOUNCE_WAIT**: The number of seconds to wait before sending announcement.</span></span> <span data-ttu-id="a49a1-153">Domyślnie ta wartość jest definiowana jako 2.</span><span class="sxs-lookup"><span data-stu-id="a49a1-153">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="a49a1-154">**NX_AUTO_IP_ANNOUNCE_NUM**: liczba ANONSÓW protokołu ARP do wysłania.</span><span class="sxs-lookup"><span data-stu-id="a49a1-154">**NX_AUTO_IP_ANNOUNCE_NUM**: The number of ARP announces to send.</span></span> <span data-ttu-id="a49a1-155">Domyślnie ta wartość jest definiowana jako 2.</span><span class="sxs-lookup"><span data-stu-id="a49a1-155">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="a49a1-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: liczba sekund oczekiwania między wysłaniem ogłaszania.</span><span class="sxs-lookup"><span data-stu-id="a49a1-156">**NX_AUTO_IP_ANNOUNCE_INTERVAL**: The number of seconds to wait between sending announces.</span></span> <span data-ttu-id="a49a1-157">Domyślnie ta wartość jest definiowana jako 2.</span><span class="sxs-lookup"><span data-stu-id="a49a1-157">By default, this value is defined as 2.</span></span>
- <span data-ttu-id="a49a1-158">**NX_AUTO_IP_DEFEND_INTERVAL**: liczba sekund oczekiwania między podwyższeniem poziomu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="a49a1-158">**NX_AUTO_IP_DEFEND_INTERVAL**: The number of seconds to wait between defense announces.</span></span> <span data-ttu-id="a49a1-159">Domyślnie ta wartość jest definiowana jako 10.</span><span class="sxs-lookup"><span data-stu-id="a49a1-159">By default, this value is defined as 10.</span></span>
