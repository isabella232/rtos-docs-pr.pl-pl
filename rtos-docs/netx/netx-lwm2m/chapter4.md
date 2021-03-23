---
title: Rozdział 4 — Opis usług Azure RTO NetX LWM2M Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX LWM2M Services (wymienionych poniżej) w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5a402790387c2720db304fe93d74252494d7638
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822578"
---
# <a name="chapter-4---description-of-azure-rtos-netx-lwm2m-services"></a><span data-ttu-id="7020e-103">Rozdział 4 — Opis usług Azure RTO NetX LWM2M Services</span><span class="sxs-lookup"><span data-stu-id="7020e-103">Chapter 4 - Description of Azure RTOS NetX LWM2M services</span></span>

<span data-ttu-id="7020e-104">Ten rozdział zawiera opis wszystkich usług Azure RTO NetX LWM2M Services (wymienionych poniżej) w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="7020e-104">This chapter contains a description of all Azure RTOS NetX LWM2M services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="7020e-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="7020e-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

### <a name="lwm2m-client-management"></a><span data-ttu-id="7020e-106">LWM2M zarządzanie klientami</span><span class="sxs-lookup"><span data-stu-id="7020e-106">LWM2M Client Management</span></span>

- <span data-ttu-id="7020e-107">**nx_lwm2m_client_create**: *Utwórz klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-107">**nx_lwm2m_client_create**: *Create LWM2M Client*</span></span>
- <span data-ttu-id="7020e-108">**nx_lwm2m_client_delete**: *Usuwanie klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-108">**nx_lwm2m_client_delete**: *Delete LWM2M Client*</span></span>
- <span data-ttu-id="7020e-109">**nx_lwm2m_client_lock**: *Zablokuj klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-109">**nx_lwm2m_client_lock**: *Lock LWM2M Client*</span></span>
- <span data-ttu-id="7020e-110">**nx_lwm2m_client_object_add**: *Dodawanie implementacji obiektu do klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-110">**nx_lwm2m_client_object_add**: *Add Object implementation to the LWM2M Client*</span></span>
- <span data-ttu-id="7020e-111">**nx_lwm2m_client_unlock**: *Odblokuj klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-111">**nx_lwm2m_client_unlock**: *Unlock LWM2M Client*</span></span>

### <a name="lwm2m-client-session-management"></a><span data-ttu-id="7020e-112">LWM2M zarządzanie sesją klienta</span><span class="sxs-lookup"><span data-stu-id="7020e-112">LWM2M Client Session Management</span></span>

- <span data-ttu-id="7020e-113">**nx_lwm2m_client_session_bootstrap**: *Uruchamianie sesji z serwerem Bootstrap*</span><span class="sxs-lookup"><span data-stu-id="7020e-113">**nx_lwm2m_client_session_bootstrap**: *Start a session with a Bootstrap Server*</span></span>
- <span data-ttu-id="7020e-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Rozpoczynanie bezpiecznej sesji z serwerem Bootstrap*</span><span class="sxs-lookup"><span data-stu-id="7020e-114">**nx_lwm2m_client_session_bootstrap_dtls**: *Start a secure session with a Bootstrap Server*</span></span>
- <span data-ttu-id="7020e-115">**nx_lwm2m_client_session_create**: *Utwórz sesję klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-115">**nx_lwm2m_client_session_create**: *Create LWM2M Client Session*</span></span>
- <span data-ttu-id="7020e-116">**nx_lwm2m_client_session_delete**: *usuwanie sesji klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-116">**nx_lwm2m_client_session_delete**: *Delete LWM2M Client Session*</span></span>
- <span data-ttu-id="7020e-117">**nx_lwm2m_client_session_deregister**: *przerywanie sesji z serwerem lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-117">**nx_lwm2m_client_session_deregister**: *Terminate a session with a LWM2M Server*</span></span>
- <span data-ttu-id="7020e-118">**nx_lwm2m_client_session_error_get**: *Pobierz ostatni błąd sesji*</span><span class="sxs-lookup"><span data-stu-id="7020e-118">**nx_lwm2m_client_session_error_get**: *Get last error of a session*</span></span>
- <span data-ttu-id="7020e-119">**nx_lwm2m_client_session_register**: *Uruchamianie sesji z serwerem lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-119">**nx_lwm2m_client_session_register**: *Start a session with a LWM2M Server*</span></span>
- <span data-ttu-id="7020e-120">**nx_lwm2m_client_session_register_dtls**: *Rozpoczynanie bezpiecznej sesji z serwerem lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-120">**nx_lwm2m_client_session_register_dtls**: *Start a secure session with a LWM2M Server*</span></span>
- <span data-ttu-id="7020e-121">**nx_lwm2m_client_session_update**: *Aktualizowanie sesji przy użyciu serwera lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-121">**nx_lwm2m_client_session_update**: *Update a session with a LWM2M Server*</span></span>

### <a name="security-object-implementation"></a><span data-ttu-id="7020e-122">Implementacja obiektu zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7020e-122">Security Object Implementation</span></span>

- <span data-ttu-id="7020e-123">**nx_lwm2m_client_security_key_callbacks_set**: *Ustaw wywołania zwrotne zarządzania kluczami zabezpieczeń*</span><span class="sxs-lookup"><span data-stu-id="7020e-123">**nx_lwm2m_client_security_key_callbacks_set**: *Set security key management callbacks*</span></span>

### <a name="device-object-implementation"></a><span data-ttu-id="7020e-124">Implementacja obiektu urządzenia</span><span class="sxs-lookup"><span data-stu-id="7020e-124">Device Object Implementation</span></span>

- <span data-ttu-id="7020e-125">**nx_lwm2m_client_device_callbacks_set**: *Ustaw wywołania zwrotne aplikacji obiektu urządzenia*</span><span class="sxs-lookup"><span data-stu-id="7020e-125">**nx_lwm2m_client_device_callbacks_set**: *Set Device Object application callbacks*</span></span>
- <span data-ttu-id="7020e-126">**nx_lwm2m_client_device_error_push**: *Dodaj kod błędu do obiektu urządzenia*</span><span class="sxs-lookup"><span data-stu-id="7020e-126">**nx_lwm2m_client_device_error_push**: *Add error code to Device Object*</span></span>
- <span data-ttu-id="7020e-127">**nx_lwm2m_client_device_error_reset**: *Resetowanie kodów błędów obiektu urządzenia*</span><span class="sxs-lookup"><span data-stu-id="7020e-127">**nx_lwm2m_client_device_error_reset**: *Reset error codes of Device Object*</span></span>
- <span data-ttu-id="7020e-128">**nx_lwm2m_client_device_resource_changed**: *zmiana sygnału zasobu obiektu urządzenia*</span><span class="sxs-lookup"><span data-stu-id="7020e-128">**nx_lwm2m_client_device_resource_changed**: *Signal change of Device Object resource*</span></span>

### <a name="custom-objects-implementation"></a><span data-ttu-id="7020e-129">Implementacja obiektów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7020e-129">Custom Objects Implementation</span></span>

- <span data-ttu-id="7020e-130">**nx_lwm2m_object_resource_changed**: *zmiana sygnału dla wartości zasobu wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-130">**nx_lwm2m_object_resource_changed**: *Signal change of a resource value of an Object Instance*</span></span>

### <a name="local-device-management"></a><span data-ttu-id="7020e-131">Zarządzanie urządzeniami lokalnymi</span><span class="sxs-lookup"><span data-stu-id="7020e-131">Local Device Management</span></span>

- <span data-ttu-id="7020e-132">**nx_lwm2m_client_object_create**: *Utwórz nowe wystąpienie obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-132">**nx_lwm2m_client_object_create**: *Create a new Object Instance*</span></span>
- <span data-ttu-id="7020e-133">**nx_lwm2m_client_object_delete**: *usuwanie wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-133">**nx_lwm2m_client_object_delete**: *Delete an Object Instance*</span></span>
- <span data-ttu-id="7020e-134">**nx_lwm2m_client_object_discover**: *odnajdywanie zasobów wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-134">**nx_lwm2m_client_object_discover**: *Discover resources of an Object Instance*</span></span>
- <span data-ttu-id="7020e-135">**nx_lwm2m_client_object_execute**: *wykonywanie zasobu wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-135">**nx_lwm2m_client_object_execute**: *Execute resource of an Object Instance*</span></span>
- <span data-ttu-id="7020e-136">**nx_lwm2m_client_object_get_next**: *Pobieranie listy obiektów wdrożonych przez klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="7020e-136">**nx_lwm2m_client_object_get_next**: *Get the list of Objects implemented by the LWM2M Client*</span></span>
- <span data-ttu-id="7020e-137">**nx_lwm2m_client_object_instance_get_next**: *Pobieranie listy wystąpień obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-137">**nx_lwm2m_client_object_instance_get_next**: *Get the list of Instances of an Object*</span></span>
- <span data-ttu-id="7020e-138">**nx_lwm2m_client_object_read**: *Odczytywanie wartości zasobów wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-138">**nx_lwm2m_client_object_read**: *Read resources values of an Object Instance*</span></span>
- <span data-ttu-id="7020e-139">**nx_lwm2m_client_object_write**: *zmiana wartości zasobów wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-139">**nx_lwm2m_client_object_write**: *Change resources values of an Object instance*</span></span>

### <a name="resources-values-decoding"></a><span data-ttu-id="7020e-140">Dekodowanie wartości zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-140">Resources Values Decoding</span></span>

- <span data-ttu-id="7020e-141">**nx_lwm2m_resource_get_boolean**: *pobieranie wartości zasobu logicznego*</span><span class="sxs-lookup"><span data-stu-id="7020e-141">**nx_lwm2m_resource_get_boolean**: *Get the value of a Boolean Resource*</span></span>
- <span data-ttu-id="7020e-142">**nx_lwm2m_resource_get_float32**: *pobieranie wartości 32-bitowego zasobu zmiennoprzecinkowego*</span><span class="sxs-lookup"><span data-stu-id="7020e-142">**nx_lwm2m_resource_get_float32**: *Get the value of a 32-bit Floating Point Resource*</span></span>
- <span data-ttu-id="7020e-143">**nx_lwm2m_resource_get_float64**: *pobieranie wartości 64-bitowego zasobu zmiennoprzecinkowego*</span><span class="sxs-lookup"><span data-stu-id="7020e-143">**nx_lwm2m_resource_get_float64**: *Get the value of a 64-bit Floating Point Resource*</span></span>
- <span data-ttu-id="7020e-144">**nx_lwm2m_resource_get_integer32**: *pobieranie wartości 32-bitowego zasobu liczb całkowitych*</span><span class="sxs-lookup"><span data-stu-id="7020e-144">**nx_lwm2m_resource_get_integer32**: *Get the value of a 32-Bit Integer Resource*</span></span>
- <span data-ttu-id="7020e-145">**nx_lwm2m_resource_get_integer64**: *pobieranie wartości 64-bitowego zasobu liczb całkowitych*</span><span class="sxs-lookup"><span data-stu-id="7020e-145">**nx_lwm2m_resource_get_integer64**: *Get the value of a 64-Bit Integer Resource*</span></span>
- <span data-ttu-id="7020e-146">**nx_lwm2m_resource_get_objlnk**: *pobieranie wartości zasobu linku do obiektu*</span><span class="sxs-lookup"><span data-stu-id="7020e-146">**nx_lwm2m_resource_get_objlnk**: *Get the value of an Object Link Resource*</span></span>
- <span data-ttu-id="7020e-147">**nx_lwm2m_resource_get_opaque**: *Pobierz wartość nieprzezroczystego zasobu*</span><span class="sxs-lookup"><span data-stu-id="7020e-147">**nx_lwm2m_resource_get_opaque**: *Get the value of an Opaque Resource*</span></span>
- <span data-ttu-id="7020e-148">**nx_lwm2m_resource_get_string**: *pobieranie wartości zasobu ciągu*</span><span class="sxs-lookup"><span data-stu-id="7020e-148">**nx_lwm2m_resource_get_string**: *Get the value of a String Resource*</span></span>
- <span data-ttu-id="7020e-149">**nx_lwm2m_resource_multiple_get_boolean**: *Pobierz wartość zasobu logicznego z wieloma wystąpieniami zasobów*</span><span class="sxs-lookup"><span data-stu-id="7020e-149">**nx_lwm2m_resource_multiple_get_boolean**: *Get the value of a Boolean Resource Multiple Resource Instance*</span></span>
- <span data-ttu-id="7020e-150">**nx_lwm2m_resource_multiple_get_float32**: *pobieranie wartości 32-bitowej liczby zmiennoprzecinkowej wielu wystąpień zasobów*</span><span class="sxs-lookup"><span data-stu-id="7020e-150">**nx_lwm2m_resource_multiple_get_float32**: *Get the value of a 32-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="7020e-151">**nx_lwm2m_resource_multiple_get_float64**: *pobieranie wartości 64-bitowej liczby zmiennoprzecinkowej wielu wystąpień zasobów*</span><span class="sxs-lookup"><span data-stu-id="7020e-151">**nx_lwm2m_resource_multiple_get_float64**: *Get the value of a 64-bit Floating Point Multiple Resource Instance*</span></span>
- <span data-ttu-id="7020e-152">**nx_lwm2m_resource_multiple_get_integer32**: *Pobierz wartość 32-bitowej liczby całkowitej wiele wystąpień zasobów*</span><span class="sxs-lookup"><span data-stu-id="7020e-152">**nx_lwm2m_resource_multiple_get_integer32**: *Get the value of a 32-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="7020e-153">**nx_lwm2m_resource_multiple_get_integer64**: *Pobierz wartość 64-bitowej liczby całkowitej wiele wystąpień zasobów*</span><span class="sxs-lookup"><span data-stu-id="7020e-153">**nx_lwm2m_resource_multiple_get_integer64**: *Get the value of a 64-Bit Integer Multiple Resource Instance*</span></span>
- <span data-ttu-id="7020e-154">**nx_lwm2m_resource_multiple_get_objlnk**: *pobieranie wartości linku do obiektu z wieloma wystąpieniami zasobów*</span><span class="sxs-lookup"><span data-stu-id="7020e-154">**nx_lwm2m_resource_multiple_get_objlnk**: *Get the value of an Object Link Multiple Resource Instance*</span></span>
- <span data-ttu-id="7020e-155">**nx_lwm2m_resource_multiple_get_opaque**: *Pobierz wartość nieprzezroczystego wystąpienia wielu zasobów*</span><span class="sxs-lookup"><span data-stu-id="7020e-155">**nx_lwm2m_resource_multiple_get_opaque**: *Get the value of an Opaque Multiple Resource Instance*</span></span>
- <span data-ttu-id="7020e-156">**nx_lwm2m_resource_multiple_get_string**: *Pobierz wartość ciągu z wieloma wystąpieniami zasobów*</span><span class="sxs-lookup"><span data-stu-id="7020e-156">**nx_lwm2m_resource_multiple_get_string**: *Get the value of a String Multiple Resource Instance*</span></span>

### <a name="firmware-update-object"></a><span data-ttu-id="7020e-157">Obiekt aktualizacji oprogramowania układowego</span><span class="sxs-lookup"><span data-stu-id="7020e-157">Firmware Update Object</span></span>

- <span data-ttu-id="7020e-158">**nx_lwm2m_firmware_create**: *Tworzenie obiektu aktualizacji oprogramowania układowego*</span><span class="sxs-lookup"><span data-stu-id="7020e-158">**nx_lwm2m_firmware_create**: *Create Firmware Update Object*</span></span>
- <span data-ttu-id="7020e-159">**nx_lwm2m_firmware_package_info_set**: *Ustawianie informacji o pakiecie aktualizacji oprogramowania układowego*</span><span class="sxs-lookup"><span data-stu-id="7020e-159">**nx_lwm2m_firmware_package_info_set**: *Set Firmware Update Package Information*</span></span>
- <span data-ttu-id="7020e-160">**nx_lwm2m_firmware_result_set**: *Ustaw wynik aktualizacji oprogramowania układowego*</span><span class="sxs-lookup"><span data-stu-id="7020e-160">**nx_lwm2m_firmware_result_set**: *Set Firmware Update Result*</span></span>
- <span data-ttu-id="7020e-161">**nx_lwm2m_firmware_state_set**: *Ustaw stan aktualizacji oprogramowania układowego*</span><span class="sxs-lookup"><span data-stu-id="7020e-161">**nx_lwm2m_firmware_state_set**: *Set Firmware Update State*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="7020e-162">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="7020e-162">nx_lwm2m_client_create</span></span>

<span data-ttu-id="7020e-163">Utwórz klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-163">Create LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-164">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-164">Prototype</span></span>

```c
UINT nx_lwm2m_client_create(NX_LWM2M_CLIENT *client_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr, UINT local_port, const CHAR *name_ptr,
    const CHAR *msisdn_ptr, UCHAR binding_modes, VOID *stack_ptr, ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="7020e-165">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-165">Description</span></span>

<span data-ttu-id="7020e-166">Ta usługa tworzy wystąpienie klienta LWM2M, które działa w kontekście jego własnego wątku ThreadX.</span><span class="sxs-lookup"><span data-stu-id="7020e-166">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="7020e-167">Klient LWM2M implementuje następujące obiekty OMA LWM2M: Security (0), Server (1), Access Control (2) i Device (3).</span><span class="sxs-lookup"><span data-stu-id="7020e-167">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="7020e-168">Inne implementacje obiektów muszą być dodane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7020e-168">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-169">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-169">Parameters</span></span>

- <span data-ttu-id="7020e-170">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-170">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-171">**ip_ptr**: wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="7020e-171">**ip_ptr**: Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="7020e-172">**packet_pool_ptr**: wskaźnik do domyślnej puli pakietów dla tego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-172">**packet_pool_ptr**: Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="7020e-173">**local_port**: lokalny port UDP używany do komunikacji niezabezpieczonej.</span><span class="sxs-lookup"><span data-stu-id="7020e-173">**local_port**: The local UDP port used for non-secure communication.</span></span>
- <span data-ttu-id="7020e-174">**name_ptr**: wskaźnik do LWM2M nazwa punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-174">**name_ptr**: Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="7020e-175">**msisdn_ptr**: wskaźnik do msisdn, w którym można skontaktować się z klientem LWM2M do użycia z POWIĄZANIEM programu SMS, może mieć wartość null, Jeśli powiązanie programu SMS nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="7020e-175">**msisdn_ptr**: Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="7020e-176">**binding_modes**: powiązanie i tryby obsługiwane przez klienta LWM2M muszą być kombinacją flag NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S i NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="7020e-176">**binding_modes**: The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="7020e-177">**stack_ptr**: wskaźnik do LWM2M obszaru stosu wątków klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-177">**stack_ptr**: Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="7020e-178">**stack_size**: rozmiar stosu wątku klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-178">**stack_size**: The LWM2M Client thread stack size.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-179">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-179">Return Values</span></span>

- <span data-ttu-id="7020e-180">**NX_SUCCESS**: klient LWM2M został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="7020e-180">**NX_SUCCESS**: The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="7020e-181">**NX_LWM2M_ERROR**: Wystąpił błąd podczas tworzenia klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-181">**NX_LWM2M_ERROR**: LWM2M Client create error.</span></span>
- <span data-ttu-id="7020e-182">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-182">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="7020e-183">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="7020e-183">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="7020e-184">Usuwanie klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-184">Delete LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-185">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-185">Prototype</span></span>

```c
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-186">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-186">Description</span></span>

<span data-ttu-id="7020e-187">Ta usługa usuwa wcześniej utworzone wystąpienie klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-187">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="7020e-188">Wszystkie sesje, które są obecnie dołączone do klienta, są również usuwane przez to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="7020e-188">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-189">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-189">Parameters</span></span>

- <span data-ttu-id="7020e-190">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-190">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-191">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-191">Return Values</span></span>

- <span data-ttu-id="7020e-192">**NX_SUCCESS**: klient LWM2M został pomyślnie usunięty.</span><span class="sxs-lookup"><span data-stu-id="7020e-192">**NX_SUCCESS**: The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="7020e-193">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-193">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_callbacks_set"></a><span data-ttu-id="7020e-194">nx_lwm2m_client_device_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="7020e-194">nx_lwm2m_client_device_callbacks_set</span></span>

<span data-ttu-id="7020e-195">Ustawianie wywołania zwrotnego aplikacji obiektu urządzenia</span><span class="sxs-lookup"><span data-stu-id="7020e-195">Set Device Object application callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-196">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-196">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_READ_CALLBACK read_callback,
    NX_LWM2M_CLIENT_DEVICE_DISCOVER_CALLBACK discover_callback,
    NX_LWM2M_CLIENT_DEVICE_WRITE_CALLBACK write_callback,
    NX_LWM2M_CLIENT_DEVICE_EXECUTE_CALLBACK execute_callback);
```

### <a name="description"></a><span data-ttu-id="7020e-197">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-197">Description</span></span>

<span data-ttu-id="7020e-198">Ta usługa instaluje wywołania zwrotne aplikacji w celu zaimplementowania operacji na zasobach obiektów urządzenia LWM2M, które nie są obsługiwane przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-198">This service installs the application callbacks for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="7020e-199">Klient LWM2M implementuje następujące zasoby: kod błędu (11), resetowanie kodu błędu (12) i obsługiwane powiązania i tryby (16), operacje innych zasobów są przekierowywane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7020e-199">The LWM2M Client implements the following resources : Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-200">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-200">Parameters</span></span>

- <span data-ttu-id="7020e-201">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-201">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-202">**read_callback**: wywołanie zwrotne metody "read".</span><span class="sxs-lookup"><span data-stu-id="7020e-202">**read_callback**: The 'Read' method callback.</span></span>
- <span data-ttu-id="7020e-203">**discover_callback**: wywołanie zwrotne metody "Discovery".</span><span class="sxs-lookup"><span data-stu-id="7020e-203">**discover_callback**: The 'Discover' method callback.</span></span>
- <span data-ttu-id="7020e-204">**write_callback**: wywołanie zwrotne metody "Write".</span><span class="sxs-lookup"><span data-stu-id="7020e-204">**write_callback**: The 'Write' method callback.</span></span>
- <span data-ttu-id="7020e-205">**execute_callback**: wywołanie zwrotne metody "Execute".</span><span class="sxs-lookup"><span data-stu-id="7020e-205">**execute_callback**: The 'Execute' method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-206">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-206">Return Values</span></span>

- <span data-ttu-id="7020e-207">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-207">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-208">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-208">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="7020e-209">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="7020e-209">nx_lwm2m_client_device_error_push</span></span>

<span data-ttu-id="7020e-210">Dodawanie kodu błędu do obiektu urządzenia</span><span class="sxs-lookup"><span data-stu-id="7020e-210">Add error code to Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-211">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-211">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_push(NX_LWM2M_CLIENT *client_ptr, UCHAR code);
```

### <a name="description"></a><span data-ttu-id="7020e-212">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-212">Description</span></span>

<span data-ttu-id="7020e-213">Ta usługa dodaje nowe wystąpienie do zasobu kod błędu (11) urządzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-213">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-214">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-214">Parameters</span></span>

- <span data-ttu-id="7020e-215">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-215">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-216">**kod**: nowy kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7020e-216">**code**: The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-217">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-217">Return Values</span></span>

- <span data-ttu-id="7020e-218">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-218">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-219">**NX_LWM2M_BUFFER_TOO_SMALL**: osiągnięto maksymalną liczbę przechowywanych kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="7020e-219">**NX_LWM2M_BUFFER_TOO_SMALL**: The maximum number of stored error codes has been reached.</span></span>
- <span data-ttu-id="7020e-220">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-220">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="7020e-221">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="7020e-221">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="7020e-222">Resetuj kody błędów obiektu urządzenia</span><span class="sxs-lookup"><span data-stu-id="7020e-222">Reset error codes of Device Object</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-223">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-223">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-224">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-224">Description</span></span>

<span data-ttu-id="7020e-225">Ta usługa usuwa wszystkie wystąpienia zasobów kodu błędu z obiektu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="7020e-225">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="7020e-226">Jest to równoznaczne z wykonaniem kodu błędu resetowania zasobu (12).</span><span class="sxs-lookup"><span data-stu-id="7020e-226">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-227">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-227">Parameters</span></span>

- <span data-ttu-id="7020e-228">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-228">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-229">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-229">Return Values</span></span>

- <span data-ttu-id="7020e-230">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-230">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-231">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-231">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="7020e-232">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="7020e-232">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="7020e-233">Zmiana sygnału zasobu obiektu urządzenia</span><span class="sxs-lookup"><span data-stu-id="7020e-233">Signal change of Device Object resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-234">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-234">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(NX_LWM2M_CLIENT *client_ptr,
                                    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="7020e-235">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-235">Description</span></span>

<span data-ttu-id="7020e-236">Usługa jest używana przez aplikację do sygnalizowania klienta LWM2M, że zasób urządzenia obiektu został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="7020e-236">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="7020e-237">Klient LWM2M wyśle powiadomienie, jeśli zasób jest zaobserwowany przez serwer LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-237">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-238">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-238">Parameters</span></span>

- <span data-ttu-id="7020e-239">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-239">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-240">**zasób**: wskaźnik do struktury opisującej zasób, który został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="7020e-240">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-241">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-241">Return Values</span></span>

- <span data-ttu-id="7020e-242">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-242">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-243">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-243">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="7020e-244">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="7020e-244">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="7020e-245">Zablokuj klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-245">Lock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-246">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-246">Prototype</span></span>

```c
UINT nx_lwm2m_client_lock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-247">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-247">Description</span></span>

<span data-ttu-id="7020e-248">Ta usługa blokuje klienta LWM2M, aby uniemożliwić concurent dostęp do obiektów LWM2M z serwerów lub z innego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7020e-248">This service locks the LWM2M Client to prevent concurent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="7020e-249">Jeśli klient LWM2M jest obecnie zablokowany przez inny wątek, funkcja zostanie Zablokowani do momentu odblokowania klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-249">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="7020e-250">Wywołania nx_lwm2m_client_lock ()/nx_lwm2m_client_unlock () mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="7020e-250">Calls to nx_lwm2m_client_lock()/nx_lwm2m_client_unlock() pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-251">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-251">Parameters</span></span>

- <span data-ttu-id="7020e-252">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-252">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-253">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-253">Return Values</span></span>

- <span data-ttu-id="7020e-254">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-254">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-255">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-255">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="7020e-256">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="7020e-256">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="7020e-257">Dodawanie implementacji obiektu do klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-257">Add Object implementation to the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-258">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-258">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_add(NX_LWM2M_CLIENT *client_ptr,
                                NX_LWM2M_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-259">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-259">Description</span></span>

<span data-ttu-id="7020e-260">Ta usługa dodaje nową implementację obiektu do klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-260">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-261">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-261">Parameters</span></span>

- <span data-ttu-id="7020e-262">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-262">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-263">**object_ptr**: wskaźnik do struktury definiującej implementację obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-263">**object_ptr**: Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-264">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-264">Return Values</span></span>

- <span data-ttu-id="7020e-265">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-265">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-266">**NX_LWM2M_ALREADY_EXIST**: identyfikator obiektu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="7020e-266">**NX_LWM2M_ALREADY_EXIST**: The Object ID already exists.</span></span>
- <span data-ttu-id="7020e-267">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-267">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="7020e-268">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="7020e-268">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="7020e-269">Utwórz nowe wystąpienie obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-269">Create a new Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-270">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-270">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(NX_LWM2M_CLIENT *client_ptr,
            NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr,
            UINT num_values, const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-271">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-271">Description</span></span>

<span data-ttu-id="7020e-272">Ta usługa wykonuje operację "Create" na obiekcie klienta LWM2M, aby utworzyć nowe wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-272">This service performs a 'Create' operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-273">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-273">Parameters</span></span>

- <span data-ttu-id="7020e-274">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-274">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-275">**object_id**: identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-275">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="7020e-276">**instance_id_ptr**: wskaźnik do identyfikatora nowego wystąpienia może mieć wartość null, jeśli klient LWM2M musi przypisać identyfikator wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-276">**instance_id_ptr**: Pointer to the ID of the new instance, can be NULL if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="7020e-277">Jeśli identyfikator jest wartością zarezerwowaną 65535, klient LWM2M przypisze identyfikator wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-277">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="7020e-278">Jeśli wartość nie jest równa NULL, przypisany identyfikator jest zwracany po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="7020e-278">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="7020e-279">**num_values**: liczba wartości do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-279">**num_values**: The number of values to set.</span></span>
- <span data-ttu-id="7020e-280">**values_ptr**: wskaźnik do tablicy wartości zasobów, aby zainicjować nowe wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-280">**values_ptr**: Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-281">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-281">Return Values</span></span>

- <span data-ttu-id="7020e-282">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-282">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-283">**NX_LWM2M_ALREADY_EXIST**: identyfikator wystąpienia obiektu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="7020e-283">**NX_LWM2M_ALREADY_EXIST**: The Object Instance ID already exists.</span></span>
- <span data-ttu-id="7020e-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: obiekt nie obsługuje tworzenia wystąpień.</span><span class="sxs-lookup"><span data-stu-id="7020e-284">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance creation.</span></span>
- <span data-ttu-id="7020e-285">**NX_LWM2M_NO_MEMORY**: nie można przydzielić pamięci do zapisania nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-285">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="7020e-286">**NX_LWM2M_NOT_FOUND**: identyfikator obiektu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7020e-286">**NX_LWM2M_NOT_FOUND**: The Object ID doesn't exist.</span></span>
- <span data-ttu-id="7020e-287">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-287">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="7020e-288">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="7020e-288">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="7020e-289">Usuwanie wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-289">Delete an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-290">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-290">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="7020e-291">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-291">Description</span></span>

<span data-ttu-id="7020e-292">Ta usługa wykonuje operację "Delete" na wystąpieniu obiektu klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-292">This service performs a 'Delete' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-293">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-293">Parameters</span></span>

- <span data-ttu-id="7020e-294">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-294">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-295">**object_id**: identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-295">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="7020e-296">**instance_ID**: identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-296">**instance_id**: The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-297">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-297">Return Values</span></span>

- <span data-ttu-id="7020e-298">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-298">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: obiekt nie obsługuje usuwania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-299">**NX_LWM2M_METHOD_NOT_ALLOWED**: The Object doesn't support instance deletion.</span></span>
- <span data-ttu-id="7020e-300">**NX_LWM2M_NOT_FOUND**: identyfikator obiektu lub identyfikatora wystąpienia obiektu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7020e-300">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="7020e-301">NX_PTR_ERROR nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-301">NX_PTR_ERROR Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="7020e-302">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="7020e-302">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="7020e-303">Odnajdywanie zasobów wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-303">Discover resources of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-304">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-304">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT *num_resources_ptr, NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-305">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-305">Description</span></span>

<span data-ttu-id="7020e-306">Ta usługa wykonuje operację "Discover" na wystąpieniu obiektu klienta LWM2M, która zwraca listę zasobów implementowanych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="7020e-306">This service performs a 'Discover' operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-307">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-307">Parameters</span></span>

- <span data-ttu-id="7020e-308">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-308">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-309">**object_id**: identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-309">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="7020e-310">**instance_ID**: identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-310">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="7020e-311">**num_resources_ptr**: przy wprowadzaniu rozmiaru buforu docelowego w danych wyjściowych liczba elementów WRITEN do buforu.</span><span class="sxs-lookup"><span data-stu-id="7020e-311">**num_resources_ptr**: On input the size of the destination buffer, on output the number of elements writen to the buffer.</span></span>
- <span data-ttu-id="7020e-312">**resources_ptr**: wskaźnik do bufora docelowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-312">**resources_ptr**: Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-313">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-313">Return Values</span></span>

- <span data-ttu-id="7020e-314">**NX_SUCCESS**: operacja powiodła się..</span><span class="sxs-lookup"><span data-stu-id="7020e-314">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="7020e-315">**NX_LWM2M_BUFFER_TOO_SMALL**: bufor zasobów jest za mały, aby można było przechowywać listę zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-315">**NX_LWM2M_BUFFER_TOO_SMALL**: The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="7020e-316">**NX_LWM2M_NOT_FOUND**: identyfikator obiektu lub identyfikatora wystąpienia obiektu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7020e-316">**NX_LWM2M_NOT_FOUND**: The Object ID or Object Instance ID doesn't exist.</span></span>
- <span data-ttu-id="7020e-317">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-317">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="7020e-318">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="7020e-318">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="7020e-319">Wykonaj zasób wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-319">Execute resource of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-320">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-320">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_execute(NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr, UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="7020e-321">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-321">Description</span></span>

<span data-ttu-id="7020e-322">Ta usługa wykonuje operację "Execute" na zasobie wystąpienia obiektu klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-322">This service performs the 'Execute' operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-323">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-323">Parameters</span></span>

- <span data-ttu-id="7020e-324">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-324">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-325">**object_id**: identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-325">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="7020e-326">**instance_ID**: identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-326">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="7020e-327">**resource_id**: Identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-327">**resource_id**: The Resource ID.</span></span>
- <span data-ttu-id="7020e-328">**arguments_ptr**: wskaźnik do argumentów operacji Execute.</span><span class="sxs-lookup"><span data-stu-id="7020e-328">**arguments_ptr**: Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="7020e-329">Może mieć wartość NULL, jeśli arguments_length wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="7020e-329">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="7020e-330">**arguments_length**: długość argumentów.</span><span class="sxs-lookup"><span data-stu-id="7020e-330">**arguments_length**: The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-331">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-331">Return Values</span></span>

- <span data-ttu-id="7020e-332">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-332">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: zasób nie obsługuje operacji Execute.</span><span class="sxs-lookup"><span data-stu-id="7020e-333">**NX_LWM2M_METHOD_NOT_ALLOWED**: The resource doesn't support the execute operation.</span></span>
- <span data-ttu-id="7020e-334">**NX_LWM2M_NOT_FOUND**: identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7020e-334">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or the resource ID doesn't exist.</span></span>
- <span data-ttu-id="7020e-335">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-335">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_get_next"></a><span data-ttu-id="7020e-336">nx_lwm2m_client_object_get_next</span><span class="sxs-lookup"><span data-stu-id="7020e-336">nx_lwm2m_client_object_get_next</span></span>

<span data-ttu-id="7020e-337">Pobierz listę obiektów wdrożonych przez klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-337">Get the list of Objects implemented by the LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-338">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-338">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_get_next(NX_LWM2M_CLIENT *client_ptr,
                                    NX_LWM2M_ID *object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-339">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-339">Description</span></span>

<span data-ttu-id="7020e-340">Ta usługa zwraca identyfikator następnego obiektu implementowanego przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-340">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="7020e-341">Jeśli bieżący identyfikator obiektu jest ustawiony na NX_LWM2M_RESERVED_ID (65535), zwracany jest pierwszy identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-341">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-342">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-342">Parameters</span></span>

- <span data-ttu-id="7020e-343">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-343">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-344">**object_id_ptr**: wskaźnik do bieżącego identyfikatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-344">**object_id_ptr**: Pointer to the current Object ID.</span></span> <span data-ttu-id="7020e-345">On return zawiera następny identyfikator obiektu zaimplementowany przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-345">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-346">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-346">Return Values</span></span>

- <span data-ttu-id="7020e-347">**NX_SUCCESS**: operacja powiodła się..</span><span class="sxs-lookup"><span data-stu-id="7020e-347">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="7020e-348">**NX_LWM2M_NOT_FOUND**: dany identyfikator obiektu jest ostatnim z baz danych.</span><span class="sxs-lookup"><span data-stu-id="7020e-348">**NX_LWM2M_NOT_FOUND**: The given Object ID is the last of the database.</span></span>
- <span data-ttu-id="7020e-349">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-349">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_instance_get_next"></a><span data-ttu-id="7020e-350">nx_lwm2m_client_object_instance_get_next</span><span class="sxs-lookup"><span data-stu-id="7020e-350">nx_lwm2m_client_object_instance_get_next</span></span>

<span data-ttu-id="7020e-351">Pobierz listę wystąpień obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-351">Get the list of Instances of an Object</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-352">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-352">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_get_next(NX_LWM2M_CLIENT *client_ptr,
                    NX_LWM2M_ID object_id, NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-353">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-353">Description</span></span>

<span data-ttu-id="7020e-354">Ta usługa zwraca identyfikator następnego wystąpienia obiektu danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-354">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="7020e-355">Jeśli bieżący identyfikator wystąpienia ma wartość NX_LWM2M_RESERVED_ID (65535) zwracany jest identyfikator pierwszego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-355">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-356">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-356">Parameters</span></span>

- <span data-ttu-id="7020e-357">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-357">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-358">**object_id**: identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-358">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="7020e-359">**instance_id_ptr**: wskaźnik do bieżącego identyfikatora wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-359">**instance_id_ptr**: Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="7020e-360">On return zawiera identyfikator następnego wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-360">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-361">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-361">Return Values</span></span>

- <span data-ttu-id="7020e-362">**NX_SUCCESS**: operacja powiodła się..</span><span class="sxs-lookup"><span data-stu-id="7020e-362">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="7020e-363">**NX_LWM2M_NOT_FOUND**: dany identyfikator wystąpienia jest ostatnim obiektem lub identyfikator obiektu nie jest zaimplementowany.</span><span class="sxs-lookup"><span data-stu-id="7020e-363">**NX_LWM2M_NOT_FOUND**: The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="7020e-364">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-364">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="7020e-365">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="7020e-365">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="7020e-366">Odczytaj wartości zasobów wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-366">Read resources values of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-367">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-367">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id,
        UINT num_values, NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="7020e-368">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-368">Description</span></span>

<span data-ttu-id="7020e-369">Ta usługa wykonuje operację "read" na wystąpieniu obiektu klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-369">This service performs a 'Read' operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-370">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-370">Parameters</span></span>

- <span data-ttu-id="7020e-371">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-371">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-372">**object_id**: identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-372">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="7020e-373">**instance_ID**: identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-373">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="7020e-374">**num_values**: liczba zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="7020e-374">**num_values**: The number of resources to read.</span></span>
- <span data-ttu-id="7020e-375">**values_ptr**: wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="7020e-375">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="7020e-376">Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.</span><span class="sxs-lookup"><span data-stu-id="7020e-376">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-377">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-377">Return Values</span></span>

- <span data-ttu-id="7020e-378">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-378">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: zasób nie obsługuje operacji odczytu.</span><span class="sxs-lookup"><span data-stu-id="7020e-379">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the read operation.</span></span>
- <span data-ttu-id="7020e-380">**NX_LWM2M_NOT_FOUND**: identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7020e-380">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="7020e-381">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-381">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="7020e-382">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="7020e-382">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="7020e-383">Zmiana wartości zasobów wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-383">Change resources values of an Object instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-384">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-384">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(NX_LWM2M_CLIENT *client_ptr,
        NX_LWM2M_ID object_id, NX_LWM2M_ID instance_id, UINT num_values,
        const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

### <a name="description"></a><span data-ttu-id="7020e-385">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-385">Description</span></span>

<span data-ttu-id="7020e-386">Ta usługa wykonuje operację "Write" na wystąpieniu obiektu klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-386">This service performs a 'Write' operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="7020e-387">Do *write_op* parametru można określić następujące operacje zapisu:</span><span class="sxs-lookup"><span data-stu-id="7020e-387">The following write operations can be specified to the *write_op* parameter:</span></span>

- <span data-ttu-id="7020e-388">**0** &mdash; aktualizacja częściowa: dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian.</span><span class="sxs-lookup"><span data-stu-id="7020e-388">**0** &mdash; Partial Update: adds or updates Resources provided in the new value and leaves other existing Resources unchanged,</span></span>

- <span data-ttu-id="7020e-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Zamień wystąpienie: zamienia wystąpienie obiektu na nowe podane wartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-389">**NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Replace Instance: replaces the Object Instance with the new provided resource values.</span></span>

- <span data-ttu-id="7020e-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Zastąp zasób: zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów).</span><span class="sxs-lookup"><span data-stu-id="7020e-390">**NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Replace Resource: replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span>

- <span data-ttu-id="7020e-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Zapis ładowania początkowego: wskazuje wywołanie z sekwencji ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-391">**NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Bootstrap Write: indicates a call from a Bootstrap sequence.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-392">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-392">Parameters</span></span>

- <span data-ttu-id="7020e-393">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-393">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-394">**object_id**: identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-394">**object_id**: The Object ID.</span></span>
- <span data-ttu-id="7020e-395">**instance_ID**: identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-395">**instance_id**: The Object Instance ID.</span></span>
- <span data-ttu-id="7020e-396">**num_values**: liczba zasobów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="7020e-396">**num_values**: The number of resources to write.</span></span>
- <span data-ttu-id="7020e-397">**values_ptr**: wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów, typy i wartości do zapisania.</span><span class="sxs-lookup"><span data-stu-id="7020e-397">**values_ptr**: Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="7020e-398">**write_op**: typ operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="7020e-398">**write_op**: The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-399">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-399">Return Values</span></span>

- <span data-ttu-id="7020e-400">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-400">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-401">**NX_LWM2M_BAD_ENCODING**: typ zasobu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7020e-401">**NX_LWM2M_BAD_ENCODING**: The type of a resource is not valid.</span></span>
- <span data-ttu-id="7020e-402">**NX_LWM2M_BUFFER_TOO_SMALL**: długość wartości jest zbyt duża, aby można było ją zapisać w wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="7020e-402">**NX_LWM2M_BUFFER_TOO_SMALL**: The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="7020e-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: zasób nie obsługuje operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="7020e-403">**NX_LWM2M_METHOD_NOT_ALLOWED**: A resource doesn't support the write operation.</span></span>
- <span data-ttu-id="7020e-404">**NX_LWM2M_NO_MEMORY**: nie można przydzielić pamięci do przechowywania wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-404">**NX_LWM2M_NO_MEMORY**: Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="7020e-405">**NX_LWM2M_NOT_ACCEPTABLE**: wartość zasobu jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="7020e-405">**NX_LWM2M_NOT_ACCEPTABLE**: The value of a resource is not valid.</span></span>
- <span data-ttu-id="7020e-406">**NX_LWM2M_NOT_FOUND**: identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7020e-406">**NX_LWM2M_NOT_FOUND**: The Object ID, Object Instance ID or a resource ID doesn't exist.</span></span>
- <span data-ttu-id="7020e-407">NX_OPTION_ERROR: nieprawidłowy typ operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="7020e-407">NX_OPTION_ERROR: Invalid type of write operation.</span></span>
- <span data-ttu-id="7020e-408">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-408">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_security_key_callbacks_set"></a><span data-ttu-id="7020e-409">nx_lwm2m_client_security_key_callbacks_set</span><span class="sxs-lookup"><span data-stu-id="7020e-409">nx_lwm2m_client_security_key_callbacks_set</span></span>

<span data-ttu-id="7020e-410">Ustaw wywołania zwrotne zarządzania kluczami obiektów zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="7020e-410">Set Security Object key management callbacks</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-411">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-411">Prototype</span></span>

```c
UINT nx_lwm2m_client_security_key_callbacks_set(NX_LWM2M_CLIENT *client_ptr,
                NX_LWM2M_CLIENT_SECURITY_KEY_WRITE_CALLBACK write_callback,
                NX_LWM2M_CLIENT_SECURITY_KEY_DELETE_CALLBACK delete_callback);
```

### <a name="description"></a><span data-ttu-id="7020e-412">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-412">Description</span></span>

<span data-ttu-id="7020e-413">Ta usługa instaluje wywołania zwrotne aplikacji w celu zaimplementowania operacji na zasobach obiektów zabezpieczeń LWM2M związanych z kluczami zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7020e-413">This service installs the application callbacks for implementing operations on the LWM2M Security Object resources related to the security keys.</span></span>

<span data-ttu-id="7020e-414">Klient LWM2M deleguje zarządzanie kluczami zabezpieczeń do aplikacji podczas sesji Bootstrap, wywołania zwrotne będą wywoływane, gdy serwer Bootstrap zapisze lub usunie następujące zasoby w wystąpieniu obiektu zabezpieczeń: klucz publiczny lub tożsamość (3), klucz publiczny serwera (4), klucz tajny (5).</span><span class="sxs-lookup"><span data-stu-id="7020e-414">The LWM2M Client delegates the security key management to the application during the Bootstrap sessions, the callbacks will be called when the Bootstrap Server writes or deletes the following resources on a Security Object Instance: Public Key or Identity (3), Server Public Key (4), Secret Key (5).</span></span>

<span data-ttu-id="7020e-415">Aplikacja jest odpowiedzialna za przechowywanie danych kluczy i na potrzeby konfigurowania sesji DTLS używanych przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-415">The application is responsible for storing the keys data and for configuring the DTLS sessions used by the LWM2M client.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-416">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-416">Parameters</span></span>

- <span data-ttu-id="7020e-417">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-417">**client_ptr**: Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="7020e-418">**write_callback**: wywołanie zwrotne metody klucza "Write".</span><span class="sxs-lookup"><span data-stu-id="7020e-418">**write_callback**: The 'Write' key method callback.</span></span>
- <span data-ttu-id="7020e-419">**delete_callback**: wywołanie zwrotne metody klucza "Delete".</span><span class="sxs-lookup"><span data-stu-id="7020e-419">**delete_callback**: The 'Delete' key method callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-420">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-420">Return Values</span></span>

- <span data-ttu-id="7020e-421">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-421">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-422">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-422">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="7020e-423">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="7020e-423">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="7020e-424">Uruchamianie sesji z serwerem Bootstrap</span><span class="sxs-lookup"><span data-stu-id="7020e-424">Start a session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-425">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-425">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(NX_LWM2M_CLIENT_SESSION
    *session_ptr, NX_LWM2M_ID security_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="7020e-426">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-426">Description</span></span>

<span data-ttu-id="7020e-427">Ta usługa uruchamia sesję z serwerem Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="7020e-427">This service start a session with a Bootstrap Server.</span></span> <span data-ttu-id="7020e-428">Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7020e-428">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="7020e-429">Jeśli zasób "Hold off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na zainicjowanie przez serwer ładowania początkowego, jeśli po tym okresie ten serwer nie zainicjuje ładowania uruchomienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-429">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="7020e-430">Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="7020e-430">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-431">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-431">Parameters</span></span>

- <span data-ttu-id="7020e-432">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-432">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7020e-433">**security_id**: identyfikator wystąpienia zabezpieczeń serwera Bootstrap musi być ustawiony na NX_LWM2M_RESERVED_ID (65535), jeśli serwer Bootstrap nie ma zdefiniowanego wystąpienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7020e-433">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="7020e-434">**IP_address**: adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-434">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="7020e-435">**port**: port UDP serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-435">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-436">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-436">Return Values</span></span>

- <span data-ttu-id="7020e-437">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-437">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-438">**NX_LWM2M_NOT_FOUND**: nie ma wystąpienia obiektu zabezpieczeń ODPOWIADAJĄCego identyfikatorowi wystąpienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7020e-438">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="7020e-439">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-439">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="7020e-440">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="7020e-440">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="7020e-441">Uruchom bezpieczną sesję z serwerem Bootstrap</span><span class="sxs-lookup"><span data-stu-id="7020e-441">Start a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-442">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-442">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID security_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="7020e-443">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-443">Description</span></span>

<span data-ttu-id="7020e-444">Ta usługa uruchamia sesję z serwerem Bootstrap przy użyciu bezpiecznego połączenia DTLS.</span><span class="sxs-lookup"><span data-stu-id="7020e-444">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="7020e-445">Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7020e-445">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="7020e-446">Przed wywołaniem tej funkcji sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza.</span><span class="sxs-lookup"><span data-stu-id="7020e-446">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="7020e-447">Należy zdefiniować NX_SECURE_ENABLE_DTLS.</span><span class="sxs-lookup"><span data-stu-id="7020e-447">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="7020e-448">Jeśli zasób "Hold off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na zainicjowanie przez serwer ładowania początkowego, jeśli po tym okresie ten serwer nie zainicjuje ładowania uruchomienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-448">If the 'Hold Off' resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="7020e-449">Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="7020e-449">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-450">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-450">Parameters</span></span>

- <span data-ttu-id="7020e-451">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-451">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7020e-452">**security_id**: identyfikator wystąpienia zabezpieczeń serwera Bootstrap musi być ustawiony na NX_LWM2M_RESERVED_ID (65535), jeśli serwer Bootstrap nie ma zdefiniowanego wystąpienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7020e-452">**security_id**: The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="7020e-453">**IP_address**: adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-453">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="7020e-454">**port**: port UDP serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-454">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="7020e-455">**dtls_session_ptr**: sesja DTLS do użycia w sesji Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="7020e-455">**dtls_session_ptr**: The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="7020e-456">**dtls_local_port**: lokalny port UDP używany do sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="7020e-456">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-457">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-457">Return Values</span></span>

- <span data-ttu-id="7020e-458">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-458">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-459">**NX_LWM2M_NOT_FOUND**: nie ma wystąpienia obiektu zabezpieczeń ODPOWIADAJĄCego identyfikatorowi wystąpienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7020e-459">**NX_LWM2M_NOT_FOUND**: There is No Security Object instance corresponding to the Security Instance ID.</span></span>
- <span data-ttu-id="7020e-460">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-460">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="7020e-461">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="7020e-461">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="7020e-462">Utwórz sesję klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-462">Create LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-463">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-463">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(NX_LWM2M_CLIENT_SESSION *session_ptr,
         NX_LWM2M_CLIENT *client_ptr,
         NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="7020e-464">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-464">Description</span></span>

<span data-ttu-id="7020e-465">Ta usługa tworzy nową sesję klienta LWM2M dołączoną do istniejącego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-465">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="7020e-466">Sesja jest używana przez klienta LWM2M do komunikacji z serwerem Bootstrap lub serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-466">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span>

<span data-ttu-id="7020e-467">Aplikacja musi udostępniać funkcję wywołania zwrotnego, która będzie wywoływana, gdy stan sesji zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="7020e-467">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-468">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-468">Parameters</span></span>

- <span data-ttu-id="7020e-469">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-469">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7020e-470">**client_ptr**: wskaźnik do wcześniej utworzonego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-470">**client_ptr**: Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="7020e-471">**state_callback**: wywołanie zwrotne aplikacji wywoływane w przypadku zmiany stanu sesji.</span><span class="sxs-lookup"><span data-stu-id="7020e-471">**state_callback**: Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-472">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-472">Return Values</span></span>

- <span data-ttu-id="7020e-473">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-473">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-474">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-474">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="7020e-475">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="7020e-475">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="7020e-476">Usuń sesję klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-476">Delete LWM2M Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-477">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-477">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-478">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-478">Description</span></span>

<span data-ttu-id="7020e-479">Ta usługa usuwa sesję klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-479">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="7020e-480">Po usunięciu klienta LWM2M przez wywołanie nx_lwm2m_client_delete wszystkie sesje dołączone do klienta również zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="7020e-480">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-481">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-481">Parameters</span></span>

- <span data-ttu-id="7020e-482">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-482">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-483">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-483">Return Values</span></span>

- <span data-ttu-id="7020e-484">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-484">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-485">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-485">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="7020e-486">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="7020e-486">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="7020e-487">Przerywanie sesji z serwerem LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-487">Terminate a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-488">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-489">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-489">Description</span></span>

<span data-ttu-id="7020e-490">Ta usługa wykonuje operację "Wyrejestrowanie" na serwerze LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-490">This service performs a 'De-Register' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-491">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-491">Parameters</span></span>

- <span data-ttu-id="7020e-492">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-492">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-493">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-493">Return Values</span></span>

- <span data-ttu-id="7020e-494">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-494">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-495">**NX_LWM2M_NOT_REGISTERED**: klient nie jest zarejestrowany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7020e-495">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="7020e-496">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-496">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="7020e-497">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="7020e-497">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="7020e-498">Pobierz ostatni błąd sesji</span><span class="sxs-lookup"><span data-stu-id="7020e-498">Get last error of a session</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-499">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-499">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-500">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-500">Description</span></span>

<span data-ttu-id="7020e-501">Ta usługa zwraca kod błędu sesji, gdy sesja jest w stanie błędu.</span><span class="sxs-lookup"><span data-stu-id="7020e-501">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-502">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-502">Parameters</span></span>

- <span data-ttu-id="7020e-503">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-503">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-504">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-504">Return Values</span></span>

- <span data-ttu-id="7020e-505">**NX_SUCCESS**: sesja nie jest w stanie błędu.</span><span class="sxs-lookup"><span data-stu-id="7020e-505">**NX_SUCCESS**: The session is not in error state.</span></span>
- <span data-ttu-id="7020e-506">**NX_LWM2M_ADDRESS_ERROR**: nieprawidłowy adres serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-506">**NX_LWM2M_ADDRESS_ERROR**: Invalid server address.</span></span>
- <span data-ttu-id="7020e-507">**NX_LWM2M_BUFFER_TOO_SMALL**: ładunek żądania nie mieści się w buforze sieciowym.</span><span class="sxs-lookup"><span data-stu-id="7020e-507">**NX_LWM2M_BUFFER_TOO_SMALL**: Payload of request doesn't fit in network buffer.</span></span>
- <span data-ttu-id="7020e-508">**NX_LWM2M_DTLS_ERROR**: nie można ustanowić bezpiecznego połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="7020e-508">**NX_LWM2M_DTLS_ERROR**: Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="7020e-509">**NX_LWM2M_ERROR**: nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="7020e-509">**NX_LWM2M_ERROR**: Unspecified error.</span></span>
- <span data-ttu-id="7020e-510">**NX_LWM2M_FORBIDDEN**: Rejestracja została odrzucona przez serwer.</span><span class="sxs-lookup"><span data-stu-id="7020e-510">**NX_LWM2M_FORBIDDEN**: Registration refused by server.</span></span>
- <span data-ttu-id="7020e-511">**NX_LWM2M_NOT_FOUND**: nie znaleziono klienta przez serwer podczas aktualizowania/wyrejestrowywania.</span><span class="sxs-lookup"><span data-stu-id="7020e-511">**NX_LWM2M_NOT_FOUND**: Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="7020e-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: wystąpienie obiektu serwera odpowiadające sesji zostało usunięte.</span><span class="sxs-lookup"><span data-stu-id="7020e-512">**NX_LWM2M_SERVER_INSTANCE_DELETED**: The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="7020e-513">**NX_LWM2M_TIMED_OUT**: Brak odpowiedzi z serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-513">**NX_LWM2M_TIMED_OUT**: No answer from server.</span></span>
- <span data-ttu-id="7020e-514">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-514">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="7020e-515">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="7020e-515">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="7020e-516">Uruchamianie sesji z serwerem LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-516">Start a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-517">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-517">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(NX_LWM2M_CLIENT_SESSION *session_ptr,
                    NX_LWM2M_ID server_id, ULONG ip_address, UINT port);
```

### <a name="description"></a><span data-ttu-id="7020e-518">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-518">Description</span></span>

<span data-ttu-id="7020e-519">Ta usługa wykonuje operację "Register" na serwerze LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-519">This service performs a 'Register' operation to a LWM2M Server.</span></span> <span data-ttu-id="7020e-520">Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwer.</span><span class="sxs-lookup"><span data-stu-id="7020e-520">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="7020e-521">Jeśli rejestracja zakończyła się pomyślnie, klient programu LWM2M będzie przetwarzać dalsze operacje z serwera i okresowo wysyła komunikat "Update", dopóki klient nie zostanie wyrejestrowany.</span><span class="sxs-lookup"><span data-stu-id="7020e-521">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="7020e-522">Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-522">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-523">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-523">Parameters</span></span>

- <span data-ttu-id="7020e-524">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-524">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7020e-525">**server_id**: Krótki identyfikator serwera serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-525">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="7020e-526">**IP_address**: adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-526">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="7020e-527">**port**: port UDP serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-527">**port**: The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-528">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-528">Return Values</span></span>

- <span data-ttu-id="7020e-529">**NX_SUCCESS**: operacja powiodła się..</span><span class="sxs-lookup"><span data-stu-id="7020e-529">**NX_SUCCESS**: Successful operation..</span></span>
- <span data-ttu-id="7020e-530">**NX_LWM2M_NOT_FOUND**: nie istnieje wystąpienie obiektu serwera odpowiadające KRÓTKIemu identyfikatorowi serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-530">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="7020e-531">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-531">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="7020e-532">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="7020e-532">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="7020e-533">Uruchamianie bezpiecznej sesji z serwerem LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-533">Start a secure session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-534">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-534">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(NX_LWM2M_CLIENT_SESSION *session_ptr,
    NX_LWM2M_ID server_id, ULONG ip_address, UINT port, NX_SECURE_DTLS_SESSION
    *dtls_session_ptr, UINT dtls_local_port);
```

### <a name="description"></a><span data-ttu-id="7020e-535">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-535">Description</span></span>

<span data-ttu-id="7020e-536">Ta usługa wykonuje operację "Register" na serwerze LWM2M przy użyciu bezpiecznego połączenia usługi DTLS.</span><span class="sxs-lookup"><span data-stu-id="7020e-536">This service performs a 'Register' operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="7020e-537">Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwer.</span><span class="sxs-lookup"><span data-stu-id="7020e-537">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="7020e-538">Przed wywołaniem tej funkcji sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza.</span><span class="sxs-lookup"><span data-stu-id="7020e-538">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="7020e-539">Należy zdefiniować NX_SECURE_ENABLE_DTLS.</span><span class="sxs-lookup"><span data-stu-id="7020e-539">NX_SECURE_ENABLE_DTLS must be defined.</span></span>

<span data-ttu-id="7020e-540">Każda sesja DTLS używa własnego gniazda UDP do komunikacji, dlatego dtls_local_port portów lokalnych musi być inna dla każdej sesji, jeśli aplikacja tworzy kilka bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="7020e-540">Each DTLS session uses its own UDP socket for communication, so the local port dtls_local_port must be different for each session if the application creates several secure sessions.</span></span>

<span data-ttu-id="7020e-541">Jeśli rejestracja zakończyła się pomyślnie, klient programu LWM2M będzie przetwarzać dalsze operacje z serwera i okresowo wysyła komunikat "Update", dopóki klient nie zostanie wyrejestrowany.</span><span class="sxs-lookup"><span data-stu-id="7020e-541">If the registration is successful the LWM2M Client will process further operations from the server and will periodically send 'Update' messages until the client is de-registered.</span></span>

<span data-ttu-id="7020e-542">Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-542">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-543">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-543">Parameters</span></span>

- <span data-ttu-id="7020e-544">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-544">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="7020e-545">**server_id**: Krótki identyfikator serwera serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-545">**server_id**: The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="7020e-546">**IP_address**: adres IP serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-546">**ip_address**: The IP address of the server.</span></span>
- <span data-ttu-id="7020e-547">**port**: port UDP serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-547">**port**: The UDP port of the server.</span></span>
- <span data-ttu-id="7020e-548">**dtls_session_ptr**: sesja DTLS używana na potrzeby sesji LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-548">**dtls_session_ptr**: The DTLS session to use for the LWM2M session.</span></span>
- <span data-ttu-id="7020e-549">**dtls_local_port**: lokalny port UDP używany do sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="7020e-549">**dtls_local_port**: The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-550">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-550">Return Values</span></span>

- <span data-ttu-id="7020e-551">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-551">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-552">**NX_LWM2M_NOT_FOUND**: nie istnieje wystąpienie obiektu serwera odpowiadające KRÓTKIemu identyfikatorowi serwera.</span><span class="sxs-lookup"><span data-stu-id="7020e-552">**NX_LWM2M_NOT_FOUND**: There is No Server Object instance corresponding to the Short Server ID.</span></span>
- <span data-ttu-id="7020e-553">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-553">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="7020e-554">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="7020e-554">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="7020e-555">Aktualizowanie sesji przy użyciu serwera LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-555">Update a session with a LWM2M Server</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-556">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-557">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-557">Description</span></span>

<span data-ttu-id="7020e-558">Ta usługa wykonuje operację "Update" na serwerze LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-558">This service performs an 'Update' operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-559">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-559">Parameters</span></span>

- <span data-ttu-id="7020e-560">**session_ptr**: wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-560">**session_ptr**: Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-561">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-561">Return Values</span></span>

- <span data-ttu-id="7020e-562">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-562">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-563">**NX_LWM2M_NOT_REGISTERED**: klient nie jest zarejestrowany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7020e-563">**NX_LWM2M_NOT_REGISTERED**: The client is not registered to the server.</span></span>
- <span data-ttu-id="7020e-564">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-564">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="7020e-565">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="7020e-565">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="7020e-566">Odblokuj klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="7020e-566">Unlock LWM2M Client</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-567">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-567">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-568">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-568">Description</span></span>

<span data-ttu-id="7020e-569">Ta usługa odblokowuje klienta LWM2M previoulsy zablokowany przez wywołanie do nx_lwm2m_client_unlock ().</span><span class="sxs-lookup"><span data-stu-id="7020e-569">This service unlocks the LWM2M Client previoulsy locked by a call to nx_lwm2m_client_unlock().</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-570">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-570">Parameters</span></span>

- <span data-ttu-id="7020e-571">**client_ptr**: wskaźnik do LWM2M bloku kontroli klienta.</span><span class="sxs-lookup"><span data-stu-id="7020e-571">**client_ptr**: Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-572">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-572">Return Values</span></span>

- <span data-ttu-id="7020e-573">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-573">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-574">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-574">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_create"></a><span data-ttu-id="7020e-575">nx_lwm2m_firmware_create</span><span class="sxs-lookup"><span data-stu-id="7020e-575">nx_lwm2m_firmware_create</span></span>

<span data-ttu-id="7020e-576">Utwórz obiekt aktualizacji oprogramowania układowego</span><span class="sxs-lookup"><span data-stu-id="7020e-576">Create Firmware Update Object</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-577">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-577">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_create(NX_LWM2M_FIRMWARE *firmware_ptr,
    NX_LWM2M_CLIENT *client_ptr, UINT protocols,
    NX_LWM2M_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_FIRMWARE_UPDATE_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="7020e-578">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-578">Description</span></span>

<span data-ttu-id="7020e-579">Ta usługa inicjuje obiekt aktualizacji oprogramowania układowego i dodaje obiekt do wcześniej utworzonego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-579">This service initializes a Firmware Update Object and adds the Object to a previously created LWM2M Client.</span></span> <span data-ttu-id="7020e-580">Obiekt aktualizacji oprogramowania układowego implementuje zasoby do komunikacji z serwerem LWM2M, ale aplikacja musi zapewnić wywołania zwrotne w celu zaimplementowania rzeczywistych operacji na oprogramowaniu układowym (dowloading, przechowywanie i aktualizowanie oprogramowania układowego).</span><span class="sxs-lookup"><span data-stu-id="7020e-580">The Firmware Update Object implements the resources for communicating with a LWM2M Server but the application must provide callbacks for implementing the actual operations on the firmware (dowloading, storing, and updating the firmware).</span></span>

<span data-ttu-id="7020e-581">Parametr Protocols wskazuje, które protokoły są obsługiwane przez aplikację do pobierania oprogramowania układowego z zasobem "identyfikator URI pakietu" zdefiniowane są następujące flagi:</span><span class="sxs-lookup"><span data-stu-id="7020e-581">The protocols parameter indicates which protocols are supported by the application for retrieving the firmware with the 'Package URI' resource, the following flags are defined:</span></span>

<span data-ttu-id="7020e-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span><span class="sxs-lookup"><span data-stu-id="7020e-582">NX_LWM2M_FIRMWARE_PROTOCOL_COAP, NX_LWM2M_FIRMWARE_PROTOCOL_COAPS, NX_LWM2M_FIRMWARE_PROTOCOL_HTTP, NX_LWM2M_FIRMWARE_PROTOCOL_HTPPS.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-583">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-583">Parameters</span></span>

- <span data-ttu-id="7020e-584">**firmware_ptr**: wskaźnik do bloku kontroli obiektów oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-584">**firmware_ptr**: Pointer to the Firmware Object control block.</span></span>
- <span data-ttu-id="7020e-585">**client_ptr**: wskaźnik do Previsously utworzonego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-585">**client_ptr**: Pointer to previsously created LWM2M Client.</span></span>
- <span data-ttu-id="7020e-586">**Protokoły**: flagi wskazujące, które protokoły są obsługiwane przez zasób URI pakietu.</span><span class="sxs-lookup"><span data-stu-id="7020e-586">**protocols**: Flags indicating which protocols are supported by the Package URI resource.</span></span>
- <span data-ttu-id="7020e-587">**package_callback**: musi mieć wartość null [TBD].</span><span class="sxs-lookup"><span data-stu-id="7020e-587">**package_callback**: Must be NULL [TBD].</span></span>
- <span data-ttu-id="7020e-588">**package_uri_callback**: wywołanie zwrotne używane do implementowania zasobu URI pakietu.</span><span class="sxs-lookup"><span data-stu-id="7020e-588">**package_uri_callback**: Callback used to implement the Package URI resource.</span></span>
- <span data-ttu-id="7020e-589">**update_callback**: wywołanie zwrotne używane do implementowania zasobu aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="7020e-589">**update_callback**: Callback used to implement the Update resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-590">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-590">Return Values</span></span>

- <span data-ttu-id="7020e-591">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-591">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-592">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-592">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_package_info_set"></a><span data-ttu-id="7020e-593">nx_lwm2m_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="7020e-593">nx_lwm2m_firmware_package_info_set</span></span>

<span data-ttu-id="7020e-594">Ustawianie informacji o pakiecie aktualizacji oprogramowania układowego</span><span class="sxs-lookup"><span data-stu-id="7020e-594">Set Firmware Update Package Information</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-595">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-595">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_package_info_set(NX_LWM2M_FIRMWARE *firmware_ptr,
                                const CHAR *name, const CHAR *version);
```

### <a name="description"></a><span data-ttu-id="7020e-596">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-596">Description</span></span>

<span data-ttu-id="7020e-597">Ta usługa zmienia wartości "PkgName" (6) i "PkgVersion" (7) zasobów obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-597">This service changes the values of the 'PkgName' (6) and 'PkgVersion' (7) resources of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-598">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-598">Parameters</span></span>

- <span data-ttu-id="7020e-599">**firmware_ptr**: wskaźnik do obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-599">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="7020e-600">**Nazwa**: Nowa wartość nazwy pakietu.</span><span class="sxs-lookup"><span data-stu-id="7020e-600">**name**: The new value of the Package Name.</span></span>
- <span data-ttu-id="7020e-601">**wersja**: Nowa wartość wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="7020e-601">**version**: The new value of the Package Version.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-602">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-602">Return Values</span></span>

- <span data-ttu-id="7020e-603">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-603">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-604">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-604">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_result_set"></a><span data-ttu-id="7020e-605">nx_lwm2m_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="7020e-605">nx_lwm2m_firmware_result_set</span></span>

<span data-ttu-id="7020e-606">Ustaw wynik aktualizacji oprogramowania układowego</span><span class="sxs-lookup"><span data-stu-id="7020e-606">Set Firmware Update Result</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-607">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-607">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_result_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR result);
```

### <a name="description"></a><span data-ttu-id="7020e-608">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-608">Description</span></span>

<span data-ttu-id="7020e-609">Ta usługa zmienia wartość zasobu "Update Result" (5) dla obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-609">This service changes the value of the 'Update Result' (5) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-610">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-610">Parameters</span></span>

- <span data-ttu-id="7020e-611">**firmware_ptr**: wskaźnik do obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-611">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="7020e-612">**wynik**: Nowa wartość zasobu wynik aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="7020e-612">**result**: The new value of the Update Result resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-613">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-613">Return Values</span></span>

- <span data-ttu-id="7020e-614">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-614">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-615">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-615">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_firmware_state_set"></a><span data-ttu-id="7020e-616">nx_lwm2m_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="7020e-616">nx_lwm2m_firmware_state_set</span></span>

<span data-ttu-id="7020e-617">Ustaw stan aktualizacji oprogramowania układowego</span><span class="sxs-lookup"><span data-stu-id="7020e-617">Set Firmware Update State</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-618">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-618">Prototype</span></span>

```c
UINT nx_lwm2m_firmware_state_set(NX_LWM2M_FIRMWARE *firmware_ptr, UCHAR state);
```

### <a name="description"></a><span data-ttu-id="7020e-619">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-619">Description</span></span>

<span data-ttu-id="7020e-620">Ta usługa zmienia wartość zasobu "State" (3) obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-620">This service changes the value of the 'State' (3) resource of the Firmware Update Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-621">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-621">Parameters</span></span>

- <span data-ttu-id="7020e-622">**firmware_ptr**: wskaźnik do obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-622">**firmware_ptr**: Pointer to the Firmware Update Object.</span></span>
- <span data-ttu-id="7020e-623">**stan**: Nowa wartość zasobu stanu.</span><span class="sxs-lookup"><span data-stu-id="7020e-623">**state**: The new value of the State resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-624">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-624">Return Values</span></span>

- <span data-ttu-id="7020e-625">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-625">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-626">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-626">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_object_resource_changed"></a><span data-ttu-id="7020e-627">nx_lwm2m_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="7020e-627">nx_lwm2m_object_resource_changed</span></span>

<span data-ttu-id="7020e-628">Zmiana sygnału dla wartości zasobu wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-628">Signal change of a resource value of an Object Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-629">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-629">Prototype</span></span>

```c
UINT nx_lwm2m_object_resource_changed(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="7020e-630">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-630">Description</span></span>

<span data-ttu-id="7020e-631">Ta usługa jest używana przez implementację obiektu do sygnalizowania klienta LWM2M, że jedna z jego wartości zasobów została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="7020e-631">This service is used by an Object implementation to signals the LWM2M Client that one of its resource value has changed.</span></span> <span data-ttu-id="7020e-632">Klient LWM2M wyśle powiadomienie, jeśli zasób jest zaobserwowany przez serwer LWM2M.</span><span class="sxs-lookup"><span data-stu-id="7020e-632">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-633">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-633">Parameters</span></span>

- <span data-ttu-id="7020e-634">**object_ptr**: wskaźnik do implementacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-634">**object_ptr**: Pointer to the Object implementation.</span></span>
- <span data-ttu-id="7020e-635">**instance_ptr**: wskaźnik do wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-635">**instance_ptr**: Pointer to the Object Instance.</span></span>
- <span data-ttu-id="7020e-636">**zasób**: wskaźnik do struktury opisującej zasób, który został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="7020e-636">**resource**: Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-637">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-637">Return Values</span></span>

- <span data-ttu-id="7020e-638">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-638">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-639">NX_PTR_ERROR: nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="7020e-639">NX_PTR_ERROR: Invalid pointer.</span></span>

## <a name="nx_lwm2m_resource_get_boolean"></a><span data-ttu-id="7020e-640">nx_lwm2m_resource_get_boolean</span><span class="sxs-lookup"><span data-stu-id="7020e-640">nx_lwm2m_resource_get_boolean</span></span>

<span data-ttu-id="7020e-641">Pobieranie wartości zasobu logicznego</span><span class="sxs-lookup"><span data-stu-id="7020e-641">Get the value of a Boolean Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-642">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-642">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_boolean(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-643">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-643">Description</span></span>

<span data-ttu-id="7020e-644">Usługa Pobiera wartość zasobu logicznego.</span><span class="sxs-lookup"><span data-stu-id="7020e-644">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-645">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-645">Parameters</span></span>

- <span data-ttu-id="7020e-646">**wartość**: wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-646">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="7020e-647">**bool_ptr**: wskaźnik do docelowej wartości logicznej.</span><span class="sxs-lookup"><span data-stu-id="7020e-647">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-648">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-648">Return Values</span></span>

- <span data-ttu-id="7020e-649">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-649">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-650">**NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością logiczną.</span><span class="sxs-lookup"><span data-stu-id="7020e-650">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_get_float32"></a><span data-ttu-id="7020e-651">nx_lwm2m_resource_get_float32</span><span class="sxs-lookup"><span data-stu-id="7020e-651">nx_lwm2m_resource_get_float32</span></span>

<span data-ttu-id="7020e-652">Pobierz wartość 32-bitowego zasobu zmiennoprzecinkowego</span><span class="sxs-lookup"><span data-stu-id="7020e-652">Get the value of a 32-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-653">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-653">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float32(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-654">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-654">Description</span></span>

<span data-ttu-id="7020e-655">Usługa Pobiera wartość 32-bitowego zasobu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-655">The service retrieves the value of a 32-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-656">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-656">Parameters</span></span>

- <span data-ttu-id="7020e-657">**wartość**: wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-657">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="7020e-658">**float32_ptr**: wskaźnik do docelowej 32-bitowej wartości zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="7020e-658">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-659">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-659">Return Values</span></span>

- <span data-ttu-id="7020e-660">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-660">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-661">**NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="7020e-661">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_float64"></a><span data-ttu-id="7020e-662">nx_lwm2m_resource_get_float64</span><span class="sxs-lookup"><span data-stu-id="7020e-662">nx_lwm2m_resource_get_float64</span></span>

<span data-ttu-id="7020e-663">Pobierz wartość 64-bitowego zasobu zmiennoprzecinkowego</span><span class="sxs-lookup"><span data-stu-id="7020e-663">Get the value of a 64-bit Floating Point Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-664">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-664">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_float64(const NX_LWM2M_RESOURCE *value,
                                NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-665">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-665">Description</span></span>

<span data-ttu-id="7020e-666">Usługa Pobiera wartość 64-bitowego zasobu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-666">The service retrieves the value of a 64-bit Floating Point Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-667">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-667">Parameters</span></span>

- <span data-ttu-id="7020e-668">**wartość**: wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-668">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="7020e-669">**float64_ptr**: wskaźnik do docelowej 64-bitowej wartości zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="7020e-669">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-670">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-670">Return Values</span></span>

- <span data-ttu-id="7020e-671">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-671">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-672">**NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="7020e-672">**NX_LWM2M_BAD_ENCODING**: The resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_get_integer32"></a><span data-ttu-id="7020e-673">nx_lwm2m_resource_get_integer32</span><span class="sxs-lookup"><span data-stu-id="7020e-673">nx_lwm2m_resource_get_integer32</span></span>

<span data-ttu-id="7020e-674">Pobierz wartość 32-bitowego zasobu liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="7020e-674">Get the value of a 32-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-675">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-675">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer32(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-676">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-676">Description</span></span>

<span data-ttu-id="7020e-677">Usługa Pobiera wartość 32-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7020e-677">The service retrieves the value of a 32-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-678">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-678">Parameters</span></span>

- <span data-ttu-id="7020e-679">**wartość**: wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-679">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="7020e-680">**int32_ptr**: wskaźnik do wartości docelowej 32-bitowej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7020e-680">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-681">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-681">Return Values</span></span>

- <span data-ttu-id="7020e-682">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-682">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-683">**NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością całkowitą lub wartość całkowita nie mieści się w 32-bitowej liczbie.</span><span class="sxs-lookup"><span data-stu-id="7020e-683">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_get_integer64"></a><span data-ttu-id="7020e-684">nx_lwm2m_resource_get_integer64</span><span class="sxs-lookup"><span data-stu-id="7020e-684">nx_lwm2m_resource_get_integer64</span></span>

<span data-ttu-id="7020e-685">Pobierz wartość 64-bitowego zasobu liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="7020e-685">Get the value of a 64-Bit Integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-686">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-686">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_integer64(const NX_LWM2M_RESOURCE *value,
                                        NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-687">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-687">Description</span></span>

<span data-ttu-id="7020e-688">Usługa Pobiera wartość 64-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7020e-688">The service retrieves the value of a 64-Bit Integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-689">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-689">Parameters</span></span>

- <span data-ttu-id="7020e-690">**wartość**: wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-690">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="7020e-691">**int64_ptr**: wskaźnik do wartości docelowej 64-bitowej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7020e-691">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-692">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-692">Return Values</span></span>

- <span data-ttu-id="7020e-693">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-693">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-694">**NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością całkowitą.</span><span class="sxs-lookup"><span data-stu-id="7020e-694">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_get_objlnk"></a><span data-ttu-id="7020e-695">nx_lwm2m_resource_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="7020e-695">nx_lwm2m_resource_get_objlnk</span></span>

<span data-ttu-id="7020e-696">Pobieranie wartości zasobu linku do obiektu</span><span class="sxs-lookup"><span data-stu-id="7020e-696">Get the value of an Object Link Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-697">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-697">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_objlnk(const NX_LWM2M_RESOURCE *value,
                                    NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-698">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-698">Description</span></span>

<span data-ttu-id="7020e-699">Usługa Pobiera wartość zasobu linku do obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-699">The service retrieves the value of an Object Link Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-700">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-700">Parameters</span></span>

- <span data-ttu-id="7020e-701">**wartość**: wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-701">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="7020e-702">**objlnk_ptr**: wskaźnik do wartości linku do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-702">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-703">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-703">Return Values</span></span>

- <span data-ttu-id="7020e-704">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-704">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-705">**NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością linku obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-705">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_get_opaque"></a><span data-ttu-id="7020e-706">nx_lwm2m_resource_get_opaque</span><span class="sxs-lookup"><span data-stu-id="7020e-706">nx_lwm2m_resource_get_opaque</span></span>

<span data-ttu-id="7020e-707">Pobierz wartość nieprzezroczystego zasobu</span><span class="sxs-lookup"><span data-stu-id="7020e-707">Get the value of an Opaque Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-708">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-708">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_opaque(const NX_LWM2M_RESOURCE *value,
            const VOID **opaque_ptr_ptr, UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-709">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-709">Description</span></span>

<span data-ttu-id="7020e-710">Usługa Pobiera wartość nieprzezroczystego zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-710">The service retrieves the value of an Opaque Resource.</span></span>

<span data-ttu-id="7020e-711">Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.</span><span class="sxs-lookup"><span data-stu-id="7020e-711">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-712">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-712">Parameters</span></span>

- <span data-ttu-id="7020e-713">**wartość**: wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-713">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="7020e-714">**opaque_ptr_ptr**: wskaźnik do docelowego wskaźnika bufora nieprzezroczystości.</span><span class="sxs-lookup"><span data-stu-id="7020e-714">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="7020e-715">**opaque_length_ptr**: wskaźnik do docelowej długości buforu nieprzezroczystości.</span><span class="sxs-lookup"><span data-stu-id="7020e-715">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-716">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-716">Return Values</span></span>

- <span data-ttu-id="7020e-717">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-717">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-718">**NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością nieprzezroczystą.</span><span class="sxs-lookup"><span data-stu-id="7020e-718">**NX_LWM2M_BAD_ENCODING**: The resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_get_string"></a><span data-ttu-id="7020e-719">nx_lwm2m_resource_get_string</span><span class="sxs-lookup"><span data-stu-id="7020e-719">nx_lwm2m_resource_get_string</span></span>

<span data-ttu-id="7020e-720">Pobierz wartość zasobu ciągu</span><span class="sxs-lookup"><span data-stu-id="7020e-720">Get the value of a String Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-721">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-721">Prototype</span></span>

```c
UINT nx_lwm2m_resource_get_string(const NX_LWM2M_RESOURCE *value,
            const CHAR **string_ptr_ptr, UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-722">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-722">Description</span></span>

<span data-ttu-id="7020e-723">Usługa Pobiera wartość zasobu ciągu.</span><span class="sxs-lookup"><span data-stu-id="7020e-723">The service retrieves the value of a String Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-724">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-724">Parameters</span></span>

- <span data-ttu-id="7020e-725">**wartość**: wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-725">**value**: Pointer to Resource value description.</span></span>
- <span data-ttu-id="7020e-726">**string_ptr_ptr**: wskaźnik do wskaźnika ciągu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-726">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="7020e-727">**string_length_ptr**: wskaźnik do docelowej długości ciągu.</span><span class="sxs-lookup"><span data-stu-id="7020e-727">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="7020e-728">Może mieć wartość NULL, jeśli ciąg jest zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="7020e-728">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-729">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-729">Return Values</span></span>

- <span data-ttu-id="7020e-730">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-730">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-731">**NX_LWM2M_BAD_ENCODING**: wartość zasobu nie jest wartością ciągu.</span><span class="sxs-lookup"><span data-stu-id="7020e-731">**NX_LWM2M_BAD_ENCODING**: The resource value is not a String value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_boolean"></a><span data-ttu-id="7020e-732">nx_lwm2m_resource_multiple_get_boolean</span><span class="sxs-lookup"><span data-stu-id="7020e-732">nx_lwm2m_resource_multiple_get_boolean</span></span>

<span data-ttu-id="7020e-733">Pobierz wartość zasobu logicznego z wieloma wystąpieniami zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-733">Get the value of a Boolean Resource Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-734">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-734">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_boolean(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-735">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-735">Description</span></span>

<span data-ttu-id="7020e-736">Usługa Pobiera wartość wystąpienia zasobu logicznego z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-736">The service retrieves the value of a Boolean Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-737">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-737">Parameters</span></span>

- <span data-ttu-id="7020e-738">**wartość**: wskaźnik do opisu wartości wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-738">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="7020e-739">**index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-739">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="7020e-740">**instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-740">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="7020e-741">**bool_ptr**: wskaźnik do docelowej wartości logicznej.</span><span class="sxs-lookup"><span data-stu-id="7020e-741">**bool_ptr**: Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-742">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-742">Return Values</span></span>

- <span data-ttu-id="7020e-743">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-743">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-744">**NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7020e-744">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="7020e-745">**NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem lub nie jest wartością logiczną.</span><span class="sxs-lookup"><span data-stu-id="7020e-745">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Boolean value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float32"></a><span data-ttu-id="7020e-746">nx_lwm2m_resource_multiple_get_float32</span><span class="sxs-lookup"><span data-stu-id="7020e-746">nx_lwm2m_resource_multiple_get_float32</span></span>

<span data-ttu-id="7020e-747">Pobierz wartość 32-bitowego wystąpienia wielu zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-747">Get the value of a 32-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-748">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-748">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float32(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-749">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-749">Description</span></span>

<span data-ttu-id="7020e-750">Usługa Pobiera wartość 32-bitowego wystąpienia zasobu zmiennoprzecinkowego z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-750">The service retrieves the value of a 32-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-751">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-751">Parameters</span></span>

- <span data-ttu-id="7020e-752">**wartość**: wskaźnik do opisu wartości wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-752">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="7020e-753">**index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-753">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="7020e-754">**instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-754">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="7020e-755">**float32_ptr**: wskaźnik do docelowej 32-bitowej wartości zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="7020e-755">**float32_ptr**: Pointer to the destination 32-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-756">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-756">Return Values</span></span>

- <span data-ttu-id="7020e-757">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-757">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-758">**NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7020e-758">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="7020e-759">**NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem lub nie jest wartością zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="7020e-759">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_float64"></a><span data-ttu-id="7020e-760">nx_lwm2m_resource_multiple_get_float64</span><span class="sxs-lookup"><span data-stu-id="7020e-760">nx_lwm2m_resource_multiple_get_float64</span></span>

<span data-ttu-id="7020e-761">Pobierz wartość 64-bitowego wystąpienia wielu zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-761">Get the value of a 64-bit Floating Point Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-762">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-762">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_float64(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-763">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-763">Description</span></span>

<span data-ttu-id="7020e-764">Usługa Pobiera wartość 64-bitowego wystąpienia zasobu zmiennoprzecinkowego z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-764">The service retrieves the value of a 64-bit Floating Point Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-765">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-765">Parameters</span></span>

- <span data-ttu-id="7020e-766">**wartość**: wskaźnik do opisu wartości wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-766">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="7020e-767">**index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-767">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="7020e-768">**instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-768">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="7020e-769">**float64_ptr**: wskaźnik do docelowej 64-bitowej wartości zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="7020e-769">**float64_ptr**: Pointer to the destination 64-Bit Floating Point value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-770">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-770">Return Values</span></span>

- <span data-ttu-id="7020e-771">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-771">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-772">**NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7020e-772">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="7020e-773">**NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem lub nie jest wartością zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="7020e-773">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not a Floating Point value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer32"></a><span data-ttu-id="7020e-774">nx_lwm2m_resource_multiple_get_integer32</span><span class="sxs-lookup"><span data-stu-id="7020e-774">nx_lwm2m_resource_multiple_get_integer32</span></span>

<span data-ttu-id="7020e-775">Pobierz wartość 32-bitowej liczby całkowitej wiele wystąpień zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-775">Get the value of a 32-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-776">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-776">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer32(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT32 *int32_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-777">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-777">Description</span></span>

<span data-ttu-id="7020e-778">Usługa Pobiera wartość 32-bitowej liczby całkowitej wystąpienia zasobu z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-778">The service retrieves the value of a 32-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-779">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-779">Parameters</span></span>

- <span data-ttu-id="7020e-780">**wartość**: wskaźnik do opisu wartości wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-780">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="7020e-781">**index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-781">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="7020e-782">**instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-782">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="7020e-783">**int32_ptr**: wskaźnik do wartości docelowej 32-bitowej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7020e-783">**int32_ptr**: Pointer to the destination 32-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-784">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-784">Return Values</span></span>

- <span data-ttu-id="7020e-785">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-785">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-786">**NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7020e-786">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="7020e-787">**NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem wielokrotnym lub wartość zasobu nie jest wartością całkowitą lub wartość całkowita nie mieści się w 32-bitowej liczbie.</span><span class="sxs-lookup"><span data-stu-id="7020e-787">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value, or the Integer value doesn't fit in a 32-Bit number.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_integer64"></a><span data-ttu-id="7020e-788">nx_lwm2m_resource_multiple_get_integer64</span><span class="sxs-lookup"><span data-stu-id="7020e-788">nx_lwm2m_resource_multiple_get_integer64</span></span>

<span data-ttu-id="7020e-789">Pobierz wartość 64-bitowej liczby całkowitej wiele wystąpień zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-789">Get the value of a 64-Bit Integer Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-790">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-790">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_integer64(const NX_LWM2M_RESOURCE *value,
        int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_INT64 *int64_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-791">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-791">Description</span></span>

<span data-ttu-id="7020e-792">Usługa Pobiera wartość 64-bitowej liczby całkowitej wystąpienia zasobu z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-792">The service retrieves the value of a 64-Bit Integer Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-793">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-793">Parameters</span></span>

- <span data-ttu-id="7020e-794">**wartość**: wskaźnik do opisu wartości wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-794">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="7020e-795">**index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-795">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="7020e-796">**instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-796">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="7020e-797">**int64_ptr**: wskaźnik do wartości docelowej 64-bitowej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7020e-797">**int64_ptr**: Pointer to the destination 64-Bit Integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-798">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-798">Return Values</span></span>

- <span data-ttu-id="7020e-799">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-799">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-800">**NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7020e-800">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="7020e-801">**NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem wielokrotnym lub wartość zasobu nie jest wartością całkowitą.</span><span class="sxs-lookup"><span data-stu-id="7020e-801">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Integer value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_objlnk"></a><span data-ttu-id="7020e-802">nx_lwm2m_resource_multiple_get_objlnk</span><span class="sxs-lookup"><span data-stu-id="7020e-802">nx_lwm2m_resource_multiple_get_objlnk</span></span>

<span data-ttu-id="7020e-803">Pobieranie wartości linku do obiektu z wieloma wystąpieniami zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-803">Get the value of an Object Link Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-804">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-804">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_objlnk(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, NX_LWM2M_OBJLNK *objlnk_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-805">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-805">Description</span></span>

<span data-ttu-id="7020e-806">Usługa Pobiera wartość wystąpienia zasobu linku do obiektu z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-806">The service retrieves the value of an Object Link Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-807">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-807">Parameters</span></span>

- <span data-ttu-id="7020e-808">**wartość**: wskaźnik do opisu wartości wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-808">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="7020e-809">**index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-809">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="7020e-810">**instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-810">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="7020e-811">**objlnk_ptr**: wskaźnik do wartości linku do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-811">**objlnk_ptr**: Pointer to the destination Object Link value.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-812">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-812">Return Values</span></span>

- <span data-ttu-id="7020e-813">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-813">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-814">**NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7020e-814">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="7020e-815">**NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem wielokrotnym lub wartość zasobu nie jest wartością linku obiektu.</span><span class="sxs-lookup"><span data-stu-id="7020e-815">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Object Link value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_opaque"></a><span data-ttu-id="7020e-816">nx_lwm2m_resource_multiple_get_opaque</span><span class="sxs-lookup"><span data-stu-id="7020e-816">nx_lwm2m_resource_multiple_get_opaque</span></span>

<span data-ttu-id="7020e-817">Pobierz wartość nieprzezroczystego wystąpienia wielu zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-817">Get the value of an Opaque Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-818">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-818">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_opaque(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const VOID **opaque_ptr_ptr,
    UINT *opaque_length_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-819">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-819">Description</span></span>

<span data-ttu-id="7020e-820">Usługa Pobiera wartość nieprzezroczystego wystąpienia zasobu z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-820">The service retrieves the value of an Opaque Resource Instance from a Multiple Resource.</span></span>

<span data-ttu-id="7020e-821">Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.</span><span class="sxs-lookup"><span data-stu-id="7020e-821">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-822">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-822">Parameters</span></span>

- <span data-ttu-id="7020e-823">**wartość**: wskaźnik do opisu wartości wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-823">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="7020e-824">**index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-824">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="7020e-825">**instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-825">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="7020e-826">**opaque_ptr_ptr**: wskaźnik do docelowego wskaźnika bufora nieprzezroczystości.</span><span class="sxs-lookup"><span data-stu-id="7020e-826">**opaque_ptr_ptr**: Pointer to the destination opaque buffer pointer.</span></span>
- <span data-ttu-id="7020e-827">**opaque_length_ptr**: wskaźnik do docelowej długości buforu nieprzezroczystości.</span><span class="sxs-lookup"><span data-stu-id="7020e-827">**opaque_length_ptr**: Pointer to the destination opaque buffer length.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-828">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-828">Return Values</span></span>

- <span data-ttu-id="7020e-829">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-829">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-830">**NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7020e-830">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="7020e-831">**NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem wielokrotnym lub wartość zasobu nie jest wartością nieprzezroczystą.</span><span class="sxs-lookup"><span data-stu-id="7020e-831">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the resource value is not an Opaque value.</span></span>

## <a name="nx_lwm2m_resource_multiple_get_string"></a><span data-ttu-id="7020e-832">nx_lwm2m_resource_multiple_get_string</span><span class="sxs-lookup"><span data-stu-id="7020e-832">nx_lwm2m_resource_multiple_get_string</span></span>

<span data-ttu-id="7020e-833">Pobierz wartość ciągu z wieloma wystąpieniami zasobów</span><span class="sxs-lookup"><span data-stu-id="7020e-833">Get the value of a String Multiple Resource Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="7020e-834">Prototype</span><span class="sxs-lookup"><span data-stu-id="7020e-834">Prototype</span></span>

```c
UINT nx_lwm2m_resource_multiple_get_string(const NX_LWM2M_RESOURCE *value,
    int index, NX_LWM2M_ID *instance_id_ptr, const CHAR **string_ptr_ptr,
    UINT *string_length_ptr);
```

### <a name="description"></a><span data-ttu-id="7020e-835">Opis</span><span class="sxs-lookup"><span data-stu-id="7020e-835">Description</span></span>

<span data-ttu-id="7020e-836">Usługa Pobiera wartość wystąpienia zasobu ciągu z wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-836">The service retrieves the value of a String Resource Instance from a Multiple Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="7020e-837">Parametry</span><span class="sxs-lookup"><span data-stu-id="7020e-837">Parameters</span></span>

- <span data-ttu-id="7020e-838">**wartość**: wskaźnik do opisu wartości wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="7020e-838">**value**: Pointer to the Multiple Resource value description.</span></span>
- <span data-ttu-id="7020e-839">**index**: indeks wystąpienia do pobrania w tablicy wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="7020e-839">**index**: Index of the Instance to retrieve in the Resource value array.</span></span>
- <span data-ttu-id="7020e-840">**instance_id_ptr**: wskaźnik do docelowego identyfikatora wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7020e-840">**instance_id_ptr**: Pointer to the destination Instance ID.</span></span>
- <span data-ttu-id="7020e-841">**string_ptr_ptr**: wskaźnik do wskaźnika ciągu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7020e-841">**string_ptr_ptr**: Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="7020e-842">**string_length_ptr**: wskaźnik do docelowej długości ciągu.</span><span class="sxs-lookup"><span data-stu-id="7020e-842">**string_length_ptr**: Pointer to the destination string length.</span></span> <span data-ttu-id="7020e-843">Może mieć wartość NULL, jeśli ciąg jest zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="7020e-843">Can be NULL if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="7020e-844">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="7020e-844">Return Values</span></span>

- <span data-ttu-id="7020e-845">**NX_SUCCESS**: operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="7020e-845">**NX_SUCCESS**: Successful operation.</span></span>
- <span data-ttu-id="7020e-846">**NX_LWM2M_BAD_PARAMETER**: indeks jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="7020e-846">**NX_LWM2M_BAD_PARAMETER**: The index is out of range.</span></span>
- <span data-ttu-id="7020e-847">**NX_LWM2M_BAD_ENCODING**: zasób nie jest zasobem lub wartość wystąpienia nie jest wartością ciągu.</span><span class="sxs-lookup"><span data-stu-id="7020e-847">**NX_LWM2M_BAD_ENCODING**: The resource is not a multiple resource, or the instance value is not a String value.</span></span>
