---
title: Rozdział 4 — opis interfejsu API kryptografii usługi Azure RTO NetX
description: Opis interfejsu API kryptografii usługi Azure RTO NetX
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822716"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a><span data-ttu-id="a7eb4-103">Rozdział 4 — opis interfejsu API kryptografii usługi Azure RTO NetX</span><span class="sxs-lookup"><span data-stu-id="a7eb4-103">Chapter 4 - Azure RTOS NetX Crypto API description</span></span>

## <a name="nx_crypto_initialize"></a><span data-ttu-id="a7eb4-104">nx_crypto_initialize</span><span class="sxs-lookup"><span data-stu-id="a7eb4-104">nx_crypto_initialize</span></span>

<span data-ttu-id="a7eb4-105">Inicjuje bezpieczną bibliotekę NetX</span><span class="sxs-lookup"><span data-stu-id="a7eb4-105">Initializes the NetX Secure Library</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-106">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-106">Prototype</span></span>

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="a7eb4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-107">Description</span></span>

<span data-ttu-id="a7eb4-108">Ta funkcja Inicjuje moduł biblioteki kryptograficznej Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-108">This function initializes the Azure RTOS NetX Crypto library module.</span></span> <span data-ttu-id="a7eb4-109">Przed użyciem którejkolwiek z innych funkcji kryptograficznych, aplikacja musi wywołać tę funkcję, aby wykonać inicjalizację i zweryfikować integralność biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-109">Before using any of the other cryptographic functions, the application must call this function to perform initialization and to validate the integrity of the library.</span></span> <span data-ttu-id="a7eb4-110">Niepowodzenie wywołania tej funkcji przed użyciem innych usług kryptograficznych NetX spowoduje zwrócenie błędów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-110">Failure to call this function before using other NetX Crypto services will result in errors being returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-111">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-111">Parameters</span></span>

- <span data-ttu-id="a7eb4-112">**Brak**</span><span class="sxs-lookup"><span data-stu-id="a7eb4-112">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-113">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-113">Return Values</span></span>

- <span data-ttu-id="a7eb4-114">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie zainicjowano bibliotekę kryptograficzną NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-114">**NX_CRYPTO_SUCCESS** (0x00) Successful initialized NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-115">Funkcje biblioteki są teraz gotowe i mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-115">The library functions are now ready, and can be used.</span></span>
- <span data-ttu-id="a7eb4-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) nie można zainicjować biblioteki kryptograficznej lub błąd sprawdzania integralności.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library fails to initialize, or fails the integrity check.</span></span> <span data-ttu-id="a7eb4-117">Aplikacja nie może użyć tej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-117">Application cannot use this library.</span></span>

### <a name="example"></a><span data-ttu-id="a7eb4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7eb4-118">Example</span></span>

<span data-ttu-id="a7eb4-119">CZYNNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="a7eb4-119">TODO</span></span>

## <a name="nx_crypto_module_state_get"></a><span data-ttu-id="a7eb4-120">nx_crypto_module_state_get</span><span class="sxs-lookup"><span data-stu-id="a7eb4-120">nx_crypto_module_state_get</span></span>

<span data-ttu-id="a7eb4-121">Pobieranie bieżącego stanu modułu z obsługą FIPS</span><span class="sxs-lookup"><span data-stu-id="a7eb4-121">Retrieve the current status of the FIPS-enabled module</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-122">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-122">Prototype</span></span>

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a><span data-ttu-id="a7eb4-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-123">Description</span></span>

<span data-ttu-id="a7eb4-124">Ta usługa jest dostępna tylko w bibliotece kompilacji FIPS.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-124">This service is only available in the FIPS build library.</span></span> <span data-ttu-id="a7eb4-125">Zwraca stan bieżącego stanu biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-125">It returns the state of the current state of the NetX Crypto library.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-126">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-126">Parameters</span></span>

- <span data-ttu-id="a7eb4-127">**Brak**</span><span class="sxs-lookup"><span data-stu-id="a7eb4-127">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-128">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-128">Return Values</span></span>

- <span data-ttu-id="a7eb4-129">**Flaga stanu:**</span><span class="sxs-lookup"><span data-stu-id="a7eb4-129">**Status Flag:**</span></span>
  - <span data-ttu-id="a7eb4-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span><span class="sxs-lookup"><span data-stu-id="a7eb4-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span></span>
  - <span data-ttu-id="a7eb4-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span><span class="sxs-lookup"><span data-stu-id="a7eb4-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span></span>
  - <span data-ttu-id="a7eb4-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span><span class="sxs-lookup"><span data-stu-id="a7eb4-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span></span>
  - <span data-ttu-id="a7eb4-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span><span class="sxs-lookup"><span data-stu-id="a7eb4-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span></span>
  - <span data-ttu-id="a7eb4-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span><span class="sxs-lookup"><span data-stu-id="a7eb4-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span></span>
- <span data-ttu-id="a7eb4-135">**Wszystkie inne wartości są nieprawidłowe.**</span><span class="sxs-lookup"><span data-stu-id="a7eb4-135">**All other values are invalid.**</span></span>

### <a name="example"></a><span data-ttu-id="a7eb4-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7eb4-136">Example</span></span>

<span data-ttu-id="a7eb4-137">CZYNNOŚĆ</span><span class="sxs-lookup"><span data-stu-id="a7eb4-137">TODO</span></span>

## <a name="_nx_crypto_method_aes_init"></a><span data-ttu-id="a7eb4-138">_nx_crypto_method_aes_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-138">_nx_crypto_method_aes_init</span></span>

<span data-ttu-id="a7eb4-139">Inicjuje blok kontroli kryptograficznej AES</span><span class="sxs-lookup"><span data-stu-id="a7eb4-139">Initializes the AES crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-140">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-140">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-141">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-141">Description</span></span>

<span data-ttu-id="a7eb4-142">Ta funkcja inicjuje blok kontrolny AES z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-142">This function initializes the AES control block with the given key string.</span></span> <span data-ttu-id="a7eb4-143">Po zainicjowaniu bloku sterowania AES kolejna operacja AES będzie używać tego samego klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-143">Once the AES control block is initialized, subsequent AES operation will be using the same key and key size.</span></span>

<span data-ttu-id="a7eb4-144">Aplikacja może tworzyć wiele bloków formantów AES, każda reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-144">Application may create multiple AES control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-145">Klucz jest przypisywany do bloku sterującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-145">A key is assigned to a control block.</span></span> <span data-ttu-id="a7eb4-146">Kolejna operacja szyfrowania lub odszyfrowywania może odwoływać się do tego samego bloku kontrolki AES bez konieczności ponownego inicjowania bloku sterowania AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-146">Subsequent encryption or decryption operation can reference to the same AES control block without the need to re-initialize the AES control block.</span></span> <span data-ttu-id="a7eb4-147">Jeśli klucz sesji zostanie zmieniony, aplikacja musi ponownie zainicjować blok kontroli AES ze zaktualizowanym kluczem.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-147">If the key for the session is changed, application needs to re-initialize AES control block with the updated key.</span></span>

<span data-ttu-id="a7eb4-148">Wywołanie _ *nx_crypto_method_aes_init ()* automatycznie aktualizuje wcześniej skonfigurowany klucz i rozmiar klucza do nowego klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-148">Calling _ *nx_crypto_method_aes_init()* automatically updates a previously configured key and key size to the new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-149">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-149">Parameters</span></span>

- <span data-ttu-id="a7eb4-150">**Metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-150">**method** Pointer to a valid AES crypto method control block.</span></span> <span data-ttu-id="a7eb4-151">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne AES:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-151">The following pre-defined AES crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-152">*crypto_method_aes_cbc_128*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-152">*crypto_method_aes_cbc_128*</span></span>
  - <span data-ttu-id="a7eb4-153">*crypto_method_aes_cbc_192*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-153">*crypto_method_aes_cbc_192*</span></span>
  - <span data-ttu-id="a7eb4-154">*crypto_method_aes_cbc_256*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-154">*crypto_method_aes_cbc_256*</span></span>
  - <span data-ttu-id="a7eb4-155">*crypto_method_aes_ctr_128*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-155">*crypto_method_aes_ctr_128*</span></span>
  - <span data-ttu-id="a7eb4-156">*crypto_method_aes_ctr_192*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-156">*crypto_method_aes_ctr_192*</span></span>
  - <span data-ttu-id="a7eb4-157">*crypto_method_aes_ctr_256*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-157">*crypto_method_aes_ctr_256*</span></span>
  - <span data-ttu-id="a7eb4-158">*crypto_method_aes_xcbc_128*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-158">*crypto_method_aes_xcbc_128*</span></span>
  - <span data-ttu-id="a7eb4-159">*crypto_method_aes_ccm_8_128*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-159">*crypto_method_aes_ccm_8_128*</span></span>
- <span data-ttu-id="a7eb4-160">**klucz** Wskazuje bufor zawierający klucz AES</span><span class="sxs-lookup"><span data-stu-id="a7eb4-160">**key** Points to a buffer containing the AES key</span></span>
- <span data-ttu-id="a7eb4-161">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-161">**key_size_in_bits** Size of the key, in bits.</span></span> <span data-ttu-id="a7eb4-162">Prawidłowe wartości:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-162">Valid values are:</span></span>
  - <span data-ttu-id="a7eb4-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span></span>
  - <span data-ttu-id="a7eb4-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span></span>
  - <span data-ttu-id="a7eb4-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span></span>
  - <span data-ttu-id="a7eb4-166">**Wszystkie inne wartości są nieprawidłowe.**</span><span class="sxs-lookup"><span data-stu-id="a7eb4-166">**All other values are invalid.**</span></span>
- <span data-ttu-id="a7eb4-167">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-167">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-168">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-168">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-169">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-169">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-170">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-170">**crypto_metadata** Pointer to a valid memory space for the AES control block.</span></span> <span data-ttu-id="a7eb4-171">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-171">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-172">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-172">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-173">W przypadku algorytmu AES rozmiar metadanych musi mieć wartość *sizeof (NX_AES)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-173">For AES, the metadata size must be *sizeof(NX_AES)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-174">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-174">Return Values</span></span>

- <span data-ttu-id="a7eb4-175">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku kontrolki AES przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-175">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the AES control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-177">**NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-177">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-178">Rozmiar klucza **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) nie jest prawidłowy dla algorytmu AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for AES.</span></span>

## <a name="_nx_crypto_method_aes_operation"></a><span data-ttu-id="a7eb4-179">_nx_crypto_method_aes_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-179">_nx_crypto_method_aes_operation</span></span>

<span data-ttu-id="a7eb4-180">Wykonaj operację AES (szyfrowanie lub odszyfrowywanie).</span><span class="sxs-lookup"><span data-stu-id="a7eb4-180">Perform an AES operation (encryption or decryption).</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-181">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-182">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-182">Description</span></span>

<span data-ttu-id="a7eb4-183">Ta funkcja wykonuje operację szyfrowania lub odszyfrowywania AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-183">This function performs AES encryption or decryption operation.</span></span> <span data-ttu-id="a7eb4-184">Blok sterowania AES musi być zainicjowany przy użyciu _ *nx_crypto_method_aes_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-184">The AES control block must have been initialized with _ *nx_crypto_method_aes_init()*.</span></span> <span data-ttu-id="a7eb4-185">Algorytm AES ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-185">The AES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-186">Rozmiar buforu wejściowego musi być wielokrotnością 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-186">The input buffer size must be a multiple of 16 bytes.</span></span> <span data-ttu-id="a7eb4-187">Rozmiar odszyfrowanych danych ma taki sam rozmiar jak rozmiar danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-187">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="a7eb4-188">Jeśli zaszyfrowane dane zostały uzupełnione w celu osiągnięcia nawet wielokrotności rozmiaru bloku AES, uzupełnienie zostanie uwzględnione w buforze wyjściowym i musi być obsługiwane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-188">If the encrypted data was padded to achieve an even multiple of the AES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="a7eb4-189">Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku sterowania AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-189">This operation does not keep state information, and does not alter the key material in the AES control block.</span></span>

<span data-ttu-id="a7eb4-190">Gdy op jest NX_CRYPTO_SET_ADDITIONAL_DATA, a algoritm to AES-CCM8, punkty wejścia do dodatkowych danych i input_length_in_byte to długość dodatkowych danych.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-190">When the op is NX_CRYPTO_SET_ADDITIONAL_DATA and algoritm is AES-CCM8, the input points to additional data and input_length_in_byte is the length of additional data.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-191">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-191">Parameters</span></span>

- <span data-ttu-id="a7eb4-192">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-192">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-193">Prawidłowe Operations:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-193">Valid opertions are:</span></span>
  - <span data-ttu-id="a7eb4-194">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-194">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="a7eb4-195">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-195">*NX_CRYPTO_DECRYPT*</span></span>
  - <span data-ttu-id="a7eb4-196">*NX_CRYPTO_AUTHENTICATE (tylko algorytm AES-XCBC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-196">*NX_CRYPTO_AUTHENTICATE (AES-XCBC only)*</span></span>
  - <span data-ttu-id="a7eb4-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (tylko algorytm AES-CCM8)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 only)*</span></span>
- <span data-ttu-id="a7eb4-198">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-198">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-199">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-199">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-200">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-200">**method** Pointer to the valid AES crypto method.</span></span> <span data-ttu-id="a7eb4-201">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_aes_init ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-201">The crypto method used here must be the same used in the *nx_crypto_method_aes_init().*</span></span>
- <span data-ttu-id="a7eb4-202">**input_data** Wskazuje bufor zawierający dane zaszyfrowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-202">**input_data** Points to a buffer containing encrypted text data.</span></span> <span data-ttu-id="a7eb4-203">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-203">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-204">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-204">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="a7eb4-205">Rozmiar danych wejściowych musi być wielokrotnością 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-205">The input data size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="a7eb4-206">**iv_ptr** Wskaźnik do początkowego wektora.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-206">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="a7eb4-207">Nie ma żadnych ograniczeń dotyczących buforu IV.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-207">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="a7eb4-208">**iv_size** Rozmiar początkowego bloku wektora, w bajtach to pole musi być 16.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-208">**iv_size** Size of the Initial Vector block, in bytes This field must be 16.</span></span>
- <span data-ttu-id="a7eb4-209">**output_buffer** Wskaźnik do obszaru pamięci dla algorytmu AES, aby przechowywać dane w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-209">**output_buffer** Pointer to the memory area for AES to store the clear text data.</span></span> <span data-ttu-id="a7eb4-210">Aplikacja musi przydzielić miejsce dla buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-210">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="a7eb4-211">Bufor wyjściowy może nakładać się na bufor wejściowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-211">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="a7eb4-212">Bufor wyjściowy może nakładać się na bufor wejściowy, jeśli korzystają one z tego samego adresu początkowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-212">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="a7eb4-213">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-213">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="a7eb4-214">Rozmiar buforu wyjściowego musi być co najmniej taki sam jak rozmiar buforu wejściowego, a rozmiar buforu wyjściowego musi być wielokrotnością 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-214">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="a7eb4-215">**crypto_metadata** Wskaźnik do bloku kontrolki AES używanego w *_nx_crypto_method_aes_init () \* . \**</span><span class="sxs-lookup"><span data-stu-id="a7eb4-215">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>
- <span data-ttu-id="a7eb4-216">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-216">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-217">W przypadku algorytmu AES rozmiar metadanych musi mieć wartość *sizeof (NX_AES)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-217">For AES, the metadata size must *sizeof(NX_AES)*</span></span>
- <span data-ttu-id="a7eb4-218">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-218">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-219">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-219">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-220">**nx_crypto_hw_process_callback** — to pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-220">**nx_crypto_hw_process_callback** - This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-221">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-221">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-222">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-222">Return Values</span></span>

- <span data-ttu-id="a7eb4-223">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-223">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the AES operation.</span></span>
- <span data-ttu-id="a7eb4-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-225">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-225">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm AES \* \*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid AES algorithm being specified\*\*.</span></span>

## <a name="_nx_crypto_method_aes_cleanup"></a><span data-ttu-id="a7eb4-227">_nx_crypto_method_aes_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-227">_nx_crypto_method_aes_cleanup</span></span>

<span data-ttu-id="a7eb4-228">Wyczyść blok kontroli AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-228">Clean up the AES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-229">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-229">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-230">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-230">Description</span></span>

<span data-ttu-id="a7eb4-231">Aplikacja wywołuje tę funkcję, aby wyczyścić blok kontroli AES po ustaleniu, że ta sesja AES nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-231">Application calls this function to clean up the AES control block after it determines this AES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-232">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-232">Parameters</span></span>

- <span data-ttu-id="a7eb4-233">**crypto_metadata** Wskaźnik do bloku kontrolki AES używanego w *_nx_crypto_method_aes_init () \* . \**</span><span class="sxs-lookup"><span data-stu-id="a7eb4-233">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-234">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-234">Return Values</span></span>

- <span data-ttu-id="a7eb4-235">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję AES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-235">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the AES session.</span></span>
- <span data-ttu-id="a7eb4-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_3des_init"></a><span data-ttu-id="a7eb4-237">_nx_crypto_method_3des_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-237">_nx_crypto_method_3des_init</span></span>

<span data-ttu-id="a7eb4-238">Zainicjuj blok kontroli 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-238">Initialize the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-239">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-239">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-240">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-240">Description</span></span>

<span data-ttu-id="a7eb4-241">Ta funkcja inicjuje blok sterowania potrójnym algorytmem DES (3DES) z podanym trzema ciągami kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-241">This function initializes the Triple DES (3DES) control block with the given three key strings.</span></span> <span data-ttu-id="a7eb4-242">Ciągi kluczy muszą zawierać 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-242">The key strings must be 8 bytes each.</span></span> <span data-ttu-id="a7eb4-243">Trzy klucze DES muszą być połączone z ciągłą ilością pamięci w buforze 24-bajtowym.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-243">The three DES keys must be concatenated into contiguous memory of 24-byte buffer.</span></span> <span data-ttu-id="a7eb4-244">W przypadku kompilacji zgodnej ze standardem FIPS trzy klucze muszą być inne niż poszczególne lub funkcja zwróci błąd NX_CRYPTO_INVALID_KEY.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-244">For FIPS-compliant build, the three keys must be different from each or the function will return the NX_CRYPTO_INVALID_KEY error.</span></span> <span data-ttu-id="a7eb4-245">Po zainicjowaniu bloku sterowania algorytmem 3DES kolejne operacje 3DES będą używać tych samych kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-245">Once the 3DES control block is initialized, subsequent 3DES operations will use the same keys.</span></span>

<span data-ttu-id="a7eb4-246">Aplikacja może utworzyć wiele bloków sterujących algorytmem 3DES, z których każda reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-246">An application may create multiple 3DES control blocks, each representing a session.</span></span> <span data-ttu-id="a7eb4-247">Klucz jest przypisywany do bloku sterowania, a kolejne operacje szyfrowania lub odszyfrowywania mogą odwoływać się do tego samego bloku sterowania bez konieczności ponownego inicjowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-247">A key is assigned to a control block and subsequent encryption or decryption operations can reference the same control block without needing to re-initialize.</span></span> <span data-ttu-id="a7eb4-248">Jeśli klucz sesji zostanie zmieniony, aplikacja będzie musiała ponownie zainicjować blok kontroli ze zaktualizowanym kluczem.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-248">If the key for a session is changed, the application will need to re-initialize the control block with the updated key.</span></span>

<span data-ttu-id="a7eb4-249">Wywołanie _ *nx_crypto_method_3des_init ()* automatycznie aktualizuje wcześniej skonfigurowany klucz do nowych kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-249">Calling _ *nx_crypto_method_3des_init()* automatically updates a previously configured key to the new keys.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-250">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-250">Parameters</span></span>

- <span data-ttu-id="a7eb4-251">**Metoda** Wskaźnik do prawidłowego bloku kontroli metody szyfrowania 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-251">**method** Pointer to a valid 3DES crypto method control block.</span></span> <span data-ttu-id="a7eb4-252">Dostępna jest następująca wstępnie zdefiniowana Metoda kryptograficzna 3DES: ***crypto_method_3des***</span><span class="sxs-lookup"><span data-stu-id="a7eb4-252">The following pre-defined 3DES crypto method is available: ***crypto_method_3des***</span></span>
- <span data-ttu-id="a7eb4-253">**klucz** Wskazuje bufor zawierający trzy (3) klucz DES</span><span class="sxs-lookup"><span data-stu-id="a7eb4-253">**key** Points to a buffer containing the three (3) DES key</span></span>
- <span data-ttu-id="a7eb4-254">**key_size_in_bits** Musi być 192 (3 klucze, każdy 64 bitów).</span><span class="sxs-lookup"><span data-stu-id="a7eb4-254">**key_size_in_bits** Must be 192 (3 keys, each 64 bits).</span></span>
- <span data-ttu-id="a7eb4-255">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-255">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-256">Dojście identyfikuje blok kontroli 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-256">The handle identifies the 3DES control block being initialized.</span></span> <span data-ttu-id="a7eb4-257">Kolejne operacje 3DES (szyfrowanie, odszyfrowywanie i czyszczenie) używają tego uchwytu do uzyskiwania dostępu do bloku sterowania 3DES</span><span class="sxs-lookup"><span data-stu-id="a7eb4-257">Subsequent 3DES operations (encryption, decryption, and cleanup) use this handle to access the 3DES control block</span></span>
- <span data-ttu-id="a7eb4-258">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-258">**crypto_metadata** Pointer to a valid memory space for the 3DES control block.</span></span> <span data-ttu-id="a7eb4-259">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-259">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-260">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-260">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-261">W przypadku algorytmu 3DES rozmiar metadanych musi mieć wartość *sizeof (NX_3DES)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-261">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>

### <a name="return-value"></a><span data-ttu-id="a7eb4-262">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7eb4-262">Return Value</span></span>

- <span data-ttu-id="a7eb4-263">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku kontroli 3DES z rozmiarem klucza i klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-263">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-265">**NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-265">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-266">Rozmiar klucza **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) nie jest prawidłowy dla algorytmu 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for 3DES.</span></span>

## <a name="_nx_crypto_method_3des_operation"></a><span data-ttu-id="a7eb4-267">_nx_crypto_method_3des_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-267">_nx_crypto_method_3des_operation</span></span>

<span data-ttu-id="a7eb4-268">Szyfrowanie lub odszyfrowywanie przy użyciu algorytmu 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-268">Encrypt or Decrypt with 3DES.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-269">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-269">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-270">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-270">Description</span></span>

<span data-ttu-id="a7eb4-271">Ta funkcja wykonuje operacje szyfrowania 3DES lub odszyfrowywania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-271">This function performs 3DES encryption or decryption operation.</span></span> <span data-ttu-id="a7eb4-272">Blok kontroli 3DES musi być zainicjowany przy użyciu _ *nx_crypto_method_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-272">The 3DES control block must have been initialized with _ *nx_crypto_method_3des_init()*.</span></span> <span data-ttu-id="a7eb4-273">Algorytm 3DES ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-273">The 3DES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-274">Rozmiar buforu wejściowego musi być wielokrotnością 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-274">The input buffer size must be a multiple of 8 bytes.</span></span> <span data-ttu-id="a7eb4-275">Rozmiar odszyfrowanych danych ma taki sam rozmiar jak rozmiar danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-275">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="a7eb4-276">Jeśli zaszyfrowane dane zostały uzupełnione w celu osiągnięcia nawet wielokrotności rozmiaru bloku 3DES, uzupełnienie zostanie uwzględnione w buforze wyjściowym i musi być obsługiwane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-276">If the encrypted data was padded to achieve an even multiple of the 3DES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="a7eb4-277">Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku kontroli 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-277">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-278">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-278">Parameters</span></span>

- <span data-ttu-id="a7eb4-279">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-279">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-280">Prawidłowe operacje:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-280">Valid operations are:</span></span>
  - <span data-ttu-id="a7eb4-281">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-281">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="a7eb4-282">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-282">*NX_CRYPTO_DECRYPT*</span></span>
- <span data-ttu-id="a7eb4-283">**Obsługa** Dojście zainicjowane przez *_nx_crypto_method_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-283">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="a7eb4-284">**Metoda** Wskaźnik do prawidłowej metody szyfrowania 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-284">**method** Pointer to the valid 3DES crypto method.</span></span> <span data-ttu-id="a7eb4-285">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_3des_init ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-285">The crypto method used here must be the same used in the *nx_crypto_method_3des_init().*</span></span>
- <span data-ttu-id="a7eb4-286">**input_data** Wskazuje bufor zawierający dane zaszyfrowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-286">**input_data** Points to a buffer containing encrypted text data.</span></span>
<span data-ttu-id="a7eb4-287">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-287">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-288">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-288">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="a7eb4-289">Rozmiar danych wejściowych musi być wielokrotnością 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-289">The input data size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="a7eb4-290">**iv_ptr** Wskaźnik do początkowego wektora.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-290">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="a7eb4-291">Nie ma żadnych ograniczeń dotyczących buforu IV.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-291">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="a7eb4-292">**iv_size** Rozmiar początkowego bloku wektora, w bajtach to pole musi zawierać wartość 8.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-292">**iv_size** Size of the Initial Vector block, in bytes This field must be 8.</span></span>
- <span data-ttu-id="a7eb4-293">**output_buffer** Wskaźnik do obszaru pamięci dla algorytmu 3DES do przechowywania danych w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-293">**output_buffer** Pointer to the memory area for 3DES to store the clear text data.</span></span> <span data-ttu-id="a7eb4-294">Aplikacja musi przydzielić miejsce dla buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-294">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="a7eb4-295">Bufor wyjściowy może nakładać się na bufor wejściowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-295">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="a7eb4-296">Bufor wyjściowy może nakładać się na bufor wejściowy, jeśli korzystają one z tego samego adresu początkowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-296">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="a7eb4-297">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-297">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="a7eb4-298">Rozmiar buforu wyjściowego musi być co najmniej taki sam jak rozmiar buforu wejściowego, a rozmiar buforu wyjściowego musi być wielokrotnością 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-298">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="a7eb4-299">**crypto_metadata** Wskaźnik do bloku sterowania algorytmem 3DES używanym w *_nx_crypto_method_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-299">**crypto_metadata** Pointer to the 3DES control block used in *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="a7eb4-300">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-300">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-301">W przypadku algorytmu 3DES rozmiar metadanych musi mieć wartość *sizeof (NX_3DES)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-301">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>
- <span data-ttu-id="a7eb4-302">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-302">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-303">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-303">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-304">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-304">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-305">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-305">Any values passed in are silently ignored.</span></span>

### <a name="description"></a><span data-ttu-id="a7eb4-306">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-306">Description</span></span>

<span data-ttu-id="a7eb4-307">Ta funkcja wykonuje szyfrowanie 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-307">This function performs 3DES encryption.</span></span> <span data-ttu-id="a7eb4-308">Blok kontroli 3DES musi być zainicjowany przy użyciu _ *nx_crypto_moethod_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-308">The 3DES control block must have been initialized with _ *nx_crypto_moethod_3des_init()*.</span></span> <span data-ttu-id="a7eb4-309">Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku kontroli 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-309">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span> <span data-ttu-id="a7eb4-310">Należy zauważyć, że uzupełnienie nie jest dodawane przez tę funkcję, więc obiekt wywołujący będzie musiał obsłużyć uzupełnienie przed wywołaniem operacji szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-310">Note that padding is not added by this function so the caller will need to handle padding before invoking the encryption operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-311">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-311">Return Values</span></span>

- <span data-ttu-id="a7eb4-312">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku kontroli 3DES z rozmiarem klucza i klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-312">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-314">**NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-314">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_3des_cleanup"></a><span data-ttu-id="a7eb4-315">_nx_crypto_method_3des_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-315">_nx_crypto_method_3des_cleanup</span></span>

<span data-ttu-id="a7eb4-316">Wyczyść blok kontroli 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-316">Clean up the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-317">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-317">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-318">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-318">Description</span></span>

<span data-ttu-id="a7eb4-319">Aplikacja wywołuje tę funkcję, aby oczyścić blok kontroli 3DES po ustaleniu, że ta sesja 3DES nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-319">Application calls this function to clean up the 3DES control block after it determines this 3DES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-320">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-320">Parameters</span></span>

- <span data-ttu-id="a7eb4-321">**Obsługa** Dojście zainicjowane przez *_nx_crypto_method_3des_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-321">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-322">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-322">Return Values</span></span>

- <span data-ttu-id="a7eb4-323">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję 3DES.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-323">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the 3DES session.</span></span>
- <span data-ttu-id="a7eb4-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_drbg_init"></a><span data-ttu-id="a7eb4-325">_nx_crypto_method_drbg_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-325">_nx_crypto_method_drbg_init</span></span>

<span data-ttu-id="a7eb4-326">Inicjuje blok kontroli kryptografii DRBG</span><span class="sxs-lookup"><span data-stu-id="a7eb4-326">Initializes the DRBG crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-327">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-327">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-328">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-328">Description</span></span>

<span data-ttu-id="a7eb4-329">Ta funkcja inicjuje blok sterowania DRBG z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-329">This function initializes the DRBG control block with the given key string.</span></span> <span data-ttu-id="a7eb4-330">Po zainicjowaniu bloku sterowania DRBG kolejna operacja DRBG będzie używać tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-330">Once the DRBG control block is initialized, subsequent DRBG operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-331">Aplikacja może utworzyć wiele bloków sterujących DRBG, każda reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-331">Application may create multiple DRBG control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-332">Inicjalizacja bloku sterowania DRBG uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-332">Initializing the DRBG control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-333">Ponowne inicjowanie bloku sterowania DRBG porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-333">Re-initializing the DRBG control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-334">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-334">Parameters</span></span>

- <span data-ttu-id="a7eb4-335">**Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-335">**method** Pointer to a valid DRBG crypto method control block.</span></span> <span data-ttu-id="a7eb4-336">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-336">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-337">*crypto_method_drbg*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-337">*crypto_method_drbg*</span></span>
- <span data-ttu-id="a7eb4-338">**klucz** To pole nie jest używane w przypadku DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-338">**key** This field is not used for DRBG.</span></span>
- <span data-ttu-id="a7eb4-339">**key_size_in_bits** To pole nie jest używane w przypadku DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-339">**key_size_in_bits** This field is not used for DRBG.</span></span>
- <span data-ttu-id="a7eb4-340">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-340">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-341">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-341">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-342">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-342">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-343">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-343">**crypto_metadata** Pointer to a valid memory space for the DRBG control block.</span></span> <span data-ttu-id="a7eb4-344">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-344">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-345">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-345">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-346">W przypadku DRBG rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_DRBG)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-346">For DRBG, the metadata size must be *sizeof(NX_CRYPTO_DRBG)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-347">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-347">Return Values</span></span>

- <span data-ttu-id="a7eb4-348">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania DRBG przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-348">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the DRBG control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-350">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-350">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_drbg_operation"></a><span data-ttu-id="a7eb4-351">_nx_crypto_method_drbg_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-351">_nx_crypto_method_drbg_operation</span></span>

<span data-ttu-id="a7eb4-352">Wykonaj operację DRBG</span><span class="sxs-lookup"><span data-stu-id="a7eb4-352">Perform DRBG operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-353">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-353">Prototype</span></span>

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-354">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-354">Description</span></span>

<span data-ttu-id="a7eb4-355">Ta funkcja wykonuje operację DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-355">This function performs DRBG operation.</span></span> <span data-ttu-id="a7eb4-356">Blok sterowania DRBG musi zostać zainicjowany przy użyciu _ *nx_crypto_method_drbg_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-356">The DRBG control block must have been initialized with _ *nx_crypto_method_drbg_init()*.</span></span> <span data-ttu-id="a7eb4-357">Algorytm DRBG ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-357">The DRBG algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span> <span data-ttu-id="a7eb4-358">Domyślnie algorytm AES-128 jest używany dla DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-358">By default AES-128 is used for DRBG.</span></span>

<span data-ttu-id="a7eb4-359">Gdy operacja jest NX_CRYPTO_DRBG_OPTIONS_SET, punkty wejścia do NX_CRYPTO_DRBG_OPTIONS struktury.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-359">When the operation is NX_CRYPTO_DRBG_OPTIONS_SET, the input points to NX_CRYPTO_DRBG_OPTIONS structure.</span></span> <span data-ttu-id="a7eb4-360">Gdy operacja jest NX_CRYPTO_DRBG_INSTANTIATE, klucz wskazuje identyfikator jednorazowy, punkty wejścia do ciągu personalizacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-360">When the operation is NX_CRYPTO_DRBG_INSTANTIATE, the key points to nonce, input points to personalization string.</span></span> <span data-ttu-id="a7eb4-361">Gdy operacja jest NX_CRYPTO_DRBG_RESEED lub NX_CRYPTO_DRBG_GENERATE, punkty wejścia wskazują dodatkowe dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-361">When the operation is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, the input points to additional input.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-362">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-362">Parameters</span></span>

- <span data-ttu-id="a7eb4-363">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-363">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-364">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-364">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span></span>
  - <span data-ttu-id="a7eb4-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span></span>
  - <span data-ttu-id="a7eb4-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span></span>
- <span data-ttu-id="a7eb4-368">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-368">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-369">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-369">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-370">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-370">**method** Pointer to the valid DRBG crypto method.</span></span> <span data-ttu-id="a7eb4-371">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_drbg_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-371">The crypto method used here must be the same used in the _ *nx_crypto_method_drbg_init().*</span></span>
- <span data-ttu-id="a7eb4-372">**klucz** Wskaźnik na identyfikator jednorazowy operacji tworzenia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-372">**key** Pointer to the the nonce for the instantiate operation.</span></span> <span data-ttu-id="a7eb4-373">To pole nie jest używane w przypadku innych operacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-373">This field is not used for other operations.</span></span>
- <span data-ttu-id="a7eb4-374">**key_size_in_bits** Rozmiar identyfikatora jednorazowego w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-374">**key_size_in_bits** Size of the nonce, in bits.</span></span> <span data-ttu-id="a7eb4-375">To pole nie jest używane w przypadku innych operacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-375">This field is not used for other operations.</span></span>
- <span data-ttu-id="a7eb4-376">**dane wejściowe** Gdy jest NX_CRYPTO_DRBG_OPTIONS_SET, to pole wskazuje opcje DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-376">**input** When op is NX_CRYPTO_DRBG_OPTIONS_SET, this field points to DRBG options.</span></span> <span data-ttu-id="a7eb4-377">Gdy jest NX_CRYPTO_DRBG_INSTANTIATE, to pole wskazuje ciąg personalizacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-377">When op is NX_CRYPTO_DRBG_INSTANTIATE, this field points to personalization string.</span></span> <span data-ttu-id="a7eb4-378">Gdy op jest NX_CRYPTO_DRBG_RESEED lub NX_CRYPTO_DRBG_GENERATE, to pole wskazuje dodatkowe dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-378">When op is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, this field points to additional input data.</span></span>
- <span data-ttu-id="a7eb4-379">**input_length_in_byte** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-379">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-380">**iv_ptr** To pole nie jest używane w przypadku DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-380">**iv_ptr** This field is not used for DRBG.</span></span>
- <span data-ttu-id="a7eb4-381">**dane wyjściowe** Gdy operacja jest NX_CRYPTO_DRBG_GENERATE, to pole wskazuje obszar pamięci dla wygenerowanego DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-381">**output** When op is NX_CRYPTO_DRBG_GENERATE, this field points to the memory area for the generated DRBG.</span></span> <span data-ttu-id="a7eb4-382">W przeciwnym razie to pole nie jest używane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-382">Otherwise, this field is not used.</span></span>
- <span data-ttu-id="a7eb4-383">**output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-383">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="a7eb4-384">**crypto_metadata** Wskaźnik do bloku sterowania DRBG używany w *_nx_crypto_method_drbg_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-384">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>
- <span data-ttu-id="a7eb4-385">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-385">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-386">W przypadku DRBG rozmiar metadanych musi być *sizeof (NX_CRYPTO_DRBG)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-386">For DRBG, the metadata size must *sizeof(NX_CRYPTO_DRBG)*</span></span>
- <span data-ttu-id="a7eb4-387">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-387">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-388">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-388">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-389">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-389">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-390">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-390">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-391">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-391">Return Values</span></span>

- <span data-ttu-id="a7eb4-392">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-392">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the DRBG operation.</span></span>
- <span data-ttu-id="a7eb4-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-394">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-394">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid DRBG algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_drbg_cleanup"></a><span data-ttu-id="a7eb4-397">_nx_crypto_method_drbg_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-397">_nx_crypto_method_drbg_cleanup</span></span>

<span data-ttu-id="a7eb4-398">Wyczyść blok sterowania DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-398">Clean up the DRBG control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-399">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-399">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-400">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-400">Description</span></span>

<span data-ttu-id="a7eb4-401">Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania DRBG po ustaleniu, że ta sesja DRBG nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-401">Application calls this function to clean up the DRBG control block after it determines this DRBG session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-402">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-402">Parameters</span></span>

- <span data-ttu-id="a7eb4-403">**crypto_metadata** Wskaźnik do bloku sterowania DRBG używany w *_nx_crypto_method_drbg_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-403">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-404">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-404">Return Values</span></span>

- <span data-ttu-id="a7eb4-405">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję DRBG.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-405">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the DRBG session.</span></span>
- <span data-ttu-id="a7eb4-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdh_init"></a><span data-ttu-id="a7eb4-407">_nx_crypto_method_ecdh_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-407">_nx_crypto_method_ecdh_init</span></span>

<span data-ttu-id="a7eb4-408">Inicjuje blok kontroli kryptografii ECDH</span><span class="sxs-lookup"><span data-stu-id="a7eb4-408">Initializes the ECDH crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-409">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-409">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-410">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-410">Description</span></span>

<span data-ttu-id="a7eb4-411">Ta funkcja inicjuje blok sterowania ECDH z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-411">This function initializes the ECDH control block with the given key string.</span></span> <span data-ttu-id="a7eb4-412">Po zainicjowaniu bloku sterowania ECDH kolejna operacja ECDH będzie używać tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-412">Once the ECDH control block is initialized, subsequent ECDH operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-413">Aplikacja może utworzyć wiele bloków sterujących ECDH, każda reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-413">Application may create multiple ECDH control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-414">Inicjalizacja bloku sterowania ECDH uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-414">Initializing the ECDH control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-415">Ponowne inicjowanie bloku sterowania ECDH porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-415">Re-initializing the ECDH control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-416">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-416">Parameters</span></span>

- <span data-ttu-id="a7eb4-417">**Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-417">**method** Pointer to a valid ECDH crypto method control block.</span></span> <span data-ttu-id="a7eb4-418">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-418">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-419">*crypto_method_ecdh*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-419">*crypto_method_ecdh*</span></span>
- <span data-ttu-id="a7eb4-420">**klucz** To pole nie jest używane w przypadku ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-420">**key** This field is not used for ECDH.</span></span>
- <span data-ttu-id="a7eb4-421">**key_size_in_bits** To pole nie jest używane w przypadku ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-421">**key_size_in_bits** This field is not used for ECDH.</span></span>
- <span data-ttu-id="a7eb4-422">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-422">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-423">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-423">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-424">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-424">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-425">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-425">**crypto_metadata** Pointer to a valid memory space for the ECDH control block.</span></span> <span data-ttu-id="a7eb4-426">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-426">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-427">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-427">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-428">W przypadku ECDH rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_ECDH)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-428">For ECDH, the metadata size must be *sizeof(NX_CRYPTO_ECDH)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-429">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-429">Return Values</span></span>

- <span data-ttu-id="a7eb4-430">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania ECDH przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-430">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDH control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-432">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-432">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdh_operation"></a><span data-ttu-id="a7eb4-433">_nx_crypto_method_ecdh_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-433">_nx_crypto_method_ecdh_operation</span></span>

<span data-ttu-id="a7eb4-434">Wykonaj operację ECDH</span><span class="sxs-lookup"><span data-stu-id="a7eb4-434">Perform ECDH operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-435">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-435">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-436">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-436">Description</span></span>

<span data-ttu-id="a7eb4-437">Ta funkcja wykonuje operację ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-437">This function performs ECDH operation.</span></span> <span data-ttu-id="a7eb4-438">Blok sterowania ECDH musi zostać zainicjowany przy użyciu _ *nx_crypto_method_ecdh_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-438">The ECDH control block must have been initialized with _ *nx_crypto_method_ecdh_init()*.</span></span> <span data-ttu-id="a7eb4-439">Algorytm ECDH ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-439">The ECDH algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-440">Gdy operacja jest NX_CRYPTO_EC_CURVE_SET, punkty wejścia do metody kryptograficznej krzywej eliptycznej.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-440">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="a7eb4-441">Gdy operacja jest NX_CRYPTO_EC_KEY_PAIR_GENERATE, punkty wyjścia do struktury NX_CRYPTO_EXTENDED_OUTPUT i pary kluczy są kopiowane do nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-441">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="a7eb4-442">Gdy operacja jest NX_CRYPTO_DH_SETUP, klucz publiczny jest zwracany do nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-442">When the operation is NX_CRYPTO_DH_SETUP, the public key is returned to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="a7eb4-443">Gdy operacja jest NX_CRYPTO_DH_KEY_PAIR_IMPORT, punkty wejścia do klucza publicznego i klucza do klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-443">When the operation is NX_CRYPTO_DH_KEY_PAIR_IMPORT, the input points to public key and key points to private key.</span></span> <span data-ttu-id="a7eb4-444">Gdy operacja jest NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, klucz prywatny jest kopiowany do nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-444">When the operation is NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, the private key is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="a7eb4-445">Gdy operacja jest NX_CRYPTO_DH_CALCULATE, punkty wejścia do zdalnego klucza publicznego i wspólny klucz tajny są kopiowane do nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-445">When the operation is NX_CRYPTO_DH_CALCULATE, the input points to remote public key and the shared secret is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-446">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-446">Parameters</span></span>

- <span data-ttu-id="a7eb4-447">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-447">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-448">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-448">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-449">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-449">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="a7eb4-450">*NX_CRYPTO_DH_SETUP*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-450">*NX_CRYPTO_DH_SETUP*</span></span>
  - <span data-ttu-id="a7eb4-451">*NX_CRYPTO_DH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-451">*NX_CRYPTO_DH_CALCULATE*</span></span>
  - <span data-ttu-id="a7eb4-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span></span>
  - <span data-ttu-id="a7eb4-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span></span>
  - <span data-ttu-id="a7eb4-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span></span>
- <span data-ttu-id="a7eb4-455">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-455">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-456">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-456">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-457">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-457">**method** Pointer to the valid ECDH crypto method.</span></span> <span data-ttu-id="a7eb4-458">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_ecdh_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-458">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdh_init().*</span></span>
- <span data-ttu-id="a7eb4-459">**klucz** Gdy jest NX_CRYPTO_DH_IMPORT_KEY_PAIR, to pole wskazuje na klucz prywatny.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-459">**key** When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to private key.</span></span> <span data-ttu-id="a7eb4-460">W przeciwnym razie to pole nie jest używane w przypadku ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-460">Otherwise, this field is not used for ECDH.</span></span>
- <span data-ttu-id="a7eb4-461">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-461">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-462">**dane wejściowe** Gdy jest NX_CRYPTO_EC_CURVE_SET, to pole wskazuje metodę kryptograficzną krzywej eliptycznej.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-462">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="a7eb4-463">Gdy jest NX_CRYPTO_DH_SETUP, to pole nie jest używane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-463">When op is NX_CRYPTO_DH_SETUP, this field is not used.</span></span> <span data-ttu-id="a7eb4-464">Gdy operacja jest NX_CRYPTO_DH_CALCULATE, to pole wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-464">When op is NX_CRYPTO_DH_CALCULATE, this field points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-465">Gdy operacja jest NX_CRYPTO_DH_IMPORT_KEY_PAIR, to pole wskazuje na klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-465">When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to public key.</span></span>
- <span data-ttu-id="a7eb4-466">**input_length_in_byte** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-466">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-467">**iv_ptr** To pole nie jest używane w przypadku ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-467">**iv_ptr** This field is not used for ECDH.</span></span>
- <span data-ttu-id="a7eb4-468">**dane wyjściowe** Gdy op jest NX_CRYPTO_EC_CURVE_SET lub NX_CRYPTO_DH_IMPORT_KEY_PAIR, to pole nie jest używane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-468">**output** When op is NX_CRYPTO_EC_CURVE_SET or NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field is not used.</span></span> <span data-ttu-id="a7eb4-469">Gdy jest NX_CRYPTO_DH_SETUP, to pole wskazuje obszar pamięci dla wygenerowanego klucza publicznego ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-469">When op is NX_CRYPTO_DH_SETUP, this field points to the memory area for the generated ECDH public key.</span></span> <span data-ttu-id="a7eb4-470">Gdy jest NX_CRYPTO_DH_CALCULATE, to pole wskazuje obszar pamięci dla wygenerowanego wspólnego wpisu tajnego ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-470">When op is NX_CRYPTO_DH_CALCULATE, this field points to the memory area for the generated ECDH shared secret.</span></span>
- <span data-ttu-id="a7eb4-471">**output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-471">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="a7eb4-472">**crypto_metadata** Wskaźnik do bloku sterowania ECDH używany w *_nx_crypto_method_ecdh_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-472">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>
- <span data-ttu-id="a7eb4-473">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-473">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-474">W przypadku ECDH rozmiar metadanych musi być *sizeof (NX_CRYPTO_ECDH)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-474">For ECDH, the metadata size must *sizeof(NX_CRYPTO_ECDH)*</span></span>
- <span data-ttu-id="a7eb4-475">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-475">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-476">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-476">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-477">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-477">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-478">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-478">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-479">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-479">Return Values</span></span>

- <span data-ttu-id="a7eb4-480">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-480">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDH operation.</span></span>
- <span data-ttu-id="a7eb4-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-482">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-482">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDH algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdh_cleanup"></a><span data-ttu-id="a7eb4-485">_nx_crypto_method_ecdh_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-485">_nx_crypto_method_ecdh_cleanup</span></span>

<span data-ttu-id="a7eb4-486">Wyczyść blok sterowania ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-486">Clean up the ECDH control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-487">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-487">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-488">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-488">Description</span></span>

<span data-ttu-id="a7eb4-489">Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania ECDH po ustaleniu, że ta sesja ECDH nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-489">Application calls this function to clean up the ECDH control block after it determines this ECDH session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-490">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-490">Parameters</span></span>

- <span data-ttu-id="a7eb4-491">**crypto_metadata** Wskaźnik do bloku sterowania ECDH używany w *_nx_crypto_method_ecdh_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-491">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-492">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-492">Return Values</span></span>

- <span data-ttu-id="a7eb4-493">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję ECDH.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-493">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDH session.</span></span>
- <span data-ttu-id="a7eb4-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdsa_init"></a><span data-ttu-id="a7eb4-495">_nx_crypto_method_ecdsa_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-495">_nx_crypto_method_ecdsa_init</span></span>

<span data-ttu-id="a7eb4-496">Inicjuje blok kontroli kryptografii ECDSA</span><span class="sxs-lookup"><span data-stu-id="a7eb4-496">Initializes the ECDSA crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-497">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-497">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-498">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-498">Description</span></span>

<span data-ttu-id="a7eb4-499">Ta funkcja inicjuje blok sterowania ECDSA z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-499">This function initializes the ECDSA control block with the given key string.</span></span> <span data-ttu-id="a7eb4-500">Po zainicjowaniu bloku sterowania ECDSA kolejna operacja ECDSA będzie używać tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-500">Once the ECDSA control block is initialized, subsequent ECDSA operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-501">Aplikacja może utworzyć wiele bloków sterujących ECDSA, każda reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-501">Application may create multiple ECDSA control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-502">Inicjalizacja bloku sterowania ECDSA uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-502">Initializing the ECDSA control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-503">Ponowne inicjowanie bloku sterowania ECDSA porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-503">Re-initializing the ECDSA control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-504">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-504">Parameters</span></span>

- <span data-ttu-id="a7eb4-505">**Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-505">**method** Pointer to a valid ECDSA crypto method control block.</span></span> <span data-ttu-id="a7eb4-506">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-506">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-507">*crypto_method_ecdsa*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-507">*crypto_method_ecdsa*</span></span>
- <span data-ttu-id="a7eb4-508">**klucz** To pole nie jest używane w przypadku ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-508">**key** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="a7eb4-509">**key_size_in_bits** To pole nie jest używane w przypadku ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-509">**key_size_in_bits** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="a7eb4-510">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-510">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-511">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-511">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-512">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-512">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-513">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-513">**crypto_metadata** Pointer to a valid memory space for the ECDSA control block.</span></span> <span data-ttu-id="a7eb4-514">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-514">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-515">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-515">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-516">W przypadku ECDSA rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_ECDSA)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-516">For ECDSA, the metadata size must be *sizeof(NX_CRYPTO_ECDSA)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-517">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-517">Return Values</span></span>

- <span data-ttu-id="a7eb4-518">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania ECDSA przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-518">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDSA control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-520">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-520">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdsa_operation"></a><span data-ttu-id="a7eb4-521">_nx_crypto_method_ecdsa_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-521">_nx_crypto_method_ecdsa_operation</span></span>

<span data-ttu-id="a7eb4-522">Wykonaj operację ECDSA</span><span class="sxs-lookup"><span data-stu-id="a7eb4-522">Perform ECDSA operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-523">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-523">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-524">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-524">Description</span></span>

<span data-ttu-id="a7eb4-525">Ta funkcja wykonuje operację ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-525">This function performs ECDSA operation.</span></span> <span data-ttu-id="a7eb4-526">Blok sterowania ECDSA musi zostać zainicjowany przy użyciu _ *nx_crypto_method_ecdsa_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-526">The ECDSA control block must have been initialized with _ *nx_crypto_method_ecdsa_init()*.</span></span> <span data-ttu-id="a7eb4-527">Algorytm ECDSA ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-527">The ECDSA algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-528">Gdy operacja jest NX_CRYPTO_EC_CURVE_SET, punkty wejścia do metody kryptograficznej krzywej eliptycznej.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-528">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="a7eb4-529">Gdy operacja jest NX_CRYPTO_EC_KEY_PAIR_GENERATE, punkty wyjścia do struktury NX_CRYPTO_EXTENDED_OUTPUT i pary kluczy są kopiowane do nx_crypto_extended_output_data.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-529">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-530">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-530">Parameters</span></span>

- <span data-ttu-id="a7eb4-531">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-531">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-532">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-532">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-533">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-533">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="a7eb4-534">*NX_CRYPTO_AUTHENTICATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-534">*NX_CRYPTO_AUTHENTICATE*</span></span>
  - <span data-ttu-id="a7eb4-535">*NX_CRYPTO_VERIFY*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-535">*NX_CRYPTO_VERIFY*</span></span>
- <span data-ttu-id="a7eb4-536">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-536">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-537">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-537">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-538">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-538">**method** Pointer to the valid ECDSA crypto method.</span></span> <span data-ttu-id="a7eb4-539">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_ecdsa_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-539">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdsa_init().*</span></span>
- <span data-ttu-id="a7eb4-540">**klucz** Wskazuje klucz, gdy operacja jest NX_CRYPTO_VERIFY.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-540">**key** Points to the key when op is NX_CRYPTO_VERIFY.</span></span> <span data-ttu-id="a7eb4-541">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-541">There are not restrictions on key buffer.</span></span> <span data-ttu-id="a7eb4-542">To pole nie jest używane w przypadku innych wartości op.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-542">This field is not used for other values of op.</span></span>
- <span data-ttu-id="a7eb4-543">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-543">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-544">**dane wejściowe** Gdy jest NX_CRYPTO_EC_CURVE_SET, to pole wskazuje metodę kryptograficzną krzywej eliptycznej.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-544">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="a7eb4-545">W przeciwnym razie to pole wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-545">Otherwise, this field points to a buffer containing input text data.</span></span>
- <span data-ttu-id="a7eb4-546">**input_length_in_byte** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-546">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-547">**iv_ptr** To pole nie jest używane w przypadku ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-547">**iv_ptr** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="a7eb4-548">**dane wyjściowe** Gdy jest NX_CRYPTO_EC_CURVE_SET, to pole nie jest używane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-548">**output** When op is NX_CRYPTO_EC_CURVE_SET, this field is not used.</span></span> <span data-ttu-id="a7eb4-549">Gdy jest NX_CRYPTO_AUTHENTICATE, to pole wskazuje obszar pamięci dla wygenerowanej sygnatury ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-549">When op is NX_CRYPTO_AUTHENTICATE, this field points to the memory area for the generated ECDSA signature.</span></span> <span data-ttu-id="a7eb4-550">Gdy jest NX_CRYPTO_VERIFY, to pole wskazuje obszar pamięci dla zweryfikowanej sygnatury ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-550">When op is NX_CRYPTO_VERIFY, this field points to the memory area for the verified ECDSA signature.</span></span>
- <span data-ttu-id="a7eb4-551">**output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-551">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="a7eb4-552">**crypto_metadata** Wskaźnik do bloku sterowania ECDSA używany w *_nx_crypto_method_ecdsa_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-552">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>
- <span data-ttu-id="a7eb4-553">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-553">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-554">W przypadku ECDSA rozmiar metadanych musi być *sizeof (NX_CRYPTO_ECDSA)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-554">For ECDSA, the metadata size must *sizeof(NX_CRYPTO_ECDSA)*</span></span>
- <span data-ttu-id="a7eb4-555">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-555">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-556">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-556">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-557">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-557">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-558">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-558">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-559">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-559">Return Values</span></span>

- <span data-ttu-id="a7eb4-560">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-560">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDSA operation.</span></span>
- <span data-ttu-id="a7eb4-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-562">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-562">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDSA algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdsa_cleanup"></a><span data-ttu-id="a7eb4-565">_nx_crypto_method_ecdsa_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-565">_nx_crypto_method_ecdsa_cleanup</span></span>

<span data-ttu-id="a7eb4-566">Wyczyść blok sterowania ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-566">Clean up the ECDSA control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-567">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-567">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-568">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-568">Description</span></span>

<span data-ttu-id="a7eb4-569">Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania ECDSA po ustaleniu, że ta sesja ECDSA nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-569">Application calls this function to clean up the ECDSA control block after it determines this ECDSA session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-570">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-570">Parameters</span></span>

- <span data-ttu-id="a7eb4-571">**crypto_metadata** Wskaźnik do bloku sterowania ECDSA używany w *_nx_crypto_method_ecdsa_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-571">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-572">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-572">Return Values</span></span>

- <span data-ttu-id="a7eb4-573">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję ECDSA.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-573">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDSA session.</span></span>
- <span data-ttu-id="a7eb4-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_md5_init"></a><span data-ttu-id="a7eb4-575">_nx_crypto_method_hmac_md5_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-575">_nx_crypto_method_hmac_md5_init</span></span>

<span data-ttu-id="a7eb4-576">Inicjuje blok kontroli kryptograficznej algorytmu HMAC MD5</span><span class="sxs-lookup"><span data-stu-id="a7eb4-576">Initializes the HMAC MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-577">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-577">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-578">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-578">Description</span></span>

<span data-ttu-id="a7eb4-579">Ta funkcja inicjuje blok kontrolny MD5 algorytmu z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-579">This function initializes the HMAC MD5 control block with the given key string.</span></span> <span data-ttu-id="a7eb4-580">Po zainicjowaniu bloku sterowania algorytmem MD5 algorytmu algorytmu, kolejne operacje HMAC MD5 używają tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-580">Once the HMAC MD5 control block is initialized, subsequent HMAC MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-581">Aplikacja może utworzyć wiele bloków sterujących algorytmem MD5, każdy reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-581">Application may create multiple HMAC MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-582">Inicjalizacja bloku kontroli MD5 algorytmu HMAC uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-582">Initializing the HMAC MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-583">Ponowne inicjowanie bloku sterowania algorytmem MD5 algorytmu porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-583">Re-initializing the HMAC MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-584">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-584">Parameters</span></span>

- <span data-ttu-id="a7eb4-585">**Metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej algorytmu algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-585">**method** Pointer to a valid HMAC MD5 crypto method control block.</span></span>
<span data-ttu-id="a7eb4-586">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-586">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-587">*crypto_method_hmac_md5*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-587">*crypto_method_hmac_md5*</span></span>
- <span data-ttu-id="a7eb4-588">**klucz** Wskazuje na klucz.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-588">**key** Points to the key.</span></span> <span data-ttu-id="a7eb4-589">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-589">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="a7eb4-590">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-590">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-591">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-591">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-592">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-592">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-593">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-593">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-594">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania algorytmem MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-594">**crypto_metadata** Pointer to a valid memory space for the HMAC MD5 control block.</span></span> <span data-ttu-id="a7eb4-595">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-595">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-596">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-596">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-597">W przypadku algorytmu HMAC MD5 rozmiar metadanych musi być *: sizeof (NX_CRYPTO_MD5_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-597">For HMAC MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-598">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-598">Return Values</span></span>

- <span data-ttu-id="a7eb4-599">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania algorytmem MD5 algorytmu przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-599">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-601">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-601">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_md5_operation"></a><span data-ttu-id="a7eb4-602">_nx_crypto_method_hmac_md5_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-602">_nx_crypto_method_hmac_md5_operation</span></span>

<span data-ttu-id="a7eb4-603">Wykonaj operację mieszania algorytmu HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-603">Perform an HMAC MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-604">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-604">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-605">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-605">Description</span></span>

<span data-ttu-id="a7eb4-606">Ta funkcja wykonuje operację mieszania algorytmu HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-606">This function performs HMAC MD5 hash operation.</span></span> <span data-ttu-id="a7eb4-607">Blok kontroli MD5 algorytmu HMAC musi być zainicjowany przy użyciu _ *nx_crypto_method_hmac_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-607">The HMAC MD5 control block must have been initialized with _ *nx_crypto_method_hmac_md5_init()*.</span></span> <span data-ttu-id="a7eb4-608">Algorytm algorytmu algorytmem MD5 w oparciu o algorytm określony w bloku sterowania *metodami* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-608">The HMAC MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-609">Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-609">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="a7eb4-610">Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku kontroli algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-610">This operation does not keep state information, and does not alter the key material in the HMAC MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-611">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-611">Parameters</span></span>

- <span data-ttu-id="a7eb4-612">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-612">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-613">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-613">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-614">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-614">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="a7eb4-615">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-615">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="a7eb4-616">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-616">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="a7eb4-617">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-617">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-618">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-618">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-619">**Metoda** Wskaźnik do prawidłowych metod kryptograficznych algorytmu algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-619">**method** Pointer to the valid HMAC MD5 crypto method.</span></span> <span data-ttu-id="a7eb4-620">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_hmac_md5_init ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-620">The crypto method used here must be the same used in the *nx_crypto_method_hmac_md5_init().*</span></span>
- <span data-ttu-id="a7eb4-621">**klucz** Wskazuje na klucz.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-621">**key** Points to the key.</span></span> <span data-ttu-id="a7eb4-622">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-622">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="a7eb4-623">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-623">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-624">**input_data** Wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-624">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-625">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-625">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-626">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-626">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-627">**iv_ptr** To pole nie jest używane dla algorytmu HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-627">**iv_ptr** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="a7eb4-628">**iv_size** To pole nie jest używane dla algorytmu HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-628">**iv_size** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="a7eb4-629">**output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu algorytmu HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-629">**output_buffer** Pointer to the memory area for the generated HMAC MD5 hash.</span></span>
- <span data-ttu-id="a7eb4-630">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-630">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="a7eb4-631">**crypto_metadata** Wskaźnik do bloku sterowania algorytmem MD5 algorytmu używanego w *_nx_crypto_method_hmac_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-631">**crypto_metadata** Pointer to the HMAC MD5 control block used in *_nx_crypto_method_hmac_md5_init()*.</span></span>
- <span data-ttu-id="a7eb4-632">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-632">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-633">W przypadku algorytmu HMAC MD5 rozmiar metadanych musi być *sizeof (NX_CRYPTO_MD5_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-633">For HMAC MD5, the metadata size must *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>
- <span data-ttu-id="a7eb4-634">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-634">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-635">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-635">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-636">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-636">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-637">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-637">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-638">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-638">Return Values</span></span>

- <span data-ttu-id="a7eb4-639">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA OPERACJĘ HMAC MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-639">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC MD5 operation.</span></span>
- <span data-ttu-id="a7eb4-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-641">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-641">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) podano nieprawidłowy algorytm algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC MD5 algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_init"></a><span data-ttu-id="a7eb4-644">_nx_crypto_method_hmac_sha1_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-644">_nx_crypto_method_hmac_sha1_init</span></span>

<span data-ttu-id="a7eb4-645">Inicjuje blok kontroli kryptografii algorytmu szyfrowania HMAC</span><span class="sxs-lookup"><span data-stu-id="a7eb4-645">Initializes the HMAC SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-646">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-646">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-647">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-647">Description</span></span>

<span data-ttu-id="a7eb4-648">Ta funkcja inicjuje blok kontroli SHA1 algorytmu HMAC z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-648">This function initializes the HMAC SHA1 control block with the given key string.</span></span> <span data-ttu-id="a7eb4-649">Po zainicjowaniu bloku sterowania SHA1 algorytmem HMAC kolejna operacja algorytmu SHA1 będzie używać tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-649">Once the HMAC SHA1 control block is initialized, subsequent HMAC SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-650">Aplikacja może tworzyć wiele bloków sterowania SHA1 algorytmem HMAC, każdy reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-650">Application may create multiple HMAC SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-651">Inicjalizacja bloku kontroli SHA1 algorytmu HMAC uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-651">Initializing the HMAC SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-652">Ponowne inicjowanie bloku kontroli SHA1 algorytmu HMAC porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-652">Re-initializing the HMAC SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-653">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-653">Parameters</span></span>

- <span data-ttu-id="a7eb4-654">**Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną algorytmu SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-654">**method** Pointer to a valid HMAC SHA1 crypto method control block.</span></span> <span data-ttu-id="a7eb4-655">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-655">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-656">*crypto_method_hmac_sha1*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-656">*crypto_method_hmac_sha1*</span></span>
- <span data-ttu-id="a7eb4-657">**klucz** Wskazuje na klucz.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-657">**key** Points to the key.</span></span> <span data-ttu-id="a7eb4-658">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-658">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="a7eb4-659">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-659">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-660">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-660">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-661">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-661">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-662">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-662">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-663">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA1 algorytmu HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-663">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA1 control block.</span></span> <span data-ttu-id="a7eb4-664">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-664">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-665">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-665">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-666">Dla algorytmu SHA1 algorytmem, rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA1_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-666">For HMAC SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-667">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-667">Return Values</span></span>

- <span data-ttu-id="a7eb4-668">**NX_CRYPTO_SUCCESS** (0X00) pomyślne INICJOWANIE bloku HMAC SHA1control z kluczem i rozmiarem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-668">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-670">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-670">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_operation"></a><span data-ttu-id="a7eb4-671">_nx_crypto_method_hmac_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-671">_nx_crypto_method_hmac_sha1_operation</span></span>

<span data-ttu-id="a7eb4-672">Wykonywanie operacji skrótu SHA1 algorytmu HMAC</span><span class="sxs-lookup"><span data-stu-id="a7eb4-672">Perform HMAC SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-673">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-673">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-674">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-674">Description</span></span>

<span data-ttu-id="a7eb4-675">Ta funkcja wykonuje operację mieszania algorytmu HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-675">This function performs HMAC SHA1 hash operation.</span></span> <span data-ttu-id="a7eb4-676">Blok sterowania SHA1 algorytmem HMAC musi być zainicjowany przy użyciu _ *nx_crypto_method_hmac_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-676">The HMAC SHA1 control block must have been initialized with _ *nx_crypto_method_hmac_sha1_init()*.</span></span> <span data-ttu-id="a7eb4-677">Algorytm SHA1 algorytmu HMAC ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-677">The HMAC SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-678">Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 20 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-678">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-679">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-679">Parameters</span></span>

- <span data-ttu-id="a7eb4-680">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-680">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-681">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-681">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-682">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-682">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="a7eb4-683">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-683">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="a7eb4-684">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-684">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="a7eb4-685">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-685">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-686">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-686">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-687">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej algorytmu SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-687">**method** Pointer to the valid HMAC SHA1 crypto method.</span></span> <span data-ttu-id="a7eb4-688">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_hmac_sha1_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-688">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha1_init().*</span></span>
- <span data-ttu-id="a7eb4-689">**klucz** Wskazuje na klucz.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-689">**key** Points to the key.</span></span> <span data-ttu-id="a7eb4-690">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-690">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="a7eb4-691">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-691">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-692">**input_data** Wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-692">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-693">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-693">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-694">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-694">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-695">**iv_ptr** To pole nie jest używane dla algorytmu SHA1 algorytmem HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-695">**iv_ptr** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="a7eb4-696">**iv_size** To pole nie jest używane dla algorytmu SHA1 algorytmem HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-696">**iv_size** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="a7eb4-697">**output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA1 algorytmu HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-697">**output_buffer** Pointer to the memory area for the generated HMAC SHA1 hash.</span></span>
- <span data-ttu-id="a7eb4-698">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-698">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="a7eb4-699">**crypto_metadata** Wskaźnik do bloku sterowania SHA1 algorytmem HMAC używanym w *_nx_crypto_method_hmac_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-699">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>
- <span data-ttu-id="a7eb4-700">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-700">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-701">Dla algorytmu SHA1 algorytmem, rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA1_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-701">For HMAC SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>
- <span data-ttu-id="a7eb4-702">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-702">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-703">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-703">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-704">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-704">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-705">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-705">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-706">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-706">Return Values</span></span>

- <span data-ttu-id="a7eb4-707">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację SHA1 algorytmu HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-707">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA1 operation.</span></span>
- <span data-ttu-id="a7eb4-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-709">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-709">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA1 algorytmu HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a><span data-ttu-id="a7eb4-712">_nx_crypto_method_hmac_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-712">_nx_crypto_method_hmac_sha1_cleanup</span></span>

<span data-ttu-id="a7eb4-713">Wyczyść blok sterowania algorytmem SHA1 algorytmu HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-713">Clean up the HMAC SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-714">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-714">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-715">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-715">Description</span></span>

<span data-ttu-id="a7eb4-716">Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania SHA1 algorytmu HMAC po ustaleniu, że ta sesja SHA1 nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-716">Application calls this function to clean up the HMAC SHA1 control block after it determines this HMAC SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-717">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-717">Parameters</span></span>

- <span data-ttu-id="a7eb4-718">**crypto_metadata** Wskaźnik do bloku sterowania SHA1 algorytmem HMAC używanym w *_nx_crypto_method_hmac_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-718">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-719">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-719">Return Values</span></span>

- <span data-ttu-id="a7eb4-720">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA1 algorytmu HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-720">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA1 session.</span></span>
- <span data-ttu-id="a7eb4-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_init"></a><span data-ttu-id="a7eb4-722">_nx_crypto_method_hmac_sha256_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-722">_nx_crypto_method_hmac_sha256_init</span></span>

<span data-ttu-id="a7eb4-723">Inicjuje blok sterowania kryptografią SHA256 HMAC</span><span class="sxs-lookup"><span data-stu-id="a7eb4-723">Initializes the HMAC SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-724">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-724">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-725">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-725">Description</span></span>

<span data-ttu-id="a7eb4-726">Ta funkcja inicjuje blok sterowania SHA256 HMAC z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-726">This function initializes the HMAC SHA256 control block with the given key string.</span></span> <span data-ttu-id="a7eb4-727">Po zainicjowaniu bloku sterowania SHA256 HMAC kolejna operacja SHA256 jest używana w tym samym bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-727">Once the HMAC SHA256 control block is initialized, subsequent HMAC SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-728">Aplikacja może utworzyć wiele bloków sterujących SHA256 HMAC, każdy reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-728">Application may create multiple HMAC SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-729">Inicjalizacja bloku sterowania SH256 HMAC uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-729">Initializing the HMAC SH256 control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-730">Ponowne inicjowanie bloku sterowania SHA256 HMAC porzuca bieżącą sesję i gwiazdy nową z nowym kluczem.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-730">Re-initializing the HMAC SHA256 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-731">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-731">Parameters</span></span>

- <span data-ttu-id="a7eb4-732">**Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-732">**method** Pointer to a valid HMAC SHA256 crypto method control block.</span></span> <span data-ttu-id="a7eb4-733">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-733">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-734">*crypto_method_hmac_sha224*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-734">*crypto_method_hmac_sha224*</span></span>
  - <span data-ttu-id="a7eb4-735">*crypto_method_hmac_sha256*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-735">*crypto_method_hmac_sha256*</span></span>
- <span data-ttu-id="a7eb4-736">**klucz** Wskazuje na klucz.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-736">**key** Points to the key.</span></span> <span data-ttu-id="a7eb4-737">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-737">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="a7eb4-738">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-738">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-739">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-739">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-740">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-740">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-741">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-741">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-742">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA256 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-742">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA256 control block.</span></span> <span data-ttu-id="a7eb4-743">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-743">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-744">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-744">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-745">W przypadku SHA256 HMAC rozmiar metadanych musi mieć wartość *sizeof (NX_CRYTPO_SHA256_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-745">For HMAC SHA256, the metadata size must be *sizeof(NX_CRYTPO_SHA256_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-746">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-746">Return Values</span></span>

- <span data-ttu-id="a7eb4-747">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania SHA256 HMAC przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-747">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-749">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-749">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_operation"></a><span data-ttu-id="a7eb4-750">_nx_crypto_method_hmac_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-750">_nx_crypto_method_hmac_sha256_operation</span></span>

<span data-ttu-id="a7eb4-751">Wykonywanie operacji skrótu SHA256 HMAC</span><span class="sxs-lookup"><span data-stu-id="a7eb4-751">Perform HMAC SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-752">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-752">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-753">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-753">Description</span></span>

<span data-ttu-id="a7eb4-754">Ta funkcja wykonuje operację mieszania SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-754">This function performs HMAC SHA256 hash operation.</span></span> <span data-ttu-id="a7eb4-755">Blok sterowania SHA256 HMAC musi być zainicjowany przy użyciu _ *nx_crypto_method_hmac_sha256_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-755">The HMAC SHA256 control block must have been initialized with _ *nx_crypto_method_hmac_sha256_init()*.</span></span> <span data-ttu-id="a7eb4-756">Algorytm SHA256 HMAC ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-756">The HMAC SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-757">Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 32 bajtów dla SHA256 lub 28 bajtów dla SHA224.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-757">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-758">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-758">Parameters</span></span>

- <span data-ttu-id="a7eb4-759">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-759">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-760">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-760">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-761">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-761">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="a7eb4-762">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-762">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="a7eb4-763">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-763">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="a7eb4-764">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-764">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-765">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-765">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-766">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-766">**method** Pointer to the valid HMAC SHA256 crypto method.</span></span> <span data-ttu-id="a7eb4-767">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_hmac_sha256_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-767">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha256_init().*</span></span>
- <span data-ttu-id="a7eb4-768">**klucz** Wskazuje na klucz.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-768">**key** Points to the key.</span></span> <span data-ttu-id="a7eb4-769">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-769">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="a7eb4-770">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-770">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-771">**input_data** Wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-771">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-772">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-772">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-773">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-773">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-774">**iv_ptr** To pole nie jest używane dla HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-774">**iv_ptr** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="a7eb4-775">**iv_size** To pole nie jest używane dla HMAC SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-775">**iv_size** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="a7eb4-776">**output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA256 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-776">**output_buffer** Pointer to the memory area for the generated HMAC SHA256 hash.</span></span>
- <span data-ttu-id="a7eb4-777">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-777">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="a7eb4-778">**crypto_metadata** Wskaźnik do bloku sterowania SHA256 HMAC używanego w *_nx_crypto_method_hmac_sha256_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-778">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>
- <span data-ttu-id="a7eb4-779">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-779">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-780">W przypadku SHA256 HMAC rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA256_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-780">For HMAC SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256_HMAC)*</span></span>
- <span data-ttu-id="a7eb4-781">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-781">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-782">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-782">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-783">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-783">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-784">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-784">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-785">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-785">Return Values</span></span>

- <span data-ttu-id="a7eb4-786">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA OPERACJĘ SHA256 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-786">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA256 operation.</span></span>
- <span data-ttu-id="a7eb4-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-788">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-788">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA256 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a><span data-ttu-id="a7eb4-791">_nx_crypto_method_hmac_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-791">_nx_crypto_method_hmac_sha256_cleanup</span></span>

<span data-ttu-id="a7eb4-792">Wyczyść blok sterowania SHA256 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-792">Clean up the HMAC SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-793">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-793">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-794">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-794">Description</span></span>

<span data-ttu-id="a7eb4-795">Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania SHA256 HMAC po ustaleniu, że ta funkcja nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-795">Application calls this function to clean up the HMAC SHA256 control block after it determines this HMAC SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-796">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-796">Parameters</span></span>

- <span data-ttu-id="a7eb4-797">**crypto_metadata** Wskaźnik do bloku sterowania SHA256 HMAC używanego w *_nx_crypto_method_hmac_sha256_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-797">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-798">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-798">Return Values</span></span>

- <span data-ttu-id="a7eb4-799">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA256 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-799">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA256 session.</span></span>
- <span data-ttu-id="a7eb4-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_init"></a><span data-ttu-id="a7eb4-801">_nx_crypto_method_hmac_sha512_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-801">_nx_crypto_method_hmac_sha512_init</span></span>

<span data-ttu-id="a7eb4-802">Inicjuje blok sterowania kryptografią SHA512 HMAC</span><span class="sxs-lookup"><span data-stu-id="a7eb4-802">Initializes the HMAC SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-803">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-803">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-804">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-804">Description</span></span>

<span data-ttu-id="a7eb4-805">Ta funkcja inicjuje blok sterowania SHA512 HMAC z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-805">This function initializes the HMAC SHA512 control block with the given key string.</span></span> <span data-ttu-id="a7eb4-806">Po zainicjowaniu bloku sterowania SHA512 HMAC kolejna operacja SHA512 jest używana w tym samym bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-806">Once the HMAC SHA512 control block is initialized, subsequent HMAC SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-807">Aplikacja może utworzyć wiele bloków sterujących SHA512 HMAC, każdy reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-807">Application may create multiple HMAC SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-808">Inicjalizacja bloku sterowania SH512 HMAC uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-808">Initializing the HMAC SH512 control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-809">Ponowne inicjowanie bloku sterowania SHA512 HMAC porzuca bieżącą sesję i gwiazdy nową z nowym kluczem.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-809">Re-initializing the HMAC SHA512 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-810">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-810">Parameters</span></span>

- <span data-ttu-id="a7eb4-811">**Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-811">**method** Pointer to a valid HMAC SHA512 crypto method control block.</span></span> <span data-ttu-id="a7eb4-812">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-812">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-813">*crypto_method_hmac_sha384*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-813">*crypto_method_hmac_sha384*</span></span>
  - <span data-ttu-id="a7eb4-814">*crypto_method_hmac_sha512*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-814">*crypto_method_hmac_sha512*</span></span>
- <span data-ttu-id="a7eb4-815">**klucz** Wskazuje na klucz.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-815">**key** Points to the key.</span></span> <span data-ttu-id="a7eb4-816">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-816">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="a7eb4-817">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-817">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-818">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-818">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-819">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-819">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-820">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-820">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-821">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA512 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-821">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA512 control block.</span></span> <span data-ttu-id="a7eb4-822">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-822">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-823">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-823">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-824">W przypadku SHA512 HMAC rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA512_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-824">For HMAC SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-825">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-825">Return Values</span></span>

- <span data-ttu-id="a7eb4-826">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania SHA512 HMAC przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-826">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-828">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-828">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_operation"></a><span data-ttu-id="a7eb4-829">_nx_crypto_method_hmac_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-829">_nx_crypto_method_hmac_sha512_operation</span></span>

<span data-ttu-id="a7eb4-830">Wykonywanie operacji skrótu SHA512 HMAC</span><span class="sxs-lookup"><span data-stu-id="a7eb4-830">Perform HMAC SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-831">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-831">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-832">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-832">Description</span></span>

<span data-ttu-id="a7eb4-833">Ta funkcja wykonuje operację mieszania SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-833">This function performs HMAC SHA512 hash operation.</span></span> <span data-ttu-id="a7eb4-834">Blok sterowania SHA512 HMAC musi być zainicjowany przy użyciu _ *nx_crypto_method_hmac_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-834">The HMAC SHA512 control block must have been initialized with _ *nx_crypto_method_hmac_sha512_init()*.</span></span> <span data-ttu-id="a7eb4-835">Algorytm SHA512 HMAC ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-835">The HMAC SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-836">Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 64 bajtów dla SHA512 lub 48 bajtów dla SHA384.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-836">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-837">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-837">Parameters</span></span>

- <span data-ttu-id="a7eb4-838">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-838">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-839">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-839">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-840">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-840">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="a7eb4-841">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-841">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="a7eb4-842">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-842">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="a7eb4-843">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-843">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-844">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-844">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-845">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-845">**method** Pointer to the valid HMAC SHA512 crypto method.</span></span> <span data-ttu-id="a7eb4-846">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_hmac_sha512_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-846">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha512_init().*</span></span>
- <span data-ttu-id="a7eb4-847">**klucz** Wskazuje na klucz.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-847">**key** Points to the key.</span></span> <span data-ttu-id="a7eb4-848">Nie ma ograniczeń dotyczących buforu kluczy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-848">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="a7eb4-849">**key_size_in_bits** Rozmiar klucza w bitach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-849">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="a7eb4-850">**input_data** Wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-850">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-851">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-851">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-852">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-852">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-853">**iv_ptr** To pole nie jest używane dla HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-853">**iv_ptr** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="a7eb4-854">**iv_size** To pole nie jest używane dla HMAC SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-854">**iv_size** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="a7eb4-855">**output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA512 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-855">**output_buffer** Pointer to the memory area for the generated HMAC SHA512 hash.</span></span>
- <span data-ttu-id="a7eb4-856">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-856">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="a7eb4-857">**crypto_metadata** Wskaźnik do bloku sterowania SHA512 HMAC używanego w *_nx_crypto_method_hmac_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-857">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>
- <span data-ttu-id="a7eb4-858">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-858">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-859">W przypadku SHA512 HMAC rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA512_HMAC)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-859">For HMAC SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>
- <span data-ttu-id="a7eb4-860">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-860">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-861">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-861">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-862">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-862">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-863">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-863">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-864">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-864">Return Values</span></span>

- <span data-ttu-id="a7eb4-865">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA OPERACJĘ SHA512 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-865">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA512 operation.</span></span>
- <span data-ttu-id="a7eb4-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-867">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-867">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA512 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a><span data-ttu-id="a7eb4-870">_nx_crypto_method_hmac_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-870">_nx_crypto_method_hmac_sha512_cleanup</span></span>

<span data-ttu-id="a7eb4-871">Wyczyść blok sterowania SHA512 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-871">Clean up the HMAC SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-872">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-872">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-873">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-873">Description</span></span>

<span data-ttu-id="a7eb4-874">Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania SHA512 HMAC po ustaleniu, że ta funkcja nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-874">Application calls this function to clean up the HMAC SHA512 control block after it determines this HMAC SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-875">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-875">Parameters</span></span>

- <span data-ttu-id="a7eb4-876">**crypto_metadata** Wskaźnik do bloku sterowania SHA512 HMAC używanego w *_nx_crypto_method_hmac_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-876">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-877">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-877">Return Values</span></span>

- <span data-ttu-id="a7eb4-878">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA512 HMAC.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-878">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA512 session.</span></span>
- <span data-ttu-id="a7eb4-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

### <a name="example"></a><span data-ttu-id="a7eb4-880">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7eb4-880">Example</span></span> 

## <a name="_nx_crypto_method_md5_init"></a><span data-ttu-id="a7eb4-881">_nx_crypto_method_md5_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-881">_nx_crypto_method_md5_init</span></span>

<span data-ttu-id="a7eb4-882">Inicjuje blok kontroli kryptograficznej MD5</span><span class="sxs-lookup"><span data-stu-id="a7eb4-882">Initializes the MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-883">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-883">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-884">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-884">Description</span></span>

<span data-ttu-id="a7eb4-885">Ta funkcja inicjuje blok kontroli MD5 z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-885">This function initializes the MD5 control block with the given key string.</span></span> <span data-ttu-id="a7eb4-886">Po zainicjowaniu bloku kontroli MD5 kolejna operacja MD5 będzie używać tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-886">Once the MD5 control block is initialized, subsequent MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-887">Aplikacja może tworzyć wiele bloków kontroli MD5, każda reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-887">Application may create multiple MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-888">Inicjalizacja bloku kontroli MD5 uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-888">Initializing the MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-889">Ponowne inicjowanie bloku kontroli MD5 porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-889">Re-initializing the MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-890">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-890">Parameters</span></span>

- <span data-ttu-id="a7eb4-891">**Metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-891">**method** Pointer to a valid MD5 crypto method control block.</span></span> <span data-ttu-id="a7eb4-892">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-892">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-893">*crypto_method_md5*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-893">*crypto_method_md5*</span></span>
- <span data-ttu-id="a7eb4-894">**klucz** To pole nie jest używane w przypadku algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-894">**key** This field is not used for MD5.</span></span>
- <span data-ttu-id="a7eb4-895">**key_size_in_bits** To pole nie jest używane dla algorytmu MD5</span><span class="sxs-lookup"><span data-stu-id="a7eb4-895">**key_size_in_bits** This field is not used for MD5</span></span>
- <span data-ttu-id="a7eb4-896">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-896">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-897">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-897">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-898">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-898">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-899">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku kontroli MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-899">**crypto_metadata** Pointer to a valid memory space for the MD5 control block.</span></span> <span data-ttu-id="a7eb4-900">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-900">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-901">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-901">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-902">W przypadku algorytmu MD5 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_MD5)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-902">For MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-903">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-903">Return Values</span></span>

- <span data-ttu-id="a7eb4-904">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku kontroli MD5 przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-904">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-906">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-906">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

### <a name="example"></a><span data-ttu-id="a7eb4-907">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7eb4-907">Example</span></span>

## <a name="_nx_crypto_method_md5_operation"></a><span data-ttu-id="a7eb4-908">_nx_crypto_method_md5_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-908">_nx_crypto_method_md5_operation</span></span>

<span data-ttu-id="a7eb4-909">Wykonaj operację mieszania MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-909">Perform an MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-910">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-910">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-911">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-911">Description</span></span>

<span data-ttu-id="a7eb4-912">Ta funkcja wykonuje operację mieszania MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-912">This function performs MD5 hash operation.</span></span> <span data-ttu-id="a7eb4-913">Blok kontroli MD5 musi być zainicjowany przy użyciu _ *nx_crypto_method_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-913">The MD5 control block must have been initialized with _ *nx_crypto_method_md5_init()*.</span></span> <span data-ttu-id="a7eb4-914">Algorytm MD5 ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-914">The MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-915">Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-915">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="a7eb4-916">Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku kontroli MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-916">This operation does not keep state information and does not alter the key material in the MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-917">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-917">Parameters</span></span>

- <span data-ttu-id="a7eb4-918">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-918">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-919">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-919">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-920">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-920">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="a7eb4-921">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-921">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="a7eb4-922">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-922">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="a7eb4-923">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-923">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-924">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-924">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-925">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-925">**method** Pointer to the valid MD5 crypto method.</span></span> <span data-ttu-id="a7eb4-926">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_md5_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-926">The crypto method used here must be the same used in the _ *nx_crypto_method_md5_init().*</span></span>
- <span data-ttu-id="a7eb4-927">**input_data** Wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-927">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-928">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-928">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-929">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-929">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-930">**iv_ptr** To pole nie jest używane w przypadku algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-930">**iv_ptr** This field is not used for MD5.</span></span>
- <span data-ttu-id="a7eb4-931">**iv_size** To pole nie jest używane w przypadku algorytmu MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-931">**iv_size** This field is not used for MD5.</span></span>
- <span data-ttu-id="a7eb4-932">**output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-932">**output_buffer** Pointer to the memory area for the generated MD5 hash.</span></span>
- <span data-ttu-id="a7eb4-933">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-933">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="a7eb4-934">W przypadku algorytmu MD5 rozmiar buforu musi wynosić 16 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-934">For MD5 the buffer size must be 16 bytes.</span></span>
- <span data-ttu-id="a7eb4-935">**crypto_metadata** Wskaźnik do bloku kontroli MD5 używanego w *_nx_crypto_method_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-935">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>
- <span data-ttu-id="a7eb4-936">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-936">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-937">W przypadku algorytmu MD5 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_MD5)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-937">For MD5, the metadata size must *sizeof(NX_CRYPTO_MD5)*</span></span>
- <span data-ttu-id="a7eb4-938">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-938">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-939">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-939">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-940">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-940">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-941">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-941">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-942">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-942">Return Values</span></span>

- <span data-ttu-id="a7eb4-943">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-943">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the MD5 operation.</span></span>
- <span data-ttu-id="a7eb4-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-945">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-945">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid MD5 algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_md5_cleanup"></a><span data-ttu-id="a7eb4-948">_nx_crypto_method_md5_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-948">_nx_crypto_method_md5_cleanup</span></span>

<span data-ttu-id="a7eb4-949">Wyczyść blok kontroli MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-949">Clean up the MD5 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-950">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-950">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-951">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-951">Description</span></span>

<span data-ttu-id="a7eb4-952">Aplikacja wywołuje tę funkcję, aby oczyścić blok kontroli MD5 po ustaleniu, że ta sesja MD5 nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-952">Application calls this function to clean up the MD5 control block after it determines this MD5 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-953">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-953">Parameters</span></span>

- <span data-ttu-id="a7eb4-954">**crypto_metadata** Wskaźnik do bloku kontroli MD5 używanego w *_nx_crypto_method_md5_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-954">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-955">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-955">Return Values</span></span>

- <span data-ttu-id="a7eb4-956">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję MD5.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-956">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the MD5 session.</span></span>
- <span data-ttu-id="a7eb4-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha1_init"></a><span data-ttu-id="a7eb4-958">_nx_crypto_method_sha1_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-958">_nx_crypto_method_sha1_init</span></span>

<span data-ttu-id="a7eb4-959">Inicjuje blok kontroli kryptografii SHA1</span><span class="sxs-lookup"><span data-stu-id="a7eb4-959">Initializes the SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-960">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-960">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-961">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-961">Description</span></span>

<span data-ttu-id="a7eb4-962">Ta funkcja inicjuje blok sterowania SHA1 z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-962">This function initializes the SHA1 control block with the given key string.</span></span> <span data-ttu-id="a7eb4-963">Po zainicjowaniu bloku sterowania SHA1 kolejna operacja SHA1 będzie używać tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-963">Once the SHA1 control block is initialized, subsequent SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-964">Aplikacja może tworzyć wiele bloków sterowania SHA1, każdy reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-964">Application may create multiple SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-965">Inicjalizacja bloku sterowania SHA1 uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-965">Initializing the SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-966">Ponowne inicjowanie bloku sterowania SHA1 porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-966">Re-initializing the SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-967">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-967">Parameters</span></span>

- <span data-ttu-id="a7eb4-968">**Metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-968">**method** Pointer to a valid SHA1 crypto method control block.</span></span> <span data-ttu-id="a7eb4-969">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-969">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-970">*crypto_method_sha1*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-970">*crypto_method_sha1*</span></span>
- <span data-ttu-id="a7eb4-971">**klucz** To pole nie jest używane na potrzeby algorytmu SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-971">**key** This field is not used for SHA1.</span></span>
- <span data-ttu-id="a7eb4-972">**key_size_in_bits** To pole nie jest używane na potrzeby algorytmu SHA1</span><span class="sxs-lookup"><span data-stu-id="a7eb4-972">**key_size_in_bits** This field is not used for SHA1</span></span>
- <span data-ttu-id="a7eb4-973">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-973">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-974">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-974">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-975">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-975">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-976">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-976">**crypto_metadata** Pointer to a valid memory space for the SHA1 control block.</span></span> <span data-ttu-id="a7eb4-977">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-977">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-978">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-978">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-979">W przypadku algorytmu SHA1 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA1)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-979">For SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-980">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-980">Return Values</span></span>

- <span data-ttu-id="a7eb4-981">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku SHA1control z rozmiarem klucza i klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-981">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-983">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-983">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha1_operation"></a><span data-ttu-id="a7eb4-984">_nx_crypto_method_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-984">_nx_crypto_method_sha1_operation</span></span>

<span data-ttu-id="a7eb4-985">Wykonywanie operacji skrótu SHA1</span><span class="sxs-lookup"><span data-stu-id="a7eb4-985">Perform SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-986">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-986">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-987">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-987">Description</span></span>

<span data-ttu-id="a7eb4-988">Ta funkcja wykonuje operację mieszania SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-988">This function performs SHA1 hash operation.</span></span> <span data-ttu-id="a7eb4-989">Blok sterowania SHA1 musi być zainicjowany przy użyciu _ *nx_crypto_method_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-989">The SHA1 control block must have been initialized with _ *nx_crypto_method_sha1_init()*.</span></span> <span data-ttu-id="a7eb4-990">Algorytm SHA1 ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-990">The SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-991">Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 20 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-991">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-992">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-992">Parameters</span></span>

- <span data-ttu-id="a7eb4-993">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-993">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-994">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-994">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-995">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-995">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="a7eb4-996">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-996">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="a7eb4-997">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-997">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="a7eb4-998">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-998">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-999">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-999">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-1000">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1000">**method** Pointer to the valid SHA1 crypto method.</span></span> <span data-ttu-id="a7eb4-1001">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_sha1_init ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1001">The crypto method used here must be the same used in the *nx_crypto_method_sha1_init().*</span></span>
- <span data-ttu-id="a7eb4-1002">**input_data** Wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1002">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-1003">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1003">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-1004">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1004">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-1005">**iv_ptr** To pole nie jest używane na potrzeby algorytmu SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1005">**iv_ptr** This field is not used for SHA1.</span></span>
- <span data-ttu-id="a7eb4-1006">**iv_size** To pole nie jest używane na potrzeby algorytmu SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1006">**iv_size** This field is not used for SHA1.</span></span>
- <span data-ttu-id="a7eb4-1007">**output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1007">**output_buffer** Pointer to the memory area for the generated SHA1 hash.</span></span>
- <span data-ttu-id="a7eb4-1008">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1008">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="a7eb4-1009">W przypadku algorytmu SHA1 rozmiar buforu musi wynosić 20 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1009">For SHA1 the buffer size must be 20 bytes.</span></span>
- <span data-ttu-id="a7eb4-1010">**crypto_metadata** Wskaźnik do bloku sterowania algorytmem SHA1 używanym w *_nx_crypto_method_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1010">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>
- <span data-ttu-id="a7eb4-1011">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1011">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-1012">W przypadku algorytmu SHA1 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA1)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1012">For SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1)*</span></span>
- <span data-ttu-id="a7eb4-1013">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1013">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-1014">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1014">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-1015">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1015">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-1016">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1016">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-1017">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1017">Return Values</span></span>

- <span data-ttu-id="a7eb4-1018">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1018">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA1 operation.</span></span>
- <span data-ttu-id="a7eb4-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-1020">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1020">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

### <a name="example"></a><span data-ttu-id="a7eb4-1023">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1023">Example</span></span>

## <a name="_nx_crypto_method_sha1_cleanup"></a><span data-ttu-id="a7eb4-1024">_nx_crypto_method_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1024">_nx_crypto_method_sha1_cleanup</span></span>

<span data-ttu-id="a7eb4-1025">Wyczyść blok sterowania SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1025">Clean up the SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-1026">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1026">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-1027">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1027">Description</span></span>

<span data-ttu-id="a7eb4-1028">Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania SHA1 po ustaleniu, że ta sesja SHA1 nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1028">Application calls this function to clean up the SHA1 control block after it determines this SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-1029">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1029">Parameters</span></span>

- <span data-ttu-id="a7eb4-1030">**crypto_metadata** Wskaźnik do bloku sterowania algorytmem SHA1 używanym w *_nx_crypto_method_sha1_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1030">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-1031">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1031">Return Values</span></span>

- <span data-ttu-id="a7eb4-1032">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1032">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA1 session.</span></span>
- <span data-ttu-id="a7eb4-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha256_init"></a><span data-ttu-id="a7eb4-1034">_nx_crypto_method_sha256_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1034">_nx_crypto_method_sha256_init</span></span>

<span data-ttu-id="a7eb4-1035">Inicjuje blok kontroli kryptografii SHA256</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1035">Initializes the SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-1036">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1036">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a><span data-ttu-id="a7eb4-1037">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1037">Description</span></span>

<span data-ttu-id="a7eb4-1038">Ta funkcja inicjuje blok sterowania SHA256 z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1038">This function initializes the SHA256 control block with the given key string.</span></span> <span data-ttu-id="a7eb4-1039">Po zainicjowaniu bloku sterowania SHA256 kolejna operacja SHA256 będzie używać tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1039">Once the SHA256 control block is initialized, subsequent SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-1040">Aplikacja może utworzyć wiele bloków sterujących SHA256, każda reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1040">Application may create multiple SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-1041">Inicjalizacja bloku sterowania SHA256 uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1041">Initializing the SHA256 control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-1042">Ponowne inicjowanie bloku sterowania SHA256 porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1042">Re-initializing the SHA256 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-1043">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1043">Parameters</span></span>

- <span data-ttu-id="a7eb4-1044">**Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1044">**method** Pointer to a valid SHA256 crypto method control block.</span></span> <span data-ttu-id="a7eb4-1045">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1045">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-1046">*crypto_method_sha256*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1046">*crypto_method_sha256*</span></span>
  - <span data-ttu-id="a7eb4-1047">*crypto_method_sha224*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1047">*crypto_method_sha224*</span></span>
- <span data-ttu-id="a7eb4-1048">**klucz** To pole nie jest używane w przypadku SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1048">**key** This field is not used for SHA256.</span></span>
- <span data-ttu-id="a7eb4-1049">**key_size_in_bits** To pole nie jest używane w przypadku SHA256</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1049">**key_size_in_bits** This field is not used for SHA256</span></span>
- <span data-ttu-id="a7eb4-1050">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1050">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-1051">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1051">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-1052">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1052">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-1053">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1053">**crypto_metadata** Pointer to a valid memory space for the SHA256 control block.</span></span> <span data-ttu-id="a7eb4-1054">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1054">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-1055">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1055">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-1056">W przypadku SHA256 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA256)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1056">For SHA256, the metadata size must be *sizeof(NX_CRYPTO_SHA256)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-1057">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1057">Return Values</span></span>

- <span data-ttu-id="a7eb4-1058">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania SHA256 przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1058">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-1060">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1060">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha256_operation"></a><span data-ttu-id="a7eb4-1061">_nx_crypto_method_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1061">_nx_crypto_method_sha256_operation</span></span>

<span data-ttu-id="a7eb4-1062">Wykonywanie operacji skrótu SHA256</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1062">Perform SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-1063">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1063">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-1064">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1064">Description</span></span>

<span data-ttu-id="a7eb4-1065">Ta funkcja wykonuje operację mieszania SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1065">This function performs SHA256 hash operation.</span></span> <span data-ttu-id="a7eb4-1066">Blok sterowania SHA256 musi zostać zainicjowany przy użyciu _ ***nx_crypto_method_sha256_init ()***.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1066">The SHA256 control block must have been initialized with _ ***nx_crypto_method_sha256_init()***.</span></span> <span data-ttu-id="a7eb4-1067">Algorytm SHA256 ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1067">The SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-1068">Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 32 bajtów dla SHA256 lub 28 bajtów dla SHA224.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1068">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-1069">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1069">Parameters</span></span>

- <span data-ttu-id="a7eb4-1070">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1070">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-1071">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1071">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-1072">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1072">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="a7eb4-1073">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1073">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="a7eb4-1074">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1074">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="a7eb4-1075">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1075">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-1076">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1076">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-1077">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1077">**method** Pointer to the valid SHA256 crypto method.</span></span> <span data-ttu-id="a7eb4-1078">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_sha256_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1078">The crypto method used here must be the same used in the _ *nx_crypto_method_sha256_init().*</span></span>
- <span data-ttu-id="a7eb4-1079">**input_data** Wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1079">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-1080">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1080">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-1081">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1081">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-1082">**iv_ptr** To pole nie jest używane w przypadku SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1082">**iv_ptr** This field is not used for SHA256.</span></span>
- <span data-ttu-id="a7eb4-1083">**iv_size** To pole nie jest używane w przypadku SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1083">**iv_size** This field is not used for SHA256.</span></span>
- <span data-ttu-id="a7eb4-1084">**output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1084">**output_buffer** Pointer to the memory area for the generated SHA256 hash.</span></span>
- <span data-ttu-id="a7eb4-1085">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1085">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="a7eb4-1086">W przypadku SHA256 rozmiar buforu musi wynosić 32 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1086">For SHA256 the buffer size must be 32 bytes.</span></span> <span data-ttu-id="a7eb4-1087">W przypadku SHA224 rozmiar buforu musi wynosić 28 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1087">For SHA224 the buffer size must be 28 bytes.</span></span>
- <span data-ttu-id="a7eb4-1088">**crypto_metadata** Wskaźnik do bloku sterowania algorytmu SHA2 używany w *_nx_crypto_method_sha2_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1088">**crypto_metadata** Pointer to the SHA2 control block used in *_nx_crypto_method_sha2_init()*.</span></span>
- <span data-ttu-id="a7eb4-1089">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1089">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-1090">W przypadku SHA256 rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA256)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1090">For SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256)*</span></span>
- <span data-ttu-id="a7eb4-1091">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1091">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-1092">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1092">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-1093">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1093">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-1094">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1094">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-1095">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1095">Return Values</span></span>

- <span data-ttu-id="a7eb4-1096">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1096">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA256 operation.</span></span>
- <span data-ttu-id="a7eb4-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-1098">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1098">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha256_cleanup"></a><span data-ttu-id="a7eb4-1101">_nx_crypto_method_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1101">_nx_crypto_method_sha256_cleanup</span></span>

<span data-ttu-id="a7eb4-1102">Wyczyść blok sterowania SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1102">Clean up the SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-1103">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1103">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-1104">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1104">Description</span></span>

<span data-ttu-id="a7eb4-1105">Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania SHA256 po ustaleniu, że ta sesja SHA256 nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1105">Application calls this function to clean up the SHA256 control block after it determines this SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-1106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1106">Parameters</span></span>

- <span data-ttu-id="a7eb4-1107">**crypto_metadata** Wskaźnik do bloku sterowania SHA256 używany w *_nx_crypto_method_sha256_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1107">**crypto_metadata** Pointer to the SHA256 control block used in *_nx_crypto_method_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-1108">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1108">Return Values</span></span>

- <span data-ttu-id="a7eb4-1109">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA256.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1109">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA256 session.</span></span>
- <span data-ttu-id="a7eb4-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha512_init"></a><span data-ttu-id="a7eb4-1111">_nx_crypto_method_sha512_init</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1111">_nx_crypto_method_sha512_init</span></span>

<span data-ttu-id="a7eb4-1112">Inicjuje blok kontroli kryptografii SHA512</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1112">Initializes the SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-1113">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1113">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="a7eb4-1114">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1114">Description</span></span>

<span data-ttu-id="a7eb4-1115">Ta funkcja inicjuje blok sterowania SHA512 z danym ciągiem klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1115">This function initializes the SHA512 control block with the given key string.</span></span> <span data-ttu-id="a7eb4-1116">Po zainicjowaniu bloku sterowania SHA512 kolejna operacja SHA512 będzie używać tego samego bloku sterowania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1116">Once the SHA512 control block is initialized, subsequent SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="a7eb4-1117">Aplikacja może utworzyć wiele bloków sterujących SHA512, każda reprezentuje sesję.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1117">Application may create multiple SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="a7eb4-1118">Inicjalizacja bloku sterowania SHA512 uruchamia nową sesję obliczeń skrótu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1118">Initializing the SHA512 control block starts a new hash computation session.</span></span> <span data-ttu-id="a7eb4-1119">Ponowne inicjowanie bloku sterowania SHA512 porzuca bieżącą sesję i gwiazdy nowe.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1119">Re-initializing the SHA512 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-1120">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1120">Parameters</span></span>

- <span data-ttu-id="a7eb4-1121">**Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1121">**method** Pointer to a valid SHA512 crypto method control block.</span></span> <span data-ttu-id="a7eb4-1122">Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1122">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="a7eb4-1123">*crypto_method_sha512*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1123">*crypto_method_sha512*</span></span>
  - <span data-ttu-id="a7eb4-1124">*crypto_method_sha384*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1124">*crypto_method_sha384*</span></span>
- <span data-ttu-id="a7eb4-1125">**klucz** To pole nie jest używane w przypadku SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1125">**key** This field is not used for SHA512.</span></span>
- <span data-ttu-id="a7eb4-1126">**key_size_in_bits** To pole nie jest używane w przypadku SHA512</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1126">**key_size_in_bits** This field is not used for SHA512</span></span>
- <span data-ttu-id="a7eb4-1127">**Obsługa** Ta usługa zwraca dojście do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1127">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="a7eb4-1128">Dojście jest zależne od implementacji i nie jest używane w tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1128">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="a7eb4-1129">Aplikacja przekaże wartość NULL dla dojścia.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1129">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="a7eb4-1130">**crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1130">**crypto_metadata** Pointer to a valid memory space for the SHA512 control block.</span></span> <span data-ttu-id="a7eb4-1131">Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1131">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="a7eb4-1132">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1132">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-1133">W przypadku SHA512 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA512)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1133">For SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512)*</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-1134">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1134">Return Values</span></span>

- <span data-ttu-id="a7eb4-1135">**NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania SHA512 przy użyciu klucza i rozmiaru klucza.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1135">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="a7eb4-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-1137">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1137">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha512_operation"></a><span data-ttu-id="a7eb4-1138">_nx_crypto_method_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1138">_nx_crypto_method_sha512_operation</span></span>

<span data-ttu-id="a7eb4-1139">Wykonywanie operacji skrótu SHA512</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1139">Perform SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-1140">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1140">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="a7eb4-1141">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1141">Description</span></span>

<span data-ttu-id="a7eb4-1142">Ta funkcja wykonuje operację mieszania SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1142">This function performs SHA512 hash operation.</span></span> <span data-ttu-id="a7eb4-1143">Blok sterowania SHA512 musi zostać zainicjowany przy użyciu _ *nx_crypto_method_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1143">The SHA512 control block must have been initialized with _ *nx_crypto_method_sha512_init()*.</span></span> <span data-ttu-id="a7eb4-1144">Algorytm SHA512 ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1144">The SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="a7eb4-1145">Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 64 bajtów dla SHA512 lub 48 bajtów dla SHA384.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1145">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-1146">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1146">Parameters</span></span>

- <span data-ttu-id="a7eb4-1147">**operacja** Typ operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1147">**op** Type of operation to perform.</span></span> <span data-ttu-id="a7eb4-1148">Prawidłowa operacja:</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1148">Valid operation is:</span></span>
  - <span data-ttu-id="a7eb4-1149">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1149">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="a7eb4-1150">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1150">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="a7eb4-1151">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1151">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="a7eb4-1152">**Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1152">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-1153">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1153">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-1154">**Metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1154">**method** Pointer to the valid SHA512 crypto method.</span></span> <span data-ttu-id="a7eb4-1155">Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_sha512_init _ ().*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1155">The crypto method used here must be the same used in the _ *nx_crypto_method_sha512_init().*</span></span>
- <span data-ttu-id="a7eb4-1156">**input_data** Wskazuje bufor zawierający dane wejściowe tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1156">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="a7eb4-1157">Bufor wejściowy nie zawiera żadnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1157">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="a7eb4-1158">**input_data_size** Rozmiar danych wejściowych w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1158">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="a7eb4-1159">**iv_ptr** To pole nie jest używane w przypadku SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1159">**iv_ptr** This field is not used for SHA512.</span></span>
- <span data-ttu-id="a7eb4-1160">**iv_size** To pole nie jest używane w przypadku SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1160">**iv_size** This field is not used for SHA512.</span></span>
- <span data-ttu-id="a7eb4-1161">**output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1161">**output_buffer** Pointer to the memory area for the generated SHA512 hash.</span></span>
- <span data-ttu-id="a7eb4-1162">**output_buffer_size** Rozmiar buforu wyjściowego w bajtach.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1162">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="a7eb4-1163">W przypadku SHA512 rozmiar buforu musi wynosić 64 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1163">For SHA512 the buffer size must be 64 bytes.</span></span> <span data-ttu-id="a7eb4-1164">W przypadku SHA384 rozmiar buforu musi wynosić 48 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1164">For SHA384 the buffer size must be 48 bytes.</span></span>
- <span data-ttu-id="a7eb4-1165">**crypto_metadata** Wskaźnik do bloku sterowania SHA512 używany w *_nx_crypto_method_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1165">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>
- <span data-ttu-id="a7eb4-1166">**crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1166">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="a7eb4-1167">W przypadku SHA512 rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA512)*</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1167">For SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512)*</span></span>
- <span data-ttu-id="a7eb4-1168">**packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1168">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-1169">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1169">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="a7eb4-1170">**nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1170">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="a7eb4-1171">Wszystkie przesyłane wartości są dyskretnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1171">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-1172">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1172">Return Values</span></span>

- <span data-ttu-id="a7eb4-1173">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1173">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA512 operation.</span></span>
- <span data-ttu-id="a7eb4-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="a7eb4-1175">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1175">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="a7eb4-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="a7eb4-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha512_cleanup"></a><span data-ttu-id="a7eb4-1178">_nx_crypto_method_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1178">_nx_crypto_method_sha512_cleanup</span></span>

<span data-ttu-id="a7eb4-1179">Wyczyść blok sterowania SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1179">Clean up the SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="a7eb4-1180">Prototype</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1180">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="a7eb4-1181">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1181">Description</span></span>

<span data-ttu-id="a7eb4-1182">Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania SHA512 po ustaleniu, że ta sesja SHA512 nie jest już wymagana.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1182">Application calls this function to clean up the SHA512 control block after it determines this SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="a7eb4-1183">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1183">Parameters</span></span>

- <span data-ttu-id="a7eb4-1184">**crypto_metadata** Wskaźnik do bloku sterowania SHA512 używany w *_nx_crypto_method_sha512_init ()*.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1184">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="a7eb4-1185">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1185">Return Values</span></span>

- <span data-ttu-id="a7eb4-1186">**NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA512.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1186">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA512 session.</span></span>
- <span data-ttu-id="a7eb4-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.</span><span class="sxs-lookup"><span data-stu-id="a7eb4-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>