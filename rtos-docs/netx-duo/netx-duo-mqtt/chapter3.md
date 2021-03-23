---
title: Rozdział 3 — Opis usługi Azure RTO NetX Duo MQTT Client Services
description: Ten rozdział zawiera opis wszystkich usług klienta NetX Duo MQTT (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821799"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a><span data-ttu-id="e1a34-103">Rozdział 3 — Opis usługi Azure RTO NetX Duo MQTT Client Services</span><span class="sxs-lookup"><span data-stu-id="e1a34-103">Chapter 3 - Description of Azure RTOS NetX Duo MQTT client services</span></span>

<span data-ttu-id="e1a34-104">Ten rozdział zawiera opis wszystkich usług klienta Azure RTO NetX Duo MQTT (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="e1a34-104">This chapter contains a description of all Azure RTOS NetX Duo MQTT client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="e1a34-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e1a34-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="e1a34-106">**nxd_mqtt_client_create** *utworzyć wystąpienia klienta MQTT*</span><span class="sxs-lookup"><span data-stu-id="e1a34-106">**nxd_mqtt_client_create** *Create MQTT client instance*</span></span>
- <span data-ttu-id="e1a34-107">**nxd_mqtt_client_will_message_set** *ustawić komunikat będzie*</span><span class="sxs-lookup"><span data-stu-id="e1a34-107">**nxd_mqtt_client_will_message_set** *Set the will message*</span></span>
- <span data-ttu-id="e1a34-108">**nxd_mqtt_client_client_login_set** *ustawić nazwy użytkownika i hasła logowania klienta MQTT*</span><span class="sxs-lookup"><span data-stu-id="e1a34-108">**nxd_mqtt_client_client_login_set** *Set MQTT client login username and password*</span></span>
- <span data-ttu-id="e1a34-109">**nxd_mqtt_client_connect** *łączenie z klientem programu MQTT z brokerem*</span><span class="sxs-lookup"><span data-stu-id="e1a34-109">**nxd_mqtt_client_connect** *Connect MQTT Client to the broker*</span></span>
- <span data-ttu-id="e1a34-110">**nxd_mqtt_client_secure_connect** *łączenie klienta z klientem przy użyciu zabezpieczeń TLS*</span><span class="sxs-lookup"><span data-stu-id="e1a34-110">**nxd_mqtt_client_secure_connect** *Connect MQTT client to the broker with TLS security*</span></span>
- <span data-ttu-id="e1a34-111">**nxd_mqtt_client_publish** *opublikować komunikat za pośrednictwem brokera.*</span><span class="sxs-lookup"><span data-stu-id="e1a34-111">**nxd_mqtt_client_publish** *Publish a message through the broker.*</span></span>
- <span data-ttu-id="e1a34-112">**nxd_mqtt_client_subscribe** *subskrybować tematu*</span><span class="sxs-lookup"><span data-stu-id="e1a34-112">**nxd_mqtt_client_subscribe** *Subscribe to a topic*</span></span>
- <span data-ttu-id="e1a34-113">**nxd_mqtt_client_unsubscribe** *Anulowanie subskrypcji tematu*</span><span class="sxs-lookup"><span data-stu-id="e1a34-113">**nxd_mqtt_client_unsubscribe** *Unsubscribe from a topic*</span></span>
- <span data-ttu-id="e1a34-114">**nxd_mqtt_client_receive_notify_set** *Ustaw funkcję wywołania zwrotnego powiadomienia o OTRZYMAniu komunikatu MQTT*</span><span class="sxs-lookup"><span data-stu-id="e1a34-114">**nxd_mqtt_client_receive_notify_set** *Set MQTT message receive notify callback function*</span></span>
- <span data-ttu-id="e1a34-115">**nxd_mqtt_client_message_get** *pobrać komunikatu z brokera*</span><span class="sxs-lookup"><span data-stu-id="e1a34-115">**nxd_mqtt_client_message_get** *Retrieve a message from the broker*</span></span>
- <span data-ttu-id="e1a34-116">**nxd_mqtt_client_disconnect_notify_set** *Ustaw funkcję wywołania zwrotnego powiadomienia o rozłączeniu komunikatu MQTT*</span><span class="sxs-lookup"><span data-stu-id="e1a34-116">**nxd_mqtt_client_disconnect_notify_set** *Set MQTT message disconnect notify callback function*</span></span>
- <span data-ttu-id="e1a34-117">**nxd_mqtt_client_disconnect** *rozłączyć klienta MQTT z brokera*</span><span class="sxs-lookup"><span data-stu-id="e1a34-117">**nxd_mqtt_client_disconnect** *Disconnect MQTT client from the broker*</span></span>
- <span data-ttu-id="e1a34-118">**nxd_mqtt_client_delete** *usunąć wystąpienia klienta MQTT*</span><span class="sxs-lookup"><span data-stu-id="e1a34-118">**nxd_mqtt_client_delete** *Delete the MQTT client instance*</span></span>

## <a name="nxd_mqtt_client_create"></a><span data-ttu-id="e1a34-119">nxd_mqtt_client_create</span><span class="sxs-lookup"><span data-stu-id="e1a34-119">nxd_mqtt_client_create</span></span>

<span data-ttu-id="e1a34-120">Utwórz wystąpienie klienta MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-120">Create MQTT Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-121">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-121">Prototype</span></span>

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="e1a34-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-122">Description</span></span>

<span data-ttu-id="e1a34-123">Ta usługa tworzy wystąpienie klienta MQTT na określonym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="e1a34-123">This service creates an MQTT Client instance on the specified IP instance.</span></span> <span data-ttu-id="e1a34-124">Ciąg *client_id* jest przesyłany do serwera podczas fazy połączenia MQTT jako *Identyfikator klienta (ClientId)*.</span><span class="sxs-lookup"><span data-stu-id="e1a34-124">The *client_id* string is passed to the server during MQTT connection phase as the *Client Identifier (ClientId)*.</span></span> <span data-ttu-id="e1a34-125">Tworzy również niezbędne zasoby ThreadX (wątek zadania klienta MQTT, mutex, grupę flag zdarzeń i gniazdo TCP).</span><span class="sxs-lookup"><span data-stu-id="e1a34-125">It also creates the necessary ThreadX resources (MQTT Client task thread, mutex, event flag group, and TCP socket).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-126">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-126">Input Parameters</span></span>

- <span data-ttu-id="e1a34-127">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-127">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-128">**CLIENT_NAME** Ciąg nazwy klienta.</span><span class="sxs-lookup"><span data-stu-id="e1a34-128">**client_name** Client name string.</span></span>
- <span data-ttu-id="e1a34-129">**client_id** Ciąg identyfikatora klienta używany podczas fazy połączenia.</span><span class="sxs-lookup"><span data-stu-id="e1a34-129">**client_id** Client ID string used during connection phase.</span></span> <span data-ttu-id="e1a34-130">Broker MQTT używa tego client_id do unikatowego identyfikowania klienta.</span><span class="sxs-lookup"><span data-stu-id="e1a34-130">MQTT broker uses this client_id to uniquely identify a client.</span></span>
- <span data-ttu-id="e1a34-131">**client_id_length** Długość ciągu identyfikatora klienta w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e1a34-131">**client_id_length** Length of the client ID string, in bytes.</span></span>
- <span data-ttu-id="e1a34-132">**ip_ptr** Wskaźnik na wystąpienie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="e1a34-132">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="e1a34-133">**pool_ptr** Wskaźnik do puli pakietów MQTT przez klienta do jego działania.</span><span class="sxs-lookup"><span data-stu-id="e1a34-133">**pool_ptr** Pointer to a packet pool MQTT client uses for its operation.</span></span>
- <span data-ttu-id="e1a34-134">**stack_ptr** Obszar stosu dla wątku klienta MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-134">**stack_ptr** Stack area for the MQTT Client thread.</span></span>
- <span data-ttu-id="e1a34-135">**stack_size** Rozmiar obszaru stosu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e1a34-135">**stack_size** Size of the stack area, in bytes.</span></span>
- <span data-ttu-id="e1a34-136">**mqtt_thread_priority** Priorytet wątku MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-136">**mqtt_thread_priority** The priority of the MQTT Thread.</span></span>
- <span data-ttu-id="e1a34-137">**memory_ptr** Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="e1a34-137">**memory_ptr** Deprecated.</span></span> <span data-ttu-id="e1a34-138">Nie jest już używane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-138">Not used anymore.</span></span>
- <span data-ttu-id="e1a34-139">**memory_size** Przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="e1a34-139">**memory_size** Deprecated.</span></span> <span data-ttu-id="e1a34-140">Nie jest już używane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-140">Not used anymore.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-141">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-141">Return Values</span></span>

- <span data-ttu-id="e1a34-142">**NXD_MQTT_SUCCESS** (0X00) pomyślnie UTWORZYŁ klienta MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-142">**NXD_MQTT_SUCCESS** (0x00) Successfully created MQTT client.</span></span>
- <span data-ttu-id="e1a34-143">Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)</span><span class="sxs-lookup"><span data-stu-id="e1a34-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e1a34-144">NX_PTR_ERROR (0x07) nieprawidłowy MQTT bloku sterowania, ip_ptr lub puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="e1a34-144">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer.</span></span>
- <span data-ttu-id="e1a34-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowa wartość ciągu tematu, will_retrain_flag lub will_QoS.</span><span class="sxs-lookup"><span data-stu-id="e1a34-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-146">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-146">Allowed From</span></span>

<span data-ttu-id="e1a34-147">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-148">Example</span></span>

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a><span data-ttu-id="e1a34-149">nxd_mqtt_client_will_message_set</span><span class="sxs-lookup"><span data-stu-id="e1a34-149">nxd_mqtt_client_will_message_set</span></span>

<span data-ttu-id="e1a34-150">Ustawia komunikat będzie</span><span class="sxs-lookup"><span data-stu-id="e1a34-150">Sets the Will message</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-151">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-151">Prototype</span></span>

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a><span data-ttu-id="e1a34-152">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-152">Description</span></span>

<span data-ttu-id="e1a34-153">Ta usługa ustawia opcjonalny temat i zostanie wyświetlony komunikat, zanim klient nawiąże połączenie z serwerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-153">This service sets the optional will topic and will message before the client connects to the server.</span></span> <span data-ttu-id="e1a34-154">Temat musi być ciągiem zakodowanym w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e1a34-154">Will topic must be UTF-8 encoded string.</span></span>

<span data-ttu-id="e1a34-155">Jeśli zestaw zostanie wysłany do brokera w ramach komunikatu CONNECT, zostanie wyświetlony komunikat.</span><span class="sxs-lookup"><span data-stu-id="e1a34-155">The will message, if set, is transmitted to the broker as part of the CONNECT message.</span></span> <span data-ttu-id="e1a34-156">W związku z tym aplikacja, której zamierzasz używać, będzie musiał używać tej usługi przed nawiązaniem połączenia MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-156">Therefore application wishing to use will message must use this service before the MQTT connection is make.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-157">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-157">Input Parameters</span></span>

- <span data-ttu-id="e1a34-158">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-158">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-159">**will_topic** Kodowanie UTF-8 będzie ciąg tematu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-159">**will_topic** UTF-8 encoded will topic string.</span></span> <span data-ttu-id="e1a34-160">Sekcja musi być obecna.</span><span class="sxs-lookup"><span data-stu-id="e1a34-160">Will topic must be present.</span></span> <span data-ttu-id="e1a34-161">Obiekt wywołujący musi utrzymywać poprawność ciągu will_topic, aż do wywołania *nx_mqtt_client_connect* .</span><span class="sxs-lookup"><span data-stu-id="e1a34-161">Caller must keep the will_topic string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="e1a34-162">**will_topic_length** Liczba bajtów w ciągu tematu</span><span class="sxs-lookup"><span data-stu-id="e1a34-162">**will_topic_length** Number of bytes in the will topic string</span></span>
- <span data-ttu-id="e1a34-163">**will_message** Zdefiniowana aplikacja będzie komunikatem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-163">**will_message** Application defined will message.</span></span> <span data-ttu-id="e1a34-164">Jeśli komunikat nie jest wymagany, aplikacja może ustawić to pole na *NX_NULL.*</span><span class="sxs-lookup"><span data-stu-id="e1a34-164">If will message is not required, application can set this field to *NX_NULL.*</span></span>
- <span data-ttu-id="e1a34-165">**will_message_length** Liczba bajtów w ciągu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-165">**will_message_length** Number of bytes in the will message string.</span></span> <span data-ttu-id="e1a34-166">Jeśli will_message ma wartość NULL, will_message_length musi być ustawiona na 0.</span><span class="sxs-lookup"><span data-stu-id="e1a34-166">If will_message is set to NULL, will_message_length must be set to 0.</span></span>
- <span data-ttu-id="e1a34-167">**will_retain_flag** Czy serwer publikuje komunikat w postaci wiadomości przechowywanej.</span><span class="sxs-lookup"><span data-stu-id="e1a34-167">**will_retain_flag** Whether the server publishes the will message as a retained message.</span></span> <span data-ttu-id="e1a34-168">Prawidłowe wartości to *NX_TRUE* lub *NX_FALSE.*</span><span class="sxs-lookup"><span data-stu-id="e1a34-168">Valid values are *NX_TRUE* or *NX_FALSE.*</span></span>
- <span data-ttu-id="e1a34-169">**will_QoS** Wartość QoS używana przez serwer podczas wysyłania zostanie wyświetlony komunikat.</span><span class="sxs-lookup"><span data-stu-id="e1a34-169">**will_QoS** QoS value used by the server when sending will message.</span></span> <span data-ttu-id="e1a34-170">Prawidłowe wartości to 0 lub 1.</span><span class="sxs-lookup"><span data-stu-id="e1a34-170">Valid values are 0 or 1.</span></span>  

### <a name="return-values"></a><span data-ttu-id="e1a34-171">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-171">Return Values</span></span>

- <span data-ttu-id="e1a34-172">**NXD_MQTT_SUCCESS** (0X00) pomyślnie ustawia komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="e1a34-172">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="e1a34-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0X1000C) jakość komunikatów poziomu 2 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="e1a34-174">NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-174">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="e1a34-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowa wartość ciągu tematu, will_retrain_flag lub will_QoS.</span><span class="sxs-lookup"><span data-stu-id="e1a34-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-176">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-176">Allowed From</span></span>

<span data-ttu-id="e1a34-177">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-178">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-178">Example</span></span>

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a><span data-ttu-id="e1a34-179">nxd_mqtt_client_login_set</span><span class="sxs-lookup"><span data-stu-id="e1a34-179">nxd_mqtt_client_login_set</span></span>

<span data-ttu-id="e1a34-180">Ustawia nazwę użytkownika i hasło logowania klienta MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-180">Sets MQTT client login username and password</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-181">Prototype</span></span>

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a><span data-ttu-id="e1a34-182">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-182">Description</span></span>

<span data-ttu-id="e1a34-183">Ta usługa ustawia nazwę użytkownika i hasło, które są używane podczas fazy połączenia MQTT na potrzeby logowania w celu uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="e1a34-183">This service sets the username and password, which is used during MQTT connection phase for log in authentication purpose.</span></span>

<span data-ttu-id="e1a34-184">Identyfikator logowania klienta MQTT z nazwą użytkownika i hasłem jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e1a34-184">The MQTT client login with username and password is optional.</span></span> <span data-ttu-id="e1a34-185">W sytuacjach, gdy serwer wymaga nazwy użytkownika i hasła, przed nawiązaniem połączenia należy ustawić nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="e1a34-185">In situations where the server requires a user name and password, the user name and password must be set before the connection is established.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-186">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-186">Input Parameters</span></span>

- <span data-ttu-id="e1a34-187">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-187">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-188">**Nazwa użytkownika** Zakodowany ciąg nazwy użytkownika w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e1a34-188">**username** UTF-8 encoded user name string.</span></span> <span data-ttu-id="e1a34-189">Obiekt wywołujący musi utrzymywać prawidłowy ciąg nazwy użytkownika, aż do wywołania *nx_mqtt_client_connect* .</span><span class="sxs-lookup"><span data-stu-id="e1a34-189">Caller must keep the username string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="e1a34-190">**username_length** Liczba bajtów w ciągu nazwy użytkownika</span><span class="sxs-lookup"><span data-stu-id="e1a34-190">**username_length** Number of bytes in the username string</span></span>
- <span data-ttu-id="e1a34-191">**hasło** Ciąg hasła.</span><span class="sxs-lookup"><span data-stu-id="e1a34-191">**password** Password string.</span></span> <span data-ttu-id="e1a34-192">Jeśli hasło nie jest wymagane, to pole może mieć wartość NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="e1a34-192">If password is not required, this field may be set to NX_NULL.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-193">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-193">Return Values</span></span>

- <span data-ttu-id="e1a34-194">**NXD_MQTT_SUCCESS** (0X00) pomyślnie ustawia komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="e1a34-194">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="e1a34-195">NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-195">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="e1a34-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Nieprawidłowa nazwa użytkownika lub ciąg hasła.</span><span class="sxs-lookup"><span data-stu-id="e1a34-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid username string or the password string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-197">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-197">Allowed From</span></span>

<span data-ttu-id="e1a34-198">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-199">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-199">Example</span></span>

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a><span data-ttu-id="e1a34-200">nxd_mqtt_client_connect</span><span class="sxs-lookup"><span data-stu-id="e1a34-200">nxd_mqtt_client_connect</span></span>

<span data-ttu-id="e1a34-201">Łączenie klienta MQTT z brokerem</span><span class="sxs-lookup"><span data-stu-id="e1a34-201">Connect MQTT Client to the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-202">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-202">Prototype</span></span>

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="e1a34-203">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-203">Description</span></span>

<span data-ttu-id="e1a34-204">Ta usługa inicjuje połączenie z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-204">This service initiates a connection to the broker.</span></span> <span data-ttu-id="e1a34-205">Najpierw wiąże się z gniazdem TCP, a następnie nawiązuje połączenie TCP.</span><span class="sxs-lookup"><span data-stu-id="e1a34-205">First it binds a TCP socket, then makes a TCP connection.</span></span> <span data-ttu-id="e1a34-206">Przy założeniu, że program zakończy się pomyślnie, tworzy czasomierz, jeśli funkcja utrzymywania aktywności MQTT jest włączona.</span><span class="sxs-lookup"><span data-stu-id="e1a34-206">Assuming that succeeds, it creates a timer if the MQTT keep alive feature is enabled.</span></span> <span data-ttu-id="e1a34-207">Następnie łączy się z serwerem MQTT (brokerem).</span><span class="sxs-lookup"><span data-stu-id="e1a34-207">Then it connects with the MQTT server (broker).</span></span>

<span data-ttu-id="e1a34-208">Należy zauważyć, że ta usługa tworzy połączenie MQTT bez ochrony TLS.</span><span class="sxs-lookup"><span data-stu-id="e1a34-208">Note that this service creates an MQTT connection with no TLS protection.</span></span> <span data-ttu-id="e1a34-209">Aby można było utworzyć bezpieczne połączenie MQTT, aplikacja używa usługi ***nxd_mqtt_client_secure_connect ().***</span><span class="sxs-lookup"><span data-stu-id="e1a34-209">To create a secure MQTT connection, the application shall use the service ***nxd_mqtt_client_secure_connect().***</span></span>

<span data-ttu-id="e1a34-210">Jeśli klient ustawi *clean_session* na NX_FALSE, klient będzie ponownie przesyłał wszystkie zapisane komunikaty, które nie zostały jeszcze potwierdzone.</span><span class="sxs-lookup"><span data-stu-id="e1a34-210">Upon the connection, if the client sets the *clean_session* to NX_FALSE, the client will retransmit any messages stored that have not been acknowledged yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-211">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-211">Input Parameters</span></span>

- <span data-ttu-id="e1a34-212">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-212">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-213">**server_IP** Adres IP brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-213">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="e1a34-214">**SERVER_PORT** Numer portu brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-214">**server_port** Broker port number.</span></span> <span data-ttu-id="e1a34-215">Domyślny port dla MQTT jest zdefiniowany jako **_NXD_MQTT_PORT_** (1883).</span><span class="sxs-lookup"><span data-stu-id="e1a34-215">The default port for MQTT is defined as **_NXD_MQTT_PORT_** (1883).</span></span>
- <span data-ttu-id="e1a34-216">**keep_alive** Wartość utrzymywania aktywności (w sekundach), która ma być używana podczas sesji.</span><span class="sxs-lookup"><span data-stu-id="e1a34-216">**keep_alive** The keep alive value, in seconds, to be used during the session.</span></span> <span data-ttu-id="e1a34-217">Wartość wskazuje maksymalny czas między dwoma komunikatami sterującymi MQTT wysyłanymi do brokera, zanim Broker przekroczy ten klient.</span><span class="sxs-lookup"><span data-stu-id="e1a34-217">The value indicates the maximum time between two MQTT control messages being sent to the broker before the broker times out this client.</span></span> <span data-ttu-id="e1a34-218">Wartość 0 wyłącza funkcję Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="e1a34-218">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="e1a34-219">**clean_session** Czy serwer rozpoczyna czyszczenie tej sesji.</span><span class="sxs-lookup"><span data-stu-id="e1a34-219">**clean_session** Whether the server shall start this session clean.</span></span> <span data-ttu-id="e1a34-220">Prawidłowe opcje to **_NX_TRUE_*_ lub _*_NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="e1a34-220">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="e1a34-221">**WAIT_OPTION** Czas oczekiwania na połączenie.</span><span class="sxs-lookup"><span data-stu-id="e1a34-221">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-222">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-222">Return Values</span></span>

- <span data-ttu-id="e1a34-223">**NXD_MQTT_SUCCESS** (0X00) pomyślnie MQTT połączenie</span><span class="sxs-lookup"><span data-stu-id="e1a34-223">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT connection</span></span>
- <span data-ttu-id="e1a34-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) klient jest już połączony z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="e1a34-225">**NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX</span><span class="sxs-lookup"><span data-stu-id="e1a34-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="e1a34-226">Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)</span><span class="sxs-lookup"><span data-stu-id="e1a34-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e1a34-227">**NXD_MQTT_CONNECT_FAILURE** (0X10005) nie może nawiązać połączenia z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="e1a34-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może wysłać komunikatów do brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="e1a34-229">Serwer **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) odpowiedział z błędem</span><span class="sxs-lookup"><span data-stu-id="e1a34-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error</span></span>
- <span data-ttu-id="e1a34-230">Kod odpowiedzi serwera **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081)</span><span class="sxs-lookup"><span data-stu-id="e1a34-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="e1a34-231">Kod odpowiedzi serwera **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082)</span><span class="sxs-lookup"><span data-stu-id="e1a34-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="e1a34-232">Kod odpowiedzi serwera **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083)</span><span class="sxs-lookup"><span data-stu-id="e1a34-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="e1a34-233">Kod odpowiedzi serwera **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084)</span><span class="sxs-lookup"><span data-stu-id="e1a34-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="e1a34-234">Kod odpowiedzi serwera **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085)</span><span class="sxs-lookup"><span data-stu-id="e1a34-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="e1a34-235">NX_PTR_ERROR (0x07) Nieprawidłowa MQTT bloku sterowania, ip_ptr lub puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e1a34-235">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-236">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-236">Allowed From</span></span>

<span data-ttu-id="e1a34-237">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-238">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-238">Example</span></span>

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a><span data-ttu-id="e1a34-239">nxd_mqtt_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="e1a34-239">nxd_mqtt_client_secure_connect</span></span>

<span data-ttu-id="e1a34-240">Podłączanie klienta MQTT do brokera z zabezpieczeniami TLS</span><span class="sxs-lookup"><span data-stu-id="e1a34-240">Connect MQTT client to the broker with TLS security</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-241">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-241">Prototype</span></span>

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="e1a34-242">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-242">Description</span></span>

<span data-ttu-id="e1a34-243">Ta usługa jest taka sama jak ***nxd_mqtt_client_connect*** , z tą różnicą, że połączenie przechodzi przez warstwę TLS zamiast TCP.</span><span class="sxs-lookup"><span data-stu-id="e1a34-243">This service is identical to ***nxd_mqtt_client_connect*** except that the connection goes through TLS layer instead of TCP.</span></span> <span data-ttu-id="e1a34-244">W związku z tym komunikacja między klientem i brokerem jest zabezpieczona.</span><span class="sxs-lookup"><span data-stu-id="e1a34-244">Therefore, communication between the client and the broker is secured.</span></span>

<span data-ttu-id="e1a34-245">*Tls_setup* zdefiniowane przez użytkownika to funkcja wywołania zwrotnego, która jest stosowana przez klienta MQTT przed nawiązaniem połączenia z klientem MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-245">The user-defined *tls_setup* is a callback function that the MQTT client uses prior to making a MQTT client connection.</span></span> <span data-ttu-id="e1a34-246">Aplikacja inicjuje NetX Secure TLS, konfiguruje parametry zabezpieczeń i ładuje odpowiednie certyfikaty do użycia podczas uzgadniania protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e1a34-246">The application shall initialize NetX Secure TLS, configure security parameters, and load relevant certificates to be used during TLS handshake.</span></span> <span data-ttu-id="e1a34-247">Rzeczywista uzgadnianie protokołu TLS następuje po ustanowieniu połączenia TCP na porcie MQTT TLS brokera (domyślny port TCP 8883).</span><span class="sxs-lookup"><span data-stu-id="e1a34-247">The actual TLS handshake happens after a TCP connection is established on the broker's MQTT TLS port (default TCP port 8883).</span></span> <span data-ttu-id="e1a34-248">Po pomyślnym przeprowadzeniu uzgadniania TLS pakiet MQTT CONNECT Control zostanie wysłany za pośrednictwem protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e1a34-248">Once the TLS handshake is successful, the MQTT CONNECT control packet is sent via TLS.</span></span>

<span data-ttu-id="e1a34-249">Aby zapewnić bezpieczne połączenia, musi być dostępna Biblioteka NetX Secure TLS, a klient NetX Duo MQTT musi być skompilowany przy użyciu zdefiniowanych ***NX_SECURE_ENABLE*** .</span><span class="sxs-lookup"><span data-stu-id="e1a34-249">To make secure connections, the NetX Secure TLS library must be available, and the NetX Duo MQTT client must be built with ***NX_SECURE_ENABLE*** defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-250">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-250">Input Parameters</span></span>

- <span data-ttu-id="e1a34-251">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-251">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-252">**server_IP** Adres IP brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-252">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="e1a34-253">**SERVER_PORT** Numer portu brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-253">**server_port** Broker port number.</span></span> <span data-ttu-id="e1a34-254">Domyślny port dla MQTT IsDefined jako **_NXD_MQTT_TLS_PORT_** (8883).</span><span class="sxs-lookup"><span data-stu-id="e1a34-254">The default port for MQTT isdefined as **_NXD_MQTT_TLS_PORT_** (8883).</span></span>
- <span data-ttu-id="e1a34-255">**tls_setup** Funkcja wywołania zwrotnego konfiguracji protokołu TLS dostarczonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e1a34-255">**tls_setup** User-provided TLS Setup callback function.</span></span> <span data-ttu-id="e1a34-256">Ta funkcja wywołania zwrotnego jest wywoływana w celu skonfigurowania parametrów połączenia klienta protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e1a34-256">This callback function is invoked to set up TLS client connection parameters.</span></span>
- <span data-ttu-id="e1a34-257">**keep_alive** Wartość Keep-Alive, która ma być używana podczas sesji.</span><span class="sxs-lookup"><span data-stu-id="e1a34-257">**keep_alive** The keep-alive value to be used during the session.</span></span> <span data-ttu-id="e1a34-258">Wartość 0 wyłącza funkcję Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="e1a34-258">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="e1a34-259">**clean_session** Bez względu na to, czy serwer rozpoczyna czyszczenie tej sesji.</span><span class="sxs-lookup"><span data-stu-id="e1a34-259">**clean_session** Whether or not the server shall start this session clean.</span></span> <span data-ttu-id="e1a34-260">Prawidłowe opcje to **_NX_TRUE_*_ lub _*_NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="e1a34-260">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="e1a34-261">**WAIT_OPTION** Czas oczekiwania na połączenie.</span><span class="sxs-lookup"><span data-stu-id="e1a34-261">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-262">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-262">Return Values</span></span>

- <span data-ttu-id="e1a34-263">**NXD_MQTT_SUCCESS** (0X00) pomyślnie MQTT połączenie z klientem za pośrednictwem protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="e1a34-263">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT client connection established via TLS.</span></span>
- <span data-ttu-id="e1a34-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) klient jest już połączony z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="e1a34-265">**NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX</span><span class="sxs-lookup"><span data-stu-id="e1a34-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="e1a34-266">Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)</span><span class="sxs-lookup"><span data-stu-id="e1a34-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e1a34-267">**NXD_MQTT_CONNECT_FAILURE** (0X10005) nie może nawiązać połączenia z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="e1a34-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może wysłać komunikatów do brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="e1a34-269">Serwer **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) odpowiedział na komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="e1a34-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error message.</span></span>
- <span data-ttu-id="e1a34-270">Kod odpowiedzi serwera **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081)</span><span class="sxs-lookup"><span data-stu-id="e1a34-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="e1a34-271">Kod odpowiedzi serwera **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082)</span><span class="sxs-lookup"><span data-stu-id="e1a34-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="e1a34-272">Kod odpowiedzi serwera **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083)</span><span class="sxs-lookup"><span data-stu-id="e1a34-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="e1a34-273">Kod odpowiedzi serwera **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084)</span><span class="sxs-lookup"><span data-stu-id="e1a34-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="e1a34-274">Kod odpowiedzi serwera **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085)</span><span class="sxs-lookup"><span data-stu-id="e1a34-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="e1a34-275">NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT lub struktura adresów serwera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-275">NX_PTR_ERROR (0x07) Invalid MQTT control block or sever address structure.</span></span>
- <span data-ttu-id="e1a34-276">Port serwera NX_INVALID_PORT (0x46) nie może mieć wartości 0.</span><span class="sxs-lookup"><span data-stu-id="e1a34-276">NX_INVALID_PORT (0x46) Server port cannot be 0.</span></span>
- <span data-ttu-id="e1a34-277">Błąd parametru wejściowego NXD_MQTT_INVALID_PARAMETER (0x10009)</span><span class="sxs-lookup"><span data-stu-id="e1a34-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>
- <span data-ttu-id="e1a34-278">Nie rozpoczęto jeszcze działania NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread has not started running yet.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-279">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-279">Allowed From</span></span>

<span data-ttu-id="e1a34-280">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-281">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-281">Example</span></span>

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a><span data-ttu-id="e1a34-282">nxd_mqtt_client_publish</span><span class="sxs-lookup"><span data-stu-id="e1a34-282">nxd_mqtt_client_publish</span></span>

<span data-ttu-id="e1a34-283">Publikowanie wiadomości za pośrednictwem brokera</span><span class="sxs-lookup"><span data-stu-id="e1a34-283">Publish a message through the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-284">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-284">Prototype</span></span>

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a><span data-ttu-id="e1a34-285">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-285">Description</span></span>

<span data-ttu-id="e1a34-286">Ta usługa publikuje komunikat za pośrednictwem brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-286">This service publishes a message through the broker.</span></span> <span data-ttu-id="e1a34-287">Publikowanie komunikatów poziomu 2 usług QoS nie jest jeszcze obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-287">Publishing QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-288">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-288">Input Parameters</span></span>

- <span data-ttu-id="e1a34-289">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-289">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-290">**topic_name** Temat do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="e1a34-290">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="e1a34-291">**topic_name_length** Długość tematu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e1a34-291">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="e1a34-292">**komunikat** Wskaźnik do buforu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e1a34-292">**message** Pointer to the message buffer.</span></span>
- <span data-ttu-id="e1a34-293">**message_length** Rozmiar wiadomości (w bajtach)</span><span class="sxs-lookup"><span data-stu-id="e1a34-293">**message_length** Size of the message, in bytes</span></span>
- <span data-ttu-id="e1a34-294">**Zachowaj** Określa, czy ten komunikat jest przechowywany przez brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-294">**retain** Determines if the broker shall retain the message.</span></span>
- <span data-ttu-id="e1a34-295">**Jakość** usług (QoS) Wymagana wartość QoS: 0 lub 1.</span><span class="sxs-lookup"><span data-stu-id="e1a34-295">**QoS** The desired QoS value: 0 or 1.</span></span>
- <span data-ttu-id="e1a34-296">**limit czasu** Wartość limitu czasu</span><span class="sxs-lookup"><span data-stu-id="e1a34-296">**timeout** Timeout value</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-297">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-297">Return Values</span></span>

- <span data-ttu-id="e1a34-298">**NXD_MQTT_SUCCESS** (0X00) pomyślne utworzenie klienta MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-298">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT Client create</span></span>
- <span data-ttu-id="e1a34-299">Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004).</span><span class="sxs-lookup"><span data-stu-id="e1a34-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error.</span></span>
- <span data-ttu-id="e1a34-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0X10006) nie może uzyskać pakietu z puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="e1a34-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Failed to obtain packet from the packet pool.</span></span>
- <span data-ttu-id="e1a34-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może nawiązać komunikacji z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Failed to communication with the broker.</span></span>
- <span data-ttu-id="e1a34-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0X1000C) jakość komunikatów poziomu 2 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="e1a34-303">NX_PTR_ERROR (0x07) Nieprawidłowa MQTT bloku sterowania, ip_ptr lub puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e1a34-303">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="e1a34-304">Błąd parametru wejściowego NXD_MQTT_INVALID_PARAMETER (0x10009)</span><span class="sxs-lookup"><span data-stu-id="e1a34-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-305">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-305">Allowed From</span></span>

<span data-ttu-id="e1a34-306">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-307">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-307">Example</span></span>

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a><span data-ttu-id="e1a34-308">nxd_mqtt_client_subscribe</span><span class="sxs-lookup"><span data-stu-id="e1a34-308">nxd_mqtt_client_subscribe</span></span>

<span data-ttu-id="e1a34-309">Subskrybowanie tematu</span><span class="sxs-lookup"><span data-stu-id="e1a34-309">Subscribe to a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-310">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-310">Prototype</span></span>

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a><span data-ttu-id="e1a34-311">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-311">Description</span></span>

<span data-ttu-id="e1a34-312">Ta usługa subskrybuje określony temat.</span><span class="sxs-lookup"><span data-stu-id="e1a34-312">This service subscribes to a specific topic.</span></span> <span data-ttu-id="e1a34-313">Subskrybowanie komunikatów poziomu 2 usługi QoS nie jest jeszcze obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-313">Subscribing to QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-314">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-314">Input Parameters</span></span>

- <span data-ttu-id="e1a34-315">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-315">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-316">**topic_name** Temat do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="e1a34-316">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="e1a34-317">**topic_name_length** Długość tematu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e1a34-317">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="e1a34-318">**Jakość usług QoS żądany poziom jakości usług:** 0 lub 1.</span><span class="sxs-lookup"><span data-stu-id="e1a34-318">**QoS The desired QoS level:** 0 or 1.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-319">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-319">Return Values</span></span>

- <span data-ttu-id="e1a34-320">**NXD_MQTT_SUCCESS** (0X00) pomyślnie subskrybuje temat.</span><span class="sxs-lookup"><span data-stu-id="e1a34-320">**NXD_MQTT_SUCCESS** (0x00) Successfully subscribed to the topic.</span></span>
- <span data-ttu-id="e1a34-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) klient nie jest połączony z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="e1a34-322">**NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX</span><span class="sxs-lookup"><span data-stu-id="e1a34-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span>
- <span data-ttu-id="e1a34-323">Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)</span><span class="sxs-lookup"><span data-stu-id="e1a34-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e1a34-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może wysłać komunikatów do brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="e1a34-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) poziom QoS 2messages nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages are not supported.</span></span>
- <span data-ttu-id="e1a34-326">NX_PTR_ERROR (0x07) Nieprawidłowa MQTT bloku sterowania, ip_ptr lub puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e1a34-326">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="e1a34-327">Nie ustawiono topic_name NXD_MQTT_INVALID_PARAMETER (0x10009) lub topic_name_length jest równa zero lub wartość ustawienia QoS jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="e1a34-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero, or QoS is value is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-328">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-328">Allowed From</span></span>

<span data-ttu-id="e1a34-329">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-330">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-330">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a><span data-ttu-id="e1a34-331">nxd_mqtt_client_unsubscribe</span><span class="sxs-lookup"><span data-stu-id="e1a34-331">nxd_mqtt_client_unsubscribe</span></span>

<span data-ttu-id="e1a34-332">Anulowanie subskrypcji tematu</span><span class="sxs-lookup"><span data-stu-id="e1a34-332">Unsubscribe from a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-333">Prototype</span></span>

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a><span data-ttu-id="e1a34-334">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-334">Description</span></span>

<span data-ttu-id="e1a34-335">Ta usługa anuluje subskrypcję z tematu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-335">This service unsubscribes from a topic.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-336">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-336">Input Parameters</span></span>

- <span data-ttu-id="e1a34-337">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-337">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-338">**topic_name** Temat anulowania subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="e1a34-338">**topic_name** Topic to unsubscribe from.</span></span>
- <span data-ttu-id="e1a34-339">**topic_name_length** Długość tematu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e1a34-339">**topic_name_length** Length of the topic, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-340">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-340">Return Values</span></span>

- <span data-ttu-id="e1a34-341">**NXD_MQTT_SUCCESS** (0X00) pomyślnie anulował subskrypcję tematu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-341">**NXD_MQTT_SUCCESS** (0x00) Successfully unsubscribed from the topic.</span></span>
- <span data-ttu-id="e1a34-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) klient nie jest połączony z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="e1a34-343">**NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX.</span><span class="sxs-lookup"><span data-stu-id="e1a34-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="e1a34-344">Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)</span><span class="sxs-lookup"><span data-stu-id="e1a34-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e1a34-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) nie może wysłać komunikatów do brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="e1a34-346">NX_PTR_ERROR (0x07) Nieprawidłowy wskaźnik bloku sterowania MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-346">NX_PTR_ERROR (0x07) Invalid MQTT control block pointer</span></span>
- <span data-ttu-id="e1a34-347">Nie ustawiono topic_name NXD_MQTT_INVALID_PARAMETER (0x10009) lub topic_name_length wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="e1a34-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-348">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-348">Allowed From</span></span>

<span data-ttu-id="e1a34-349">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-350">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-350">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a><span data-ttu-id="e1a34-351">nxd_mqtt_client_receive_notify_set</span><span class="sxs-lookup"><span data-stu-id="e1a34-351">nxd_mqtt_client_receive_notify_set</span></span>

<span data-ttu-id="e1a34-352">Ustaw funkcję wywołania zwrotnego powiadomienia o otrzymaniu komunikatu MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-352">Set MQTT message receive notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-353">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-353">Prototype</span></span>

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a><span data-ttu-id="e1a34-354">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-354">Description</span></span>

<span data-ttu-id="e1a34-355">Ta usługa rejestruje funkcję wywołania zwrotnego za pomocą klienta MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-355">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="e1a34-356">Po odebraniu komunikatu opublikowanego przez brokera klient MQTT przechowuje komunikat w kolejce odbierania.</span><span class="sxs-lookup"><span data-stu-id="e1a34-356">Upon receiving a message published by the broker, MQTT client stores the message in the receive queue.</span></span> <span data-ttu-id="e1a34-357">Jeśli funkcja wywołania zwrotnego jest ustawiona, wywoływana jest funkcja wywołania zwrotnego w celu powiadomienia aplikacji o gotowości do pobrania.</span><span class="sxs-lookup"><span data-stu-id="e1a34-357">If the callback function is set, the callback function is invoked to notify the application that a message is ready to be retrieved.</span></span> <span data-ttu-id="e1a34-358">Funkcja odbierania powiadomień przyjmuje wskaźnik do bloku kontroli klienta MQTT, a *message_count* wskazujący liczbę komunikatów dostępnych w kolejce odbierania.</span><span class="sxs-lookup"><span data-stu-id="e1a34-358">The receive notify function takes a pointer to the MQTT client control block, and a *message_count* indicating the number of messages available in the receive queue.</span></span> <span data-ttu-id="e1a34-359">Należy pamiętać, że liczba może ulec zmianie między powiadomieniem dotyczącym odebrania a pobraniem tych komunikatów przez aplikację, ponieważ w interwale mogły zostać odebrane nowe komunikaty.</span><span class="sxs-lookup"><span data-stu-id="e1a34-359">Note that the number may change between the receive notification and when the application retrieves these messages, as new messages may have arrived in the interval.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-360">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-360">Input Parameters</span></span>

- <span data-ttu-id="e1a34-361">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-361">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-362">**receive_notify** Funkcja wywołania zwrotnego podanego przez użytkownika ma być wywoływana podczas otrzymywania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-362">**receive_notify** User supplied callback function to be invoked on receiving a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-363">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-363">Return Values</span></span>

- <span data-ttu-id="e1a34-364">**NXD_MQTT_SUCCESS** (0X00) pomyślnie ustawił funkcję Odbierz powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="e1a34-364">**NXD_MQTT_SUCCESS** (0x00) Successfully set the receive notify function.</span></span>
- <span data-ttu-id="e1a34-365">NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-365">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-366">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-366">Allowed From</span></span>

<span data-ttu-id="e1a34-367">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-368">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-368">Example</span></span>

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a><span data-ttu-id="e1a34-369">nxd_mqtt_client_message_get</span><span class="sxs-lookup"><span data-stu-id="e1a34-369">nxd_mqtt_client_message_get</span></span>

<span data-ttu-id="e1a34-370">Pobieranie komunikatu z brokera</span><span class="sxs-lookup"><span data-stu-id="e1a34-370">Retrieve a message from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-371">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-371">Prototype</span></span>

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a><span data-ttu-id="e1a34-372">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-372">Description</span></span>

<span data-ttu-id="e1a34-373">Ta usługa pobiera komunikat opublikowany przez brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-373">This service retrieves a message published by the broker.</span></span> <span data-ttu-id="e1a34-374">Wszystkie komunikaty przychodzące są przechowywane w kolejce odbierania.</span><span class="sxs-lookup"><span data-stu-id="e1a34-374">All incoming messages are stored in the receive queue.</span></span> <span data-ttu-id="e1a34-375">Aplikacja używa tej usługi do pobierania tych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e1a34-375">The application uses this service to retrieve these messages.</span></span> <span data-ttu-id="e1a34-376">To wywołanie nie blokuje się.</span><span class="sxs-lookup"><span data-stu-id="e1a34-376">This call is non-blocking.</span></span> <span data-ttu-id="e1a34-377">Jeśli kolejka odbierania jest pusta, ta usługa zwraca \***NXD_MQTT_NO_MESSAGE** _.</span><span class="sxs-lookup"><span data-stu-id="e1a34-377">If the receive queue is empty, this service returns \***NXD_MQTT_NO_MESSAGE** _.</span></span> <span data-ttu-id="e1a34-378">Aplikacja, która chce otrzymywać powiadomienia o przychodzących komunikatach, może wywołać usługę _ \*_nxd_mqtt_client_receive_notify_set_\*\*, aby zarejestrować funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e1a34-378">An application wishing to be notified of incoming message can call the service _ *_nxd_mqtt_client_receive_notify_set_*\* to register a receive callback function.</span></span>

<span data-ttu-id="e1a34-379">Obiekt wywołujący musi podać miejsce w pamięci dla ciągu tematu i treści komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-379">The caller needs to provide memory space for the topic string and the message body.</span></span> <span data-ttu-id="e1a34-380">Rozmiary tych dwóch buforów są przesyłane przy użyciu *topic_buffer_size* i *message_buffer_size*.</span><span class="sxs-lookup"><span data-stu-id="e1a34-380">The sizes of these two buffers are passed in using *topic_buffer_size* and *message_buffer_size*.</span></span> <span data-ttu-id="e1a34-381">Rzeczywista liczba bajtów w ciągu tematu i treść komunikatu są zwracane w *actual_topic_length* i *actual_message_length*.</span><span class="sxs-lookup"><span data-stu-id="e1a34-381">The actual number of bytes in the topic string and the message body are returned in *actual_topic_length* and *actual_message_length*.</span></span> <span data-ttu-id="e1a34-382">Jeśli długość tematu lub długość Massage jest większa niż podana ilość miejsca w buforze, ta usługa zwróci kod błędu *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span><span class="sxs-lookup"><span data-stu-id="e1a34-382">If topic length or massage length is greater than the buffer space provided, this service returns error code *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span></span>

<span data-ttu-id="e1a34-383">Aplikacja przydzieli większy bufor i spróbuj ponownie.</span><span class="sxs-lookup"><span data-stu-id="e1a34-383">The application shall allocate a bigger buffer and try again.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-384">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-384">Input Parameters</span></span>

- <span data-ttu-id="e1a34-385">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-385">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-386">**topic_buffer** Wskaźnik do lokalizacji pamięci, w której jest kopiowany ciąg tematu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-386">**topic_buffer** Pointer to the memory location where the topic string is copied into.</span></span>
- <span data-ttu-id="e1a34-387">**topic_buffer_size** Rozmiar buforu tematu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-387">**topic_buffer_size** Size of the topic buffer.</span></span>
- <span data-ttu-id="e1a34-388">**actual_topic_length** Wskaźnik do lokalizacji pamięci, w której jest zwracana rzeczywista długość tematu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-388">**actual_topic_length** Pointer to the memory location where the actual topic length is returned.</span></span>
- <span data-ttu-id="e1a34-389">**message_buffer** Wskaźnik do lokalizacji pamięci, w której jest kopiowany ciąg wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e1a34-389">**message_buffer** Pointer to the memory location where the message string is copied into.</span></span>
- <span data-ttu-id="e1a34-390">**message_buffer_size** Rozmiar buforu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e1a34-390">**message_buffer_size** Size of the message buffer.</span></span>
- <span data-ttu-id="e1a34-391">**actual_message_length** Wskaźnik do lokalizacji pamięci, w której zostanie zwrócona długość wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e1a34-391">**actual_message_length** Pointer to the memory location where the message length is returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-392">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-392">Return Values</span></span>

- <span data-ttu-id="e1a34-393">**NXD_MQTT_SUCCESS** (0X00) pomyślnie pobrał komunikat.</span><span class="sxs-lookup"><span data-stu-id="e1a34-393">**NXD_MQTT_SUCCESS** (0x00) Successfully retrieved message.</span></span>
- <span data-ttu-id="e1a34-394">Błąd wewnętrzny logiki **NXD_MQTT_INTERNAL_ERROR** (0x10004)</span><span class="sxs-lookup"><span data-stu-id="e1a34-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="e1a34-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) Kolejka odbierania jest pusta.</span><span class="sxs-lookup"><span data-stu-id="e1a34-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) The receive queue is empty.</span></span>
- <span data-ttu-id="e1a34-396">Bufor tematu (0x1000D) lub bufor komunikatów jest za mały dla tematu lub wiadomości. **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE**</span><span class="sxs-lookup"><span data-stu-id="e1a34-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Topic buffer or message buffer is too small for the topic or the message.</span></span>
- <span data-ttu-id="e1a34-397">NX_PTR_ERROR (0x07) Nieprawidłowa MQTT bloku sterowania, ip_ptr lub puli pakietów</span><span class="sxs-lookup"><span data-stu-id="e1a34-397">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="e1a34-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer lub topic_buffer wskaźnik ma wartość NULL</span><span class="sxs-lookup"><span data-stu-id="e1a34-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer or topic_buffer pointer is NULL</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-399">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-399">Allowed From</span></span>

<span data-ttu-id="e1a34-400">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-401">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-401">Example</span></span>

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a><span data-ttu-id="e1a34-402">nxd_mqtt_client_disconnect_notify_set</span><span class="sxs-lookup"><span data-stu-id="e1a34-402">nxd_mqtt_client_disconnect_notify_set</span></span>

<span data-ttu-id="e1a34-403">Ustaw funkcję wywołania zwrotnego powiadomienia o rozłączeniu komunikatu MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-403">Set MQTT message disconnect notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-404">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-404">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a><span data-ttu-id="e1a34-405">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-405">Description</span></span>

<span data-ttu-id="e1a34-406">Ta usługa rejestruje funkcję wywołania zwrotnego za pomocą klienta MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-406">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="e1a34-407">Gdy MQTT wykrywa połączenie z brokerem, wywołuje tę funkcję powiadamiania o alercie do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1a34-407">When MQTT detects the connection to the broker is lost, it calls this notify function to alert the application.</span></span> <span data-ttu-id="e1a34-408">W związku z tym aplikacja może używać tej funkcji wywołania zwrotnego do wykrywania utraconych połączeń i w celu ponownego nawiązania połączenia z brokerem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-408">Therefore, the application can use this callback function to detect a lost connection, and to be able to re-establish connection to the broker.</span></span>

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a><span data-ttu-id="e1a34-409">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-409">Input Parameters</span></span>

- <span data-ttu-id="e1a34-410">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-410">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="e1a34-411">**disconnect_notify** Funkcja wywołania zwrotnego, która ma zostać wywołana, gdy MQTT wykrywa połączenie z brokerem, zostanie utracona.</span><span class="sxs-lookup"><span data-stu-id="e1a34-411">**disconnect_notify** User supplied callback function to be invoked when MQTT detects the connection to the broker is lost.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-412">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-412">Return Values</span></span>

- <span data-ttu-id="e1a34-413">**NXD_MQTT_SUCCESS** (0X00) pomyślnie ustawił funkcję powiadamiania o rozłączeniu.</span><span class="sxs-lookup"><span data-stu-id="e1a34-413">**NXD_MQTT_SUCCESS** (0x00) Successfully set the disconnect notify function.</span></span>
- <span data-ttu-id="e1a34-414">NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-414">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-415">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-415">Allowed From</span></span>

<span data-ttu-id="e1a34-416">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-417">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-417">Example</span></span>

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a><span data-ttu-id="e1a34-418">nxd_mqtt_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="e1a34-418">nxd_mqtt_client_disconnect</span></span>

<span data-ttu-id="e1a34-419">Odłączanie klienta MQTT od brokera</span><span class="sxs-lookup"><span data-stu-id="e1a34-419">Disconnect MQTT client from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-420">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-420">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="e1a34-421">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-421">Description</span></span>

<span data-ttu-id="e1a34-422">Ta usługa rozłącza klienta od brokera.</span><span class="sxs-lookup"><span data-stu-id="e1a34-422">This service disconnects the client from the broker.</span></span> <span data-ttu-id="e1a34-423">Zwróć uwagę na to, że komunikaty w kolejce odbierania są wydane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-423">Note that messages on the receive queue are released.</span></span> <span data-ttu-id="e1a34-424">Komunikaty z funkcją QoS 1 w kolejce transmisji nie są wydane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-424">Messages with QoS 1 in the transmit queue are not released.</span></span> <span data-ttu-id="e1a34-425">Po ponownym nawiązaniu połączenia klienta z serwerem można przetworzyć komunikaty QoS 1, chyba że klient ponownie nawiąże połączenie z serwerem z flagą *clean_session* ustawioną na ***NX_TRUE***.</span><span class="sxs-lookup"><span data-stu-id="e1a34-425">After the client reconnects to the server, QoS 1 messages can be processed, unless the client reconnects to the server with *clean_session* flag set to ***NX_TRUE***.</span></span>

<span data-ttu-id="e1a34-426">Jeśli połączenie zostało nawiązane z ochroną zabezpieczeń TLS, ta usługa zamknie sesję TLS przed odłączeniem połączenia TCP.</span><span class="sxs-lookup"><span data-stu-id="e1a34-426">If the connection was made with TLS security protection, this service will close the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="e1a34-427">Rzeczywiste wywołanie rozłączenia gniazda TCP jest zdefiniowane przez NXD_MQTT_SOCKET_TIMEOUT (Takty czasomierza).</span><span class="sxs-lookup"><span data-stu-id="e1a34-427">The actual TCP socket disconnect call has a wait option defined by NXD_MQTT_SOCKET_TIMEOUT (timer ticks).</span></span> <span data-ttu-id="e1a34-428">Wartość domyślna to NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="e1a34-428">The default value is NX_WAIT_FOREVER.</span></span> <span data-ttu-id="e1a34-429">Aby uniknąć nieograniczonego zawieszenia w przypadku utraty połączenia sieciowego lub braku odpowiedzi serwera, ustaw tę opcję na wartość skończoną.</span><span class="sxs-lookup"><span data-stu-id="e1a34-429">To avoid indefinite suspension in the event that the network connection is lost or the server is not responding, set this option to a finite value.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-430">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-430">Input Parameters</span></span>

- <span data-ttu-id="e1a34-431">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-431">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-432">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-432">Return Values</span></span>

- <span data-ttu-id="e1a34-433">**NXD_MQTT_SUCCESS** (0X00) zostało pomyślnie rozłączone z brokerem</span><span class="sxs-lookup"><span data-stu-id="e1a34-433">**NXD_MQTT_SUCCESS** (0x00) Successfully disconnected from broker</span></span>
- <span data-ttu-id="e1a34-434">**NXD_MQTT_MUTEX_FAILURE** (0X10003) nie może uzyskać MQTT obiektu MUTEX.</span><span class="sxs-lookup"><span data-stu-id="e1a34-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="e1a34-435">NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-435">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-436">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-436">Allowed From</span></span>

<span data-ttu-id="e1a34-437">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-438">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-438">Example</span></span>

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a><span data-ttu-id="e1a34-439">nxd_mqtt_client_delete</span><span class="sxs-lookup"><span data-stu-id="e1a34-439">nxd_mqtt_client_delete</span></span>

<span data-ttu-id="e1a34-440">Usuwanie wystąpienia klienta MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-440">Delete the MQTT client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="e1a34-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="e1a34-441">Prototype</span></span>

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="e1a34-442">Opis</span><span class="sxs-lookup"><span data-stu-id="e1a34-442">Description</span></span>

<span data-ttu-id="e1a34-443">Ta usługa usuwa wystąpienie klienta MQTT i zwalnia zasoby wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="e1a34-443">This service deletes the MQTT client instance and releases internal resources.</span></span> <span data-ttu-id="e1a34-444">Ta usługa automatycznie rozłącza klienta z brokera, jeśli jest nadal połączony.</span><span class="sxs-lookup"><span data-stu-id="e1a34-444">This service automatically disconnects the client from the broker if it is still connected.</span></span> <span data-ttu-id="e1a34-445">Komunikaty, które nie zostały jeszcze przesłane lub nie zostały potwierdzone, są wydawane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-445">Messages not yet transmitted or not been acknowledged are released.</span></span> <span data-ttu-id="e1a34-446">Komunikaty odebrane, ale nie pobrane przez aplikację są również wydane.</span><span class="sxs-lookup"><span data-stu-id="e1a34-446">Messages received but not retrieved by the application are also released.</span></span>

<span data-ttu-id="e1a34-447">Jeśli nastąpiło połączenie z ochroną zabezpieczeń TLS, ta usługa zamyka sesję protokołu TLS przed odłączeniem połączenia TCP.</span><span class="sxs-lookup"><span data-stu-id="e1a34-447">If the connection was made with TLS security protection, this service closes the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="e1a34-448">Po usunięciu klienta aplikacja, która chce korzystać z usługi MQTT, musi utworzyć nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="e1a34-448">After the client is deleted, an application wishing to use MQTT service needs to create a new instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="e1a34-449">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="e1a34-449">Input Parameters</span></span>

- <span data-ttu-id="e1a34-450">**client_ptr** Wskaźnik do MQTT bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="e1a34-450">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="e1a34-451">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="e1a34-451">Return Values</span></span>

- <span data-ttu-id="e1a34-452">**NXD_MQTT_SUCCESS** (0X00) pomyślnie usunął klienta MQTT.</span><span class="sxs-lookup"><span data-stu-id="e1a34-452">**NXD_MQTT_SUCCESS** (0x00) Successfully deleted MQTT client.</span></span>
- <span data-ttu-id="e1a34-453">NX_PTR_ERROR (0x07) nieprawidłowy blok sterowania MQTT</span><span class="sxs-lookup"><span data-stu-id="e1a34-453">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="e1a34-454">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="e1a34-454">Allowed From</span></span>

<span data-ttu-id="e1a34-455">Wątki</span><span class="sxs-lookup"><span data-stu-id="e1a34-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="e1a34-456">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1a34-456">Example</span></span>

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
