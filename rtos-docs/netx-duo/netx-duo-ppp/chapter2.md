---
title: Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo Point-to-Point Protocol (PPP)
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTO NetX Duo Point-to-Point Protocol (PPP).
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2270a2668884dbecc8368d4ee130e419afa92491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821732"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a><span data-ttu-id="5704f-103">Rozdział 2 — Instalowanie i korzystanie z platformy Azure RTO NetX Duo Point-to-Point Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="5704f-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo Point-to-Point Protocol (PPP)</span></span>

<span data-ttu-id="5704f-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika Azure RTO NetX Duo Point-to-Point Protocol (PPP).</span><span class="sxs-lookup"><span data-stu-id="5704f-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo Point-to-Point Protocol (PPP) component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="5704f-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="5704f-105">Product Distribution</span></span>

<span data-ttu-id="5704f-106">Pakiet Azure RTO NetX Duo Point-to-Point Protocol (PPP) jest dostępny pod adresem <https://github.com/azure-rtos/netxduo> .</span><span class="sxs-lookup"><span data-stu-id="5704f-106">The Azure RTOS NetX Duo Point-to-Point Protocol (PPP) package is available at <https://github.com/azure-rtos/netxduo>.</span></span> <span data-ttu-id="5704f-107">Pakiet zawiera następujące pliki:</span><span class="sxs-lookup"><span data-stu-id="5704f-107">The package includes the following files:</span></span>

- <span data-ttu-id="5704f-108">**nx_ppp. h**: plik nagłówkowy dla protokołu PPP dla NetX</span><span class="sxs-lookup"><span data-stu-id="5704f-108">**nx_ppp.h**: Header file for PPP for NetX</span></span>
- <span data-ttu-id="5704f-109">plik źródłowy **nx_ppp. c**: c dla protokołu PPP dla NetX</span><span class="sxs-lookup"><span data-stu-id="5704f-109">**nx_ppp.c**: C Source file for PPP for NetX</span></span>
- <span data-ttu-id="5704f-110">**nx_ppp.pdf**: Opis PDF dotyczący protokołu PPP dla NetX</span><span class="sxs-lookup"><span data-stu-id="5704f-110">**nx_ppp.pdf**: PDF description of PPP for NetX</span></span>
- <span data-ttu-id="5704f-111">**demo_netx_ppp. c**: NetX PPP</span><span class="sxs-lookup"><span data-stu-id="5704f-111">**demo_netx_ppp.c**: NetX PPP demonstration</span></span>

## <a name="ppp-installation"></a><span data-ttu-id="5704f-112">Instalacja protokołu PPP</span><span class="sxs-lookup"><span data-stu-id="5704f-112">PPP Installation</span></span>

<span data-ttu-id="5704f-113">Aby można było korzystać z protokołu PPP dla NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="5704f-113">In order to use PPP for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="5704f-114">Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_ppp. h* i *nx_ppp. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5704f-114">For example, if NetX is installed in the directory “*\threadx\arm7\green*” then the *nx_ppp.h* and *nx_ppp.c* files should be copied into this directory.</span></span>

## <a name="using-ppp"></a><span data-ttu-id="5704f-115">Korzystanie z protokołu PPP</span><span class="sxs-lookup"><span data-stu-id="5704f-115">Using PPP</span></span>

<span data-ttu-id="5704f-116">Korzystanie z protokołu PPP dla NetX jest proste.</span><span class="sxs-lookup"><span data-stu-id="5704f-116">Using PPP for NetX is easy.</span></span> <span data-ttu-id="5704f-117">W zasadzie kod aplikacji musi zawierać *nx_ppp. h* po zawiera *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX.</span><span class="sxs-lookup"><span data-stu-id="5704f-117">Basically, the application code must include *nx_ppp.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="5704f-118">Po dołączeniu *nx_ppp. h* kod aplikacji może następnie wykonać wywołania funkcji PPP określone w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="5704f-118">Once *nx_ppp.h* is included, the application code is then able to make the PPP function calls specified later in this guide.</span></span> <span data-ttu-id="5704f-119">Aplikacja musi również zawierać *nx_ppp. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5704f-119">The application must also include *nx_ppp.c* in the build process.</span></span> <span data-ttu-id="5704f-120">Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5704f-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="5704f-121">To wszystko, co jest wymagane do korzystania z protokołu PPP NetX.</span><span class="sxs-lookup"><span data-stu-id="5704f-121">This is all that is required to use NetX PPP.</span></span>

## <a name="using-modems"></a><span data-ttu-id="5704f-122">Korzystanie z modemów</span><span class="sxs-lookup"><span data-stu-id="5704f-122">Using Modems</span></span>

<span data-ttu-id="5704f-123">Jeśli do nawiązania połączenia z Internetem wymagany jest modem, niektóre specjalne zagadnienia są wymagane do korzystania z produktu NetX PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-123">If a modem is required for connection to the internet, some special considerations are required in order to use the NetX PPP product.</span></span> <span data-ttu-id="5704f-124">Zasadniczo przy użyciu modemu wprowadzono dodatkową logikę inicjalizacji i logikę do utraty komunikacji.</span><span class="sxs-lookup"><span data-stu-id="5704f-124">Basically, using a modem introduces additional initialization logic and logic for loss of communication.</span></span> <span data-ttu-id="5704f-125">Ponadto większość dodatkowych logiki modemów jest wykonywana poza kontekstem protokołu PPP NetX.</span><span class="sxs-lookup"><span data-stu-id="5704f-125">In addition, most of the additional modem logic is done outside the context of NetX PPP.</span></span> <span data-ttu-id="5704f-126">Podstawowy przepływ użycia protokołu PPP NetX z modemem wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="5704f-126">The basic flow of using the NetX PPP with a modem goes something like this:</span></span>

1. <span data-ttu-id="5704f-127">Zainicjuj modem</span><span class="sxs-lookup"><span data-stu-id="5704f-127">Initialize Modem</span></span>

1. <span data-ttu-id="5704f-128">Wybierz usługodawcę internetowego (ISP)</span><span class="sxs-lookup"><span data-stu-id="5704f-128">Dial Internet Service Provider (ISP)</span></span>

1. <span data-ttu-id="5704f-129">Zaczekaj na połączenie</span><span class="sxs-lookup"><span data-stu-id="5704f-129">Wait for Connection</span></span>

1. <span data-ttu-id="5704f-130">Poczekaj na monit o podanie identyfikatora użytkownika</span><span class="sxs-lookup"><span data-stu-id="5704f-130">Wait for UserID Prompt</span></span>

1. <span data-ttu-id="5704f-131">Uruchamianie NetX PPP [PPP w operacji]</span><span class="sxs-lookup"><span data-stu-id="5704f-131">Start NetX PPP [PPP in operation]</span></span>

1. <span data-ttu-id="5704f-132">Utrata komunikacji</span><span class="sxs-lookup"><span data-stu-id="5704f-132">Loss of Communication</span></span>

1. <span data-ttu-id="5704f-133">Zatrzymaj NetX PPP (lub Uruchom ponownie za pośrednictwem nx_ppp_restart)</span><span class="sxs-lookup"><span data-stu-id="5704f-133">Stop NetX PPP (or restart via nx_ppp_restart)</span></span>

### <a name="initialize-modem"></a><span data-ttu-id="5704f-134">Zainicjuj modem</span><span class="sxs-lookup"><span data-stu-id="5704f-134">Initialize Modem</span></span>

<span data-ttu-id="5704f-135">Korzystając z procedury wyjścia szeregowego niskiego poziomu aplikacji, modem jest inicjowany za pośrednictwem szeregu poleceń znaków ASCII (zobacz dokumentację modemu, aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="5704f-135">Using the application’s low-level serial output routine, the modem is initialized via a series of ASCII character commands (see modem’s documentation for more details).</span></span>

### <a name="dial-internet-service-provider"></a><span data-ttu-id="5704f-136">Wybieranie dostawcy usług internetowych</span><span class="sxs-lookup"><span data-stu-id="5704f-136">Dial Internet Service Provider</span></span>

<span data-ttu-id="5704f-137">Przy użyciu procedury wyjścia szeregowego niskiego poziomu aplikacji modem jest wybierany w celu wybrania usługodawcy internetowego.</span><span class="sxs-lookup"><span data-stu-id="5704f-137">Using the application’s low-level serial output routine, the modem is instructed to dial the ISP.</span></span> <span data-ttu-id="5704f-138">Na przykład poniżej przedstawiono typowy ciąg ASCII używany do wybierania usługodawcy internetowego o numerze 123-4567:</span><span class="sxs-lookup"><span data-stu-id="5704f-138">For example, the following is typical of an ASCII string used to dial an ISP at the number 123-4567:</span></span>

<span data-ttu-id="5704f-139">"ATDT123456\r"</span><span class="sxs-lookup"><span data-stu-id="5704f-139">“ATDT123456\r”</span></span>

### <a name="wait-for-connection"></a><span data-ttu-id="5704f-140">Zaczekaj na połączenie</span><span class="sxs-lookup"><span data-stu-id="5704f-140">Wait for Connection</span></span>

<span data-ttu-id="5704f-141">W tym momencie aplikacja czeka na otrzymanie wskazania od modemu, że połączenie zostało nawiązane.</span><span class="sxs-lookup"><span data-stu-id="5704f-141">At this point, the application waits to receive indication from the modem that a connection has been established.</span></span> <span data-ttu-id="5704f-142">Jest to osiągane przez wyszukiwanie znaków z procedury wejściowej szeregu niskiego poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5704f-142">This is accomplished by looking for characters from the application’s low-level serial input routine.</span></span> <span data-ttu-id="5704f-143">Zwykle modemy zwracają ciąg ASCII "CONNECT", gdy połączenie zostało nawiązane.</span><span class="sxs-lookup"><span data-stu-id="5704f-143">Typically, modems return an ASCII string “CONNECT” when a connection has been established.</span></span>

### <a name="wait-for-user-id-prompt"></a><span data-ttu-id="5704f-144">Zaczekaj na monit o podanie identyfikatora użytkownika</span><span class="sxs-lookup"><span data-stu-id="5704f-144">Wait for User ID Prompt</span></span>

<span data-ttu-id="5704f-145">Po nawiązaniu połączenia aplikacja musi teraz oczekiwać na początkowe żądanie logowania od usługodawcy internetowego.</span><span class="sxs-lookup"><span data-stu-id="5704f-145">Once the connection has been established, the application must now wait for an initial login request from the ISP.</span></span> <span data-ttu-id="5704f-146">Zwykle przyjmuje postać ciągu ASCII, takiego jak "login?".</span><span class="sxs-lookup"><span data-stu-id="5704f-146">This typically takes the form of an ASCII string like “Login?”</span></span>

### <a name="start-netx-ppp"></a><span data-ttu-id="5704f-147">Uruchom NetX PPP</span><span class="sxs-lookup"><span data-stu-id="5704f-147">Start NetX PPP</span></span>

<span data-ttu-id="5704f-148">W tym momencie można uruchomić NetX PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-148">At this point, the NetX PPP can be started.</span></span> <span data-ttu-id="5704f-149">Jest to realizowane przez wywołanie usługi *nx_ppp_create* , a następnie usługi *nx_ip_create* .</span><span class="sxs-lookup"><span data-stu-id="5704f-149">This is accomplished by calling the *nx_ppp_create* service followed by the *nx_ip_create* service.</span></span> <span data-ttu-id="5704f-150">Mogą być również wymagane dodatkowe usługi umożliwiające włączenie protokołu PAP i skonfigurowanie adresów IP PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-150">Additional services to enable PAP and to setup the PPP IP addresses might also be required.</span></span> <span data-ttu-id="5704f-151">Aby uzyskać więcej informacji, zapoznaj się z poniższymi sekcjami tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="5704f-151">Please review the following sections of this guide for more information.</span></span>

### <a name="loss-of-communication"></a><span data-ttu-id="5704f-152">Utrata komunikacji</span><span class="sxs-lookup"><span data-stu-id="5704f-152">Loss of Communication</span></span>

<span data-ttu-id="5704f-153">Po uruchomieniu protokołu PPP wszystkie informacje inne niż PPP są przekazywane do procedury "nieprawidłowa obsługa pakietów" aplikacji określonej dla usługi *nx_ppp_create* .</span><span class="sxs-lookup"><span data-stu-id="5704f-153">Once PPP is started, any non-PPP information is passed to the “invalid packet handling” routine the application specified to the *nx_ppp_create* service.</span></span> <span data-ttu-id="5704f-154">Zwykle modemy wysyłają ciąg ASCII, taki jak "NO CARRIER", gdy komunikacja zostanie utracona w ramach usługodawcy internetowego.</span><span class="sxs-lookup"><span data-stu-id="5704f-154">Typically, modems send an ASCII string such as “NO CARRIER” when communication is lost with the ISP.</span></span> <span data-ttu-id="5704f-155">Gdy aplikacja odbiera pakiet bez protokołu PPP z takimi informacjami, powinien kontynuować zatrzymanie wystąpienia NetX PPP lub ponowne uruchomienie komputera stanu PPP za pośrednictwem interfejsu API *nx_ppp_restart* .</span><span class="sxs-lookup"><span data-stu-id="5704f-155">When the application receives a non-PPP packet with such information, it should proceed to either stop the NetX PPP instance or to restart the PPP state machine via the *nx_ppp_restart* API.</span></span>

### <a name="stop-netx-ppp"></a><span data-ttu-id="5704f-156">Zatrzymaj NetX PPP</span><span class="sxs-lookup"><span data-stu-id="5704f-156">Stop NetX PPP</span></span>

<span data-ttu-id="5704f-157">Zatrzymywanie NetX PPP jest dość proste.</span><span class="sxs-lookup"><span data-stu-id="5704f-157">Stopping the NetX PPP is fairly straightforward.</span></span> <span data-ttu-id="5704f-158">W zasadzie wszystkie utworzone gniazda muszą być niepowiązane i usunięte.</span><span class="sxs-lookup"><span data-stu-id="5704f-158">Basically, all created sockets must be unbound and deleted.</span></span> <span data-ttu-id="5704f-159">Następnie Usuń wystąpienie protokołu IP za pośrednictwem usługi *nx_ip_delete* .</span><span class="sxs-lookup"><span data-stu-id="5704f-159">Next, delete the IP instance via the *nx_ip_delete* service.</span></span> <span data-ttu-id="5704f-160">Po usunięciu wystąpienia adresu IP należy wywołać usługę *nx_ppp_delete* , aby zakończyć proces zatrzymywania protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-160">Once the IP instance is deleted, the *nx_ppp_delete* service should be called to finish the process of stopping PPP.</span></span> <span data-ttu-id="5704f-161">W tym momencie aplikacja może teraz próbować ponownie ustanowić komunikację z usługodawcą internetowym.</span><span class="sxs-lookup"><span data-stu-id="5704f-161">At this point, the application is now able to attempt to reestablish communication with the ISP.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="5704f-162">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="5704f-162">Small Example System</span></span>

<span data-ttu-id="5704f-163">Przykład, który ilustruje, jak łatwo jest używać NetX PPP jest opisany na rysunku 1,1 poniżej.</span><span class="sxs-lookup"><span data-stu-id="5704f-163">An example that illustrates how easy it is to use NetX PPP is described in Figure 1.1 that appears below.</span></span> <span data-ttu-id="5704f-164">W tym przykładzie plik dołączany PPP *nx_ppp. h* jest wprowadzany w wierszu 3.</span><span class="sxs-lookup"><span data-stu-id="5704f-164">In this example, the PPP include file *nx_ppp.h* is brought in at line 3.</span></span> <span data-ttu-id="5704f-165">Następnie protokół PPP jest tworzony w lokalizacji *"tx_application_define*" w wierszu 56.</span><span class="sxs-lookup"><span data-stu-id="5704f-165">Next, PPP is created in *”tx_application_define*” at line 56.</span></span> <span data-ttu-id="5704f-166">Blok kontroli PPP "*my_ppp*" został wcześniej zdefiniowany jako zmienna globalna w wierszu 9.</span><span class="sxs-lookup"><span data-stu-id="5704f-166">The PPP control block “*my_ppp*” was defined as a global variable at line 9 previously.</span></span> 

>[!NOTE]
><span data-ttu-id="5704f-167">Przed utworzeniem wystąpienia adresu IP należy utworzyć protokół PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-167">PPP should be created prior to creating the IP instance.</span></span> <span data-ttu-id="5704f-168">Po pomyślnym utworzeniu protokołu PPP i IP wątek "*my_thread*" czeka na połączenie protokołu PPP z wierszem 98.</span><span class="sxs-lookup"><span data-stu-id="5704f-168">After successful creation of PPP and IP, the thread “*my_thread*” waits for the PPP link to come alive at line 98.</span></span> <span data-ttu-id="5704f-169">W wierszu 104 zarówno protokół PPP, jak i NetX są w pełni funkcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5704f-169">At line 104, both PPP and NetX are fully operational.</span></span>

<span data-ttu-id="5704f-170">Jeden z elementów niewidocznych w tym przykładzie jest bajtem szeregowym aplikacji, który odbiera ISR.</span><span class="sxs-lookup"><span data-stu-id="5704f-170">The one item not shown in this example is the application’s serial byte receive ISR.</span></span> <span data-ttu-id="5704f-171">Należy wywołać *nx_ppp_byte_receive* z "*my_ppp*" i bajt odebrany jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="5704f-171">It will need to call *nx_ppp_byte_receive* with “*my_ppp*” and the byte received as input parameters.</span></span>

```c
0001 #include   "tx_api.h"
0002 #include   "nx_api.h"
0003 #include   "nx_ppp.h"
0004
#define     DEMO_STACK_SIZE         4096
TX_THREAD               my_thread;
NX_PACKET_POOL          my_pool;
NX_IP                   my_ip;
NX_PPP                  my_ppp;

/* Define function prototypes. */

void    my_thread_entry(ULONG thread_input);
void    my_serial_driver_byte_output(UCHAR byte);
void    my_invalid_packet_handler(NX_PACKET *packet_ptr);
 
/* Define main entry point. */
intmain()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
 }


/* Define what the initial system looks like. */

void    tx_application_define(void *first_unused_memory)
{

CHAR    *pointer;
UINT    status;

/* Setup the working pointer. */
pointer =  (CHAR *) first_unused_memory;

/* Create “my_thread”. */
    tx_thread_create(&my_thread, "my thread", my_thread_entry, 0,  
                  pointer, DEMO_STACK_SIZE, 
                  2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool. */
    status =  nx_packet_pool_create(&my_pool, "NetX Main Packet Pool", 
                                    1024, pointer, 64000);
    pointer = pointer + 64000;

    /* Check for pool creation error. */
    if (status)
        error_counter++;

    /* Create a PPP instance. */
    status = nx_ppp_create(&my_ppp, “My PPP”, &my_ip, pointer, 1024, 2, 
                           &my_pool, my_invalid_packet_handler, my_serial_driver_byte_output);
    pointer =  pointer + 1024;
    /* Check for PPP creation pool. */
    if (status)
        error_counter++;

    /* Create an IP instance with the PPP driver. */
    status = nx_ip_create(&my_ip,"My NetX IP Instance", 
                           IP_ADDRESS(216,2,3,1), 0xFFFFFF00, &my_pool, 
                           nx_ppp_driver, pointer, DEMO_STACK_SIZE, 1);
    pointer =  pointer + DEMO_STACK_SIZE;

    /* Check for IP create errors. */
    if (status)
        error_counter++;

    /* Enable ICMP for my IP Instance. */
    status =  nx_icmp_enable(&my_ip);

    /* Check for ICMP enable errors. */
    if (status)
        error_counter++;

    /* Enable UDP. */
    status =  nx_udp_enable(&my_ip);
    if (status)
        error_counter++;
}

/* Define my thread. */
void    my_thread_entry(ULONG thread_input)
{

UINT        status;
ULONG       ip_status;
NX_PACKET   *my_packet;

/* Wait for the PPP link in my_ip to become enabled. */
    status =  nx_ip_status_check(&my_ip,NX_IP_LINK_ENABLED,&ip_status,3000);

    /* Check for IP status error. */
    if (status) 
        return;

    /* Link is fully up and operational. All NetX activities 
    are now available. */

}
```
## <a name="configuration-options"></a><span data-ttu-id="5704f-172">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5704f-172">Configuration Options</span></span>

<span data-ttu-id="5704f-173">Istnieje kilka opcji konfiguracji dla tworzenia protokołu PPP dla NetX.</span><span class="sxs-lookup"><span data-stu-id="5704f-173">There are several configuration options for building PPP for NetX.</span></span> <span data-ttu-id="5704f-174">Poniższa lista zawiera szczegółowy opis:</span><span class="sxs-lookup"><span data-stu-id="5704f-174">The following list describes each in detail:</span></span>

- <span data-ttu-id="5704f-175">**NX_DISABLE_ERROR_CHECKING**: zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-175">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPP error checking.</span></span> <span data-ttu-id="5704f-176">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5704f-176">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="5704f-177">**NX_PPP_PPPOE_ENABLE**: Jeśli jest zdefiniowany, protokół PPP może transmitować pakiet przez sieć Ethernet</span><span class="sxs-lookup"><span data-stu-id="5704f-177">**NX_PPP_PPPOE_ENABLE**: If defined, PPP can transmit packet over Ethernet</span></span>
- <span data-ttu-id="5704f-178">**NX_PPP_BASE_TIMEOUT**: określa współczynnik okresu (w taktach czasomierza), który zadanie wątku PPP jest wybudzany do sprawdzania zdarzeń PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-178">**NX_PPP_BASE_TIMEOUT**: This defines the period rate (in timer ticks) that the PPP thread task is woken to check for PPP events.</span></span> <span data-ttu-id="5704f-179">Wartość domyślna to 1 \* NX_IP_PERIODIC_RATE (100 Takty).</span><span class="sxs-lookup"><span data-stu-id="5704f-179">The default value is 1\*NX_IP_PERIODIC_RATE (100 ticks).</span></span>
- <span data-ttu-id="5704f-180">**NX_PPP_DISABLE_INFO**: jeśli zdefiniowane, wewnętrzne zbieranie informacji PPP jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="5704f-180">**NX_PPP_DISABLE_INFO**: If defined, internal PPP information gathering is disabled.</span></span>
- <span data-ttu-id="5704f-181">**NX_PPP_DEBUG_LOG_ENABLE**: Jeśli jest zdefiniowany, wewnętrzny Dziennik debugowania PPP jest włączony.</span><span class="sxs-lookup"><span data-stu-id="5704f-181">**NX_PPP_DEBUG_LOG_ENABLE**: If defined, internal PPP debug log is enabled.</span></span>
- <span data-ttu-id="5704f-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**: Jeśli jest zdefiniowany, wewnętrzny Dziennik debugowania PPP *printf* do *stdio* jest włączony.</span><span class="sxs-lookup"><span data-stu-id="5704f-182">**NX_PPP_DEBUG_LOG_PRINT_ENABLE**:If defined, internal PPP debug log *printf* to *stdio* is enabled.</span></span> <span data-ttu-id="5704f-183">Jest to prawidłowe tylko wtedy, gdy Dziennik debugowania jest włączony.</span><span class="sxs-lookup"><span data-stu-id="5704f-183">This is only valid if the debug log is also enabled.</span></span>
- <span data-ttu-id="5704f-184">**NX_PPP_DEBUG_LOG_SIZE**: rozmiar dziennika debugowania (liczba wpisów w dzienniku debugowania).</span><span class="sxs-lookup"><span data-stu-id="5704f-184">**NX_PPP_DEBUG_LOG_SIZE**: Size of debug log (number of entries in the debug log).</span></span> <span data-ttu-id="5704f-185">Po osiągnięciu ostatniego wpisu przechwytywanie debugowania jest zawijane do pierwszego wpisu i zastępuje wszelkie przechwycone wcześniej dane.</span><span class="sxs-lookup"><span data-stu-id="5704f-185">On reaching the last entry, the debug capture wraps to the first entry and overwrites any data previously captured.</span></span> <span data-ttu-id="5704f-186">Wartość domyślna to 50.</span><span class="sxs-lookup"><span data-stu-id="5704f-186">The default value is 50.</span></span>
- <span data-ttu-id="5704f-187">**NX_PPP_DEBUG_FRAME_SIZE**: Maksymalna ilość danych przechwyconych z odebranego ładunku pakietu i zapisanych w danych wyjściowych debugowania.</span><span class="sxs-lookup"><span data-stu-id="5704f-187">**NX_PPP_DEBUG_FRAME_SIZE**: Maximum amount of data captured from a received packet payload and saved to debug output.</span></span> <span data-ttu-id="5704f-188">Wartość domyślna to 50.</span><span class="sxs-lookup"><span data-stu-id="5704f-188">The default value is 50.</span></span>
- <span data-ttu-id="5704f-189">**NX_PPP_DISABLE_CHAP**: Jeśli jest zdefiniowana, wewnętrzna LOGIKa CHAP protokołu PPP jest usuwana, w tym LOGIKI Digest MD5.</span><span class="sxs-lookup"><span data-stu-id="5704f-189">**NX_PPP_DISABLE_CHAP**: If defined, internal PPP CHAP logic is removed, including the MD5 digest logic.</span></span>
- <span data-ttu-id="5704f-190">**NX_PPP_DISABLE_PAP**: Jeśli jest zdefiniowany, wewnętrzna logika PAP protokołu PPP jest usuwana.</span><span class="sxs-lookup"><span data-stu-id="5704f-190">**NX_PPP_DISABLE_PAP**: If defined, internal PPP PAP logic is removed.</span></span>
- <span data-ttu-id="5704f-191">**NX_PPP_DNS_OPTION_DISABLE**: w przypadku określenia opcji podstawowy serwer DNS jest wyłączona w odpowiedzi IPCP.</span><span class="sxs-lookup"><span data-stu-id="5704f-191">**NX_PPP_DNS_OPTION_DISABLE**: If defined, the primary DNS Server Option is disabled in the IPCP response.</span></span> <span data-ttu-id="5704f-192">Domyślnie ta opcja nie jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="5704f-192">By default this option is not defined.</span></span>
- <span data-ttu-id="5704f-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: określa, ile razy Host PPP będzie żądał adresu serwera DNS od elementu równorzędnego w stanie IPCP.</span><span class="sxs-lookup"><span data-stu-id="5704f-193">**NX_PPP_DNS_ADDRESS_MAX_RETRIES**: This specifies how many times the PPP host will request a DNS Server address from the peer in the IPCP state.</span></span> <span data-ttu-id="5704f-194">Nie ma to wpływu, jeśli NX_PPP_DNS_OPTION_DISABLE jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="5704f-194">This has no effect if NX_PPP_DNS_OPTION_DISABLE is defined.</span></span> <span data-ttu-id="5704f-195">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="5704f-195">The default value is 2.</span></span>
- <span data-ttu-id="5704f-196">**NX_PPP_HASHED_VALUE_SIZE**: Określa rozmiar ciągów "wartość skrótu" używany w uwierzytelnianiu CHAP.</span><span class="sxs-lookup"><span data-stu-id="5704f-196">**NX_PPP_HASHED_VALUE_SIZE**: Specifies the size of “hashed value” strings used in CHAP authentication.</span></span> <span data-ttu-id="5704f-197">Wartość domyślna to 16 bajtów, ale można ją zdefiniować ponownie przed włączeniem *nx_ppp. h.*</span><span class="sxs-lookup"><span data-stu-id="5704f-197">The default value is set to 16 bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="5704f-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: określa maksymalną liczbę ponownych prób w przypadku przekroczenia limitu czasu protokołu PPP przed wysłaniem kolejnego komunikatu żądania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5704f-198">**NX_PPP_MAX_LCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another LCP configure request message.</span></span> <span data-ttu-id="5704f-199">Po osiągnięciu tej liczby uzgadnianie PPP jest przerywane, a stan łącza nie działa.</span><span class="sxs-lookup"><span data-stu-id="5704f-199">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="5704f-200">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="5704f-200">The default value is 20.</span></span>
- <span data-ttu-id="5704f-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: określa maksymalną liczbę ponownych prób w przypadku przekroczenia limitu czasu protokołu PPP przed wysłaniem innego komunikatu żądania uwierzytelnienia PAP.</span><span class="sxs-lookup"><span data-stu-id="5704f-201">**NX_PPP_MAX_PAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another PAP authentication request message.</span></span> <span data-ttu-id="5704f-202">Po osiągnięciu tej liczby uzgadnianie PPP jest przerywane, a stan łącza nie działa.</span><span class="sxs-lookup"><span data-stu-id="5704f-202">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="5704f-203">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="5704f-203">The default value is 20.</span></span>
- <span data-ttu-id="5704f-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: określa maksymalną liczbę ponownych prób w przypadku przekroczenia limitu czasu protokołu PPP przed wysłaniem kolejnego komunikatu wyzwania protokołu CHAP.</span><span class="sxs-lookup"><span data-stu-id="5704f-204">**NX_PPP_MAX_CHAP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another CHAP challenge message.</span></span> <span data-ttu-id="5704f-205">Po osiągnięciu tej liczby uzgadnianie PPP jest przerywane, a stan łącza nie działa.</span><span class="sxs-lookup"><span data-stu-id="5704f-205">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="5704f-206">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="5704f-206">The default value is 20.</span></span>
- <span data-ttu-id="5704f-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: określa maksymalną liczbę ponownych prób w przypadku przekroczenia limitu czasu PPP przed wysłaniem kolejnego komunikatu o żądaniu konfiguracji protokołu IPCP.</span><span class="sxs-lookup"><span data-stu-id="5704f-207">**NX_PPP_MAX_IPCP_PROTOCOL_RETRIES**: This defines the max number of retries if the PPP times out before sending another IPCP configure request message.</span></span> <span data-ttu-id="5704f-208">Po osiągnięciu tej liczby uzgadnianie PPP jest przerywane, a stan łącza nie działa.</span><span class="sxs-lookup"><span data-stu-id="5704f-208">When this number is reached the PPP handshake is aborted and the link status is down.</span></span> <span data-ttu-id="5704f-209">Wartość domyślna to 20.</span><span class="sxs-lookup"><span data-stu-id="5704f-209">The default value is 20.</span></span>
- <span data-ttu-id="5704f-210">**NX_PPP_MRU**: określa maksymalną jednostkę odbierania (MRU) dla protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-210">**NX_PPP_MRU**: Specifies the Maximum Receive Unit (MRU) for PPP.</span></span> <span data-ttu-id="5704f-211">Wartość domyślna to 1 500 bajtów (wartość minimalna).</span><span class="sxs-lookup"><span data-stu-id="5704f-211">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="5704f-212">Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ppp. h*.</span><span class="sxs-lookup"><span data-stu-id="5704f-212">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="5704f-213">**NX_PPP_MINIMUM_MRU**: Określa minimalną wartość MRU odebraną w komunikacie żądania konfiguracji LCP.</span><span class="sxs-lookup"><span data-stu-id="5704f-213">**NX_PPP_MINIMUM_MRU**: Specifies the minimum MRU received in an LCP configure request message.</span></span> <span data-ttu-id="5704f-214">Wartość domyślna to 1 500 bajtów (wartość minimalna).</span><span class="sxs-lookup"><span data-stu-id="5704f-214">By default, this value is 1,500 bytes (the minimum value).</span></span> <span data-ttu-id="5704f-215">Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ppp. h*.</span><span class="sxs-lookup"><span data-stu-id="5704f-215">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="5704f-216">**NX_PPP_NAME_SIZE**: Określa rozmiar ciągów "name" używanych w uwierzytelnianiu.</span><span class="sxs-lookup"><span data-stu-id="5704f-216">**NX_PPP_NAME_SIZE**: Specifies the size of “name” strings used in authentication.</span></span> <span data-ttu-id="5704f-217">Wartość domyślna to 32bytes, ale można ją ponownie zdefiniować przed włączeniem \* nx_ppp. h.</span><span class="sxs-lookup"><span data-stu-id="5704f-217">The default value is set to 32bytes, but can be redefined prior to inclusion of \*nx_ppp.h.</span></span>
- <span data-ttu-id="5704f-218">**NX_PPP_PASSWORD_SIZE**: Określa rozmiar ciągów "Password" używanych w uwierzytelnianiu.</span><span class="sxs-lookup"><span data-stu-id="5704f-218">**NX_PPP_PASSWORD_SIZE**: Specifies the size of “password” strings used in authentication.</span></span> <span data-ttu-id="5704f-219">Wartość domyślna to 32bytes, ale można ją zdefiniować ponownie przed włączeniem *nx_ppp. h.*</span><span class="sxs-lookup"><span data-stu-id="5704f-219">The default value is set to 32bytes, but can be redefined prior to inclusion of *nx_ppp.h.*</span></span>
- <span data-ttu-id="5704f-220">**NX_PPP_PROTOCOL_TIMEOUT**: definiuje opcję oczekiwania (w sekundach), przez jaką zadanie PPP odbiera odpowiedź na komunikat żądania protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-220">**NX_PPP_PROTOCOL_TIMEOUT**: This defines the wait option (in seconds) for the PPP task to receive a response to a PPP protocol request message.</span></span> <span data-ttu-id="5704f-221">Wartość domyślna to 4 sekundy.</span><span class="sxs-lookup"><span data-stu-id="5704f-221">The default value is 4 seconds.</span></span>
- <span data-ttu-id="5704f-222">**NX_PPP_RECEIVE_TIMEOUTS**: określa, ile razy zadanie wątku PPP przekroczy czas oczekiwania na odebranie następnego znaku w strumieniu komunikatów PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-222">**NX_PPP_RECEIVE_TIMEOUTS**: This defines the number of times the PPP thread task times out waiting to receive the next character in a PPP message stream.</span></span> <span data-ttu-id="5704f-223">Następnie protokół PPP zwalnia pakiet i rozpoczyna oczekiwanie na odebranie następnego komunikatu PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-223">Thereafter, PPP releases the packet and begins waiting to receive the next PPP message.</span></span> <span data-ttu-id="5704f-224">Wartość domyślna to 4.</span><span class="sxs-lookup"><span data-stu-id="5704f-224">The default value is 4.</span></span>
- <span data-ttu-id="5704f-225">**NX_PPP_SERIAL_BUFFER_SIZE**: Określa rozmiar buforu szeregowego odbioru znaków.</span><span class="sxs-lookup"><span data-stu-id="5704f-225">**NX_PPP_SERIAL_BUFFER_SIZE**: Specifies the size of the receive character serial buffer.</span></span> <span data-ttu-id="5704f-226">Wartość domyślna to 3 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5704f-226">By default, this value is 3,000 bytes.</span></span> <span data-ttu-id="5704f-227">Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ppp. h*.</span><span class="sxs-lookup"><span data-stu-id="5704f-227">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="5704f-228">**NX_PPP_TIMEOUT**: definiuje opcję oczekiwania (w taktach czasomierza) na potrzeby przydzielania pakietów do przesyłania danych, a także do buforowania danych szeregowych PPP w pakietach w celu wysłania ich do warstwy adresów IP.</span><span class="sxs-lookup"><span data-stu-id="5704f-228">**NX_PPP_TIMEOUT**: This defines the wait option (in timer ticks) for allocating packets to transmit data as well as buffer PPP serial data into packets to send to the IP layer.</span></span> <span data-ttu-id="5704f-229">Wartość domyślna to 4 \* NX_IP_PERIODIC_RATE (400 Takty).</span><span class="sxs-lookup"><span data-stu-id="5704f-229">The default value is 4\*NX_IP_PERIODIC_RATE (400 ticks).</span></span>
- <span data-ttu-id="5704f-230">**NX_PPP_THREAD_TIME_SLICE**: opcja wycinek czasu dla wątków PPP.</span><span class="sxs-lookup"><span data-stu-id="5704f-230">**NX_PPP_THREAD_TIME_SLICE**: Time-slice option for PPP threads.</span></span> <span data-ttu-id="5704f-231">Domyślnie ta wartość jest TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="5704f-231">By default, this value is TX_NO_TIME_SLICE.</span></span> <span data-ttu-id="5704f-232">Ta definicja może być ustawiana przez aplikację przed włączeniem *nx_ppp. h*.</span><span class="sxs-lookup"><span data-stu-id="5704f-232">This define can be set by the application prior to inclusion of *nx_ppp.h*.</span></span>
- <span data-ttu-id="5704f-233">**NX_PPP_VALUE_SIZE**: Określa rozmiar ciągów "value" używanych w uwierzytelnianiu CHAP.</span><span class="sxs-lookup"><span data-stu-id="5704f-233">**NX_PPP_VALUE_SIZE**: Specifies the size of “value” strings used in CHAP authentication.</span></span> <span data-ttu-id="5704f-234">Wartość domyślna to 32bytes, ale można ją zdefiniować ponownie przed włączeniem nx_ppp. h.</span><span class="sxs-lookup"><span data-stu-id="5704f-234">The default value is set to 32bytes, but can be redefined prior to inclusion of nx_ppp.h.</span></span>