---
title: Rozdział 3 — Opis usług Azure RTO NetX Duo Point-to-Point Protocol (PPP)
description: Ten rozdział zawiera opis wszystkich usług PPP usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 90c24cad5e595087ba27178243f9dda0dab11029
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821727"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a><span data-ttu-id="71e5a-103">Rozdział 3 — Opis usług Azure RTO NetX Duo Point-to-Point Protocol (PPP)</span><span class="sxs-lookup"><span data-stu-id="71e5a-103">Chapter 3 - Description of Azure RTOS NetX Duo Point-to-Point Protocol (PPP) services</span></span>

<span data-ttu-id="71e5a-104">Ten rozdział zawiera opis wszystkich usług PPP usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="71e5a-104">This chapter contains a description of all Azure RTOS NetX Duo PPP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="71e5a-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="71e5a-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="71e5a-106">**nx_ppp_byte_receive**: *odebranie bajtu z SZEREGowego procedury ISR*</span><span class="sxs-lookup"><span data-stu-id="71e5a-106">**nx_ppp_byte_receive**: *Receive a byte from serial ISR*</span></span>
- <span data-ttu-id="71e5a-107">**nx_ppp_chap_challenge**: *generowanie wyzwania protokołu CHAP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-107">**nx_ppp_chap_challenge**: *Generate a CHAP challenge*</span></span>
- <span data-ttu-id="71e5a-108">**nx_ppp_chap_enable**: *Włączanie uwierzytelniania CHAP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-108">**nx_ppp_chap_enable**: *Enable CHAP authentication*</span></span>
- <span data-ttu-id="71e5a-109">**nx_ppp_create**: *Tworzenie wystąpienia protokołu PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-109">**nx_ppp_create**: *Create a PPP instance*</span></span>
- <span data-ttu-id="71e5a-110">**nx_ppp_delete**: *usuwanie wystąpienia protokołu PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-110">**nx_ppp_delete**: *Delete a PPP instance*</span></span>
- <span data-ttu-id="71e5a-111">**nx_ppp_dns_address_get**: *Pobierz adres IP serwera DNS*</span><span class="sxs-lookup"><span data-stu-id="71e5a-111">**nx_ppp_dns_address_get**: *Get DNS Server IP address*</span></span>
- <span data-ttu-id="71e5a-112">**nx_ppp_dns_address_set**:*Ustaw adres IP serwera DNS*</span><span class="sxs-lookup"><span data-stu-id="71e5a-112">**nx_ppp_dns_address_set**:*Set DNS Server IP address*</span></span>
- <span data-ttu-id="71e5a-113">**nx_ppp_secondary_dns_address_get**: *Pobierz adres IP POMOCNICZego serwera DNS*</span><span class="sxs-lookup"><span data-stu-id="71e5a-113">**nx_ppp_secondary_dns_address_get**: *Get Secondary DNS Server IP address*</span></span>
- <span data-ttu-id="71e5a-114">**nx_ppp_secondary_dns_address_set**: *Ustaw adres IP serwera Secondary_DNS*</span><span class="sxs-lookup"><span data-stu-id="71e5a-114">**nx_ppp_secondary_dns_address_set**: *Set Secondary_DNS Server IP address*</span></span>
- <span data-ttu-id="71e5a-115">**nx_ppp_interface_index_get**: *Pobierz indeks interfejsu IP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-115">**nx_ppp_interface_index_get**: *Get IP interface index*</span></span>
- <span data-ttu-id="71e5a-116">**nx_ppp_ip_address_assign**: *Przypisz adresy IP do protokołu IPCP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-116">**nx_ppp_ip_address_assign**: *Assign IP addresses for IPCP*</span></span>
- <span data-ttu-id="71e5a-117">**nx_ppp_link_down_notify**: *Powiadamiaj aplikację przy połączeniu w dół*</span><span class="sxs-lookup"><span data-stu-id="71e5a-117">**nx_ppp_link_down_notify**: *Notify application on link down*</span></span>
- <span data-ttu-id="71e5a-118">**nx_ppp_link_up_notify**: *Powiadom aplikację przy połączeniu*</span><span class="sxs-lookup"><span data-stu-id="71e5a-118">**nx_ppp_link_up_notify**: *Notify application on link up*</span></span>
- <span data-ttu-id="71e5a-119">**nx_ppp_nak_authentication_notify**: *Powiadamiaj aplikację w przypadku ODEBRANia uwierzytelniania nak*</span><span class="sxs-lookup"><span data-stu-id="71e5a-119">**nx_ppp_nak_authentication_notify**: *Notify application if authentication NAK is received*</span></span>
- <span data-ttu-id="71e5a-120">**nx_ppp_pap_enable**: *Włączanie uwierzytelniania PAP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-120">**nx_ppp_pap_enable**: *Enable PAP authentication*</span></span>
- <span data-ttu-id="71e5a-121">**nx_ppp_ping_request**: *Wyślij żądanie echa LCP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-121">**nx_ppp_ping_request**: *Send an LCP echo request*</span></span>
- <span data-ttu-id="71e5a-122">**nx_ppp_raw_string_send**: *Wyślij ciąg NIEbędący protokołem PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-122">**nx_ppp_raw_string_send**: *Send non PPP string*</span></span>
- <span data-ttu-id="71e5a-123">**nx_ppp_restart**: *Ponowne uruchamianie przetwarzania PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-123">**nx_ppp_restart**: *Restart PPP processing*</span></span>
- <span data-ttu-id="71e5a-124">**nx_ppp_start**: *Uruchamianie przetwarzania PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-124">**nx_ppp_start**: *Start PPP processing*</span></span>
- <span data-ttu-id="71e5a-125">**nx_ppp_status_get**: *Pobierz bieżący stan protokołu PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-125">**nx_ppp_status_get**: *Get current PPP status*</span></span>
- <span data-ttu-id="71e5a-126">**nx_ppp_stop**: *ZAtrzymywanie przetwarzania PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-126">**nx_ppp_stop**: *Stop PPP processing*</span></span>
- <span data-ttu-id="71e5a-127">**nx_ppp_packet_receive**: *odbieranie pakietu PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-127">**nx_ppp_packet_receive**: *Receive PPP packet*</span></span>
- <span data-ttu-id="71e5a-128">**nx_ppp_packet_send_set**: *Ustaw funkcję wysyłania pakietów PPP*</span><span class="sxs-lookup"><span data-stu-id="71e5a-128">**nx_ppp_packet_send_set**: *Set PPP packet send function*</span></span>

## <a name="nx_ppp_byte_receive"></a><span data-ttu-id="71e5a-129">nx_ppp_byte_receive</span><span class="sxs-lookup"><span data-stu-id="71e5a-129">nx_ppp_byte_receive</span></span>

<span data-ttu-id="71e5a-130">Odbierz bajt od szeregu ISR</span><span class="sxs-lookup"><span data-stu-id="71e5a-130">Receive a byte from serial ISR</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-131">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-131">Prototype</span></span>

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a><span data-ttu-id="71e5a-132">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-132">Description</span></span>

<span data-ttu-id="71e5a-133">Ta usługa jest zazwyczaj wywoływana z procedury usługi przerwania sterownika szeregowego aplikacji (ISR) do transferu odebranego bajtu do PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-133">This service is typically called from the application’s serial driver Interrupt Service Routine (ISR) to transfer a received byte to PPP.</span></span> <span data-ttu-id="71e5a-134">Gdy jest wywoływana, ta procedura umieszcza odebrany bajt w buforze bajtów cyklicznych i powiadamia odpowiedni wątek PPP do przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="71e5a-134">When called, this routine places the received byte into a circular byte buffer and notifies the appropriate PPP thread for processing.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-135">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-135">Input Parameters</span></span>

- <span data-ttu-id="71e5a-136">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-136">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-137">**Byte**: bajt odebrany z urządzenia szeregowego</span><span class="sxs-lookup"><span data-stu-id="71e5a-137">**byte**: Byte received from serial device</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-138">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-138">Return Values</span></span>

- <span data-ttu-id="71e5a-139">**NX_SUCCESS**: (0X00) pomyślne odebranie BAJTOWEGO protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-139">**NX_SUCCESS**: (0x00) Successful PPP byte receive.</span></span>
- <span data-ttu-id="71e5a-140">**NX_PPP_BUFFER_FULL**: bufor szeregowy PPP (0xB1) jest już zapełniony.</span><span class="sxs-lookup"><span data-stu-id="71e5a-140">**NX_PPP_BUFFER_FULL**: (0xB1) PPP serial buffer is already full.</span></span>
- <span data-ttu-id="71e5a-141">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-141">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-142">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-142">Allowed From</span></span>

<span data-ttu-id="71e5a-143">Wątki, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71e5a-143">Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-144">Example</span></span>

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a><span data-ttu-id="71e5a-145">nx_ppp_chap_challenge</span><span class="sxs-lookup"><span data-stu-id="71e5a-145">nx_ppp_chap_challenge</span></span>

<span data-ttu-id="71e5a-146">Generuj wyzwanie CHAP</span><span class="sxs-lookup"><span data-stu-id="71e5a-146">Generate a CHAP challenge</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-147">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-147">Prototype</span></span>

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-148">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-148">Description</span></span>

<span data-ttu-id="71e5a-149">Ta usługa inicjuje wyzwanie protokołu CHAP po nawiązaniu połączenia PPP i uruchomieniu go.</span><span class="sxs-lookup"><span data-stu-id="71e5a-149">This service initiates a CHAP challenge after the PPP connection is already up and running.</span></span> <span data-ttu-id="71e5a-150">Dzięki temu aplikacja ma możliwość regularnego weryfikowania autentyczności połączenia.</span><span class="sxs-lookup"><span data-stu-id="71e5a-150">This gives the application the ability to verify the authenticity of the connection on a periodic basis.</span></span> <span data-ttu-id="71e5a-151">Jeśli test nie powiedzie się, łącze PPP zostanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="71e5a-151">If the challenge is unsuccessful, the PPP link is closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-152">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-152">Input Parameters</span></span>

- <span data-ttu-id="71e5a-153">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-153">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-154">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-154">Return Values</span></span>

- <span data-ttu-id="71e5a-155">**NX_SUCCESS**: (0X00) pomyślnie zainicjowano żądanie PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-155">**NX_SUCCESS**: (0x00) Successful PPP challenge initiated.</span></span>
- <span data-ttu-id="71e5a-156">**NX_PPP_FAILURE**: (0XB0) nieprawidłowe wyzwanie protokołu PPP, protokół CHAP został włączony tylko dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-156">**NX_PPP_FAILURE**: (0xB0) Invalid PPP challenge, CHAP was enabled only for response.</span></span>
- <span data-ttu-id="71e5a-157">**NX_NOT_IMPLEMENTED**: (0x80) logika protokołu CHAP została wyłączona za pośrednictwem NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-157">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="71e5a-158">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-158">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="71e5a-159">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-159">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-160">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-160">Allowed From</span></span>

<span data-ttu-id="71e5a-161">Wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-161">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-162">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-162">Example</span></span>

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a><span data-ttu-id="71e5a-163">nx_ppp_chap_enable</span><span class="sxs-lookup"><span data-stu-id="71e5a-163">nx_ppp_chap_enable</span></span>

<span data-ttu-id="71e5a-164">Włącz uwierzytelnianie CHAP</span><span class="sxs-lookup"><span data-stu-id="71e5a-164">Enable CHAP authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-165">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-165">Prototype</span></span>

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a><span data-ttu-id="71e5a-166">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-166">Description</span></span>

<span data-ttu-id="71e5a-167">Ta usługa włącza protokół uwierzytelniania Challenge-Handshake (CHAP) dla określonego wystąpienia protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-167">This service enables the Challenge-Handshake Authentication Protocol (CHAP) for the specified PPP instance.</span></span>

<span data-ttu-id="71e5a-168">Jeśli określono wskaźniki funkcji "\***get_challenge_values**_" i "_ \* _get_verification_values_\* \*", protokół CHAP jest wymagany przez to wystąpienie protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-168">If the “\***get_challenge_values**_” and “_\*_get_verification_values_\*\*” function pointers are specified, CHAP is required by this PPP instance.</span></span> <span data-ttu-id="71e5a-169">W przeciwnym razie protokół CHAP odpowiada tylko na żądania wyzwania elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="71e5a-169">Otherwise, CHAP only responds to the peer’s challenge requests.</span></span>

<span data-ttu-id="71e5a-170">Poniżej przedstawiono kilka elementów danych, do których odwołuje się wymagana funkcja wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="71e5a-170">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="71e5a-171">Parametry *tajne*, *Nazwa* i *system* elementów danych mają być ciągiem zakończonym wartością null o maksymalnym rozmiarze NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="71e5a-171">The data items *secret*, *name*, and *system* are expected to be NULL-terminated strings with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="71e5a-172">Oczekiwanym *rand_valuem* elementu danych będzie ciąg zakończony znakiem null o maksymalnym rozmiarze NX_PPP_VALUE_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="71e5a-172">The data item *rand_value* is expected to be a NULL-terminated string with a maximum size of NX_PPP_VALUE_SIZE-1.</span></span> <span data-ttu-id="71e5a-173">*Identyfikator* elementu danych to prosty typ znaku bez znaku.</span><span class="sxs-lookup"><span data-stu-id="71e5a-173">The data item *id* is a simple unsigned character type.</span></span>

>[!NOTE]
> <span data-ttu-id="71e5a-174">Ta funkcja musi być wywoływana po *nx_ppp_create* , ale przed nx_ip_create lub *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="71e5a-174">This function must be called after *nx_ppp_create* but before nx_ip_create or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-175">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-175">Input Parameters</span></span>

- <span data-ttu-id="71e5a-176">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-176">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-177">**get_challenge_values**: wskaźnik do funkcji aplikacji, aby pobrać wartości używane dla wyzwania.</span><span class="sxs-lookup"><span data-stu-id="71e5a-177">**get_challenge_values**: Pointer to application function to retrieve values used for the challenge.</span></span> <span data-ttu-id="71e5a-178">Należy pamiętać, że wartości *rand_value*, *ID* i *Secret* muszą zostać skopiowane do dostarczonych miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="71e5a-178">Note that the *rand_value*, *id*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="71e5a-179">**get_responder_values**: wskaźnik do funkcji aplikacji, która pobiera wartości używane do reagowania na wyzwanie.</span><span class="sxs-lookup"><span data-stu-id="71e5a-179">**get_responder_values**: Pointer to application function that retrieves values used to respond to a challenge.</span></span> <span data-ttu-id="71e5a-180">Należy zauważyć, że wartości *system*, *name* i *Secret* muszą zostać skopiowane do dostarczonych miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="71e5a-180">Note that the *system*, *name*, and *secret* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="71e5a-181">**get_verification_values**: wskaźnik do funkcji aplikacji pobierającej wartości używane do weryfikowania odpowiedzi na wezwanie.</span><span class="sxs-lookup"><span data-stu-id="71e5a-181">**get_verification_values**: Pointer to application function that retrieves values used to verify the challenge response.</span></span> <span data-ttu-id="71e5a-182">Należy zauważyć, że wartości *system*,*name* i *Secret* muszą zostać skopiowane do dostarczonych miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="71e5a-182">Note that the *system*,*name*, and *secret* values must be copied into the supplied destinations.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-183">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-183">Return Values</span></span>

- <span data-ttu-id="71e5a-184">**NX_SUCCESS**: (0X00) pomyślne włączenie protokołu CHAP PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-184">**NX_SUCCESS**: (0x00) Successful PPP CHAP enable</span></span>
- <span data-ttu-id="71e5a-185">**NX_NOT_IMPLEMENTED**: (0x80) logika protokołu CHAP została wyłączona za pośrednictwem NX_PPP_DISABLE_CHAP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-185">**NX_NOT_IMPLEMENTED**: (0x80) CHAP logic was disabled via NX_PPP_DISABLE_CHAP.</span></span>
- <span data-ttu-id="71e5a-186">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="71e5a-186">NX_PTR_ERROR: (0x07) Invalid PPP pointer or callback function pointer.</span></span> <span data-ttu-id="71e5a-187">Należy pamiętać, że jeśli *get_challenge_values* jest określony, należy również podać funkcję *get_verification_values* .</span><span class="sxs-lookup"><span data-stu-id="71e5a-187">Note that if *get_challenge_values* is specified, then the *get_verification_values* function must also be supplied.</span></span>
- <span data-ttu-id="71e5a-188">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-188">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-189">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-189">Allowed From</span></span>

<span data-ttu-id="71e5a-190">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-190">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-191">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-191">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a><span data-ttu-id="71e5a-192">nx_ppp_create</span><span class="sxs-lookup"><span data-stu-id="71e5a-192">nx_ppp_create</span></span>

<span data-ttu-id="71e5a-193">Tworzenie wystąpienia protokołu PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-193">Create a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-194">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-194">Prototype</span></span>

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a><span data-ttu-id="71e5a-195">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-195">Description</span></span>

<span data-ttu-id="71e5a-196">Ta usługa tworzy wystąpienie protokołu PPP dla określonego wystąpienia NetX IP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-196">This service creates a PPP instance for the specified NetX IP instance.</span></span> <span data-ttu-id="71e5a-197">Ta funkcja musi zostać wywołana przed utworzeniem wystąpienia adresu IP NetX.</span><span class="sxs-lookup"><span data-stu-id="71e5a-197">This function must be called prior to creating the NetX IP instance.</span></span>

>[!NOTE]
> <span data-ttu-id="71e5a-198">Zwykle dobrym pomysłem jest utworzenie wątku IP NetX o wyższym priorytecie niż priorytet wątku PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-198">It is generally a good idea to create the NetX IP thread at a higher priority than the PPP thread priority.</span></span> <span data-ttu-id="71e5a-199">Aby uzyskać więcej informacji na temat określania priorytetu wątku IP, zapoznaj się z usługą *nx_ip_create* .</span><span class="sxs-lookup"><span data-stu-id="71e5a-199">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-200">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-200">Input Parameters</span></span>

- <span data-ttu-id="71e5a-201">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-201">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-202">**name**: Nazwa tego wystąpienia protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-202">**name**: Name of this PPP instance.</span></span>
- <span data-ttu-id="71e5a-203">**ip_ptr**: wskaźnik kontroli dla niejeszcze utworzonego wystąpienia adresu IP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-203">**ip_ptr**: Pointer to control block for not-yet-created IP instance.</span></span>
- <span data-ttu-id="71e5a-204">**stack_memory_ptr**: wskaźnik do początku obszaru stosu wątku PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-204">**stack_memory_ptr**: Pointer to start of PPP thread’s stack area.</span></span>
- <span data-ttu-id="71e5a-205">**stack_size**: rozmiar w bajtach w stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="71e5a-205">**stack_size**: Size in bytes in the thread’s stack.</span></span>
- <span data-ttu-id="71e5a-206">**pool_ptr**: wskaźnik do domyślnej puli pakietów.</span><span class="sxs-lookup"><span data-stu-id="71e5a-206">**pool_ptr**: Pointer to default packet pool.</span></span>
- <span data-ttu-id="71e5a-207">**thread_priority**: priorytet wewnętrznych wątków PPP (1-31).</span><span class="sxs-lookup"><span data-stu-id="71e5a-207">**thread_priority**: Priority of internal PPP threads (1-31).</span></span>
- <span data-ttu-id="71e5a-208">**ppp_invalid_packet_handler**: wskaźnik funkcji do obsługi aplikacji dla wszystkich pakietów innych niż PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-208">**ppp_invalid_packet_handler**: Function pointer to application’s handler for all non-PPP packets.</span></span> <span data-ttu-id="71e5a-209">NetX PPP zazwyczaj wywołuje tę procedurę podczas inicjacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-209">The NetX PPP typically calls this routine during initialization.</span></span> <span data-ttu-id="71e5a-210">Jest to miejsce, w którym aplikacja może odpowiadać na polecenia modemowe lub w przypadku systemu Windows XP aplikacja NetX PPP może inicjować protokół PPP przez odpowiadanie na początkowy "klient", który jest wysyłany przez system Windows XP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-210">This is where the application can respond to modem commands or in the case of Windows XP, the NetX PPP application can initiate PPP by responding with“ CLIENT SERVER” to the initial “CLIENT” sent by Windows XP.</span></span>
- <span data-ttu-id="71e5a-211">**ppp_byte_send**: wskaźnik funkcji do procedury wyjściowej bajtów szeregowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-211">**ppp_byte_send**: Function pointer to application’s serial byte output routine.</span></span>


### <a name="return-values"></a><span data-ttu-id="71e5a-212">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-212">Return Values</span></span>

- <span data-ttu-id="71e5a-213">**NX_SUCCESS**: (0X00) pomyślne utworzenie protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-213">**NX_SUCCESS**: (0x00) Successful PPP create.</span></span>
- <span data-ttu-id="71e5a-214">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik funkcji danych wyjściowych PPP, IP lub Byte.</span><span class="sxs-lookup"><span data-stu-id="71e5a-214">NX_PTR_ERROR: (0x07) Invalid PPP, IP, or byte output function pointer.</span></span>
- <span data-ttu-id="71e5a-215">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-216">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-216">Allowed From</span></span>

<span data-ttu-id="71e5a-217">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-217">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-218">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-218">Example</span></span>

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a><span data-ttu-id="71e5a-219">nx_ppp_delete</span><span class="sxs-lookup"><span data-stu-id="71e5a-219">nx_ppp_delete</span></span>

<span data-ttu-id="71e5a-220">Usuwanie wystąpienia protokołu PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-220">Delete a PPP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-221">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-221">Prototype</span></span>

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-222">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-222">Description</span></span>

<span data-ttu-id="71e5a-223">Ta usługa usuwa poprzednio utworzone wystąpienie protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-223">This service deletes the previously created PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-224">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-224">Input Parameters</span></span>

- <span data-ttu-id="71e5a-225">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-225">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-226">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-226">Return Values</span></span>

- <span data-ttu-id="71e5a-227">**NX_SUCCESS**: (0X00) pomyślne usunięcie protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-227">**NX_SUCCESS**: (0x00) Successful PPP deletion.</span></span>
- <span data-ttu-id="71e5a-228">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-228">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="71e5a-229">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-229">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-230">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-230">Allowed From</span></span>

<span data-ttu-id="71e5a-231">Wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-232">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-232">Example</span></span>

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a><span data-ttu-id="71e5a-233">nx_ppp_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="71e5a-233">nx_ppp_dns_address_get</span></span>

<span data-ttu-id="71e5a-234">Pobierz adres IP serwera DNS</span><span class="sxs-lookup"><span data-stu-id="71e5a-234">Get DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-235">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-235">Prototype</span></span>

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-236">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-236">Description</span></span>

<span data-ttu-id="71e5a-237">Ta usługa Pobiera adres IP DNS dostarczony przez element równorzędny w uzgadnianiu IPCP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-237">This service retrieves the DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="71e5a-238">Jeśli adres IP nie został dostarczony przez element równorzędny, zwracany jest adres IP 0.</span><span class="sxs-lookup"><span data-stu-id="71e5a-238">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-239">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-239">Input Parameters</span></span>

- <span data-ttu-id="71e5a-240">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-240">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-241">**dns_address_ptr**: miejsce docelowe dla adresu serwera DNS</span><span class="sxs-lookup"><span data-stu-id="71e5a-241">**dns_address_ptr**: Destination for DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-242">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-242">Return Values</span></span>

- <span data-ttu-id="71e5a-243">**NX_SUCCESS**: (0X00) pomyślne uzyskanie adresu DNS.</span><span class="sxs-lookup"><span data-stu-id="71e5a-243">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="71e5a-244">**NX_PPP_NOT_ESTABLISHED**: (0XB5) Protokół PPP nie ukończył negocjacji z elementem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="71e5a-244">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="71e5a-245">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-245">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-246">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-246">Allowed From</span></span>

<span data-ttu-id="71e5a-247">Inicjalizacja, wątki, czasomierze, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71e5a-247">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-248">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-248">Example</span></span>

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a><span data-ttu-id="71e5a-249">nx_ppp_secondary_dns_address_get</span><span class="sxs-lookup"><span data-stu-id="71e5a-249">nx_ppp_secondary_dns_address_get</span></span>

<span data-ttu-id="71e5a-250">Pobierz adres IP pomocniczego serwera DNS</span><span class="sxs-lookup"><span data-stu-id="71e5a-250">Get Secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-251">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-251">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-252">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-252">Description</span></span>

<span data-ttu-id="71e5a-253">Ta usługa pobiera pomocniczy adres IP serwera DNS dostarczony przez element równorzędny w uzgadnianiu IPCP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-253">This service retrieves the secondary DNS IP address supplied by the peer in the IPCP handshake.</span></span> <span data-ttu-id="71e5a-254">Jeśli adres IP nie został dostarczony przez element równorzędny, zwracany jest adres IP 0.</span><span class="sxs-lookup"><span data-stu-id="71e5a-254">If no IP address was supplied by the peer, an IP address of 0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-255">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-255">Input Parameters</span></span>

- <span data-ttu-id="71e5a-256">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-256">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-257">**dns_address_ptr**: miejsce docelowe dla adresu pomocniczego serwera DNS</span><span class="sxs-lookup"><span data-stu-id="71e5a-257">**dns_address_ptr**: Destination for Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-258">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-258">Return Values</span></span>

- <span data-ttu-id="71e5a-259">**NX_SUCCESS**: (0X00) pomyślne uzyskanie adresu DNS.</span><span class="sxs-lookup"><span data-stu-id="71e5a-259">**NX_SUCCESS**: (0x00) Successful DNS address get.</span></span>
- <span data-ttu-id="71e5a-260">**NX_PPP_NOT_ESTABLISHED**: (0XB5) Protokół PPP nie ukończył negocjacji z elementem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="71e5a-260">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="71e5a-261">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-261">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-262">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-262">Allowed From</span></span>

<span data-ttu-id="71e5a-263">Inicjalizacja, wątki, czasomierze, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71e5a-263">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-264">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-264">Example</span></span>

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a><span data-ttu-id="71e5a-265">nx_ppp_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="71e5a-265">nx_ppp_dns_address_set</span></span>

<span data-ttu-id="71e5a-266">Ustaw adres IP podstawowego serwera DNS</span><span class="sxs-lookup"><span data-stu-id="71e5a-266">Set primary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-267">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-267">Prototype</span></span>

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="71e5a-268">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-268">Description</span></span>

<span data-ttu-id="71e5a-269">Ta usługa ustawia adres IP serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="71e5a-269">This service sets the DNS Server IP address.</span></span> <span data-ttu-id="71e5a-270">Jeśli element równorzędny wyśle żądanie opcji serwera DNS w stanie IPCP, ten host dostarczy informacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-270">If the peer sends a DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-271">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-271">Input Parameters</span></span>

- <span data-ttu-id="71e5a-272">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-272">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-273">**dns_address**: adres serwera DNS</span><span class="sxs-lookup"><span data-stu-id="71e5a-273">**dns_address**: DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-274">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-274">Return Values</span></span>

- <span data-ttu-id="71e5a-275">**NX_SUCCESS**: (0x00) pomyślny zbiór adresów DNS.</span><span class="sxs-lookup"><span data-stu-id="71e5a-275">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span>
- <span data-ttu-id="71e5a-276">**NX_PPP_NOT_ESTABLISHED**: (0XB5) Protokół PPP nie ukończył negocjacji z elementem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="71e5a-276">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="71e5a-277">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-277">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-278">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-278">Allowed From</span></span>

<span data-ttu-id="71e5a-279">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-279">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-280">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-280">Example</span></span>

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a><span data-ttu-id="71e5a-281">nx_ppp_secondary_dns_address_set</span><span class="sxs-lookup"><span data-stu-id="71e5a-281">nx_ppp_secondary_dns_address_set</span></span>

<span data-ttu-id="71e5a-282">Ustaw adres IP pomocniczego serwera DNS</span><span class="sxs-lookup"><span data-stu-id="71e5a-282">Set secondary DNS Server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-283">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-283">Prototype</span></span>

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a><span data-ttu-id="71e5a-284">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-284">Description</span></span>

<span data-ttu-id="71e5a-285">Ta usługa ustawia adres IP pomocniczego serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="71e5a-285">This service sets the secondary DNS Server IP address.</span></span> <span data-ttu-id="71e5a-286">Jeśli element równorzędny wyśle żądanie dodatkowej opcji serwera DNS w stanie IPCP, ten host dostarczy informacje.</span><span class="sxs-lookup"><span data-stu-id="71e5a-286">If the peer sends a secondary DNS Server option request in the IPCP state, this host will provide the information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-287">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-287">Input Parameters</span></span>

- <span data-ttu-id="71e5a-288">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-288">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-289">**dns_address**: pomocniczy adres serwera DNS</span><span class="sxs-lookup"><span data-stu-id="71e5a-289">**dns_address**: Secondary DNS server address</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-290">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-290">Return Values</span></span>

- <span data-ttu-id="71e5a-291">**NX_SUCCESS**: (0x00) pomyślny zbiór adresów DNS.</span><span class="sxs-lookup"><span data-stu-id="71e5a-291">**NX_SUCCESS**: (0x00) Successful DNS address set.</span></span> 
- <span data-ttu-id="71e5a-292">**NX_PPP_NOT_ESTABLISHED**: (0XB5) Protokół PPP nie ukończył negocjacji z elementem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="71e5a-292">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP has not completed negotiation with peer.</span></span>
- <span data-ttu-id="71e5a-293">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-293">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-294">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-294">Allowed From</span></span>

<span data-ttu-id="71e5a-295">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-296">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-296">Example</span></span>

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a><span data-ttu-id="71e5a-297">nx_ppp_interface_index_get</span><span class="sxs-lookup"><span data-stu-id="71e5a-297">nx_ppp_interface_index_get</span></span>

<span data-ttu-id="71e5a-298">Pobierz indeks interfejsu IP</span><span class="sxs-lookup"><span data-stu-id="71e5a-298">Get IP interface index</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-299">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-299">Prototype</span></span>

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-300">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-300">Description</span></span>

<span data-ttu-id="71e5a-301">Ta usługa Pobiera indeks interfejsu IP skojarzony z tym wystąpieniem protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-301">This service retrieves the IP interface index associated with this PPP instance.</span></span> <span data-ttu-id="71e5a-302">Jest to przydatne tylko wtedy, gdy wystąpienie protokołu PPP nie jest podstawowym interfejsem wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-302">This is only useful when the PPP instance is not the primary interface of an IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-303">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-303">Input Parameters</span></span>

- <span data-ttu-id="71e5a-304">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-304">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-305">**index_ptr**: miejsce docelowe dla indeksu interfejsu</span><span class="sxs-lookup"><span data-stu-id="71e5a-305">**index_ptr**: Destination for interface index</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-306">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-306">Return Values</span></span>

- <span data-ttu-id="71e5a-307">**NX_SUCCESS**: (0X00) pomyślne pobieranie indeksu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-307">**NX_SUCCESS**: (0x00) Successful PPP index get.</span></span>
- <span data-ttu-id="71e5a-308">**NX_IN_PROGRESS**: (0X37) Protokół PPP nie ukończył inicjacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-308">**NX_IN_PROGRESS**: (0x37) PPP has not completed initialization.</span></span>
- <span data-ttu-id="71e5a-309">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-309">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-310">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-310">Allowed From</span></span>

<span data-ttu-id="71e5a-311">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-311">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-312">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-312">Example</span></span>

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a><span data-ttu-id="71e5a-313">nx_ppp_ip_address_assign</span><span class="sxs-lookup"><span data-stu-id="71e5a-313">nx_ppp_ip_address_assign</span></span>

<span data-ttu-id="71e5a-314">Przypisywanie adresów IP do protokołu IPCP</span><span class="sxs-lookup"><span data-stu-id="71e5a-314">Assign IP addresses for IPCP</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-315">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-315">Prototype</span></span>

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a><span data-ttu-id="71e5a-316">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-316">Description</span></span>

<span data-ttu-id="71e5a-317">Ta usługa konfiguruje lokalne i równorzędne adresy IP do użycia w protokole protokołu kontroli ruchu internetowego (IPCP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-317">This service sets up the local and peer IP addresses for use in the Internet Protocol Control Protocol (IPCP.</span></span> <span data-ttu-id="71e5a-318">Należy ją wywołać dla wystąpienia protokołu PPP, które ma prawidłowe adresy IP dla siebie i drugiego elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="71e5a-318">It should be called for the PPP instance that has valid IP addresses for itself and the other peer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-319">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-319">Input Parameters</span></span>

- <span data-ttu-id="71e5a-320">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-320">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-321">**local_ip_address**: lokalny adres IP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-321">**local_ip_address**: Local IP address.</span></span>
- <span data-ttu-id="71e5a-322">**peer_ip_address**: adres IP elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="71e5a-322">**peer_ip_address**: Peer’s IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-323">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-323">Return Values</span></span>

- <span data-ttu-id="71e5a-324">**NX_SUCCESS**: (0X00) pomyślne przypisanie adresu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-324">**NX_SUCCESS**: (0x00) Successful PPP address assignment.</span></span>
- <span data-ttu-id="71e5a-325">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-325">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="71e5a-326">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-326">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-327">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-327">Allowed From</span></span>

<span data-ttu-id="71e5a-328">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-329">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-329">Example</span></span>

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a><span data-ttu-id="71e5a-330">nx_ppp_link_down_notify</span><span class="sxs-lookup"><span data-stu-id="71e5a-330">nx_ppp_link_down_notify</span></span>

<span data-ttu-id="71e5a-331">Powiadamiaj aplikację o linku w dół</span><span class="sxs-lookup"><span data-stu-id="71e5a-331">Notify application on link down</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-332">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-332">Prototype</span></span>

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a><span data-ttu-id="71e5a-333">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-333">Description</span></span>

<span data-ttu-id="71e5a-334">Ta usługa rejestruje wywołanie zwrotne powiadomienia o podłączeniu aplikacji z określonym wystąpieniem PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-334">This service registers the application’s link down notification callback with the specified PPP instance.</span></span> <span data-ttu-id="71e5a-335">Jeśli wartość nie jest równa NULL, funkcja wywołania zwrotnego łącza aplikacji jest wywoływana za każdym razem, gdy link zostanie wyłączony.</span><span class="sxs-lookup"><span data-stu-id="71e5a-335">If non-NULL, the application’s link down callback function is called whenever the link goes down.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-336">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-336">Input Parameters</span></span>

- <span data-ttu-id="71e5a-337">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-337">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-338">**link_down_callback**: wskaźnik funkcji powiadomień dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-338">**link_down_callback**: Application’s link down notification function pointer.</span></span> <span data-ttu-id="71e5a-339">Jeśli wartość jest równa NULL, powiadomienie o linku w dół jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="71e5a-339">If NULL, link down notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-340">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-340">Return Values</span></span>

- <span data-ttu-id="71e5a-341">**NX_SUCCESS**: (0X00) pomyślne łącze rejestracji wywołania zwrotnego powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="71e5a-341">**NX_SUCCESS**: (0x00) Successful link down notification callback registration.</span></span>
- <span data-ttu-id="71e5a-342">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-342">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-343">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-343">Allowed From</span></span>

<span data-ttu-id="71e5a-344">Inicjalizacja, wątki, czasomierze, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71e5a-344">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-345">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-345">Example</span></span>

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a><span data-ttu-id="71e5a-346">nx_ppp_link_up_notify</span><span class="sxs-lookup"><span data-stu-id="71e5a-346">nx_ppp_link_up_notify</span></span>

<span data-ttu-id="71e5a-347">Powiadamiaj aplikację przy połączeniu</span><span class="sxs-lookup"><span data-stu-id="71e5a-347">Notify application on link up</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-348">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-348">Prototype</span></span>

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a><span data-ttu-id="71e5a-349">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-349">Description</span></span>

<span data-ttu-id="71e5a-350">Ta usługa rejestruje połączenie zwrotne powiadomienia aplikacji z określonym wystąpieniem PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-350">This service registers the application’s link up notification callback with the specified PPP instance.</span></span> <span data-ttu-id="71e5a-351">Jeśli wartość jest inna niż NULL, funkcja wywołania zwrotnego linku aplikacji jest wywoływana za każdym razem, gdy zostanie wyświetlony link.</span><span class="sxs-lookup"><span data-stu-id="71e5a-351">If non-NULL, the application’s link up callback function is called whenever the link comes up.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-352">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-352">Input Parameters</span></span>

- <span data-ttu-id="71e5a-353">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-353">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-354">**link_up_callback**: wskaźnik funkcji powiadomień dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-354">**link_up_callback**: Application’s link up notification function pointer.</span></span> <span data-ttu-id="71e5a-355">Jeśli wartość jest równa NULL, powiadomienie o linku jest wyłączone. \* \*</span><span class="sxs-lookup"><span data-stu-id="71e5a-355">If NULL, link up notification is disabled.\*\*</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-356">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-356">Return Values</span></span>

- <span data-ttu-id="71e5a-357">**NX_SUCCESS**: (0X00) pomyślne łączenie rejestracji wywołania zwrotnego powiadomień.</span><span class="sxs-lookup"><span data-stu-id="71e5a-357">**NX_SUCCESS**: (0x00) Successful link up notification callback registration.</span></span>
- <span data-ttu-id="71e5a-358">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-358">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-359">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-359">Allowed From</span></span>

<span data-ttu-id="71e5a-360">Inicjalizacja, wątki, czasomierze, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71e5a-360">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-361">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-361">Example</span></span>

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a><span data-ttu-id="71e5a-362">nx_ppp_nak_authentication_notify</span><span class="sxs-lookup"><span data-stu-id="71e5a-362">nx_ppp_nak_authentication_notify</span></span>

<span data-ttu-id="71e5a-363">Powiadamiaj aplikację o otrzymaniu NAK uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="71e5a-363">Notify application if authentication NAK received</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-364">Prototype</span></span>

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a><span data-ttu-id="71e5a-365">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-365">Description</span></span>

<span data-ttu-id="71e5a-366">Ta usługa rejestruje wywołanie zwrotne powiadomienia nak uwierzytelniania aplikacji z określonym wystąpieniem PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-366">This service registers the application’s authentication nak notification callback with the specified PPP instance.</span></span> <span data-ttu-id="71e5a-367">Jeśli wartość jest inna niż NULL, ta funkcja wywołania zwrotnego jest wywoływana za każdym razem, gdy wystąpienie protokołu PPP odbiera NAK podczas authentiaction.</span><span class="sxs-lookup"><span data-stu-id="71e5a-367">If non-NULL, this callback function is called whenever the PPP instance receives a NAK during authentiaction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-368">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-368">Input Parameters</span></span>

- <span data-ttu-id="71e5a-369">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-369">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-370">**nak_authentication_notify**: wskaźnik do funkcji wywoływana, gdy wystąpienie protokołu PPP odbiera nak uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="71e5a-370">**nak_authentication_notify**: Pointer to function called when the PPP instance receives an authentication NAK.</span></span> <span data-ttu-id="71e5a-371">Jeśli wartość jest równa NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="71e5a-371">If NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-372">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-372">Return Values</span></span>

- <span data-ttu-id="71e5a-373">**NX_SUCCESS**: (0x00) pomyślna Rejestracja wywołania zwrotnego powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="71e5a-373">**NX_SUCCESS**: (0x00) Successful notification callback registration.</span></span>
- <span data-ttu-id="71e5a-374">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-374">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-375">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-375">Allowed From</span></span>

<span data-ttu-id="71e5a-376">Inicjalizacja, wątki, czasomierze, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71e5a-376">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-377">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-377">Example</span></span>

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a><span data-ttu-id="71e5a-378">nx_ppp_pap_enable</span><span class="sxs-lookup"><span data-stu-id="71e5a-378">nx_ppp_pap_enable</span></span>

<span data-ttu-id="71e5a-379">Włącz uwierzytelnianie PAP</span><span class="sxs-lookup"><span data-stu-id="71e5a-379">Enable PAP Authentication</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-380">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-380">Prototype</span></span>

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a><span data-ttu-id="71e5a-381">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-381">Description</span></span>

<span data-ttu-id="71e5a-382">Ta usługa włącza protokół uwierzytelniania hasła (PAP) dla określonego wystąpienia protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-382">This service enables the Password Authentication Protocol (PAP) for the specified PPP instance.</span></span> <span data-ttu-id="71e5a-383">Jeśli jest określony wskaźnik funkcji "***verify_login***", protokół PAP jest wymagany przez to wystąpienie protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-383">If the “***verify_login***” function pointer is specified, PAP is required by this PPP instance.</span></span> <span data-ttu-id="71e5a-384">W przeciwnym razie protokół PAP odpowiada wymaganiom protokołu PAP elementu równorzędnego określonym podczas negocjacji protokołu LCP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-384">Otherwise, PAP only responds to the peer’s PAP requirements as specified during LCP negotiation.</span></span>

<span data-ttu-id="71e5a-385">Poniżej przedstawiono kilka elementów danych, do których odwołuje się wymagana funkcja wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="71e5a-385">There are several data items referenced below in the required callback functions.</span></span> <span data-ttu-id="71e5a-386">Oczekiwano, że *Nazwa* elementu danych ma być ciągiem ZAKOŃCZONYM wartością null o maksymalnym rozmiarze NX_PPP_NAME_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="71e5a-386">The data item *name* is expected to be NULL-terminated string with a maximum size of NX_PPP_NAME_SIZE-1.</span></span> <span data-ttu-id="71e5a-387">Oczekiwane jest również, że *hasło* elementu danych będzie ciągiem ZAKOŃCZONYM wartością null o maksymalnym rozmiarze NX_PPP_PASSWORD_SIZE-1.</span><span class="sxs-lookup"><span data-stu-id="71e5a-387">The data item *password* is also expected to be a NULL-terminated string with a maximum size of NX_PPP_PASSWORD_SIZE-1.</span></span>

>[!NOTE]
> <span data-ttu-id="71e5a-388">Ta funkcja musi być wywoływana po *nx_ppp_create* , ale przed *nx_ip_create* lub *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="71e5a-388">This function must be called after *nx_ppp_create* but before *nx_ip_create* or *nx_ip_interface_attach*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-389">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-389">Input Parameters</span></span>

- <span data-ttu-id="71e5a-390">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-390">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-391">**generate_login**: wskaźnik do funkcji aplikacji, która tworzy *nazwę* i *hasło* na potrzeby uwierzytelniania przez element równorzędny.</span><span class="sxs-lookup"><span data-stu-id="71e5a-391">**generate_login**: Pointer to application function that produces a *name* and *password* for authentication by the peer.</span></span> <span data-ttu-id="71e5a-392">Należy pamiętać, że wartości *nazwy* i *hasła* muszą być skopiowane do dostarczonych miejsc docelowych.</span><span class="sxs-lookup"><span data-stu-id="71e5a-392">Note that the *name* and *password* values must be copied into the supplied destinations.</span></span>
- <span data-ttu-id="71e5a-393">**verify_login**: wskaźnik do funkcji aplikacji, która weryfikuje *nazwę* i *hasło* dostarczone przez element równorzędny.</span><span class="sxs-lookup"><span data-stu-id="71e5a-393">**verify_login**: Pointer to application function that verifies the *name* and *password* supplied by the peer.</span></span> <span data-ttu-id="71e5a-394">Ta procedura musi porównać podaną *nazwę* i *hasło*.</span><span class="sxs-lookup"><span data-stu-id="71e5a-394">This routine must compare the supplied *name* and *password*.</span></span> <span data-ttu-id="71e5a-395">Jeśli ta procedura zwróci NX_SUCCESS, nazwa i hasło są poprawne, a protokół PPP może przejść do następnego kroku.</span><span class="sxs-lookup"><span data-stu-id="71e5a-395">If this routine returns NX_SUCCESS, the name and password are correct and PPP can proceed to the next step.</span></span> <span data-ttu-id="71e5a-396">W przeciwnym razie ta procedura zwraca NX_PPP_ERROR i PPP czeka na inną nazwę i hasło.</span><span class="sxs-lookup"><span data-stu-id="71e5a-396">Otherwise, this routine returns NX_PPP_ERROR and PPP simply waits for another name and password.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-397">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-397">Return Values</span></span>

- <span data-ttu-id="71e5a-398">**NX_SUCCESS**: (0X00) pomyślne włączenie protokołu PPP PAP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-398">**NX_SUCCESS**: (0x00) Successful PPP PAP enable.</span></span>
- <span data-ttu-id="71e5a-399">**NX_NOT_IMPLEMENTED**: (0x80) logika PAP została wyłączona za pośrednictwem NX_PPP_DISABLE_PAP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-399">**NX_NOT_IMPLEMENTED**: (0x80) PAP logic was disabled via NX_PPP_DISABLE_PAP.</span></span>
- <span data-ttu-id="71e5a-400">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik funkcji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-400">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="71e5a-401">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-401">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-402">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-402">Allowed From</span></span>

<span data-ttu-id="71e5a-403">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-403">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-404">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-404">Example</span></span>

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a><span data-ttu-id="71e5a-405">nx_ppp_ping_request</span><span class="sxs-lookup"><span data-stu-id="71e5a-405">nx_ppp_ping_request</span></span>

<span data-ttu-id="71e5a-406">Wysyłanie żądania ping protokołu LCP</span><span class="sxs-lookup"><span data-stu-id="71e5a-406">Send an LCP ping request</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-407">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-407">Prototype</span></span>

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a><span data-ttu-id="71e5a-408">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-408">Description</span></span>

<span data-ttu-id="71e5a-409">Ta usługa wysyła żądanie LCP i ustawia flagę, którą urządzenie PPP oczekuje na odpowiedź ECHA.</span><span class="sxs-lookup"><span data-stu-id="71e5a-409">This service sends an LCP request and sets a flag that the PPP device is waiting for an echo response.</span></span> <span data-ttu-id="71e5a-410">Opcja oczekiwania dotyczy przede wszystkim wywołania *nx_packet_allocate* .</span><span class="sxs-lookup"><span data-stu-id="71e5a-410">The wait option is primarily for the *nx_packet_allocate* call.</span></span> <span data-ttu-id="71e5a-411">Usługa wraca natychmiast po wysłaniu żądania.</span><span class="sxs-lookup"><span data-stu-id="71e5a-411">The service returns as soon as the request is sent.</span></span> <span data-ttu-id="71e5a-412">Nie czeka na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="71e5a-412">It does not wait for a response.</span></span> 

<span data-ttu-id="71e5a-413">Po otrzymaniu zgodnej odpowiedzi echa zadanie wątku PPP wyczyści flagę.</span><span class="sxs-lookup"><span data-stu-id="71e5a-413">When a matching echo response is received, the PPP thread task will clear the flag.</span></span> <span data-ttu-id="71e5a-414">Urządzenie PPP musi zakończyć część LCP negocjacji protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-414">The PPP device must have completed the LCP part of the PPP negotiation.</span></span>

<span data-ttu-id="71e5a-415">Ta usługa jest przydatna w przypadku zestawów PPP, w których sondowanie sprzętu pod kątem stanu linku może nie być możliwe.</span><span class="sxs-lookup"><span data-stu-id="71e5a-415">This service is useful for PPP set ups where polling the hardware for link status may not be readily possible.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-416">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-416">Input Parameters</span></span>

- <span data-ttu-id="71e5a-417">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-417">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-418">**dane**: wskaźnik do danych do wysłania w żądaniu ECHA.</span><span class="sxs-lookup"><span data-stu-id="71e5a-418">**data**: Pointer to data to send in echo request.</span></span>
- <span data-ttu-id="71e5a-419">**data_size**: rozmiar danych do wysłania WAIT_OPTION czas oczekiwania na wysłanie komunikatu LCP echo.</span><span class="sxs-lookup"><span data-stu-id="71e5a-419">**data_size**: Size of data to send wait_option Time to wait to send the LCP echo message.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-420">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-420">Return Values</span></span>

- <span data-ttu-id="71e5a-421">**NX_SUCCESS**: (0X00) pomyślnie wysłano żądanie echa.</span><span class="sxs-lookup"><span data-stu-id="71e5a-421">**NX_SUCCESS**: (0x00) Successful sent echo request.</span></span>
- <span data-ttu-id="71e5a-422">**NX_PPP_NOT_ESTABLISHED**: nie ustanowiono połączenia PPP (0xB5).</span><span class="sxs-lookup"><span data-stu-id="71e5a-422">**NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP connection not established.</span></span>
- <span data-ttu-id="71e5a-423">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik funkcji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-423">NX_PTR_ERROR: (0x07) Invalid PPP pointer or application function pointer.</span></span>
- <span data-ttu-id="71e5a-424">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-424">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-425">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-425">Allowed From</span></span>

<span data-ttu-id="71e5a-426">Wątki aplikacji</span><span class="sxs-lookup"><span data-stu-id="71e5a-426">Application threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-427">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-427">Example</span></span>

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a><span data-ttu-id="71e5a-428">nx_ppp_raw_string_send</span><span class="sxs-lookup"><span data-stu-id="71e5a-428">nx_ppp_raw_string_send</span></span>

<span data-ttu-id="71e5a-429">Wyślij nieprzetworzony ciąg ASCII</span><span class="sxs-lookup"><span data-stu-id="71e5a-429">Send a raw ASCII string</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-430">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-430">Prototype</span></span>

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-431">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-431">Description</span></span>

<span data-ttu-id="71e5a-432">Ta usługa wysyła ciąg ASCII bez protokołu PPP bezpośrednio poza interfejsem PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-432">This service sends a non-PPP ASCII string directly out the PPP interface.</span></span> <span data-ttu-id="71e5a-433">Jest zazwyczaj używany po odebraniu przez protokół PPP pakietu, który zawiera informacje o kontrolkach modemu.</span><span class="sxs-lookup"><span data-stu-id="71e5a-433">It is typically used after PPP receives an non-PPP packet that contains modem control information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-434">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-434">Input Parameters</span></span>

- <span data-ttu-id="71e5a-435">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-435">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-436">**string_ptr**: wskaźnik do ciągu do wysłania.</span><span class="sxs-lookup"><span data-stu-id="71e5a-436">**string_ptr**: Pointer to string to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-437">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-437">Return Values</span></span>

- <span data-ttu-id="71e5a-438">**NX_SUCCESS**: (0X00) pomyślne wysyłanie ciągów nieprzetworzonych PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-438">**NX_SUCCESS**: (0x00) Successful PPP raw string send.</span></span>
- <span data-ttu-id="71e5a-439">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP lub wskaźnik ciągu.</span><span class="sxs-lookup"><span data-stu-id="71e5a-439">NX_PTR_ERROR: (0x07) Invalid PPP pointer or string pointer.</span></span>
- <span data-ttu-id="71e5a-440">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-440">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-441">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-441">Allowed From</span></span>

<span data-ttu-id="71e5a-442">Wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-442">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-443">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-443">Example</span></span>

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a><span data-ttu-id="71e5a-444">nx_ppp_restart</span><span class="sxs-lookup"><span data-stu-id="71e5a-444">nx_ppp_restart</span></span>

<span data-ttu-id="71e5a-445">Uruchom ponownie przetwarzanie PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-445">Restart PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-446">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-446">Prototype</span></span>

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-447">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-447">Description</span></span>

<span data-ttu-id="71e5a-448">Ta usługa ponownie uruchamia przetwarzanie PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-448">This service restarts the PPP processing.</span></span> <span data-ttu-id="71e5a-449">Jest on zazwyczaj wywoływany, gdy połączenie musi zostać ponownie nawiązane przy użyciu wywołania zwrotnego linku lub komunikatu z modemem innym niż PPP informującego o utracie komunikacji.</span><span class="sxs-lookup"><span data-stu-id="71e5a-449">It is typically called when the link needs to be re-established either from a link down callback or by a non-PPP modem message indicating communication was lost.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-450">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-450">Input Parameters</span></span>

- <span data-ttu-id="71e5a-451">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-451">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-452">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-452">Return Values</span></span>

- <span data-ttu-id="71e5a-453">**NX_SUCCESS**: (0X00) pomyślnie zainicjowano ponowne uruchomienie protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-453">**NX_SUCCESS**: (0x00) Successful PPP restart initiated.</span></span>
- <span data-ttu-id="71e5a-454">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-454">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="71e5a-455">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-455">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-456">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-456">Allowed From</span></span>

<span data-ttu-id="71e5a-457">Wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-457">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-458">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-458">Example</span></span>

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a><span data-ttu-id="71e5a-459">nx_ppp_start</span><span class="sxs-lookup"><span data-stu-id="71e5a-459">nx_ppp_start</span></span>

<span data-ttu-id="71e5a-460">Uruchom przetwarzanie PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-460">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-461">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-461">Prototype</span></span>

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-462">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-462">Description</span></span>

<span data-ttu-id="71e5a-463">Ta usługa uruchamia przetwarzanie PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-463">This service starts the PPP processing.</span></span> <span data-ttu-id="71e5a-464">Jest on zazwyczaj wywoływany po wywołaniu nx_ppp_stop ().</span><span class="sxs-lookup"><span data-stu-id="71e5a-464">It is typically called after nx_ppp_stop() called.</span></span>

>[!NOTE]
> <span data-ttu-id="71e5a-465">Protokół PPP automatycznie uruchamia przetwarzanie PPP, gdy łącze jest włączone.</span><span class="sxs-lookup"><span data-stu-id="71e5a-465">PPP automatically starts the PPP processing when the link is enabled.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-466">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-466">Input Parameters</span></span>

- <span data-ttu-id="71e5a-467">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-467">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-468">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-468">Return Values</span></span>

- <span data-ttu-id="71e5a-469">**NX_SUCCESS**: (0X00) pomyślnie zainicjowano uruchamianie protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-469">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="71e5a-470">**NX_PPP_ALREADY_STARTED**: (0XB9) Protokół PPP jest już uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="71e5a-470">**NX_PPP_ALREADY_STARTED**: (0xb9) PPP already started.</span></span>
- <span data-ttu-id="71e5a-471">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-471">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="71e5a-472">NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-472">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-473">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-473">Allowed From</span></span>

<span data-ttu-id="71e5a-474">Wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-474">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-475">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-475">Example</span></span>

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a><span data-ttu-id="71e5a-476">nx_ppp_status_get</span><span class="sxs-lookup"><span data-stu-id="71e5a-476">nx_ppp_status_get</span></span>

<span data-ttu-id="71e5a-477">Pobierz bieżący stan protokołu PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-477">Get current PPP status</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-478">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-478">Prototype</span></span>

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a><span data-ttu-id="71e5a-479">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-479">Description</span></span>

<span data-ttu-id="71e5a-480">Ta usługa Pobiera bieżący stan określonego wystąpienia protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-480">This service gets the current status of the specified PPP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-481">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-481">Input Parameters</span></span>

- <span data-ttu-id="71e5a-482">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-482">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-483">**STATUS_PTR**: miejsce docelowe dla stanu protokołu PPP, dostępne są następujące wartości stanu:</span><span class="sxs-lookup"><span data-stu-id="71e5a-483">**status_ptr**: Destination for the PPP status, the following are possible status values:</span></span>
    - <span data-ttu-id="71e5a-484">**NX_PPP_STATUS_ESTABLISHED**</span><span class="sxs-lookup"><span data-stu-id="71e5a-484">**NX_PPP_STATUS_ESTABLISHED**</span></span>
    - <span data-ttu-id="71e5a-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="71e5a-485">**NX_PPP_STATUS_LCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="71e5a-486">**NX_PPP_STATUS_LCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="71e5a-486">**NX_PPP_STATUS_LCP_FAILED**</span></span>
    - <span data-ttu-id="71e5a-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="71e5a-487">**NX_PPP_STATUS_PAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="71e5a-488">**NX_PPP_STATUS_PAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="71e5a-488">**NX_PPP_STATUS_PAP_FAILED**</span></span>
    - <span data-ttu-id="71e5a-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="71e5a-489">**NX_PPP_STATUS_CHAP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="71e5a-490">**NX_PPP_STATUS_CHAP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="71e5a-490">**NX_PPP_STATUS_CHAP_FAILED**</span></span>
    - <span data-ttu-id="71e5a-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span><span class="sxs-lookup"><span data-stu-id="71e5a-491">**NX_PPP_STATUS_IPCP_IN_PROGRESS**</span></span>
    - <span data-ttu-id="71e5a-492">**NX_PPP_STATUS_IPCP_FAILED**</span><span class="sxs-lookup"><span data-stu-id="71e5a-492">**NX_PPP_STATUS_IPCP_FAILED**</span></span>

>[!NOTE]
> <span data-ttu-id="71e5a-493">Stan jest prawidłowy tylko wtedy, gdy interfejs API zwraca NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="71e5a-493">The status is only valid if the API returns NX_SUCCESS.</span></span> <span data-ttu-id="71e5a-494">Ponadto, jeśli dowolna z wartości stanu \* _FAILED jest zwracana, przetwarzanie PPP jest skutecznie przerywane, dopóki nie zostanie ponownie uruchomione przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="71e5a-494">In addition, if any of the \*_FAILED status values are returned, PPP processing is effectively stopped until it is restarted again by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-495">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-495">Return Values</span></span>

- <span data-ttu-id="71e5a-496">**NX_SUCCESS**: (0X00) pomyślne żądanie stanu protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-496">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="71e5a-497">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-497">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-498">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-498">Allowed From</span></span>

<span data-ttu-id="71e5a-499">Inicjalizacja, wątki, czasomierze, procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71e5a-499">Initialization, threads, timers, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-500">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-500">Example</span></span>

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a><span data-ttu-id="71e5a-501">nx_ppp_stop</span><span class="sxs-lookup"><span data-stu-id="71e5a-501">nx_ppp_stop</span></span>

<span data-ttu-id="71e5a-502">Uruchom przetwarzanie PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-502">Start PPP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-503">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-503">Prototype</span></span>

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a><span data-ttu-id="71e5a-504">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-504">Description</span></span>

<span data-ttu-id="71e5a-505">Ta usługa przerywa przetwarzanie PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-505">This service stops the PPP processing.</span></span> <span data-ttu-id="71e5a-506">Użytkownik może także wywoływać nx_ppp_start (), aby uruchomić przetwarzanie PPP w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="71e5a-506">User also can calls nx_ppp_start() to start the PPP processing if needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-507">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-507">Input Parameters</span></span>

- <span data-ttu-id="71e5a-508">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-508">**ppp_ptr**: Pointer to PPP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-509">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-509">Return Values</span></span>

- <span data-ttu-id="71e5a-510">**NX_SUCCESS**: (0X00) pomyślnie zainicjowano uruchamianie protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-510">**NX_SUCCESS**: (0x00) Successful PPP start initiated.</span></span> 
- <span data-ttu-id="71e5a-511">**NX_PPP_ALREADY_STOPPED**: (0XB8) Protokół PPP został już zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="71e5a-511">**NX_PPP_ALREADY_STOPPED**: (0xb8) PPP already stopped.</span></span>
- <span data-ttu-id="71e5a-512">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-512">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>
- <span data-ttu-id="71e5a-513">NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="71e5a-513">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-514">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-514">Allowed From</span></span>

<span data-ttu-id="71e5a-515">Wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-515">Threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-516">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-516">Example</span></span>

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a><span data-ttu-id="71e5a-517">nx_ppp_packet_receive</span><span class="sxs-lookup"><span data-stu-id="71e5a-517">nx_ppp_packet_receive</span></span>

<span data-ttu-id="71e5a-518">Odbieranie pakietu protokołu PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-518">Receive PPP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-519">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-519">Prototype</span></span>

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a><span data-ttu-id="71e5a-520">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-520">Description</span></span>

<span data-ttu-id="71e5a-521">Ta usługa odbiera pakiet protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-521">This service receives PPP packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-522">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-522">Input Parameters</span></span>

- <span data-ttu-id="71e5a-523">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-523">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-524">**packet_ptr**: wskaźnik do pakietu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-524">**packet_ptr**: Pointer to PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-525">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-525">Return Values</span></span>

- <span data-ttu-id="71e5a-526">**NX_SUCCESS**: (0X00) pomyślne żądanie stanu protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-526">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="71e5a-527">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-527">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-528">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-528">Allowed From</span></span>

<span data-ttu-id="71e5a-529">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-529">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-530">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-530">Example</span></span>

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a><span data-ttu-id="71e5a-531">nx_ppp_packet_send_set</span><span class="sxs-lookup"><span data-stu-id="71e5a-531">nx_ppp_packet_send_set</span></span>

<span data-ttu-id="71e5a-532">Ustaw funkcję wysyłania pakietów protokołu PPP</span><span class="sxs-lookup"><span data-stu-id="71e5a-532">Set the PPP packet send function</span></span>

### <a name="prototype"></a><span data-ttu-id="71e5a-533">Prototype</span><span class="sxs-lookup"><span data-stu-id="71e5a-533">Prototype</span></span>

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a><span data-ttu-id="71e5a-534">Opis</span><span class="sxs-lookup"><span data-stu-id="71e5a-534">Description</span></span>

<span data-ttu-id="71e5a-535">Ta usługa ustawia ATANH wysyłania pakietów protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-535">This service sets the PPP packet send funciton.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="71e5a-536">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71e5a-536">Input Parameters</span></span>

- <span data-ttu-id="71e5a-537">**ppp_ptr**: wskaźnik do bloku kontroli PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-537">**ppp_ptr**: Pointer to PPP control block.</span></span>
- <span data-ttu-id="71e5a-538">**nx_ppp_packet_send**: procedura wysyłania pakietu protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-538">**nx_ppp_packet_send**: Routine to send PPP packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="71e5a-539">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71e5a-539">Return Values</span></span>

- <span data-ttu-id="71e5a-540">**NX_SUCCESS**: (0X00) pomyślne żądanie stanu protokołu PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-540">**NX_SUCCESS**: (0x00) Successful PPP status request.</span></span>
- <span data-ttu-id="71e5a-541">NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik PPP.</span><span class="sxs-lookup"><span data-stu-id="71e5a-541">NX_PTR_ERROR: (0x07) Invalid PPP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="71e5a-542">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71e5a-542">Allowed From</span></span>

<span data-ttu-id="71e5a-543">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="71e5a-543">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="71e5a-544">Przykład</span><span class="sxs-lookup"><span data-stu-id="71e5a-544">Example</span></span>

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```