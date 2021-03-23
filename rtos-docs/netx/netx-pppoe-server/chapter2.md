---
title: Rozdział 2 — Instalowanie i używanie serwera usługi Azure RTO NetX PPPoE
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika serwera usługi Azure RTO NetX PPPoE.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5b52164911676b68c67da01d698e41c02730e45a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821492"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-pppoe-server"></a><span data-ttu-id="a603b-103">Rozdział 2 — Instalowanie i używanie serwera usługi Azure RTO NetX PPPoE</span><span class="sxs-lookup"><span data-stu-id="a603b-103">Chapter 2 - Installation and use of Azure RTOS NetX PPPoE Server</span></span>

<span data-ttu-id="a603b-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika serwera usługi Azure RTO NetX PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX PPPoE Server component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="a603b-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="a603b-105">Product Distribution</span></span>

<span data-ttu-id="a603b-106">Serwer PPPoE dla NetX jest dostępny pod adresem [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) .</span><span class="sxs-lookup"><span data-stu-id="a603b-106">PPPoE Server for NetX is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="a603b-107">Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a603b-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="a603b-108">**nx_pppoe_server. h**: plik nagłówkowy dla serwera PPPoE dla NetX</span><span class="sxs-lookup"><span data-stu-id="a603b-108">**nx_pppoe_server.h**: Header file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="a603b-109">plik źródłowy **nx_pppoe_server. c**: c dla serwera PPPoE dla NetX</span><span class="sxs-lookup"><span data-stu-id="a603b-109">**nx_pppoe_server.c**: C Source file for PPPoE Server for NetX</span></span>
- <span data-ttu-id="a603b-110">**nx_pppoe_server.pdf**: Opis pliku PDF serwera PPPoE dla NetX</span><span class="sxs-lookup"><span data-stu-id="a603b-110">**nx_pppoe_server.pdf**: PDF description of PPPoE Server for NetX</span></span>
- <span data-ttu-id="a603b-111">**demo_netx_pppoe_server. c**: Demonstracja serwera NetX PPPoE</span><span class="sxs-lookup"><span data-stu-id="a603b-111">**demo_netx_pppoe_server.c**: NetX PPPoE Server demonstration</span></span>

## <a name="pppoe-server-installation"></a><span data-ttu-id="a603b-112">Instalacja serwera PPPoE</span><span class="sxs-lookup"><span data-stu-id="a603b-112">PPPoE Server Installation</span></span>

<span data-ttu-id="a603b-113">Aby można było używać serwera PPPoE dla NetX, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX.</span><span class="sxs-lookup"><span data-stu-id="a603b-113">In order to use PPPoE Server for NetX, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="a603b-114">Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_pppoe_server. h* i *nx_pppoe_server. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="a603b-114">For example, if NetX is installed in the directory "*\threadx\arm7\green*" then the *nx_pppoe_server.h* and *nx_pppoe_server.c* files should be copied into this directory.</span></span>

## <a name="using-pppoe-server"></a><span data-ttu-id="a603b-115">Korzystanie z serwera PPPoE</span><span class="sxs-lookup"><span data-stu-id="a603b-115">Using PPPoE Server</span></span>

<span data-ttu-id="a603b-116">Korzystanie z serwera PPPoE dla NetX jest łatwe.</span><span class="sxs-lookup"><span data-stu-id="a603b-116">Using PPPoE Server for NetX is easy.</span></span> <span data-ttu-id="a603b-117">W zasadzie kod aplikacji musi zawierać *nx_pppoe_server. h* po zawiera *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX.</span><span class="sxs-lookup"><span data-stu-id="a603b-117">Basically, the application code must include *nx_pppoe_server.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX, respectively.</span></span> <span data-ttu-id="a603b-118">Po dołączeniu *nx_pppoe_server. h* kod aplikacji może następnie wprowadzić wywołania funkcji serwera PPPoE w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a603b-118">Once *nx_pppoe_server.h* is included, the application code is then able to make the PPPoE Server function calls specified later in this guide.</span></span> <span data-ttu-id="a603b-119">Aplikacja musi również zawierać *nx_pppoe_server. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a603b-119">The application must also include *nx_pppoe_server.c* in the build process.</span></span> <span data-ttu-id="a603b-120">Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a603b-120">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="a603b-121">To wszystko, co jest wymagane do korzystania z serwera NetX PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-121">This is all that is required to use NetX PPPoE Server.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="a603b-122">Mały przykładowy system</span><span class="sxs-lookup"><span data-stu-id="a603b-122">Small Example System</span></span>

<span data-ttu-id="a603b-123">Poniżej przedstawiono przykład, który ilustruje sposób używania serwera NetX PPPoE, opisany na rysunku 1,1.</span><span class="sxs-lookup"><span data-stu-id="a603b-123">The following is an example that illustrates how to use NetX PPPoE Server is described in Figure 1.1.</span></span> <span data-ttu-id="a603b-124">W tym przykładzie serwer PPPoE zawiera plik *nx_pppoe_server. h* jest wprowadzony w wierszu 50.</span><span class="sxs-lookup"><span data-stu-id="a603b-124">In this example, the PPPoE Server include file *nx_pppoe_server.h* is brought in at line 50.</span></span> <span data-ttu-id="a603b-125">Następnie serwer PPPoE jest tworzony w lokalizacji *"thread_0_entry*" w wierszu 248.</span><span class="sxs-lookup"><span data-stu-id="a603b-125">Next, PPPoE Server is created in *"thread_0_entry*" at line 248.</span></span> <span data-ttu-id="a603b-126">Należy pamiętać, że po utworzeniu wystąpienia adresu IP należy utworzyć serwer PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-126">Note that PPPoE Server should be created after create the IP instance.</span></span> <span data-ttu-id="a603b-127">Wystąpienie adresu IP zostało utworzone i zainicjowany line165.</span><span class="sxs-lookup"><span data-stu-id="a603b-127">The IP instance is created and initialized line165.</span></span> <span data-ttu-id="a603b-128">Blok kontroli serwera PPPoE "*pppoe_server*" został zdefiniowany jako zmienna globalna w wierszu 79.</span><span class="sxs-lookup"><span data-stu-id="a603b-128">The PPPoE Server control block "*pppoe_server*" was defined as a global variable at line 79 previously.</span></span> <span data-ttu-id="a603b-129">Funkcje powiadamiania są ustawiane w wierszu 257.</span><span class="sxs-lookup"><span data-stu-id="a603b-129">The notify functions are set at line 257.</span></span> <span data-ttu-id="a603b-130">Należy pamiętać, że musi być ustawiona funkcja powiadamiania pppoe_session_data_receive.</span><span class="sxs-lookup"><span data-stu-id="a603b-130">Note that pppoe_session_data_receive notify function must be set.</span></span> <span data-ttu-id="a603b-131">Po pomyślnym utworzeniu serwera IP i PPPoE, proces serwera PPPoE, który ustanawia sesję PPPoE w wywołaniu nx_pppoe_server_enable w wierszu 272.</span><span class="sxs-lookup"><span data-stu-id="a603b-131">After successful creation of IP and PPPoE Server, the PPPoE Server process of establishing a PPPoE session at the call to nx_pppoe_server_enable at line 272.</span></span>

<span data-ttu-id="a603b-132">Ogólnie rzecz biorąc, moduł PPPoE należy używać z modułem PPP.</span><span class="sxs-lookup"><span data-stu-id="a603b-132">In general, PPPoE module should be used with PPP module.</span></span> <span data-ttu-id="a603b-133">W tym przykładzie serwer PPP zawiera plik *nx_ppp. h* jest wprowadzony w wierszu 49.</span><span class="sxs-lookup"><span data-stu-id="a603b-133">In this example, the PPP Server include file *nx_ppp.h* is brought in at line 49.</span></span> <span data-ttu-id="a603b-134">Następnie serwer PPP jest tworzony w wierszu 174.</span><span class="sxs-lookup"><span data-stu-id="a603b-134">Next, PPP Server is created at line 174.</span></span> <span data-ttu-id="a603b-135">Wiersz 182 Skonfiguruj funkcję do wysyłania pakietów PPP.</span><span class="sxs-lookup"><span data-stu-id="a603b-135">Line 182 setup the function to send PPP packet.</span></span> <span data-ttu-id="a603b-136">Wiersz 188-200 Skonfiguruj adresy IP i zdefiniuj protokół PAP.</span><span class="sxs-lookup"><span data-stu-id="a603b-136">Line 188-200 setup the IP addresses and define the pap protocol.</span></span> <span data-ttu-id="a603b-137">Wiersz 115-139 skonfiguruj nazwę użytkownika i hasło dla protokołu PAP.</span><span class="sxs-lookup"><span data-stu-id="a603b-137">Line 115-139 setup the user name and password for pap protocol.</span></span>

<span data-ttu-id="a603b-138">Po ustanowieniu sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-138">After the PPPoE session established.</span></span> <span data-ttu-id="a603b-139">Aplikacja może wywoływać nx_pppoe_server_session_get, aby uzyskać informacje o sesji (adres MAC klienta i identyfikator sesji) w wierszu 281.</span><span class="sxs-lookup"><span data-stu-id="a603b-139">The application can call nx_pppoe_server_session_get to get the session information (client MAC address and session id) at line 281.</span></span>

<span data-ttu-id="a603b-140">Gdy aplikacja nie przetwarza już ruchu PPP, aplikacja PppCloseInd lub nx_pppoe_server_session_terminate, aby zakończyć sesję PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-140">When the application no longer process PPP traffic, the application PppCloseInd or nx_pppoe_server_session_terminate to terminate the PPPoE session.</span></span>

> [!NOTE]
> <span data-ttu-id="a603b-141">W tym przykładzie serwer PPPoE pracuje z normalnym stosem IP w tym samym czasie i udostępnia jeden sterownik Ethernet.</span><span class="sxs-lookup"><span data-stu-id="a603b-141">In this example, PPPoE Server work with normal IP stack at the same time, and share one Ethernet driver.</span></span> <span data-ttu-id="a603b-142">Przekaż ten sam sterownik Ethernet dla normalnego wystąpienia adresu IP w wierszu 165 i wystąpieniu serwera PPPoE w wierszu 248.</span><span class="sxs-lookup"><span data-stu-id="a603b-142">Pass the same Ethernet driver for normal IP instance at line 165 and PPPoE Server instance at line 248.</span></span>

> [!NOTE]
> <span data-ttu-id="a603b-143">Funkcje są udostępniane przez implementację protokołu PPPoE na potrzeby wywoływania przez oprogramowanie zdefiniowane NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.</span><span class="sxs-lookup"><span data-stu-id="a603b-143">The functions are provided by the PPPoE implementation for calling by the software under defined NX_PPPoE_SERVER_SESSION_CONTROL_ENABELE.</span></span>

<span data-ttu-id="a603b-144">Jeśli jest zdefiniowany, włącza funkcję, która steruje sesją PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-144">If defined, enables the feature that controls the PPPoE session.</span></span>

<span data-ttu-id="a603b-145">Serwer PPPoE nie odpowiada automatycznie na żądanie, dopóki nie zostanie zdefiniowany interfejs API specyficzny dla wywołania aplikacji, serwer PPPoE automatycznie odpowiedzi na żądanie.</span><span class="sxs-lookup"><span data-stu-id="a603b-145">PPPoE server does not automatically response to the request until application call specific API, if not defined, PPPoE Server automatically responses to the request.</span></span> <span data-ttu-id="a603b-146">Domyślnie jest włączona w nx_pppoe_server. h.</span><span class="sxs-lookup"><span data-stu-id="a603b-146">It enables by default in nx_pppoe_server.h.</span></span>

<span data-ttu-id="a603b-147">Zwróć uwagę, że Przedefiniuj **NX_PHYSICAL_HEADER** na 24, aby zapewnić wystarczającą ilość miejsca do wypełniania nagłówka fizycznego.</span><span class="sxs-lookup"><span data-stu-id="a603b-147">Note, redefine **NX_PHYSICAL_HEADER** to 24 to ensure enough space for filling in physical header.</span></span> <span data-ttu-id="a603b-148">Nagłówek fizyczny: 14 (nagłówek Ethernet) + 6 (nagłówek PPPoE) + 2 (Nagłówek PPP) + 2 (cztery bajty aligment).</span><span class="sxs-lookup"><span data-stu-id="a603b-148">Physical header:14(Ethernet header) + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment).</span></span>

```c
/**************************************************************************/
/**************************************************************************/
/**                                                                       */
/** NetX PPPoE Server stack Component                                     */
/**                                                                       */
/** This is a small demo of the high-performance NetX PPPoE Server        */
/** stack. This demo includes IP instance, PPPoE Server and PPP Server    */
/** stack. Create one IP instance includes two interfaces to support      */
/** for normal IP stack and PPPoE Server, PPPoE Server can use the        */
/** mutex of IP instance to send PPPoE message when share one Ethernet    */
/** driver. PPPoE Server work with normal IP instance at the same time.   */
/**                                                                       */
/** Note1: Substitute your Ethernet driver instead of                     */
/** _nx_ram_network_driver before run this demo                           */
/**                                                                       */
/** Note2: Prerequisite for using PPPoE.                                  */
/** Redefine NX_PHYSICAL_HEADER to 24 to ensure enough space for filling  */
/** in physical header. Physical header:14(Ethernet header)               */
/** + 6(PPPoE header) + 2(PPP header) + 2(four-byte aligment)             */
/**                                                                       */
/**************************************************************************/
/**************************************************************************/


/*****************************************************************/
/*                            NetX Stack                         */
/*****************************************************************/

                                      /***************************/
                                      /* PPP Server              */
                                      /***************************/

                                      /***************************/
                                      /* PPPoE Server            */
                                      /***************************/
/***************************/         /***************************/
/* Normal Ethernet Type    */         /* PPPoE Ethernet Type     */
/***************************/         /***************************/
/***************************/         /***************************/
/* Interface 0             */         /* Interface 1             */
/***************************/         /***************************/

/*****************************************************************/
/*                     Ethernet Dirver                           */
/*****************************************************************/

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nx_ppp.h"
#include     "nx_pppoe_server.h"

/* Defined NX_PPP_PPPOE_ENABLE if use Express Logic's PPP, since PPP module has been modified to match PPPoE moduler under this definition. */
#ifdef NX_PPP_PPPOE_ENABLE

/*   If the driver is not initialized in other module, define */
/*   NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE to initialize the driver in PPPoE module. */
/*   In this demo, the driver has been initialized in IP module. */

#ifdef NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE

/*   NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE: If defined, enables the feature that */
/*   controls the PPPoE session. PPPoE server does not automatically response to the */
/*   request until application call specific API. */

/* Define the block size. */
#define     NX_PACKET_POOL_SIZE     ((1536 + sizeof(NX_PACKET)) * 30)
#define     DEMO_STACK_SIZE         2048
#define     PPPOE_THREAD_SIZE       2048

/* Define the ThreadX and NetX object control blocks... */
TX_THREAD           thread_0;

/* Define the packet pool and IP instance for normal IP instnace. */
NX_PACKET_POOL      pool_0;
NX_IP               ip_0;

/* Define the PPP Server instance. */
NX_PPP              ppp_server;

/* Define the PPPoE Server instance. */
NX_PPPOE_SERVER     pppoe_server;

/* Define the counters. */
CHAR                *pointer;
ULONG               error_counter;

/* Define thread prototypes. */
void     thread_0_entry(ULONG thread_input);

/***** Substitute your PPP driver entry function here *********/
extern void     _nx_ppp_driver(NX_IP_DRIVER *driver_req_ptr);

/***** Substitute your Ethernet driver entry function here *********/
extern void     _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define the callback functions. */
void     PppDiscoverReq(UINT interfaceHandle);
void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data);
void     PppCloseRsp(UINT interfaceHandle);
void     PppCloseReq(UINT interfaceHandle);
void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id);
void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data);

/* Define the porting layer function for Express Logic's PPP to simulate TTP's PPP. */
/* Functions to be provided by PPP for calling by the PPPoE Stack. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr);

/* Define main entry point. */

int main()
{

    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

UINT verify_login(CHAR *name, CHAR *password)
{

    if ((name[0] == 'm') &&
        (name[1] == 'y') &&
        (name[2] == 'n') &&
        (name[3] == 'a') &&
        (name[4] == 'm') &&
        (name[5] == 'e') &&
        (name[6] == (CHAR) 0) &&
        (password[0] == 'm') &&
        (password[1] == 'y') &&
        (password[2] == 'p') &&
        (password[3] == 'a') &&
        (password[4] == 's') &&
        (password[5] == 's') &&
        (password[6] == 'w') &&
        (password[7] == 'o') &&
        (password[8] == 'r') &&
        (password[9] == 'd') &&
        (password[10] == (CHAR) 0))
            return(NX_SUCCESS);
    else
        return(NX_PPP_ERROR);
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{

    UINT status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a packet pool for normal IP instance. */
    status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool",
                                    (1536 + sizeof(NX_PACKET)),
                                    pointer, NX_PACKET_POOL_SIZE);
                                    pointer = pointer + NX_PACKET_POOL_SIZE;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create an normal IP instance. */
    status = nx_ip_create(&ip_0, "NetX IP Instance", IP_ADDRESS(192, 168, 100, 43),
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    /* Check for error. */
    if (status)
        error_counter++;

    /* Create the PPP instance. */
    status = nx_ppp_create(&ppp_server, "PPP Instance", &ip_0, pointer, 2048, 1,
                            &pool_0, NX_NULL, NX_NULL);
    pointer = pointer + 2048;

    /* Check for PPP create error. */
    if (status)
        error_counter++;

    /* Set the PPP packet send function. */
    status = nx_ppp_packet_send_set(&ppp_server, ppp_server_packet_send);

    /* Check for PPP packet send function set error. */
    if (status)
        error_counter++;

    /* Define IP address. This PPP instance is effectively the server since it has both IP addresses. */
    status = nx_ppp_ip_address_assign(&ppp_server, IP_ADDRESS(192, 168, 10, 43),                                         IP_ADDRESS(192, 168, 10, 44));

    /* Check for PPP IP address assign error. */
    if (status)
        error_counter++;

    /* Setup PAP, this PPP instance is effectively the server since it will verify the name and password. */
    status = nx_ppp_pap_enable(&ppp_server, NX_NULL, verify_login);

    /* Check for PPP PAP enable error. */
    if (status)
        error_counter++;

    /* Attach an interface for PPP. */
    status = nx_ip_interface_attach(&ip_0, "Second Interface For PPP", 
                            IP_ADDRESS(0, 0, 0, 0), 0, nx_ppp_driver);

    /* Check for error. */
    if (status)
        error_counter++;

    /* Enable ARP and supply ARP cache memory for Normal IP Instance. */
    status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check for ARP enable errors. */
    if (status)
        error_counter++;

    /* Enable ICMP */
    status = nx_icmp_enable(&ip_0);
    if(status)
        error_counter++;

    /* Enable UDP traffic. */
    status = nx_udp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Enable TCP traffic. */
    status = nx_tcp_enable(&ip_0);
    if (status)
        error_counter++;

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
                    pointer, DEMO_STACK_SIZE,
                    4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
                    pointer = pointer + DEMO_STACK_SIZE;
}

/* Define the test threads. */

void     thread_0_entry(ULONG thread_input)
{
UINT     status;
ULONG    ip_status;

    /* Create the PPPoE instance. */
    status = nx_pppoe_server_create(&pppoe_server, (UCHAR *)"PPPoE Server", &ip_0, 0,
                    _nx_ram_network_driver, &pool_0, pointer, PPPOE_THREAD_SIZE, 4);
    pointer = pointer + PPPOE_THREAD_SIZE;
    if (status)
    {
        error_counter++;
        return;
    }

    /* Set the callback notify function. */
    status = nx_pppoe_server_callback_notify_set(&pppoe_server, PppDiscoverReq,
        PppOpenReq, PppCloseRsp, PppCloseReq, PppTransmitDataReq, PppReceiveDataRsp);

    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call function function to set the default service Name. */
        /* PppInitInd(length, aData); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

    /* Enable PPPoE Server. */
    status = nx_pppoe_server_enable(&pppoe_server);
    if (status)
    {
        error_counter++;
        return;
    }

    /* Get the PPPoE Client physical address and Session ID after establish PPPoE Session. */
    /*
        status = nx_pppoe_server_session_get(&pppoe_server, interfaceHandle, &client_mac_msw, &client_mac_lsw, &session_id);
        if (status)
            error_counter++;
    */

    /* Wait for the link to come up. */
    status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_ADDRESS_RESOLVED,
                                            &ip_status, NX_WAIT_FOREVER);
    if (status)
    {
        error_counter++;
        return;
    }

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to terminate the PPPoE Session. */
        /* PppCloseInd(interfaceHandle, causeCode); */
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */

}

void     PppDiscoverReq(UINT interfaceHandle)
{

    /* Receive the PPPoE Discovery Initiation Message. */
    
    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to define the Service Name field of the PADO packet. */
        PppDiscoverCnf(0, NX_NULL, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppOpenReq(UINT interfaceHandle, ULONG length, UCHAR *data)
{

    /* Get the notify that receive the PPPoE Discovery Request Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to accept the PPPoE session. */
        PppOpenCnf(NX_TRUE, interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseRsp(UINT interfaceHandle)
{

    /* Get the notify that receive the PPPoE Discovery Terminate Message. */

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to allow TTP's software to confirm that the handle has been freed. */
        PppCloseCnf(interfaceHandle);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppCloseReq(UINT interfaceHandle)
{

    /* Get the notify that PPPoE Discovery Terminate Message has been sent. */

}

void     PppTransmitDataReq(UINT interfaceHandle, ULONG length, UCHAR *data, UINT packet_id)
{

    NX_PACKET *packet_ptr;

    /* Get the notify that receive the PPPoE Session data. */

    /* Call PPP Server to receive the PPP data fame. */
    packet_ptr = (NX_PACKET *)(packet_id);
    nx_ppp_packet_receive(&ppp_server, packet_ptr);

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        /* Call PPPoE function to confirm that the data has been processed. */
        PppTransmitDataCnf(interfaceHandle, data, packet_id);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}

void     PppReceiveDataRsp(UINT interfaceHandle, UCHAR *data)
{

    /* Get the notify that the PPPoE Session data has been sent. */

}

/* PPP Server send function. */
void     ppp_server_packet_send(NX_PACKET *packet_ptr)
{

    /* For Express Logic's PPP test, the session should be the first session, so set interfaceHandle as 0. */
    UINT interfaceHandle = 0;

    #ifdef NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE
        while(packet_ptr)
        {

            /* Call functions to be provided by PPPoE for TTP. */
            PppReceiveDataInd(interfaceHandle, (packet_ptr -> nx_packet_append_ptr -
            packet_ptr -> nx_packet_prepend_ptr), packet_ptr -> nx_packet_prepend_ptr);

            /* Move to the next packet structure. */
            packet_ptr = packet_ptr -> nx_packet_next;
        }
    #else
        /* Directly Call PPPoE send function to send out the data through PPPoE module. */
        nx_pppoe_server_session_packet_send(&pppoe_server, interfaceHandle, packet_ptr);
    #endif /* NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE */
}
#endif /* NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE */

#endif /* NX_PPP_PPPOE_ENABLE */
```

<span data-ttu-id="a603b-149">Rysunek 1,1 przykład użycia serwera PPPoE z NetX</span><span class="sxs-lookup"><span data-stu-id="a603b-149">Figure 1.1 Example of PPPoE Server use with NetX</span></span>

## <a name="configuration-options"></a><span data-ttu-id="a603b-150">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a603b-150">Configuration Options</span></span>

<span data-ttu-id="a603b-151">Istnieje kilka opcji konfiguracji dla tworzenia serwera PPPoE dla NetX.</span><span class="sxs-lookup"><span data-stu-id="a603b-151">There are several configuration options for building PPPoE Server for NetX.</span></span> <span data-ttu-id="a603b-152">Poniższa lista zawiera szczegółowy opis:</span><span class="sxs-lookup"><span data-stu-id="a603b-152">The following list describes each in detail:</span></span>

- <span data-ttu-id="a603b-153">**NX_DISABLE_ERROR_CHECKING**: zdefiniowane, ta opcja usuwa podstawowe sprawdzanie błędów serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-153">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic PPPoE Server error checking.</span></span> <span data-ttu-id="a603b-154">Jest on zazwyczaj używany po debugowaniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a603b-154">It is typically used after the application has been debugged.</span></span>

- <span data-ttu-id="a603b-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: Jeśli jest zdefiniowany, włącza funkcję, która steruje sesją PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-155">**NX_PPPOE_SERVER_SESSION_CONTROL_ENABLE**: If defined, enables the feature that controls the PPPoE session.</span></span> <span data-ttu-id="a603b-156">Serwer PPPoE nie odpowiada automatycznie na żądanie, dopóki nie zostanie określony interfejs API wywołania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a603b-156">PPPoE server does not automatically response to the request until application call specific API.</span></span>

- <span data-ttu-id="a603b-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: Jeśli jest zdefiniowany, włącza funkcję do inicjowania sterownika Ethernet w module PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-157">**NX_PPPOE_SERVER_INITIALIZE_DRIVER_ENABLE**: If defined, enables the feature to initialize the Ethernet driver in PPPoE module.</span></span> <span data-ttu-id="a603b-158">Domyślnie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a603b-158">It disables by default.</span></span>

- <span data-ttu-id="a603b-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: opcja wycinania czasu dla wątku serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-159">**NX_PPPOE_SERVER_THREAD_TIME_SLICE**: Time-slice option for PPPoE Server thread.</span></span> <span data-ttu-id="a603b-160">Domyślnie ta wartość jest TX_NO_TIME_SLICE.</span><span class="sxs-lookup"><span data-stu-id="a603b-160">By default, this value is TX_NO_TIME_SLICE.</span></span>

- <span data-ttu-id="a603b-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: określa maksymalną liczbę równoczesnych sesji klientów.</span><span class="sxs-lookup"><span data-stu-id="a603b-161">**NX_PPPOE_SERVER_MAX_CLIENT_SESSION_NUMBER**: This defines the max number of concurrent client sessions.</span></span> <span data-ttu-id="a603b-162">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="a603b-162">By default, this value is 10.</span></span>

- <span data-ttu-id="a603b-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: określa maksymalny rozmiar uniq hosta.</span><span class="sxs-lookup"><span data-stu-id="a603b-163">**NX_PPPOE_SERVER_MAX_HOST_UNIQ_SIZE**: This defines the max size of Host-Uniq.</span></span> <span data-ttu-id="a603b-164">Wartość domyślna to 32.</span><span class="sxs-lookup"><span data-stu-id="a603b-164">By default, this value is 32.</span></span>

- <span data-ttu-id="a603b-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: określa maksymalny rozmiar identyfikatora sesji przekazywania. Wartość domyślna to 12.</span><span class="sxs-lookup"><span data-stu-id="a603b-165">**NX_PPPOE_SERVER_MAX_RELAY_SESSION_ID_SIZE**: This defines the max size of Relay-Session-Id. By default, this value is 12.</span></span>

- <span data-ttu-id="a603b-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: określa minimalny rozmiar ładunku pakietu dla serwera PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-166">**NX_PPPOE_SERVER_MIN_PACKET_PAYLOAD_SIZE**: Specifies the Minimum packet payload size for PPPoE Server.</span></span> <span data-ttu-id="a603b-167">Jeśli rozmiar ładunku pakietu jest większy niż ta wartość, można uniknąć łańcucha pakietów.</span><span class="sxs-lookup"><span data-stu-id="a603b-167">If the packet payload size is greater than this value, can avoid packet chained.</span></span> <span data-ttu-id="a603b-168">Wartość domyślna to 1520 (maksymalny rozmiar ładunku: Ethernet 1500, nagłówek Ethernet 14, CRC 2 i cztery bajty wyrównania 4).</span><span class="sxs-lookup"><span data-stu-id="a603b-168">By default, this value is 1520 (Maximum Payload Size of Ethernet 1500, Ethernet Header 14, CRC 2 and Four-byte alignment 4).</span></span>

- <span data-ttu-id="a603b-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: definiuje Potion oczekiwania (w taktach czasomierza) do alokowania pakietów lub dołączania danych do pakietów.</span><span class="sxs-lookup"><span data-stu-id="a603b-169">**NX_PPPOE_SERVER_PACKET_TIMEOUT**: This defines the wait potion(in timer ticks) for allocating packets or appending data into packets.</span></span> <span data-ttu-id="a603b-170">Domyślnie ta wartość jest **NX_IP_PERIODIC_RATE** (100 taktów).</span><span class="sxs-lookup"><span data-stu-id="a603b-170">By default, this value is **NX_IP_PERIODIC_RATE** (100 ticks).</span></span>

- <span data-ttu-id="a603b-171">**NX_PPPOE_SERVER_START_SESSION_ID**: Określa identyfikator sesji uruchamiania do przypisywania do sesji PPPoE.</span><span class="sxs-lookup"><span data-stu-id="a603b-171">**NX_PPPOE_SERVER_START_SESSION_ID**: This defines the start Session ID for assigning to the PPPoE Session.</span></span> <span data-ttu-id="a603b-172">Domyślnie ta wartość to 0X4944 (wartość ASCII dla identyfikatora).</span><span class="sxs-lookup"><span data-stu-id="a603b-172">By default, this value is 0X4944(ASCII value for ID).</span></span>