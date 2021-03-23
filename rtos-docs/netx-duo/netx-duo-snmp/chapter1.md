---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo SNMP
description: Implementacja SNMP NetX Duo to Agent SNMP. Agent jest odpowiedzialny za odpowiadanie na polecenia menedżera SNMP i wysyłanie pułapek opartych na zdarzeniach.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821685"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a><span data-ttu-id="45b8c-104">Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-104">Chapter 1 - Introduction to Azure RTOS NetX Duo SNMP</span></span>

<span data-ttu-id="45b8c-105">Simple Network Management Protocol (SNMP) to protokół przeznaczony do zarządzania urządzeniami w Internecie.</span><span class="sxs-lookup"><span data-stu-id="45b8c-105">The Simple Network Management Protocol (SNMP) is a protocol designed for managing devices on the internet.</span></span> <span data-ttu-id="45b8c-106">SNMP to protokół, który używa usług UDP (Unported User Datagram Protocol) do wykonywania funkcji zarządzania.</span><span class="sxs-lookup"><span data-stu-id="45b8c-106">SNMP is a protocol that utilizes the connectionless User Datagram Protocol (UDP) services to perform its management function.</span></span> <span data-ttu-id="45b8c-107">Implementacja protokołu SNMP platformy Azure RTO NetX Duo to Agent SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-107">The Azure RTOS NetX Duo SNMP implementation is that of an SNMP Agent.</span></span> <span data-ttu-id="45b8c-108">Agent jest odpowiedzialny za odpowiadanie na polecenia menedżera SNMP i wysyłanie pułapek opartych na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="45b8c-108">An agent is responsible for responding to SNMP Manager’s commands and sending event driven traps.</span></span> 

<span data-ttu-id="45b8c-109">NetX Duo SNMP obsługuje komunikację między protokołami IPv4 i IPv6 z menedżerami SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-109">NetX Duo SNMP supports both IPv4 and IPv6 communication with SNMP Managers.</span></span> <span data-ttu-id="45b8c-110">NetX aplikacje SNMP powinny kompilować i uruchamiać w NetX Duo SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-110">NetX SNMP applications should compile and run in NetX Duo SNMP.</span></span> <span data-ttu-id="45b8c-111">Jednak deweloperzy są zachęcani do portów istniejących aplikacji SNMP do korzystania z równoważnych usług "Duo".</span><span class="sxs-lookup"><span data-stu-id="45b8c-111">However, the developer is encouraged to port existing SNMP applications to using the equivalent “duo” services.</span></span> <span data-ttu-id="45b8c-112">Na przykład podczas wysyłania komunikatów pułapki SNMP następujące usługi "Duo" powinny zastąpić swój odpowiednik NetX:</span><span class="sxs-lookup"><span data-stu-id="45b8c-112">For example, when sending SNMP trap messages, the following ‘duo’ services should replace their NetX equivalent:</span></span>

<span data-ttu-id="45b8c-113">*nxd_snmp_object_trap_send*</span><span class="sxs-lookup"><span data-stu-id="45b8c-113">*nxd_snmp_object_trap_send*</span></span>

<span data-ttu-id="45b8c-114">*nxd_snmp_object_trapv2_send*</span><span class="sxs-lookup"><span data-stu-id="45b8c-114">*nxd_snmp_object_trapv2_send*</span></span>

<span data-ttu-id="45b8c-115">*nxd_snmp_object_trapv3_send*</span><span class="sxs-lookup"><span data-stu-id="45b8c-115">*nxd_snmp_object_trapv3_send*</span></span>

<span data-ttu-id="45b8c-116">Aby uzyskać więcej informacji, zobacz **Opis usług agenta SNMP** w innym miejscu w tym przewodniku użytkownika, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="45b8c-116">For more details, see **Description of SNMP Agent Services** elsewhere in this User Guide for more details.</span></span>

## <a name="netx-duo-snmp-agent-requirements"></a><span data-ttu-id="45b8c-117">Wymagania dotyczące agenta SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="45b8c-117">NetX Duo SNMP Agent Requirements</span></span>

<span data-ttu-id="45b8c-118">Pakiet SNMP NetX Duo wymaga, aby wystąpienie adresu IP zostało już utworzone.</span><span class="sxs-lookup"><span data-stu-id="45b8c-118">The NetX Duo SNMP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="45b8c-119">Ponadto należy włączyć protokół UDP dla tego samego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-119">In addition, UDP must be enabled on that same IP instance.</span></span>

<span data-ttu-id="45b8c-120">Agent SNMP NetX Duo ma kilka dodatkowych wymagań.</span><span class="sxs-lookup"><span data-stu-id="45b8c-120">The NetX Duo SNMP Agent has several additional requirements.</span></span> <span data-ttu-id="45b8c-121">Najpierw wymaga dostępu do portu 161 do obsługi wszystkich żądań menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-121">First, it requires access to port 161 for handling all SNMP manager requests.</span></span> <span data-ttu-id="45b8c-122">Wymaga również dostępu do portu 162 do wysyłania komunikatów pułapki do Menedżera.</span><span class="sxs-lookup"><span data-stu-id="45b8c-122">It also requires access to port 162 for sending trap messages to the Manager.</span></span>

<span data-ttu-id="45b8c-123">Aby można było użyć agenta SNMP NetX Duo z użyciem protokołu IPv6 i uzyskać obiektów IPv6, należy włączyć protokół IPv6 w NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="45b8c-123">To use NetX Duo SNMP Agent with over IPv6 and to obtain IPv6 objects, IPv6 must be enabled in NetX Duo.</span></span> <span data-ttu-id="45b8c-124">Szczegółowe informacje na temat włączania wystąpienia protokołu IP dla usług IPv6 można znaleźć w ***podręczniku użytkownika NetX Duo*** .</span><span class="sxs-lookup"><span data-stu-id="45b8c-124">See the ***NetX Duo User Guide*** for details on enabling the IP instance for IPv6 services.</span></span>

## <a name="netx-duo-snmp-constraints"></a><span data-ttu-id="45b8c-125">Ograniczenia SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="45b8c-125">NetX Duo SNMP Constraints</span></span>

<span data-ttu-id="45b8c-126">Protokół SNMP NetX Duo implementuje SNMP w wersji 1, 2 i 3.</span><span class="sxs-lookup"><span data-stu-id="45b8c-126">The NetX Duo SNMP protocol implements SNMP Version 1, 2, and 3.</span></span> <span data-ttu-id="45b8c-127">Implementacja SNMPv3 obsługuje uwierzytelnianie MD5 i SHA oraz szyfrowanie DES.</span><span class="sxs-lookup"><span data-stu-id="45b8c-127">The SNMPv3 implementation supports MD5 and SHA authentication, and DES encryption.</span></span> <span data-ttu-id="45b8c-128">Ta wersja agenta SNMP NetX Duo ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="45b8c-128">This version of the NetX Duo SNMP Agent has the following constraints:</span></span>

1. <span data-ttu-id="45b8c-129">Jeden Agent SNMP na wystąpienie NetX IP</span><span class="sxs-lookup"><span data-stu-id="45b8c-129">One SNMP Agent per NetX IP Instance</span></span>
2. <span data-ttu-id="45b8c-130">Brak obsługi dla RMON</span><span class="sxs-lookup"><span data-stu-id="45b8c-130">No support for RMON</span></span>
3. <span data-ttu-id="45b8c-131">Komunikaty INFORM protokołu SNMP V3 nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="45b8c-131">SNMP v3 Inform messages are not supported</span></span>
4. <span data-ttu-id="45b8c-132">Typy danych nieprzezroczystych i NSAP nie są obsługiwane</span><span class="sxs-lookup"><span data-stu-id="45b8c-132">OPAQUE and NSAP data types are not supported</span></span>
5. <span data-ttu-id="45b8c-133">Adresy IPv6 są zdefiniowane jako ciągi oktetowe, a sprawdzanie formatu jest pozostawione do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45b8c-133">IPv6 addresses are defined as octet strings, and format checking is left to the application.</span></span>

## <a name="snmp-object-names"></a><span data-ttu-id="45b8c-134">Nazwy obiektów SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-134">SNMP Object Names</span></span>

<span data-ttu-id="45b8c-135">Protokół SNMP jest przeznaczony do zarządzania urządzeniami w Internecie.</span><span class="sxs-lookup"><span data-stu-id="45b8c-135">The SNMP protocol is designed to manage devices on the internet.</span></span> <span data-ttu-id="45b8c-136">W tym celu każde urządzenie zarządzane przez protokół SNMP ma zestaw obiektów, które są zdefiniowane przez strukturę informacji o zarządzaniu (SMI) zgodnie z definicją w dokumencie RFC 1155.</span><span class="sxs-lookup"><span data-stu-id="45b8c-136">To accomplish this, each SNMP managed device has a set of objects that are defined by the Structure of Management Information (SMI) as defined by RFC 1155.</span></span> <span data-ttu-id="45b8c-137">Struktura jest hierarchicznym typem drzewa struktury, która wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="45b8c-137">The structure is a hierarchical tree type of structure that looks like the following:</span></span>

![Diagram struktury informacji o zarządzaniu.](media/image3.png)

<span data-ttu-id="45b8c-139">Każdy węzeł drzewa jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="45b8c-139">Each node in the tree is an object.</span></span> <span data-ttu-id="45b8c-140">Obiekt "dod" w drzewie jest identyfikowany przez notację 1.3.6, podczas gdy obiekt "Internet" w drzewie jest identyfikowany przez notację 1.3.6.1.</span><span class="sxs-lookup"><span data-stu-id="45b8c-140">The “dod” object in the tree is identified by the notation 1.3.6, while the “internet” object in the tree is identified by the notation 1.3.6.1.</span></span> <span data-ttu-id="45b8c-141">Wszystkie nazwy obiektów SNMP zaczynają się od notacji 1.3.6.</span><span class="sxs-lookup"><span data-stu-id="45b8c-141">All SNMP object names begin with the notation 1.3.6.</span></span>

<span data-ttu-id="45b8c-142">Menedżer SNMP używa tej notacji obiektu, aby określić obiekt na urządzeniu, który ma zostać pobrany lub ustawiony.</span><span class="sxs-lookup"><span data-stu-id="45b8c-142">An SNMP Manager uses this object notation to specify what object in the device it wishes to get or set.</span></span> <span data-ttu-id="45b8c-143">Agent SNMP NetX Duo interpretuje takie żądania Menedżera i udostępnia mechanizmy dla aplikacji, aby wykonać żądaną operację.</span><span class="sxs-lookup"><span data-stu-id="45b8c-143">The NetX Duo SNMP Agent interprets such manager requests and provides mechanisms for the application to perform the requested operation.</span></span>

## <a name="snmp-manager-requests"></a><span data-ttu-id="45b8c-144">Żądania menedżera SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-144">SNMP Manager Requests</span></span>

<span data-ttu-id="45b8c-145">Protokół SNMP ma prosty mechanizm zarządzania urządzeniami.</span><span class="sxs-lookup"><span data-stu-id="45b8c-145">The SNMP has a simple mechanism for managing devices.</span></span> <span data-ttu-id="45b8c-146">Istnieje zestaw standardowych poleceń SNMP, które są wydawane przez menedżera SNMP na urządzeniu SNMP na *porcie 161*.</span><span class="sxs-lookup"><span data-stu-id="45b8c-146">There is a set of standard SNMP commands that are issued by the SNMP Manager to the SNMP device on *port 161*.</span></span> <span data-ttu-id="45b8c-147">Poniżej przedstawiono niektóre z podstawowych poleceń Menedżera SNMP:</span><span class="sxs-lookup"><span data-stu-id="45b8c-147">The following shows some of the basic SNMP Manager commands:</span></span>

| <span data-ttu-id="45b8c-148">SNMP — polecenie</span><span class="sxs-lookup"><span data-stu-id="45b8c-148">SNMP Command</span></span> | <span data-ttu-id="45b8c-149">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="45b8c-149">Meaning</span></span>                                                        |
|--------------|----------------------------------------------------------------|
| <span data-ttu-id="45b8c-150">GET</span><span class="sxs-lookup"><span data-stu-id="45b8c-150">GET</span></span>          | <span data-ttu-id="45b8c-151">*Pobierz określony obiekt*</span><span class="sxs-lookup"><span data-stu-id="45b8c-151">*Get the specified object*</span></span>                                       |
| <span data-ttu-id="45b8c-152">GETNEXT</span><span class="sxs-lookup"><span data-stu-id="45b8c-152">GETNEXT</span></span>      | <span data-ttu-id="45b8c-153">*Pobierz następny obiekt logiczny po określonym IDENTYFIKATORze obiektu*</span><span class="sxs-lookup"><span data-stu-id="45b8c-153">*Get the next logical object after the specified object ID*</span></span>      |
| <span data-ttu-id="45b8c-154">GetBulk</span><span class="sxs-lookup"><span data-stu-id="45b8c-154">GETBULK</span></span>      | <span data-ttu-id="45b8c-155">*Pobierz wiele obiektów logicznych po określonym IDENTYFIKATORze obiektu*</span><span class="sxs-lookup"><span data-stu-id="45b8c-155">*Get the multiple logical objects after the specified object ID*</span></span> |
| <span data-ttu-id="45b8c-156">SET</span><span class="sxs-lookup"><span data-stu-id="45b8c-156">SET</span></span>          | <span data-ttu-id="45b8c-157">*Ustaw określony obiekt*</span><span class="sxs-lookup"><span data-stu-id="45b8c-157">*Set the specified object*</span></span>                                       |

<span data-ttu-id="45b8c-158">Te polecenia są zakodowane w formacie składni abstrakcyjnej (ASN. 1) i znajdują się w ładunku pakietu UDP wysyłanego przez menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-158">These commands are encoded in the Abstract Syntax Notation One (ASN.1) format and reside in the payload of the UDP packet sent by the SNMP Manager.</span></span> <span data-ttu-id="45b8c-159">Agent SNMP NetX Duo przetwarza żądanie, a następnie wywołuje odpowiadającą procedurę obsługi określoną w wywołaniu ***nx_snmp_agent_create*** .</span><span class="sxs-lookup"><span data-stu-id="45b8c-159">The NetX Duo SNMP Agent processes the request and then calls the corresponding handling routine specified in the ***nx_snmp_agent_create*** call.</span></span>

## <a name="netx-duo-snmp-agent-traps"></a><span data-ttu-id="45b8c-160">Pułapki agenta SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="45b8c-160">NetX Duo SNMP Agent Traps</span></span>

<span data-ttu-id="45b8c-161">Agent SNMP NetX Duo umożliwia także asynchroniczne powiadamianie menedżera SNMP o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="45b8c-161">The NetX Duo SNMP Agent provides the ability to also alert an SNMP Manager of events asynchronously.</span></span> <span data-ttu-id="45b8c-162">Jest to realizowane za pośrednictwem polecenia SNMP TRAP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-162">This is done via an SNMP trap command.</span></span> <span data-ttu-id="45b8c-163">Istnieje unikatowy interfejs API dla każdej wersji protokołu SNMP do wysyłania pułapek do menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-163">There is a unique API for each version of SNMP for sending traps to an SNMP Manager.</span></span> <span data-ttu-id="45b8c-164">Domyślnie pułapki są wysyłane do menedżera SNMP na porcie 162.</span><span class="sxs-lookup"><span data-stu-id="45b8c-164">By default, the traps are sent to the SNMP Manager on port 162.</span></span>

<span data-ttu-id="45b8c-165">Agent SNMP NetX Duo udostępnia oddzielne klucze zabezpieczeń dla komunikatów pułapki SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="45b8c-165">The NetX Duo SNMP Agent provides separate security keys for SNMPv3 trap messages.</span></span> <span data-ttu-id="45b8c-166">W tym celu aplikacja SNMP musi utworzyć oddzielny zestaw kluczy od tych stosowanych do odpowiedzi na żądania Menedżera.</span><span class="sxs-lookup"><span data-stu-id="45b8c-166">To do so, the SNMP application must create a separate set of keys from those applied to responses to Manager requests.</span></span> <span data-ttu-id="45b8c-167">Zabezpieczenia pułapek umożliwiają agentowi SNMP używanie tych samych lub różnych haseł na potrzeby uwierzytelniania i prywatności.</span><span class="sxs-lookup"><span data-stu-id="45b8c-167">Trap security enables the SNMP Agent to use the same or different passwords for authentication and privacy.</span></span> <span data-ttu-id="45b8c-168">Aby uzyskać więcej informacji na temat tworzenia kluczy zabezpieczeń, zobacz **NetX Duo — uwierzytelnianie i szyfrowanie SNMP** w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="45b8c-168">For more information on creating security keys, see **NetX Duo SNMP Authentication and Encryption** in the next section.</span></span>

<span data-ttu-id="45b8c-169">Lista standardowych zmiennych pułapek SNMP jest wyliczana w górnej części *nxd_snmp. h:*</span><span class="sxs-lookup"><span data-stu-id="45b8c-169">A list of standard SNMP trap variables is enumerated at the top of *nxd_snmp.h:*</span></span>

| <span data-ttu-id="45b8c-170">Zmienne</span><span class="sxs-lookup"><span data-stu-id="45b8c-170">Variables</span></span>                                 | <span data-ttu-id="45b8c-171">Wartość</span><span class="sxs-lookup"><span data-stu-id="45b8c-171">Value</span></span>  |
|-------------------------------------------|---|
| <span data-ttu-id="45b8c-172">#define NX_SNMP_TRAP_COLDSTART</span><span class="sxs-lookup"><span data-stu-id="45b8c-172">#define NX_SNMP_TRAP_COLDSTART</span></span>            | <span data-ttu-id="45b8c-173">0</span><span class="sxs-lookup"><span data-stu-id="45b8c-173">0</span></span> |
| <span data-ttu-id="45b8c-174">#define NX_SNMP_TRAP_WARMSTART</span><span class="sxs-lookup"><span data-stu-id="45b8c-174">#define NX_SNMP_TRAP_WARMSTART</span></span>            | <span data-ttu-id="45b8c-175">1</span><span class="sxs-lookup"><span data-stu-id="45b8c-175">1</span></span> |
| <span data-ttu-id="45b8c-176">#define NX_SNMP_TRAP_LINKDOWN</span><span class="sxs-lookup"><span data-stu-id="45b8c-176">#define NX_SNMP_TRAP_LINKDOWN</span></span>             | <span data-ttu-id="45b8c-177">2</span><span class="sxs-lookup"><span data-stu-id="45b8c-177">2</span></span> |
| <span data-ttu-id="45b8c-178">#define NX_SNMP_TRAP_LINKUP</span><span class="sxs-lookup"><span data-stu-id="45b8c-178">#define NX_SNMP_TRAP_LINKUP</span></span>               | <span data-ttu-id="45b8c-179">3</span><span class="sxs-lookup"><span data-stu-id="45b8c-179">3</span></span> |
| <span data-ttu-id="45b8c-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span><span class="sxs-lookup"><span data-stu-id="45b8c-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span></span> | <span data-ttu-id="45b8c-181">4</span><span class="sxs-lookup"><span data-stu-id="45b8c-181">4</span></span> |
| <span data-ttu-id="45b8c-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span><span class="sxs-lookup"><span data-stu-id="45b8c-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span></span>      | <span data-ttu-id="45b8c-183">5</span><span class="sxs-lookup"><span data-stu-id="45b8c-183">5</span></span> |
| <span data-ttu-id="45b8c-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span><span class="sxs-lookup"><span data-stu-id="45b8c-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span></span>   | <span data-ttu-id="45b8c-185">6</span><span class="sxs-lookup"><span data-stu-id="45b8c-185">6</span></span> |

<span data-ttu-id="45b8c-186">Aby uwzględnić te zmienne w komunikacie pułapki, trap_type argument wejściowy w *nx_snmp_agent_trapv2_send* (SNMPv2) lub *nx_snmp_agent_trapv3_send* (SNMPv3) jest ustawiony na wartość wyliczaną tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="45b8c-186">To include these variables in the trap message, the trap_type input argument in *nx_snmp_agent_trapv2_send* (SNMPv2) or *nx_snmp_agent_trapv3_send* (SNMPv3) is set to the enumerated value of these variables.</span></span> <span data-ttu-id="45b8c-187">Poniżej przedstawiono przykład dla protokołu SNMPv2 do powiadamiania menedżera SNMP o zimnym zdarzeniu uruchamiania:</span><span class="sxs-lookup"><span data-stu-id="45b8c-187">An example is shown below for SNMPv2 to notify the SNMP Manager of a cold start event:</span></span>

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

<span data-ttu-id="45b8c-188">Aby uwzględnić zmienne zastrzeżone w komunikacie pułapki, trap_type argument wejściowy jest ustawiony na NX_SNMP_TRAP_CUSTOM, a argument wejściowy listy pułapek zawiera dane zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="45b8c-188">To include proprietary variables in the trap message, the trap_type input argument is set to NX_SNMP_TRAP_CUSTOM and the trap list input argument contains the proprietary data.</span></span> <span data-ttu-id="45b8c-189">Należy pamiętać, że komunikat pułapki będzie zawierał jako czas systemowy (1.3.6.1.6.3.1.1.4.1.0).</span><span class="sxs-lookup"><span data-stu-id="45b8c-189">Note that the trap message will contain as the system up time (1.3.6.1.6.3.1.1.4.1.0).</span></span> <span data-ttu-id="45b8c-190">Poniżej przedstawiono przykład dla SNMPv2:</span><span class="sxs-lookup"><span data-stu-id="45b8c-190">An example is shown below for SNMPv2:</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a><span data-ttu-id="45b8c-191">NetX Duo — uwierzytelnianie i szyfrowanie SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-191">NetX Duo SNMP Authentication and Encryption</span></span>

<span data-ttu-id="45b8c-192">Istnieją dwa typy uwierzytelniania, czyli *podstawowe* i *szyfrowane*.</span><span class="sxs-lookup"><span data-stu-id="45b8c-192">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="45b8c-193">Uwierzytelnianie podstawowe jest równoznaczne z prostym uwierzytelnianiem zwykłego *tekstu w* wielu protokołach.</span><span class="sxs-lookup"><span data-stu-id="45b8c-193">Basic authentication is equivalent to a simple plain text *username* authentication found in many protocols.</span></span> <span data-ttu-id="45b8c-194">W podstawowym uwierzytelnianiu SNMP użytkownik po prostu weryfikuje, czy podana nazwa użytkownika jest prawidłowa do wykonywania operacji SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-194">In SNMP basic authentication, the user simply verifies that the supplied username is valid for performing SNMP operations.</span></span> <span data-ttu-id="45b8c-195">Uwierzytelnianie podstawowe jest jedyną opcją dla SNMP w wersji 1 i 2.</span><span class="sxs-lookup"><span data-stu-id="45b8c-195">Basic authentication is the only option for SNMP versions 1 and 2.</span></span>

<span data-ttu-id="45b8c-196">Główną wadą uwierzytelniania podstawowego jest nazwa użytkownika, która jest przesyłana w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-196">The main disadvantage of basic authentication is the username is transmitted in plain text.</span></span> <span data-ttu-id="45b8c-197">Uwierzytelnianie Digest szyfrowanego rozwiązuje ten problem przez nigdy nie przesyłaj nazwy użytkownika w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-197">The SNMPv3 digest authentication addresses this problem by never transmitting the username in plain text.</span></span> <span data-ttu-id="45b8c-198">Zamiast tego algorytm jest używany do wygenerowania 96-bitowego elementu "Digest" z nazwy użytkownika, aparatu kontekstu i innych informacji.</span><span class="sxs-lookup"><span data-stu-id="45b8c-198">Instead, an algorithm is used to derive a 96-bit ‘digest’ from the username, context engine, and other information.</span></span> <span data-ttu-id="45b8c-199">Agent SNMP NetX Duo obsługuje algorytmy szyfrowane MD5 i SHA.</span><span class="sxs-lookup"><span data-stu-id="45b8c-199">The NetX Duo SNMP Agent supports both MD5 and SHA digest algorithms.</span></span>

<span data-ttu-id="45b8c-200">Aby włączyć uwierzytelnianie, Agent SNMP musi ustawić jego identyfikator aparatu kontekstu przy użyciu usługi *nx_snmp_agent_context_engine_set* .</span><span class="sxs-lookup"><span data-stu-id="45b8c-200">To enable authentication, the SNMP Agent must set its Context Engine ID using the *nx_snmp_agent_context_engine_set* service.</span></span> <span data-ttu-id="45b8c-201">Identyfikator aparatu kontekstu jest używany podczas tworzenia klucza uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="45b8c-201">The Context Engine ID is used in the creation of the authentication key.</span></span>

<span data-ttu-id="45b8c-202">Szyfrowanie danych SNMPv3 jest dostępne przy użyciu algorytmu DES.</span><span class="sxs-lookup"><span data-stu-id="45b8c-202">Encryption of SNMPv3 data is available using the DES algorithm.</span></span> <span data-ttu-id="45b8c-203">Szyfrowanie wymaga włączenia uwierzytelniania (jeden nie może szyfrować danych bez ustawiania parametrów uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="45b8c-203">Encryption requires that authentication be enabled (one cannot encrypt data without setting the authentication parameters).</span></span>

<span data-ttu-id="45b8c-204">Do utworzenia kluczy uwierzytelniania i prywatności są używane następujące interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="45b8c-204">To create authentication and privacy keys, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

<span data-ttu-id="45b8c-205">Następnie Agent SNMP musi być skonfigurowany do korzystania z tych kluczy.</span><span class="sxs-lookup"><span data-stu-id="45b8c-205">Next, the SNMP agent must be configured to use these keys.</span></span> <span data-ttu-id="45b8c-206">Aby zarejestrować klucz za pomocą agenta SNMP, są używane następujące interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="45b8c-206">To register a key with the SNMP agent, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="45b8c-207">Osobne klucze można utworzyć dla komunikatów pułapki.</span><span class="sxs-lookup"><span data-stu-id="45b8c-207">Separate keys can be created for trap messages.</span></span> <span data-ttu-id="45b8c-208">Aby zastosować klucze dla komunikatów pułapki, dostępne są następujące interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="45b8c-208">To apply keys for trap messages the following API are available:</span></span>

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="45b8c-209">Aby wyłączyć uwierzytelnianie lub szyfrowanie dla komunikatów odpowiedzi i wysyłania pułapek, Użyj tych usług z wartością wejściową wskaźnika klucza ustawioną na wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="45b8c-209">To disable authentication or encryption for response messages and sending traps, use these services with the key pointer input set to NULL.</span></span>

## <a name="netx-duo-snmp-community-strings"></a><span data-ttu-id="45b8c-210">NetX Duo — ciągi społeczności SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-210">NetX Duo SNMP Community Strings</span></span>

<span data-ttu-id="45b8c-211">Agent SNMP NetX Duo obsługuje zarówno publiczne, jak i prywatne ciągi społeczności.</span><span class="sxs-lookup"><span data-stu-id="45b8c-211">The NetX Duo SNMP Agent supports both public and private community strings.</span></span> <span data-ttu-id="45b8c-212">Ciąg publiczny jest ustawiany za pomocą usługi *_public_string_set nx_snmp_agent* .</span><span class="sxs-lookup"><span data-stu-id="45b8c-212">The public string is set with the *nx_snmp_agent _public_string_set* service.</span></span> <span data-ttu-id="45b8c-213">Prywatny ciąg agenta SNMP NetX Duo jest ustawiany przy użyciu usługi *nx_snmp_agent_private_string_set* .</span><span class="sxs-lookup"><span data-stu-id="45b8c-213">The NetX Duo SNMP Agent private string is set using the *nx_snmp_agent_private_string_set* service.</span></span>

## <a name="netx-duo-snmp-username-callback"></a><span data-ttu-id="45b8c-214">Wywołanie zwrotne SNMP nazwy użytkownika NetX Duo</span><span class="sxs-lookup"><span data-stu-id="45b8c-214">NetX Duo SNMP Username Callback</span></span>

<span data-ttu-id="45b8c-215">Pakiet agenta SNMP NetX Duo umożliwia aplikacji określenie (za pośrednictwem wywołania ***nx_snmp_agent_create*** ) wywołania zwrotnego nazwy użytkownika, która jest wywoływana na początku obsługi poszczególnych żądań klienta SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-215">The NetX Duo SNMP Agent package allows the application to specify (via the ***nx_snmp_agent_create*** call) a username callback  that is called at the beginning of handling each SNMP Client request.</span></span>

<span data-ttu-id="45b8c-216">Procedura wywołania zwrotnego zapewnia agentowi SNMP NetX Duo o nazwie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="45b8c-216">The callback routine provides the NetX Duo SNMP Agent with the username.</span></span> <span data-ttu-id="45b8c-217">Jeśli podana nazwa użytkownika jest prawidłowa lub w przypadku odpowiedzi na żądanie nie jest wymagane sprawdzanie nazwy użytkownika, wywołanie zwrotne nazwy użytkownika powinna zwracać wartość **NX_SUCCESS**.</span><span class="sxs-lookup"><span data-stu-id="45b8c-217">If the supplied username is valid or if no username check is necessary for the responding to the request, the username callback should return the value of **NX_SUCCESS**.</span></span> <span data-ttu-id="45b8c-218">W przeciwnym razie procedura powinna zwracać **NX_SNMP_ERROR** , aby wskazać, że określona nazwa użytkownika jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="45b8c-218">Otherwise, the routine should return **NX_SNMP_ERROR** to indicate the specified username is invalid.</span></span>

<span data-ttu-id="45b8c-219">Format procedury wywołania zwrotnego nazwy użytkownika aplikacji został zdefiniowany poniżej:</span><span class="sxs-lookup"><span data-stu-id="45b8c-219">The format of the application username callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

<span data-ttu-id="45b8c-220">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="45b8c-220">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="45b8c-221">Parametr</span><span class="sxs-lookup"><span data-stu-id="45b8c-221">Parameter</span></span> | <span data-ttu-id="45b8c-222">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="45b8c-222">Meaning</span></span>                                              |
|-----------|------------------------------------------------------|
| <span data-ttu-id="45b8c-223">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="45b8c-223">*agent_ptr*</span></span> | <span data-ttu-id="45b8c-224">Wskaźnik do wywoływania agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-224">Pointer to calling SNMP agent</span></span>                        |
| <span data-ttu-id="45b8c-225">nazwa użytkownika</span><span class="sxs-lookup"><span data-stu-id="45b8c-225">username</span></span>  | <span data-ttu-id="45b8c-226">Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika</span><span class="sxs-lookup"><span data-stu-id="45b8c-226">Destination for the pointer to the required username</span></span> |

<span data-ttu-id="45b8c-227">W przypadku sesji SNMPv1 i SNMPv2/v2C aplikacja będzie chciała sprawdzić ciąg identyfikacyjny w przychodzącym żądaniu SNMP, aby określić, czy żądanie SNMP ma prawidłowy ciąg identyfikacyjny.</span><span class="sxs-lookup"><span data-stu-id="45b8c-227">For SNMPv1 and SNMPv2/v2C sessions, the application will want to examine the community string on an incoming SNMP request to determine if the SNMP request has a valid community string.</span></span> <span data-ttu-id="45b8c-228">Istnieje kilka usług dla aplikacji SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-228">There are several services for the SNMP application to do this.</span></span>

<span data-ttu-id="45b8c-229">Aplikacja SNMP może dowiedzieć się, czy bieżące żądanie menedżera SNMP jest GET (np. GET, GetNext lub GetBulk) lub typu żądania przy użyciu tej usługi:</span><span class="sxs-lookup"><span data-stu-id="45b8c-229">The SNMP application can inquire if the current SNMP Manager request is a GET (e.g. GET, GETNEXT, or GETBULK) or SET type of request using this service:</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

<span data-ttu-id="45b8c-230">Jeśli żądanie jest typu GET, aplikacja będzie chcieć porównać wejściowy ciąg identyfikacyjny z publicznym ciągiem agenta SNMP:</span><span class="sxs-lookup"><span data-stu-id="45b8c-230">If the request is a GET type, the application will want to compare the input community string to the SNMP Agent’s public string:</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

<span data-ttu-id="45b8c-231">Podobnie jeśli żądanie jest typem zestawu, aplikacja będzie chcieć porównać wejściowy ciąg identyfikacyjny z prywatnym ciągiem agenta SNMP:</span><span class="sxs-lookup"><span data-stu-id="45b8c-231">Similarly if the request is a SET type, the application will want to compare the input community string to the SNMP Agent’s private string:</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

<span data-ttu-id="45b8c-232">Is_public i is_private wartości zwracane wskazują odpowiednio, jeśli wejściowy ciąg identyfikacyjny jest prawidłowym publicznym lub prywatnym ciągiem społeczności.</span><span class="sxs-lookup"><span data-stu-id="45b8c-232">The is_public and is_private return values indicate respectively if the input community string is a valid public or private community string.</span></span>

<span data-ttu-id="45b8c-233">Zwracana wartość procedury wywołania zwrotnego username wskazuje, czy nazwa użytkownika jest prawidłowa.</span><span class="sxs-lookup"><span data-stu-id="45b8c-233">The return value of the username callback routine indicates if the username is valid.</span></span> <span data-ttu-id="45b8c-234">Wartość **NX_SUCCESS** jest zwracana, jeśli nazwa użytkownika jest prawidłowa, lub **NX_SNMP_ERROR** , jeśli nazwa użytkownika jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="45b8c-234">The value **NX_SUCCESS** is returned if the username is valid, or **NX_SNMP_ERROR** if the username is invalid.</span></span>

## <a name="netx-duo-snmp-agent-get-callback"></a><span data-ttu-id="45b8c-235">Wywołanie zwrotne agenta SNMP NetX Duo</span><span class="sxs-lookup"><span data-stu-id="45b8c-235">NetX Duo SNMP Agent GET Callback</span></span>

<span data-ttu-id="45b8c-236">Aplikacja musi ustawić procedurę wywołania zwrotnego dla obsługi żądań GET Object z menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-236">The application must set a callback routine for handling GET object requests from the SNMP Manager.</span></span> <span data-ttu-id="45b8c-237">Wywołanie zwrotne Pobiera wartość obiektu określonego w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-237">The callback retrieves the value of the object specified in the request.</span></span>

<span data-ttu-id="45b8c-238">Procedura wywołania zwrotnego żądania GET aplikacji została zdefiniowana poniżej:</span><span class="sxs-lookup"><span data-stu-id="45b8c-238">The application GET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="45b8c-239">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="45b8c-239">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="45b8c-240">Parametr</span><span class="sxs-lookup"><span data-stu-id="45b8c-240">Parameter</span></span>        | <span data-ttu-id="45b8c-241">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="45b8c-241">Meaning</span></span> |
|------------------|----------------------------------|
| <span data-ttu-id="45b8c-242">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="45b8c-242">*agent_ptr*</span></span>        | <span data-ttu-id="45b8c-243">Wskaźnik do wywoływania agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-243">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="45b8c-244">object_requested</span><span class="sxs-lookup"><span data-stu-id="45b8c-244">object_requested</span></span> | <span data-ttu-id="45b8c-245">Ciąg ASCII reprezentujący identyfikator obiektu dla operacji pobierania.</span><span class="sxs-lookup"><span data-stu-id="45b8c-245">ASCII string representing the object ID the GET operation is for.</span></span> |
| <span data-ttu-id="45b8c-246">object_data</span><span class="sxs-lookup"><span data-stu-id="45b8c-246">object_data</span></span>      | <span data-ttu-id="45b8c-247">Struktura danych do przechowywania wartości pobranej przez wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="45b8c-247">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="45b8c-248">Można to ustawić przy użyciu serii interfejsu API SNMP NetX Duo opisanej poniżej.</span><span class="sxs-lookup"><span data-stu-id="45b8c-248">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

> [!NOTE]
> <span data-ttu-id="45b8c-249">*W przypadku ciągów oktetowych obiekt musi mieć przypisaną długość, tak aby wewnętrzna funkcja wiedziała, jak długo długość jest równa, ponieważ wywołanie zwrotne nie ma argumentu length:*</span><span class="sxs-lookup"><span data-stu-id="45b8c-249">*For octet strings, the object must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:*</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="45b8c-250">Ponieważ typ danych nie jest znany w wywołaniu wywołania zwrotnego, nie trzeba sprawdzać typu danych.</span><span class="sxs-lookup"><span data-stu-id="45b8c-250">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="45b8c-251">Długość nie będzie miała wpływu na typy liczbowe ani ciągi o wartości null.</span><span class="sxs-lookup"><span data-stu-id="45b8c-251">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="45b8c-252">Następnie wywołaj funkcję wewnętrzną:</span><span class="sxs-lookup"><span data-stu-id="45b8c-252">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="45b8c-253">Jeśli funkcja wywołania zwrotnego nie może odnaleźć żądanego obiektu, należy zwrócić **NX_SNMP_ERROR_NOSUCHNAME** kod błędu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-253">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="45b8c-254">W przypadku wykrycia innego błędu należy zwrócić **NX_SNMP_ERROR** .</span><span class="sxs-lookup"><span data-stu-id="45b8c-254">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-getnext-callback"></a><span data-ttu-id="45b8c-255">NetX Duo — Agent SNMP-następne wywołanie zwrotne</span><span class="sxs-lookup"><span data-stu-id="45b8c-255">NetX Duo SNMP Agent GETNEXT Callback</span></span>

<span data-ttu-id="45b8c-256">Aplikacja musi również ustawić procedurę wywołania zwrotnego dla żądań GetNext obiektu z menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-256">The application must also set the callback routine for GETNEXT object requests from the SNMP Manager.</span></span> <span data-ttu-id="45b8c-257">To wywołanie zwrotne GetNext Pobiera wartość następnego obiektu określonego przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="45b8c-257">The GETNEXT callback retrieves the value of the next object specified by the request.</span></span>

<span data-ttu-id="45b8c-258">Procedura wywołania zwrotnego żądania aplikacji GetNext została zdefiniowana poniżej:</span><span class="sxs-lookup"><span data-stu-id="45b8c-258">The application GETNEXT request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="45b8c-259">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="45b8c-259">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="45b8c-260">Parametr</span><span class="sxs-lookup"><span data-stu-id="45b8c-260">Parameter</span></span>        | <span data-ttu-id="45b8c-261">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="45b8c-261">Meaning</span></span> |
|------------------|-------------------------------------------|
| <span data-ttu-id="45b8c-262">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="45b8c-262">*agent_ptr*</span></span>        | <span data-ttu-id="45b8c-263">Wskaźnik do wywoływania agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-263">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="45b8c-264">object_requested</span><span class="sxs-lookup"><span data-stu-id="45b8c-264">object_requested</span></span> | <span data-ttu-id="45b8c-265">Ciąg ASCII reprezentujący identyfikator obiektu dla operacji GetNext.</span><span class="sxs-lookup"><span data-stu-id="45b8c-265">ASCII string representing the object ID the GETNEXT operation is for.</span></span> |
| <span data-ttu-id="45b8c-266">object_data</span><span class="sxs-lookup"><span data-stu-id="45b8c-266">object_data</span></span>      | <span data-ttu-id="45b8c-267">Struktura danych do przechowywania wartości pobranej przez wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="45b8c-267">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="45b8c-268">Można to ustawić przy użyciu serii interfejsu API SNMP NetX Duo opisanej poniżej.</span><span class="sxs-lookup"><span data-stu-id="45b8c-268">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="45b8c-269">Analogicznie jak ma wartość true w przypadku wywołań zwrotnych, obiekty z danymi ciągu oktetowego muszą mieć przypisaną długość, tak aby wewnętrzna funkcja wiedziała, jak długo długość jest równa, ponieważ wywołanie zwrotne nie ma argumentu długości:</span><span class="sxs-lookup"><span data-stu-id="45b8c-269">Same as is true for GET callbacks, objects with octet string data must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="45b8c-270">Ponieważ typ danych nie jest znany w wywołaniu wywołania zwrotnego, nie trzeba sprawdzać typu danych.</span><span class="sxs-lookup"><span data-stu-id="45b8c-270">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="45b8c-271">Długość nie będzie miała wpływu na typy liczbowe ani ciągi o wartości null.</span><span class="sxs-lookup"><span data-stu-id="45b8c-271">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="45b8c-272">Następnie wywołaj funkcję wewnętrzną:</span><span class="sxs-lookup"><span data-stu-id="45b8c-272">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="45b8c-273">Jeśli funkcja wywołania zwrotnego nie może odnaleźć żądanego obiektu, należy zwrócić **NX_SNMP_ERROR_NOSUCHNAME** kod błędu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-273">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="45b8c-274">W przypadku wykrycia innego błędu należy zwrócić **NX_SNMP_ERROR** .</span><span class="sxs-lookup"><span data-stu-id="45b8c-274">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-set-callback"></a><span data-ttu-id="45b8c-275">Wywołanie zwrotne agenta SNMP zestawu NetX Duo</span><span class="sxs-lookup"><span data-stu-id="45b8c-275">NetX Duo SNMP Agent SET Callback</span></span>

<span data-ttu-id="45b8c-276">Aplikacja powinna ustawić procedurę wywołania zwrotnego dla obsługi żądań SET obiektu z menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-276">The application should set the callback routine for handling SET object requests from the SNMP Manager.</span></span> <span data-ttu-id="45b8c-277">Ustawianie wywołania zwrotnego ustawia wartość obiektu określonego przez żądanie.</span><span class="sxs-lookup"><span data-stu-id="45b8c-277">The SET callback sets the value of the object specified by the request.</span></span>

<span data-ttu-id="45b8c-278">Procedura wywołania zwrotnego żądania zestawu aplikacji jest definiowana poniżej:</span><span class="sxs-lookup"><span data-stu-id="45b8c-278">The application SET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="45b8c-279">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="45b8c-279">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="45b8c-280">Parametr</span><span class="sxs-lookup"><span data-stu-id="45b8c-280">Parameter</span></span>        | <span data-ttu-id="45b8c-281">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="45b8c-281">Meaning</span></span> |
|------------------|-------- |
| <span data-ttu-id="45b8c-282">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="45b8c-282">*agent_ptr*</span></span>      | <span data-ttu-id="45b8c-283">Wskaźnik do wywoływania agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-283">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="45b8c-284">object_requested</span><span class="sxs-lookup"><span data-stu-id="45b8c-284">object_requested</span></span> | <span data-ttu-id="45b8c-285">Ciąg ASCII reprezentujący identyfikator obiektu dla operacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-285">ASCII string representing the object ID the SET operation is for.</span></span> |
| <span data-ttu-id="45b8c-286">object_data</span><span class="sxs-lookup"><span data-stu-id="45b8c-286">object_data</span></span>      | <span data-ttu-id="45b8c-287">Struktura danych, która zawiera nową wartość dla określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-287">Data structure that contains the new value for the specified object.</span></span> <span data-ttu-id="45b8c-288">Rzeczywistą operację można wykonać przy użyciu interfejsu API protokołu SNMP NetX Duo opisanej poniżej.</span><span class="sxs-lookup"><span data-stu-id="45b8c-288">The actual operation can be done using the NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="45b8c-289">Należy pamiętać, że w przypadku ciągów oktetowych Ustaw wywołanie zwrotne powinno zaktualizować tabelę MIB o długość danych, ponieważ Agent SNMP przeanalizuje dane i zna typ i Długość:</span><span class="sxs-lookup"><span data-stu-id="45b8c-289">Note that for octet strings, the SET callback should update the MIB table with the length of the data since the SNMP Agent has parsed the data and knows the type and length:</span></span>

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

<span data-ttu-id="45b8c-290">Jeśli funkcja wywołania zwrotnego nie może odnaleźć żądanego obiektu, należy zwrócić **NX_SNMP_ERROR_NOSUCHNAME** kod błędu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-290">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span>

<span data-ttu-id="45b8c-291">Jeśli host SNMP NetX Duo utworzył prywatne ciągi społecznościowe, a nadawca protokołu SNMP dla żądania SET nie ma pasującego ciągu prywatnego, może zwrócić błąd **NX_SNMP_ERROR_NOACCESS** .</span><span class="sxs-lookup"><span data-stu-id="45b8c-291">If the NetX Duo SNMP host has created private community strings, and the SNMP sender of the SET request does not have the matching private string, it may return an **NX_SNMP_ERROR_NOACCESS** error.</span></span> <span data-ttu-id="45b8c-292">W przypadku wykrycia innego błędu należy zwrócić **NX_SNMP_ERROR** .</span><span class="sxs-lookup"><span data-stu-id="45b8c-292">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

> [!NOTE]
> <span data-ttu-id="45b8c-293">*Mimo że Agent SNMP NetX Duo dostarcza bazę danych SNMP MIB z dystrybucją, jest ona głównie do testowania i programowania. Deweloper będzie prawdopodobnie wymagał zastrzeżonej bazy danych MIB dla profesjonalnej aplikacji SNMP.*</span><span class="sxs-lookup"><span data-stu-id="45b8c-293">*Although NetX Duo SNMP Agent supplies an SNMP MIB database with the distribution, it is primarily for testing and development purposes. The developer will likely require a proprietary MIB database for a professional SNMP application.*</span></span>

## <a name="changing-snmp-version-at-run-time"></a><span data-ttu-id="45b8c-294">Zmiana wersji SNMP w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="45b8c-294">Changing SNMP Version at Run Time</span></span>

<span data-ttu-id="45b8c-295">Host agenta SNMP może zmienić wersję protokołu SNMP dla każdej z trzech wersji w czasie wykonywania za pomocą usługi *nx_snmp_agent_set_version* .</span><span class="sxs-lookup"><span data-stu-id="45b8c-295">The SNMP Agent host can change SNMP version for each of the three versions at run time using the *nx_snmp_agent_set_version* service.</span></span> <span data-ttu-id="45b8c-296">Agent SNMP jest domyślnie włączony dla wszystkich trzech wersji, gdy zostanie utworzony Agent SNMP w *nx_snmp_agent_create*.</span><span class="sxs-lookup"><span data-stu-id="45b8c-296">The SNMP Agent is by default enabled for all three versions when the SNMP Agent is created in *nx_snmp_agent_create*.</span></span> <span data-ttu-id="45b8c-297">Jednak aplikacja może ograniczyć to podzbiór wszystkich wersji.</span><span class="sxs-lookup"><span data-stu-id="45b8c-297">However, the application can limit that to a subset of all versions.</span></span>

> [!NOTE]
> <span data-ttu-id="45b8c-298">*W przypadku zdefiniowania opcji konfiguracji NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 i/lub NX_SNMP_DISABLE_V3 ta funkcja nie będzie miała wpływu na to, że te wersje nie zostaną zastosowane.*</span><span class="sxs-lookup"><span data-stu-id="45b8c-298">*If the configuration options NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 and/or NX_SNMP_DISABLE_V3 are defined, this function will have no effect enabling the effected versions.*</span></span>

<span data-ttu-id="45b8c-299">Agent SNMP może pobrać wersję SNMP najnowszego pakietu SNMP otrzymanego przy użyciu usługi *nx_snmp_agent_get_current_version* .</span><span class="sxs-lookup"><span data-stu-id="45b8c-299">The SNMP Agent can retrieve the SNMP version of the latest SNMP packet received using the *nx_snmp_agent_get_current_version* service.</span></span>

## <a name="snmpv3-discovery"></a><span data-ttu-id="45b8c-300">Odnajdywanie SNMPv3</span><span class="sxs-lookup"><span data-stu-id="45b8c-300">SNMPv3 Discovery</span></span>

<span data-ttu-id="45b8c-301">Agent SNMP, jeśli jest włączony dla SNMPv3, będzie odpowiadać na żądania odnajdywania od menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="45b8c-301">The SNMP Agent, if enabled for SNMPv3, will respond to discovery requests from the SNMP Manager.</span></span> <span data-ttu-id="45b8c-302">Takie żądanie zawiera dane parametrów zabezpieczeń z wartościami null dla identyfikatora aparatu autorytatywnego, nazwy użytkownika, liczby rozruchowej i czasu rozruchu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-302">Such a request contains security parameter data with null values for Authoritative Engine ID, user name, boot count and boot time.</span></span> <span data-ttu-id="45b8c-303">Parametry uwierzytelniania nie są stosowane do komunikatu ODNAJDOWAnia.</span><span class="sxs-lookup"><span data-stu-id="45b8c-303">Authentication parameters are not applied to the DISCOVERY message.</span></span> <span data-ttu-id="45b8c-304">Lista powiązań zmiennych w żądaniu jest pusta (zawiera zerowe elementy).</span><span class="sxs-lookup"><span data-stu-id="45b8c-304">The variable binding list in the request is empty (contains zero items).</span></span> <span data-ttu-id="45b8c-305">Agent SNMP reaguje na zero czasu i liczby rozruchów oraz listę powiązań zmiennych zawierającą 1 element, *usmStatsUnknownEngineIDs*, czyli liczbę żądań odebranych z nieznanym (null) identyfikatorem aparatu.</span><span class="sxs-lookup"><span data-stu-id="45b8c-305">The SNMP agent responds with a zero boot time and count, and the variable binding list containing 1 item, *usmStatsUnknownEngineIDs*, which is the count of requests received with an unknown (null) engine ID.</span></span> <span data-ttu-id="45b8c-306">Na kolejne żądanie GetNext z przeglądarki/Menedżera, dane rozruchowe i parametry zabezpieczeń są wypełniane tylko wtedy, gdy włączono zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="45b8c-306">On the subsequent GETNEXT request from the Browser/Manager, the boot data and security parameters are filled in only if security is enabled.</span></span> <span data-ttu-id="45b8c-307">W takim przypadku wyśle także NotInTimeą aktualizację danych w jednostce PDU.</span><span class="sxs-lookup"><span data-stu-id="45b8c-307">If so it will also send a NotInTime data update in the PDU.</span></span> <span data-ttu-id="45b8c-308">Parametry zabezpieczeń, np. uwierzytelnianie udowadniają tożsamość agenta dla Menedżera.</span><span class="sxs-lookup"><span data-stu-id="45b8c-308">The security parameters, e.g. authentication prove the identity of the Agent to the Manager.</span></span>

<span data-ttu-id="45b8c-309">Bardziej szczegółowe informacje na temat uwierzytelniania SNMPv3 są dostępne w dokumencie RFC 3414 "model zabezpieczeń oparty na użytkownikach (USM) dla wersji 3 Simple Network Management Protocol (SNMPv3)".</span><span class="sxs-lookup"><span data-stu-id="45b8c-309">More detailed information on SNMPv3 authentication is available in RFC 3414 “User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)”.</span></span>

## <a name="netx-duo-snmp-rfcs"></a><span data-ttu-id="45b8c-310">NetX Duo — specyfikacje RFC protokołu SNMP</span><span class="sxs-lookup"><span data-stu-id="45b8c-310">NetX Duo SNMP RFCs</span></span>

<span data-ttu-id="45b8c-311">NetX Duo SNMP jest zgodne z RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575,, RFC 3414 i powiązane z nimi specyfikacje RFC.</span><span class="sxs-lookup"><span data-stu-id="45b8c-311">NetX Duo SNMP is compliant with RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 and related RFCs.</span></span>
