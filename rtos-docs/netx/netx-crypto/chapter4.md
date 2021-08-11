---
title: Rozdział 4 — Azure RTOS interfejsu API kryptograficznego netx
description: Azure RTOS interfejsu API kryptograficznego netx
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5bd4cdae28a293ec9ef259bbd29fdb8f8d6dc43f964cbc184290b82ee8f590a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788807"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>Rozdział 4 — Azure RTOS interfejsu API kryptograficznego netx

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

Inicjuje bezpieczną bibliotekę NetX

### <a name="prototype"></a>Prototype

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje moduł Azure RTOS Biblioteki kryptograficzne NetX. Przed użyciem jakichkolwiek innych funkcji kryptograficznych aplikacja musi wywołać tę funkcję w celu przeprowadzenia inicjowania i zweryfikowania integralności biblioteki. Niepowodzenie wywołania tej funkcji przed użyciem innych usług kryptograficznych NetX spowoduje zwrócenie błędów.

### <a name="parameters"></a>Parametry

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie zainicjowana biblioteka kryptograficzna NetX. Funkcje biblioteki są teraz gotowe i można ich używać.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Nie można zainicjować biblioteki kryptograficznej lub nie można sprawdzić integralności. Aplikacja nie może używać tej biblioteki.

### <a name="example"></a>Przykład

Todo

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

Pobieranie bieżącego stanu modułu z włączoną obsługą zasad FIPS

### <a name="prototype"></a>Prototype

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>Opis

Ta usługa jest dostępna tylko w bibliotece kompilacji FIPS. Zwraca stan bieżącego stanu biblioteki kryptograficznych NetX.

### <a name="parameters"></a>Parametry

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **Flaga stanu:**
  - NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001
  - NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002
  - NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004
  - NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008
  - NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000
- **Wszystkie inne wartości są nieprawidłowe.**

### <a name="example"></a>Przykład

Todo

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

Inicjuje blok kontroli kryptografii AES

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania AES z danym ciągiem klucza. Po zainicjowania bloku sterowania AES kolejna operacja AES będzie używać tego samego klucza i tego samego rozmiaru klucza.

Aplikacja może utworzyć wiele bloków sterujących AES, z których każdy reprezentuje sesję. Klucz jest przypisywany do bloku sterującego. Kolejna operacja szyfrowania lub odszyfrowywania może odwoływać się do tego samego bloku sterowania AES bez konieczności ponownego inicjowania bloku sterowania AES. Jeśli klucz sesji zostanie zmieniony, aplikacja musi ponownie zainicjować blok kontroli AES przy użyciu zaktualizowanego klucza.

Wywołanie funkcji *_ nx_crypto_method_aes_init()* automatycznie aktualizuje wcześniej skonfigurowany klucz i rozmiar klucza do nowego klucza.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych AES. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne AES:
  - *crypto_method_aes_cbc_128*
  - *crypto_method_aes_cbc_192*
  - *crypto_method_aes_cbc_256*
  - *crypto_method_aes_ctr_128*
  - *crypto_method_aes_ctr_192*
  - *crypto_method_aes_ctr_256*
  - *crypto_method_aes_xcbc_128*
  - *crypto_method_aes_ccm_8_128*
- **klucz** Wskazuje bufor zawierający klucz AES
- **key_size_in_bits** Rozmiar klucza w bitach. Prawidłowe wartości:
  - *NX_CRYPTO_AES_KEY_SIZE_128_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_192_BITS*
  - *NX_CRYPTO_AES_KEY_SIZE_256_BITS*
  - **Wszystkie inne wartości są nieprawidłowe.**
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście zależy od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania AES. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku AES rozmiar metadanych musi być *sizeof(NX_AES)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania AES z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie jest wyrównany o 4 bajty.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Rozmiar klucza nie jest prawidłowy dla AES.

## <a name="_nx_crypto_method_aes_operation"></a>_nx_crypto_method_aes_operation

Wykonaj operację AES (szyfrowanie lub odszyfrowywanie).

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację szyfrowania lub odszyfrowywania AES. Blok sterowania AES musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_aes_init()*. Algorytm AES do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody.

Rozmiar buforu wejściowego musi być wielokrotnością 16 bajtów. Rozmiar odszyfrowanych danych jest taki sam jak rozmiar danych wejściowych. Jeśli zaszyfrowane dane zostały dopełnione w celu osiągnięcia równomiernej wielokrotności rozmiaru bloku AES, wypełnienie zostanie uwzględnione w buforze wyjściowym i musi być obsługiwane przez aplikację.

Ta operacja nie powoduje przechowania informacji o stanie i nie zmienia materiału klucza w bloku sterowania AES.

Gdy opa jest NX_CRYPTO_SET_ADDITIONAL_DATA a algoritm to AES-CCM8, dane wejściowe wskazuje dodatkowe dane, a input_length_in_byte to długość dodatkowych danych.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowe działanie to:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE (tylko AES-XCBC)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA (tylko AES-CCM8)*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej AES. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *nx_crypto_method_aes_init().*
- **input_data** Wskazuje bufor zawierający zaszyfrowane dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach. Rozmiar danych wejściowych musi być wielokrotnością 16 bajtów.
- **iv_ptr** Wskaźnik do wektora początkowego. Nie ma żadnych ograniczeń dotyczących buforu IV.
- **iv_size** Rozmiar bloku Wektor początkowy w bajtach To pole musi mieć wartość 16.
- **output_buffer** Wskaźnik do obszaru pamięci dla funkcji AES do przechowywania danych w for sposób jednoznacznie tekstowy. Aplikacja musi przydzielić miejsce dla buforu wyjściowego. Bufor wyjściowy może pokrywać się z buforem wejściowym. Bufor wyjściowy może pokrywać się z buforem wejściowym, jeśli mają ten sam adres początkowy.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. Rozmiar buforu wyjściowego musi być co najmniej taki sam jak rozmiar bufora wejściowego, a rozmiar buforu wyjściowego musi być wielokrotnością 16 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania AES używanego w funkcji *_nx_crypto_method_aes_init() \* . \**
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku usługi AES rozmiar metadanych musi *być sizeof(NX_AES)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** — to pole nie jest używane w programowej implementacji biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację AES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm AES**.

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

Wyczyść blok sterowania AES.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania AES po ustaleniu, że ta sesja AES nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania AES używanego w funkcji *_nx_crypto_method_aes_init() \* . \**

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja AES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

Zaimicjuj blok sterowania 3DES.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania Triple DES (3DES) przy użyciu podanych trzech ciągów kluczy. Ciągi kluczy muszą mieć 8 bajtów każdy. Trzy klucze DES muszą być zwięzłe w pamięci ciągłej buforu 24-bajtowego. W przypadku kompilacji zgodnej ze standardem FIPS trzy klucze muszą różnić się od każdego lub funkcja zwróci NX_CRYPTO_INVALID_KEY błąd. Po zainicjowania bloku sterowania 3DES kolejne operacje 3DES będą używać tych samych kluczy.

Aplikacja może utworzyć wiele bloków sterowania 3DES, z których każdy reprezentuje sesję. Klucz jest przypisywany do bloku sterowania, a kolejne operacje szyfrowania lub odszyfrowywania mogą odwoływać się do tego samego bloku sterowania bez konieczności ponownego inicjowania. Jeśli klucz sesji zostanie zmieniony, aplikacja będzie musiał ponownie zainicjować blok sterowania przy użyciu zaktualizowanego klucza.

Wywołanie funkcji *_ nx_crypto_method_3des_init()* automatycznie aktualizuje wcześniej skonfigurowany klucz do nowych kluczy.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej 3DES. Dostępna jest następująca wstępnie zdefiniowana metoda kryptograficzna 3DES: ***crypto_method_3des***
- **klucz** Wskazuje bufor zawierający trzy (3) klucz DES
- **key_size_in_bits** Musi mieć 192 (3 klucze, każdy 64 bity).
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście identyfikuje blok sterowania 3DES, który jest inicjowany. Kolejne operacje 3DES (szyfrowanie, odszyfrowywanie i oczyszczanie) używają tego dojścia do uzyskiwania dostępu do bloku sterowania 3DES
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania 3DES. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku usługi 3DES rozmiar metadanych musi być *sizeof(NX_3DES)*

### <a name="return-value"></a>Wartość zwracana

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania 3DES z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie jest wyrównany o 4 bajty.
- **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Rozmiar klucza nie jest prawidłowy dla 3DES.

## <a name="_nx_crypto_method_3des_operation"></a>_nx_crypto_method_3des_operation

Szyfruj lub odszyfruj przy użyciu 3DES.

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację szyfrowania lub odszyfrowywania 3DES. Blok sterowania usługi 3DES musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_3des_init()*. Algorytm 3DES do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody.

Rozmiar buforu wejściowego musi być wielokrotnością 8 bajtów. Rozmiar odszyfrowanych danych jest taki sam jak rozmiar danych wejściowych. Jeśli zaszyfrowane dane zostały wypełnione w celu osiągnięcia równomiernej wielokrotności rozmiaru bloku 3DES, wypełnienie zostanie uwzględnione w buforze wyjściowym i musi być obsługiwane przez aplikację.

Ta operacja nie powoduje przechowania informacji o stanie i nie zmienia materiału klucza w bloku sterowania 3DES.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowe operacje to:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **dojście** Dojście zainicjowane przez *_nx_crypto_method_3des_init()*.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej 3DES. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *nx_crypto_method_3des_init().*
- **input_data** Wskazuje bufor zawierający zaszyfrowane dane tekstowe.
Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach. Rozmiar danych wejściowych musi być wielokrotnością 8 bajtów.
- **iv_ptr** Wskaźnik do wektora początkowego. Nie ma żadnych ograniczeń dotyczących buforu IV.
- **iv_size** Rozmiar bloku wektora początkowego w bajtach To pole musi mieć wartość 8.
- **output_buffer** Wskaźnik do obszaru pamięci dla 3DES do przechowywania danych w for sposób jednoznacznie tekstowy. Aplikacja musi przydzielić miejsce dla buforu wyjściowego. Bufor wyjściowy może pokrywać się z buforem wejściowym. Bufor wyjściowy może pokrywać się z buforem wejściowym, jeśli mają ten sam adres początkowy.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. Rozmiar buforu wyjściowego musi być co najmniej taki sam, jak rozmiar bufora wejściowego, a rozmiar buforu wyjściowego musi być wielokrotnością 8 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania 3DES używanego w *_nx_crypto_method_3des_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku usługi 3DES rozmiar metadanych musi być *sizeof(NX_3DES)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="description"></a>Opis

Ta funkcja wykonuje szyfrowanie 3DES. Blok sterowania usługi 3DES musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_moethod_3des_init()*. Ta operacja nie powoduje przechowania informacji o stanie i nie zmienia materiału klucza w bloku sterowania 3DES. Pamiętaj, że dopełnienie nie jest dodawane przez tę funkcję, więc obiekt wywołujący musi obsłużyć dopełnienie przed wywołaniem operacji szyfrowania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania 3DES z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

Wyczyść blok sterowania 3DES.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania 3DES po ustaleniu, że ta sesja 3DES nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **dojście** Dojście zainicjowane przez *_nx_crypto_method_3des_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja 3DES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

## <a name="_nx_crypto_method_drbg_init"></a>_nx_crypto_method_drbg_init

Inicjuje blok kontroli kryptografii DRBG

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania DRBG z danym ciągiem klucza. Po zainicjowania bloku sterowania DRBG kolejna operacja DRBG musi używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterowania DRBG, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania DRBG uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania DRBG porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych DRBG. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_drbg*
- **klucz** To pole nie jest używane dla drbg.
- **key_size_in_bits** To pole nie jest używane dla drbg.
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania DRBG. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku usługi DRBG rozmiar metadanych musi być *sizeof(NX_CRYPTO_DRBG)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania DRBG z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

Wykonywanie operacji DRBG

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację DRBG. Blok sterowania DRBG musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_drbg_init()*. Algorytm DRBG do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody. Domyślnie dla drbg jest używany standard AES-128.

Gdy operacja jest NX_CRYPTO_DRBG_OPTIONS_SET, dane wejściowe wskazuje NX_CRYPTO_DRBG_OPTIONS strukturę. Gdy operacja jest NX_CRYPTO_DRBG_INSTANTIATE, klucz wskazuje wartość nonce, a punkty wejściowe na ciąg personalizacji. Gdy operacja jest NX_CRYPTO_DRBG_RESEED lub NX_CRYPTO_DRBG_GENERATE, dane wejściowe wskazuje dodatkowe dane wejściowe.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej DRBG. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *_nx_crypto_method_drbg_init().*
- **klucz** Wskaźnik do wskaźnika nonce dla operacji wystąpienia. To pole nie jest używane w przypadku innych operacji.
- **key_size_in_bits** Rozmiar nonce w bitach. To pole nie jest używane w przypadku innych operacji.
- **dane wejściowe** Po NX_CRYPTO_DRBG_OPTIONS_SET to pole wskazuje opcje DRBG. Po NX_CRYPTO_DRBG_INSTANTIATE to pole wskazuje ciąg personalizacji. Gdy opa NX_CRYPTO_DRBG_RESEED lub NX_CRYPTO_DRBG_GENERATE, to pole wskazuje dodatkowe dane wejściowe.
- **input_length_in_byte** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla drbg.
- **dane wyjściowe** Po NX_CRYPTO_DRBG_GENERATE to pole wskazuje obszar pamięci dla wygenerowanej strefy DRBG. W przeciwnym razie to pole nie jest używane.
- **output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania DRBG używanego w funkcji *_nx_crypto_method_drbg_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku usługi DRBG rozmiar metadanych musi *być sizeof(NX_CRYPTO_DRBG)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm DRBG.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

Wyczyść blok sterowania DRBG.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję w celu oczyszczenia bloku sterowania DRBG po ustaleniu, że ta sesja DRBG nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania DRBG używanego w funkcji *_nx_crypto_method_drbg_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

## <a name="_nx_crypto_method_ecdh_init"></a>_nx_crypto_method_ecdh_init

Inicjuje blok kontroli kryptografii ECDH

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania ECDH z danym ciągiem klucza. Po zainicjowania bloku sterowania ECDH kolejna operacja ECDH musi używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterowania ECDH, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania ECDH uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku kontrolki ECDH porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych ECDH. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_ecdh*
- **klucz** To pole nie jest używane dla ECDH.
- **key_size_in_bits** To pole nie jest używane dla ECDH.
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania ECDH. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku usługi ECDH rozmiar metadanych musi być *sizeof(NX_CRYPTO_ECDH)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania ECDH z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

Wykonywanie operacji ECDH

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację ECDH. Blok sterowania ECDH musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_ecdh_init()*. Algorytm ECDH do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody.

Gdy operacja jest NX_CRYPTO_EC_CURVE_SET, dane wejściowe wskazuje metodę kryptograficzna krzywej eliptycznej. Po NX_CRYPTO_EC_KEY_PAIR_GENERATE dane wyjściowe wskazuje na NX_CRYPTO_EXTENDED_OUTPUT, a para kluczy jest kopiowana do nx_crypto_extended_output_data. Po NX_CRYPTO_DH_SETUP klucz publiczny jest zwracany do nx_crypto_extended_output_data. Gdy operacja jest NX_CRYPTO_DH_KEY_PAIR_IMPORT, dane wejściowe wskazuje klucz publiczny, a klucz na klucz prywatny. Po NX_CRYPTO_DH_PRIVATE_KEY_EXPORT klucz prywatny jest kopiowany do nx_crypto_extended_output_data. Gdy operacja jest NX_CRYPTO_DH_CALCULATE, dane wejściowe wskazuje zdalny klucz publiczny i wspólny klucz tajny są kopiowane do nx_crypto_extended_output_data.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej ECDH. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *_nx_crypto_method_ecdh_init().*
- **klucz** Po NX_CRYPTO_DH_IMPORT_KEY_PAIR to pole wskazuje na klucz prywatny. W przeciwnym razie to pole nie jest używane dla ECDH.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **dane wejściowe** Gdy operacje są NX_CRYPTO_EC_CURVE_SET, to pole wskazuje na metodę kryptograficzna krzywej eliptycznej. Gdy jest NX_CRYPTO_DH_SETUP, to pole nie jest używane. Po NX_CRYPTO_DH_CALCULATE to pole wskazuje bufor zawierający wejściowe dane tekstowe. Po NX_CRYPTO_DH_IMPORT_KEY_PAIR to pole wskazuje klucz publiczny.
- **input_length_in_byte** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla ECDH.
- **dane wyjściowe** W przypadku NX_CRYPTO_EC_CURVE_SET lub NX_CRYPTO_DH_IMPORT_KEY_PAIR to pole nie jest używane. Po NX_CRYPTO_DH_SETUP to pole wskazuje obszar pamięci dla wygenerowanego klucza publicznego ECDH. Po NX_CRYPTO_DH_CALCULATE to pole wskazuje obszar pamięci dla wygenerowanego wspólnego tajnego ecdh.
- **output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania ECDH używanego w funkcji *_nx_crypto_method_ecdh_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku ecdh rozmiar metadanych musi *być sizeof(NX_CRYPTO_ECDH)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm ECDH.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

Wyczyść blok sterowania ECDH.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania ECDH po ustaleniu, że ta sesja ECDH nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania ECDH używanego w funkcji *_nx_crypto_method_ecdh_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

## <a name="_nx_crypto_method_ecdsa_init"></a>_nx_crypto_method_ecdsa_init

Inicjuje blok kontroli kryptografii ECDSA

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania ECDSA z danym ciągiem klucza. Po zainicjowania bloku sterowania ECDSA kolejna operacja ECDSA powinna używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących ECDSA, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania ECDSA uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania ECDSA porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych ECDSA. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_ecdsa*
- **klucz** To pole nie jest używane w przypadku ecdsa.
- **key_size_in_bits** To pole nie jest używane w przypadku ecdsa.
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania ECDSA. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku ecdsa rozmiar metadanych musi być *sizeof(NX_CRYPTO_ECDSA)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania ECDSA z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

Wykonywanie operacji ECDSA

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację ECDSA. Blok sterowania ECDSA musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_ecdsa_init()*. Algorytm ECDSA do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody.

Gdy operacja jest NX_CRYPTO_EC_CURVE_SET, dane wejściowe wskazuje metodę kryptograficzna krzywej eliptycznej. Po NX_CRYPTO_EC_KEY_PAIR_GENERATE dane wyjściowe wskazuje na NX_CRYPTO_EXTENDED_OUTPUT, a para kluczy jest kopiowana do nx_crypto_extended_output_data.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej ECDSA. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *_nx_crypto_method_ecdsa_init().*
- **klucz** Wskazuje klucz, gdy po NX_CRYPTO_VERIFY. Nie ma żadnych ograniczeń dotyczących buforu kluczy. To pole nie jest używane dla innych wartości op.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **dane wejściowe** Gdy operacje są NX_CRYPTO_EC_CURVE_SET, to pole wskazuje na metodę kryptograficzna krzywej eliptycznej. W przeciwnym razie to pole wskazuje bufor zawierający wejściowe dane tekstowe.
- **input_length_in_byte** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane w przypadku ecdsa.
- **dane wyjściowe** W przypadku NX_CRYPTO_EC_CURVE_SET to pole nie jest używane. Po NX_CRYPTO_AUTHENTICATE to pole wskazuje obszar pamięci dla wygenerowanego podpisu ECDSA. Po NX_CRYPTO_VERIFY to pole wskazuje obszar pamięci dla zweryfikowanego podpisu ECDSA.
- **output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania ECDSA używanego w funkcji *_nx_crypto_method_ecdsa_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku ecdsa rozmiar metadanych musi *być sizeof(NX_CRYPTO_ECDSA)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm ECDSA.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

Wyczyść blok sterowania ECDSA.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania ECDSA po ustaleniu, że ta sesja ECDSA nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania ECDSA używanego w funkcji *_nx_crypto_method_ecdsa_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

Inicjuje blok formantu kryptograficznego HMAC MD5

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania HMAC MD5 z danym ciągiem klucza. Po zainicjowania bloku sterowania HMAC MD5 kolejne działanie HMAC MD5 musi używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterowania HMAC MD5, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania HMAC MD5 uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania HMAC MD5 porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych HMAC MD5.
Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_hmac_md5*
- **klucz** Wskazuje klucz. Nie ma żadnych ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania HMAC MD5. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku HMAC MD5 rozmiar metadanych musi być *sizeof(NX_CRYPTO_MD5_HMAC)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania HMAC MD5 z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

Wykonaj operację skrótu HMAC MD5.

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację skrótu HMAC MD5. Blok sterowania HMAC MD5 musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_hmac_md5_init()*. Algorytm HMAC MD5 do wykonania jest oparty na algorytmie określonym w bloku *sterowania* metodą.

W przypadku *ostatniej NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 16 bajtów.

Ta operacja nie powoduje przechowania informacji o stanie i nie zmienia materiału klucza w bloku sterowania HMAC MD5.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej HMAC MD5. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *nx_crypto_method_hmac_md5_init().*
- **klucz** Wskazuje klucz. Nie ma żadnych ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **input_data** Wskazuje bufor zawierający wejściowe dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla HMAC MD5.
- **iv_size** To pole nie jest używane dla HMAC MD5.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu HMAC MD5.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania HMAC MD5 używanego w funkcji *_nx_crypto_method_hmac_md5_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku HMAC MD5 rozmiar metadanych musi *być sizeof(NX_CRYPTO_MD5_HMAC)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację HMAC MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm HMAC MD5.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

Inicjuje blok formantu kryptograficznego HMAC SHA1

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania HMAC SHA1 z danym ciągiem klucza. Po zainicjowania bloku sterowania HMAC SHA1 kolejne działanie HMAC SHA1 musi używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterowania HMAC SHA1, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania HMAC SHA1 uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania HMAC SHA1 porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych HMAC SHA1. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_hmac_sha1*
- **klucz** Wskazuje klucz. Nie ma żadnych ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania HMAC SHA1. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku HMAC SHA1 rozmiar metadanych musi być *sizeof(NX_CRYPTO_SHA1_HMAC)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania SHA1 HMAC z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

Wykonywanie operacji skrótu SHA1 HMAC

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację skrótu SHA1 HMAC. Blok sterowania HMAC SHA1 musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_hmac_sha1_init()*. Algorytm SHA1 HMAC do wykonania jest oparty na algorytmie określonym w bloku *sterowania* metodą.

W przypadku *ostatniej NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 20 bajtów.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej HMAC SHA1. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *_nx_crypto_method_hmac_sha1_init().*
- **klucz** Wskazuje klucz. Nie ma żadnych ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **input_data** Wskazuje bufor zawierający wejściowe dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla HMAC SHA1.
- **iv_size** To pole nie jest używane dla HMAC SHA1.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA1 HMAC.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania HMAC SHA1 używanego w funkcji *_nx_crypto_method_hmac_sha1_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku HMAC SHA1 rozmiar metadanych musi *być sizeof(NX_CRYPTO_SHA1_HMAC)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację SHA1 HMAC.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm SHA1 HMAC.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

Wyczyść blok sterowania HMAC SHA1.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję w celu oczyszczenia bloku sterowania HMAC SHA1 po ustaleniu, że ta sesja HMAC SHA1 nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania HMAC SHA1 używanego w funkcji *_nx_crypto_method_hmac_sha1_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja HMAC SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

Inicjuje blok sterowania kryptograficznego HMAC SHA256

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania HMAC SHA256 z danym ciągiem klucza. Po zainicjowania bloku sterowania HMAC SHA256 kolejna operacja HMAC SHA256 musi używać tego samego bloku sterującego.

Aplikacja może utworzyć wiele bloków sterowania HMAC SHA256, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania HMAC SH256 uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania HMAC SHA256 porzuca bieżącą sesję i dodaje nowy klucz.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku sterowania metodami kryptograficznymi HMAC SHA256. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **klucz** Wskazuje klucz. Nie ma żadnych ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście zależy od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania HMAC SHA256. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku HMAC SHA256 rozmiar metadanych musi być *sizeof(NX_CRYTPO_SHA256_HMAC)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania HMAC SHA256 z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

Wykonywanie operacji skrótu HMAC SHA256

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację skrótu HMAC SHA256. Blok sterowania HMAC SHA256 musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_hmac_sha256_init()*. Algorytm SHA256 HMAC do wykonania jest oparty na algorytmie określonym w bloku *sterowania* metodą.

W przypadku *ostatniej NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 32 bajtów dla SHA256 lub 28 bajtów dla SHA224.

### <a name="parameters"></a>Parametry

- **op (op)** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej HMAC SHA256. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie _ *nx_crypto_method_hmac_sha256_init().*
- **klucz** Wskazuje klucz. Nie ma żadnych ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **input_data** Wskazuje bufor zawierający wejściowe dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla HMAC SHA256.
- **iv_size** To pole nie jest używane dla HMAC SHA256.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu HMAC SHA256.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania HMAC SHA256 używanego w funkcji *_nx_crypto_method_hmac_sha256_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku HMAC SHA256 rozmiar metadanych musi *być sizeof(NX_CRYPTO_SHA256_HMAC)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację SHA256 HMAC.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm SHA256 HMAC.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

Wyczyść blok sterowania HMAC SHA256.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję w celu oczyszczenia bloku sterowania HMAC SHA256 po ustaleniu, że ta sesja HMAC SHA256 nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania HMAC SHA256 używanego w funkcji *_nx_crypto_method_hmac_sha256_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja HMAC SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

Inicjuje blok sterowania kryptograficznego HMAC SHA512

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania HMAC SHA512 z danym ciągiem klucza. Po zainicjowania bloku sterowania HMAC SHA512 kolejna operacja HMAC SHA512 musi używać tego samego bloku sterującego.

Aplikacja może utworzyć wiele bloków sterowania HMAC SHA512, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania HMAC SH512 uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania HMAC SHA512 porzuca bieżącą sesję i dodaje nowy klucz.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku sterowania metodami kryptograficznymi HMAC SHA512. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **klucz** Wskazuje klucz. Nie ma żadnych ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście zależy od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania HMAC SHA512. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku HMAC SHA512 rozmiar metadanych musi być *sizeof(NX_CRYPTO_SHA512_HMAC)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania HMAC SHA512 z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

Wykonywanie operacji skrótu HMAC SHA512

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację skrótu HMAC SHA512. Blok sterowania HMAC SHA512 musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_hmac_sha512_init()*. Algorytm HMAC SHA512 do wykonania jest oparty na algorytmie określonym w bloku *sterowania* metodą.

W przypadku *ostatniej NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 64 bajtów dla SHA512 lub 48 bajtów dla SHA384.

### <a name="parameters"></a>Parametry

- **op (op)** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej HMAC SHA512. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie _ *nx_crypto_method_hmac_sha512_init().*
- **klucz** Wskazuje klucz. Nie ma żadnych ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **input_data** Wskazuje bufor zawierający wejściowe dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla HMAC SHA512.
- **iv_size** To pole nie jest używane dla HMAC SHA512.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu HMAC SHA512.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania HMAC SHA512 używanego w funkcji *_nx_crypto_method_hmac_sha512_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku HMAC SHA512 rozmiar metadanych musi *być NX_CRYPTO_SHA512_HMAC)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację HMAC SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm SHA512 HMAC.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

Wyczyść blok sterowania HMAC SHA512.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję w celu oczyszczenia bloku sterowania HMAC SHA512 po ustaleniu, że ta sesja HMAC SHA512 nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania HMAC SHA512 używanego w funkcji *_nx_crypto_method_hmac_sha512_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja HMAC SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

### <a name="example"></a>Przykład 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

Inicjuje blok kontroli kryptografii MD5

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterujący MD5 przy użyciu danego ciągu klucza. Po zainicjowania bloku sterowania MD5 kolejnej operacji MD5 musi używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących MD5, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania MD5 uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania MD5 porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych MD5. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_md5*
- **klucz** To pole nie jest używane w przypadku rozwiązania MD5.
- **key_size_in_bits** To pole nie jest używane w przypadku rozwiązania MD5
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście zależy od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania MD5. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku md5 rozmiar metadanych musi być *sizeof(NX_CRYPTO_MD5)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania MD5 z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

### <a name="example"></a>Przykład

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

Wykonaj operację skrótu MD5.

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację skrótu MD5. Blok sterowania MD5 musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_md5_init()*. Algorytm MD5 do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody.

W przypadku *ostatniej NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 16 bajtów.

Ta operacja nie powoduje przechowania informacji o stanie i nie zmienia materiału klucza w bloku sterowania MD5.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej MD5. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *_nx_crypto_method_md5_init().*
- **input_data** Wskazuje bufor zawierający wejściowe dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane w przypadku rozwiązania MD5.
- **iv_size** To pole nie jest używane w przypadku rozwiązania MD5.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu MD5.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. W przypadku rozwiązania MD5 rozmiar buforu musi być 16 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania MD5 używanego w funkcji *_nx_crypto_method_md5_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku md5 rozmiar metadanych musi *być sizeof(NX_CRYPTO_MD5)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm MD5.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

Wyczyść blok sterowania MD5.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania MD5 po ustaleniu, że ta sesja MD5 nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania MD5 używanego w funkcji *_nx_crypto_method_md5_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

## <a name="_nx_crypto_method_sha1_init"></a>_nx_crypto_method_sha1_init

Inicjuje blok kontroli kryptografii SHA1

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania SHA1 z danym ciągiem klucza. Po zainicjowania bloku sterowania SHA1 kolejna operacja SHA1 musi używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterowania SHA1, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania SHA1 uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania SHA1 porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych SHA1. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_sha1*
- **klucz** To pole nie jest używane dla sha1.
- **key_size_in_bits** To pole nie jest używane dla sha1
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania SHA1. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku sha1 rozmiar metadanych musi być *sizeof(NX_CRYPTO_SHA1)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku SHA1control z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

Wykonywanie operacji wyznaczania wartości skrótu SHA1

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację wyznaczania wartości skrótu SHA1. Blok sterowania SHA1 musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_sha1_init()*. Algorytm SHA1 do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody.

W przypadku *ostatniej NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 20 bajtów.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA1. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie *nx_crypto_method_sha1_init().*
- **input_data** Wskazuje bufor zawierający wejściowe dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla sha1.
- **iv_size** To pole nie jest używane dla sha1.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA1.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. W przypadku sha1 rozmiar buforu musi być 20 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania SHA1 używanego w funkcji *_nx_crypto_method_sha1_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku sha1 rozmiar metadanych musi *być sizeof(NX_CRYPTO_SHA1)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm SHA1.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

### <a name="example"></a>Przykład

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

Wyczyść blok sterowania SHA1.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję w celu oczyszczenia bloku sterowania SHA1 po ustaleniu, że ta sesja SHA1 nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania SHA1 używanego w funkcji *_nx_crypto_method_sha1_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

Inicjuje blok sterowania kryptograficznego SHA256

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania SHA256 z danym ciągiem klucza. Po zainicjowania bloku sterowania SHA256 kolejna operacja SHA256 musi używać tego samego bloku sterującego.

Aplikacja może utworzyć wiele bloków sterowania SHA256, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania SHA256 uruchamia nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania SHA256 porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych SHA256. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **klucz** To pole nie jest używane dla sha256.
- **key_size_in_bits** To pole nie jest używane dla sha256
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście zależy od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania SHA256. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku sha256 rozmiar metadanych musi być *sizeof(NX_CRYPTO_SHA256)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania SHA256 z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

Wykonywanie operacji wyznaczania wartości skrótu SHA256

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację wyznaczania wartości skrótu SHA256. Blok sterowania SHA256 musi zostać zainicjowany za pomocą funkcji _ ***nx_crypto_method_sha256_init()***. Algorytm SHA256 do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody.

W przypadku *ostatniej NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 32 bajtów dla SHA256 lub 28 bajtów dla SHA224.

### <a name="parameters"></a>Parametry

- **op (op)** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA256. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie _ *nx_crypto_method_sha256_init().*
- **input_data** Wskazuje bufor zawierający wejściowe dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla sha256.
- **iv_size** To pole nie jest używane dla sha256.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA256.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. W przypadku sha256 rozmiar buforu musi być 32 bajty. W przypadku sha224 rozmiar buforu musi być 28 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania SHA2 używanego w funkcji *_nx_crypto_method_sha2_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku sha256 rozmiar metadanych musi *być sizeof(NX_CRYPTO_SHA256)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki Kryptograficzne NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm SHA256.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

Wyczyść blok sterowania SHA256.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję w celu oczyszczenia bloku sterowania SHA256 po ustaleniu, że ta sesja SHA256 nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania SHA256 używanego w funkcji *_nx_crypto_method_sha256_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.

## <a name="_nx_crypto_method_sha512_init"></a>_nx_crypto_method_sha512_init

Inicjuje blok kontroli kryptografii SHA512

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a>Opis

Ta funkcja inicjuje blok sterowania SHA512 z danym ciągiem klucza. Po zainicjowania bloku sterowania SHA512 kolejna operacja SHA512 musi używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterowania SHA512, z których każdy reprezentuje sesję. Inicjowanie bloku sterowania SHA512 rozpoczyna nową sesję obliczania skrótu. Ponowne inicjowanie bloku sterowania SHA512 porzuca bieżącą sesję i dodaje nową.

### <a name="parameters"></a>Parametry

- **metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznych SHA512. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **klucz** To pole nie jest używane dla sha512.
- **key_size_in_bits** To pole nie jest używane dla sha512
- **dojście** Ta usługa zwraca dojście do wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja musi przekazać wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik do prawidłowego miejsca w pamięci dla bloku sterowania SHA512. Adres początkowy przestrzeni pamięci musi być wyrównany o 4 bajty.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku sha512 rozmiar metadanych musi być *sizeof(NX_CRYPTO_SHA512)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślne zainicjowanie bloku sterowania SHA512 z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik do klucza, nieprawidłowy crypto_metadata lub crypto_metadata_size albo crypto_metadata nie jest wyrównany o 4 bajty.

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

Wykonywanie operacji wyznaczania wartości skrótu SHA512

### <a name="prototype"></a>Prototype

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

### <a name="description"></a>Opis

Ta funkcja wykonuje operację wyznaczania wartości skrótu SHA512. Blok sterowania SHA512 musi zostać zainicjowany za pomocą funkcji _ *nx_crypto_method_sha512_init()*. Algorytm SHA512 do wykonania jest oparty na algorytmie określonym w bloku *kontroli* metody.

W przypadku *ostatniej NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 64 bajtów dla sha512 lub 48 bajtów dla SHA384.

### <a name="parameters"></a>Parametry

- **op** Typ operacji do wykonania. Prawidłowa operacja to:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **dojście** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA512. Używana tutaj metoda kryptograficzna musi być taka sama jak w metodzie _ *nx_crypto_method_sha512_init().*
- **input_data** Wskazuje bufor zawierający wejściowe dane tekstowe. Nie ma żadnych ograniczeń dotyczących buforu wejściowego.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla sha512.
- **iv_size** To pole nie jest używane dla sha512.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA512.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. W przypadku sha512 rozmiar buforu musi być 64 bajtów. W przypadku sha384 rozmiar buforu musi być 48 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania SHA512 używanego w funkcji *_nx_crypto_method_sha512_init()*.
- **crypto_metadata_size** Rozmiar w bajtach obszaru crypto_metadata danych. W przypadku sha512 rozmiar metadanych musi być *sizeof(NX_CRYPTO_SHA512)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznych NetX. Wszystkie przekazane wartości są ignorowane w trybie dyskretnym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wykonano operację SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Określono nieprawidłowy algorytm SHA512.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

Wyczyść blok sterowania SHA512.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję w celu oczyszczenia bloku sterowania SHA512 po ustaleniu, że ta sesja SHA512 nie jest już potrzebna.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania SHA512 używanego w funkcji *_nx_crypto_method_sha512_init()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0x00) Pomyślnie wyczyszczona sesja SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej używać.