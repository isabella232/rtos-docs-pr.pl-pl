---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Duo BSD
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika systemu Azure RTO NetX Duo BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 582661bc66c51341fc098de9ff7b6fa2a7d746de
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822057"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-bsd"></a><span data-ttu-id="28eca-103">Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="28eca-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo BSD</span></span>

<span data-ttu-id="28eca-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika systemu Azure RTO NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo BSD component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="28eca-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="28eca-105">Product Distribution</span></span>

<span data-ttu-id="28eca-106">Usługę Azure RTO NetX Duo BSD można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) .</span><span class="sxs-lookup"><span data-stu-id="28eca-106">Azure RTOS NetX Duo BSD can be obtained from our public source code repository at [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/).</span></span> <span data-ttu-id="28eca-107">Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="28eca-107">The package includes two source files and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="28eca-108">**nxd_bsd. h**: plik nagłówkowy dla NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="28eca-108">**nxd_bsd.h**: Header file for NetX Duo BSD</span></span>
- <span data-ttu-id="28eca-109">plik źródłowy **nxd_bsd. c**: c dla NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="28eca-109">**nxd_bsd.c**: C Source file for NetX Duo BSD</span></span>
- <span data-ttu-id="28eca-110">**nxd_bsd.pdf**: Podręcznik użytkownika dotyczący NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="28eca-110">**nxd_bsd.pdf**: User Guide for NetX Duo BSD</span></span>

<span data-ttu-id="28eca-111">Pliki demonstracyjne:</span><span class="sxs-lookup"><span data-stu-id="28eca-111">Demo files:</span></span>

- <span data-ttu-id="28eca-112">**bsd_demo_udp. c**</span><span class="sxs-lookup"><span data-stu-id="28eca-112">**bsd_demo_udp.c**</span></span>
- <span data-ttu-id="28eca-113">**bsd_demo_tcp. c**</span><span class="sxs-lookup"><span data-stu-id="28eca-113">**bsd_demo_tcp.c**</span></span>
- <span data-ttu-id="28eca-114">**bsd_demo_raw. c**</span><span class="sxs-lookup"><span data-stu-id="28eca-114">**bsd_demo_raw.c**</span></span>

## <a name="netx-duo-bsd-installation"></a><span data-ttu-id="28eca-115">Instalacja BSD NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28eca-115">NetX Duo BSD Installation</span></span>

<span data-ttu-id="28eca-116">Aby można było użyć NetX Duo BSD, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="28eca-116">In order to use NetX Duo BSD the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="28eca-117">Na przykład jeśli NetX Duo jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nxd_bsd. h* i *nxd_bsd. c* powinny zostać skopiowane do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="28eca-117">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_bsd.h* and *nxd_bsd.c* files should be copied into this directory.</span></span>

## <a name="building-the-threadx-and-netx-duo-components-of-a-bsd-application"></a><span data-ttu-id="28eca-118">Kompilowanie składników ThreadX i NetX Duo aplikacji BSD</span><span class="sxs-lookup"><span data-stu-id="28eca-118">Building the ThreadX and NetX Duo components of a BSD Application</span></span>

### <a name="threadx"></a><span data-ttu-id="28eca-119">ThreadX</span><span class="sxs-lookup"><span data-stu-id="28eca-119">ThreadX</span></span>

<span data-ttu-id="28eca-120">Biblioteka ThreadX musi definiować `bsd_errno` w lokalnym magazynie wątków.</span><span class="sxs-lookup"><span data-stu-id="28eca-120">The ThreadX library must define `bsd_errno` in the thread local storage.</span></span> <span data-ttu-id="28eca-121">Zalecamy wykonanie następującej procedury:</span><span class="sxs-lookup"><span data-stu-id="28eca-121">We recommend the following procedure:</span></span>

1. <span data-ttu-id="28eca-122">W *tx_port. h* Ustaw jeden z TX_THREAD_EXTENSION makr w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="28eca-122">In *tx_port.h*, set one of the TX_THREAD_EXTENSION macros as follows:</span></span>
   - `#define TX_THREAD_EXTENSION_3     int bsd_errno`

1. <span data-ttu-id="28eca-123">Skompiluj ponownie bibliotekę ThreadX.</span><span class="sxs-lookup"><span data-stu-id="28eca-123">Rebuild the ThreadX library.</span></span>

> [!NOTE]
> <span data-ttu-id="28eca-124">Jeśli TX_THREAD_EXTENSION_3 jest już używany, użytkownik może korzystać z jednego z innych TX_THREAD_EXTENSION makr.</span><span class="sxs-lookup"><span data-stu-id="28eca-124">If TX_THREAD_EXTENSION_3 is already used, the user is free to use one of the other TX_THREAD_EXTENSION macros.</span></span>

### <a name="netx-duo"></a><span data-ttu-id="28eca-125">NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28eca-125">NetX Duo</span></span>

<span data-ttu-id="28eca-126">Przed rozpoczęciem korzystania z usług BSD NetX Duo należy skompilować bibliotekę NetX Duo przy użyciu zdefiniowanych NX_ENABLE_EXTENDED_NOTIFY_SUPPORT.</span><span class="sxs-lookup"><span data-stu-id="28eca-126">Before using NetX Duo BSD Services, the NetX Duo library must be built with NX_ENABLE_EXTENDED_NOTIFY_SUPPORT defined.</span></span> <span data-ttu-id="28eca-127">Domyślnie nie jest on zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="28eca-127">By default it is not defined.</span></span> <span data-ttu-id="28eca-128">Jeśli wykorzystano gniazda BSD RAW, biblioteka NetX Duo musi być skompilowana przy użyciu zdefiniowanych NX_ENABLE_IP_RAW_PACKET_FILTER.</span><span class="sxs-lookup"><span data-stu-id="28eca-128">If the BSD raw sockets are to be used, the NetX Duo library must be built with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span>

## <a name="using-netx-duo-bsd"></a><span data-ttu-id="28eca-129">Korzystanie z NetX Duo BSD</span><span class="sxs-lookup"><span data-stu-id="28eca-129">Using NetX Duo BSD</span></span>

<span data-ttu-id="28eca-130">Projekt aplikacji BSD NetX Duo musi zawierać *nxd_bsd. h* , który zawiera *tx_api. h* i *nx_api. h* , aby można było korzystać z usług BSD określonych w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="28eca-130">A NetX Duo BSD application project must include *nxd_bsd.h* after it includes *tx_api.h* and *nx_api.h* to be able to use BSD services specified later in this guide.</span></span> <span data-ttu-id="28eca-131">Aplikacja musi również zawierać *nxd_bsd. c* w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="28eca-131">The application must also include *nxd_bsd.c* in the build process.</span></span> <span data-ttu-id="28eca-132">Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28eca-132">This file must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="28eca-133">To wszystko, co jest wymagane do korzystania z NetX Duo BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-133">This is all that is required to use NetX Duo BSD.</span></span>

<span data-ttu-id="28eca-134">Aby można było korzystać z usług NetX Duo BSD, aplikacja musi utworzyć wystąpienie IP, utworzyć pulę pakietów dla warstwy BSD do przydzielania pakietów z, przydzielić miejsce na pamięć dla wewnętrznego stosu wątków BSD i określić priorytet wewnętrznego wątku BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-134">To utilize NetX Duo BSD services, the application must create an IP instance, create a packet pool for the BSD layer to allocate packets from, allocate memory space for the internal BSD thread stack, and specify the priority of the internal BSD thread.</span></span> <span data-ttu-id="28eca-135">Warstwa BSD jest inicjowana przez wywołanie *bsd_initialize* i przekazanie parametrów.</span><span class="sxs-lookup"><span data-stu-id="28eca-135">The BSD layer is initialized by calling *bsd_initialize* and passing in the parameters.</span></span> <span data-ttu-id="28eca-136">Przedstawiono to w "małych przykładach" w dalszej części tego dokumentu, ale prototyp jest przedstawiony poniżej:</span><span class="sxs-lookup"><span data-stu-id="28eca-136">This is demonstrated in the "Small Examples" later in this document but the prototype is shown below:</span></span>

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                    *CHAR *bsd_thread_stack_area,
                    *ULONG bsd_thread_stack_size,
                    *UINT bsd_thread_priority*);
```

<span data-ttu-id="28eca-137">Default_ip jest wystąpieniem IP, na którym działa warstwa BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-137">The default_ip is the IP instance the BSD layer operates on.</span></span> <span data-ttu-id="28eca-138">Default_pool jest używany przez usługi firmy BSD do przydzielania pakietów z programu.</span><span class="sxs-lookup"><span data-stu-id="28eca-138">The default_pool is used by the BSD services to allocate packets from.</span></span> <span data-ttu-id="28eca-139">Poniższe dwa parametry: bsd_thread_stack_area, bsd_thread_stack_size definiuje obszar stosu używany przez wewnętrzny wątek BSD, a ostatni parametr, bsd_thread_priority, ustawia priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="28eca-139">The next two parameters: bsd_thread_stack_area, bsd_thread_stack_size defines the stack area used by the internal BSD thread, and the last parameter, bsd_thread_priority, sets the priority of the thread.</span></span>

## <a name="netx-duo-bsd-raw-socket-support"></a><span data-ttu-id="28eca-140">Obsługa NetX Duo BSD RAW Socket</span><span class="sxs-lookup"><span data-stu-id="28eca-140">NetX Duo BSD Raw Socket Support</span></span>

<span data-ttu-id="28eca-141">NetX Duo BSD obsługuje również niesformatowane gniazda.</span><span class="sxs-lookup"><span data-stu-id="28eca-141">NetX Duo BSD also supports raw sockets.</span></span> <span data-ttu-id="28eca-142">Aby można było używać gniazd surowych w NetX Duo BSD, biblioteka NetX Duo musi być skompilowana przy użyciu zdefiniowanej NX_ENABLE_IP_RAW_PACKET_FILTER.</span><span class="sxs-lookup"><span data-stu-id="28eca-142">To use raw sockets in NetX Duo BSD, the NetX Duo library must be compiled with NX_ENABLE_IP_RAW_PACKET_FILTER defined.</span></span> <span data-ttu-id="28eca-143">Domyślnie nie jest on zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="28eca-143">By default it is not defined.</span></span> <span data-ttu-id="28eca-144">Aplikacja musi następnie włączyć przetwarzanie nieprzetworzonego gniazda dla utworzonego wcześniej wystąpienia adresu IP przez wywołanie *nx_ip_raw_packet_enable.*</span><span class="sxs-lookup"><span data-stu-id="28eca-144">The application must then enable raw socket processing for a previously created IP instance by calling *nx_ip_raw_packet_enable.*</span></span>

<span data-ttu-id="28eca-145">Aby utworzyć nieprzetworzony gniazdo w NetX Duo BSD, aplikacja używa gniazda Create Service *Socket* i określa rodzinę protokołów, typ gniazda i protokół:</span><span class="sxs-lookup"><span data-stu-id="28eca-145">To create a raw socket in NetX Duo BSD, the application uses the socket create service *socket* and specifies the protocol family, socket type and protocol:</span></span>

```c
sock_1 = socket(INT protocolFamily, INT socket_type, INT protocol)
```

<span data-ttu-id="28eca-146">protocolFamily jest AF_INET dla gniazd IPv4 lub AF_INET6 dla gniazd IPv6, przy założeniu, że w wystąpieniu IP jest włączony protokół IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-146">protocolFamily is AF_INET for IPv4 sockets, or AF_INET6 for IPv6 sockets, assuming IPv6 is enabled on the IP instance.</span></span> <span data-ttu-id="28eca-147">Socket_type musi być ustawiona na SOCK_RAW.</span><span class="sxs-lookup"><span data-stu-id="28eca-147">The socket_type must be set to SOCK_RAW.</span></span> <span data-ttu-id="28eca-148">Protokół jest specyficzny dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28eca-148">protocol is application specific.</span></span>

<span data-ttu-id="28eca-149">Aby wysyłać i odbierać pakiety pierwotne oraz zamykać niesformatowane gniazdo, aplikacja zwykle używa tych samych usług BSD jak dla protokołu UDP, np. *SendTo, recvfrom, Select* i *soc_close*.</span><span class="sxs-lookup"><span data-stu-id="28eca-149">To send and receive raw packets as well as close a raw socket, the application typically uses the same BSD services as for UDP e.g. *sendto, recvfrom, select* and *soc_close*.</span></span> <span data-ttu-id="28eca-150">Gniazda RAW nie obsługują *akceptowania* ani *nasłuchiwania* usług BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-150">Raw sockets do not support either *accept* or *listen* BSD services.</span></span>

- <span data-ttu-id="28eca-151">Domyślnie odebrane dane pierwotne IPv4 zawierają nagłówek IPv4.</span><span class="sxs-lookup"><span data-stu-id="28eca-151">By default, received IPv4 raw data includes the IPv4 header.</span></span>  <span data-ttu-id="28eca-152">Z drugiej strony odebrane dane pierwotne IPv6 nie obejmują nagłówka IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-152">Conversely, received IPv6 raw data does not include the IPv6 header.</span></span>

- <span data-ttu-id="28eca-153">Domyślnie podczas wysyłania pierwotnych pakietów IPv6 lub IPv4 warstwa otoki BSD dodaje nagłówek IPv6 lub IPv4 przed wysłaniem danych.</span><span class="sxs-lookup"><span data-stu-id="28eca-153">By default, when sending either raw IPv6 or IPv4 packets, the BSD wrapper layer adds the IPv6 or IPv4 header before sending the data.</span></span>

<span data-ttu-id="28eca-154">NetX Duo BSD obsługuje dodatkowe niesformatowane Opcje gniazda, w tym IP_RAW_RX_NO_HEADER, IP_HDRINCL i IP_RAW_IPV6_HDRINCL.</span><span class="sxs-lookup"><span data-stu-id="28eca-154">NetX Duo BSD supports additional raw socket options, including IP_RAW_RX_NO_HEADER, IP_HDRINCL and IP_RAW_IPV6_HDRINCL.</span></span>

<span data-ttu-id="28eca-155">Jeśli ustawiono IP_RAW_RX_NO_HEADER, nagłówek IPv4 zostanie usunięty, tak że odebrane dane nie zawierają nagłówka IPv4, a raportowana długość komunikatu nie zawiera nagłówka IPv4.</span><span class="sxs-lookup"><span data-stu-id="28eca-155">If IP_RAW_RX_NO_HEADER is set, the IPv4 header is removed so that the received data does not contain the IPv4 header, and the reported message length does not include the IPv4 header.</span></span>  <span data-ttu-id="28eca-156">W przypadku usługi IPv6 Sockets domyślnie nieprzetworzony dostęp do gniazda nie zawiera nagłówka IPv6, równoważne z ustawioną opcją IP_RAW_RX_NO_HEADER.</span><span class="sxs-lookup"><span data-stu-id="28eca-156">For IPv6 sockets, by default the raw socket receive does not include IPv6 header, equivalent to having the IP_RAW_RX_NO_HEADER option set.</span></span> <span data-ttu-id="28eca-157">Aplikacja może użyć usługi *SetSockOpt* do wyczyszczenia opcji IP_RAW_RX_NO_HEADER, gdy opcja IP_RAW_RX_NO_HEADER zostanie wyczyszczona, odebrane dane pierwotne IPv6 będą zawierać nagłówek IPv6, a raportowana długość komunikatu zawiera nagłówek IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-157">Application may use the *setsockopt* service to clear the IP_RAW_RX_NO_HEADER option, Once the IP_RAW_RX_NO_HEADER option is cleared, the received IPv6 raw data would include the IPv6 header, and the reported message length includes the IPv6 header.</span></span>

<span data-ttu-id="28eca-158">Ta opcja nie ma wpływu na dane przesyłane przez protokół IPv4 lub IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-158">This option has no effect on IPv4 or IPv6 transmitted data.</span></span>

<span data-ttu-id="28eca-159">Jeśli ustawiono IP_HDRINCL, aplikacja zawiera nagłówek IPv4 podczas wysyłania danych.</span><span class="sxs-lookup"><span data-stu-id="28eca-159">If IP_HDRINCL is set, the application includes the IPv4 header when sending data.</span></span>  <span data-ttu-id="28eca-160">Ta opcja nie ma wpływu na przesyłanie IPv6 i nie jest domyślnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="28eca-160">This option has no effect on IPv6 transmission and is not defined by default.</span></span> <span data-ttu-id="28eca-161">Jeśli ustawiono IP_RAW_IPV6_HDRINCL, aplikacja zawiera nagłówek IPv6 podczas wysyłania danych.</span><span class="sxs-lookup"><span data-stu-id="28eca-161">If IP_RAW_IPV6_HDRINCL is set, the application includes the IPv6 header when sending data.</span></span>  <span data-ttu-id="28eca-162">Ta opcja nie ma wpływu na transmisję IPv4 i nie jest domyślnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="28eca-162">This option has no effect on IPv4 transmission and is not defined by default.</span></span>

<span data-ttu-id="28eca-163">IP_HDRINCL i IP_RAW_IPV6_HDRINCL nie mają wpływu na odbieranie protokołu IPv4 lub IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-163">IP_HDRINCL and IP_RAW_IPV6_HDRINCL have no effect on IPv4 or IPv6 reception.</span></span>

> [!NOTE]
> <span data-ttu-id="28eca-164">Specyfikacja gniazda BSD 4,3 określa, że jądro musi skopiować pakiet pierwotny do każdego buforu odbioru gniazda.</span><span class="sxs-lookup"><span data-stu-id="28eca-164">The BSD 4.3 Socket specification specifies that the kernel must copy the raw packet to each socket receive buffer.</span></span> <span data-ttu-id="28eca-165">Jednak w NetX Duo BSD, jeśli utworzono wiele gniazd współużytkujących ten sam protokół, zachowanie jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="28eca-165">However in NetX Duo BSD, if multiple sockets are created sharing the same protocol, the behavior is undefined.</span></span>

## <a name="netx-duo-bsd-raw-packet-support"></a><span data-ttu-id="28eca-166">Obsługa pakietów NetX Duo BSD RAW</span><span class="sxs-lookup"><span data-stu-id="28eca-166">NetX Duo BSD Raw Packet Support</span></span>

<span data-ttu-id="28eca-167">Aby włączyć obsługę pakietów nieprzetworzonych dla protokołu PPPoE, NetX Duo BSD muszą zostać skompilowane z włączonym NX_BSD_RAW_PPPOE_SUPPORT.</span><span class="sxs-lookup"><span data-stu-id="28eca-167">To enable the raw packet support for PPPoE, NetX Duo BSD wrapper needs to be built with NX_BSD_RAW_PPPOE_SUPPORT enabled.</span></span>

<span data-ttu-id="28eca-168">Następujące polecenie tworzy gniazdo BSD do obsługi pierwotnych pakietów PPPoE:</span><span class="sxs-lookup"><span data-stu-id="28eca-168">The following command creates a BSD socket to handle PPPoE raw packets:</span></span>

```c
Sockfd = socket(AF_PACKET, SOCK_RAW, protocol);
```

<span data-ttu-id="28eca-169">Bieżąca implementacja BSD obsługuje tylko dwa typy protokołów w rodzinie AF_PACKET</span><span class="sxs-lookup"><span data-stu-id="28eca-169">The current BSD implementation only supports two protocol types in AF_PACKET family</span></span>

- <span data-ttu-id="28eca-170">`ETHERTYPE_PPPOE_DISC`: Pakiety odnajdywania PPPoE.</span><span class="sxs-lookup"><span data-stu-id="28eca-170">`ETHERTYPE_PPPOE_DISC`: PPPoE Discovery packets.</span></span> <span data-ttu-id="28eca-171">W ramce danych MAC pakiety odnajdywania mają typ ramki Ethernet 0x8863.</span><span class="sxs-lookup"><span data-stu-id="28eca-171">In the MAC data frame, the Discovery packets have the Ethernet frame type 0x8863.</span></span>

- <span data-ttu-id="28eca-172">`ETHERTYPE_PPPOE_SESS`: Pakiety sesji PPP.</span><span class="sxs-lookup"><span data-stu-id="28eca-172">`ETHERTYPE_PPPOE_SESS`: PPP Session packets.</span></span> <span data-ttu-id="28eca-173">W ramce danych MAC pakiety sesji mają typ ramki Ethernet 0x8864.</span><span class="sxs-lookup"><span data-stu-id="28eca-173">In the MAC data frame, the Session packets have the Ethernet frame type 0x8864.</span></span>

<span data-ttu-id="28eca-174">Struktura `sockaddr_ll` służy do określania parametrów podczas wysyłania lub otrzymywania ramek PPPoE.</span><span class="sxs-lookup"><span data-stu-id="28eca-174">The structure `sockaddr_ll` is used to specify parameters when sending or receiving PPPoE frames.</span></span>

<span data-ttu-id="28eca-175">`struct sockaddr_ll` jest zadeklarowany jako:</span><span class="sxs-lookup"><span data-stu-id="28eca-175">`struct sockaddr_ll` is declared as:</span></span>

```c
struct sockaddr_ll
{
    USHORT  sll_family;     /* Must be AF_PACKET */
    USHORT  sll_protocol;   /* LL frame type */
    INT     sll_ifindex;    /* Interface Index. */
    USHORT  sll_hatype;     /* Header type */
    UCHAR   sll_pkttype;    /* Packet type */
    UCHAR   sll_halen;      /* Length of address */
    UCHAR   sll_addr[8];    /* Physical layer address */
};
```

> [!NOTE]
> <span data-ttu-id="28eca-176">Nie każde pole w strukturze jest używane przez `sendto()` lub `recvfrom()` .</span><span class="sxs-lookup"><span data-stu-id="28eca-176">Not every field in the structure is used by `sendto()` or `recvfrom()`.</span></span> <span data-ttu-id="28eca-177">Zapoznaj się z opisem poniżej, jak skonfigurować na `sockaddr_ll` potrzeby wysyłania i otrzymywania pakietów PPPoE.</span><span class="sxs-lookup"><span data-stu-id="28eca-177">See the description below on how to set up the `sockaddr_ll` for sending and receiving PPPoE packets.</span></span>

<span data-ttu-id="28eca-178">Gniazda utworzonego w ramach rodziny AF_PACKET mogą być używane do wysyłania pakietów odnajdywania PPPoE lub pakietów sesji PPP, niezależnie od określonego protokołu.</span><span class="sxs-lookup"><span data-stu-id="28eca-178">Socket created in the AF_PACKET family can be used to send either PPPoE Discovery packets or PPP session packets, regardless of the protocol specified.</span></span> <span data-ttu-id="28eca-179">Podczas przesyłania pakietu PPPoE aplikacja musi przygotować bufor zawierający prawidłowo sformatowaną ramkę PPPoE, w tym nagłówki MAC (docelowy adres MAC, źródłowy adres MAC i typ ramki). Rozmiar buforu zawiera 14-bajtowy nagłówek Ethernet.</span><span class="sxs-lookup"><span data-stu-id="28eca-179">When transmitting a PPPoE packet, application must prepare the buffer that includes properly formatted PPPoE frame, including the MAC headers (Destination MAC address, source MAC address, and frame type.) The size of the buffer includes the 14-byte Ethernet header.</span></span>

<span data-ttu-id="28eca-180">`sockaddr_ll`Struktura `sll_ifindex` jest używana do wskazania interfejsu fizycznego, który ma być używany do wysyłania tego pakietu.</span><span class="sxs-lookup"><span data-stu-id="28eca-180">The `sockaddr_ll` struct, the `sll_ifindex` is used to indicate the physical interface to be used for sending this packet.</span></span> <span data-ttu-id="28eca-181">Pozostałe pola w strukturze nie są używane.</span><span class="sxs-lookup"><span data-stu-id="28eca-181">The rest of the fields in the structure are not used.</span></span> <span data-ttu-id="28eca-182">Wartości ustawione na nieużywane pola są ignorowane przez proces wewnętrzny BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-182">Values set to the unused fields are ignored by the BSD internal process.</span></span>

<span data-ttu-id="28eca-183">Poniższy blok kodu ilustruje, jak przesłać pakiet PPPoE:</span><span class="sxs-lookup"><span data-stu-id="28eca-183">The following code block illustrates how to transmit a PPPoE packet:</span></span>

```c
struct sockaddr_ll peer_addr;

/* Transmit a PPPoE frame using the primary network interface. */
peer_addr.sll_ifindex = 0;
n = sendto(sockfd, frame, frame_size, 0, (struct
        sockaddr*)&peer_addr, sizeof(peer_addr));
```

<span data-ttu-id="28eca-184">Wartość zwracana wskazuje liczbę przesłanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="28eca-184">The return value indicates the number of bytes transmitted.</span></span> <span data-ttu-id="28eca-185">Ponieważ pakiety PPPoE są oparte na komunikatach, w przypadku pomyślnej transmisji liczba wysłanych bajtów jest zgodna z rozmiarem pakietu, łącznie z 14-bajtowym nagłówkiem Ethernet.</span><span class="sxs-lookup"><span data-stu-id="28eca-185">Since PPPoE packets are message-based, on a successful transmission, the number of bytes sent matches the size of the packet, including the 14-byte Ethernet header.</span></span>

<span data-ttu-id="28eca-186">Pakiety PPPoE można odbierać przy użyciu polecenia `recvfrom()` .</span><span class="sxs-lookup"><span data-stu-id="28eca-186">PPPoE packets can be received using `recvfrom()`.</span></span> <span data-ttu-id="28eca-187">Bufor odbioru musi być wystarczająco duży, aby pomieścić komunikat o rozmiarze MTU sieci Ethernet.</span><span class="sxs-lookup"><span data-stu-id="28eca-187">The receive buffer must be big enough to accommodate message of Ethernet MTU size.</span></span> <span data-ttu-id="28eca-188">Odebrany pakiet PPPoE zawiera 14-bajtowy nagłówek Ethernet.</span><span class="sxs-lookup"><span data-stu-id="28eca-188">The received PPPoE packet includes 14-byte Ethernet header.</span></span> <span data-ttu-id="28eca-189">W przypadku odbierania pakietów PPPoE pakiety odnajdywania PPPoE mogą być odbierane tylko przez gniazdo utworzone za pomocą protokołu `ETHERTYPE_PPPOE_DISC` .</span><span class="sxs-lookup"><span data-stu-id="28eca-189">On receiving PPPoE packets, PPPoE Discovery packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_DISC`.</span></span> <span data-ttu-id="28eca-190">Podobnie pakiety sesji PPP mogą być odbierane tylko przez gniazdo utworzone za pomocą protokołu `ETHERTYPE_PPPOE_SESS` .</span><span class="sxs-lookup"><span data-stu-id="28eca-190">Similarly, PPP session packets can only be received by socket created with protocol `ETHERTYPE_PPPOE_SESS`.</span></span> <span data-ttu-id="28eca-191">Jeśli dla tego samego typu protokołu utworzono wiele gniazd, przychodzące pakiety PPPoE są przekazywane do gniazda utworzonego jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="28eca-191">If multiple sockets are created for the same protocol type, arriving PPPoE packets are forwarded to the socket created first.</span></span> <span data-ttu-id="28eca-192">Jeśli pierwsze gniazdo utworzone dla protokołu jest zamknięte, do otrzymywania tych pakietów jest używane następne gniazdo w kolejności tworzenia.</span><span class="sxs-lookup"><span data-stu-id="28eca-192">If the first socket created for the protocol is closed, the next socket in the order of creation is used for receiving these packets.</span></span>

<span data-ttu-id="28eca-193">Po odebraniu pakietu PPPoE następujące pola w `sockaddr_ll` strukturze są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="28eca-193">After a PPPoE packet is received, the following fields in the `sockaddr_ll` struct are valid:</span></span>
- <span data-ttu-id="28eca-194">**sll_family**: Ustaw przez wewnętrzną wartość właściwości BSD do AF_PACKET</span><span class="sxs-lookup"><span data-stu-id="28eca-194">**sll_family**: Set by the BSD internal to be AF_PACKET</span></span>
- <span data-ttu-id="28eca-195">**sll_ifindex**: wskazuje interfejs, z którego został odebrany pakiet</span><span class="sxs-lookup"><span data-stu-id="28eca-195">**sll_ifindex**: Indicates the interface from which the packet is received</span></span>
- <span data-ttu-id="28eca-196">**sll_protocol**: Ustaw typ odebranego pakietu: `ETHERTYPE_PPPOE_DISC` lub `ETHERTYPE_PPPOE_SESS`</span><span class="sxs-lookup"><span data-stu-id="28eca-196">**sll_protocol**: Set to the type of packet received: `ETHERTYPE_PPPOE_DISC` or `ETHERTYPE_PPPOE_SESS`</span></span>

## <a name="eliminating-internal-bsd-thread"></a><span data-ttu-id="28eca-197">Eliminowanie wewnętrznego wątku BSD</span><span class="sxs-lookup"><span data-stu-id="28eca-197">Eliminating Internal BSD Thread</span></span>

<span data-ttu-id="28eca-198">Domyślnie firma BSD używa wewnętrznego wątku do wykonywania niektórych operacji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="28eca-198">By default, BSD utilizes an internal thread to perform some of its processing.</span></span> <span data-ttu-id="28eca-199">W systemach z ograniczeniami pamięci, BSD można skompilować przy użyciu zdefiniowanych NX_BSD_TIMEOUT_PROCESS_IN_TIMER, co eliminuje wewnętrzny wątek BSD, a zamiast tego używa wewnętrznego czasomierza do przeprowadzenia tego samego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="28eca-199">In systems with tight memory constraints, BSD can be built with NX_BSD_TIMEOUT_PROCESS_IN_TIMER defined, which eliminates the internal BSD thread and instead uses an internal timer to perform the same processing.</span></span> <span data-ttu-id="28eca-200">Eliminuje to pamięć wymaganą dla wewnętrznego bloku sterowania i stosu kontrolki wątku BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-200">This eliminates the memory required for the internal BSD thread control block and stack.</span></span> <span data-ttu-id="28eca-201">Jednak znacznie zwiększono przetwarzanie czasomierza, a przetwarzanie BSD może być wykonywane z wyższym priorytetem niż trzeba.</span><span class="sxs-lookup"><span data-stu-id="28eca-201">However, overall timer processing is significantly increased and the BSD processing may also execute at a higher priority than needed.</span></span>

<span data-ttu-id="28eca-202">Aby skonfigurować gniazda BSD do uruchamiania w kontekście czasomierza ThreadX, zdefiniuj NX_BSD_TIMEOUT_PROCESS_IN_TIMER w *nxd_bsd. h*.</span><span class="sxs-lookup"><span data-stu-id="28eca-202">To configure BSD sockets to run in the ThreadX timer context, define NX_BSD_TIMEOUT_PROCESS_IN_TIMER in *nxd_bsd.h*.</span></span> <span data-ttu-id="28eca-203">Jeśli warstwa BSD jest skonfigurowana do wykonywania zadań BSD w kontekście czasomierza, w wywołaniu *bsd_initialize*, następujące trzy parametry są ignorowane i powinny mieć wartość null:</span><span class="sxs-lookup"><span data-stu-id="28eca-203">If the BSD layer is configured to execute the BSD tasks in the timer context, in the call to *bsd_initialize*, the following three parameters are ignored, and should be set to NULL:</span></span>

- <span data-ttu-id="28eca-204">**bsd_thread_stack_area**</span><span class="sxs-lookup"><span data-stu-id="28eca-204">**bsd_thread_stack_area**</span></span>
- <span data-ttu-id="28eca-205">**bsd_thread_stack_size**</span><span class="sxs-lookup"><span data-stu-id="28eca-205">**bsd_thread_stack_size**</span></span>
- <span data-ttu-id="28eca-206">**bsd_thread_priority**</span><span class="sxs-lookup"><span data-stu-id="28eca-206">**bsd_thread_priority**</span></span>

## <a name="netx-duo-bsd-with-dns-support"></a><span data-ttu-id="28eca-207">NetX Duo BSD z obsługą systemu DNS</span><span class="sxs-lookup"><span data-stu-id="28eca-207">NetX Duo BSD with DNS Support</span></span>

<span data-ttu-id="28eca-208">Jeśli NX_BSD_ENABLE_DNS jest zdefiniowany, NetX Duo BSD może wysyłać zapytania DNS w celu uzyskania informacji o nazwie hosta lub adresie IP hosta.</span><span class="sxs-lookup"><span data-stu-id="28eca-208">If NX_BSD_ENABLE_DNS is defined, NetX Duo BSD can send DNS queries to obtain hostname or host IP information.</span></span> <span data-ttu-id="28eca-209">Ta funkcja wymaga, aby klient NetX DNS był wcześniej tworzony przy użyciu usługi *nx_dns_create* .</span><span class="sxs-lookup"><span data-stu-id="28eca-209">This feature requires a NetX DNS Client to be previously created using the *nx_dns_create* service.</span></span> <span data-ttu-id="28eca-210">Co najmniej jeden znany adres IP serwera DNS musi być zarejestrowany w wystąpieniu usługi DNS przy użyciu usługi *nx_dns_server_add* do dodawania adresów serwera IPv4 lub przy użyciu usługi *nxd_dns_server_add* do dodawania adresów IPv4 lub IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-210">One or more known DNS server IP addresses must be registered with the DNS instance using the *nx_dns_server_add* service for adding IPv4 server addresses, or using the *nxd_dns_server_add* service for adding either IPv4 or IPv6 server addresses.</span></span>

<span data-ttu-id="28eca-211">Usługi systemu DNS i alokacja pamięci są używane przez usługi *Getaddrinfo* i *getnameinfo* :</span><span class="sxs-lookup"><span data-stu-id="28eca-211">DNS services and memory allocation are used by *getaddrinfo* and *getnameinfo* services:</span></span>

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
        const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
        char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

<span data-ttu-id="28eca-212">Gdy aplikacja BSD wywołuje *Getaddrinfo* z nazwą hosta, NetX BSD wywoła następujące usługi, aby uzyskać adres IP:</span><span class="sxs-lookup"><span data-stu-id="28eca-212">When the BSD application calls *getaddrinfo* with a hostname, NetX BSD will call any of the below services to obtain the IP address:</span></span>

- <span data-ttu-id="28eca-213">**nx_dns_ipv4_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="28eca-213">**nx_dns_ipv4_address_by_name_get**</span></span>
- <span data-ttu-id="28eca-214">**nxd_dns_ipv6_address_by_name_get**</span><span class="sxs-lookup"><span data-stu-id="28eca-214">**nxd_dns_ipv6_address_by_name_get**</span></span>
- <span data-ttu-id="28eca-215">**nx_dns_cname_get**</span><span class="sxs-lookup"><span data-stu-id="28eca-215">**nx_dns_cname_get**</span></span>

<span data-ttu-id="28eca-216">W przypadku *nx_dns_ipv4_address_by_name_get* i *NXD_DNS_IPV6_ADDRESS_BY_NAME_GET*, NetX BSD używa odpowiednio ipv4_addr_buffer i ipv6_addr_buffer obszarów pamięci.</span><span class="sxs-lookup"><span data-stu-id="28eca-216">For *nx_dns_ipv4_address_by_name_get* and *nxd_dns_ipv6_address_by_name_get*, NetX BSD uses the ipv4_addr_buffer and ipv6_addr_buffer memory areas respectively.</span></span> <span data-ttu-id="28eca-217">Rozmiar tych buforów jest definiowany odpowiednio przez (NX_BSD_IPV4_ADDR_PER_HOST \* 4) i (NX_BSD_IPV6_ADDR_PER_HOST \* 16).</span><span class="sxs-lookup"><span data-stu-id="28eca-217">The size of these buffers are defined by (NX_BSD_IPV4_ADDR_PER_HOST \* 4) and (NX_BSD_IPV6_ADDR_PER_HOST \* 16) respectively.</span></span>

<span data-ttu-id="28eca-218">W przypadku zwracania informacji o adresie z *Getaddrinfo*, NetX BSD używa tabeli pamięci blokowej ThreadX nx_bsd_addrinfo_pool_memory, której obszar pamięci jest zdefiniowany przez inny zestaw konfigurowalnych opcji, NX_BSD_IPV4_ADDR_MAX_NUM i NX_BSD_IPV6_ADDR_MAX_NUM.</span><span class="sxs-lookup"><span data-stu-id="28eca-218">For returning address information from *getaddrinfo*, NetX BSD uses the ThreadX block memory table nx_bsd_addrinfo_pool_memory, whose memory area is defined by another set of configurable options, NX_BSD_IPV4_ADDR_MAX_NUM and NX_BSD_IPV6_ADDR_MAX_NUM.</span></span>

<span data-ttu-id="28eca-219">Aby uzyskać szczegółowe informacje na temat powyższych opcji konfiguracji, zobacz **Ogólne opcje konfiguracji** .</span><span class="sxs-lookup"><span data-stu-id="28eca-219">See **General Configuration Options** for more details on the above configuration options.</span></span>

<span data-ttu-id="28eca-220">Ponadto jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES jest zdefiniowana, a dane wejściowe hosta są nazwą kanoniczną, NetX Duo BSD przydzieli pamięć dynamicznie z wcześniej utworzonej puli blokowej "_nx_bsd_cname_block_pool</span><span class="sxs-lookup"><span data-stu-id="28eca-220">Additionally, if NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, and the host input is a canonical name, NetX Duo BSD will allocate memory dynamically from a previously created block pool \`_nx_bsd_cname_block_pool</span></span>

> [!NOTE]
> <span data-ttu-id="28eca-221">Po wywołaniu *Getaddrinfo* aplikacja BSD jest odpowiedzialna za zwolnienie pamięci wskazywanej przez argument res z powrotem do tabeli blokowej przy użyciu usługi *freeaddrinfo* .</span><span class="sxs-lookup"><span data-stu-id="28eca-221">After calling *getaddrinfo* the BSD application is responsible for releasing the memory pointed to by the res argument back to the block table using the *freeaddrinfo* service.</span></span>

## <a name="netx-duo-bsd-limitations"></a><span data-ttu-id="28eca-222">Ograniczenia BSD NetX Duo</span><span class="sxs-lookup"><span data-stu-id="28eca-222">NetX Duo BSD Limitations</span></span>

<span data-ttu-id="28eca-223">Ze względu na problemy z wydajnością i architekturą NetX Duo BSD nie obsługuje wszystkich funkcji gniazda BSD 4,3:</span><span class="sxs-lookup"><span data-stu-id="28eca-223">Due to performance and architecture issues, NetX Duo BSD does not support all the BSD 4.3 socket features:</span></span>

<span data-ttu-id="28eca-224">Flagi INT nie są obsługiwane dla wywołań *send, recv, SendTo* i *recvfrom* .</span><span class="sxs-lookup"><span data-stu-id="28eca-224">INT flags are not supported for *send, recv, sendto* and *recvfrom* calls.</span></span>

## <a name="general-configuration-options"></a><span data-ttu-id="28eca-225">Ogólne opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="28eca-225">General Configuration Options</span></span>

<span data-ttu-id="28eca-226">Opcje konfigurowalne przez użytkownika w *nxd_bsd. h* pozwalają aplikacji dostroić NetX Duo dla określonych wymagań aplikacji.</span><span class="sxs-lookup"><span data-stu-id="28eca-226">User configurable options in *nxd_bsd.h* allow the application to fine tune NetX Duo BSD sockets for its particular application requirements.</span></span>

<span data-ttu-id="28eca-227">Poniżej znajduje się lista konfigurowalnych opcji ustawionych w czasie kompilacji:</span><span class="sxs-lookup"><span data-stu-id="28eca-227">The following is the list of configurable options that are set at compile time:</span></span>

- <span data-ttu-id="28eca-228">**NX_BSD_TCP_WINDOW**: używany w wywołaniach tworzenia gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="28eca-228">**NX_BSD_TCP_WINDOW**: Used in TCP socket create calls.</span></span> <span data-ttu-id="28eca-229">64 KB to typowy rozmiar okna dla sieci Ethernet 100 MB.</span><span class="sxs-lookup"><span data-stu-id="28eca-229">64k is typical window size for 100Mb Ethernet.</span></span> <span data-ttu-id="28eca-230">Wartość domyślna to 65535.</span><span class="sxs-lookup"><span data-stu-id="28eca-230">The default value is 65535.</span></span>

- <span data-ttu-id="28eca-231">**NX_BSD_SOCKFD_START**: jest to logiczny indeks dla wartości początkowej deskryptora pliku gniazda BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-231">**NX_BSD_SOCKFD_START**: This is the logical index for the BSD socket file descriptor start value.</span></span> <span data-ttu-id="28eca-232">Domyślnie ta opcja to 32.</span><span class="sxs-lookup"><span data-stu-id="28eca-232">By default this option is 32.</span></span>

- <span data-ttu-id="28eca-233">**NX_BSD_MAX_SOCKETS**: określa maksymalną liczbę gniazd dostępnych w warstwie BSD i musi być wielokrotnością 32.</span><span class="sxs-lookup"><span data-stu-id="28eca-233">**NX_BSD_MAX_SOCKETS**: Specifies the maximum number of total sockets available in the BSD layer and must be a multiple of 32.</span></span> <span data-ttu-id="28eca-234">Wartość domyślna to 32.</span><span class="sxs-lookup"><span data-stu-id="28eca-234">The value is defaulted to 32.</span></span>

- <span data-ttu-id="28eca-235">**NX_BSD_SOCKET_QUEUE_MAX**: określa maksymalną liczbę pakietów UDP przechowywanych w kolejce odbierania.</span><span class="sxs-lookup"><span data-stu-id="28eca-235">**NX_BSD_SOCKET_QUEUE_MAX**: Specifies the maximum number of UDP packets stored on the receive socket queue.</span></span> <span data-ttu-id="28eca-236">Wartość jest domyślnie równa 5.</span><span class="sxs-lookup"><span data-stu-id="28eca-236">The value is defaulted to 5.</span></span>

- <span data-ttu-id="28eca-237">**NX_BSD_MAX_LISTEN_BACKLOG**: Określa rozmiar kolejki nasłuchu ("zaległości") dla gniazd TCP BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-237">**NX_BSD_MAX_LISTEN_BACKLOG**: This specifies the size of the listen queue ('backlog') for BSD TCP sockets.</span></span> <span data-ttu-id="28eca-238">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="28eca-238">The default value is 5.</span></span>

- <span data-ttu-id="28eca-239">**NX_MICROSECOND_PER_CPU_TICK**: określa liczbę mikrosekund na cykl czasomierza harmonogramu.</span><span class="sxs-lookup"><span data-stu-id="28eca-239">**NX_MICROSECOND_PER_CPU_TICK**: Specifies the number of microseconds per scheduler timer tick.</span></span>

- <span data-ttu-id="28eca-240">**NX_BSD_TIMEOUT**: określa limit czasu w taktach czasomierza dla wywołań wewnętrznych NetX Duo wymaganych przez BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-240">**NX_BSD_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo internal calls required by BSD.</span></span> <span data-ttu-id="28eca-241">Wartość domyślna to (20 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="28eca-241">The default value is (20 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="28eca-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: określa limit czasu w taktach czasomierza dla wywołania rozłączenia NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="28eca-242">**NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: Specifies the timeout in timer ticks on NetX Duo disconnect call.</span></span> <span data-ttu-id="28eca-243">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="28eca-243">The default value is 1.</span></span>

- <span data-ttu-id="28eca-244">**NX_BSD_PRINT_ERRORS**: w przypadku ustawienia zwracany stan błędu funkcji BSD zwraca numer wiersza i typ błędu, np. NX_SOC_ERROR wystąpienia błędu.</span><span class="sxs-lookup"><span data-stu-id="28eca-244">**NX_BSD_PRINT_ERRORS**: If set, the error status return of a BSD function returns a line number and type of error e.g. NX_SOC_ERROR where the error occurs.</span></span> <span data-ttu-id="28eca-245">Wymaga to od deweloperów aplikacji zdefiniowania danych wyjściowych debugowania.</span><span class="sxs-lookup"><span data-stu-id="28eca-245">This requires the application developer to define the debug output.</span></span> <span data-ttu-id="28eca-246">Ustawienie domyślne jest wyłączone i nie określono danych wyjściowych debugowania w *nxd_bsd. h*.</span><span class="sxs-lookup"><span data-stu-id="28eca-246">The default setting is disabled and no debug output is specified in *nxd_bsd.h*.</span></span>

- <span data-ttu-id="28eca-247">**NX_BSD_TIMER_RATE**: interwał, po którym uruchamiane jest zadanie okresowego czasomierza BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-247">**NX_BSD_TIMER_RATE**: Interval after which BSD periodic timer task runs.</span></span> <span data-ttu-id="28eca-248">Wartość domyślna to 1 sekunda (1 \* NX_IP_PERIODIC_RATE).</span><span class="sxs-lookup"><span data-stu-id="28eca-248">The default value is 1 second (1 \* NX_IP_PERIODIC_RATE).</span></span>

- <span data-ttu-id="28eca-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: w przypadku ustawienia ta opcja umożliwia wykonanie procesu limitu czasu BSD w kontekście czasomierza systemu.</span><span class="sxs-lookup"><span data-stu-id="28eca-249">**NX_BSD_TIMEOUT_PROCESS_IN_TIMER**: If set, this option allows the BSD timeout process to execute in the system timer context.</span></span> <span data-ttu-id="28eca-250">Zachowanie domyślne jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="28eca-250">The default behavior is disabled.</span></span> <span data-ttu-id="28eca-251">Ta funkcja została szczegółowo opisana w rozdziale 2 "Instalacja i korzystanie z NetX Duo BSD".</span><span class="sxs-lookup"><span data-stu-id="28eca-251">This feature is described in more detail in Chapter 2 "Installation and Use of NetX Duo BSD".</span></span>

- <span data-ttu-id="28eca-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Włącz obsługę pakietów pierwotnych PPPoE.</span><span class="sxs-lookup"><span data-stu-id="28eca-252">**NX_BSD_RAW_PPPOE_SUPPORT**: Enable PPPoE raw packet support.</span></span> <span data-ttu-id="28eca-253">Domyślnie ta opcja nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="28eca-253">By default this option is not enabled.</span></span>

- <span data-ttu-id="28eca-254">**NX_BSD_ENABLE_DNS**: Jeśli ta funkcja jest włączona, NetX Duo BSD wyśle zapytanie DNS dla nazwy hosta lub adresu IP hosta.</span><span class="sxs-lookup"><span data-stu-id="28eca-254">**NX_BSD_ENABLE_DNS**: If enabled, NetX Duo BSD will send a DNS query for a hostname or host IP address.</span></span> <span data-ttu-id="28eca-255">Wymaga wcześniejszego utworzenia i uruchomienia wystąpienia klienta DNS.</span><span class="sxs-lookup"><span data-stu-id="28eca-255">Requires a DNS Client instance to be previously created and started.</span></span> <span data-ttu-id="28eca-256">Domyślnie nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="28eca-256">By default it is not enabled.</span></span>

- <span data-ttu-id="28eca-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Określa rozmiar nieprzetworzonej tabeli gniazda.</span><span class="sxs-lookup"><span data-stu-id="28eca-257">**NX_BSD_SOCKET_RAW_PROTOCOL_TABLE_SIZE**: Defines the size of the raw socket table.</span></span> <span data-ttu-id="28eca-258">Wartość musi być potęgą liczby dwa.</span><span class="sxs-lookup"><span data-stu-id="28eca-258">The value must be a power of two.</span></span> <span data-ttu-id="28eca-259">NetX BSD tworzy tablicę gniazd typu NX_BSD_SOCKETS do wysyłania i otrzymywania pakietów raw.</span><span class="sxs-lookup"><span data-stu-id="28eca-259">NetX BSD creates an array of sockets of type NX_BSD_SOCKETS for sending and receiving raw packets.</span></span> <span data-ttu-id="28eca-260">Należy włączyć NX_ENABLE_IP_RAW_PACKET_FILTER.</span><span class="sxs-lookup"><span data-stu-id="28eca-260">NX_ENABLE_IP_RAW_PACKET_FILTER must be enabled.</span></span> <span data-ttu-id="28eca-261">Domyślnie jest to 32.</span><span class="sxs-lookup"><span data-stu-id="28eca-261">By default it is 32.</span></span>

- <span data-ttu-id="28eca-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Maksymalna liczba adresów IPv4 zwróconych przez *Getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="28eca-262">**NX_BSD_IPV4_ADDR_MAX_NUM**: Maximum number of IPv4 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="28eca-263">Dzięki NX_BSD_IPV6_ADDR_MAX_NUM definiuje rozmiar puli bloku NetX BSD nx_bsd_addrinfo_block_pool do dynamicznego przydzielania pamięci do przechowywania informacji w *Getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="28eca-263">This along with NX_BSD_IPV6_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span> <span data-ttu-id="28eca-264">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="28eca-264">The default value is 5.</span></span>

- <span data-ttu-id="28eca-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Maksymalna liczba adresów IPv6 zwróconych przez *Getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="28eca-265">**NX_BSD_IPV6_ADDR_MAX_NUM**: Maximum number of IPv6 addresses returned by *getaddrinfo*.</span></span> <span data-ttu-id="28eca-266">Dzięki NX_BSD_IPV4_ADDR_MAX_NUM definiuje rozmiar puli bloku NetX BSD nx_bsd_addrinfo_block_pool do dynamicznego przydzielania pamięci do przechowywania informacji w *Getaddrinfo*.</span><span class="sxs-lookup"><span data-stu-id="28eca-266">This along with NX_BSD_IPV4_ADDR_MAX_NUM defines the size of the NetX BSD block pool nx_bsd_addrinfo_block_pool for dynamically allocating memory to address information storage in *getaddrinfo*.</span></span>

- <span data-ttu-id="28eca-267">**NX_BSD_IPV4_ADDR_PER_HOST**: określa maksymalną liczbę adresów IPv4 przechowywanych dla kwerendy DNS.</span><span class="sxs-lookup"><span data-stu-id="28eca-267">**NX_BSD_IPV4_ADDR_PER_HOST**: Defines maximum IPv4 addresses stored per DNS query.</span></span> <span data-ttu-id="28eca-268">Wartość domyślna to 5.</span><span class="sxs-lookup"><span data-stu-id="28eca-268">The default value is 5.</span></span>

- <span data-ttu-id="28eca-269">**NX_BSD_IPV6_ADDR_PER_HOST**: określa maksymalne adresy IPv6 przechowywane dla kwerendy DNS.</span><span class="sxs-lookup"><span data-stu-id="28eca-269">**NX_BSD_IPV6_ADDR_PER_HOST**: Defines maximum IPv6 addresses stored per DNS query.</span></span> <span data-ttu-id="28eca-270">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="28eca-270">The default value is 2.</span></span>

## <a name="bsd-socket-options"></a><span data-ttu-id="28eca-271">Opcje gniazda BSD</span><span class="sxs-lookup"><span data-stu-id="28eca-271">BSD Socket Options</span></span>

<span data-ttu-id="28eca-272">Poniższa lista opcji gniazda BSD NetX Duo można włączyć (lub wyłączyć) w czasie wykonywania dla poszczególnych gniazd przy użyciu usługi *SetSockOpt* :</span><span class="sxs-lookup"><span data-stu-id="28eca-272">The following list of NetX Duo BSD socket options can be enabled (or disabled) at run time on a per socket basis using the *setsockopt* service:</span></span>

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, 
                const void *option_value, INT option_length);
```

<span data-ttu-id="28eca-273">Istnieją dwa różne ustawienia dla option_level.</span><span class="sxs-lookup"><span data-stu-id="28eca-273">There are two different settings for option_level.</span></span>

<span data-ttu-id="28eca-274">Pierwszy typ opcji gniazda czasu wykonywania jest SOL_SOCKET dla opcji poziomu gniazda.</span><span class="sxs-lookup"><span data-stu-id="28eca-274">The first type of run time socket options is SOL_SOCKET for socket level options.</span></span> <span data-ttu-id="28eca-275">Aby włączyć opcję poziomu gniazda, należy wywołać *setsockopt* option_level z ustawionym na SOL_SOCKET, a option_name ustawić dla konkretnej opcji, np. SO_BROADCAST *.*</span><span class="sxs-lookup"><span data-stu-id="28eca-275">To enable a socket level option, call *setsockopt* with option_level set to SOL_SOCKET and option_name set to the specific option e.g. SO_BROADCAST *.*</span></span> <span data-ttu-id="28eca-276">Aby pobrać ustawienie opcji, wywołaj *getsockopt* dla option_name z option_level ponownie ustawiona na SOL_SOCKET.</span><span class="sxs-lookup"><span data-stu-id="28eca-276">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to SOL_SOCKET.</span></span>

<span data-ttu-id="28eca-277">Zostanie wyświetlona lista opcji poziomu gniazda w czasie wykonywania poniżej.</span><span class="sxs-lookup"><span data-stu-id="28eca-277">The list of run time socket level options is shown below.</span></span>

- <span data-ttu-id="28eca-278">**SO_BROADCAST**: ustawienie umożliwia wysyłanie i otrzymywanie pakietów emisji z gniazd NetX.</span><span class="sxs-lookup"><span data-stu-id="28eca-278">**SO_BROADCAST**:  If set, this enables sending and receiving broadcast packets from Netx sockets.</span></span> <span data-ttu-id="28eca-279">Jest to domyślne zachowanie dla NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="28eca-279">This is the default behavior for NetX Duo.</span></span> <span data-ttu-id="28eca-280">Wszystkie gniazda mają tę możliwość.</span><span class="sxs-lookup"><span data-stu-id="28eca-280">All sockets have this capability.</span></span>

- <span data-ttu-id="28eca-281">**SO_ERROR**: służy do uzyskiwania stanu gniazda dla operacji poprzedniej gniazda określonego gniazda przy użyciu usługi *getsockopt* .</span><span class="sxs-lookup"><span data-stu-id="28eca-281">**SO_ERROR**:  Used to obtain socket status on the previous socket operation of the specified socket, using the *getsockopt* service.</span></span> <span data-ttu-id="28eca-282">Wszystkie gniazda mają tę możliwość.</span><span class="sxs-lookup"><span data-stu-id="28eca-282">All sockets have this capability.</span></span>

- <span data-ttu-id="28eca-283">**SO_KEEPALIVE**: ustawienie powoduje włączenie funkcji utrzymywania aktywności protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="28eca-283">**SO_KEEPALIVE**:  If set, this enables the TCP Keep Alive feature.</span></span> <span data-ttu-id="28eca-284">Wymaga to, aby Biblioteka NetX Duo była skompilowana przy użyciu NX_TCP_ENABLE_KEEPALIVE zdefiniowanej w *nx_user. h*.</span><span class="sxs-lookup"><span data-stu-id="28eca-284">This requires the NetX Duo library to be built with NX_TCP_ENABLE_KEEPALIVE defined in *nx_user.h*.</span></span> <span data-ttu-id="28eca-285">Domyślnie ta funkcja jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="28eca-285">By default this feature is disabled.</span></span>

- <span data-ttu-id="28eca-286">**SO_RCVTIMEO**: ustawia opcję oczekiwania w sekundach dla pakietów odbieranych w NetX Duo BSD Sockets.</span><span class="sxs-lookup"><span data-stu-id="28eca-286">**SO_RCVTIMEO**:  This sets the wait option in seconds for receiving packets on NetX Duo BSD sockets.</span></span> <span data-ttu-id="28eca-287">Wartość domyślna to NX_WAIT_FOREVER (0xFFFFFFFF) lub, jeśli jest włączony bez blokowania, NX_NO_WAIT (0x0).</span><span class="sxs-lookup"><span data-stu-id="28eca-287">The default value is the NX_WAIT_FOREVER (0xFFFFFFFF) or, if non-blocking is enabled, NX_NO_WAIT (0x0).</span></span>

- <span data-ttu-id="28eca-288">**SO_RCVBUF**: Określa rozmiar okna gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="28eca-288">**SO_RCVBUF**:  This sets the window size of the TCP socket.</span></span> <span data-ttu-id="28eca-289">Wartość domyślna NX_BSD_TCP_WINDOW jest ustawiona na 64 KB w przypadku pakietów BSD TCP Sockets.</span><span class="sxs-lookup"><span data-stu-id="28eca-289">The default value, NX_BSD_TCP_WINDOW, is set to 64k for BSD TCP sockets.</span></span> <span data-ttu-id="28eca-290">Aby ustawić rozmiar ponad 65535 wymaga skompilowania biblioteki NetX Duo z NX_TCP_ENABLE_WINDOW_SCALING być zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="28eca-290">To set the size over 65535 requires the NetX Duo library to be built with the NX_TCP_ENABLE_WINDOW_SCALING be defined.</span></span>

- <span data-ttu-id="28eca-291">**SO_REUSEADDR**: ustawienie umożliwia zmapowanie wielu gniazd na jeden port.</span><span class="sxs-lookup"><span data-stu-id="28eca-291">**SO_REUSEADDR**:  If set, this enables multiple sockets to be mapped to one port.</span></span> <span data-ttu-id="28eca-292">Typowy sposób użycia dotyczy gniazda serwera TCP.</span><span class="sxs-lookup"><span data-stu-id="28eca-292">The typical usage is for the TCP Server socket.</span></span> <span data-ttu-id="28eca-293">Jest to domyślne zachowanie NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="28eca-293">This is the default behavior of NetX Duo sockets.</span></span>

<span data-ttu-id="28eca-294">Drugim typem opcji gniazda czasu wykonywania jest poziom opcji IP.</span><span class="sxs-lookup"><span data-stu-id="28eca-294">The second type of run time socket options is the IP option level.</span></span> <span data-ttu-id="28eca-295">Aby włączyć opcję poziomu IP, należy wywołać *setsockopt* option_level z ustawionym na IP_PROTO, a option_name ustawić opcję na np. IP_MULTICAST_TTL *.*</span><span class="sxs-lookup"><span data-stu-id="28eca-295">To enable an IP level option, call *setsockopt* with option_level set to IP_PROTO and option_name set to the option e.g. IP_MULTICAST_TTL *.*</span></span> <span data-ttu-id="28eca-296">Aby pobrać ustawienie opcji, wywołaj *getsockopt* dla option_name z option_level ponownie ustawiona na IP_PROTO.</span><span class="sxs-lookup"><span data-stu-id="28eca-296">To retrieve an option setting, call *getsockopt* for the option_name with option_level again set to IP_PROTO.</span></span>

<span data-ttu-id="28eca-297">Zostanie wyświetlona lista opcji poziomu adresu IP czasu wykonywania poniżej.</span><span class="sxs-lookup"><span data-stu-id="28eca-297">The list of run time IP level options is shown below.</span></span>

- <span data-ttu-id="28eca-298">**IP_MULTICAST_TTL**: służy do ustawiania czasu wygaśnięcia dla gniazd UDP.</span><span class="sxs-lookup"><span data-stu-id="28eca-298">**IP_MULTICAST_TTL**:  This sets the time to live for UDP sockets.</span></span> <span data-ttu-id="28eca-299">Wartość domyślna to NX_IP_TIME_TO_LIVE (0x80) podczas tworzenia gniazda.</span><span class="sxs-lookup"><span data-stu-id="28eca-299">The default value is NX_IP_TIME_TO_LIVE (0x80) when the socket is created.</span></span> <span data-ttu-id="28eca-300">Tę wartość można zastąpić, wywołując *SetSockOpt* z tą opcją gniazda.</span><span class="sxs-lookup"><span data-stu-id="28eca-300">This value can be overridden by calling *setsockopt* with this socket option.</span></span>

- <span data-ttu-id="28eca-301">**IP_RAW_IPV6_HDRINCL**: Jeśli ta opcja jest ustawiona, aplikacja wywołująca musi dołączyć nagłówek IPv6 i opcjonalne nagłówki aplikacji do danych przesyłanych w przypadku nieprzetworzonych gniazd IPv6 utworzonych przez BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-301">**IP_RAW_IPV6_HDRINCL**:  If this option is set, the calling application must append an IPv6 header and optionally application headers to data being transmitted on raw IPv6 sockets created by BSD.</span></span> <span data-ttu-id="28eca-302">Aby można było użyć tej opcji, w zadaniu adresu IP musi być włączone przetwarzanie nieprzetworzonego gniazda.</span><span class="sxs-lookup"><span data-stu-id="28eca-302">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="28eca-303">**IP_ADD_MEMBERSHIP**: Jeśli ta opcja jest ustawiona, w celu przyłączenia do określonej grupy IGMP gniazdo BSD (dotyczy tylko gniazd UDP).</span><span class="sxs-lookup"><span data-stu-id="28eca-303">**IP_ADD_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to join the specified IGMP group.</span></span>

- <span data-ttu-id="28eca-304">**IP_DROP_MEMBERSHIP**: w przypadku ustawienia, ta opcja włącza gniazdo BSD (dotyczy tylko gniazd UDP), aby opuścić określoną grupę IGMP.</span><span class="sxs-lookup"><span data-stu-id="28eca-304">**IP_DROP_MEMBERSHIP**:  If set, this options enables the BSD socket (applies only to UDP sockets) to leave the specified IGMP group.</span></span>

- <span data-ttu-id="28eca-305">**IP_HDRINCL**: Jeśli ta opcja jest ustawiona, aplikacja wywołująca musi dołączyć nagłówek IP i opcjonalne nagłówki aplikacji do danych przesyłanych w przypadku nieprzetworzonych gniazd IPv4 utworzonych w programie BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-305">**IP_HDRINCL**:  If this option is set, the calling application must append the IP header and optionally application headers to data being transmitted on raw IPv4 sockets created in BSD.</span></span> <span data-ttu-id="28eca-306">Aby można było użyć tej opcji, w zadaniu adresu IP musi być włączone przetwarzanie nieprzetworzonego gniazda.</span><span class="sxs-lookup"><span data-stu-id="28eca-306">To use this option, raw socket processing must be enabled on the IP task.</span></span>

- <span data-ttu-id="28eca-307">**IP_RAW_RX_NO_HEADER**: Jeśli zostanie wyczyszczony, nagłówek IPv6 zostanie dołączony do odebranych danych dla nieprzetworzonych gniazd protokołu IPv6 utworzonych w systemie BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-307">**IP_RAW_RX_NO_HEADER**:  If cleared, the IPv6 header is included with the received data for raw IPv6 sockets created in BSD.</span></span> <span data-ttu-id="28eca-308">Nagłówki IPv6 są domyślnie usuwane w gniazdach BSD RAW IPv6 Sockets, a długość pakietu nie obejmuje nagłówka IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-308">IPv6 headers are removed by default in BSD raw IPv6 sockets, and the packet length does not include the IPv6 header.</span></span>

<span data-ttu-id="28eca-309">W przypadku ustawienia nagłówek IPv4 zostanie usunięty z odbierania danych w gniazdach BSD RAW typu IPv4.</span><span class="sxs-lookup"><span data-stu-id="28eca-309">If set, the IPv4 header is removed from received data on BSD raw sockets of type IPv4.</span></span> <span data-ttu-id="28eca-310">Nagłówki IPv4 są domyślnie uwzględniane w przypadku gniazd BSD RAW IPv4 i długość pakietu obejmuje nagłówek IPv4.</span><span class="sxs-lookup"><span data-stu-id="28eca-310">IPv4 headers are included by default in BSD raw IPv4 sockets and packet length includes the IPv4 header.</span></span>

<span data-ttu-id="28eca-311">Ta opcja nie ma wpływu na dane transmisji IPv4 lub IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-311">This option has no effect on either IPv4 or IPv6 transmission data.</span></span>

## <a name="small-ipv4-example"></a><span data-ttu-id="28eca-312">Przykład małych adresów IPv4</span><span class="sxs-lookup"><span data-stu-id="28eca-312">Small IPv4 Example</span></span>

<span data-ttu-id="28eca-313">Poniżej opisano przykład korzystania z usług BSD NetX Duo dla sieci IPv4.</span><span class="sxs-lookup"><span data-stu-id="28eca-313">An example of how to use NetX Duo BSD services for IPv4 networks is described below.</span></span> <span data-ttu-id="28eca-314">W tym przykładzie plik dołączany *nxd_bsd. h* jest wprowadzany w wierszu 8.</span><span class="sxs-lookup"><span data-stu-id="28eca-314">In this example, the include file *nxd_bsd.h* is brought in at line 8.</span></span> <span data-ttu-id="28eca-315">Następnie *bsd_pool* *bsd_ip* wystąpienia adresu IP i puli pakietów są tworzone jako zmienne globalne w wierszu 20 i 21.</span><span class="sxs-lookup"><span data-stu-id="28eca-315">Next, the IP instance *bsd_ip* and packet pool *bsd_pool* are created as global variables at line 20 and 21.</span></span> <span data-ttu-id="28eca-316">Należy zauważyć, że w tej wersji demonstracyjnej jest wykorzystywany sterownik sieciowy pamięci RAM (wirtualnej)*_nx_ram_network_driver*.</span><span class="sxs-lookup"><span data-stu-id="28eca-316">Note that this demo uses a ram (virtual) network driver *, _nx_ram_network_driver*.</span></span> <span data-ttu-id="28eca-317">Klient i serwer będą współużytkować ten sam adres IP na pojedynczym wystąpieniu IP w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="28eca-317">The client and server will share the same IP address on single IP instance in this example.</span></span>

<span data-ttu-id="28eca-318">Wątki klienta i serwera są tworzone w wierszach 62 i 68.</span><span class="sxs-lookup"><span data-stu-id="28eca-318">The client and server threads are created on lines 62 and 68.</span></span> <span data-ttu-id="28eca-319">Pula pakietów BSD do przesyłania pakietów jest tworzona w wierszu 78 i używana w tworzeniu wystąpienia IP w wierszu 87.</span><span class="sxs-lookup"><span data-stu-id="28eca-319">The BSD packet pool for transmitting packets is created on line 78 and used in the IP instance creation on line 87.</span></span> <span data-ttu-id="28eca-320">Zwróć uwagę, że zadanie wątku IP ma określony priorytet 1 w wywołaniu *nx_ip_create* .</span><span class="sxs-lookup"><span data-stu-id="28eca-320">Note that the IP thread task is given priority 1 in the *nx_ip_create* call.</span></span> <span data-ttu-id="28eca-321">Ten wątek powinien być zadaniem o najwyższym priorytecie zdefiniowanym w programie w celu uzyskania optymalnej wydajności NetX.</span><span class="sxs-lookup"><span data-stu-id="28eca-321">This thread should be the highest priority task defined in the program for optimal NetX performance.</span></span>

<span data-ttu-id="28eca-322">Wystąpienie protokołu IP jest włączone dla usług ARP i TCP w wierszach 88 i 110.</span><span class="sxs-lookup"><span data-stu-id="28eca-322">The IP instance is enabled for ARP and TCP services on lines 88 and 110 respectively.</span></span> <span data-ttu-id="28eca-323">Ostatnim wymaganiem przed użyciem usług BSD jest wywołanie *bsd_initialize* w wierszu 120 w celu skonfigurowania wszystkich struktur danych i zasobów NetX i ThreadX wymaganych przez BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-323">The last requirement before BSD services can be used is to call *bsd_initialize* on line 120 to set up all data structures and NetX and ThreadX resources needed by BSD.</span></span>

<span data-ttu-id="28eca-324">Funkcja wprowadzania wątku serwera jest zdefiniowana dalej.</span><span class="sxs-lookup"><span data-stu-id="28eca-324">The server thread entry function is defined next.</span></span> <span data-ttu-id="28eca-325">Gniazdo TCP BSD jest tworzone w wierszu 149.</span><span class="sxs-lookup"><span data-stu-id="28eca-325">The BSD TCP socket is created on line 149.</span></span> <span data-ttu-id="28eca-326">Adres IP serwera i port są ustawiane w wierszach 160-163.</span><span class="sxs-lookup"><span data-stu-id="28eca-326">The server IP address and port are set on lines 160-163.</span></span> <span data-ttu-id="28eca-327">Zwróć uwagę na użycie makr w kolejności bajtów sieci *htonl* i *htons* zastosowanych do adresu IP i portu.</span><span class="sxs-lookup"><span data-stu-id="28eca-327">Note the use of host to network byte order macros *htonl* and *htons* applied to the IP address and port.</span></span> <span data-ttu-id="28eca-328">Jest to zgodne ze specyfikacją gniazda BSD, że dane wielobajtowe są przesyłane do usług BSD w kolejności bajtów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="28eca-328">This is in compliance with BSD socket specification that multi byte data is submitted to the BSD services in network byte order.</span></span>

<span data-ttu-id="28eca-329">Następnie główne gniazdo serwera jest powiązane z portem przy użyciu usługi *bind* w wierszu 166.</span><span class="sxs-lookup"><span data-stu-id="28eca-329">Next, the master server socket is bound to the port using the *bind* service on line 166.</span></span> <span data-ttu-id="28eca-330">Jest to gniazdo nasłuchiwania dla żądań połączeń TCP korzystających z usługi *Listen* w wierszu 180.</span><span class="sxs-lookup"><span data-stu-id="28eca-330">This is the listening socket for TCP connection requests using the *listen* service on line 180.</span></span> <span data-ttu-id="28eca-331">W tym miejscu funkcja wątek serwera *thread_server_entry*, pętle służące do sprawdzania odbierania zdarzeń przy użyciu wywołania *select* w wierszu 202.</span><span class="sxs-lookup"><span data-stu-id="28eca-331">From here the server thread function, *thread_server_entry*, loops to check for receive events using the *select* call on line 202.</span></span> <span data-ttu-id="28eca-332">Jeśli zdarzenie Odbierz jest żądaniem połączenia, które jest określane przez porównanie listy gotowość do odczytu, wywołuje metodę *Accept* w wierszu 213.</span><span class="sxs-lookup"><span data-stu-id="28eca-332">If a receive event is a connection request, which is determined by comparing the read ready list, it calls *accept* on line 213.</span></span> <span data-ttu-id="28eca-333">Podrzędne gniazdo serwera jest przypisane do obsługi żądania połączenia i dodawane do głównej listy gniazd serwera TCP podłączonych do klienta w wierszu 223.</span><span class="sxs-lookup"><span data-stu-id="28eca-333">A child server socket is assigned to handle the connection request and added to the master list of TCP server sockets connected to a Client on line 223.</span></span> <span data-ttu-id="28eca-334">Jeśli nie ma nowych żądań połączeń, wątek serwera sprawdza wszystkie aktualnie połączone gniazda dla zdarzeń odbioru w pętli for, rozpoczynając od wiersza 236.</span><span class="sxs-lookup"><span data-stu-id="28eca-334">If there are no new connection requests, the server thread then checks all the currently connected sockets for receive events in the for loop starting on line 236.</span></span> <span data-ttu-id="28eca-335">W przypadku wykrycia zdarzenia odbierania, wywołuje on funkcję *send* i *Odbierz* dla tego gniazda, dopóki nie zostaną odebrane żadne dane (połączenie zamknięte po drugiej stronie), a gniazdo zostanie zamknięte przy użyciu usługi *soc_close* w wierszu 277.</span><span class="sxs-lookup"><span data-stu-id="28eca-335">When a receive event waiting is detected, it calls *send* and *recv* on that socket until no data is received (connection closed on the other side) and the socket is closed using the *soc_close* service on line 277.</span></span>

<span data-ttu-id="28eca-336">Po skonfigurowaniu wątku serwera funkcja wprowadzania wątku klienta *thread_client_entry* tworzy gniazdo w wierszu 326 i łączy się z gniazdem serwera TCP przy użyciu połączenia *połączenia* w wierszu 337.</span><span class="sxs-lookup"><span data-stu-id="28eca-336">After the server thread sets up, the Client thread entry function, *thread_client_entry,* creates a socket on line 326 and connects with the TCP server socket using the *connect* call on line 337.</span></span> <span data-ttu-id="28eca-337">Następnie tworzy pętlę, aby wysyłać i odbierać pakiety  przy użyciu *odpowiednio usług wysyłania i odbierania.*</span><span class="sxs-lookup"><span data-stu-id="28eca-337">It then loops to send and receive packets using the *send* and *recv* services respectively.</span></span> <span data-ttu-id="28eca-338">Gdy nie otrzymasz więcej danych, program zamknie gniazdo w wierszu 398 przy użyciu usługi *soc_close* .</span><span class="sxs-lookup"><span data-stu-id="28eca-338">When no more data is received, it closes the socket on line 398 using the *soc_close* service.</span></span> <span data-ttu-id="28eca-339">Po rozłączeniu funkcja wprowadzania wątku klienta tworzy nowe gniazdo TCP i wysyła kolejne żądanie połączenia w pętli while uruchomione w wierszu 321.</span><span class="sxs-lookup"><span data-stu-id="28eca-339">After disconnection, the client thread entry function creates a new TCP socket and makes another connection request in the while loop started on line 321.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection, sending,
and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQR
    STUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */

ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */

VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */
int     main()
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

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16, TX_NO_TIME_SLICE,
                    TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool", 128,
                                pointer, 16384);

    pointer = pointer + 16384;
    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                    0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                    pointer, 2048, 1);
                    pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable ARP \n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize (&bsd_ip, &bsd_pool,pointer, 2048, 2);
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT       status, sock, sock_tcp_server;
ULONG     actual_status;
INT       Clientlen;
INT       i;
UINT      is_set = NX_FALSE;
struct    sockaddr_in serverAddr;
struct    sockaddr_in ClientAddr;

    tx_thread_sleep(100);

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
        &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("Error on Server socket %d create \n", sock_tcp_server);
        return;
    }

    printf("Server socket %d created\n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin_family = AF_INET;
    serverAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    serverAddr.sin_port = htons(SERVER_PORT);

    /* Bind this server socket */
    status = bind (sock_tcp_server, (struct sockaddr *) &serverAddr,
                sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error on Server Socket %d Bind \n", sock_tcp_server);
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen (sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error on Server Socket %d Listen\n", sock_tcp_server);
        return;
    }
    else
        printf("Server socket %d listen complete\n", sock_tcp_server);

    /* All set to accept client connections */

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ((status == 0xFFFFFFFF) || (status == 0))
        {

            printf("Error with select. Status 0x%x\n", status);

            continue;
        }

        /* Check for a connection request. */
        is_set = FD_ISSET(sock_tcp_server, &read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,(struct sockaddr*)&ClientAddr,
                        &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i , &master_list)) &&
                (FD_ISSET(i , &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server received no data from Client on
                            socket %d)\n", i);
                        break;
                    }
                    else if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server receiving data from Client on
                            socket %d\n", i);
                        break;
                    }
                    if(status == SERVER_RCV_BUFFER_SIZE) status--;
                    Server_Rcv_Buffer[status] = 0;
                    printf("Server socket %d received %d bytes: %s\n ",
                            i, (ULONG)status, Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == NX_SOC_ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                        Client\n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                        Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != NX_SOC_ERROR)
                {
                    printf("Server socket %d closed \n", i);
                }
                else
                {
                    printf("Error on closing Server socket %d \n", i);
                }
            }
        }

    /* Loop back to check any next client connection */
    }
}

CHAR     Client_Rcv_Buffer[100];

VOID     thread_client_entry(ULONG thread_input)
{

INT        status;
INT        sock_tcp_client, length;
struct     sockaddr_in echoServAddr;
struct     sockaddr_in localAddr; /

    /* Let the server side get set up. */
    tx_thread_sleep(200);

    /* Set local port for displaying IP address and port. */
    memset(&localAddr, 0, sizeof(localAddr));
    localAddr.sin_family = AF_INET;
    localAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    localAddr.sin_port = htons(CLIENT_PORT);

    /* Set server port and IP address which we need to connect. */
    memset(&echoServAddr, 0, sizeof(echoServAddr));
    echoServAddr.sin_family = AF_INET;
    echoServAddr.sin_addr.s_addr = htonl(IP_ADDRESS(1,2,3,4));
    echoServAddr.sin_port = htons(SERVER_PORT);

    /* Now make client connections with the server. */
    while (1)
    {

        printf("\n");

        /* Create BSD TCP Socket */
        sock_tcp_client = socket( AF_INET, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n", sock_tcp_client);
            return;
        }

        printf("Client socket %d created\n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr,
                        sizeof(echoServAddr));

        /* Check for error. */
        if (status != OK)
        {
            printf("Error on Client socket %d connect\n", sock_tcp_client);
                    soc_close(sock_tcp_client);
            return;
        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr,
                            &length);

        printf("Client port = %lu , Client = 0x%x,",
            htonl(localAddr.sin_port), htonl(localAddr.sin_addr.s_addr));

        length = sizeof(struct sockaddr_in);

        status = getpeername( sock_tcp_client, (struct sockaddr *)
                            &echoServAddr, &length);

        printf("Remote port = %lu, Remote IP = 0x%x \n",
                htonl(echoServAddr.sin_port),
                htonl(echoServAddr.sin_addr.s_addr));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
            sock_tcp_client);

            status = send(sock_tcp_client, "Hello", (sizeof("Hello")), 0);

            if (status == ERROR)
            {
                printf("Error: Client Socket (%d) send \n", sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,100,0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    380 printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Nothing received by Client on socket %d\n",
                            sock_tcp_client);
                }

                break;
            }
            else
            {
                printf("Client socket %d received %d bytes: %s\n",
                        sock_tcp_client,
                        status, Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = soc_close(sock_tcp_client);

        if (status != ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```

## <a name="small-ipv6-example-system"></a><span data-ttu-id="28eca-340">Mały system przykładowych adresów IPv6</span><span class="sxs-lookup"><span data-stu-id="28eca-340">Small IPv6 Example System</span></span>

<span data-ttu-id="28eca-341">Przykład sposobu korzystania z usług BSD NetX Duo dla sieci IPv6 jest opisany w programie poniżej.</span><span class="sxs-lookup"><span data-stu-id="28eca-341">An example of how to use NetX Duo BSD services for IPv6 networks is described in the program below.</span></span> <span data-ttu-id="28eca-342">Ten przykład jest bardzo podobny do programu demonstracyjnego protokołu IPv4, który został wcześniej opisany przy użyciu kilku ważnych różnic.</span><span class="sxs-lookup"><span data-stu-id="28eca-342">This example is very similar to the IPv4 demo program previously described with a few important differences.</span></span>

<span data-ttu-id="28eca-343">Wątki klienta i serwera, Pula pakietów BSD, wystąpienie protokołu IP i Inicjowanie BSD odbywają się tak, jak w przypadku protokołu IPv4 BSD.</span><span class="sxs-lookup"><span data-stu-id="28eca-343">The client and server threads, BSD packet pool, IP instance and BSD initialization happens as it does for IPv4 BSD sockets.</span></span>

<span data-ttu-id="28eca-344">W funkcji wprowadzania wątku serwera *thread_server_entry* definiuje kilka zmiennych IPv6 przy użyciu *sockaddr_in6* i *NXD_ADDRESS* typów danych w wierszach 145-148.</span><span class="sxs-lookup"><span data-stu-id="28eca-344">In the server thread entry function, *thread_server_entry*, defines a couple IPv6 variables using *sockaddr_in6* and *NXD_ADDRESS* data types on lines 145-148.</span></span> <span data-ttu-id="28eca-345">Typ danych NXD_ADDRESS może w rzeczywistości przechowywać typy adresów IPv4 i IPv6.</span><span class="sxs-lookup"><span data-stu-id="28eca-345">The NXD_ADDRESS data type can actually store both IPv4 and IPv6 address types.</span></span>

<span data-ttu-id="28eca-346">Następnie wątek serwera włącza protokół IPv6 i ICMPv6 w wystąpieniu IP przy użyciu usług *nxd_ipv6_enable* i *nxd_icmpv6_enable* odpowiednio w wierszu 161 i 169.</span><span class="sxs-lookup"><span data-stu-id="28eca-346">Next, the server thread enables IPv6 and ICMPv6 on the IP instance using the *nxd_ipv6_enable* and *nxd_icmpv6_enable* service respectively on line 161 and 169.</span></span> <span data-ttu-id="28eca-347">Następnie lokalne i globalne adresy IP są rejestrowane przy użyciu wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="28eca-347">Next, the link local and global IP addresses are registered with the IP instance.</span></span> <span data-ttu-id="28eca-348">Odbywa się to za pomocą usługi *nxd_ipv6_address_set* w wierszach 180 i 195.</span><span class="sxs-lookup"><span data-stu-id="28eca-348">This is done using the *nxd_ipv6_address_set* service on lines 180 and 195.</span></span> <span data-ttu-id="28eca-349">Następnie w trybie uśpienia jest wystarczająco dużo miejsca, aby zadanie wątku IP zakończyło protokół wykrywania zduplikowanych adresów i zarejestrować te adresy jako prawidłowe adresy w *tx_thread_sleep* wywołaniu w wierszu 201.</span><span class="sxs-lookup"><span data-stu-id="28eca-349">It then sleeps long enough for the IP thread task to complete the Duplicate Address Detection protocol and register these addresses as valid addresses on the *tx_thread_sleep* call on line 201.</span></span>

<span data-ttu-id="28eca-350">Następnie gniazdo serwera TCP jest tworzone z argumentem wejściowym typu gniazdo AF_INET6 w wierszu 204.</span><span class="sxs-lookup"><span data-stu-id="28eca-350">Next, the TCP server socket is created with the AF_INET6 socket type input argument on line 204.</span></span> <span data-ttu-id="28eca-351">Adres IPv6 i port gniazda są ustawiane w wierszach 216-221, a następnie w przypadku używania makr *htonl* i *htons* do umieszczania danych w kolejności bajtów sieciowych dla usług BSD Sockets.</span><span class="sxs-lookup"><span data-stu-id="28eca-351">The socket IPv6 address and port are set on lines 216-221, again noting the use of *htonl* and *htons* macros to put data in network byte order for BSD socket services.</span></span> <span data-ttu-id="28eca-352">W tym miejscu funkcja wprowadzania wątku serwera jest niemal identyczna z przykładem IPv4.</span><span class="sxs-lookup"><span data-stu-id="28eca-352">From here on, the server thread entry function is virtually identical to the IPv4 example.</span></span>

<span data-ttu-id="28eca-353">Funkcja wprowadzania wątku klienta, *thread_client_entry*, została zdefiniowana dalej.</span><span class="sxs-lookup"><span data-stu-id="28eca-353">The client thread entry function, *thread_client_entry*, is defined next.</span></span> <span data-ttu-id="28eca-354">Należy zauważyć, że ponieważ klient TCP w tym przykładzie współużytkuje to samo wystąpienie IP i adres IPv6 co serwer TCP, nie musi ponownie włączać usług IPv6 ani ICMPv6 w wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="28eca-354">Note that because the TCP client in this example shares the same IP instance and IPv6 address as the TCP server, we do not need to enable IPv6 or ICMPv6 services on the IP instance again.</span></span> <span data-ttu-id="28eca-355">Ponadto adres IPv6 jest już zarejestrowany w wystąpieniu adresu IP.</span><span class="sxs-lookup"><span data-stu-id="28eca-355">Further, the IPv6 address is also already registered with the IP instance.</span></span> <span data-ttu-id="28eca-356">Zamiast tego funkcja wprowadzania wątku klienta po prostu czeka na wiersz 368, aby skonfigurować serwer.</span><span class="sxs-lookup"><span data-stu-id="28eca-356">Instead, the client thread entry function simply waits on line 368 for the server to set up.</span></span> <span data-ttu-id="28eca-357">Adres serwera i port są ustawiane, przy użyciu makr hosta do kolejności bajtów sieciowych w wierszach 387-392, a następnie klient może połączyć się z serwerem TCP w wierszu 412.</span><span class="sxs-lookup"><span data-stu-id="28eca-357">The server address and port are set, using the host to network byte order macros on lines 387-392, and then the Client can connect with the TCP server on line 412.</span></span> <span data-ttu-id="28eca-358">Należy pamiętać, że typy danych lokalnego adresu IP w wierszach 378-383 są używane tylko w celu przedstawienia usług *getsockname* i *getpeername* w wierszach 425 i 434 odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="28eca-358">Note that the local IP address data types in lines 378-383 are used only to demonstrate the *getsockname* and *getpeername* services on lines 425 and 434 respectively.</span></span> <span data-ttu-id="28eca-359">Ze względu na to, że dane pochodzą z sieci, w sieci można hostować makra kolejności bajtów używane w wierszach 378-383.</span><span class="sxs-lookup"><span data-stu-id="28eca-359">Because the data is coming from the network, the network to host byte order macros as used in lines 378-383.</span></span>

<span data-ttu-id="28eca-360">Kolejna funkcja wprowadzania wątku klienta wprowadza pętlę, w której tworzony jest gniazdo TCP, sprawia, że połączenie TCP i wysyła i odbiera dane z serwerem TCP, dopóki nie zostanie odebrane praktycznie więcej danych, jak w przypadku przykładu IPv4.</span><span class="sxs-lookup"><span data-stu-id="28eca-360">Next the client thread entry function enters a loop in which it creates a TCP socket, makes a TCP connection and sends and receives data with the TCP server until no more data is received virtually the same as the IPv4 example.</span></span> <span data-ttu-id="28eca-361">Następnie zamyka gniazdo w wierszu 483, wstrzymuje się krótko i tworzy kolejne gniazdo TCP i żąda połączenia z serwerem TCP.</span><span class="sxs-lookup"><span data-stu-id="28eca-361">It then closes the socket on line 483, pauses briefly and creates another TCP socket and requests a TCP server connection.</span></span>

<span data-ttu-id="28eca-362">Jedną z ważnych różnic przy użyciu protokołu IPv4 jest to, że wywołania *gniazda* określają gniazdo IPv6 przy użyciu argumentu AF_INET6 Input.</span><span class="sxs-lookup"><span data-stu-id="28eca-362">One important difference with the IPv4 example is the *socket* calls specify an IPv6 socket using the AF_INET6 input argument.</span></span> <span data-ttu-id="28eca-363">Kolejną istotną różnicą jest to, że wywołanie *połączenia* klienta TCP pobiera *sockaddr_in6* typ danych, a argument długości ma ustawioną wartość *sockaddr_in6* typu danych.</span><span class="sxs-lookup"><span data-stu-id="28eca-363">Another important difference is that the TCP Client *connect* call takes an *sockaddr_in6* data type and a length argument set to the size of the *sockaddr_in6* data type.</span></span>

```c
/* This is a small demo of BSD Wrapper for the high-performance NetX Duo
TCP/IP stack which uses standard BSD services for TCP connection,
disconnection, sending, and receiving using a simulated Ethernet driver. */

#include     "tx_api.h"
#include     "nx_api.h"
#include     "nxd_bsd.h"
#include     <string.h>
#include     <stdlib.h>

#define     DEMO_STACK_SIZE     (16*1024)
#define     SERVER_PORT         87
#define     CLIENT_PORT         77

/* Define the ThreadX and NetX object control blocks... */

TX_THREAD         thread_server;
TX_THREAD         thread_client;
NX_PACKET_POOL    bsd_pool;
NX_IP             bsd_ip;

/* Define some global data. */
CHAR     *msg0 = "Client 1:
    ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";

INT     maxfd;

/* Define the counters used in the demo application... */
ULONG     error_counter;

/* Define fd_sets for the BSD server socket. */
fd_set     master_list, read_ready;

/* Define thread prototypes. */
VOID     thread_server_entry(ULONG thread_input);
VOID     thread_client_entry(ULONG thread_input);
void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);

/* Define main entry point. */

int     main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */

void tx_application_define(void *first_unused_memory)
{
CHAR     *pointer;
UINT     status;

    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;

    /* Create a server thread. */
    tx_thread_create(&thread_server, "Server", thread_server_entry, 0,
                    pointer, DEMO_STACK_SIZE, 8, 8,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Create a Client thread. */
    tx_thread_create(&thread_client, "Client", thread_client_entry, 0,
                    pointer, DEMO_STACK_SIZE, 16, 16,
                    TX_NO_TIME_SLICE, TX_AUTO_START);

    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

    /* Create a BSD packet pool. */
    status = nx_packet_pool_create(&bsd_pool, "NetX BSD Packet Pool",
    128, pointer, 16384);

    pointer = pointer + 16384;

    if (status)
    {
        error_counter++;
        printf("Error in creating BSD packet pool\n!");
    }

    /* Create an IP instance for BSD. */
    status = nx_ip_create(&bsd_ip, "BSD IP Instance", IP_ADDRESS(1,2,3,4),
                        0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                        pointer, 2048, 1);
                        pointer = pointer + 2048;

    if (status)
    {
        error_counter++;
        printf("Error creating BSD IP instance\n!");
    }

    /* Enable ARP and supply ARP cache memory for BSD IP Instance */
    status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Check ARP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in enable ARP on BSD IP instance\n");
    }

    /* Enable TCP processing for BSD IP instances. */
    status = nx_tcp_enable(&bsd_ip);

    /* Check TCP enable status. */
    if (status)
    {
        error_counter++;
        printf("Error in Enable TCP \n");
    }

    /* Now initialize BSD Scoket Wrapper */
    status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 2);

    /* Check BSD initialize status. */
    if (status)
    {
        error_counter++;
        printf("Error in BSD initialize \n");
    }

    pointer = pointer + 2048;
}

/* Define the Server thread. */
CHAR     Server_Rcv_Buffer[100];

VOID     thread_server_entry(ULONG thread_input)
{

INT             status, sock, sock_tcp_server;
ULONG           actual_status;
INT             Clientlen;
INT             i;
UINT            is_set = NX_FALSE;
NXD_ADDRESS     ip_address;
struct          sockaddr_in6 serverAddr;
struct          sockaddr_in6 ClientAddr;
UINT            iface_index, address_index;

    status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE,
            &actual_status, 100);

    /* Check status... */
    if (status != NX_SUCCESS)
    {
        return;
    }

    /* Enable IPv6 */
    status = nxd_ipv6_enable(&bsd_ip);
    if((status != NX_SUCCESS) && (status != NX_ALREADY_ENABLED))
    {
        printf("Error with IPv6 enable 0x%x\n", status);
        return;
    }

    /* Enable ICMPv6 */
    status = nxd_icmp_enable(&bsd_ip);

    if(status)
    {
        printf("Error with ECMPv6 enable 0x%x\n", status);
        return;
    }

    /* Set the primary interface for our DNS IPv6 addresses. */
    iface_index = 0;

    /* This assumes we are using the primary network interface (index 0). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, NX_NULL, 10,
                                &address_index);

    if (status)
        return;

    /* Set ip_0 interface address. */
    ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    ip_address.nxd_ip_address.v6[0] = htonl(0x20010db8);
    ip_address.nxd_ip_address.v6[1] = htonl(0x0000f101);
    ip_address.nxd_ip_address.v6[2] = 0;
    ip_address.nxd_ip_address.v6[3] = htonl(0x101);

    /* Set the host global IP address. We are assuming a 64
    bit prefix here but this can be any value (< 128). */
    status = nxd_ipv6_address_set(&bsd_ip, iface_index, &ip_address, 64,
                                &address_index);

    if (status)
        return;

    /* Wait for IPv6 stack to finish DAD process. */
    tx_thread_sleep(400);

    /* Create BSD TCP Socket */
    sock_tcp_server = socket(AF_INET6, SOCK_STREAM, 0);

    if (sock_tcp_server == -1)
    {
        printf("\nError: BSD TCP Server socket create \n");
        return;
    }

    printf("\nBSD TCP Server socket created %lu \n", sock_tcp_server);

    /* Set the server port and IP address */
    memset(&serverAddr, 0, sizeof(serverAddr));
    serverAddr.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    serverAddr.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    serverAddr.sin6_addr._S6_un._S6_u32[2] = 0x0;
    serverAddr.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    serverAddr.sin6_port = htons(SERVER_PORT);
    serverAddr.sin6_family = AF_INET6;

    /* Bind this server socket */
    status = bind(sock_tcp_server, (struct sockaddr *) &serverAddr,
                    sizeof(serverAddr));

    if (status < 0)
    {
        printf("Error: Server Socket Bind \n");
        return;
    }

    FD_ZERO(&master_list);
    FD_ZERO(&read_ready);
    FD_SET(sock_tcp_server,&master_list);
    maxfd = sock_tcp_server;

    /* Now listen for any client connections for this server socket */
    status = listen(sock_tcp_server, 5);
    if (status < 0)
    {
        printf("Error: Server Socket Listen\n");
        return;
    }
    else
        printf("Server Listen complete\n");

    /* All set to accept client connections */
    printf("Now accepting client connections\n");

    /* Loop to create and establish server connections. */
    while(1)
    {

        printf("\n");

        read_ready = master_list;

        tx_thread_sleep(20); /* Allow some time to other threads too */

        /* Let the underlying TCP stack determine the timeout. */
        status = select(maxfd + 1, &read_ready, 0, 0, 0);

        if ( (status == 0xFFFFFFFF) || (status == 0) )
        {
            printf("Error with select? Status 0x%x. Try again\n", status);

            continue;
        }

        /* Detected a connection request. */
        is_set = FD_ISSET(sock_tcp_server,&read_ready);

        if(is_set)
        {

            Clientlen = sizeof(ClientAddr);

            sock = accept(sock_tcp_server,
            (struct sockaddr*)&ClientAddr,
            &Clientlen);

            /* Add this new connection to our master list */
            FD_SET(sock, &master_list);

            if ( sock \maxfd)
            {
                printf("New connection %d\n", sock);

                maxfd = sock;
            }

            continue;
        }

        /* Check the set of 'ready' sockets, e.g connected to remote host and
        waiting for notice of packets received. */
        for (i = NX_BSD_SOCKFD_START; i < (maxfd+1+NX_BSD_SOCKFD_START); i++)
        {

            if ((i != sock_tcp_server) &&
                (FD_ISSET(i, &master_list)) &&
                (FD_ISSET(i, &read_ready)))
            {

                while(1)
                {

                    status = recv(i, (VOID *)Server_Rcv_Buffer, 100, 0);

                    if (status == 0)
                    {
                        printf("(Server socket %d received no data from
                                Client)\n", i);

                        break;
                    }
                    else if (status == 0xFFFFFFFF)
                    {
                        printf("Error on Server socket %d receiving data from
                                Client\n", i);

                        break;
                    }

                    printf("Server socket %d received from Client %lu bytes:
                            %s\n ", i, (ULONG)status,
                            Server_Rcv_Buffer);

                    status = send(i, "Hello\n", sizeof("Hello\n"), 0);

                    if (status == ERROR)
                    {
                        printf("Error on Server socket %d sending data to
                                Client \n", i);
                    }
                    else
                    {
                        printf("Server socket %d message sent to Client:
                                Hello\n", i);
                    }
                }

                /* Close this socket */
                status = soc_close(i);

                if (status != ERROR)
                {
                    printf("Server socket %d closing\n", i);
                }
                else
                {

                    printf("Error on Server socket %d closing\n", i);
                }
            }
        }

        /* Loop back to check any next client connection */
    }
}

#define     CLIENT_BUFFER_SIZE 100
CHAR        Client_Rcv_Buffer[CLIENT_BUFFER_SIZE];

VOID        thread_client_entry(ULONG thread_input)
{

INT         status;
INT         sock_tcp_client, length;
struct      sockaddr_in6 echoServAddr6;
struct      sockaddr_in6 localAddr6; address */

    /* Wait for the server side to get set up, including the DAD process. */
    tx_thread_sleep(500);

    /* ICMPv6 and IPv6 should already be enabled on the IP instance
    by the server thread entry function. */

    /* Further the IPv6 address is already established with the IP instance.
    so no need to wait for DAD completion. */

    /* Set local port and IP address (used only for getsockname call). */
    memset(&localAddr6, 0, sizeof(localAddr6));
    localAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    localAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    localAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    localAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    localAddr6.sin6_port = htons(CLIENT_PORT);
    localAddr6.sin6_family = AF_INET6;

    /* Set Server port and IP address to connect to the TCP server. */
    memset(&echoServAddr6, 0, sizeof(echoServAddr6));
    echoServAddr6.sin6_addr._S6_un._S6_u32[0] = htonl(0x20010db8);
    echoServAddr6.sin6_addr._S6_un._S6_u32[1] = htonl(0xf101);
    echoServAddr6.sin6_addr._S6_un._S6_u32[2] = 0x0;
    echoServAddr6.sin6_addr._S6_un._S6_u32[3] = htonl(0x0101);
    echoServAddr6.sin6_port = htons(SERVER_PORT);
    echoServAddr6.sin6_family = AF_INET6;

    /* Now make client connections with the server. */
    while (1)
    {
        printf("\n");

        /* Create BSD TCP Socket */

        sock_tcp_client = socket(AF_INET6, SOCK_STREAM, 0);

        if (sock_tcp_client == -1)
        {
            printf("Error on Client socket %d create \n");
            return;
        }

        printf("Client socket %d created \n", sock_tcp_client);

        /* Now connect this client to the server */
        status = connect(sock_tcp_client, (struct sockaddr *)&echoServAddr6,
                sizeof(echoServAddr6));

        /* Check for error. */
        if (status != NX_SOC_OK)
        {
            printf("Error on Client socket %d connect\n");
            soc_close(sock_tcp_client);
            return;

        }

        /* Get and print source and destination information */
        printf("Client socket %d connected \n", sock_tcp_client);

        status = getsockname(sock_tcp_client, (struct sockaddr *)&localAddr6,
        &length);

        printf("Client port = %lu , Client = 0x%x 0x%x 0x%x 0x%x,",
                ntohs(localAddr6.sin6_port),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(localAddr6.sin6_addr._S6_un._S6_u32[3]));

        length = sizeof(struct sockaddr_in6);

        status = getpeername(sock_tcp_client, (struct sockaddr *)
                            &echoServAddr6, &length);

        printf("Remote port = %lu, Remote IP = 0x%x 0x%x 0x%x 0x%x \n",
                ntohs(echoServAddr6.sin6_port),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[0]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[1]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[2]),
                ntohl(echoServAddr6.sin6_addr._S6_un._S6_u32[3]));

        /* Now receive the echoed packet from the server */
        while(1)
        {

            printf("Client sock %d sending packet to server\n",
                sock_tcp_client);

            status = send(sock_tcp_client, "Hello", sizeof("Hello"), 0);

            if (status == NX_SOC_ERROR)
            {
                printf("Error on Client Socket (%d) send \n",
                        sock_tcp_client);
            }
            else
            {
                printf("Client socket %d sent message: Hello\n",
                        sock_tcp_client);
            }

            status = recv(sock_tcp_client, (VOID *)Client_Rcv_Buffer,
                        CLIENT_BUFFER_SIZE, 0);

            if (status <= 0)
            {

                if (status < 0)
                {
                    printf("Error on Client receiving on socket %d \n",
                            sock_tcp_client);
                }
                else
                {
                    printf("Client received no data on socket %d\n",
                            sock_tcp_client);
                }

            break;
            }
            else
            {
                printf("Client socket %d received %d bytes and this message:
                        %s\n", sock_tcp_client, status,
                        Client_Rcv_Buffer);
            }

        }

        /* close this client socket */
        status = oc_close(sock_tcp_client);

        if (status != NX_SOC_ERROR)
        {
            printf("Client Socket %d closed\n", sock_tcp_client);
        }
        else
        {
            printf("Error on Client Socket %d on close \n", sock_tcp_client);
        }

        /* Make another Client connection...*/

    }
}
```
