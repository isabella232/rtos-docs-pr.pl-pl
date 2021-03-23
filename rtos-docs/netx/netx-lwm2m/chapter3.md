---
title: Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX LWM2M
description: Ten rozdział zawiera opis funkcjonalny usługi Azure RTO NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822584"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="8f782-103">Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX LWM2M</span><span class="sxs-lookup"><span data-stu-id="8f782-103">Chapter 3 - Functional description of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="8f782-104">Ten rozdział zawiera opis funkcjonalny usługi Azure RTO NetX LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-104">This chapter contains a functional description of Azure RTOS NetX LWM2M.</span></span>

## <a name="lwm2m-client-initialization"></a><span data-ttu-id="8f782-105">LWM2M inicjowanie klienta</span><span class="sxs-lookup"><span data-stu-id="8f782-105">LWM2M Client Initialization</span></span>

<span data-ttu-id="8f782-106">Klient LWM2M jest inicjowany przez wywołanie usługi ***nx_lwm2m_client_create*** .</span><span class="sxs-lookup"><span data-stu-id="8f782-106">The LWM2M Client is initialized by calling ***nx_lwm2m_client_create*** service.</span></span> <span data-ttu-id="8f782-107">Klient LWM2M działa we własnym wątku i może zgłosić pewne zdarzenia do aplikacji za pomocą wywołań zwrotnych lub przez wywołanie metod niestandardowych obiektów wdrożonych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8f782-107">The LWM2M Client runs in its own thread and can report some events to the application through the use of callbacks, or by calling methods of the custom objects implemented by the application.</span></span>

<span data-ttu-id="8f782-108">Ponadto należy utworzyć sesje klienta LWM2M przez wywołanie ***nx_lwm2m_client_session_create*** w celu włączenia komunikacji z co najmniej jednym serwerem.</span><span class="sxs-lookup"><span data-stu-id="8f782-108">In addition, LWM2M Client Sessions must be created by calling ***nx_lwm2m_client_session_create*** for enabling communication with one or more servers.</span></span> <span data-ttu-id="8f782-109">Sesja może komunikować się z dwoma różnymi typami serwerów: serwerem Bootstrap lub serwerem LWM2M (Zarządzanie urządzeniami).</span><span class="sxs-lookup"><span data-stu-id="8f782-109">A session can communicate with two different types of servers: a Bootstrap Server or a LWM2M Server (Device Management).</span></span>

### <a name="bootstrap-server-session"></a><span data-ttu-id="8f782-110">Sesja serwera Bootstrap</span><span class="sxs-lookup"><span data-stu-id="8f782-110">Bootstrap Server Session</span></span>

<span data-ttu-id="8f782-111">Sesja komunikacji z serwerem Bootstrap służy do aprowizacji najważniejszych informacji w kliencie LWM2M, aby umożliwić klientowi LWM2M wykonywanie operacji "Register" z co najmniej jednym serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-111">A communication session with a Bootstrap Server is used to provision essential information into the LWM2M Client to enable the LWM2M Client to perform the operation "Register" with one or more LWM2M Servers.</span></span> <span data-ttu-id="8f782-112">Ten typ serwera jest używany podczas inicjowania klienta i inicjowanego przez serwer trybów ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="8f782-112">This type of server is used during the Client Initiated and Server Initiated Bootstrap modes.</span></span>

<span data-ttu-id="8f782-113">Aplikacja może uruchomić sesję ładowania początkowego przez wywołanie ***nx_lwm2m_client_session_bootstrap** _ lub _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, musi podać adres IP i numer portu serwera oraz opcjonalny identyfikator wystąpienia obiektu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8f782-113">The application can start a Bootstrap session by calling ***nx_lwm2m_client_session_bootstrap** _ or _*_nx_lwm2m_client_session_bootstrap_dtls_\*_, it must provide the IP address and port number of the server, and an optional Security Object Instance ID.</span></span> <span data-ttu-id="8f782-114">Funkcja _*_nx_lwm2m_client_session_bootstrap_*_ używa niezabezpieczonej komunikacji, natomiast _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* nawiązuje bezpieczne połączenie DTLS z serwerem.</span><span class="sxs-lookup"><span data-stu-id="8f782-114">The _*_nx_lwm2m_client_session_bootstrap_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_bootstrap_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="8f782-115">Jeśli operacja ładowania początkowego zakończyła się powodzeniem, serwer Bootstrap powinien mieć utworzone wystąpienia obiektów zabezpieczeń dla serwerów Bootstrap i LWM2M oraz wystąpienia obiektów serwera dla serwerów LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-115">If the Bootstrap operation is successful, the Bootstrap server should have created Security Object Instance(s) for the Bootstrap and LWM2M Servers, and Server Object Instance(s) for the LWM2M Servers.</span></span> <span data-ttu-id="8f782-116">Aplikacja musi używać tych informacji do ustanawiania sesji z serwerami LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-116">The application must use this information for establishing a session with the LWM2M Server(s).</span></span>

<span data-ttu-id="8f782-117">Dane ładowania początkowego powinny zostać zapisane w pamięci nieulotnej przez aplikację w celu skonfigurowania klienta LWM2M przy następnym ponownym uruchomieniu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="8f782-117">The Bootstrap data should be saved to non-volatile memory by the application in order to configure the LWM2M Client at the next reboot of the device.</span></span>

### <a name="lwm2m-server-session"></a><span data-ttu-id="8f782-118">Sesja serwera LWM2M</span><span class="sxs-lookup"><span data-stu-id="8f782-118">LWM2M Server Session</span></span>

<span data-ttu-id="8f782-119">Sesja komunikacji z serwerem LWM2M jest używana do rejestracji, zarządzania urządzeniami i włączania usług.</span><span class="sxs-lookup"><span data-stu-id="8f782-119">A communication session with a LWM2M Server is used for Registration, Device Management and Service Enablement.</span></span>

<span data-ttu-id="8f782-120">Aplikacja może zarejestrować klienta LWM2M na serwerze, wywołując ***nx_lwm2m_client_session_register** _ lub _*_nx_lwm2m_client_session_register_dtls_\*_, musi podać adres IP i numer portu serwera oraz krótki identyfikator serwera, który odpowiada istniejącemu wystąpieniu obiektu serwera.</span><span class="sxs-lookup"><span data-stu-id="8f782-120">The application can register the LWM2M Client to a server by calling ***nx_lwm2m_client_session_register** _ or _*_nx_lwm2m_client_session_register_dtls_\*_, it must provide the IP address and port number of the server, and the Short Server ID which corresponds to an existing Server Object Instance.</span></span> <span data-ttu-id="8f782-121">Funkcja _*_nx_lwm2m_client_session_register_*_ używa niezabezpieczonej komunikacji, natomiast _ *_nx_lwm2m_client_session_register_dtls_*\* nawiązuje bezpieczne połączenie DTLS z serwerem.</span><span class="sxs-lookup"><span data-stu-id="8f782-121">The _*_nx_lwm2m_client_session_register_*_ function uses insecure communication, whereas _ *_nx_lwm2m_client_session_register_dtls_*\* establishes a secure DTLS connection with the server.</span></span>

<span data-ttu-id="8f782-122">Aplikacja może wyrejestrować klienta LWM2M przez wywołanie \***nx_lwm2m_client_session_deregister** _ i poproszenie klienta o wysłanie komunikatu "Update" przez wywołanie _ *_nx_lwm2m_client_session_update_* \*.</span><span class="sxs-lookup"><span data-stu-id="8f782-122">The application can de-register the LWM2M Client by calling ***nx_lwm2m_client_session_deregister** _, and ask the client to send an 'Update' message by calling _*_nx_lwm2m_client_session_update_\*\*.</span></span>

### <a name="session-state-callback"></a><span data-ttu-id="8f782-123">Wywołanie zwrotne stanu sesji</span><span class="sxs-lookup"><span data-stu-id="8f782-123">Session State Callback</span></span>

<span data-ttu-id="8f782-124">Aplikacja rejestruje wywołanie zwrotne podczas tworzenia sesji, która jest wywoływana w momencie aktualizacji stanu sesji, funkcja wywołania zwrotnego NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK ma następujący prototyp:</span><span class="sxs-lookup"><span data-stu-id="8f782-124">The application registers a callback at creation of a session which is called when the state of the session is updated, the callback function NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK has the following prototype:</span></span>

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

<span data-ttu-id="8f782-125">Zdefiniowane są następujące stany:</span><span class="sxs-lookup"><span data-stu-id="8f782-125">The following states are defined :</span></span>

- <span data-ttu-id="8f782-126">**NX_LWM2M_CLIENT_SESSION_INIT**: stan początkowy po utworzeniu sesji.</span><span class="sxs-lookup"><span data-stu-id="8f782-126">**NX_LWM2M_CLIENT_SESSION_INIT**: The initial state after session creation.</span></span>

- <span data-ttu-id="8f782-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: klient czeka na zakończenie okresu ważności czasomierza "wstrzymanie" lub zainicjowanie serwera.</span><span class="sxs-lookup"><span data-stu-id="8f782-127">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: The client is waiting for the expiration of the 'Hold Off' timer or Server Initiated Bootstrap.</span></span>

- <span data-ttu-id="8f782-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: klient wysłał komunikat "Request" do serwera Bootstrap (zainicjowany przez klienta).</span><span class="sxs-lookup"><span data-stu-id="8f782-128">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: The client has sent a 'Request' message to the Bootstrap Server (Client Initiated Bootstrap).</span></span>

- <span data-ttu-id="8f782-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: klient otrzymuje dane z serwera Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="8f782-129">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: The client is receiving data from the Bootstrap Server.</span></span>

- <span data-ttu-id="8f782-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: serwer ładowania początkowego wysłał komunikat "gotowe".</span><span class="sxs-lookup"><span data-stu-id="8f782-130">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: The Bootstrap Server has sent a 'Finished' message.</span></span>

- <span data-ttu-id="8f782-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: sesja ładowania początkowego zakończyła się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8f782-131">**NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: The bootstrap session has failed.</span></span>

- <span data-ttu-id="8f782-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: klient wysłał komunikat "Register" do serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-132">**NX_LWM2M_CLIENT_SESSION_REGISTERING**: The client has sent a 'Register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="8f782-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: klient jest zarejestrowany na serwerze LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-133">**NX_LWM2M_CLIENT_SESSION_REGISTERED**: The client is registered to the LWM2M Server.</span></span>

- <span data-ttu-id="8f782-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: klient wysłał komunikat "Update" do serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-134">**NX_LWM2M_CLIENT_SESSION_UPDATING**: The client has sent an 'Update' message to the LWM2M Server.</span></span>

- <span data-ttu-id="8f782-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: klient wysłał komunikat "de-Register" do serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-135">**NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: The client has sent an 'De-register' message to the LWM2M Server.</span></span>

- <span data-ttu-id="8f782-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: klient jest Wyrejestrowanie z serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="8f782-136">**NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: The client is de-registered from the LWM2M Server.</span></span>

- <span data-ttu-id="8f782-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: serwer LWM2M jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="8f782-137">**NX_LWM2M_CLIENT_SESSION_DISABLED**: The LWM2M Server is disabled.</span></span> <span data-ttu-id="8f782-138">Po wygaśnięciu czasomierza Wyłącz zostanie wysłany komunikat "Register".</span><span class="sxs-lookup"><span data-stu-id="8f782-138">A 'Register' will be sent after the expiration of the disable timer.</span></span>

- <span data-ttu-id="8f782-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: operacja rejestracji lub aktualizacji na serwerze LWM2M nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="8f782-139">**NX_LWM2M_CLIENT_SESSION_ERROR**: The registration or update operation to the LWM2M Server has failed.</span></span>

- <span data-ttu-id="8f782-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: wystąpienie obiektu serwera odpowiadające serwerowi LWM2M zostało usunięte.</span><span class="sxs-lookup"><span data-stu-id="8f782-140">**NX_LWM2M_CLIENT_SESSION_DELETED**: The Server Object Instance corresponding to the LWM2M Server has been deleted.</span></span> <span data-ttu-id="8f782-141">W przypadku błędu aplikacja może pobrać przyczynę błędu przez wywołanie **_nx_lwm2m_client_session_error_get_**.</span><span class="sxs-lookup"><span data-stu-id="8f782-141">In case of error the application can retrieve the cause of the error by calling **_nx_lwm2m_client_session_error_get_**.</span></span>

## <a name="local-device-management"></a><span data-ttu-id="8f782-142">Zarządzanie urządzeniami lokalnymi</span><span class="sxs-lookup"><span data-stu-id="8f782-142">Local Device Management</span></span>

<span data-ttu-id="8f782-143">Aplikacja może uzyskiwać dostęp do obiektów klienta LWM2M za pomocą funkcji zarządzania urządzeniami lokalnymi.</span><span class="sxs-lookup"><span data-stu-id="8f782-143">The application can access the Objects of the LWM2M Client by using the local device management functions.</span></span> <span data-ttu-id="8f782-144">Dostępne są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="8f782-144">The following functions are provided:</span></span>

- <span data-ttu-id="8f782-145">***nx_lwm2m_client_object_read***: Odczytuj zasoby z wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-145">***nx_lwm2m_client_object_read***: Read resources from an Object Instance.</span></span>

- <span data-ttu-id="8f782-146">***nx_lwm2m_client_object_discover***: Pobierz listę zasobów wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-146">***nx_lwm2m_client_object_discover***: Get the list of the resources of an Object Instance.</span></span>

- <span data-ttu-id="8f782-147">***nx_lwm2m_client_object_write***: zapisywanie zasobów do wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="8f782-147">***nx_lwm2m_client_object_write***: Write resources to an Object Instance</span></span>

- <span data-ttu-id="8f782-148">***nx_lwm2m_client_object_execute***: wykonaj operację EXECUTE na zasobie wystąpienia obiektu Object.</span><span class="sxs-lookup"><span data-stu-id="8f782-148">***nx_lwm2m_client_object_execute***: Perform the Execute operation on a resource of an Object Instance.</span></span>

- <span data-ttu-id="8f782-149">***nx_lwm2m_client_object_create***: Utwórz nowe wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-149">***nx_lwm2m_client_object_create***: Create a new Object Instance.</span></span>

- <span data-ttu-id="8f782-150">***nx_lwm2m_client_object_delete***: Usuń istniejące wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-150">***nx_lwm2m_client_object_delete***: Delete an existing Object Instance.</span></span>

- <span data-ttu-id="8f782-151">***nx_lwm2m_client_object_get_next***: Pobierz następny identyfikator obiektu zaimplementowany przez klienta lwm2m.</span><span class="sxs-lookup"><span data-stu-id="8f782-151">***nx_lwm2m_client_object_get_next***: Get the next Object ID implemented by the LWM2M Client.</span></span>

- <span data-ttu-id="8f782-152">***nx_lwm2m_client_object_instance_get_next***: Pobierz następne wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-152">***nx_lwm2m_client_object_instance_get_next***: Get the next Instance of an Object.</span></span>

## <a name="resource-information"></a><span data-ttu-id="8f782-153">Informacje o zasobach</span><span class="sxs-lookup"><span data-stu-id="8f782-153">Resource Information</span></span>

<span data-ttu-id="8f782-154">Podczas odczytywania i zapisywania do obiektów zasób jest reprezentowany przez strukturę NX_LWM2M_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="8f782-154">When reading from and writing to Objects a Resource is represented by the NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="8f782-155">Ta struktura zawiera identyfikator zasobu/wystąpienia i jego wartość.</span><span class="sxs-lookup"><span data-stu-id="8f782-155">This structure contains the ID of the Resource/Instance and its value.</span></span> <span data-ttu-id="8f782-156">Kodowanie wartości zależy od jego typu i jego pochodzenia (aplikacji lub sieci).</span><span class="sxs-lookup"><span data-stu-id="8f782-156">The encoding of the value depends on its type and its origin (application or network).</span></span>

<span data-ttu-id="8f782-157">Struktura NX_LWM2M_RESOURCE ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-157">The NX_LWM2M_RESOURCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- <span data-ttu-id="8f782-158">**nx_lwm2m_resource_id**: Identyfikator zasobu lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8f782-158">**nx_lwm2m_resource_id**: The ID of the Resource or the Instance.</span></span>
- <span data-ttu-id="8f782-159">**nx_lwm2m_resource_type**: typ wartości, zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="8f782-159">**nx_lwm2m_resource_type**: The type of the value, see below.</span></span>
- <span data-ttu-id="8f782-160">**nx_lwm2m_resource_value**: wartość zasobu zależy od typu wartości.</span><span class="sxs-lookup"><span data-stu-id="8f782-160">**nx_lwm2m_resource_value**: The value of the Resource, depends on the type of the value.</span></span>

<span data-ttu-id="8f782-161">Zdefiniowano następujący typ wartości:</span><span class="sxs-lookup"><span data-stu-id="8f782-161">The following type of values are defined :</span></span>

- <span data-ttu-id="8f782-162">**NX_LWM2M_RESOURCE_NONE**: pusty zasób.</span><span class="sxs-lookup"><span data-stu-id="8f782-162">**NX_LWM2M_RESOURCE_NONE**: Empty resource.</span></span>

- <span data-ttu-id="8f782-163">**NX_LWM2M_RESOURCE_STRING**: wartość ciągu UTF-8 zakończona wartością null jest przechowywana w *nx_lwm2m_resource_stringdata*.</span><span class="sxs-lookup"><span data-stu-id="8f782-163">**NX_LWM2M_RESOURCE_STRING**: A null-terminated UTF-8 string value stored in *nx_lwm2m_resource_stringdata*.</span></span>

- <span data-ttu-id="8f782-164">**NX_LWM2M_RESOURCE_INTEGER32**: 32-bitowej wartości całkowitej przechowywanej w *nx_lwm2m_resource_integer32data*.</span><span class="sxs-lookup"><span data-stu-id="8f782-164">**NX_LWM2M_RESOURCE_INTEGER32**: A 32-Bit Integer value stored in *nx_lwm2m_resource_integer32data*.</span></span>

- <span data-ttu-id="8f782-165">**NX_LWM2M_RESOURCE_INTEGER64**: 64-bitowej wartości całkowitej przechowywanej w *nx_lwm2m_resource_integer64data*.</span><span class="sxs-lookup"><span data-stu-id="8f782-165">**NX_LWM2M_RESOURCE_INTEGER64**: A 64-Bit Integer value stored in *nx_lwm2m_resource_integer64data*.</span></span>

- <span data-ttu-id="8f782-166">**NX_LWM2M_RESOURCE_FLOAT32**: 32-bitowej wartości zmiennoprzecinkowej przechowywanej w *nx_lwm2m_resource_float32data*.</span><span class="sxs-lookup"><span data-stu-id="8f782-166">**NX_LWM2M_RESOURCE_FLOAT32**: A 32-Bit Floating Point value stored in *nx_lwm2m_resource_float32data*.</span></span>

- <span data-ttu-id="8f782-167">**NX_LWM2M_RESOURCE_FLOAT64**: 64-bitowej wartości zmiennoprzecinkowej przechowywanej w *nx_lwm2m_resource_float64data*.</span><span class="sxs-lookup"><span data-stu-id="8f782-167">**NX_LWM2M_RESOURCE_FLOAT64**: A 64-Bit Floating Point value stored in *nx_lwm2m_resource_float64data*.</span></span>

- <span data-ttu-id="8f782-168">**NX_LWM2M_RESOURCE_BOOLEAN**: wartość logiczna przechowywana w *nx_lwm2m_resource_booleandata*.</span><span class="sxs-lookup"><span data-stu-id="8f782-168">**NX_LWM2M_RESOURCE_BOOLEAN**: A Boolean value stored in *nx_lwm2m_resource_booleandata*.</span></span>

- <span data-ttu-id="8f782-169">**NX_LWM2M_RESOURCE_OPAQUE**: wartość nieprzezroczysta zdefiniowana przez *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="8f782-169">**NX_LWM2M_RESOURCE_OPAQUE**: An Opaque value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="8f782-170">**NX_LWM2M_RESOURCE_OBJLNK**: wartość linku obiektu przechowywana w *nx_lwm2m_resource_objlnkdata*.</span><span class="sxs-lookup"><span data-stu-id="8f782-170">**NX_LWM2M_RESOURCE_OBJLNK**: An Object Link value stored in *nx_lwm2m_resource_objlnkdata*.</span></span>

- <span data-ttu-id="8f782-171">**NX_LWM2M_RESOURCE_TLV**: wartość zakodowana przez element TLV zdefiniowana przez *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="8f782-171">**NX_LWM2M_RESOURCE_TLV**: A TLV encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="8f782-172">**NX_LWM2M_RESOURCE_TEXT**: wartość zakodowana Plain-Text zdefiniowana przez *nx_lwm2m_resource_bufferdata*.</span><span class="sxs-lookup"><span data-stu-id="8f782-172">**NX_LWM2M_RESOURCE_TEXT**: A Plain-Text encoded value defined by *nx_lwm2m_resource_bufferdata*.</span></span>

- <span data-ttu-id="8f782-173">**NX_LWM2M_RESOURCE_MULTIPLE**: wiele zasobów zdefiniowanych przez *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="8f782-173">**NX_LWM2M_RESOURCE_MULTIPLE**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="8f782-174">*nx_lwm2m_resource_multiple_ptr* jest wskaźnikiem do tablicy struktur **NX_LWM2M_RESOURCE** zawierających informacje o poszczególnych wystąpieniach zasobów.</span><span class="sxs-lookup"><span data-stu-id="8f782-174">*nx_lwm2m_resource_multiple_ptr* is a pointer to an array of **NX_LWM2M_RESOURCE** structures containing information about each Resource Instances.</span></span>

- <span data-ttu-id="8f782-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: wiele zasobów zdefiniowanych przez *nx_lwm2m_resource_multipledata*.</span><span class="sxs-lookup"><span data-stu-id="8f782-175">**NX_LWM2M_RESOURCE_MULTIPLE_TLV**: A Multiple Resource defined by *nx_lwm2m_resource_multipledata*.</span></span> <span data-ttu-id="8f782-176">*nx_lwm2m_resource_multiple_ptr* jest wskaźnikiem do buforu zakodowanego za pomocą obiektu TLV.</span><span class="sxs-lookup"><span data-stu-id="8f782-176">*nx_lwm2m_resource_multiple_ptr* is a pointer to a TLV encoded buffer.</span></span>

<span data-ttu-id="8f782-177">W celu pobrania wartości i sprawdzenia jej typu aplikacja nie powinna bezpośrednio uzyskiwać dostępu do pola *nx_lwm2m_resource_value* podczas pobierania wartości ze struktury NX_LWM2M_RESOURCE.</span><span class="sxs-lookup"><span data-stu-id="8f782-177">Convenience functions are provided for retrieving the value and checking its type, the application should never directly access the *nx_lwm2m_resource_value* field when getting a value from a NX_LWM2M_RESOURCE structure.</span></span> <span data-ttu-id="8f782-178">Zdefiniowane są następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="8f782-178">The following functions are defined :</span></span>

- <span data-ttu-id="8f782-179">***nx_lwm2m_resource_get_***: Pobierz wartość o podanym typie.</span><span class="sxs-lookup"><span data-stu-id="8f782-179">***nx_lwm2m_resource_get_***: Get a value with the given type.</span></span>
- <span data-ttu-id="8f782-180">***nx_lwm2m_resource_multiple_get_***: Pobierz wartość o danym typie z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="8f782-180">***nx_lwm2m_resource_multiple_get_***: Get a value with the given type from a Multiple Resource.</span></span>

<span data-ttu-id="8f782-181">Makro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(typ) może służyć do sprawdzenia, czy typem zasobu jest wiele zasobów.</span><span class="sxs-lookup"><span data-stu-id="8f782-181">The macro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(type) can be used to check if a resource type is a Multiple Resource.</span></span>

## <a name="object-implementation"></a><span data-ttu-id="8f782-182">Implementacja obiektu</span><span class="sxs-lookup"><span data-stu-id="8f782-182">Object Implementation</span></span>

<span data-ttu-id="8f782-183">Klient LWM2M implementuje wymagane obiekty LWM2M OMA: Security (0), Server (1), Access Control (2) i Device (3).</span><span class="sxs-lookup"><span data-stu-id="8f782-183">The LWM2M Client implements the mandatory OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="8f782-184">Inne obiekty specyficzne dla urządzenia muszą być implementowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8f782-184">Other device specific objects must be implemented by the application.</span></span>

<span data-ttu-id="8f782-185">Do zdefiniowania obiektu służą dwie struktury danych: Struktura NX_LWM2M_OBJECT definiuje implementację obiektu, łącznie z IDENTYFIKATORem obiektu i metodami obiektu, a struktura NX_LWM2M_OBJECT_INSTANCE zawiera dane wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-185">Two data structures are used to define an Object: the NX_LWM2M_OBJECT structure defines the Object implementation, including the Object ID and the object methods, and the NX_LWM2M_OBJECT_INSTANCE structure contains the data of an Object Instance.</span></span>

<span data-ttu-id="8f782-186">Struktura NX_LWM2M_OBJECT ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-186">The NX_LWM2M_OBJECT structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- <span data-ttu-id="8f782-187">**nx_lwm2m_object_next**: Następny obiekt na liście.</span><span class="sxs-lookup"><span data-stu-id="8f782-187">**nx_lwm2m_object_next**: The next object in the list.</span></span>
- <span data-ttu-id="8f782-188">**nx_lwm2m_object_id**: identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-188">**nx_lwm2m_object_id**: The Object ID.</span></span>
- <span data-ttu-id="8f782-189">**nx_lwm2m_object_read**: Metoda "read", patrz poniżej.</span><span class="sxs-lookup"><span data-stu-id="8f782-189">**nx_lwm2m_object_read**: The 'Read' method, see below.</span></span>
- <span data-ttu-id="8f782-190">**nx_lwm2m_object_discover**: Metoda "Discovery", patrz poniżej.</span><span class="sxs-lookup"><span data-stu-id="8f782-190">**nx_lwm2m_object_discover**: The 'Discover' method, see below.</span></span>
- <span data-ttu-id="8f782-191">**nx_lwm2m_object_write**: Metoda "Write", patrz poniżej.</span><span class="sxs-lookup"><span data-stu-id="8f782-191">**nx_lwm2m_object_write**: The 'Write' method, see below.</span></span>
- <span data-ttu-id="8f782-192">**nx_lwm2m_object_execute**: Metoda "Execute", patrz poniżej.</span><span class="sxs-lookup"><span data-stu-id="8f782-192">**nx_lwm2m_object_execute**: The 'Execute' method, see below.</span></span>
- <span data-ttu-id="8f782-193">**nx_lwm2m_object_create**: Metoda "Create", patrz poniżej.</span><span class="sxs-lookup"><span data-stu-id="8f782-193">**nx_lwm2m_object_create**: The 'Create' method, see below.</span></span>
- <span data-ttu-id="8f782-194">**nx_lwm2m_object_delete**: Metoda "Delete", patrz poniżej.</span><span class="sxs-lookup"><span data-stu-id="8f782-194">**nx_lwm2m_object_delete**: The 'Delete' method, see below.</span></span>
- <span data-ttu-id="8f782-195">**nx_lwm2m_object_instances**: Lista wystąpień obiektów zakończonych znakiem null.</span><span class="sxs-lookup"><span data-stu-id="8f782-195">**nx_lwm2m_object_instances**: The NULL-terminated list of object instances.</span></span>

<span data-ttu-id="8f782-196">Struktura NX_LWM2M_OBJECT_INSTANCE ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-196">The NX_LWM2M_OBJECT_INSTANCE structure has the following definition:</span></span>

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- <span data-ttu-id="8f782-197">**nx_lwm2m_object_instance_next**: następne wystąpienie z listy.</span><span class="sxs-lookup"><span data-stu-id="8f782-197">**nx_lwm2m_object_instance_next**: The next instance in the list.</span></span>
- <span data-ttu-id="8f782-198">**nx_lwm2m_object_instance_id**: identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-198">**nx_lwm2m_object_instance_id**: The Object Instance ID.</span></span>

<span data-ttu-id="8f782-199">Obiekt musi implementować metody odpowiadające operacjom zdefiniowanym przez interfejs zarządzania urządzeniami LWM2M: "read", "Discovery", "Write", "Execute", "Create" i "Delete".</span><span class="sxs-lookup"><span data-stu-id="8f782-199">The Object must implement the methods corresponding to the operations defined by the LWM2M Device Management Interface: 'Read', 'Discover', 'Write', 'Execute', 'Create' and 'Delete'.</span></span> <span data-ttu-id="8f782-200">Metody "Create" i "Delete" można ustawić na wartość NULL, jeśli obiekt nie obsługuje dynamicznego tworzenia wystąpień.</span><span class="sxs-lookup"><span data-stu-id="8f782-200">The 'Create' and 'Delete' methods can be set to NULL if the object doesn't support dynamic creation of instances.</span></span>

### <a name="the-read-method"></a><span data-ttu-id="8f782-201">Metoda "read"</span><span class="sxs-lookup"><span data-stu-id="8f782-201">The 'Read' Method</span></span>

<span data-ttu-id="8f782-202">Metoda "read" służy do odczytywania wartości zasobów z wystąpienia obiektu, funkcja ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-202">The 'Read' method is used to read Resource values from an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

<span data-ttu-id="8f782-203">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f782-203">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8f782-204">**object_ptr**: wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-204">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="8f782-205">**instance_ptr**: wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-205">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="8f782-206">**num_values**: liczba zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="8f782-206">**num_values**: The number of resources to read.</span></span>

- <span data-ttu-id="8f782-207">**values_ptr**: wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="8f782-207">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="8f782-208">Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.</span><span class="sxs-lookup"><span data-stu-id="8f782-208">On return the array is filled with the corresponding types and values.</span></span>

### <a name="the-discover-method"></a><span data-ttu-id="8f782-209">Metoda "Discovery"</span><span class="sxs-lookup"><span data-stu-id="8f782-209">The 'Discover' Method</span></span>

<span data-ttu-id="8f782-210">Metoda "Discovery" służy do pobierania listy wszystkich zasobów zaimplementowanych przez obiekt, funkcja ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-210">The 'Discover' method is used to retrieve the list of all Resources implemented by an Object, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

<span data-ttu-id="8f782-211">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f782-211">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8f782-212">**object_ptr**: wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-212">**object_ptr**: Pointer to the Object implementation.</span></span>

- <span data-ttu-id="8f782-213">**instance_ptr**: wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-213">**instance_ptr**: Pointer to the Object Instance.</span></span>

- <span data-ttu-id="8f782-214">**num_resources_ptr**: przy wprowadzaniu rozmiaru buforu docelowego w danych wyjściowych liczba elementów WRITEN do buforu.</span><span class="sxs-lookup"><span data-stu-id="8f782-214">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>

- <span data-ttu-id="8f782-215">**resources_ptr**: wskaźnik do bufora docelowego.</span><span class="sxs-lookup"><span data-stu-id="8f782-215">**resources_ptr**: Pointer to the destination buffer.</span></span>

<span data-ttu-id="8f782-216">Informacje o zasobie są zwracane w strukturze NX_LWM2M_RESOURCE_INFO zdefiniowanej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f782-216">The resource information is returned in a NX_LWM2M_RESOURCE_INFO structure defined as follows:</span></span>

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- <span data-ttu-id="8f782-217">**nx_lwm2m_resource_info_id**: Identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="8f782-217">**nx_lwm2m_resource_info_id**: The ID of the Resource.</span></span>

- <span data-ttu-id="8f782-218">**nx_lwm2m_resource_info_flags**: Zobacz poniżej.</span><span class="sxs-lookup"><span data-stu-id="8f782-218">**nx_lwm2m_resource_info_flags**: See below.</span></span>

- <span data-ttu-id="8f782-219">**nx_lwm2m_resource_info_dim**: wymiar wielu zasobów, jeśli flaga NX_LWM2M_RESOURCE_INFO_MULTIPLE jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="8f782-219">**nx_lwm2m_resource_info_dim**: The dimension of Multiple Resource if the flag NX_LWM2M_RESOURCE_INFO_MULTIPLE is set.</span></span>

<span data-ttu-id="8f782-220">Pole *nx_lwm2m_resource_flags* może mieć następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="8f782-220">The field *nx_lwm2m_resource_flags* can have to the following values:</span></span>

- <span data-ttu-id="8f782-221">0: pojedynczy możliwy do odczytu zasób.</span><span class="sxs-lookup"><span data-stu-id="8f782-221">0: Single readable resource.</span></span>

- <span data-ttu-id="8f782-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: należy zdefiniować wiele zasobów, *nx_lwm2m_resource_info_dim* .</span><span class="sxs-lookup"><span data-stu-id="8f782-222">**NX_LWM2M_RESOURCE_INFO_MULTIPLE**: Multiple Resource, *nx_lwm2m_resource_info_dim* must be defined.</span></span>

- <span data-ttu-id="8f782-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: plik wykonywalny lub niemożliwy do odczytu.</span><span class="sxs-lookup"><span data-stu-id="8f782-223">**NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: Executable or Non-Readable Resource.</span></span>

### <a name="the-write-method"></a><span data-ttu-id="8f782-224">Metoda "Write"</span><span class="sxs-lookup"><span data-stu-id="8f782-224">The 'Write' Method</span></span>

<span data-ttu-id="8f782-225">Metoda "Write" służy do aktualizowania lub zastępowania zasobów wystąpienia obiektu, funkcja ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-225">The 'Write' method is used to update or replace resources of an Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

<span data-ttu-id="8f782-226">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f782-226">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8f782-227">**object_ptr**: wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-227">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="8f782-228">**instance_ptr**: wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-228">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="8f782-229">**num_values**: liczba zasobów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="8f782-229">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="8f782-230">**values_ptr**: wskaźnik do wartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="8f782-230">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="8f782-231">**write_op**: typ operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="8f782-231">**write_op**: The type of write operations.</span></span>

<span data-ttu-id="8f782-232">Do *write_op* parametru można określić następujące operacje zapisu:</span><span class="sxs-lookup"><span data-stu-id="8f782-232">The following write operations can be specified to the *write_op* parameter :</span></span>

- <span data-ttu-id="8f782-233">0 &mdash; aktualizacja częściowa: dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian.</span><span class="sxs-lookup"><span data-stu-id="8f782-233">0 &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="8f782-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Zamień wystąpienie: zamienia wystąpienie obiektu na nowe podane wartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="8f782-234">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="8f782-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Zastąp zasób: zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów).</span><span class="sxs-lookup"><span data-stu-id="8f782-235">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="8f782-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Utwórz wystąpienie: inicjuje nowo utworzone wystąpienie obiektu o podanych wartościach zasobów (wywołanych z metody *nx_lwm2m_object_create* ).</span><span class="sxs-lookup"><span data-stu-id="8f782-236">**NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Create Instance: initializes the newly created Object Instance with the provided resource values (called from the *nx_lwm2m_object_create* method).</span></span>

- <span data-ttu-id="8f782-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Zapis ładowania początkowego: wywoływany podczas sekwencji ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="8f782-237">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: called during Bootstrap sequence.</span></span>

### <a name="the-execute-method"></a><span data-ttu-id="8f782-238">Metoda "Execute"</span><span class="sxs-lookup"><span data-stu-id="8f782-238">The 'Execute' Method</span></span>

<span data-ttu-id="8f782-239">Metoda "Execute" implementuje wykonywanie zasobu obiektu, a funkcja ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-239">The 'Execute' method implements the execution of an Object Resource, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

<span data-ttu-id="8f782-240">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f782-240">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8f782-241">**object_ptr**: wskaźnik do implementacji obiektu</span><span class="sxs-lookup"><span data-stu-id="8f782-241">**object_ptr**: Pointer to the Object implementation</span></span>
- <span data-ttu-id="8f782-242">**instance_ptr**: wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-242">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="8f782-243">**resource_id**: Identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="8f782-243">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="8f782-244">**arguments_ptr**: wskaźnik do argumentów operacji Execute.</span><span class="sxs-lookup"><span data-stu-id="8f782-244">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="8f782-245">Może mieć wartość NULL, jeśli *arguments_length* wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="8f782-245">Can be NULL if *arguments_length* is zero.</span></span>
- <span data-ttu-id="8f782-246">**arguments_length**: długość argumentów.</span><span class="sxs-lookup"><span data-stu-id="8f782-246">**arguments_length**: The length of the arguments.</span></span>

<span data-ttu-id="8f782-247">Funkcja musi zwrócić NX_LWM2M_NOT_FOUND, jeśli identyfikator zasobu nie istnieje lub NX_LWM2M_METHOD_NOT_ALLOWED, jeśli nie obsługuje wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8f782-247">The function must return NX_LWM2M_NOT_FOUND if the Resource ID doesn't exist, or NX_LWM2M_METHOD_NOT_ALLOWED if it doesn't support execution.</span></span>

### <a name="the-create-method"></a><span data-ttu-id="8f782-248">Metoda "Create"</span><span class="sxs-lookup"><span data-stu-id="8f782-248">The 'Create' Method</span></span>

<span data-ttu-id="8f782-249">Metoda "Create" implementuje Tworzenie nowego wystąpienia obiektu, a funkcja ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-249">The 'Create' method implements the creation of a new Object Instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

<span data-ttu-id="8f782-250">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f782-250">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8f782-251">**object_ptr**: wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-251">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="8f782-252">**instance_ID**: Identyfikator nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8f782-252">**instance_id**: The ID of the new Instance.</span></span>
- <span data-ttu-id="8f782-253">**num_values**: liczba zasobów do zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="8f782-253">**num_values**: The number of resources to initialize.</span></span>
- <span data-ttu-id="8f782-254">**values_ptr**: wskaźnik do wartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="8f782-254">**values_ptr**: Pointer to the resources values.</span></span>
- <span data-ttu-id="8f782-255">**instance_ptr**: wskaźnik do docelowego wskaźnika utworzonego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8f782-255">**instance_ptr**: Pointer to the destination pointer of the created instance.</span></span>
- <span data-ttu-id="8f782-256">**Bootstrap**: true, jeśli wywołano z sekwencji Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="8f782-256">**bootstrap**: True if called from bootstrap sequence.</span></span>

<span data-ttu-id="8f782-257">Obiekt musi przydzielić i initialiaze nowe wystąpienie obiektu przy użyciu podanej listy wartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="8f782-257">The Object must allocate and initialiaze a new Object instance, using the provided list of resource values.</span></span>

### <a name="the-delete-method"></a><span data-ttu-id="8f782-258">Metoda "Delete"</span><span class="sxs-lookup"><span data-stu-id="8f782-258">The 'Delete' Method</span></span>

<span data-ttu-id="8f782-259">Metoda "Delete" implementuje usuwanie wystąpienia obiektu, a funkcja ma następującą definicję:</span><span class="sxs-lookup"><span data-stu-id="8f782-259">The 'Delete' method implements the deletion of an object instance, the function has the following definition:</span></span>

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

<span data-ttu-id="8f782-260">Parametry wejściowe są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8f782-260">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="8f782-261">**object_ptr**: wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-261">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="8f782-262">**instance_ptr**: wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-262">**instance_ptr**: Pointer to the Object Instance.</span></span>

<span data-ttu-id="8f782-263">Po powodzeniu obiekt musi zwolnić dane wystąpienia obiektu i wszelkie inne zasoby przydzielone przez wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="8f782-263">On success the Object must release the Object Instance data and any other resource allocated by the instance.</span></span>

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a><span data-ttu-id="8f782-264">Dodawanie implementacji obiektów i wystąpień do klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="8f782-264">Adding Object Implementations and Instances to the LWM2M Client</span></span>

<span data-ttu-id="8f782-265">Aplikacja może dodać nową implementację obiektu do klienta LWM2M przez wywołanie usługi ***nx_lwm2m_client_object_add*** .</span><span class="sxs-lookup"><span data-stu-id="8f782-265">The application can add new object implementation to the LWM2M Client by calling the ***nx_lwm2m_client_object_add*** service.</span></span>

<span data-ttu-id="8f782-266">Jeśli obiekt nie obsługuje dynamicznego tworzenia wystąpień, na przykład jeśli jest tylko pojedynczym obiektem wystąpienia, pole *nx_lwm2m_object_instances* struktury obiektów powinno wskazywać na listę struktur wystąpień statycznych.</span><span class="sxs-lookup"><span data-stu-id="8f782-266">If the Object doesn't support dynamic creation of Instances, for example if it's a single instance only Object, the *nx_lwm2m_object_instances* field of the object structure should point to the list of the static instances structures.</span></span>

<span data-ttu-id="8f782-267">Jeśli obiekt obsługuje dynamiczne tworzenie wystąpień, *nx_lwm2m_object_instances* powinien mieć wartość null, a usługa ***nx_lwm2m_client_object_create*** powinna być używana zamiast tego w celu wywołania metody "Create" obiektu.</span><span class="sxs-lookup"><span data-stu-id="8f782-267">If the Object supports dynamic instance creation, *nx_lwm2m_object_instances* should be set to NULL and the ***nx_lwm2m_client_object_create*** service should be used instead in order to call the 'Create' method of the object.</span></span>

## <a name="example-of-lwm2m-client-application"></a><span data-ttu-id="8f782-268">Przykład aplikacji klienckiej LWM2M</span><span class="sxs-lookup"><span data-stu-id="8f782-268">Example of LWM2M Client Application</span></span>

<span data-ttu-id="8f782-269">Poniższy kod jest przykładem prostej aplikacji klienckiej LWM2M, która implementuje urządzenie niestandardowe składające się z czujnika temperatury i przełącznika oświetlenia.</span><span class="sxs-lookup"><span data-stu-id="8f782-269">The following code is an example of a simple LWM2M Client Application which implements a custom device consisting of a temperature sensor and a light switch.</span></span>

<span data-ttu-id="8f782-270">Urządzenie umożliwia serwerowi Odczytywanie wartości czujnika temperatury i stanu logicznego przełącznika światła oraz ustawienie opcji przełączania światła na Włącz/Wyłącz.</span><span class="sxs-lookup"><span data-stu-id="8f782-270">The device allows a server to read the value of the temperature sensor and the boolean state of the light switch, and to set the light switch to on/off.</span></span>

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
