---
title: Rozdział 4 — Opis usług klienta LWM2M
description: Ten rozdział zawiera opis wszystkich usług LWM2M Client w porządku alfabetycznym.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 825a215ba756b39b6d76e6cc773c288e8b8aab01
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821834"
---
# <a name="chapter-4--description-of-lwm2m-client-services"></a><span data-ttu-id="f6e5f-103">Rozdział 4 Opis usług klienta LWM2M</span><span class="sxs-lookup"><span data-stu-id="f6e5f-103">Chapter 4  Description of LWM2M CLIENT Services</span></span>

<span data-ttu-id="f6e5f-104">Ten rozdział zawiera opis wszystkich usług klienta LWM2M wymienionych poniżej w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-104">This chapter contains a description of all LWM2M Client services listed below in alphabetic order.</span></span>

<span data-ttu-id="f6e5f-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione**  **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the  **NX_DISABLE_ERROR_CHECKING** define that is used to disable API  error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="f6e5f-106">**LWM2M zarządzanie klientami:**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-106">**LWM2M Client Management:**</span></span>

- <span data-ttu-id="f6e5f-107">nx_lwm2m_client_create: *Utwórz klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-107">nx_lwm2m_client_create: *Create LWM2M Client*</span></span>

- <span data-ttu-id="f6e5f-108">nx_lwm2m_client_delete: *Usuwanie klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-108">nx_lwm2m_client_delete: *Delete LWM2M Client*</span></span>

- <span data-ttu-id="f6e5f-109">nx_lwm2m_client_lock: *Zablokuj klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-109">nx_lwm2m_client_lock: *Lock LWM2M Client*</span></span>

- <span data-ttu-id="f6e5f-110">nx_lwm2m_client_unlock: *Odblokuj klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-110">nx_lwm2m_client_unlock: *Unlock LWM2M Client*</span></span>

<span data-ttu-id="f6e5f-111">**LWM2M zarządzanie sesją klienta:**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-111">**LWM2M Client Session Management:**</span></span>

- <span data-ttu-id="f6e5f-112">nx_lwm2m_client_session_create: *Utwórz sesję klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-112">nx_lwm2m_client_session_create: *Create LWM2M Client Session*</span></span>

- <span data-ttu-id="f6e5f-113">nx_lwm2m_client_session_delete: *usuwanie sesji klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-113">nx_lwm2m_client_session_delete: *Delete LWM2M Client Session*</span></span>

- <span data-ttu-id="f6e5f-114">nx_lwm2m_client_session_bootstrap: *Uruchamianie sesji z serwerem Bootstrap*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-114">nx_lwm2m_client_session_bootstrap: *Start a session with a Bootstrap Server*</span></span>

- <span data-ttu-id="f6e5f-115">nx_lwm2m_client_session_bootstrap_dtls: *Rozpoczynanie bezpiecznej sesji z serwerem Bootstrap*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-115">nx_lwm2m_client_session_bootstrap_dtls: *Start a secure session with a Bootstrap Server*</span></span>

- <span data-ttu-id="f6e5f-116">nx_lwm2m_client_session_register_info_get: *pobieranie informacji o rejestrowaniu serwera lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-116">nx_lwm2m_client_session_register_info_get: *Get LWM2M Server register info*</span></span>

- <span data-ttu-id="f6e5f-117">nx_lwm2m_client_session_register: *Uruchamianie sesji z serwerem lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-117">nx_lwm2m_client_session_register: *Start a session with a LWM2M Server*</span></span>

- <span data-ttu-id="f6e5f-118">nx_lwm2m_client_session_register_dtls: *Rozpoczynanie bezpiecznej sesji z serwerem lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-118">nx_lwm2m_client_session_register_dtls: *Start a secure session with a LWM2M Server*</span></span>

- <span data-ttu-id="f6e5f-119">nx_lwm2m_client_session_update: *Aktualizowanie sesji przy użyciu serwera lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-119">nx_lwm2m_client_session_update: *Update a session with a LWM2M Server*</span></span>

- <span data-ttu-id="f6e5f-120">nx_lwm2m_client_session_deregister: *przerywanie sesji z serwerem lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-120">nx_lwm2m_client_session_deregister: *Terminate a session with a LWM2M Server*</span></span>

- <span data-ttu-id="f6e5f-121">nx_lwm2m_client_session_error_get: *Pobierz ostatni błąd sesji*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-121">nx_lwm2m_client_session_error_get: *Get last error of a session*</span></span>

<span data-ttu-id="f6e5f-122">**Implementacja obiektu urządzenia:**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-122">**Device Object Implementation:**</span></span>

- <span data-ttu-id="f6e5f-123">nx_lwm2m_client_device_callbacks_set: *Ustaw wywołania zwrotne aplikacji obiektu urządzenia*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-123">nx_lwm2m_client_device_callbacks_set: *Set Device Object application callbacks*</span></span>

- <span data-ttu-id="f6e5f-124">nx_lwm2m_client_device_error_push: *Dodaj kod błędu do obiektu urządzenia*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-124">nx_lwm2m_client_device_error_push: *Add error code to Device Object*</span></span>

- <span data-ttu-id="f6e5f-125">nx_lwm2m_client_device_error_reset: *Resetowanie kodów błędów obiektu urządzenia*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-125">nx_lwm2m_client_device_error_reset: *Reset error codes of Device Object*</span></span>

- <span data-ttu-id="f6e5f-126">nx_lwm2m_client_device_resource_changed: *zmiana sygnału zasobu obiektu urządzenia*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-126">nx_lwm2m_client_device_resource_changed: *Signal change of Device Object resource*</span></span>

<span data-ttu-id="f6e5f-127">**Implementacja obiektu aktualizacji oprogramowania układowego:**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-127">**Firmware Update Object Implementation:**</span></span>

- <span data-ttu-id="f6e5f-128">nx_lwm2m_firmware_create: *Tworzenie obiektu aktualizacji oprogramowania układowego*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-128">nx_lwm2m_firmware_create: *Create Firmware Update Object*</span></span>

- <span data-ttu-id="f6e5f-129">nx_lwm2m_firmware_package_info_set: *Ustawianie informacji o pakiecie aktualizacji oprogramowania układowego*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-129">nx_lwm2m_firmware_package_info_set: *Set Firmware Update Package Information*</span></span>

- <span data-ttu-id="f6e5f-130">nx_lwm2m_firmware_result_set: *Ustaw wynik aktualizacji oprogramowania układowego*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-130">nx_lwm2m_firmware_result_set: *Set Firmware Update Result*</span></span>

- <span data-ttu-id="f6e5f-131">nx_lwm2m_firmware_state_set: *Ustaw stan aktualizacji oprogramowania układowego*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-131">nx_lwm2m_firmware_state_set: *Set Firmware Update State*</span></span>

<span data-ttu-id="f6e5f-132">**Implementacja obiektów niestandardowych:**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-132">**Custom Objects Implementation:**</span></span>

- <span data-ttu-id="f6e5f-133">nx_lwm2m_client_object_add: *Dodawanie implementacji obiektu do klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-133">nx_lwm2m_client_object_add: *Add Object implementation to LWM2M Client*</span></span>

- <span data-ttu-id="f6e5f-134">nx_lwm2m_client_object_remove: *usuwanie implementacji obiektu z klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-134">nx_lwm2m_client_object_remove: *Remove Object implementation from LWM2M Client*</span></span>

- <span data-ttu-id="f6e5f-135">nx_lwm2m_client_object_instance_add: *Dodaj wystąpienie obiektu do Lwm2m klienta*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-135">nx_lwm2m_client_object_instance_add: *Add Object Instance to LWM2M Client*</span></span>

- <span data-ttu-id="f6e5f-136">nx_lwm2m_client_object_instance_remove: *usuwanie wystąpienia obiektu z klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-136">nx_lwm2m_client_object_instance_remove: *Remove Object Instance from LWM2M Client*</span></span>

- <span data-ttu-id="f6e5f-137">nx_lwm2m_object_resource_changed: *zmiana sygnału dla wartości zasobu wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-137">nx_lwm2m_object_resource_changed: *Signal change of a resource value of an Object Instance*</span></span>

<span data-ttu-id="f6e5f-138">**Zarządzanie urządzeniami lokalnymi**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-138">**Local Device Management**</span></span>

- <span data-ttu-id="f6e5f-139">nx_lwm2m_client_object_create: *Utwórz nowe wystąpienie obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-139">nx_lwm2m_client_object_create: *Create a new Object Instance*</span></span>

- <span data-ttu-id="f6e5f-140">nx_lwm2m_client_object_delete: *usuwanie wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-140">nx_lwm2m_client_object_delete: *Delete an Object Instance*</span></span>

- <span data-ttu-id="f6e5f-141">nx_lwm2m_client_object_discover: *odnajdywanie zasobów wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-141">nx_lwm2m_client_object_discover: *Discover resources of an Object Instance*</span></span>

- <span data-ttu-id="f6e5f-142">nx_lwm2m_client_object_execute: *wykonywanie zasobu wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-142">nx_lwm2m_client_object_execute: *Execute resource of an Object Instance*</span></span>

- <span data-ttu-id="f6e5f-143">nx_lwm2m_client_object_next_get: *Pobieranie listy obiektów wdrożonych przez klienta lwm2m*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-143">nx_lwm2m_client_object_next_get: *Get the list of Objects implemented by the LWM2M Client*</span></span>

- <span data-ttu-id="f6e5f-144">nx_lwm2m_client_object_instance_next_get: *Pobieranie listy wystąpień obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-144">nx_lwm2m_client_object_instance_next_get: *Get the list of Instances of an Object*</span></span>

- <span data-ttu-id="f6e5f-145">nx_lwm2m_client_object_read: *Odczytywanie wartości zasobów wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-145">nx_lwm2m_client_object_read: *Read resources values of an Object Instance*</span></span>

- <span data-ttu-id="f6e5f-146">nx_lwm2m_client_object_write: *zmiana wartości zasobów wystąpienia obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-146">nx_lwm2m_client_object_write: *Change resources values of an Object instance*</span></span>

<span data-ttu-id="f6e5f-147">**Ustawienia informacji o zasobach i wartości:**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-147">**Resources Info and Values Setting:**</span></span>

- <span data-ttu-id="f6e5f-148">nx_lwm2m_client_resource_info_set: *Ustaw informacje o zasobie*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-148">nx_lwm2m_client_resource_info_set: *Set the resource info*</span></span>

- <span data-ttu-id="f6e5f-149">nx_lwm2m_client_resource_string_set: *Ustaw wartość zasobu jako ciąg*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-149">nx_lwm2m_client_resource_string_set: *Set the resource value as string*</span></span>

- <span data-ttu-id="f6e5f-150">nx_lwm2m_client_resource_integer32_set: *Ustaw wartość zasobu jako 32-bitową liczbę całkowitą*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-150">nx_lwm2m_client_resource_integer32_set: *Set the resource value as 32-Bit integer*</span></span>

- <span data-ttu-id="f6e5f-151">nx_lwm2m_client_resource_integer64_set: *Ustaw wartość zasobu jako 64-bitową liczbę całkowitą*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-151">nx_lwm2m_client_resource_integer64_set: *Set the resource value as 64-Bit integer*</span></span>

- <span data-ttu-id="f6e5f-152">nx_lwm2m_client_resource_float32_set: *Ustaw wartość zasobu jako 32-bitową zmiennoprzecinkową*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-152">nx_lwm2m_client_resource_float32_set: *Set the resource value as 32-Bit float*</span></span>

- <span data-ttu-id="f6e5f-153">nx_lwm2m_client_resource_float64_set: *Ustaw wartość zasobu jako 64-bitową zmiennoprzecinkową*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-153">nx_lwm2m_client_resource_float64_set: *Set the resource value as 64-Bit float*</span></span>

- <span data-ttu-id="f6e5f-154">nx_lwm2m_client_resource_boolean_set: *Ustaw wartość zasobu jako logiczną*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-154">nx_lwm2m_client_resource_boolean_set: *Set the resource value as boolean*</span></span>

- <span data-ttu-id="f6e5f-155">nx_lwm2m_client_resource_objlnk_set: *Ustaw wartość zasobu jako link do obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-155">nx_lwm2m_client_resource_objlnk_set: *Set the resource value as object link*</span></span>

- <span data-ttu-id="f6e5f-156">nx_lwm2m_client_resource_opaque_set: *Ustaw wartość zasobu jako nieprzezroczystą*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-156">nx_lwm2m_client_resource_opaque_set: *Set the resource value as opaque*</span></span>

- <span data-ttu-id="f6e5f-157">nx_lwm2m_client_resource_instance_set: *Ustaw wartość zasobu jako wystąpienie dla wielu zasobów*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-157">nx_lwm2m_client_resource_instance_set: *Set the resource value as instance for multiple resource*</span></span>
-
- <span data-ttu-id="f6e5f-158">nx_lwm2m_client_resource_dim_set: *Ustaw wymiar zasobu dla wielu zasobów.*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-158">nx_lwm2m_client_resource_dim_set: *Set the resource dimension for multiple resource.*</span></span>

<span data-ttu-id="f6e5f-159">**Informacje o zasobach i wartości:**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-159">**Resources Info and Values Getting:**</span></span>

- <span data-ttu-id="f6e5f-160">nx_lwm2m_client_resource_info_get: *Uzyskiwanie informacji o zasobie*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-160">nx_lwm2m_client_resource_info_get: *Get the resource info*</span></span>

- <span data-ttu-id="f6e5f-161">nx_lwm2m_client_resource_string_get: *pobieranie wartości zasobu ciągu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-161">nx_lwm2m_client_resource_string_get: *Get the value of a string resource*</span></span>

- <span data-ttu-id="f6e5f-162">nx_lwm2m_client_resource_integer32_get: *pobieranie wartości 32-bitowego zasobu liczb całkowitych*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-162">nx_lwm2m_client_resource_integer32_get: *Get the value of a 32-Bit integer resource*</span></span>

- <span data-ttu-id="f6e5f-163">nx_lwm2m_client_resource_integer64_get: *pobieranie wartości 64-bitowego zasobu liczb całkowitych*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-163">nx_lwm2m_client_resource_integer64_get: *Get the value of a 64-Bit integer resource*</span></span>

- <span data-ttu-id="f6e5f-164">nx_lwm2m_client_resource_float32_get: *pobieranie wartości 32-bitowego zasobu zmiennoprzecinkowego*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-164">nx_lwm2m_client_resource_float32_get: *Get the value of a 32-Bit float resource*</span></span>

- <span data-ttu-id="f6e5f-165">nx_lwm2m_client_resource_float64_get: *pobieranie wartości 64-bitowego zasobu zmiennoprzecinkowego*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-165">nx_lwm2m_client_resource_float64_get: *Get the value of a 64-Bit float resource*</span></span>

- <span data-ttu-id="f6e5f-166">nx_lwm2m_client_resource_boolean_get: *pobieranie wartości zasobu logicznego*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-166">nx_lwm2m_client_resource_boolean_get: *Get the value of a boolean resource*</span></span>

- <span data-ttu-id="f6e5f-167">nx_lwm2m_client_resource_objlnk_get: *pobieranie wartości zasobu linku do obiektu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-167">nx_lwm2m_client_resource_objlnk_get: *Get the value of an object link resource*</span></span>

- <span data-ttu-id="f6e5f-168">nx_lwm2m_client_resource_opaque_get: *Pobierz wartość nieprzezroczystego zasobu*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-168">nx_lwm2m_client_resource_opaque_get: *Get the value of an opaque resource*</span></span>

- <span data-ttu-id="f6e5f-169">nx_lwm2m_client_resource_instance_get: *Pobieranie wystąpienia zasobu dla wielu zasobów*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-169">nx_lwm2m_client_resource_instance_get: *Get the resource instance for multiple resource*</span></span>

- <span data-ttu-id="f6e5f-170">nx_lwm2m_client_resource_dim_get: *Pobierz wymiar zasobu dla wielu zasobów.*</span><span class="sxs-lookup"><span data-stu-id="f6e5f-170">nx_lwm2m_client_resource_dim_get: *Get the resource dimension for multiple resource.*</span></span>

## <a name="nx_lwm2m_client_create"></a><span data-ttu-id="f6e5f-171">nx_lwm2m_client_create</span><span class="sxs-lookup"><span data-stu-id="f6e5f-171">nx_lwm2m_client_create</span></span>

<span data-ttu-id="f6e5f-172">Tworzy klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-172">Creates a LWM2M client.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-173">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-173">Prototype</span></span>

```C
UINT nx_lwm2m_client_create(
    NX_LWM2M_CLIENT client_ptr,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    const CHAR *name_ptr,
    UINT name_length,
    const CHAR *msisdn_ptr,
    UINT msisdn_length,
    UCHAR binding_modes,
    VOID *stack_ptr,
    ULONG stack_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="f6e5f-174">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-174">Description</span></span>

<span data-ttu-id="f6e5f-175">Ta usługa tworzy wystąpienie klienta LWM2M, które działa w kontekście jego własnego wątku ThreadX.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-175">This service creates a LWM2M Client instance, which runs in the context of its own ThreadX thread.</span></span>

<span data-ttu-id="f6e5f-176">Klient LWM2M implementuje następujące obiekty OMA LWM2M: Security (0), Server (1), Access Control (2) i Device (3).</span><span class="sxs-lookup"><span data-stu-id="f6e5f-176">The LWM2M Client implements the following OMA LWM2M Objects: Security (0), Server (1), Access Control (2) and Device (3).</span></span> <span data-ttu-id="f6e5f-177">Inne implementacje obiektów muszą być dodane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-177">The other objects implementations must be added by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-178">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-178">Parameters</span></span>

- <span data-ttu-id="f6e5f-179">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-179">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-180">**ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-180">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="f6e5f-181">**packet_pool_ptr** Wskaźnik do domyślnej puli pakietów dla tego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-181">**packet_pool_ptr** Pointer to the default packet pool for this LWM2M Client.</span></span>
- <span data-ttu-id="f6e5f-182">**name_ptr** Wskaźnik do LWM2M nazwa punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-182">**name_ptr** Pointer to LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="f6e5f-183">**name_length** Długość nazwy punktu końcowego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-183">**name_length** Length of LWM2M Client endpoint name.</span></span>
- <span data-ttu-id="f6e5f-184">**msisdn_ptr** Wskaźnik do MSISDN, w którym można nawiązać połączenie z klientem LWM2M do użycia z powiązaniem programu SMS, może mieć wartość NULL, Jeśli powiązanie programu SMS nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-184">**msisdn_ptr** Pointer to the MSISDN where the LWM2M Client can be reached for use with the SMS binding, can be NULL if SMS binding is not supported.</span></span>
- <span data-ttu-id="f6e5f-185">**msisdn_length** Długość numeru MSISDN.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-185">**msisdn_length** Length of MSISDN number.</span></span>
- <span data-ttu-id="f6e5f-186">**binding_modes** Powiązanie i tryby obsługiwane przez klienta LWM2M muszą być kombinacją flag NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S i NX_LWM2M_BINDING_SQ.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-186">**binding_modes** The binding and modes supported by the LWM2M Client, must be a combination of NX_LWM2M_BINDING_U, NX_LWM2M_BINDING_UQ, NX_LWM2M_BINDING_S and NX_LWM2M_BINDING_SQ flags.</span></span>
- <span data-ttu-id="f6e5f-187">**stack_ptr** Wskaźnik do obszaru stosu wątku klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-187">**stack_ptr** Pointer to LWM2M Client thread stack area.</span></span>
- <span data-ttu-id="f6e5f-188">**stack_size** Rozmiar stosu wątku klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-188">**stack_size** The LWM2M Client thread stack size.</span></span>
- <span data-ttu-id="f6e5f-189">**priorytet** Priorytet klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-189">**priority** Priority of LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-190">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-190">Return Values</span></span>

- <span data-ttu-id="f6e5f-191">**NX_SUCCESS** Klient LWM2M został pomyślnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-191">**NX_SUCCESS** The LWM2M Client has been successfully created.</span></span>
- <span data-ttu-id="f6e5f-192">**NX_LWM2M_CLIENT_ERROR** Wystąpił błąd podczas tworzenia klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-192">**NX_LWM2M_CLIENT_ERROR** LWM2M Client create error.</span></span>
- <span data-ttu-id="f6e5f-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-193">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="f6e5f-194">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-194">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="f6e5f-195">**NX_SIZE_ERROR** Nieprawidłowy rozmiar stosu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-195">**NX_SIZE_ERROR** Invalid stack size.</span></span>
- <span data-ttu-id="f6e5f-196">**NX_OPTION_ERROR** Nieprawidłowy priorytet.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-196">**NX_OPTION_ERROR** Invalid priority.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-197">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-197">Allowed From</span></span>

<span data-ttu-id="f6e5f-198">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-198">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-199">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-199">Example</span></span>

```C
/* Create LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client, &ip_0, &pool_0, 
  "netxlwm2mclient", sizeof("netxlwm2mclient") - 1,           
                                NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, 
                                stack_ptr, stack_size, priority);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully created.  */
```

## <a name="nx_lwm2m_client_delete"></a><span data-ttu-id="f6e5f-200">nx_lwm2m_client_delete</span><span class="sxs-lookup"><span data-stu-id="f6e5f-200">nx_lwm2m_client_delete</span></span>

<span data-ttu-id="f6e5f-201">Usuwa klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-201">Deletes a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-202">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-202">Prototype</span></span>

```C
UINT nx_lwm2m_client_delete(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-203">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-203">Description</span></span>

<span data-ttu-id="f6e5f-204">Ta usługa usuwa wcześniej utworzone wystąpienie klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-204">This service deletes a previously created LWM2M Client instance.</span></span>

<span data-ttu-id="f6e5f-205">Wszystkie sesje, które są obecnie dołączone do klienta, są również usuwane przez to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-205">All sessions currently attached the client are also deleted by this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-206">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-206">Parameters</span></span>

- <span data-ttu-id="f6e5f-207">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-207">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-208">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-208">Return Values</span></span>

- <span data-ttu-id="f6e5f-209">**NX_SUCCESS** Klient LWM2M został pomyślnie usunięty.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-209">**NX_SUCCESS** The LWM2M Client has been successfully deleted.</span></span>
- <span data-ttu-id="f6e5f-210">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-210">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-211">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-211">Allowed From</span></span>

<span data-ttu-id="f6e5f-212">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-212">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-213">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-213">Example</span></span>

```c
/* Delete the LWM2M Client instance.  */
status = nx_lwm2m_client_create(&lwm2m_client);

/* If status is NX_SUCCESS a LWM2M Client instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_device_callback_set"></a><span data-ttu-id="f6e5f-214">nx_lwm2m_client_device_callback_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-214">nx_lwm2m_client_device_callback_set</span></span>

<span data-ttu-id="f6e5f-215">Ustawia wywołanie zwrotne aplikacji obiektu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-215">Sets a device object's application callback.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-216">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_callback_set**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_DEVICE_OPERATION_CALLBACK operation_callback);
```

### <a name="description"></a><span data-ttu-id="f6e5f-217">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-217">Description</span></span>

<span data-ttu-id="f6e5f-218">Ta usługa służy do instalowania wywołania zwrotnego aplikacji w celu zaimplementowania operacji na zasobach obiektów urządzenia LWM2M, które nie są obsługiwane przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-218">This service installs the application callback for implementing operations on the LWM2M Device Object resources that are not handled by the LWM2M Client.</span></span>

<span data-ttu-id="f6e5f-219">Klient LWM2M implementuje następujące zasoby: kod błędu (11), resetowanie kodu błędu (12) i obsługiwane powiązania i tryby (16), operacje innych zasobów są przekierowywane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-219">The LWM2M Client implements the following resources: Error Code (11), Reset Error Code (12) and Supported Binding and Modes (16), operations to the other resources are redirected to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-220">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-220">Parameters</span></span>

- <span data-ttu-id="f6e5f-221">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-221">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-222">**operation_callback** Wywołanie zwrotne operacji dla "read", "Discovery", "Write" i "Execute".</span><span class="sxs-lookup"><span data-stu-id="f6e5f-222">**operation_callback** The operation callback for “Read”, “Discover”, “Write” and “Execute”.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-223">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-223">Return Values</span></span>

- <span data-ttu-id="f6e5f-224">**NX_SUCCESS** Wywołanie zwrotne operacji zostało pomyślnie ustawione.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-224">**NX_SUCCESS** The operation callback has been successfully set.</span></span>
- <span data-ttu-id="f6e5f-225">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-225">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-226">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-226">Allowed From</span></span>

<span data-ttu-id="f6e5f-227">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-227">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-228">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-228">Example</span></span>

```c
/* Set device callback.  */
status = nx_lwm2m_client_device_callback_set(&lwm2m_client, device_operation);

/* If status is NX_SUCCESS a device callback was successfully set.  */
```

## <a name="nx_lwm2m_client_device_error_push"></a><span data-ttu-id="f6e5f-229">nx_lwm2m_client_device_error_push</span><span class="sxs-lookup"><span data-stu-id="f6e5f-229">nx_lwm2m_client_device_error_push</span></span>
<span data-ttu-id="f6e5f-230">Dodaje kod błędu do obiektu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-230">Adds an error code to a device object.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-231">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-231">Prototype</span></span>

```C
UINT **nx_lwm2m_client_device_error_push**(
    NX_LWM2M_CLIENT *client_ptr,
    UCHAR code);
```

### <a name="description"></a><span data-ttu-id="f6e5f-232">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-232">Description</span></span>

<span data-ttu-id="f6e5f-233">Ta usługa dodaje nowe wystąpienie do zasobu kod błędu (11) urządzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-233">This service adds a new instance to the Error Code (11) resource of the Object Device.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-234">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-234">Parameters</span></span>

- <span data-ttu-id="f6e5f-235">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-235">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-236">**kod** Nowy kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-236">**code** The new error code.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-237">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-237">Return Values</span></span>

- <span data-ttu-id="f6e5f-238">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-238">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-239">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL**</span></span>

<span data-ttu-id="f6e5f-240">Maksymalna liczba przechowywanych kodów błędów ma</span><span class="sxs-lookup"><span data-stu-id="f6e5f-240">The maximum number of stored error codes has</span></span>

<span data-ttu-id="f6e5f-241">został osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-241">been reached.</span></span>

<span data-ttu-id="f6e5f-242">NX_PTR_ERROR nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-242">NX_PTR_ERROR Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-243">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-243">Allowed From</span></span>

<span data-ttu-id="f6e5f-244">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-244">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-245">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-245">Example</span></span>

```C
/* Push device error 1 (Low battery power) to server.  */
status = nx_lwm2m_client_device_error_push(&lwm2m_client, 1);

/* If status is NX_SUCCESS a device error was successfully pushed.  */
```

## <a name="nx_lwm2m_client_device_error_reset"></a><span data-ttu-id="f6e5f-246">nx_lwm2m_client_device_error_reset</span><span class="sxs-lookup"><span data-stu-id="f6e5f-246">nx_lwm2m_client_device_error_reset</span></span>

<span data-ttu-id="f6e5f-247">Resetuje kody błędów obiektu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-247">Resets the error codes of Device Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-248">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-248">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_error_reset(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-249">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-249">Description</span></span>

<span data-ttu-id="f6e5f-250">Ta usługa usuwa wszystkie wystąpienia zasobów kodu błędu z obiektu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-250">This service deletes all error code resource instances from the Device Object.</span></span> <span data-ttu-id="f6e5f-251">Jest to równoznaczne z wykonaniem kodu błędu resetowania zasobu (12).</span><span class="sxs-lookup"><span data-stu-id="f6e5f-251">This is equivalent to executing the resource Reset Error Code (12).</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-252">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-252">Parameters</span></span>

- <span data-ttu-id="f6e5f-253">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-253">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-254">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-254">Return Values</span></span>

- <span data-ttu-id="f6e5f-255">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-255">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-256">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-256">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-257">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-257">Allowed From</span></span>

<span data-ttu-id="f6e5f-258">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-258">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-259">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-259">Example</span></span>

```c
/* Delete all device error code.  */
status = nx_lwm2m_client_device_error_reset(&lwm2m_client);

/* If status is NX_SUCCESS, reset device error successfully.  */
```

## <a name="nx_lwm2m_client_device_resource_changed"></a><span data-ttu-id="f6e5f-260">nx_lwm2m_client_device_resource_changed</span><span class="sxs-lookup"><span data-stu-id="f6e5f-260">nx_lwm2m_client_device_resource_changed</span></span>

<span data-ttu-id="f6e5f-261">Sygnalizuje zmianę zasobu obiektu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-261">Signals a change to a Device Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-262">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-262">Prototype</span></span>

```c
UINT nx_lwm2m_client_device_resource_changed(
    NX_LWM2M_CLIENT *client_ptr, 
    const NX_LWM2M_RESOURCE *resource);

```

### <a name="description"></a><span data-ttu-id="f6e5f-263">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-263">Description</span></span>

<span data-ttu-id="f6e5f-264">Usługa jest używana przez aplikację do sygnalizowania klienta LWM2M, że zasób urządzenia obiektu został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-264">The service is used by the application to signal to the LWM2M Client that a resource of the Object Device has changed.</span></span> <span data-ttu-id="f6e5f-265">Klient LWM2M wyśle powiadomienie, jeśli zasób jest zaobserwowany przez serwer LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-265">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-266">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-266">Parameters</span></span>

- <span data-ttu-id="f6e5f-267">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-267">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-268">**zasób** Wskaźnik do struktury opisującej zasób, który został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-268">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-269">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-269">Return Values</span></span>

- <span data-ttu-id="f6e5f-270">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-270">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-271">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-271">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-272">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-272">Allowed From</span></span>

<span data-ttu-id="f6e5f-273">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-273">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-274">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-274">Example</span></span>

```c
/* Change device resource.  */
status = nx_lwm2m_client_device_resource_changed(&lwm2m_client, &resource);

/* If status is NX_SUCCESS, a device resource was successfully changed.  */
```

##  <a name="nx_lwm2m_client_firmware_create"></a><span data-ttu-id="f6e5f-275">nx_lwm2m_client_firmware_create</span><span class="sxs-lookup"><span data-stu-id="f6e5f-275">nx_lwm2m_client_firmware_create</span></span>

<span data-ttu-id="f6e5f-276">Utwórz obiekt oprogramowania układowego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-276">Create a LWM2M Client Firmware Object.</span></span> 

### <a name="prototype"></a><span data-ttu-id="f6e5f-277">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-277">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_create(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    NX_LWM2M_CLIENT *client_ptr, 
    UINT protocols,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_CALLBACK package_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK package_uri_callback,
    NX_LWM2M_CLIENT_FIRMWARE_PACKAGE_URI_CALLBACK update_callback);
```

### <a name="description"></a><span data-ttu-id="f6e5f-278">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-278">Description</span></span>

<span data-ttu-id="f6e5f-279">Usługa jest używana przez aplikację do tworzenia obiektu oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-279">The service is used by the application to create firmware object.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-280">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-280">Parameters</span></span>

- <span data-ttu-id="f6e5f-281">**firmware_ptr** Wskaźnik do LWM2M obiektu oprogramowania układowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-281">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="f6e5f-282">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-282">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-283">**Protokoły** Obsługiwane protokoły.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-283">**protocols** The supported protocols.</span></span>
- <span data-ttu-id="f6e5f-284">**package_callback** Wywołanie zwrotne pakietu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-284">**package_callback** The package callback.</span></span>
- <span data-ttu-id="f6e5f-285">**package_uri_callback** Wywołanie zwrotne URI pakietu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-285">**package_uri_callback** The package URI callback.</span></span>
- <span data-ttu-id="f6e5f-286">**update_callback** Wywołanie zwrotne aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-286">**update_callback** The update callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-287">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-287">Return Values</span></span>

<span data-ttu-id="f6e5f-288">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-288">**NX_SUCCESS** Successful operation.</span></span>
<span data-ttu-id="f6e5f-289">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-289">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-290">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-290">Allowed From</span></span>

<span data-ttu-id="f6e5f-291">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-291">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-292">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-292">Example</span></span>

```c
/* Create firmware object.  */
status = nx_lwm2m_client_firmware_create(&firmware, &lwm2m_client,     
                                         NX_LWM2M_CLIENT_FIRMWARE_PROTOCOL_HTTP, 
                                         NX_NULL, firmware_packet_uri,
                                         firmware_update);

/* If status is NX_SUCCESS, firmware object was successfully created.  */
```

##  <a name="nx_lwm2m_client_firmware_package_info_set"></a><span data-ttu-id="f6e5f-293">nx_lwm2m_client_firmware_package_info_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-293">nx_lwm2m_client_firmware_package_info_set</span></span>

<span data-ttu-id="f6e5f-294">Ustawia informacje o pakiecie oprogramowania układowego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-294">Sets the LWM2M Client Firmware package information.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-295">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-295">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_package_info_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    const CHAR *name, 
    UINT name_length, 
    const CHAR *version, 
    UINT version_length);
```

### <a name="description"></a><span data-ttu-id="f6e5f-296">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-296">Description</span></span>

<span data-ttu-id="f6e5f-297">Ta usługa jest używana przez aplikację do ustawiania zasobów informacji o pakiecie dla obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-297">The service is used by the application to set the package information resources of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-298">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-298">Parameters</span></span>

- <span data-ttu-id="f6e5f-299">**firmware_ptr** Wskaźnik do LWM2M obiektu oprogramowania układowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-299">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="f6e5f-300">**Nazwa** Nazwa pakietu oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-300">**name** The name of firmware package.</span></span>
- <span data-ttu-id="f6e5f-301">**name_length** Długość nazwy.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-301">**name_length** The length of name.</span></span>
- <span data-ttu-id="f6e5f-302">**wersja** Wersja pakietu oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-302">**version** The version of firmware package.</span></span>
- <span data-ttu-id="f6e5f-303">**version_length** Długość wersji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-303">**version_length** The length of version.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-304">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-304">Return Values</span></span>

- <span data-ttu-id="f6e5f-305">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-305">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-306">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-306">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-307">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-307">Allowed From</span></span>

<span data-ttu-id="f6e5f-308">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-308">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-309">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-309">Example</span></span>

```c
/* Set the package information resources of the firmware object.  */
status = nx_lwm2m_client_firmware_package_info_set(&firmware, 2m_client,     
                                    “LWM2M Firmware”, sizeof(“LWM2M Firmware”) -1,
                                    “1.0.0.0”, sizeof(“1.0.0.0”) - 1);

/* If status is NX_SUCCESS, package information resources was successfully set. */
```

##  <a name="nx_lwm2m_client_firmware_result_set"></a><span data-ttu-id="f6e5f-310">nx_lwm2m_client_firmware_result_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-310">nx_lwm2m_client_firmware_result_set</span></span>

<span data-ttu-id="f6e5f-311">Ustawia zasób wynik aktualizacji dla obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-311">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-312">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-312">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_result_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="f6e5f-313">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-313">Description</span></span>

<span data-ttu-id="f6e5f-314">Ta usługa jest używana przez aplikację do ustawiania zasobu wynik aktualizacji dla obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-314">The service is used by the application to set the update result resource of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-315">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-315">Parameters</span></span>

- <span data-ttu-id="f6e5f-316">**firmware_ptr** Wskaźnik do LWM2M obiektu oprogramowania układowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-316">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="f6e5f-317">**wynik** Wynik aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-317">**result** The update result.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-318">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-318">Return Values</span></span>

- <span data-ttu-id="f6e5f-319">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-319">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-320">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-320">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-321">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-321">Allowed From</span></span>

<span data-ttu-id="f6e5f-322">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-322">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-323">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-323">Example</span></span>

```c
/* Set the update result resource of the firmware object.  */
status = nx_lwm2m_client_firmware_result_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_RESULT_SUCCESS);

/* If status is NX_SUCCESS, the update result resource was successfully set.  */
```

##  <a name="nx_lwm2m_client_firmware_state_set"></a><span data-ttu-id="f6e5f-324">nx_lwm2m_client_firmware_state_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-324">nx_lwm2m_client_firmware_state_set</span></span>

<span data-ttu-id="f6e5f-325">Ustawia zasób wynik aktualizacji dla obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-325">Sets the update result resource of the firmware update object.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-326">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-326">Prototype</span></span>

```c
UINT nx_lwm2m_client_firmware_state_set(
    NX_LWM2M_CLIENT_FIRMWARE *firmware_ptr, 
    UCHAR result);
```

### <a name="description"></a><span data-ttu-id="f6e5f-327">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-327">Description</span></span>

<span data-ttu-id="f6e5f-328">Ta usługa jest używana przez aplikację do ustawiania stanu obiektu aktualizacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-328">The service is used by the application to set the state of the firmware update object.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-329">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-329">Parameters</span></span>

- <span data-ttu-id="f6e5f-330">**firmware_ptr** Wskaźnik do LWM2M obiektu oprogramowania układowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-330">**firmware_ptr** Pointer to LWM2M Client Firmware object.</span></span>
- <span data-ttu-id="f6e5f-331">**stan** Stan obiektu oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-331">**state** The state of the firmware object.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-332">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-332">Return Values</span></span>

- <span data-ttu-id="f6e5f-333">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-333">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-334">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-334">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-335">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-335">Allowed From</span></span>

<span data-ttu-id="f6e5f-336">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-336">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-337">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-337">Example</span></span>

```c
/* Set the state of the firmware object.  */
status = nx_lwm2m_client_firmware_state_set(&firmware, 
                                         NX_LWM2M_CLIENT_FIRMWARE_STATE_IDLE);

/* If status is NX_SUCCESS, the state was successfully set.  */
```

## <a name="nx_lwm2m_client_lock"></a><span data-ttu-id="f6e5f-338">nx_lwm2m_client_lock</span><span class="sxs-lookup"><span data-stu-id="f6e5f-338">nx_lwm2m_client_lock</span></span>

<span data-ttu-id="f6e5f-339">Blokuje klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-339">Locks the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-340">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-340">Prototype</span></span>

```c
UINT **nx_lwm2m_client_lock**(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-341">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-341">Description</span></span>

<span data-ttu-id="f6e5f-342">Ta usługa blokuje klienta LWM2M, aby zapobiec współbieżnemu dostępowi do obiektów LWM2M z serwerów lub z innego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-342">This service locks the LWM2M Client to prevent concurrent access to the LWM2M objects from the servers or another application thread.</span></span>

<span data-ttu-id="f6e5f-343">Jeśli klient LWM2M jest obecnie zablokowany przez inny wątek, funkcja zostanie Zablokowani do momentu odblokowania klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-343">If the LWM2M Client is currently locked by another thread, the function will block until the LWM2M Client is unlocked.</span></span>

<span data-ttu-id="f6e5f-344">Wywołania ***nx_lwm2m_client_lock** _/_ *_nx_lwm2m_client_unlock_** par mogą być zagnieżdżane.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-344">Calls to \***nx_lwm2m_client_lock**_/_*_nx_lwm2m_client_unlock_*\* pairs can be nested.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-345">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-345">Parameters</span></span>

- <span data-ttu-id="f6e5f-346">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-346">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-347">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-347">Return Values</span></span>

- <span data-ttu-id="f6e5f-348">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-348">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-349">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-349">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-350">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-350">Allowed From</span></span>

<span data-ttu-id="f6e5f-351">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-351">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-352">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-352">Example</span></span>

```c
/* Lock the LWM2M client.  */
status = nx_lwm2m_client_lock(&lwm2m_client);

/* If status is NX_SUCCESS, lwm2m client was successfully locked.  */
```

## <a name="nx_lwm2m_client_object_add"></a><span data-ttu-id="f6e5f-353">nx_lwm2m_client_object_add</span><span class="sxs-lookup"><span data-stu-id="f6e5f-353">nx_lwm2m_client_object_add</span></span>

<span data-ttu-id="f6e5f-354">Dodaje implementację obiektu do klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-354">Adds an Object implementation to the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-355">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-355">Prototype</span></span>

```c
UINT **nx_lwm2m_client_object_add**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK object_operation);
```

### <a name="description"></a><span data-ttu-id="f6e5f-356">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-356">Description</span></span>

<span data-ttu-id="f6e5f-357">Ta usługa dodaje nową implementację obiektu do klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-357">This service adds a new Object implementation to the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-358">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-358">Parameters</span></span>

- <span data-ttu-id="f6e5f-359">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-359">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-360">**object_ptr** Wskaźnik do struktury definiującej implementację obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-360">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="f6e5f-361">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-361">**object_id** The object id.</span></span>
- <span data-ttu-id="f6e5f-362">**object_operation** Funkcja wywołania zwrotnego operacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-362">**object_operation** The object operation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-363">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-363">Return Values</span></span>

- <span data-ttu-id="f6e5f-364">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-364">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-365">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="f6e5f-366">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-366">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-367">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-367">Allowed From</span></span>

<span data-ttu-id="f6e5f-368">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-368">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-369">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-369">Example</span></span>

```c
/* Add new object to the lwm2m client.  */
status = nx_lwm2m_client_object_add(&lwm2m_client, &object, 
                                    3303, object_operation);

/* If status is NX_SUCCESS, the new object was successfully added.  */
```

## <a name="nx_lwm2m_client_object_create"></a><span data-ttu-id="f6e5f-370">nx_lwm2m_client_object_create</span><span class="sxs-lookup"><span data-stu-id="f6e5f-370">nx_lwm2m_client_object_create</span></span>

<span data-ttu-id="f6e5f-371">Tworzy nowe wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-371">Creates a new Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-372">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-372">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_create(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-373">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-373">Description</span></span>

<span data-ttu-id="f6e5f-374">Ta usługa wykonuje operację "Create" na obiekcie klienta LWM2M, aby utworzyć nowe wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-374">This service performs a ‘Create’ operation on an Object of the LWM2M Client to create a new Object Instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-375">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-375">Parameters</span></span>

- <span data-ttu-id="f6e5f-376">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-376">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-377">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-377">**object_id** The Object ID.</span></span>
- <span data-ttu-id="f6e5f-378">**instance_id_ptr** Wskaźnik na identyfikator nowego wystąpienia może mieć **wartość null** , jeśli klient LWM2M musi przypisać identyfikator wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-378">**instance_id_ptr** Pointer to the ID of the new instance, can be **NULL** if the LWM2M Client must assign an Instance ID.</span></span> <span data-ttu-id="f6e5f-379">Jeśli identyfikator jest wartością zarezerwowaną 65535, klient LWM2M przypisze identyfikator wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-379">If the ID is the reserved value 65535 the LWM2M Client will assign an Instance ID.</span></span> <span data-ttu-id="f6e5f-380">Jeśli wartość nie jest równa NULL, przypisany identyfikator jest zwracany po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-380">If not NULL the assigned ID is returned after the call.</span></span>
- <span data-ttu-id="f6e5f-381">**num_values** Liczba wartości do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-381">**num_values** The number of values to set.</span></span>
- <span data-ttu-id="f6e5f-382">**values_ptr** Wskaźnik na tablicę wartości zasobów, aby zainicjować nowe wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-382">**values_ptr** Pointer to an array of resource values to initialize the new Object Instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-383">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-383">Return Values</span></span>

- <span data-ttu-id="f6e5f-384">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-384">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator wystąpienia obiektu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-385">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object Instance ID already exists.</span></span>
- <span data-ttu-id="f6e5f-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Obiekt nie obsługuje tworzenia wystąpień.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-386">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance creation.</span></span>
- <span data-ttu-id="f6e5f-387">**NX_LWM2M_CLIENT_NO_MEMORY** Nie można przydzielić pamięci do zapisania nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-387">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store the new instance.</span></span>
- <span data-ttu-id="f6e5f-388">**NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-388">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID doesn’t exist.</span></span>
- <span data-ttu-id="f6e5f-389">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-389">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-390">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-390">Allowed From</span></span>

<span data-ttu-id="f6e5f-391">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-391">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-392">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-392">Example</span></span>

```c
/* Create new object instance.  */
status = nx_lwm2m_client_object_create(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, a new object instance was successfully created.  */
```

## <a name="nx_lwm2m_client_object_delete"></a><span data-ttu-id="f6e5f-393">nx_lwm2m_client_object_delete</span><span class="sxs-lookup"><span data-stu-id="f6e5f-393">nx_lwm2m_client_object_delete</span></span>

<span data-ttu-id="f6e5f-394">Usuwa wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-394">Deletes an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-395">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-395">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_delete(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="f6e5f-396">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-396">Description</span></span>

<span data-ttu-id="f6e5f-397">Ta usługa wykonuje operację "Delete" na wystąpieniu obiektu klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-397">This service performs a ‘Delete’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-398">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-398">Parameters</span></span>

- <span data-ttu-id="f6e5f-399">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-399">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-400">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-400">**object_id** The Object ID.</span></span>
- <span data-ttu-id="f6e5f-401">**instance_ID** Identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-401">**instance_id** The Object Instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-402">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-402">Return Values</span></span>

- <span data-ttu-id="f6e5f-403">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-403">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Obiekt nie obsługuje usuwania wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-404">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** The Object doesn’t support instance deletion.</span></span>
- <span data-ttu-id="f6e5f-405">**NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-405">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="f6e5f-406">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-406">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-407">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-407">Allowed From</span></span>

<span data-ttu-id="f6e5f-408">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-408">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-409">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-409">Example</span></span>

```c
/* Delete an object instance.  */
status = nx_lwm2m_client_object_delete(&lwm2m_client, 3303, 0);

/* If status is NX_SUCCESS, an object instance was successfully deleted.  */
```

## <a name="nx_lwm2m_client_object_discover"></a><span data-ttu-id="f6e5f-410">nx_lwm2m_client_object_discover</span><span class="sxs-lookup"><span data-stu-id="f6e5f-410">nx_lwm2m_client_object_discover</span></span>

<span data-ttu-id="f6e5f-411">Odnajduje zasoby wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-411">Discovers resources of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-412">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-412">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_discover(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT *num_resources,
    NX_LWM2M_CLIENT_RESOURCE *resources);

```

### <a name="description"></a><span data-ttu-id="f6e5f-413">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-413">Description</span></span>

<span data-ttu-id="f6e5f-414">Ta usługa wykonuje operację "Discover" na wystąpieniu obiektu klienta LWM2M, która zwraca listę zasobów implementowanych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-414">This service performs a ‘Discover’ operation on an Object Instance of the LWM2M Client, this returns the list of resources implemented by the Object.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-415">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-415">Parameters</span></span>

- <span data-ttu-id="f6e5f-416">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-416">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-417">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-417">**object_id** The Object ID.</span></span>
- <span data-ttu-id="f6e5f-418">**instance_ID** Identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-418">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="f6e5f-419">**num_resources** Przy wprowadzaniu rozmiaru buforu docelowego w danych wyjściowych liczba elementów zapisywana w buforze.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-419">**num_resources** On input the size of the destination buffer, on output the number of elements written to the buffer.</span></span>
- <span data-ttu-id="f6e5f-420">**zasoby** Wskaźnik do bufora docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-420">**resources** Pointer to the destination buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-421">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-421">Return Values</span></span>

- <span data-ttu-id="f6e5f-422">*NX_SUCCESS*\* operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-422">*NX_SUCCESS*\* Successful operation.</span></span>
- <span data-ttu-id="f6e5f-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Bufor zasobów jest za mały, aby można było przechowywać listę zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-423">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="f6e5f-424">**NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-424">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="f6e5f-425">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-425">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-426">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-426">Allowed From</span></span>

<span data-ttu-id="f6e5f-427">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-427">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-428">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-428">Example</span></span>

```c
NX_LWM2M_CLIENT_RESOURCE resources[10]
UINT num_resources = 10;

/* Discover object resources.  */
status = nx_lwm2m_client_object_discover(&lwm2m_client, 3303, 0, 
                                         &num_resources, resource);

/* If status is NX_SUCCESS, discover object resources successfully.  */
```

## <a name="nx_lwm2m_client_object_execute"></a><span data-ttu-id="f6e5f-429">nx_lwm2m_client_object_execute</span><span class="sxs-lookup"><span data-stu-id="f6e5f-429">nx_lwm2m_client_object_execute</span></span>

<span data-ttu-id="f6e5f-430">Wykonuje operację "Execute" na zasobie wystąpienia obiektu Object.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-430">Performs an 'Execute' operation on a resource of an Object Instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-431">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-431">Prototype</span></span>

```C
UINT **nx_lwm2m_client_object_execute**(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr,
    UINT arguments_length);
```

### <a name="description"></a><span data-ttu-id="f6e5f-432">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-432">Description</span></span>

<span data-ttu-id="f6e5f-433">Ta usługa wykonuje operację "Execute" na zasobie wystąpienia obiektu klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-433">This service performs the ‘Execute’ operation on an Object Instance Resource of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-434">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-434">Parameters</span></span>

- <span data-ttu-id="f6e5f-435">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-435">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-436">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-436">**object_id** The Object ID.</span></span>
- <span data-ttu-id="f6e5f-437">**instance_ID** Identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-437">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="f6e5f-438">**resource_id** Identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-438">**resource_id** The Resource ID.</span></span>
- <span data-ttu-id="f6e5f-439">**arguments_ptr** Wskaźnik do argumentów operacji Execute.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-439">**arguments_ptr** Pointer to the arguments of the execute operation.</span></span> <span data-ttu-id="f6e5f-440">Może mieć wartość NULL, jeśli arguments_length wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-440">Can be NULL if arguments_length is zero.</span></span>
- <span data-ttu-id="f6e5f-441">**arguments_length** Długość argumentów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-441">**arguments_length** The length of the arguments.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-442">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-442">Return Values</span></span>

- <span data-ttu-id="f6e5f-443">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-443">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Bufor zasobów jest za mały, aby można było przechowywać listę zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-444">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The resources buffer is too small to store the list of resources.</span></span>
- <span data-ttu-id="f6e5f-445">**NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu lub identyfikator wystąpienia obiektu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-445">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID or Object Instance ID doesn’t exist.</span></span>
- <span data-ttu-id="f6e5f-446">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-446">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-447">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-447">Allowed From</span></span>

<span data-ttu-id="f6e5f-448">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-448">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-449">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-449">Example</span></span>

```c
/* Execute object resource.  */
status = nx_lwm2m_client_object_execute (&lwm2m_client, 3303, 0, 0,  
                                         “5”, 1);

/* If status is NX_SUCCESS, an object resource was successfully executed.  */
```

## <a name="nx_lwm2m_client_object_instance_add"></a><span data-ttu-id="f6e5f-450">nx_lwm2m_client_object_instance_add</span><span class="sxs-lookup"><span data-stu-id="f6e5f-450">nx_lwm2m_client_object_instance_add</span></span>

<span data-ttu-id="f6e5f-451">Dodaje implementację wystąpienia obiektu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-451">Adds an Object instance implementation to an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-452">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-452">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_add(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-453">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-453">Description</span></span>

<span data-ttu-id="f6e5f-454">Ta usługa dodaje nową implementację wystąpienia obiektu do klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-454">This service adds a new Object instance implementation to the LWM2M Client.</span></span> <span data-ttu-id="f6e5f-455">Jeśli wartość instance_id_ptr jest **NX_LWM2M_CLIENT_RESERVED_ID**, klient LWM2M automatycznie przypisze nieużywany identyfikator wystąpienia, w przeciwnym razie klient LWM2M będzie używał zestawu aplikacji wartości.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-455">If the value of instance_id_ptr is **NX_LWM2M_CLIENT_RESERVED_ID**, LWM2M Client will automatically assign an unused instance id, otherwise, LWM2M Client will use the value application set.</span></span> <span data-ttu-id="f6e5f-456">Po pomyślnym dodaniu nowego wystąpienia instance_id zostanie wypełnione instance_id_ptr, aby powrócić do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-456">Once new instance was added successfully, the instance_id will be filled in instance_id_ptr to return to application.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-457">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-457">Parameters</span></span>

- <span data-ttu-id="f6e5f-458">**object_ptr** Wskaźnik do struktury definiującej implementację obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-458">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="f6e5f-459">**instance_ptr** Wskaźnik do struktury definiującej implementację wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-459">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="f6e5f-460">**instance_id_ptr** Wskaźnik na identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-460">**instance_id_ptr** Pointer to the object instance id.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-461">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-461">Return Values</span></span>

- <span data-ttu-id="f6e5f-462">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-462">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** Identyfikator obiektu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-463">**NX_CLIENT_LWM2M_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="f6e5f-464">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-464">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-465">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-465">Allowed From</span></span>

<span data-ttu-id="f6e5f-466">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-466">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-467">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-467">Example</span></span>

```c
/* Add new object instance to the object.  */
status = nx_lwm2m_client_object_instance_add(&object, &object_instance,
                                             &instance_id);

/* If status is NX_SUCCESS, the new object instance was successfully added.  */
```

## <a name="nx_lwm2m_client_object_instance_next_get"></a><span data-ttu-id="f6e5f-468">nx_lwm2m_client_object_instance_next_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-468">nx_lwm2m_client_object_instance_next_get</span></span>

<span data-ttu-id="f6e5f-469">Pobiera następne wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-469">Gets the next instance of an Object.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-470">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-470">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID *instance_id_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-471">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-471">Description</span></span>

<span data-ttu-id="f6e5f-472">Ta usługa zwraca identyfikator następnego wystąpienia obiektu danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-472">This service returns the ID of the next Object Instance of the given Object.</span></span> <span data-ttu-id="f6e5f-473">Jeśli bieżący identyfikator wystąpienia ma wartość NX_LWM2M_RESERVED_ID (65535) zwracany jest identyfikator pierwszego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-473">If the current Instance ID is set to NX_LWM2M_RESERVED_ID (65535) the ID of the first instance is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-474">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-474">Parameters</span></span>

- <span data-ttu-id="f6e5f-475">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-475">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-476">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-476">**object_id** The Object ID.</span></span>
- <span data-ttu-id="f6e5f-477">**instance_id_ptr** Wskaźnik do bieżącego identyfikatora wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-477">**instance_id_ptr** Pointer to the current Object Instance ID.</span></span> <span data-ttu-id="f6e5f-478">On return zawiera identyfikator następnego wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-478">On return contains the next Instance ID of the Object.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-479">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-479">Return Values</span></span>

- <span data-ttu-id="f6e5f-480">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-480">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-481">**NX_CLIENT_LWM2M_NOT_FOUND** Dany identyfikator wystąpienia jest ostatnim obiektem lub identyfikator obiektu nie jest zaimplementowany.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-481">**NX_CLIENT_LWM2M_NOT_FOUND** The given Instance ID is the last of the object, or the Object ID is not implemented.</span></span>
- <span data-ttu-id="f6e5f-482">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-482">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-483">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-483">Allowed From</span></span>

<span data-ttu-id="f6e5f-484">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-484">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-485">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-485">Example</span></span>

```c
/* Get the next instance of an object.  */
status = nx_lwm2m_client_object_instance_next_get(&lwm2m_client, 3303, 
                                                  &instance_id);

/* If status is NX_SUCCESS, get the next instance successfully.  */
```

## <a name="nx_lwm2m_client_object_instance_remove"></a><span data-ttu-id="f6e5f-486">nx_lwm2m_client_object_instance_remove</span><span class="sxs-lookup"><span data-stu-id="f6e5f-486">nx_lwm2m_client_object_instance_remove</span></span>

<span data-ttu-id="f6e5f-487">Usuwa implementację wystąpienia obiektu z obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-487">Removes an  Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-488">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-488">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_instance_remove(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-489">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-489">Description</span></span>

<span data-ttu-id="f6e5f-490">Ta usługa usuwa wystąpienie obiektu z obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-490">This service removes an Object instance from an object.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-491">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-491">Parameters</span></span>

- <span data-ttu-id="f6e5f-492">***object_ptr*** Wskaźnik do struktury definiującej implementację obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-492">***object_ptr*** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="f6e5f-493">**instance_ptr** Wskaźnik do struktury definiującej implementację wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-493">**instance_ptr** Pointer to the structure defining the Object instance implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-494">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-494">Return Values</span></span>

- <span data-ttu-id="f6e5f-495">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-495">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-496">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="f6e5f-497">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-497">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-498">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-498">Allowed From</span></span>

<span data-ttu-id="f6e5f-499">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-499">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-500">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-500">Example</span></span>

```c
/* Remove object instance from an object.  */
status = nx_lwm2m_client_object_instance_remove(&object, &object_instance);

/* If status is NX_SUCCESS, the object instance was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_next_get"></a><span data-ttu-id="f6e5f-501">nx_lwm2m_client_object_next_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-501">nx_lwm2m_client_object_next_get</span></span>

<span data-ttu-id="f6e5f-502">Pobiera następny obiekt klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-502">Gets the next object of the LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-503">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-503">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_next_get(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID \*object_id_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-504">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-504">Description</span></span>

<span data-ttu-id="f6e5f-505">Ta usługa zwraca identyfikator następnego obiektu implementowanego przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-505">This service returns the ID of the next Object implemented by the LWM2M Client.</span></span> <span data-ttu-id="f6e5f-506">Jeśli bieżący identyfikator obiektu jest ustawiony na NX_LWM2M_RESERVED_ID (65535), zwracany jest pierwszy identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-506">If the current Object ID is set to NX_LWM2M_RESERVED_ID (65535) the first Object ID is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-507">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-507">Parameters</span></span>

- <span data-ttu-id="f6e5f-508">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-508">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-509">**object_id_ptr** Wskaźnik do bieżącego identyfikatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-509">**object_id_ptr** Pointer to the current Object ID.</span></span> <span data-ttu-id="f6e5f-510">On return zawiera następny identyfikator obiektu zaimplementowany przez klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-510">On return contains the next Object ID implemented by the LWM2M Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-511">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-511">Return Values</span></span>

- <span data-ttu-id="f6e5f-512">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-512">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-513">**NX_LWM2M_CLIENT_NOT_FOUND** Określony identyfikator obiektu jest ostatnim z baz danych.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-513">**NX_LWM2M_CLIENT_NOT_FOUND** The given Object ID is the last of the database.</span></span>
<span data-ttu-id="f6e5f-514">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-514">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-515">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-515">Allowed From</span></span>

<span data-ttu-id="f6e5f-516">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-516">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-517">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-517">Example</span></span>

```c
/* Get the next object of lwm2m client.  */
status = nx_lwm2m_client_object_next_get(&lwm2m_client, &object_id);

/* If status is NX_SUCCESS, get the next object successfully.  */
```

## <a name="nx_lwm2m_client_object_read"></a><span data-ttu-id="f6e5f-518">nx_lwm2m_client_object_read</span><span class="sxs-lookup"><span data-stu-id="f6e5f-518">nx_lwm2m_client_object_read</span></span>

<span data-ttu-id="f6e5f-519">Odczytuje wartości resource's wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-519">Reads an Object Instance's resource's values.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-520">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-520">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_read(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    NX_LWM2M_RESOURCE *values);
```

### <a name="description"></a><span data-ttu-id="f6e5f-521">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-521">Description</span></span>

<span data-ttu-id="f6e5f-522">Ta usługa wykonuje operację "read" na wystąpieniu obiektu klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-522">This service performs a ‘Read’ operation on an Object Instance of the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-523">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-523">Parameters</span></span>

- <span data-ttu-id="f6e5f-524">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-524">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-525">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-525">**object_id** The Object ID.</span></span>
- <span data-ttu-id="f6e5f-526">**instance_ID** Identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-526">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="f6e5f-527">**num_values** Liczba zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-527">**num_values** The number of resources to read.</span></span>
- <span data-ttu-id="f6e5f-528">**values_ptr** Wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-528">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources to read.</span></span> <span data-ttu-id="f6e5f-529">Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-529">On return the array is filled with the corresponding types and values.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-530">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-530">Return Values</span></span>

- <span data-ttu-id="f6e5f-531">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-531">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Zasób nie obsługuje operacji odczytu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-532">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the read operation.</span></span>
- <span data-ttu-id="f6e5f-533">**NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-533">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="f6e5f-534">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-534">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-535">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-535">Allowed From</span></span>

<span data-ttu-id="f6e5f-536">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-536">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-537">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-537">Example</span></span>

```c
/* Read the object resources.  */
status = nx_lwm2m_client_object_read(&lwm2m_client, 3303, 0, 2, &resource);

/* If status is NX_SUCCESS, the resources were successfully read.  */
```

## <a name="nx_lwm2m_client_object_remove"></a><span data-ttu-id="f6e5f-538">nx_lwm2m_client_object_remove</span><span class="sxs-lookup"><span data-stu-id="f6e5f-538">nx_lwm2m_client_object_remove</span></span>

<span data-ttu-id="f6e5f-539">Usuwa implementację wystąpienia obiektu z obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-539">Removes an Object instance implementation from an object.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-540">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-540">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_remove(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_OBJECT *object_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-541">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-541">Description</span></span>

<span data-ttu-id="f6e5f-542">Ta usługa usuwa obiekt z klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-542">This service removes an Object from the LWM2M Client.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-543">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-543">Parameters</span></span>

- <span data-ttu-id="f6e5f-544">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-544">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-545">**object_ptr** Wskaźnik do struktury definiującej implementację obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-545">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-546">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-546">Return Values</span></span>

- <span data-ttu-id="f6e5f-547">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-547">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** Identyfikator obiektu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-548">**NX_LWM2M_CLIENT_ALREADY_EXIST** The Object ID already exists.</span></span>
- <span data-ttu-id="f6e5f-549">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-549">**NX_PTR_ERROR** Invalid pointer.</span></span>
- <span data-ttu-id="f6e5f-550">**NX_LWM2M_CLIENT_FORBIDDEN** Usuwanie obiektu wewnętrznego jest zabronione.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-550">**NX_LWM2M_CLIENT_FORBIDDEN** Removing internal object is forbidden.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-551">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-551">Allowed From</span></span>

<span data-ttu-id="f6e5f-552">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-552">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-553">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-553">Example</span></span>

```c
/* Remove object from lwm2m client.  */
status = nx_lwm2m_client_object_remove(&lwm2m_client, &object);

/* If status is NX_SUCCESS, the object was successfully removed.  */
```

## <a name="nx_lwm2m_client_object_resource_changed"></a><span data-ttu-id="f6e5f-554">nx_lwm2m_client_object_resource_changed</span><span class="sxs-lookup"><span data-stu-id="f6e5f-554">nx_lwm2m_client_object_resource_changed</span></span>

<span data-ttu-id="f6e5f-555">Sygnalizuje zmianę zasobu obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-555">Signals a change of an Object resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-556">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-556">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_resource_changed(
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr,
    const NX_LWM2M_RESOURCE *resource);
```

### <a name="description"></a><span data-ttu-id="f6e5f-557">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-557">Description</span></span>

<span data-ttu-id="f6e5f-558">Usługa jest używana przez aplikację do sygnalizowania klienta LWM2M, że zasób obiektu został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-558">The service is used by the application to signal to the LWM2M Client that a resource of the Object has changed.</span></span> <span data-ttu-id="f6e5f-559">Klient LWM2M wyśle powiadomienie, jeśli zasób jest zaobserwowany przez serwer LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-559">The LWM2M Client will send a notification if the resource is observed by a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-560">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-560">Parameters</span></span>

- <span data-ttu-id="f6e5f-561">**object_ptr** Wskaźnik do struktury definiującej implementację obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-561">**object_ptr** Pointer to the structure defining the Object implementation.</span></span>
- <span data-ttu-id="f6e5f-562">***instance_ptr*** Wskaźnik do struktury definiującej implementację wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-562">***instance_ptr*** Pointer to the structure defining the Object instance implementation.</span></span>
- <span data-ttu-id="f6e5f-563">**zasób** Wskaźnik do struktury opisującej zasób, który został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-563">**resource** Pointer to the structure describing the resource that has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-564">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-564">Return Values</span></span>

- <span data-ttu-id="f6e5f-565">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-565">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-566">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-566">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-567">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-567">Allowed From</span></span>

<span data-ttu-id="f6e5f-568">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-568">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-569">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-569">Example</span></span>

```c
/* Change object resource.  */
status = nx_lwm2m_client_object_resource_changed(&object, &instance, &resource);

/* If status is NX_SUCCESS, a resource was successfully changed.  */
```

## <a name="nx_lwm2m_client_object_write"></a><span data-ttu-id="f6e5f-570">nx_lwm2m_client_object_write</span><span class="sxs-lookup"><span data-stu-id="f6e5f-570">nx_lwm2m_client_object_write</span></span>

<span data-ttu-id="f6e5f-571">Zmienia wartości zasobu wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-571">Changes resource's values of an Object instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-572">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-572">Prototype</span></span>

```c
UINT nx_lwm2m_client_object_write(
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_ID object_id,
    NX_LWM2M_ID instance_id,
    UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr,
    UINT write_op);
```

### <a name="description"></a><span data-ttu-id="f6e5f-573">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-573">Description</span></span>

<span data-ttu-id="f6e5f-574">Ta usługa wykonuje operację "Write" na wystąpieniu obiektu klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-574">This service performs a ‘Write’ operation on an Object Instance of the LWM2M Client.</span></span>

<span data-ttu-id="f6e5f-575">Do parametru *write_op* można określić następujące operacje zapisu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-575">The following write operations can be specified to the *write_op* parameter.</span></span>

| <span data-ttu-id="f6e5f-576">Wartość</span><span class="sxs-lookup"><span data-stu-id="f6e5f-576">Value</span></span> | <span data-ttu-id="f6e5f-577">&nbsp;Operacja zapisu</span><span class="sxs-lookup"><span data-stu-id="f6e5f-577">Write&nbsp;Operation</span></span> | <span data-ttu-id="f6e5f-578">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-578">Description</span></span> |
| --- | ---| --- |
| <span data-ttu-id="f6e5f-579">0</span><span class="sxs-lookup"><span data-stu-id="f6e5f-579">0</span></span> | <span data-ttu-id="f6e5f-580">Aktualizacja częściowa</span><span class="sxs-lookup"><span data-stu-id="f6e5f-580">Partial Update</span></span> | <span data-ttu-id="f6e5f-581">Dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-581">Adds or updates Resources provided in the new value and leaves other existing Resources unchanged.</span></span> |
| <span data-ttu-id="f6e5f-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-582">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE**</span></span> | <span data-ttu-id="f6e5f-583">Zamień wystąpienie</span><span class="sxs-lookup"><span data-stu-id="f6e5f-583">Replace Instance</span></span> | <span data-ttu-id="f6e5f-584">Zamienia wystąpienie obiektu na nowe podane wartości zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-584">Replaces the Object Instance with the new provided resource values.</span></span> |
| <span data-ttu-id="f6e5f-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-585">**NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE**</span></span> | <span data-ttu-id="f6e5f-586">Zastąp zasób</span><span class="sxs-lookup"><span data-stu-id="f6e5f-586">Replace Resource</span></span> | <span data-ttu-id="f6e5f-587">Zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów).</span><span class="sxs-lookup"><span data-stu-id="f6e5f-587">Replaces the Resources with the new provided resource values (used to replace Multiple Resources).</span></span> |
| <span data-ttu-id="f6e5f-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-588">**NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP**</span></span> | <span data-ttu-id="f6e5f-589">Zapis ładowania początkowego</span><span class="sxs-lookup"><span data-stu-id="f6e5f-589">Bootstrap Write</span></span> | <span data-ttu-id="f6e5f-590">Wskazuje wywołanie z sekwencji ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-590">Indicates a call from a Bootstrap sequence.</span></span> |

### <a name="parameters"></a><span data-ttu-id="f6e5f-591">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-591">Parameters</span></span>

- <span data-ttu-id="f6e5f-592">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-592">**client_ptr** Pointer to LWM2M Client control block.</span></span>
- <span data-ttu-id="f6e5f-593">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-593">**object_id** The Object ID.</span></span>
- <span data-ttu-id="f6e5f-594">**instance_ID** Identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-594">**instance_id** The Object Instance ID.</span></span>
- <span data-ttu-id="f6e5f-595">**num_values** Liczba zasobów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-595">**num_values** The number of resources to write.</span></span>
- <span data-ttu-id="f6e5f-596">**values_ptr** Wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów, typy i wartości do zapisania.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-596">**values_ptr** Pointer to an array of NX_LWM2M_RESOURCE containing the IDs of the resources, the types and the values to write.</span></span>
- <span data-ttu-id="f6e5f-597">**write_op** Typ operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-597">**write_op** The type of write operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-598">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-598">Return Values</span></span>

- <span data-ttu-id="f6e5f-599">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-599">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-600">**NX_LWM2M_CLIENT_BAD_ENCODING** Typ zasobu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-600">**NX_LWM2M_CLIENT_BAD_ENCODING** The type of a resource is not valid.</span></span>
- <span data-ttu-id="f6e5f-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** Długość wartości jest zbyt duża, aby można było ją zapisać w wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-601">**NX_LWM2M_CLIENT_BUFFER_TOO_SMALL** The length of a value is too big to be stored in the instance.</span></span>
- <span data-ttu-id="f6e5f-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** Zasób nie obsługuje operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-602">**NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** A resource doesn’t support the write operation.</span></span>
- <span data-ttu-id="f6e5f-603">**NX_LWM2M_CLIENT_NO_MEMORY** Nie można przydzielić pamięci do przechowywania wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-603">**NX_LWM2M_CLIENT_NO_MEMORY** Cannot allocate memory to store a resource value.</span></span>
- <span data-ttu-id="f6e5f-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** Wartość zasobu jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-604">**NX_LWM2M_CLIENT_NOT_ACCEPTABLE** The value of a resource is not valid.</span></span>
- <span data-ttu-id="f6e5f-605">**NX_LWM2M_CLIENT_NOT_FOUND** Identyfikator obiektu, identyfikator wystąpienia obiektu lub identyfikator zasobu nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-605">**NX_LWM2M_CLIENT_NOT_FOUND** The Object ID, Object Instance ID or a resource ID doesn’t exist.</span></span>
- <span data-ttu-id="f6e5f-606">**NX_OPTION_ERROR** Nieprawidłowy typ operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-606">**NX_OPTION_ERROR** Invalid type of write operation.</span></span> 
- <span data-ttu-id="f6e5f-607">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-607">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-608">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-608">Allowed From</span></span>

<span data-ttu-id="f6e5f-609">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-609">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-610">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-610">Example</span></span>

```c
/* Write object resources.  */
status = nx_lwm2m_client_object_write(&lwm2m_client, 3303, 0, 2, &resource,
                                      NX_LWM2M_CLIENT_OBJECT_WRITE_UPDATE);

/* If status is NX_SUCCESS, write object resources successfully.  */
```

## <a name="nx_lwm2m_client_resource_boolean_get"></a><span data-ttu-id="f6e5f-611">nx_lwm2m_client_resource_boolean_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-611">nx_lwm2m_client_resource_boolean_get</span></span>

<span data-ttu-id="f6e5f-612">Pobiera wartość zasobu logicznego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-612">Gets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-613">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-613">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL *bool_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-614">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-614">Description</span></span>

<span data-ttu-id="f6e5f-615">Usługa Pobiera wartość zasobu logicznego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-615">The service retrieves the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-616">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-616">Parameters</span></span>

- <span data-ttu-id="f6e5f-617">**zasób** Wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-617">**resource** Pointer to Resource value description.</span></span>
- <span data-ttu-id="f6e5f-618">**bool_ptr** Wskaźnik do docelowej wartości logicznej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-618">**bool_ptr** Pointer to the destination Boolean value.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-619">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-619">Return Values</span></span>

- <span data-ttu-id="f6e5f-620">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-620">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-621">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-621">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="f6e5f-622">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-622">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-623">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-623">Allowed From</span></span>

<span data-ttu-id="f6e5f-624">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-624">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-625">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-625">Example</span></span>

```c
/* Get the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_get(&resource, &bool);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_boolean_set"></a><span data-ttu-id="f6e5f-626">nx_lwm2m_client_resource_boolean_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-626">nx_lwm2m_client_resource_boolean_set</span></span>

<span data-ttu-id="f6e5f-627">Ustawia wartość zasobu logicznego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-627">Sets the value of a Boolean Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-628">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-628">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_boolean_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_BOOL bool_data);
```

### <a name="description"></a><span data-ttu-id="f6e5f-629">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-629">Description</span></span>

<span data-ttu-id="f6e5f-630">Usługa ustawia wartość zasobu logicznego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-630">The service sets the value of a Boolean Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-631">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-631">Parameters</span></span>

- <span data-ttu-id="f6e5f-632">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-632">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-633">**bool_data** Dane logiczne.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-633">**bool_data** Boolean data.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-634">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-634">Return Values</span></span>

- <span data-ttu-id="f6e5f-635">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-635">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-636">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-636">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-637">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-637">Allowed From</span></span>

<span data-ttu-id="f6e5f-638">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-638">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-639">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-639">Example</span></span>

```c
/* Set the value of a Boolean resource.  */
status = nx_lwm2m_client_resource_boolean_set(&resource, NX_TRUE);

/* If status is NX_SUCCESS, the value of Boolean resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_dim_get"></a><span data-ttu-id="f6e5f-640">nx_lwm2m_client_resource_dim_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-640">nx_lwm2m_client_resource_dim_get</span></span>

<span data-ttu-id="f6e5f-641">Pobiera wymiar zasobu dla wielu zasobów</span><span class="sxs-lookup"><span data-stu-id="f6e5f-641">Gets the resource dimension for multiple Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-642">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-642">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    UCHAR *dim);
```

### <a name="description"></a><span data-ttu-id="f6e5f-643">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-643">Description</span></span>

<span data-ttu-id="f6e5f-644">Usługa pobiera wymiar zasobu dla wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-644">The service retrieves the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-645">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-645">Parameters</span></span>

- <span data-ttu-id="f6e5f-646">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-646">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-647">**Przyciemnij** wskaźnik do wymiaru docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-647">**dim** Pointer to the destination dimension.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-648">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-648">Return Values</span></span>

- <span data-ttu-id="f6e5f-649">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-649">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-650">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-650">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="f6e5f-651">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-651">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-652">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-652">Allowed From</span></span>

<span data-ttu-id="f6e5f-653">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-654">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-654">Example</span></span>

```c
/* Get the resource dimension for multiple resource.  */
status = nx_lwm2m_client_resource_dim_get(&resource, &dim);

/* If status is NX_SUCCESS, the resource dimension was successfully get. */
```

## <a name="nx_lwm2m_client_resource_dim_set"></a><span data-ttu-id="f6e5f-655">nx_lwm2m_client_resource_dim_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-655">nx_lwm2m_client_resource_dim_set</span></span>

<span data-ttu-id="f6e5f-656">Ustawia wymiar zasobu dla wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-656">Sets the resource dimension for multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-657">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-657">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_dim_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR dim);
```

### <a name="description"></a><span data-ttu-id="f6e5f-658">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-658">Description</span></span>

<span data-ttu-id="f6e5f-659">Usługa ustawia wymiar zasobu dla wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-659">The service sets the resource dimension for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-660">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-660">Parameters</span></span>

- <span data-ttu-id="f6e5f-661">**wartość** Wskaźnik do opisu wartości zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-661">**value** Pointer to Resource value description.</span></span>
- <span data-ttu-id="f6e5f-662">wartość wymiaru **Dim** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-662">**dim** Dimension value.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-663">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-663">Return Values</span></span>

- <span data-ttu-id="f6e5f-664">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-664">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-665">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-665">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-666">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-666">Allowed From</span></span>

<span data-ttu-id="f6e5f-667">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-667">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-668">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-668">Example</span></span>

```c
/* Set the resource dimension.  */
status = nx_lwm2m_client_resource_dim_set(&resource, 3);

/* If status is NX_SUCCESS, the resource dimension was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float32_get"></a><span data-ttu-id="f6e5f-669">nx_lwm2m_client_resource_float32_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-669">nx_lwm2m_client_resource_float32_get</span></span>

<span data-ttu-id="f6e5f-670">Pobiera wartość 32-bitowego zasobu **zmiennoprzecinkowego**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-670">Gets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-671">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-671">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 *float32_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-672">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-672">Description</span></span>

<span data-ttu-id="f6e5f-673">Usługa Pobiera wartość 32-bitowego zasobu **zmiennoprzecinkowego** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-673">The service retrieves the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-674">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-674">Parameters</span></span>

- <span data-ttu-id="f6e5f-675">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-675">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-676">**float32_ptr** Wskaźnik do docelowej 32-bitowej wartości **zmiennoprzecinkowej** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-676">**float32_ptr** Pointer to the destination 32-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-677">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-677">Return Values</span></span>

- <span data-ttu-id="f6e5f-678">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-678">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-679">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-679">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="f6e5f-680">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-680">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-681">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-681">Allowed From</span></span>

<span data-ttu-id="f6e5f-682">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-682">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-683">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-683">Example</span></span>

```C
/* Get the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_get(&resource, &float32);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float32_set"></a><span data-ttu-id="f6e5f-684">nx_lwm2m_client_resource_float32_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-684">nx_lwm2m_client_resource_float32_set</span></span>

<span data-ttu-id="f6e5f-685">Ustawia wartość 32-bitowego zasobu **zmiennoprzecinkowego**</span><span class="sxs-lookup"><span data-stu-id="f6e5f-685">Sets the value of a 32-Bit **float** Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-686">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-686">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_float32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource,
    NX_LWM2M_FLOAT32 float32_data);
```

### <a name="description"></a><span data-ttu-id="f6e5f-687">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-687">Description</span></span>

<span data-ttu-id="f6e5f-688">Usługa ustawia wartość 32-bitowego zasobu **zmiennoprzecinkowego** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-688">The service sets the value of a 32-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-689">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-689">Parameters</span></span>

- <span data-ttu-id="f6e5f-690">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-690">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-691">**float32_data** 32-bitowe dane **zmiennoprzecinkowe** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-691">**float32_data** 32-Bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-692">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-692">Return Values</span></span>

- <span data-ttu-id="f6e5f-693">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-693">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-694">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-694">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-695">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-695">Allowed From</span></span>

<span data-ttu-id="f6e5f-696">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-696">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-697">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-697">Example</span></span>

```c
/* Set the value of a 32-Bit float resource.  */
status = nx_lwm2m_client_resource_float32_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 32-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_float64_get"></a><span data-ttu-id="f6e5f-698">nx_lwm2m_client_resource_float64_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-698">nx_lwm2m_client_resource_float64_get</span></span>

<span data-ttu-id="f6e5f-699">Pobiera wartość 64-bitowego zasobu zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-699">Gets the value of a 64-Bit float Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-700">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-700">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 *float64_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-701">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-701">Description</span></span>

<span data-ttu-id="f6e5f-702">Usługa Pobiera wartość 64-bitowego zasobu **zmiennoprzecinkowego** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-702">The service retrieves the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-703">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-703">Parameters</span></span>

- <span data-ttu-id="f6e5f-704">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-704">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-705">**float64_ptr** Wskaźnik do docelowej 64-bitowej wartości **zmiennoprzecinkowej** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-705">**float64_ptr** Pointer to the destination 64-Bit **float** value.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-706">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-706">Return Values</span></span>

- <span data-ttu-id="f6e5f-707">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-707">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-708">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-708">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a float value.</span></span>
- <span data-ttu-id="f6e5f-709">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-709">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-710">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-710">Allowed From</span></span>

<span data-ttu-id="f6e5f-711">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-711">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-712">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-712">Example</span></span>

```c
/* Get the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_get(&resource, &float64);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_float64_set"></a><span data-ttu-id="f6e5f-713">nx_lwm2m_client_resource_float64_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-713">nx_lwm2m_client_resource_float64_set</span></span>

<span data-ttu-id="f6e5f-714">Ustawia wartość 64-bitowego zasobu **zmiennoprzecinkowego** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-714">Sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-715">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-715">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_float64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="f6e5f-716">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-716">Description</span></span>

<span data-ttu-id="f6e5f-717">Usługa ustawia wartość 64-bitowego zasobu **zmiennoprzecinkowego** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-717">The service sets the value of a 64-Bit **float** Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-718">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-718">Parameters</span></span>

- <span data-ttu-id="f6e5f-719">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-719">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-720">**float64_data** 64-bitowe dane **zmiennoprzecinkowe** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-720">**float64_data** 64-bit **float** data.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-721">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-721">Return Values</span></span>

- <span data-ttu-id="f6e5f-722">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-722">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-723">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-723">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-724">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-724">Allowed From</span></span>

<span data-ttu-id="f6e5f-725">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-725">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-726">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-726">Example</span></span>

```c
/* Set the value of a 64-Bit float resource.  */
status = nx_lwm2m_client_resource_float64_set(&resource, 1.24);

/* If status is NX_SUCCESS, the value of 64-Bit float resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_info_get"></a><span data-ttu-id="f6e5f-727">nx_lwm2m_client_resource_info_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-727">nx_lwm2m_client_resource_info_get</span></span>

<span data-ttu-id="f6e5f-728">Pobiera informacje o zasobach.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-728">Gets the resource info.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-729">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-729">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_info_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *resource_id, 
    ULONG *operation);
```

### <a name="description"></a><span data-ttu-id="f6e5f-730">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-730">Description</span></span>

<span data-ttu-id="f6e5f-731">Usługa pobiera informacje o zasobach.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-731">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-732">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-732">Parameters</span></span>

- <span data-ttu-id="f6e5f-733">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-733">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-734">**resource_id** Wskaźnik na identyfikator zasobu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-734">**resource_id** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="f6e5f-735">**operacja** Wskaźnik do operacji zasobu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-735">**operation** Pointer to the destination resource operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-736">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-736">Return Values</span></span>

- <span data-ttu-id="f6e5f-737">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-737">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-738">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-738">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-739">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-739">Allowed From</span></span>

<span data-ttu-id="f6e5f-740">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-740">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-741">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-741">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_info_get(&resource, &resource_id, &operation);

/* If status is NX_SUCCESS, the resource information was successfully get. */
```

## <a name="nx_lwm2m_client_resource_info_set"></a><span data-ttu-id="f6e5f-742">nx_lwm2m_client_resource_info_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-742">nx_lwm2m_client_resource_info_set</span></span>

<span data-ttu-id="f6e5f-743">Ustawia informacje o zasobach.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-743">Sets the resource information.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-744">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-744">Prototype</span></span>

```C
UINT nx_lwm2m_client_resource_info_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_FLOAT64 float64_data);
```

### <a name="description"></a><span data-ttu-id="f6e5f-745">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-745">Description</span></span>

<span data-ttu-id="f6e5f-746">Usługa ustawia informacje o zasobach.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-746">The service sets the resource information.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-747">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-747">Parameters</span></span>

- <span data-ttu-id="f6e5f-748">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-748">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-749">**resource_id** Identyfikator zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-749">**resource_id** ID of the resource.</span></span>
- <span data-ttu-id="f6e5f-750">**operacja** Operacja zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-750">**operation** Operation of the resource.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-751">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-751">Return Values</span></span>

- <span data-ttu-id="f6e5f-752">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-752">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-753">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-753">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-754">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-754">Allowed From</span></span>

<span data-ttu-id="f6e5f-755">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-755">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-756">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-756">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_info_set(&resource, 0, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

/* If status is NX_SUCCESS, the resource information was successfully set. */
```

## <a name="nx_lwm2m_client_resource_instances_get"></a><span data-ttu-id="f6e5f-757">nx_lwm2m_client_resource_instances_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-757">nx_lwm2m_client_resource_instances_get</span></span>

<span data-ttu-id="f6e5f-758">Pobiera wystąpienie wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-758">Gets the instance of multiple resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-759">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-759">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT *count);
```

### <a name="description"></a><span data-ttu-id="f6e5f-760">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-760">Description</span></span>

<span data-ttu-id="f6e5f-761">Usługa pobiera informacje o zasobach.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-761">The service retrieves the resource information of Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-762">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-762">Parameters</span></span>

- <span data-ttu-id="f6e5f-763">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-763">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-764">**resource_instances** Wskaźnik na identyfikator zasobu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-764">**resource_instances** Pointer to the destination resource ID.</span></span>
- <span data-ttu-id="f6e5f-765">**Liczba** Wskaźnik do liczby.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-765">**count** Pointer to the count.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-766">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-766">Return Values</span></span>

- <span data-ttu-id="f6e5f-767">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-767">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-768">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością logiczną.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-768">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a Boolean value.</span></span>
- <span data-ttu-id="f6e5f-769">**NX_LWM2M_CLIENT_NO_MEMORY** Brak pamięci do wypełniania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-769">**NX_LWM2M_CLIENT_NO_MEMORY** No memory to fill out instances.</span></span>
- <span data-ttu-id="f6e5f-770">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-770">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-771">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-771">Allowed From</span></span>

<span data-ttu-id="f6e5f-772">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-772">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-773">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-773">Example</span></span>

```c
/* Get the resource information.  */
status = nx_lwm2m_client_resource_instances_get(&resource, &resource_instances,
                                                &count);

/* If status is NX_SUCCESS, the instances of multiple resource information were successfully get. */
```

## <a name="nx_lwm2m_client_resource_instances_set"></a><span data-ttu-id="f6e5f-774">nx_lwm2m_client_resource_instances_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-774">nx_lwm2m_client_resource_instances_set</span></span>

<span data-ttu-id="f6e5f-775">Ustawia wystąpienia zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-775">Sets the resource instances.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-776">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-776">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_instances_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_CLIENT_RESOURCE *resource_instances, 
    UINT count);
```
### <a name="description"></a><span data-ttu-id="f6e5f-777">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-777">Description</span></span>

<span data-ttu-id="f6e5f-778">Usługa ustawia wystąpienia zasobów dla wielu zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-778">The service sets the resource instances for multiple resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-779">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-779">Parameters</span></span>

- <span data-ttu-id="f6e5f-780">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-780">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-781">**resource_instance** Wskaźnik do wystąpień zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-781">**resource_instance** Pointer to resource instances.</span></span>
- <span data-ttu-id="f6e5f-782">**Liczba** Liczba wystąpień zasobów.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-782">**count** Count of resource instances.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-783">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-783">Return Values</span></span>

- <span data-ttu-id="f6e5f-784">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-784">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-785">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-785">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-786">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-786">Allowed From</span></span>

<span data-ttu-id="f6e5f-787">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-787">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-788">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-788">Example</span></span>

```c
/* Set the resource information.  */
status = nx_lwm2m_client_resource_instances_set(&resource, &resource_instance, 2);

/* If status is NX_SUCCESS, the resource instances were successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer32_get"></a><span data-ttu-id="f6e5f-789">nx_lwm2m_client_resource_integer32_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-789">nx_lwm2m_client_resource_integer32_get</span></span>

<span data-ttu-id="f6e5f-790">Pobiera wartość 32-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-790">Gets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-791">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-791">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 *integer32_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-792">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-792">Description</span></span>

<span data-ttu-id="f6e5f-793">Usługa Pobiera wartość 32-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-793">The service retrieves the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-794">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-794">Parameters</span></span>

- <span data-ttu-id="f6e5f-795">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-795">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-796">**integer32_ptr** Wskaźnik na 32-bitową wartość całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-796">**integer32_ptr** Pointer to the 32-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-797">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-797">Return Values</span></span>

- <span data-ttu-id="f6e5f-798">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-798">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-799">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-799">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not integer value.</span></span>
- <span data-ttu-id="f6e5f-800">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-800">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-801">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-801">Allowed From</span></span>

<span data-ttu-id="f6e5f-802">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-802">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-803">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-803">Example</span></span>

```c
/* Get the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_get(&resource, &integer32);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer32_set"></a><span data-ttu-id="f6e5f-804">nx_lwm2m_client_resource_integer32_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-804">nx_lwm2m_client_resource_integer32_set</span></span>

<span data-ttu-id="f6e5f-805">Ustawia wartość 32-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-805">Sets the value of a 32-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-806">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-806">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer32_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER32 integer32_data);
```

### <a name="description"></a><span data-ttu-id="f6e5f-807">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-807">Description</span></span>

<span data-ttu-id="f6e5f-808">Usługa ustawia wartość 32-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-808">The service sets the value of a 32-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-809">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-809">Parameters</span></span>

- <span data-ttu-id="f6e5f-810">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-810">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-811">**integer32_data** 32-bitowe dane całkowite.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-811">**integer32_data** 32-Bit integer data.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-812">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-812">Return Values</span></span>

- <span data-ttu-id="f6e5f-813">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-813">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-814">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-814">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-815">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-815">Allowed From</span></span>

<span data-ttu-id="f6e5f-816">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-816">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-817">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-817">Example</span></span>

```c
/* Set the value of a 32-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer32_set(&resource, 8);

/* If status is NX_SUCCESS, the value of 32-Bit integer resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_integer64_get"></a><span data-ttu-id="f6e5f-818">nx_lwm2m_client_resource_integer64_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-818">nx_lwm2m_client_resource_integer64_get</span></span>

<span data-ttu-id="f6e5f-819">Pobiera wartość 64-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-819">Gets the value of a 64-Bit integer Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-820">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-820">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 *integer64_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-821">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-821">Description</span></span>

<span data-ttu-id="f6e5f-822">Usługa Pobiera wartość 64-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-822">The service retrieves the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-823">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-823">Parameters</span></span>

- <span data-ttu-id="f6e5f-824">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-824">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-825">**integer64_ptr** Wskaźnik na 64-bitową wartość całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-825">**integer64_ptr** Pointer to the 64-Bit integer value.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-826">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-826">Return Values</span></span>

- <span data-ttu-id="f6e5f-827">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-827">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-828">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest 64-bitową wartością całkowitą.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-828">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not 64-Bit integer value.</span></span>
- <span data-ttu-id="f6e5f-829">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-829">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-830">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-830">Allowed From</span></span>

<span data-ttu-id="f6e5f-831">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-831">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-832">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-832">Example</span></span>

```c
/* Get the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_get(&resource, &integer64);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_integer64_set"></a><span data-ttu-id="f6e5f-833">nx_lwm2m_client_resource_integer64_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-833">nx_lwm2m_client_resource_integer64_set</span></span>

## <a name="set-the-value-of-a-64-bit-integer-resource"></a><span data-ttu-id="f6e5f-834">Ustaw wartość 64-bitowego zasobu liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="f6e5f-834">Set the value of a 64-Bit integer Resource</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-835">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-835">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_integer64_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_INTEGER64 integer64_data);
```

### <a name="description"></a><span data-ttu-id="f6e5f-836">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-836">Description</span></span>

<span data-ttu-id="f6e5f-837">Usługa ustawia wartość 64-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-837">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-838">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-838">Parameters</span></span>

- <span data-ttu-id="f6e5f-839">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-839">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-840">**integer64_data** 64-bitowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-840">**integer64_data** 64-bit integer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-841">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-841">Return Values</span></span>

- <span data-ttu-id="f6e5f-842">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-842">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-843">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-843">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-844">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-844">Allowed From</span></span>

<span data-ttu-id="f6e5f-845">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-845">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-846">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-846">Example</span></span>

```c
/* Set the value of a 64-Bit integer resource.  */
status = nx_lwm2m_client_resource_integer64_set(&resource, 32323);

/* If status is NX_SUCCESS, the value of 64-Bit integer resource was successfully set. */
```

##  <a name="nx_lwm2m_client_resource_objlnk_get"></a><span data-ttu-id="f6e5f-847">nx_lwm2m_client_resource_objlnk_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-847">nx_lwm2m_client_resource_objlnk_get</span></span>

<span data-ttu-id="f6e5f-848">Pobiera wartość zasobu linku do obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-848">Gets the value of an object link resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-849">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-849">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    NX_LWM2M_ID *object_id, 
    NX_LWM2M_ID *instance_id);
```

### <a name="description"></a><span data-ttu-id="f6e5f-850">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-850">Description</span></span>

<span data-ttu-id="f6e5f-851">Usługa Pobiera wartość linku do obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-851">The service retrieves the value of object link.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-852">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-852">Parameters</span></span>

- <span data-ttu-id="f6e5f-853">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-853">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-854">**object_id** Wskaźnik na identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-854">**object_id** Pointer to the object ID.</span></span>
- <span data-ttu-id="f6e5f-855">**instance_ID** Wskaźnik na identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-855">**instance_id** Pointer to the object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-856">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-856">Return Values</span></span>

- <span data-ttu-id="f6e5f-857">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-857">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-858">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością linku obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-858">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an object link value.</span></span>
- <span data-ttu-id="f6e5f-859">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-859">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-860">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-860">Allowed From</span></span>

<span data-ttu-id="f6e5f-861">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-861">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-862">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-862">Example</span></span>

```c
/* Get the value of the object link resource.  */
status = nx_lwm2m_client_resource_objlnk_get(&resource, &object_id, &instance_id);

/* If status is NX_SUCCESS, the object link value was successfully get. */
```

## <a name="nx_lwm2m_client_resource_objlnk_set"></a><span data-ttu-id="f6e5f-863">nx_lwm2m_client_resource_objlnk_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-863">nx_lwm2m_client_resource_objlnk_set</span></span>

<span data-ttu-id="f6e5f-864">Ustawia wystąpienia zasobów</span><span class="sxs-lookup"><span data-stu-id="f6e5f-864">Sets the resource instances</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-865">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-865">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_objlnk_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    NX_LWM2M_ID object_id, 
    NX_LWM2M_ID instance_id);
```

### <a name="description"></a><span data-ttu-id="f6e5f-866">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-866">Description</span></span>

<span data-ttu-id="f6e5f-867">Usługa ustawia wartość zasobu linku do obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-867">The service sets the value of the object link resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-868">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-868">Parameters</span></span>

- <span data-ttu-id="f6e5f-869">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-869">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-870">**object_id** Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-870">**object_id** Object ID.</span></span>
- <span data-ttu-id="f6e5f-871">**instance_ID** Identyfikator wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-871">**instance_id** Object instance ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-872">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-872">Return Values</span></span>

- <span data-ttu-id="f6e5f-873">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-873">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-874">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-874">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-875">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-875">Allowed From</span></span>

<span data-ttu-id="f6e5f-876">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-876">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-877">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-877">Example</span></span>

```c
/* Set the value of object link resource.  */
status = nx_lwm2m_client_resource_objlnk_set(&resource, 3303, 2);

/* If status is NX_SUCCESS, the value of object link resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_opaque_get"></a><span data-ttu-id="f6e5f-878">nx_lwm2m_client_resource_opaque_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-878">nx_lwm2m_client_resource_opaque_get</span></span>

<span data-ttu-id="f6e5f-879">Pobiera wartość nieprzezroczystego zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-879">Gets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-880">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-880">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const VOID **opaque_ptr, 
    UINT \*opaque_length);
```


### <a name="description"></a><span data-ttu-id="f6e5f-881">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-881">Description</span></span>

<span data-ttu-id="f6e5f-882">Usługa Pobiera wartość nieprzezroczystego zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-882">The service retrieves the value of an opaque Resource.</span></span> <span data-ttu-id="f6e5f-883">Nieprzezroczysta wartość zasobu składa się ze wskaźnika do buforu i długości.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-883">An opaque resource value consists of a pointer to a buffer and a length.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-884">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-884">Parameters</span></span>

- <span data-ttu-id="f6e5f-885">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-885">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-886">**opaque_ptr** Wskaźnik na dane nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-886">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="f6e5f-887">**opaque_length** Wskaźnik na nieprzezroczystą długość danych.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-887">**opaque_length** Pointer to the opaque data length.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-888">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-888">Return Values</span></span>

- <span data-ttu-id="f6e5f-889">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-889">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-890">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest zasobem nieprzezroczystym.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-890">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not an opaque resource.</span></span>
- <span data-ttu-id="f6e5f-891">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-891">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-892">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-892">Allowed From</span></span>

<span data-ttu-id="f6e5f-893">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-893">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-894">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-894">Example</span></span>

```c
/* Get the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_get(&resource, &opaque_ptr, &opaque_length);

/* If status is NX_SUCCESS, the value of opaque resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_opaque_set"></a><span data-ttu-id="f6e5f-895">nx_lwm2m_client_resource_opaque_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-895">nx_lwm2m_client_resource_opaque_set</span></span>

<span data-ttu-id="f6e5f-896">Ustawia wartość nieprzezroczystego zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-896">Sets the value of an opaque Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-897">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-897">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_opaque_set(
    NX_LWM2M_CLIENT_RESOURCE *value, 
    VOID *opaque_ptr, 
    UINT opaque_length);
```

### <a name="description"></a><span data-ttu-id="f6e5f-898">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-898">Description</span></span>

<span data-ttu-id="f6e5f-899">Usługa ustawia wartość nieprzezroczystego zasobu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-899">The service sets the value of an opaque Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-900">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-900">Parameters</span></span>

- <span data-ttu-id="f6e5f-901">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-901">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-902">**opaque_ptr** Wskaźnik na dane nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-902">**opaque_ptr** Pointer to the opaque data.</span></span>
- <span data-ttu-id="f6e5f-903">**opaque_length** Długość nieprzezroczystych danych.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-903">**opaque_length** Length of the opaque data.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-904">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-904">Return Values</span></span>

- <span data-ttu-id="f6e5f-905">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-905">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-906">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-906">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-907">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-907">Allowed From</span></span>

<span data-ttu-id="f6e5f-908">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-908">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-909">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-909">Example</span></span>

```c
/* Set the value of an opaque resource.  */
status = nx_lwm2m_client_resource_opaque_set(&resource, “AQIDBAU=”, 8);

/* If status is NX_SUCCESS, the value of opaque resource was successfully set. */
```

## <a name="nx_lwm2m_client_resource_string_get"></a><span data-ttu-id="f6e5f-910">nx_lwm2m_client_resource_string_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-910">nx_lwm2m_client_resource_string_get</span></span>

<span data-ttu-id="f6e5f-911">Pobiera wartość zasobu ciągu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-911">Gets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-912">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-912">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_get(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    const CHAR **string_ptr, 
    UINT *string_length);
```

### <a name="description"></a><span data-ttu-id="f6e5f-913">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-913">Description</span></span>

<span data-ttu-id="f6e5f-914">Usługa Pobiera wartość zasobu ciągu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-914">The service retrieves the value of a string Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-915">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-915">Parameters</span></span>

- <span data-ttu-id="f6e5f-916">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-916">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-917">**string_ptr** Wskaźnik na wskaźnik ciągu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-917">**string_ptr** Pointer to the destination string pointer.</span></span>
- <span data-ttu-id="f6e5f-918">**string_length** Wskaźnik na długość ciągu docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-918">**string_length** Pointer to the destination string length.</span></span> <span data-ttu-id="f6e5f-919">Może mieć **wartość null** , jeśli ciąg jest zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-919">Can be **NULL** if the string is null-terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-920">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-920">Return Values</span></span>

- <span data-ttu-id="f6e5f-921">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-921">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-922">**NX_LWM2M_CLIENT_BAD_ENCODING** Wartość zasobu nie jest wartością ciągu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-922">**NX_LWM2M_CLIENT_BAD_ENCODING** The resource value is not a string value.</span></span>
- <span data-ttu-id="f6e5f-923">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-923">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-924">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-924">Allowed From</span></span>

<span data-ttu-id="f6e5f-925">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-925">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-926">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-926">Example</span></span>

```c
/* Get the value of a string resource.  */
status = nx_lwm2m_client_resource_string_get(&resource, &string_ptr, &string_length);

/* If status is NX_SUCCESS, the value of string resource was successfully get. */
```

## <a name="nx_lwm2m_client_resource_string_set"></a><span data-ttu-id="f6e5f-927">nx_lwm2m_client_resource_string_set</span><span class="sxs-lookup"><span data-stu-id="f6e5f-927">nx_lwm2m_client_resource_string_set</span></span>

<span data-ttu-id="f6e5f-928">Ustawia wartość zasobu ciągu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-928">Sets the value of a string Resource.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-929">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-929">Prototype</span></span>

```c
UINT nx_lwm2m_client_resource_string_set(
    NX_LWM2M_CLIENT_RESOURCE *resource, 
    CHAR *string_ptr, 
    UINT string_length);
```

### <a name="description"></a><span data-ttu-id="f6e5f-930">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-930">Description</span></span>

<span data-ttu-id="f6e5f-931">Usługa ustawia wartość 64-bitowego zasobu liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-931">The service sets the value of a 64-Bit integer Resource.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-932">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-932">Parameters</span></span>

- <span data-ttu-id="f6e5f-933">**zasób** Wskaźnik na zasób.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-933">**resource** Pointer to Resource.</span></span>
- <span data-ttu-id="f6e5f-934">**string_ptr** Wskaźnik na ciąg.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-934">**string_ptr** Pointer to the string.</span></span>
- <span data-ttu-id="f6e5f-935">**string_length** Długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-935">**string_length** Length of the string.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-936">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-936">Return Values</span></span>

- <span data-ttu-id="f6e5f-937">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-937">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-938">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-938">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-939">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-939">Allowed From</span></span>

<span data-ttu-id="f6e5f-940">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-940">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-941">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-941">Example</span></span>

```c
/* Set the value of a string resource.  */
status = nx_lwm2m_client_resource_string_set(&resource, “test”, sizeof(“test”) - 1);

/* If status is NX_SUCCESS, the value of string resource was successfully set. */
```

## <a name="nx_lwm2m_client_session_bootstrap"></a><span data-ttu-id="f6e5f-942">nx_lwm2m_client_session_bootstrap</span><span class="sxs-lookup"><span data-stu-id="f6e5f-942">nx_lwm2m_client_session_bootstrap</span></span>

<span data-ttu-id="f6e5f-943">Uruchamia sesję z serwerem Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-943">Starts a session with a Bootstrap Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-944">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-944">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port);
```

### <a name="description"></a><span data-ttu-id="f6e5f-945">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-945">Description</span></span>

<span data-ttu-id="f6e5f-946">Ta usługa uruchamia sesję z serwerem Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-946">This service starts a session with a Bootstrap Server.</span></span> <span data-ttu-id="f6e5f-947">Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-947">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="f6e5f-948">Jeśli zasób "Hold off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na zainicjowanie przez serwer ładowania początkowego, jeśli po tym okresie ten serwer nie zainicjuje ładowania uruchomienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-948">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, If no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span>

<span data-ttu-id="f6e5f-949">Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-949">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-950">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-950">Parameters</span></span>

- <span data-ttu-id="f6e5f-951">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-951">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="f6e5f-952">**security_id** Identyfikator wystąpienia zabezpieczeń serwera Bootstrap musi być ustawiony na NX_LWM2M_RESERVED_ID (65535), jeśli na serwerze Bootstrap nie zdefiniowano wystąpienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-952">**security_id** The Security Instance ID of the Bootstrap Server, must be set to NX_LWM2M_RESERVED_ID (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="f6e5f-953">**IP_address** Adres IP serwera programu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-953">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="f6e5f-954">**port** Port UDP serwera.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-954">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-955">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-955">Return Values</span></span>

- <span data-ttu-id="f6e5f-956">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-956">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-957">**NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-957">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="f6e5f-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-958">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="f6e5f-959">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-959">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-960">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-960">Allowed From</span></span>

<span data-ttu-id="f6e5f-961">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-961">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-962">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-962">Example</span></span>

```c
/* Start bootstrap.  */
status = nx_lwm2m_client_session_bootstrap(&lwm2m_client, 0, &ip_address, 5783);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_bootstrap_dtls"></a><span data-ttu-id="f6e5f-963">nx_lwm2m_client_session_bootstrap_dtls</span><span class="sxs-lookup"><span data-stu-id="f6e5f-963">nx_lwm2m_client_session_bootstrap_dtls</span></span>

<span data-ttu-id="f6e5f-964">Uruchamia bezpieczną sesję z serwerem Bootstrap</span><span class="sxs-lookup"><span data-stu-id="f6e5f-964">Starts a secure session with a Bootstrap Server</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-965">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-965">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_bootstrap_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID security_id, 
    ULONG ip_address, 
    UINT port, 
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-966">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-966">Description</span></span>

<span data-ttu-id="f6e5f-967">Ta usługa uruchamia sesję z serwerem Bootstrap przy użyciu bezpiecznego połączenia DTLS.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-967">This service start a session with a Bootstrap Server using a secure DTLS connection.</span></span> <span data-ttu-id="f6e5f-968">Serwer powinien mieć odpowiednie wystąpienie zabezpieczeń w obiekcie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-968">The server should have a corresponding security instance in the Security Object.</span></span>

<span data-ttu-id="f6e5f-969">Przed wywołaniem tej funkcji sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-969">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="f6e5f-970">Należy zdefiniować **NX_SECURE_ENABLE_DTLS** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-970">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="f6e5f-971">Jeśli zasób "Hold off" różni się od zera w wystąpieniu zabezpieczeń skojarzonym z tym serwerem, sesja będzie czekać na zainicjowanie przez serwer ładowania początkowego, jeśli po tym okresie ten serwer nie zainicjuje ładowania uruchomienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-971">If the ‘Hold Off’ resource is different than zero in the Security Instance associated with this server the session will wait for a Server Initiated Bootstrap, if no bootstrap is initiated by the server after this period of time a Client Initiated Boostrap will be performed.</span></span> 

<span data-ttu-id="f6e5f-972">Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-972">Any current active session is aborted by this call and replaced by the new Bootstrap Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-973">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-973">Parameters</span></span>

- <span data-ttu-id="f6e5f-974">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-974">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="f6e5f-975">**security_id** Identyfikator wystąpienia zabezpieczeń serwera Bootstrap musi być ustawiony na **NX_LWM2M_RESERVED_ID** (65535), jeśli na serwerze Bootstrap nie zdefiniowano wystąpienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-975">**security_id** The Security Instance ID of the Bootstrap Server, must be set to **NX_LWM2M_RESERVED_ID** (65535) if the Bootstrap Server has no Security Instance defined.</span></span>
- <span data-ttu-id="f6e5f-976">**IP_address** Adres IP serwera programu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-976">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="f6e5f-977">**port** Port UDP serwera.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-977">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="f6e5f-978">**dtls_session_ptr** Sesja DTLS używana dla sesji Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-978">**dtls_session_ptr** The DTLS session to use for the Bootstrap session.</span></span>
- <span data-ttu-id="f6e5f-979">**dtls_local_port** Lokalny port UDP używany do sesji DTLS.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-979">**dtls_local_port** The local UDP port used for the DTLS session.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-980">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-980">Return Values</span></span>

- <span data-ttu-id="f6e5f-981">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-981">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-982">**NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-982">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="f6e5f-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-983">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="f6e5f-984">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-984">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-985">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-985">Allowed From</span></span>

<span data-ttu-id="f6e5f-986">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-986">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-987">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-987">Example</span></span>

```c
/* Start bootstrap with DTLS.  */
status = nx_lwm2m_client_session_bootstrap_dtls(&lwm2m_client, 0, &ip_address, 5784, &dtls_session);

/* If status is NX_SUCCESS, start bootstrap successfully.  */
```

## <a name="nx_lwm2m_client_session_create"></a><span data-ttu-id="f6e5f-988">nx_lwm2m_client_session_create</span><span class="sxs-lookup"><span data-stu-id="f6e5f-988">nx_lwm2m_client_session_create</span></span>

<span data-ttu-id="f6e5f-989">Tworzy sesję klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-989">Creates a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-990">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-990">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_create(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_CLIENT *client_ptr,
    NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK state_callback);
```

### <a name="description"></a><span data-ttu-id="f6e5f-991">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-991">Description</span></span>

<span data-ttu-id="f6e5f-992">Ta usługa tworzy nową sesję klienta LWM2M dołączoną do istniejącego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-992">This service creates a new LWM2M Client Session attached to an existing LWM2M Client.</span></span> <span data-ttu-id="f6e5f-993">Sesja jest używana przez klienta LWM2M do komunikacji z serwerem Bootstrap lub serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-993">The session is used by the LWM2M Client to communicate with a Bootstrap Server or a LWM2M Server.</span></span> 

<span data-ttu-id="f6e5f-994">Aplikacja musi udostępniać funkcję wywołania zwrotnego, która będzie wywoływana, gdy stan sesji zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-994">The application must provide a callback function that will be called when the state of the session is updated.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-995">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-995">Parameters</span></span>

- <span data-ttu-id="f6e5f-996">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-996">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="f6e5f-997">**client_ptr** Wskaźnik do wcześniej utworzonego klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-997">**client_ptr** Pointer to the previously created LWM2M Client.</span></span>
- <span data-ttu-id="f6e5f-998">**state_callback** Wywołanie zwrotne aplikacji wywoływane w przypadku zmiany stanu sesji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-998">**state_callback** Application callback that is called when the state of the session has changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-999">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-999">Return Values</span></span>

- <span data-ttu-id="f6e5f-1000">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1000">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-1001">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1001">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1002">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1002">Allowed From</span></span>

<span data-ttu-id="f6e5f-1003">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1003">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1004">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1004">Example</span></span>

```c
/* Create session.  */
status = nx_lwm2m_client_session_create(&session, &lwm2m_client, session_callback);

/* If status is NX_SUCCESS, a session was successfully created.  */
```

## <a name="nx_lwm2m_client_session_delete"></a><span data-ttu-id="f6e5f-1005">nx_lwm2m_client_session_delete</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1005">nx_lwm2m_client_session_delete</span></span>

<span data-ttu-id="f6e5f-1006">Usuwa sesję klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1006">Deletes a LWM2M Client Session.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-1007">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1007">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_delete(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-1008">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1008">Description</span></span>

<span data-ttu-id="f6e5f-1009">Ta usługa usuwa sesję klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1009">This service deletes a LWM2M Client Session.</span></span>

<span data-ttu-id="f6e5f-1010">Po usunięciu klienta LWM2M przez wywołanie nx_lwm2m_client_delete wszystkie sesje dołączone do klienta również zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1010">When a LWM2M Client is deleted by calling nx_lwm2m_client_delete all sessions attached to the client are also deleted.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-1011">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1011">Parameters</span></span>

- <span data-ttu-id="f6e5f-1012">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1012">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-1013">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1013">Return Values</span></span>

- <span data-ttu-id="f6e5f-1014">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1014">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-1015">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1015">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1016">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1016">Allowed From</span></span>

<span data-ttu-id="f6e5f-1017">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1017">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1018">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1018">Example</span></span>

```c
/* Delete session.  */
status = nx_lwm2m_client_session_delete(&session);

/* If status is NX_SUCCESS, a session was successfully deleted.  */
```

## <a name="nx_lwm2m_client_session_deregister"></a><span data-ttu-id="f6e5f-1019">nx_lwm2m_client_session_deregister</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1019">nx_lwm2m_client_session_deregister</span></span>

<span data-ttu-id="f6e5f-1020">Kończy sesję z serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1020">Terminates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-1021">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1021">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_deregister(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-1022">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1022">Description</span></span>

<span data-ttu-id="f6e5f-1023">Ta usługa wykonuje operację "Wyrejestrowanie" na serwerze LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1023">This service performs a ‘De-Register’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-1024">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1024">Parameters</span></span>

- <span data-ttu-id="f6e5f-1025">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1025">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-1026">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1026">Return Values</span></span>

- <span data-ttu-id="f6e5f-1027">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1027">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** Klient nie jest zarejestrowany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1028">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="f6e5f-1029">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1029">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1030">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1030">Allowed From</span></span>

<span data-ttu-id="f6e5f-1031">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1031">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1032">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1032">Example</span></span>

```c
/* De-register session.  */
status = nx_lwm2m_client_session_deregister(&session);

/* If status is NX_SUCCESS, session was successfully de-registered.  */
```

## <a name="nx_lwm2m_client_session_error_get"></a><span data-ttu-id="f6e5f-1033">nx_lwm2m_client_session_error_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1033">nx_lwm2m_client_session_error_get</span></span>

<span data-ttu-id="f6e5f-1034">Pobiera ostatni błąd sesji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1034">Gets the last error of a session.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-1035">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1035">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_error_get(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-1036">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1036">Description</span></span>

<span data-ttu-id="f6e5f-1037">Ta usługa zwraca kod błędu sesji, gdy sesja jest w stanie błędu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1037">This service returns the error code of the session when the session is in an error state.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-1038">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1038">Parameters</span></span>

- <span data-ttu-id="f6e5f-1039">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1039">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-1040">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1040">Return Values</span></span>

- <span data-ttu-id="f6e5f-1041">**NX_SUCCESS** Sesja nie jest w stanie błędu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1041">**NX_SUCCESS** The session is not in error state.</span></span>
- <span data-ttu-id="f6e5f-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Nieprawidłowy adres serwera.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1042">**NX_LWM2M_CLIENT_ADDRESS_ERROR** Invalid server address.</span></span>
- <span data-ttu-id="f6e5f-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Ładunek żądania nie mieści się w buforze sieciowym.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1043">**NX_LWM2M_ CLIENT_BUFFER_TOO_SMALL** Payload of request doesn’t fit in network buffer.</span></span>
- <span data-ttu-id="f6e5f-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Nie można ustanowić bezpiecznego połączenia z serwerem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1044">**NX_LWM2M_ CLIENT_DTLS_ERROR** Failed to establish secured connection with server.</span></span>
- <span data-ttu-id="f6e5f-1045">**NX_LWM2M_ CLIENT_ERROR** Nieokreślony błąd.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1045">**NX_LWM2M_ CLIENT_ERROR** Unspecified error.</span></span>
- <span data-ttu-id="f6e5f-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Odmowa rejestracji przez serwer.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1046">**NX_LWM2M_ CLIENT_FORBIDDEN** Registration refused by server.</span></span>
- <span data-ttu-id="f6e5f-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Nie odnaleziono klienta przez serwer podczas aktualizowania/wyrejestrowywania.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1047">**NX_LWM2M_ CLIENT_NOT_FOUND** Client not found by server when updating/deregistering.</span></span>
- <span data-ttu-id="f6e5f-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** Wystąpienie obiektu serwera odpowiadające sesji zostało usunięte.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1048">**NX_LWM2M_ CLIENT_SERVER_INSTANCE_DELETED** The Server Object Instance corresponding to the session has been deleted.</span></span>
- <span data-ttu-id="f6e5f-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** Brak odpowiedzi z serwera.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1049">**NX_LWM2M_ CLIENT_TIMED_OUT** No answer from server.</span></span>
- <span data-ttu-id="f6e5f-1050">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1050">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1051">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1051">Allowed From</span></span>

<span data-ttu-id="f6e5f-1052">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1052">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1053">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1053">Example</span></span>

```c
/* Get the error.  */
status = nx_lwm2m_client_session_error_get(&session);
```
## <a name="nx_lwm2m_client_session_register"></a><span data-ttu-id="f6e5f-1054">nx_lwm2m_client_session_register</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1054">nx_lwm2m_client_session_register</span></span>

<span data-ttu-id="f6e5f-1055">Uruchamia sesję z serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1055">Starts a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-1056">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1056">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port);
```


### <a name="description"></a><span data-ttu-id="f6e5f-1057">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1057">Description</span></span>

<span data-ttu-id="f6e5f-1058">Ta usługa wykonuje operację "Register" na serwerze LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1058">This service performs a ‘Register’ operation to a LWM2M Server.</span></span> <span data-ttu-id="f6e5f-1059">Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwer.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1059">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="f6e5f-1060">Jeśli rejestracja zakończyła się pomyślnie, klient programu LWM2M będzie przetwarzać dalsze operacje z serwera i okresowo wysyła komunikat "Update", dopóki klient nie zostanie wyrejestrowany.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1060">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="f6e5f-1061">Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1061">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-1062">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1062">Parameters</span></span>

- <span data-ttu-id="f6e5f-1063">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1063">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="f6e5f-1064">**server_id** Krótki identyfikator serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1064">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="f6e5f-1065">**IP_address** Adres IP serwera programu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1065">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="f6e5f-1066">**port** Port UDP serwera.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1066">**port** The UDP port of the server.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-1067">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1067">Return Values</span></span>

- <span data-ttu-id="f6e5f-1068">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1068">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-1069">**NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1069">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="f6e5f-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1070">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="f6e5f-1071">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1071">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1072">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1072">Allowed From</span></span>

<span data-ttu-id="f6e5f-1073">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1073">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1074">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1074">Example</span></span>

```c
/* Start register.  */
status = nx_lwm2m_client_session_register (&lwm2m_client, 123, &ip_address, 5683);

/* If status is NX_SUCCESS, start register successfully.  */
```

## <a name="nx_lwm2m_client_session_register_dtls"></a><span data-ttu-id="f6e5f-1075">nx_lwm2m_client_session_register_dtls</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1075">nx_lwm2m_client_session_register_dtls</span></span>

<span data-ttu-id="f6e5f-1076">Uruchamia bezpieczną sesję z serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1076">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-1077">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1077">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    NX_LWM2M_ID server_id, 
    ULONG ip_address, 
    UINT port,
    NX_SECURE_DTLS_SESSION *dtls_session_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-1078">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1078">Description</span></span>

<span data-ttu-id="f6e5f-1079">Ta usługa wykonuje operację "Register" na serwerze LWM2M przy użyciu bezpiecznego połączenia usługi DTLS.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1079">This service performs a ‘Register’ operation to a LWM2M Server using a secure DTLS connection.</span></span> <span data-ttu-id="f6e5f-1080">Serwer musi mieć odpowiednie wystąpienie serwera w obiekcie serwer.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1080">The server must have a corresponding server instance in the Server Object.</span></span>

<span data-ttu-id="f6e5f-1081">Przed wywołaniem tej funkcji sesja DTLS musi zostać skonfigurowana przy użyciu odpowiednich mechanizmów szyfrowania i materiału klucza.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1081">The DTLS session must have been configured with the proper cipher suites and key material before calling this function.</span></span> <span data-ttu-id="f6e5f-1082">Należy zdefiniować **NX_SECURE_ENABLE_DTLS** .</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1082">**NX_SECURE_ENABLE_DTLS** must be defined.</span></span>

<span data-ttu-id="f6e5f-1083">Jeśli rejestracja zakończyła się pomyślnie, klient programu LWM2M będzie przetwarzać dalsze operacje z serwera i okresowo wysyła komunikat "Update", dopóki klient nie zostanie wyrejestrowany.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1083">If the registration is successfully the LWM2M Client will process further operations from the server and will periodically send ‘Update’ messages until the client is de-registered.</span></span>

<span data-ttu-id="f6e5f-1084">Wszystkie bieżące aktywne sesje są przerywane przez to wywołanie i zastępowane przez nową sesję serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1084">Any current active session is aborted by this call and replaced by the new LWM2M Server session.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-1085">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1085">Parameters</span></span>

- <span data-ttu-id="f6e5f-1086">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1086">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="f6e5f-1087">**server_id** Krótki identyfikator serwera LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1087">**server_id** The Short Server ID of the LWM2M Server.</span></span>
- <span data-ttu-id="f6e5f-1088">**IP_address** Adres IP serwera programu.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1088">**ip_address** The IP address of the server.</span></span>
- <span data-ttu-id="f6e5f-1089">**port** Port UDP serwera.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1089">**port** The UDP port of the server.</span></span>
- <span data-ttu-id="f6e5f-1090">**dtls_session_ptr** Sesja DTLS używana na potrzeby sesji LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1090">**dtls_session_ptr** The DTLS session to use for the LWM2M session.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-1091">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1091">Return Values</span></span>

- <span data-ttu-id="f6e5f-1092">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1092">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-1093">**NX_LWM2M_CLIENT_ERROR** Błąd ładowania początkowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1093">**NX_LWM2M_CLIENT_ERROR** Bootstrap error.</span></span>
- <span data-ttu-id="f6e5f-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1094">**NX_LWM2M_CLIENT_PORT_UNAVAILABLE** Port is unavailable.</span></span>
- <span data-ttu-id="f6e5f-1095">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1095">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1096">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1096">Allowed From</span></span>

<span data-ttu-id="f6e5f-1097">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1097">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1098">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1098">Example</span></span>

```c
/* Start register with DTLS.  */
status = nx_lwm2m_client_session_register_dtls(&lwm2m_client, 123, &ip_address, 5683, &dtls_session);

/* If status is NX_SUCCESS, start register with DTLS successfully.  */
```

## <a name="nx_lwm2m_client_session_register_info_get"></a><span data-ttu-id="f6e5f-1099">nx_lwm2m_client_session_register_info_get</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1099">nx_lwm2m_client_session_register_info_get</span></span>

<span data-ttu-id="f6e5f-1100">Uruchamia bezpieczną sesję z serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1100">Starts a secure session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-1101">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1101">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_register_dtls(
    NX_LWM2M_CLIENT_SESSION *session_ptr, 
    UINT security_instance_id, 
    NX_LWM2M_ID *server_id,
    CHAR **server_uri, 
    UINT *server_uri_length, 
    UCHAR *security_mode, 
    UCHAR **pub_key_or_id, 
    UINT *pub_key_or_id_len, 
    UCHAR **server_pub_key, 
    UINT *server_pub_key_len, 
    UCHAR **secret_key, 
    UINT *secret_key_len);
```

### <a name="description"></a><span data-ttu-id="f6e5f-1102">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1102">Description</span></span>

<span data-ttu-id="f6e5f-1103">Po ustanowieniu sesji komunikacji z serwerem Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1103">Once a communication session with a Bootstrap server was established.</span></span> <span data-ttu-id="f6e5f-1104">Aplikacja może wywołać ten interfejs API, aby uzyskać informacje o serwerze i zabezpieczeniach dla kolejnego kroku rejestracji.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1104">Application can call this api to get the server and security information for the next registration step.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-1105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1105">Parameters</span></span>

- <span data-ttu-id="f6e5f-1106">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1106">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>
- <span data-ttu-id="f6e5f-1107">**security_instance_id** Identyfikator wystąpienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1107">**security_instance_id** Security instance ID.</span></span>
- <span data-ttu-id="f6e5f-1108">**server_id** Wskaźnik na identyfikator serwera docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1108">**server_id** Pointer to destination server ID.</span></span>
- <span data-ttu-id="f6e5f-1109">**server_uri** Wskaźnik na identyfikator URI serwera docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1109">**server_uri** Pointer to destination server uri.</span></span>
- <span data-ttu-id="f6e5f-1110">**server_uri_len** Wskaźnik na długość identyfikatora URI serwera docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1110">**server_uri_len** Pointer to destination server uri length.</span></span>
- <span data-ttu-id="f6e5f-1111">**security_mode** Wskaźnik do docelowego trybu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1111">**security_mode** Pointer to destination security mode.</span></span>
- <span data-ttu-id="f6e5f-1112">**pub_key_or_id** Wskaźnik na docelowy klucz publiczny lub tożsamość.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1112">**pub_key_or_id** Pointer to destination public key or identity.</span></span>
- <span data-ttu-id="f6e5f-1113">**pub_key_or_id_len** Wskaźnik na docelowy klucz publiczny lub długość tożsamości.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1113">**pub_key_or_id_len** Pointer to destination public key or identity length.</span></span>
- <span data-ttu-id="f6e5f-1114">**server_pub_key** Wskaźnik na klucz publiczny serwera docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1114">**server_pub_key** Pointer to destination server public key.</span></span>
- <span data-ttu-id="f6e5f-1115">**server_pub_key_len** Wskaźnik na długość klucza publicznego serwera docelowego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1115">**server_pub_key_len** Pointer to destination server public key length.</span></span>
- <span data-ttu-id="f6e5f-1116">**SECRET_KEY** Wskaźnik na docelowy klucz tajny.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1116">**secret_key** Pointer to destination secret key.</span></span>
- <span data-ttu-id="f6e5f-1117">**secret_key_len** Wskaźnik na długość docelowego klucza tajnego.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1117">**secret_key_len** Pointer to destination secret key length.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-1118">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1118">Return Values</span></span>

- <span data-ttu-id="f6e5f-1119">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1119">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-1120">**NX_LWM2M_CLIENT_NOT_FOUND** Brak wystąpienia obiektu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1120">**NX_LWM2M_CLIENT_NOT_FOUND** There is no security Object instance.</span></span>
- <span data-ttu-id="f6e5f-1121">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1121">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1122">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1122">Allowed From</span></span>

<span data-ttu-id="f6e5f-1123">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1123">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1124">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1124">Example</span></span>

```c
/* Get the register information.  */
status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_length, &security_mode, &pub_key_or_id, &pub_key_or_id_len, NX_NULL, NX_NULL, &secret_key, &secret_key_len);

/* If status is NX_SUCCESS, the register information was successfully gotten.  */
```

## <a name="nx_lwm2m_client_session_update"></a><span data-ttu-id="f6e5f-1125">nx_lwm2m_client_session_update</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1125">nx_lwm2m_client_session_update</span></span>

<span data-ttu-id="f6e5f-1126">Aktualizuje sesję z serwerem LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1126">Updates a session with a LWM2M Server.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-1127">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1127">Prototype</span></span>

```c
UINT nx_lwm2m_client_session_update(NX_LWM2M_CLIENT_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-1128">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1128">Description</span></span>

<span data-ttu-id="f6e5f-1129">Ta usługa wykonuje operację "Update" na serwerze LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1129">This service performs an ‘Update’ operation to a LWM2M Server.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-1130">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1130">Parameters</span></span>

- <span data-ttu-id="f6e5f-1131">**session_ptr** Wskaźnik do LWM2M bloku sterowania sesją klienta.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1131">**session_ptr** Pointer to LWM2M Client Session control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-1132">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1132">Return Values</span></span>

- <span data-ttu-id="f6e5f-1133">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1133">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** Klient nie jest zarejestrowany na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1134">**NX_LWM2M_CLIENT_NOT_REGISTERED** The client is not registered to the server.</span></span>
- <span data-ttu-id="f6e5f-1135">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1135">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1136">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1136">Allowed From</span></span>

<span data-ttu-id="f6e5f-1137">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1137">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1138">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1138">Example</span></span>

```c
/* Update a session.  */
status = nx_lwm2m_client_session_update(&session);

/* If status is NX_SUCCESS, a session was successfully updated.  */
```

## <a name="nx_lwm2m_client_unlock"></a><span data-ttu-id="f6e5f-1139">nx_lwm2m_client_unlock</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1139">nx_lwm2m_client_unlock</span></span>

<span data-ttu-id="f6e5f-1140">Odblokowuje klienta LWM2M.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1140">Unlocks a LWM2M Client.</span></span>

### <a name="prototype"></a><span data-ttu-id="f6e5f-1141">Prototype</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1141">Prototype</span></span>

```c
UINT nx_lwm2m_client_unlock(NX_LWM2M_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="f6e5f-1142">Opis</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1142">Description</span></span>

<span data-ttu-id="f6e5f-1143">Ta usługa odblokowuje klienta LWM2M poprzednio zablokowany przez wywołanie do ***nx_lwm2m_client_unlock***.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1143">This service unlocks the LWM2M Client previously locked by a call to ***nx_lwm2m_client_unlock***.</span></span>

### <a name="parameters"></a><span data-ttu-id="f6e5f-1144">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1144">Parameters</span></span>

- <span data-ttu-id="f6e5f-1145">**client_ptr** Wskaźnik do LWM2M bloku sterowania klientem.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1145">**client_ptr** Pointer to LWM2M Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f6e5f-1146">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1146">Return Values</span></span>

- <span data-ttu-id="f6e5f-1147">**NX_SUCCESS** Operacja zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1147">**NX_SUCCESS** Successful operation.</span></span>
- <span data-ttu-id="f6e5f-1148">**NX_PTR_ERROR** Nieprawidłowy wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1148">**NX_PTR_ERROR** Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f6e5f-1149">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1149">Allowed From</span></span>

<span data-ttu-id="f6e5f-1150">Wątki, Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1150">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="f6e5f-1151">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6e5f-1151">Example</span></span>

```c
/* Unlock lwm2m client.  */
status = nx_lwm2m_client_unlock(&lwm2m_client);

/* If status is NX_SUCCESS, unlock lwm2m client successfully.  */
```