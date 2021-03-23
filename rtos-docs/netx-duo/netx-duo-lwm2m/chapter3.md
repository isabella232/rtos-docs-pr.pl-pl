---
title: Rozdział 3 — Opis funkcjonalny klienta LWM2M
description: Ten rozdział zawiera opis funkcjonalny klienta programu LWM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821841"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a><span data-ttu-id="3d54b-103">Rozdział 3 funkcjonalny opis klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="3d54b-103">Chapter 3  Functional Description of LWM2M Client</span></span>

> <span data-ttu-id="3d54b-104">Ten rozdział zawiera opis funkcjonalny klienta programu LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-104">This chapter contains a functional description of LWM2M Client.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="3d54b-105">LWM2M inicjowanie klienta</span><span class="sxs-lookup"><span data-stu-id="3d54b-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="3d54b-106">Klient LWM2M jest inicjowany przez wywołanie usługi ***nx_lwm2m_client_create*** .</span><span class="sxs-lookup"><span data-stu-id="3d54b-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="3d54b-107">Klient LWM2M działa we własnym wątku i może zgłosić pewne zdarzenia do aplikacji za pomocą wywołań zwrotnych lub przez wywołanie metod niestandardowych obiektów wdrożonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="3d54b-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="3d54b-108">Ponadto należy utworzyć sesje klienta LWM2M przez wywołanie ***nx_lwm2m_client_session_create*** w celu włączenia komunikacji z co najmniej jednym serwerem.</span><span class="sxs-lookup"><span data-stu-id="3d54b-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="3d54b-109">Sesja może komunikować się z dwoma różnymi typami serwerów: serwerem Bootstrap lub serwerem LWM2M (Zarządzanie urządzeniami).</span><span class="sxs-lookup"><span data-stu-id="3d54b-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="3d54b-110">Sesja serwera Bootstrap</span><span class="sxs-lookup"><span data-stu-id="3d54b-110">Bootstrap Server Session</span></span>

<span data-ttu-id="3d54b-111">Sesja komunikacji z serwerem Bootstrap służy do aprowizacji najważniejszych informacji w kliencie LWM2M, aby umożliwić klientowi LWM2M wykonywanie operacji "Register" z co najmniej jednym serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation “Register” with one or more LWM2M Servers.</span></span> <span data-ttu-id="3d54b-112">Ten typ serwera jest używany podczas inicjowania klienta i inicjowanego przez serwer trybów ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="3d54b-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="3d54b-113">Aplikacja może uruchomić sesję ładowania początkowego przez wywołanie ***nx_lwm2m_client_session_bootstrap** _ lub _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, musi podać adres IP i numer portu serwera oraz opcjonalny identyfikator wystąpienia obiektu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3d54b-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="3d54b-114">Funkcja _*_nx_lwm2m_client_session_bootstrap_*_ używa niezabezpieczonej komunikacji, natomiast _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* nawiązuje bezpieczne połączenie DTLS z serwerem.</span><span class="sxs-lookup"><span data-stu-id="3d54b-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="3d54b-115">Jeśli operacja ładowania początkowego zakończyła się powodzeniem, serwer Bootstrap powinien mieć utworzone wystąpienia obiektów zabezpieczeń dla serwerów Bootstrap i LWM2M oraz wystąpienia obiektów serwera dla serwerów LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="3d54b-116">Aplikacja może wywoływać ***nx_lwm2m_client_session_register_info_get*** , aby uzyskać informacje o serwerach lwm2m i użyć tych informacji do ustanowienia sesji z serwerem lwm2m.</span><span class="sxs-lookup"><span data-stu-id="3d54b-116">The application can call ***nx_lwm2m_client_session_register_info_get*** to get LWM2M Server(s) information and use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="3d54b-117">Dane ładowania początkowego powinny zostać zapisane w pamięci nieulotnej przez aplikację w celu skonfigurowania klienta LWM2M przy następnym ponownym uruchomieniu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="3d54b-117">The Bootstrap data should be saved to non-volatile memory by the application to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="3d54b-118">Sesja serwera LWM2M</span><span class="sxs-lookup"><span data-stu-id="3d54b-118">LWM2M Server Session</span></span>

<span data-ttu-id="3d54b-119">Sesja komunikacji z serwerem LWM2M jest używana do rejestracji, zarządzania urządzeniami i włączania usług.</span><span class="sxs-lookup"><span data-stu-id="3d54b-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="3d54b-120">Aplikacja może zarejestrować klienta LWM2M na serwerze, wywołując ***nx_lwm2m_client_session_register** _ lub _*_nx_lwm2m_client_session_register_dtls_\*_, musi podać adres IP i numer portu serwera oraz krótki identyfikator serwera, który odpowiada istniejącemu wystąpieniu obiektu serwera.</span><span class="sxs-lookup"><span data-stu-id="3d54b-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="3d54b-121">Funkcja _*_nx_lwm2m_client_session_register_*_ używa niezabezpieczonej komunikacji, natomiast _ *_nx_lwm2m_client_session_register_dtls_*\* nawiązuje bezpieczne połączenie DTLS z serwerem.</span><span class="sxs-lookup"><span data-stu-id="3d54b-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas  _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="3d54b-122">Aplikacja może wyrejestrować klienta LWM2M przez wywołanie \***nx_lwm2m_client_session_deregister** _ i poproszenie klienta o wysłanie komunikatu "Update" przez wywołanie _ *_nx_lwm2m_client_session_update_* \*.</span><span class="sxs-lookup"><span data-stu-id="3d54b-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an ‘Update’ message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="3d54b-123">Wywołanie zwrotne stanu sesji</span><span class="sxs-lookup"><span data-stu-id="3d54b-123">Session State Callback</span></span>

<span data-ttu-id="3d54b-124">Aplikacja rejestruje wywołanie zwrotne podczas tworzenia sesji, która jest wywoływana w momencie aktualizacji stanu sesji, funkcja wywołania zwrotnego **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** ma następujący prototyp.</span><span class="sxs-lookup"><span data-stu-id="3d54b-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** has the following prototype.</span></span>

<span data-ttu-id="3d54b-125">typedef VOID ( \* NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK) (NX_LWM2M_CLIENT_SESSION \* SESSION_PTR, uint State);</span><span class="sxs-lookup"><span data-stu-id="3d54b-125">typedef VOID (\*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \*session_ptr,UINT state);</span></span>

<span data-ttu-id="3d54b-126">Zdefiniowane są następujące Stany.</span><span class="sxs-lookup"><span data-stu-id="3d54b-126">The following states are defined.</span></span>

| <span data-ttu-id="3d54b-127">&nbsp;Stan sesji</span><span class="sxs-lookup"><span data-stu-id="3d54b-127">Session&nbsp;State</span></span> | <span data-ttu-id="3d54b-128">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-128">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span><span class="sxs-lookup"><span data-stu-id="3d54b-129">**NX_LWM2M_CLIENT_SESSION_INIT**</span></span> | <span data-ttu-id="3d54b-130">Stan początkowy po utworzeniu sesji.</span><span class="sxs-lookup"><span data-stu-id="3d54b-130">The initial state after session creation.</span></span> |
| <span data-ttu-id="3d54b-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span><span class="sxs-lookup"><span data-stu-id="3d54b-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**</span></span> | <span data-ttu-id="3d54b-132">Klient czeka na wygaśnięcie czasomierza "wstrzymanie" lub zainicjowanie serwera Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="3d54b-132">The client is waiting for the expiration of the ‘Hold Off’ timer or Server Initiated Bootstrap.</span></span> |
| <span data-ttu-id="3d54b-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span><span class="sxs-lookup"><span data-stu-id="3d54b-133">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**</span></span> | <span data-ttu-id="3d54b-134">Klient wysłał komunikat "żądanie" do serwera Bootstrap (zainicjowany przez klienta).</span><span class="sxs-lookup"><span data-stu-id="3d54b-134">The client has sent a ‘Request’ message to the Bootstrap Server (Client Initiated Bootstrap).</span></span> |
| <span data-ttu-id="3d54b-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span><span class="sxs-lookup"><span data-stu-id="3d54b-135">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**</span></span> | <span data-ttu-id="3d54b-136">Klient otrzymuje dane z serwera Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="3d54b-136">The client is receiving data from the Bootstrap Server.</span></span> |
| <span data-ttu-id="3d54b-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span><span class="sxs-lookup"><span data-stu-id="3d54b-137">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**</span></span> | <span data-ttu-id="3d54b-138">Serwer ładowania początkowego wysłał komunikat "gotowe".</span><span class="sxs-lookup"><span data-stu-id="3d54b-138">The Bootstrap Server has sent a ‘Finished’ message.</span></span> |
| <span data-ttu-id="3d54b-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span><span class="sxs-lookup"><span data-stu-id="3d54b-139">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**</span></span> | <span data-ttu-id="3d54b-140">Sesja ładowania początkowego zakończyła się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="3d54b-140">The bootstrap session has failed.</span></span> |
| <span data-ttu-id="3d54b-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span><span class="sxs-lookup"><span data-stu-id="3d54b-141">**NX_LWM2M_CLIENT_SESSION_REGISTERING**</span></span> | <span data-ttu-id="3d54b-142">Klient wysłał komunikat "Register" do serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-142">The client has sent a ‘Register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="3d54b-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span><span class="sxs-lookup"><span data-stu-id="3d54b-143">**NX_LWM2M_CLIENT_SESSION_REGISTERED**</span></span> | <span data-ttu-id="3d54b-144">Klient jest zarejestrowany na serwerze LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-144">The client is registered to the LWM2M Server.</span></span> |
| <span data-ttu-id="3d54b-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span><span class="sxs-lookup"><span data-stu-id="3d54b-145">**NX_LWM2M_CLIENT_SESSION_UPDATING**</span></span> | <span data-ttu-id="3d54b-146">Klient wysłał komunikat "Update" do serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-146">The client has sent an ‘Update’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="3d54b-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span><span class="sxs-lookup"><span data-stu-id="3d54b-147">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**</span></span> | <span data-ttu-id="3d54b-148">Klient wysłał komunikat "de-Register" do serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-148">The client has sent an ‘De-register’ message to the LWM2M Server.</span></span> |
| <span data-ttu-id="3d54b-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span><span class="sxs-lookup"><span data-stu-id="3d54b-149">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**</span></span> | <span data-ttu-id="3d54b-150">Klient zostanie wyrejestrowany z serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-150">The client is de-registered from the LWM2M Server.</span></span> |
| <span data-ttu-id="3d54b-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span><span class="sxs-lookup"><span data-stu-id="3d54b-151">**NX_LWM2M_CLIENT_SESSION_DISABLED**</span></span> | <span data-ttu-id="3d54b-152">Serwer LWM2M jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="3d54b-152">The LWM2M Server is disabled.</span></span> <span data-ttu-id="3d54b-153">Po wygaśnięciu czasomierza Wyłącz zostanie wysłany komunikat "Register".</span><span class="sxs-lookup"><span data-stu-id="3d54b-153">A ‘Register’ will be sent after the expiration of the disable timer.</span></span> |
| <span data-ttu-id="3d54b-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span><span class="sxs-lookup"><span data-stu-id="3d54b-154">**NX_LWM2M_CLIENT_SESSION_ERROR**</span></span> | <span data-ttu-id="3d54b-155">Operacja rejestracji lub aktualizacji na serwerze LWM2M nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="3d54b-155">The registration or update operation to the LWM2M Server has failed.</span></span> |
| <span data-ttu-id="3d54b-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span><span class="sxs-lookup"><span data-stu-id="3d54b-156">**NX_LWM2M_CLIENT_SESSION_DELETED**</span></span> | <span data-ttu-id="3d54b-157">Wystąpienie obiektu serwera odpowiadające serwerowi LWM2M zostało usunięte.</span><span class="sxs-lookup"><span data-stu-id="3d54b-157">The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> |

<span data-ttu-id="3d54b-158">W przypadku błędu aplikacja może pobrać przyczynę błędu przez wywołanie ***nx_lwm2m_client_session_error_get***.</span><span class="sxs-lookup"><span data-stu-id="3d54b-158">In case of error the application can retrieve the cause of the error by calling ***nx_lwm2m_client_session_error_get***.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="3d54b-159">Zarządzanie urządzeniami lokalnymi</span><span class="sxs-lookup"><span data-stu-id="3d54b-159">Local Device Management</span></span>

<span data-ttu-id="3d54b-160">Aplikacja może uzyskiwać dostęp do obiektów klienta LWM2M za pomocą funkcji zarządzania urządzeniami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="3d54b-160">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="3d54b-161">Dostępne są następujące funkcje.</span><span class="sxs-lookup"><span data-stu-id="3d54b-161">The following functions are provided.</span></span>

| <span data-ttu-id="3d54b-162">&nbsp;Nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="3d54b-162">Function&nbsp;Name</span></span> | <span data-ttu-id="3d54b-163">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-163">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-164">***nx_lwm2m_client_object_read***</span><span class="sxs-lookup"><span data-stu-id="3d54b-164">***nx_lwm2m_client_object_read***</span></span> | <span data-ttu-id="3d54b-165">Odczytaj zasoby z wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-165">Read resources from an Object Instance.</span></span> |
| <span data-ttu-id="3d54b-166">***nx_lwm2m_client_object_discover***</span><span class="sxs-lookup"><span data-stu-id="3d54b-166">***nx_lwm2m_client_object_discover***</span></span> | <span data-ttu-id="3d54b-167">Pobierz listę zasobów wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-167">Get the list of the resources of an Object Instance.</span></span>
| <span data-ttu-id="3d54b-168">***nx_lwm2m_client_object_write***</span><span class="sxs-lookup"><span data-stu-id="3d54b-168">***nx_lwm2m_client_object_write***</span></span> | <span data-ttu-id="3d54b-169">Zapisz zasoby do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-169">Write resources to an Object Instance.</span></span> |
| <span data-ttu-id="3d54b-170">***nx_lwm2m_client_object_execute***</span><span class="sxs-lookup"><span data-stu-id="3d54b-170">***nx_lwm2m_client_object_execute***</span></span> | <span data-ttu-id="3d54b-171">Wykonaj operację wykonywania na zasobie wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-171">Perform the Execute operation on a resource of an Object Instance.</span></span> |
| <span data-ttu-id="3d54b-172">***nx_lwm2m_client_object_create***</span><span class="sxs-lookup"><span data-stu-id="3d54b-172">***nx_lwm2m_client_object_create***</span></span> | <span data-ttu-id="3d54b-173">Utwórz nowe wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-173">Create a new Object Instance.</span></span> |
| <span data-ttu-id="3d54b-174">***nx_lwm2m_client_object_delete***</span><span class="sxs-lookup"><span data-stu-id="3d54b-174">***nx_lwm2m_client_object_delete***</span></span> | <span data-ttu-id="3d54b-175">Usuń istniejące wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-175">Delete an existing Object Instance.</span></span> |
| <span data-ttu-id="3d54b-176">***nx_lwm2m_client_object_next_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-176">***nx_lwm2m_client_object_next_get***</span></span> | <span data-ttu-id="3d54b-177">Pobierz następny identyfikator obiektu przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-177">Get the next Object ID by the LWM2M Client.</span></span> |
| <span data-ttu-id="3d54b-178">***nx_lwm2m_client_object_instance_next_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-178">***nx_lwm2m_client_object_instance_next_get***</span></span> | <span data-ttu-id="3d54b-179">Pobierz następne wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-179">Get the next Instance of an Object.</span></span> |

## <a name="resource-information"></a><span data-ttu-id="3d54b-180">Informacje o zasobach</span><span class="sxs-lookup"><span data-stu-id="3d54b-180">Resource Information</span></span>

<span data-ttu-id="3d54b-181">Podczas odczytywania i zapisywania do obiektów zasób jest reprezentowany przez strukturę NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="3d54b-181">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_CLIENT_RESOURCE structure.</span></span> <span data-ttu-id="3d54b-182">Ta struktura zawiera identyfikator zasobu/wystąpienia i jego wartość.</span><span class="sxs-lookup"><span data-stu-id="3d54b-182">This structure contains the ID of the Resource/Instance and its value.</span></span>

<span data-ttu-id="3d54b-183">Następujące funkcje są dostępne do ustawiania informacji o zasobach i wartości.</span><span class="sxs-lookup"><span data-stu-id="3d54b-183">The following functions are provided for setting resource info and value.</span></span>

| <span data-ttu-id="3d54b-184">&nbsp;Nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="3d54b-184">Function&nbsp;Name</span></span> | <span data-ttu-id="3d54b-185">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-185">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-186">***nx_lwm2m_client_resource_info_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-186">***nx_lwm2m_client_resource_info_set***</span></span> | <span data-ttu-id="3d54b-187">Ustawianie informacji o zasobie: Identyfikator zasobu i operacja: Odczyt, zapis, plik WYKONYWALNy.</span><span class="sxs-lookup"><span data-stu-id="3d54b-187">Set resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="3d54b-188">***nx_lwm2m_client_resource_string_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-188">***nx_lwm2m_client_resource_string_set***</span></span> | <span data-ttu-id="3d54b-189">Ustaw wartość zasobu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="3d54b-189">Set the resource value as string.</span></span> |
| <span data-ttu-id="3d54b-190">***nx_lwm2m_client_resource_integer32_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-190">***nx_lwm2m_client_resource_integer32_set***</span></span> | <span data-ttu-id="3d54b-191">Ustaw wartość zasobu jako 32-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="3d54b-191">Set the resource value as 32-Bit integer.</span></span> |
| <span data-ttu-id="3d54b-192">***nx_lwm2m_client_resource_integer64_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-192">***nx_lwm2m_client_resource_integer64_set***</span></span> | <span data-ttu-id="3d54b-193">Ustaw wartość zasobu jako 64-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="3d54b-193">Set the resource value as 64-Bit integer.</span></span> |
| <span data-ttu-id="3d54b-194">***nx_lwm2m_client_resource_float32_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-194">***nx_lwm2m_client_resource_float32_set***</span></span> | <span data-ttu-id="3d54b-195">Ustaw wartość zasobu jako 32-bitową zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="3d54b-195">Set the resource value as 32-Bit float.</span></span> |
| <span data-ttu-id="3d54b-196">***nx_lwm2m_client_resource_float64_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-196">***nx_lwm2m_client_resource_float64_set***</span></span> | <span data-ttu-id="3d54b-197">Ustaw wartość zasobu jako 64-bitową zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="3d54b-197">Set the resource value as 64-Bit float.</span></span> |
| <span data-ttu-id="3d54b-198">***nx_lwm2m_client_resource_boolean_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-198">***nx_lwm2m_client_resource_boolean_set***</span></span> | <span data-ttu-id="3d54b-199">Ustaw wartość zasobu jako logiczną.</span><span class="sxs-lookup"><span data-stu-id="3d54b-199">Set the resource value as boolean.</span></span> |
| <span data-ttu-id="3d54b-200">***nx_lwm2m_client_resource_objlnk_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-200">***nx_lwm2m_client_resource_objlnk_set***</span></span> | <span data-ttu-id="3d54b-201">Ustaw wartość zasobu jako link do obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-201">Set the resource value as object link.</span></span> |
| <span data-ttu-id="3d54b-202">***nx_lwm2m_client_resource_opaque_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-202">***nx_lwm2m_client_resource_opaque_set***</span></span> | <span data-ttu-id="3d54b-203">Ustaw wartość zasobu jako nieprzezroczystą.</span><span class="sxs-lookup"><span data-stu-id="3d54b-203">Set the resource value as opaque.</span></span> |
| <span data-ttu-id="3d54b-204">***nx_lwm2m_client_resource_instance_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-204">***nx_lwm2m_client_resource_instance_set***</span></span> | <span data-ttu-id="3d54b-205">Ustaw wartość zasobu jako wystąpienie dla wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="3d54b-205">Set the resource value as instance for multiple resource.</span></span> |
| <span data-ttu-id="3d54b-206">***nx_lwm2m_client_resource_dim_set***</span><span class="sxs-lookup"><span data-stu-id="3d54b-206">***nx_lwm2m_client_resource_dim_set***</span></span> | <span data-ttu-id="3d54b-207">Ustaw wymiar zasobu dla wielu zasobów na potrzeby odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-207">Set the resource dimension for multiple resource for discover.</span></span> |

<span data-ttu-id="3d54b-208">Do pobierania informacji o zasobach i wartości są dostępne następujące funkcje.</span><span class="sxs-lookup"><span data-stu-id="3d54b-208">The following functions are provided for getting resource info and value.</span></span>

| <span data-ttu-id="3d54b-209">&nbsp;Nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="3d54b-209">Function&nbsp;Name</span></span> | <span data-ttu-id="3d54b-210">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-210">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-211">***nx_lwm2m_client_resource_info_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-211">***nx_lwm2m_client_resource_info_get***</span></span> | <span data-ttu-id="3d54b-212">Pobierz informacje o zasobie: Identyfikator zasobu i operacja: Odczyt, zapis, plik WYKONYWALNy.</span><span class="sxs-lookup"><span data-stu-id="3d54b-212">Get resource info: resource id and operation: READ, WRITE, EXECUTABLE.</span></span> |
| <span data-ttu-id="3d54b-213">***nx_lwm2m_client_resource_string_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-213">***nx_lwm2m_client_resource_string_get***</span></span> | <span data-ttu-id="3d54b-214">Pobierz wartość zasobu ciągu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-214">Get the value of a string resource.</span></span> |
| <span data-ttu-id="3d54b-215">***nx_lwm2m_client_resource_integer32_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-215">***nx_lwm2m_client_resource_integer32_get***</span></span> | <span data-ttu-id="3d54b-216">Pobierz wartość 32-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="3d54b-216">Get the value of a 32-Bit integer resource.</span></span> |
| <span data-ttu-id="3d54b-217">***nx_lwm2m_client_resource_integer64_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-217">***nx_lwm2m_client_resource_integer64_get***</span></span> | <span data-ttu-id="3d54b-218">Pobierz wartość dla zasobu liczby całkowitej B4-bitowej.</span><span class="sxs-lookup"><span data-stu-id="3d54b-218">Get the value of a b4-Bit integer resource.</span></span> |
| <span data-ttu-id="3d54b-219">***nx_lwm2m_client_resource_float32_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-219">***nx_lwm2m_client_resource_float32_get***</span></span> | <span data-ttu-id="3d54b-220">Pobierz wartość 32-bitowego zasobu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="3d54b-220">Get the value of a 32-Bit float resource.</span></span> |
| <span data-ttu-id="3d54b-221">***nx_lwm2m_client_resource_float64_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-221">***nx_lwm2m_client_resource_float64_get***</span></span> | <span data-ttu-id="3d54b-222">Pobierz wartość 64-bitowego zasobu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="3d54b-222">Get the value of a 64-Bit float resource.</span></span> |
| <span data-ttu-id="3d54b-223">***nx_lwm2m_client_resource_boolean_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-223">***nx_lwm2m_client_resource_boolean_get***</span></span> | <span data-ttu-id="3d54b-224">Pobierz wartość zasobu logicznego.</span><span class="sxs-lookup"><span data-stu-id="3d54b-224">Get the value of a Boolean resource.</span></span> |
| <span data-ttu-id="3d54b-225">***nx_lwm2m_client_resource_objlnk_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-225">***nx_lwm2m_client_resource_objlnk_get***</span></span> | <span data-ttu-id="3d54b-226">Pobierz wartość zasobu linku do obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-226">Get the value of an object link resource.</span></span> |
| <span data-ttu-id="3d54b-227">***nx_lwm2m_client_resource_opaque_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-227">***nx_lwm2m_client_resource_opaque_get***</span></span> | <span data-ttu-id="3d54b-228">Pobierz wartość nieprzezroczystego zasobu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-228">Get the value of an opaque resource.</span></span> |
| <span data-ttu-id="3d54b-229">***nx_lwm2m_client_resource_instance_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-229">***nx_lwm2m_client_resource_instance_get***</span></span> | <span data-ttu-id="3d54b-230">Pobierz wystąpienie zasobu dla wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="3d54b-230">Get the resource instance for multiple resource.</span></span> |
| <span data-ttu-id="3d54b-231">***nx_lwm2m_client_resource_dim_get***</span><span class="sxs-lookup"><span data-stu-id="3d54b-231">***nx_lwm2m_client_resource_dim_get***</span></span> | <span data-ttu-id="3d54b-232">Pobierz wymiar zasobu dla wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="3d54b-232">Get the resource dimension for multiple resource.</span></span> |

## <a name="object-implementation"></a><span data-ttu-id="3d54b-233">Implementacja obiektu</span><span class="sxs-lookup"><span data-stu-id="3d54b-233">Object Implementation</span></span>

<span data-ttu-id="3d54b-234">Klient LWM2M implementuje wymagane obiekty LWM2M OMA: Security (0), Server (1), Access Control (2) i Device (3).</span><span class="sxs-lookup"><span data-stu-id="3d54b-234">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="3d54b-235">Inne obiekty specyficzne dla urządzenia muszą być implementowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="3d54b-235">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="3d54b-236">Do zdefiniowania obiektu służą dwie struktury danych: Struktura NX_LWM2M_CLIENT_OBJECT definiuje implementację obiektu, łącznie z IDENTYFIKATORem obiektu i metodami obiektu, a struktura NX_LWM2M_CLIENT_OBJECT_INSTANCE zawiera dane wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-236">Two data structures are used to define an Object: the NX_LWM2M_CLIENT_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_CLIENT_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="3d54b-237">Dostępne są następujące funkcje.</span><span class="sxs-lookup"><span data-stu-id="3d54b-237">The following functions are provided.</span></span>

| <span data-ttu-id="3d54b-238">&nbsp;Nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="3d54b-238">Function&nbsp;Name</span></span> | <span data-ttu-id="3d54b-239">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-239">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-240">***nx_lwm2m_client_object_add***</span><span class="sxs-lookup"><span data-stu-id="3d54b-240">***nx_lwm2m_client_object_add***</span></span> | <span data-ttu-id="3d54b-241">Dodaj implementację obiektu do klienta LwM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-241">Add object implementation to the LwM2M Client.</span></span> |
| <span data-ttu-id="3d54b-242">***nx_lwm2m_client_object_remove***</span><span class="sxs-lookup"><span data-stu-id="3d54b-242">***nx_lwm2m_client_object_remove***</span></span> | <span data-ttu-id="3d54b-243">Usuń implementację obiektu z klienta LwM2M.</span><span class="sxs-lookup"><span data-stu-id="3d54b-243">Remove object implementation from the LwM2M Client.</span></span> |
| <span data-ttu-id="3d54b-244">***nx_lwm2m_client_object_instance_add***</span><span class="sxs-lookup"><span data-stu-id="3d54b-244">***nx_lwm2m_client_object_instance_add***</span></span> | <span data-ttu-id="3d54b-245">Dodaj wystąpienie obiektu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-245">Add object instance to the Object.</span></span> |
| <span data-ttu-id="3d54b-246">***nx_lwm2m_client_object_instance_remove***</span><span class="sxs-lookup"><span data-stu-id="3d54b-246">***nx_lwm2m_client_object_instance_remove***</span></span> | <span data-ttu-id="3d54b-247">Usuń wystąpienie obiektu z obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-247">Remove object instance from the Object.</span></span> |

<span data-ttu-id="3d54b-248">Funkcja wywołania zwrotnego metody obiektu ma sygnaturę pokazaną poniżej.</span><span class="sxs-lookup"><span data-stu-id="3d54b-248">The object method callback function has signature shown below.</span></span>

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a><span data-ttu-id="3d54b-249">Metoda "read"</span><span class="sxs-lookup"><span data-stu-id="3d54b-249">The ‘Read’ Method</span></span>

<span data-ttu-id="3d54b-250">Metoda "read" służy do odczytywania wartości zasobów z wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-250">The ‘Read’ method is used to read Resource values from an Object Instance.</span></span> <span data-ttu-id="3d54b-251">Parametry są zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3d54b-251">The parameters are defined as follows.</span></span>

| <span data-ttu-id="3d54b-252">Parametr</span><span class="sxs-lookup"><span data-stu-id="3d54b-252">Parameter</span></span> | <span data-ttu-id="3d54b-253">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-253">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-254">**operacje**</span><span class="sxs-lookup"><span data-stu-id="3d54b-254">**operation**</span></span> | <span data-ttu-id="3d54b-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span><span class="sxs-lookup"><span data-stu-id="3d54b-255">**NX_LWM2M_CLIENT_OBJECT_READ**</span></span> |
| <span data-ttu-id="3d54b-256">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-256">**object_ptr**</span></span> | <span data-ttu-id="3d54b-257">Wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-257">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="3d54b-258">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-258">**instance_ptr**</span></span> | <span data-ttu-id="3d54b-259">Wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-259">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="3d54b-260">**zasoby**</span><span class="sxs-lookup"><span data-stu-id="3d54b-260">**resource**</span></span> | <span data-ttu-id="3d54b-261">Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-261">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="3d54b-262">Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.</span><span class="sxs-lookup"><span data-stu-id="3d54b-262">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="3d54b-263">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="3d54b-263">**resource_count**</span></span> | <span data-ttu-id="3d54b-264">Wskaźnik na liczbę zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-264">Pointer to the number of resources to read.</span></span> |
| <span data-ttu-id="3d54b-265">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-265">**args_ptr**</span></span> | <span data-ttu-id="3d54b-266">Nieużywany parametr do odczytu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-266">Unused parameter for read.</span></span> |
| <span data-ttu-id="3d54b-267">**args_length**</span><span class="sxs-lookup"><span data-stu-id="3d54b-267">**args_length**</span></span> | <span data-ttu-id="3d54b-268">Nieużywany parametr do odczytu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-268">Unused parameter for read.</span></span> |

### <a name="the-discover-method"></a><span data-ttu-id="3d54b-269">Metoda "Discovery"</span><span class="sxs-lookup"><span data-stu-id="3d54b-269">The ‘Discover’ Method</span></span>

<span data-ttu-id="3d54b-270">Metoda "Discovery" służy do pobierania listy wszystkich zasobów implementowanych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="3d54b-270">The ‘Discover’ method is used to retrieve the list of all Resources implemented by an Object.</span></span> <span data-ttu-id="3d54b-271">Parametry są zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3d54b-271">The parameters are defined as follows.</span></span>

| <span data-ttu-id="3d54b-272">Parametr</span><span class="sxs-lookup"><span data-stu-id="3d54b-272">Parameter</span></span> | <span data-ttu-id="3d54b-273">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-273">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-274">**operacje**</span><span class="sxs-lookup"><span data-stu-id="3d54b-274">**operation**</span></span> | <span data-ttu-id="3d54b-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span><span class="sxs-lookup"><span data-stu-id="3d54b-275">**NX_LWM2M_CLIENT_OBJECT_DISCOVER**</span></span> |
| <span data-ttu-id="3d54b-276">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-276">**object_ptr**</span></span> | <span data-ttu-id="3d54b-277">Wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-277">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="3d54b-278">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-278">**instance_ptr**</span></span> | <span data-ttu-id="3d54b-279">Wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-279">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="3d54b-280">**zasoby**</span><span class="sxs-lookup"><span data-stu-id="3d54b-280">**resource**</span></span> | <span data-ttu-id="3d54b-281">Wskaźnik do tablicy NX_LWM2M_CLIENT_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="3d54b-281">Pointer to an array of NX_LWM2M_CLIENT_RESOURCE.</span></span> <span data-ttu-id="3d54b-282">Po powrocie tablica jest wypełniana odpowiednimi informacjami o zasobach.</span><span class="sxs-lookup"><span data-stu-id="3d54b-282">On return the array is filled with corresponding resource info.</span></span> |
| <span data-ttu-id="3d54b-283">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="3d54b-283">**resource_count**</span></span> | <span data-ttu-id="3d54b-284">Wskaźnik na liczbę zasobów do odnalezienia.</span><span class="sxs-lookup"><span data-stu-id="3d54b-284">Pointer to the number of resources to discover.</span></span> <span data-ttu-id="3d54b-285">W przypadku zwracania ten parametr należy zaktualizować jako wartość true.</span><span class="sxs-lookup"><span data-stu-id="3d54b-285">On return this parameter must be updated as the true value.</span></span> |
| <span data-ttu-id="3d54b-286">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-286">**args_ptr**</span></span> | <span data-ttu-id="3d54b-287">Nieużywany parametr do odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-287">Unused parameter for discover.</span></span> |
| <span data-ttu-id="3d54b-288">**args_length**</span><span class="sxs-lookup"><span data-stu-id="3d54b-288">**args_length**</span></span> | <span data-ttu-id="3d54b-289">Nieużywany parametr do odnajdowania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-289">Unused parameter for discover.</span></span> |

### <a name="the-write-method"></a><span data-ttu-id="3d54b-290">Metoda "Write"</span><span class="sxs-lookup"><span data-stu-id="3d54b-290">The ‘Write’ Method</span></span>

<span data-ttu-id="3d54b-291">Metoda "Write" służy do aktualizowania lub zastępowania zasobów wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-291">The ‘Write’ method is used to update or replace resources of an Object Instance.</span></span> <span data-ttu-id="3d54b-292">Parametry są zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3d54b-292">The parameters are defined as follows.</span></span>

| <span data-ttu-id="3d54b-293">Parametr</span><span class="sxs-lookup"><span data-stu-id="3d54b-293">Parameter</span></span>  | <span data-ttu-id="3d54b-294">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-294">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-295">**operacje**</span><span class="sxs-lookup"><span data-stu-id="3d54b-295">**operation**</span></span> | <span data-ttu-id="3d54b-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span><span class="sxs-lookup"><span data-stu-id="3d54b-296">**NX_LWM2M_CLIENT_OBJECT_WRITE**</span></span> |
| <span data-ttu-id="3d54b-297">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-297">**object_ptr**</span></span> | <span data-ttu-id="3d54b-298">Wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-298">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="3d54b-299">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-299">**instance_ptr**</span></span> | <span data-ttu-id="3d54b-300">Wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-300">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="3d54b-301">**zasoby**</span><span class="sxs-lookup"><span data-stu-id="3d54b-301">**resource**</span></span> | <span data-ttu-id="3d54b-302">Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-302">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="3d54b-303">Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.</span><span class="sxs-lookup"><span data-stu-id="3d54b-303">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="3d54b-304">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="3d54b-304">**resource_count**</span></span> | <span data-ttu-id="3d54b-305">Wskaźnik na liczbę zasobów do odnalezienia.</span><span class="sxs-lookup"><span data-stu-id="3d54b-305">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="3d54b-306">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-306">**args_ptr**</span></span> | <span data-ttu-id="3d54b-307">Zapisz flagi.</span><span class="sxs-lookup"><span data-stu-id="3d54b-307">Write flags.</span></span> |
| <span data-ttu-id="3d54b-308">**args_length**</span><span class="sxs-lookup"><span data-stu-id="3d54b-308">**args_length**</span></span> | <span data-ttu-id="3d54b-309">Długość argumentów.</span><span class="sxs-lookup"><span data-stu-id="3d54b-309">The length of the arguments.</span></span> |

<span data-ttu-id="3d54b-310">Do parametru *flag* można określić następujące operacje zapisu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-310">The following write operations can be specified to the *flag* parameter.</span></span>

| <span data-ttu-id="3d54b-311">Operacja</span><span class="sxs-lookup"><span data-stu-id="3d54b-311">Operation</span></span> | <span data-ttu-id="3d54b-312">Akcja</span><span class="sxs-lookup"><span data-stu-id="3d54b-312">Action</span></span> | <span data-ttu-id="3d54b-313">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-313">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="3d54b-314">0</span><span class="sxs-lookup"><span data-stu-id="3d54b-314">0</span></span> | <span data-ttu-id="3d54b-315">Aktualizacja częściowa</span><span class="sxs-lookup"><span data-stu-id="3d54b-315">Partial Update</span></span> | <span data-ttu-id="3d54b-316">Dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian.</span><span class="sxs-lookup"><span data-stu-id="3d54b-316">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span>
| <span data-ttu-id="3d54b-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="3d54b-317">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="3d54b-318">Zamień wystąpienie</span><span class="sxs-lookup"><span data-stu-id="3d54b-318">Replace Instance</span></span> | <span data-ttu-id="3d54b-319">Zamienia wystąpienie obiektu na nowe podane wartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="3d54b-319">Replaces the Object Instance with the new provided resource values.</span></span>
| <span data-ttu-id="3d54b-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="3d54b-320">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> |  <span data-ttu-id="3d54b-321">Zastąp zasób</span><span class="sxs-lookup"><span data-stu-id="3d54b-321">Replace Resource</span></span> | <span data-ttu-id="3d54b-322">Zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów).</span><span class="sxs-lookup"><span data-stu-id="3d54b-322">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="3d54b-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span><span class="sxs-lookup"><span data-stu-id="3d54b-323">**NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE**</span></span> | <span data-ttu-id="3d54b-324">Utwórz wystąpienie</span><span class="sxs-lookup"><span data-stu-id="3d54b-324">Create Instance</span></span> | <span data-ttu-id="3d54b-325">Inicjuje nowo utworzone wystąpienie obiektu o podanych wartościach zasobów (wywołanych z metody **_nx_lwm2m_object_create_** ).</span><span class="sxs-lookup"><span data-stu-id="3d54b-325">Initializes the newly created Object Instance with the provided resource values (called from the **_nx_lwm2m_object_create_** method).</span></span> |
| <span data-ttu-id="3d54b-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="3d54b-326">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="3d54b-327">Zapis ładowania początkowego</span><span class="sxs-lookup"><span data-stu-id="3d54b-327">Bootstrap Write</span></span> | <span data-ttu-id="3d54b-328">Wywoływana podczas sekwencji ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="3d54b-328">Called during Bootstrap sequence.</span></span> |

### <a name="the-execute-method"></a><span data-ttu-id="3d54b-329">Metoda "Execute"</span><span class="sxs-lookup"><span data-stu-id="3d54b-329">The ‘Execute’ Method</span></span>

<span data-ttu-id="3d54b-330">Metoda "Execute" implementuje wykonywanie zasobu obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-330">The ‘Execute’ method implements the execution of an Object Resource.</span></span>

<span data-ttu-id="3d54b-331">Parametry wejściowe są zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3d54b-331">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="3d54b-332">Parametr</span><span class="sxs-lookup"><span data-stu-id="3d54b-332">Parameter</span></span>  | <span data-ttu-id="3d54b-333">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-333">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-334">**operacje**</span><span class="sxs-lookup"><span data-stu-id="3d54b-334">**operation**</span></span> | <span data-ttu-id="3d54b-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="3d54b-335">NX_LWM2M_CLIENT_OBJECT_EXECUTE</span></span> |
| <span data-ttu-id="3d54b-336">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-336">**object_ptr**</span></span> | <span data-ttu-id="3d54b-337">Wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-337">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="3d54b-338">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-338">**instance_ptr**</span></span> | <span data-ttu-id="3d54b-339">Wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-339">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="3d54b-340">**zasoby**</span><span class="sxs-lookup"><span data-stu-id="3d54b-340">**resource**</span></span> | <span data-ttu-id="3d54b-341">Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-341">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="3d54b-342">Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.</span><span class="sxs-lookup"><span data-stu-id="3d54b-342">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="3d54b-343">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="3d54b-343">**resource_count**</span></span> | <span data-ttu-id="3d54b-344">Wskaźnik na liczbę zasobów do odnalezienia.</span><span class="sxs-lookup"><span data-stu-id="3d54b-344">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="3d54b-345">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-345">**args_ptr**</span></span> | <span data-ttu-id="3d54b-346">Wskaźnik do argumentów.</span><span class="sxs-lookup"><span data-stu-id="3d54b-346">Pointer to the arguments.</span></span> |
| <span data-ttu-id="3d54b-347">**args_length**</span><span class="sxs-lookup"><span data-stu-id="3d54b-347">**args_length**</span></span> | <span data-ttu-id="3d54b-348">Długość argumentów.</span><span class="sxs-lookup"><span data-stu-id="3d54b-348">The length of the arguments.</span></span>  |

<span data-ttu-id="3d54b-349">Funkcja musi zwrócić **NX_LWM2M_CLIENT_NOT_FOUND** , jeśli identyfikator zasobu nie istnieje lub **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** , jeśli nie obsługuje wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-349">The function must return **NX_LWM2M_CLIENT_NOT_FOUND** if the Resource ID doesn’t exist, or **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** if it doesn’t support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="3d54b-350">Metoda "Create"</span><span class="sxs-lookup"><span data-stu-id="3d54b-350">The ‘Create’ Method</span></span>

<span data-ttu-id="3d54b-351">Metoda "Create" implementuje Tworzenie nowego wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-351">The ‘Create’ method implements the creation of a new Object Instance.</span></span>

<span data-ttu-id="3d54b-352">Parametry wejściowe są zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3d54b-352">The input parameters are defined as follows.</span></span>

| <span data-ttu-id="3d54b-353">Parametr</span><span class="sxs-lookup"><span data-stu-id="3d54b-353">Parameter</span></span>  | <span data-ttu-id="3d54b-354">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-354">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-355">**operacje**</span><span class="sxs-lookup"><span data-stu-id="3d54b-355">**operation**</span></span> | <span data-ttu-id="3d54b-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span><span class="sxs-lookup"><span data-stu-id="3d54b-356">**NX_LWM2M_CLIENT_OBJECT_CREATE**</span></span> |
| <span data-ttu-id="3d54b-357">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-357">**object_ptr**</span></span> | <span data-ttu-id="3d54b-358">Wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-358">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="3d54b-359">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-359">**instance_ptr**</span></span> | <span data-ttu-id="3d54b-360">Nieużywany parametr.</span><span class="sxs-lookup"><span data-stu-id="3d54b-360">Unused parameter.</span></span> |
| <span data-ttu-id="3d54b-361">**zasoby**</span><span class="sxs-lookup"><span data-stu-id="3d54b-361">**resource**</span></span> | <span data-ttu-id="3d54b-362">Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="3d54b-362">Pointer to an array of **NX_LWM2M_CLIENT_RESOURCE** containing the IDs of the resources to read.</span></span> <span data-ttu-id="3d54b-363">Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.</span><span class="sxs-lookup"><span data-stu-id="3d54b-363">On return the array is filled with corresponding types and values.</span></span> |
| <span data-ttu-id="3d54b-364">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="3d54b-364">**resource_count**</span></span> | <span data-ttu-id="3d54b-365">Wskaźnik na liczbę zasobów do odnalezienia.</span><span class="sxs-lookup"><span data-stu-id="3d54b-365">Pointer to the number of resources to discover.</span></span> |
| <span data-ttu-id="3d54b-366">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-366">**args_ptr**</span></span> | <span data-ttu-id="3d54b-367">Identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-367">Object instance id.</span></span> |
| <span data-ttu-id="3d54b-368">**args_length**</span><span class="sxs-lookup"><span data-stu-id="3d54b-368">**args_length**</span></span> | <span data-ttu-id="3d54b-369">Długość argumentów.</span><span class="sxs-lookup"><span data-stu-id="3d54b-369">The length of the arguments.</span></span> |

### <a name="the-delete-method"></a><span data-ttu-id="3d54b-370">Metoda "Delete"</span><span class="sxs-lookup"><span data-stu-id="3d54b-370">The ‘Delete’ Method</span></span>

<span data-ttu-id="3d54b-371">Metoda "Delete" implementuje usuwanie wystąpienia obiektu. parametry wejściowe są zdefiniowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3d54b-371">The ‘Delete’ method implements the deletion of an object instance, the input parameters are defined as follows.</span></span>

| <span data-ttu-id="3d54b-372">Parametr</span><span class="sxs-lookup"><span data-stu-id="3d54b-372">Parameter</span></span>  | <span data-ttu-id="3d54b-373">Opis</span><span class="sxs-lookup"><span data-stu-id="3d54b-373">Description</span></span> |
| --- | --- |
| <span data-ttu-id="3d54b-374">**operacje**</span><span class="sxs-lookup"><span data-stu-id="3d54b-374">**operation**</span></span> | <span data-ttu-id="3d54b-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span><span class="sxs-lookup"><span data-stu-id="3d54b-375">NX_LWM2M_CLIENT_OBJECT_DELETE</span></span> |
| <span data-ttu-id="3d54b-376">**object_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-376">**object_ptr**</span></span> | <span data-ttu-id="3d54b-377">Wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-377">Pointer to the Object implementation.</span></span> |
| <span data-ttu-id="3d54b-378">**instance_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-378">**instance_ptr**</span></span> | <span data-ttu-id="3d54b-379">Wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="3d54b-379">Pointer to the Object Instance.</span></span> |
| <span data-ttu-id="3d54b-380">**zasoby**</span><span class="sxs-lookup"><span data-stu-id="3d54b-380">**resource**</span></span> | <span data-ttu-id="3d54b-381">Nieużywany parametr.</span><span class="sxs-lookup"><span data-stu-id="3d54b-381">Unused parameter.</span></span> |
| <span data-ttu-id="3d54b-382">**resource_count**</span><span class="sxs-lookup"><span data-stu-id="3d54b-382">**resource_count**</span></span> | <span data-ttu-id="3d54b-383">Nieużywany parametr.</span><span class="sxs-lookup"><span data-stu-id="3d54b-383">Unused parameter.</span></span> |
| <span data-ttu-id="3d54b-384">**args_ptr**</span><span class="sxs-lookup"><span data-stu-id="3d54b-384">**args_ptr**</span></span> | <span data-ttu-id="3d54b-385">Nieużywany parametr.</span><span class="sxs-lookup"><span data-stu-id="3d54b-385">Unused parameter.</span></span> |
| <span data-ttu-id="3d54b-386">**args_length**</span><span class="sxs-lookup"><span data-stu-id="3d54b-386">**args_length**</span></span> | <span data-ttu-id="3d54b-387">Nieużywany parametr.</span><span class="sxs-lookup"><span data-stu-id="3d54b-387">Unused parameter.</span></span> |

<span data-ttu-id="3d54b-388">Po powodzeniu obiekt musi zwolnić dane wystąpienia obiektu i wszelkie inne zasoby przydzielone przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="3d54b-388">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="3d54b-389">Przykład aplikacji klienckiej LWM2M</span><span class="sxs-lookup"><span data-stu-id="3d54b-389">Example of LWM2M Client Application</span></span>

<span data-ttu-id="3d54b-390">Poniższy kod jest przykładem prostej aplikacji klienckiej LWM2M, która implementuje urządzenie niestandardowe składające się z czujnika temperatury i przełącznika oświetlenia.</span><span class="sxs-lookup"><span data-stu-id="3d54b-390">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="3d54b-391">Urządzenie umożliwia serwerowi Odczytywanie wartości czujnika temperatury i stanu logicznego przełącznika światła oraz ustawienie opcji przełączania światła na Włącz/Wyłącz.</span><span class="sxs-lookup"><span data-stu-id="3d54b-391">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```