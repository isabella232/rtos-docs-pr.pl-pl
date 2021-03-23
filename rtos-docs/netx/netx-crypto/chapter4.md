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
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a>Rozdział 4 — opis interfejsu API kryptografii usługi Azure RTO NetX

## <a name="nx_crypto_initialize"></a>nx_crypto_initialize

Inicjuje bezpieczną bibliotekę NetX

### <a name="prototype"></a>Prototype

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a>Opis

Ta funkcja Inicjuje moduł biblioteki kryptograficznej Azure RTO NetX. Przed użyciem którejkolwiek z innych funkcji kryptograficznych, aplikacja musi wywołać tę funkcję, aby wykonać inicjalizację i zweryfikować integralność biblioteki. Niepowodzenie wywołania tej funkcji przed użyciem innych usług kryptograficznych NetX spowoduje zwrócenie błędów.

### <a name="parameters"></a>Parametry

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie zainicjowano bibliotekę kryptograficzną NetX. Funkcje biblioteki są teraz gotowe i mogą być używane.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) nie można zainicjować biblioteki kryptograficznej lub błąd sprawdzania integralności. Aplikacja nie może użyć tej biblioteki.

### <a name="example"></a>Przykład

CZYNNOŚĆ

## <a name="nx_crypto_module_state_get"></a>nx_crypto_module_state_get

Pobieranie bieżącego stanu modułu z obsługą FIPS

### <a name="prototype"></a>Prototype

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a>Opis

Ta usługa jest dostępna tylko w bibliotece kompilacji FIPS. Zwraca stan bieżącego stanu biblioteki kryptograficznej NetX.

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

CZYNNOŚĆ

## <a name="_nx_crypto_method_aes_init"></a>_nx_crypto_method_aes_init

Inicjuje blok kontroli kryptograficznej AES

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

Ta funkcja inicjuje blok kontrolny AES z danym ciągiem klucza. Po zainicjowaniu bloku sterowania AES kolejna operacja AES będzie używać tego samego klucza i rozmiaru klucza.

Aplikacja może tworzyć wiele bloków formantów AES, każda reprezentuje sesję. Klucz jest przypisywany do bloku sterującego. Kolejna operacja szyfrowania lub odszyfrowywania może odwoływać się do tego samego bloku kontrolki AES bez konieczności ponownego inicjowania bloku sterowania AES. Jeśli klucz sesji zostanie zmieniony, aplikacja musi ponownie zainicjować blok kontroli AES ze zaktualizowanym kluczem.

Wywołanie _ *nx_crypto_method_aes_init ()* automatycznie aktualizuje wcześniej skonfigurowany klucz i rozmiar klucza do nowego klucza.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej AES. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne AES:
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
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania AES. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu AES rozmiar metadanych musi mieć wartość *sizeof (NX_AES)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku kontrolki AES przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.
- Rozmiar klucza **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) nie jest prawidłowy dla algorytmu AES.

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

Ta funkcja wykonuje operację szyfrowania lub odszyfrowywania AES. Blok sterowania AES musi być zainicjowany przy użyciu _ *nx_crypto_method_aes_init ()*. Algorytm AES ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .

Rozmiar buforu wejściowego musi być wielokrotnością 16 bajtów. Rozmiar odszyfrowanych danych ma taki sam rozmiar jak rozmiar danych wejściowych. Jeśli zaszyfrowane dane zostały uzupełnione w celu osiągnięcia nawet wielokrotności rozmiaru bloku AES, uzupełnienie zostanie uwzględnione w buforze wyjściowym i musi być obsługiwane przez aplikację.

Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku sterowania AES.

Gdy op jest NX_CRYPTO_SET_ADDITIONAL_DATA, a algoritm to AES-CCM8, punkty wejścia do dodatkowych danych i input_length_in_byte to długość dodatkowych danych.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowe Operations:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
  - *NX_CRYPTO_AUTHENTICATE (tylko algorytm AES-XCBC)*
  - *NX_CRYPTO_SET_ADDITIONAL_DATA (tylko algorytm AES-CCM8)*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej AES. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_aes_init ().*
- **input_data** Wskazuje bufor zawierający dane zaszyfrowanego tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach. Rozmiar danych wejściowych musi być wielokrotnością 16 bajtów.
- **iv_ptr** Wskaźnik do początkowego wektora. Nie ma żadnych ograniczeń dotyczących buforu IV.
- **iv_size** Rozmiar początkowego bloku wektora, w bajtach to pole musi być 16.
- **output_buffer** Wskaźnik do obszaru pamięci dla algorytmu AES, aby przechowywać dane w postaci zwykłego tekstu. Aplikacja musi przydzielić miejsce dla buforu wyjściowego. Bufor wyjściowy może nakładać się na bufor wejściowy. Bufor wyjściowy może nakładać się na bufor wejściowy, jeśli korzystają one z tego samego adresu początkowego.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. Rozmiar buforu wyjściowego musi być co najmniej taki sam jak rozmiar buforu wejściowego, a rozmiar buforu wyjściowego musi być wielokrotnością 16 bajtów.
- **crypto_metadata** Wskaźnik do bloku kontrolki AES używanego w *_nx_crypto_method_aes_init () \* . \**
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu AES rozmiar metadanych musi mieć wartość *sizeof (NX_AES)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** — to pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację AES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm AES * *.

## <a name="_nx_crypto_method_aes_cleanup"></a>_nx_crypto_method_aes_cleanup

Wyczyść blok kontroli AES.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby wyczyścić blok kontroli AES po ustaleniu, że ta sesja AES nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku kontrolki AES używanego w *_nx_crypto_method_aes_init () \* . \**

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję AES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

## <a name="_nx_crypto_method_3des_init"></a>_nx_crypto_method_3des_init

Zainicjuj blok kontroli 3DES.

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

Ta funkcja inicjuje blok sterowania potrójnym algorytmem DES (3DES) z podanym trzema ciągami kluczy. Ciągi kluczy muszą zawierać 8 bajtów. Trzy klucze DES muszą być połączone z ciągłą ilością pamięci w buforze 24-bajtowym. W przypadku kompilacji zgodnej ze standardem FIPS trzy klucze muszą być inne niż poszczególne lub funkcja zwróci błąd NX_CRYPTO_INVALID_KEY. Po zainicjowaniu bloku sterowania algorytmem 3DES kolejne operacje 3DES będą używać tych samych kluczy.

Aplikacja może utworzyć wiele bloków sterujących algorytmem 3DES, z których każda reprezentuje sesję. Klucz jest przypisywany do bloku sterowania, a kolejne operacje szyfrowania lub odszyfrowywania mogą odwoływać się do tego samego bloku sterowania bez konieczności ponownego inicjowania. Jeśli klucz sesji zostanie zmieniony, aplikacja będzie musiała ponownie zainicjować blok kontroli ze zaktualizowanym kluczem.

Wywołanie _ *nx_crypto_method_3des_init ()* automatycznie aktualizuje wcześniej skonfigurowany klucz do nowych kluczy.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku kontroli metody szyfrowania 3DES. Dostępna jest następująca wstępnie zdefiniowana Metoda kryptograficzna 3DES: ***crypto_method_3des***
- **klucz** Wskazuje bufor zawierający trzy (3) klucz DES
- **key_size_in_bits** Musi być 192 (3 klucze, każdy 64 bitów).
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście identyfikuje blok kontroli 3DES. Kolejne operacje 3DES (szyfrowanie, odszyfrowywanie i czyszczenie) używają tego uchwytu do uzyskiwania dostępu do bloku sterowania 3DES
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania 3DES. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu 3DES rozmiar metadanych musi mieć wartość *sizeof (NX_3DES)*

### <a name="return-value"></a>Wartość zwracana

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku kontroli 3DES z rozmiarem klucza i klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.
- Rozmiar klucza **NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) nie jest prawidłowy dla algorytmu 3DES.

## <a name="_nx_crypto_method_3des_operation"></a>_nx_crypto_method_3des_operation

Szyfrowanie lub odszyfrowywanie przy użyciu algorytmu 3DES.

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

Ta funkcja wykonuje operacje szyfrowania 3DES lub odszyfrowywania. Blok kontroli 3DES musi być zainicjowany przy użyciu _ *nx_crypto_method_3des_init ()*. Algorytm 3DES ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .

Rozmiar buforu wejściowego musi być wielokrotnością 8 bajtów. Rozmiar odszyfrowanych danych ma taki sam rozmiar jak rozmiar danych wejściowych. Jeśli zaszyfrowane dane zostały uzupełnione w celu osiągnięcia nawet wielokrotności rozmiaru bloku 3DES, uzupełnienie zostanie uwzględnione w buforze wyjściowym i musi być obsługiwane przez aplikację.

Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku kontroli 3DES.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowe operacje:
  - *NX_CRYPTO_ENCRYPT*
  - *NX_CRYPTO_DECRYPT*
- **Obsługa** Dojście zainicjowane przez *_nx_crypto_method_3des_init ()*.
- **Metoda** Wskaźnik do prawidłowej metody szyfrowania 3DES. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_3des_init ().*
- **input_data** Wskazuje bufor zawierający dane zaszyfrowanego tekstu.
Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach. Rozmiar danych wejściowych musi być wielokrotnością 8 bajtów.
- **iv_ptr** Wskaźnik do początkowego wektora. Nie ma żadnych ograniczeń dotyczących buforu IV.
- **iv_size** Rozmiar początkowego bloku wektora, w bajtach to pole musi zawierać wartość 8.
- **output_buffer** Wskaźnik do obszaru pamięci dla algorytmu 3DES do przechowywania danych w postaci zwykłego tekstu. Aplikacja musi przydzielić miejsce dla buforu wyjściowego. Bufor wyjściowy może nakładać się na bufor wejściowy. Bufor wyjściowy może nakładać się na bufor wejściowy, jeśli korzystają one z tego samego adresu początkowego.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. Rozmiar buforu wyjściowego musi być co najmniej taki sam jak rozmiar buforu wejściowego, a rozmiar buforu wyjściowego musi być wielokrotnością 8 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania algorytmem 3DES używanym w *_nx_crypto_method_3des_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu 3DES rozmiar metadanych musi mieć wartość *sizeof (NX_3DES)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="description"></a>Opis

Ta funkcja wykonuje szyfrowanie 3DES. Blok kontroli 3DES musi być zainicjowany przy użyciu _ *nx_crypto_moethod_3des_init ()*. Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku kontroli 3DES. Należy zauważyć, że uzupełnienie nie jest dodawane przez tę funkcję, więc obiekt wywołujący będzie musiał obsłużyć uzupełnienie przed wywołaniem operacji szyfrowania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku kontroli 3DES z rozmiarem klucza i klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR (0x07)** Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_3des_cleanup"></a>_nx_crypto_method_3des_cleanup

Wyczyść blok kontroli 3DES.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok kontroli 3DES po ustaleniu, że ta sesja 3DES nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **Obsługa** Dojście zainicjowane przez *_nx_crypto_method_3des_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję 3DES.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

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

Ta funkcja inicjuje blok sterowania DRBG z danym ciągiem klucza. Po zainicjowaniu bloku sterowania DRBG kolejna operacja DRBG będzie używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących DRBG, każda reprezentuje sesję. Inicjalizacja bloku sterowania DRBG uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania DRBG porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną DRBG. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_drbg*
- **klucz** To pole nie jest używane w przypadku DRBG.
- **key_size_in_bits** To pole nie jest używane w przypadku DRBG.
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania DRBG. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku DRBG rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_DRBG)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania DRBG przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_drbg_operation"></a>_nx_crypto_method_drbg_operation

Wykonaj operację DRBG

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

Ta funkcja wykonuje operację DRBG. Blok sterowania DRBG musi zostać zainicjowany przy użyciu _ *nx_crypto_method_drbg_init ()*. Algorytm DRBG ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* . Domyślnie algorytm AES-128 jest używany dla DRBG.

Gdy operacja jest NX_CRYPTO_DRBG_OPTIONS_SET, punkty wejścia do NX_CRYPTO_DRBG_OPTIONS struktury. Gdy operacja jest NX_CRYPTO_DRBG_INSTANTIATE, klucz wskazuje identyfikator jednorazowy, punkty wejścia do ciągu personalizacji. Gdy operacja jest NX_CRYPTO_DRBG_RESEED lub NX_CRYPTO_DRBG_GENERATE, punkty wejścia wskazują dodatkowe dane wejściowe.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_DRBG_OPTIONS_SET*
  - *NX_CRYPTO_DRBG_INSTANTIATE*
  - *NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej DRBG. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_drbg_init _ ().*
- **klucz** Wskaźnik na identyfikator jednorazowy operacji tworzenia wystąpienia. To pole nie jest używane w przypadku innych operacji.
- **key_size_in_bits** Rozmiar identyfikatora jednorazowego w bitach. To pole nie jest używane w przypadku innych operacji.
- **dane wejściowe** Gdy jest NX_CRYPTO_DRBG_OPTIONS_SET, to pole wskazuje opcje DRBG. Gdy jest NX_CRYPTO_DRBG_INSTANTIATE, to pole wskazuje ciąg personalizacji. Gdy op jest NX_CRYPTO_DRBG_RESEED lub NX_CRYPTO_DRBG_GENERATE, to pole wskazuje dodatkowe dane wejściowe.
- **input_length_in_byte** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane w przypadku DRBG.
- **dane wyjściowe** Gdy operacja jest NX_CRYPTO_DRBG_GENERATE, to pole wskazuje obszar pamięci dla wygenerowanego DRBG. W przeciwnym razie to pole nie jest używane.
- **output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania DRBG używany w *_nx_crypto_method_drbg_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku DRBG rozmiar metadanych musi być *sizeof (NX_CRYPTO_DRBG)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm DRBG.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_drbg_cleanup"></a>_nx_crypto_method_drbg_cleanup

Wyczyść blok sterowania DRBG.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania DRBG po ustaleniu, że ta sesja DRBG nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania DRBG używany w *_nx_crypto_method_drbg_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję DRBG.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

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

Ta funkcja inicjuje blok sterowania ECDH z danym ciągiem klucza. Po zainicjowaniu bloku sterowania ECDH kolejna operacja ECDH będzie używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących ECDH, każda reprezentuje sesję. Inicjalizacja bloku sterowania ECDH uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania ECDH porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną ECDH. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_ecdh*
- **klucz** To pole nie jest używane w przypadku ECDH.
- **key_size_in_bits** To pole nie jest używane w przypadku ECDH.
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania ECDH. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku ECDH rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_ECDH)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania ECDH przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_ecdh_operation"></a>_nx_crypto_method_ecdh_operation

Wykonaj operację ECDH

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

Ta funkcja wykonuje operację ECDH. Blok sterowania ECDH musi zostać zainicjowany przy użyciu _ *nx_crypto_method_ecdh_init ()*. Algorytm ECDH ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .

Gdy operacja jest NX_CRYPTO_EC_CURVE_SET, punkty wejścia do metody kryptograficznej krzywej eliptycznej. Gdy operacja jest NX_CRYPTO_EC_KEY_PAIR_GENERATE, punkty wyjścia do struktury NX_CRYPTO_EXTENDED_OUTPUT i pary kluczy są kopiowane do nx_crypto_extended_output_data. Gdy operacja jest NX_CRYPTO_DH_SETUP, klucz publiczny jest zwracany do nx_crypto_extended_output_data. Gdy operacja jest NX_CRYPTO_DH_KEY_PAIR_IMPORT, punkty wejścia do klucza publicznego i klucza do klucza prywatnego. Gdy operacja jest NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, klucz prywatny jest kopiowany do nx_crypto_extended_output_data. Gdy operacja jest NX_CRYPTO_DH_CALCULATE, punkty wejścia do zdalnego klucza publicznego i wspólny klucz tajny są kopiowane do nx_crypto_extended_output_data.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_DH_SETUP*
  - *NX_CRYPTO_DH_CALCULATE*
  - *NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*
  - *NX_CRYPTO_DH_KEY_PAIR_GENERATE*
  - *NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej ECDH. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_ecdh_init _ ().*
- **klucz** Gdy jest NX_CRYPTO_DH_IMPORT_KEY_PAIR, to pole wskazuje na klucz prywatny. W przeciwnym razie to pole nie jest używane w przypadku ECDH.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **dane wejściowe** Gdy jest NX_CRYPTO_EC_CURVE_SET, to pole wskazuje metodę kryptograficzną krzywej eliptycznej. Gdy jest NX_CRYPTO_DH_SETUP, to pole nie jest używane. Gdy operacja jest NX_CRYPTO_DH_CALCULATE, to pole wskazuje bufor zawierający dane wejściowe tekstu. Gdy operacja jest NX_CRYPTO_DH_IMPORT_KEY_PAIR, to pole wskazuje na klucz publiczny.
- **input_length_in_byte** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane w przypadku ECDH.
- **dane wyjściowe** Gdy op jest NX_CRYPTO_EC_CURVE_SET lub NX_CRYPTO_DH_IMPORT_KEY_PAIR, to pole nie jest używane. Gdy jest NX_CRYPTO_DH_SETUP, to pole wskazuje obszar pamięci dla wygenerowanego klucza publicznego ECDH. Gdy jest NX_CRYPTO_DH_CALCULATE, to pole wskazuje obszar pamięci dla wygenerowanego wspólnego wpisu tajnego ECDH.
- **output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania ECDH używany w *_nx_crypto_method_ecdh_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku ECDH rozmiar metadanych musi być *sizeof (NX_CRYPTO_ECDH)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm ECDH.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_ecdh_cleanup"></a>_nx_crypto_method_ecdh_cleanup

Wyczyść blok sterowania ECDH.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania ECDH po ustaleniu, że ta sesja ECDH nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania ECDH używany w *_nx_crypto_method_ecdh_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję ECDH.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

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

Ta funkcja inicjuje blok sterowania ECDSA z danym ciągiem klucza. Po zainicjowaniu bloku sterowania ECDSA kolejna operacja ECDSA będzie używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących ECDSA, każda reprezentuje sesję. Inicjalizacja bloku sterowania ECDSA uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania ECDSA porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną ECDSA. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_ecdsa*
- **klucz** To pole nie jest używane w przypadku ECDSA.
- **key_size_in_bits** To pole nie jest używane w przypadku ECDSA.
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania ECDSA. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku ECDSA rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_ECDSA)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania ECDSA przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_ecdsa_operation"></a>_nx_crypto_method_ecdsa_operation

Wykonaj operację ECDSA

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

Ta funkcja wykonuje operację ECDSA. Blok sterowania ECDSA musi zostać zainicjowany przy użyciu _ *nx_crypto_method_ecdsa_init ()*. Algorytm ECDSA ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .

Gdy operacja jest NX_CRYPTO_EC_CURVE_SET, punkty wejścia do metody kryptograficznej krzywej eliptycznej. Gdy operacja jest NX_CRYPTO_EC_KEY_PAIR_GENERATE, punkty wyjścia do struktury NX_CRYPTO_EXTENDED_OUTPUT i pary kluczy są kopiowane do nx_crypto_extended_output_data.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_EC_CURVE_SET*
  - *NX_CRYPTO_AUTHENTICATE*
  - *NX_CRYPTO_VERIFY*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej ECDSA. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_ecdsa_init _ ().*
- **klucz** Wskazuje klucz, gdy operacja jest NX_CRYPTO_VERIFY. Nie ma ograniczeń dotyczących buforu kluczy. To pole nie jest używane w przypadku innych wartości op.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **dane wejściowe** Gdy jest NX_CRYPTO_EC_CURVE_SET, to pole wskazuje metodę kryptograficzną krzywej eliptycznej. W przeciwnym razie to pole wskazuje bufor zawierający dane wejściowe tekstu.
- **input_length_in_byte** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane w przypadku ECDSA.
- **dane wyjściowe** Gdy jest NX_CRYPTO_EC_CURVE_SET, to pole nie jest używane. Gdy jest NX_CRYPTO_AUTHENTICATE, to pole wskazuje obszar pamięci dla wygenerowanej sygnatury ECDSA. Gdy jest NX_CRYPTO_VERIFY, to pole wskazuje obszar pamięci dla zweryfikowanej sygnatury ECDSA.
- **output_length_in_byte** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania ECDSA używany w *_nx_crypto_method_ecdsa_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku ECDSA rozmiar metadanych musi być *sizeof (NX_CRYPTO_ECDSA)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm ECDSA.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_ecdsa_cleanup"></a>_nx_crypto_method_ecdsa_cleanup

Wyczyść blok sterowania ECDSA.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania ECDSA po ustaleniu, że ta sesja ECDSA nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania ECDSA używany w *_nx_crypto_method_ecdsa_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję ECDSA.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

## <a name="_nx_crypto_method_hmac_md5_init"></a>_nx_crypto_method_hmac_md5_init

Inicjuje blok kontroli kryptograficznej algorytmu HMAC MD5

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

Ta funkcja inicjuje blok kontrolny MD5 algorytmu z danym ciągiem klucza. Po zainicjowaniu bloku sterowania algorytmem MD5 algorytmu algorytmu, kolejne operacje HMAC MD5 używają tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących algorytmem MD5, każdy reprezentuje sesję. Inicjalizacja bloku kontroli MD5 algorytmu HMAC uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania algorytmem MD5 algorytmu porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej algorytmu algorytmu MD5.
Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_hmac_md5*
- **klucz** Wskazuje na klucz. Nie ma ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania algorytmem MD5. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu HMAC MD5 rozmiar metadanych musi być *: sizeof (NX_CRYPTO_MD5_HMAC)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania algorytmem MD5 algorytmu przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_hmac_md5_operation"></a>_nx_crypto_method_hmac_md5_operation

Wykonaj operację mieszania algorytmu HMAC MD5.

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

Ta funkcja wykonuje operację mieszania algorytmu HMAC MD5. Blok kontroli MD5 algorytmu HMAC musi być zainicjowany przy użyciu _ *nx_crypto_method_hmac_md5_init ()*. Algorytm algorytmu algorytmem MD5 w oparciu o algorytm określony w bloku sterowania *metodami* .

Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 16 bajtów.

Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku kontroli algorytmu MD5.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowych metod kryptograficznych algorytmu algorytmu MD5. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_hmac_md5_init ().*
- **klucz** Wskazuje na klucz. Nie ma ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **input_data** Wskazuje bufor zawierający dane wejściowe tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla algorytmu HMAC MD5.
- **iv_size** To pole nie jest używane dla algorytmu HMAC MD5.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu algorytmu HMAC MD5.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania algorytmem MD5 algorytmu używanego w *_nx_crypto_method_hmac_md5_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu HMAC MD5 rozmiar metadanych musi być *sizeof (NX_CRYPTO_MD5_HMAC)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA OPERACJĘ HMAC MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) podano nieprawidłowy algorytm algorytmu MD5.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_hmac_sha1_init"></a>_nx_crypto_method_hmac_sha1_init

Inicjuje blok kontroli kryptografii algorytmu szyfrowania HMAC

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

Ta funkcja inicjuje blok kontroli SHA1 algorytmu HMAC z danym ciągiem klucza. Po zainicjowaniu bloku sterowania SHA1 algorytmem HMAC kolejna operacja algorytmu SHA1 będzie używać tego samego bloku sterowania.

Aplikacja może tworzyć wiele bloków sterowania SHA1 algorytmem HMAC, każdy reprezentuje sesję. Inicjalizacja bloku kontroli SHA1 algorytmu HMAC uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku kontroli SHA1 algorytmu HMAC porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną algorytmu SHA1. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_hmac_sha1*
- **klucz** Wskazuje na klucz. Nie ma ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA1 algorytmu HMAC. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. Dla algorytmu SHA1 algorytmem, rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA1_HMAC)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślne INICJOWANIE bloku HMAC SHA1control z kluczem i rozmiarem klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_hmac_sha1_operation"></a>_nx_crypto_method_hmac_sha1_operation

Wykonywanie operacji skrótu SHA1 algorytmu HMAC

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

Ta funkcja wykonuje operację mieszania algorytmu HMAC. Blok sterowania SHA1 algorytmem HMAC musi być zainicjowany przy użyciu _ *nx_crypto_method_hmac_sha1_init ()*. Algorytm SHA1 algorytmu HMAC ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .

Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 20 bajtów.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej algorytmu SHA1. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_hmac_sha1_init _ ().*
- **klucz** Wskazuje na klucz. Nie ma ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **input_data** Wskazuje bufor zawierający dane wejściowe tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla algorytmu SHA1 algorytmem HMAC.
- **iv_size** To pole nie jest używane dla algorytmu SHA1 algorytmem HMAC.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA1 algorytmu HMAC.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania SHA1 algorytmem HMAC używanym w *_nx_crypto_method_hmac_sha1_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. Dla algorytmu SHA1 algorytmem, rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA1_HMAC)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację SHA1 algorytmu HMAC.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA1 algorytmu HMAC.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a>_nx_crypto_method_hmac_sha1_cleanup

Wyczyść blok sterowania algorytmem SHA1 algorytmu HMAC.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania SHA1 algorytmu HMAC po ustaleniu, że ta sesja SHA1 nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania SHA1 algorytmem HMAC używanym w *_nx_crypto_method_hmac_sha1_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA1 algorytmu HMAC.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

## <a name="_nx_crypto_method_hmac_sha256_init"></a>_nx_crypto_method_hmac_sha256_init

Inicjuje blok sterowania kryptografią SHA256 HMAC

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

Ta funkcja inicjuje blok sterowania SHA256 HMAC z danym ciągiem klucza. Po zainicjowaniu bloku sterowania SHA256 HMAC kolejna operacja SHA256 jest używana w tym samym bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących SHA256 HMAC, każdy reprezentuje sesję. Inicjalizacja bloku sterowania SH256 HMAC uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania SHA256 HMAC porzuca bieżącą sesję i gwiazdy nową z nowym kluczem.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną SHA256. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_hmac_sha224*
  - *crypto_method_hmac_sha256*
- **klucz** Wskazuje na klucz. Nie ma ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA256 HMAC. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku SHA256 HMAC rozmiar metadanych musi mieć wartość *sizeof (NX_CRYTPO_SHA256_HMAC)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania SHA256 HMAC przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_hmac_sha256_operation"></a>_nx_crypto_method_hmac_sha256_operation

Wykonywanie operacji skrótu SHA256 HMAC

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

Ta funkcja wykonuje operację mieszania SHA256. Blok sterowania SHA256 HMAC musi być zainicjowany przy użyciu _ *nx_crypto_method_hmac_sha256_init ()*. Algorytm SHA256 HMAC ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .

Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 32 bajtów dla SHA256 lub 28 bajtów dla SHA224.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej HMAC SHA256. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_hmac_sha256_init _ ().*
- **klucz** Wskazuje na klucz. Nie ma ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **input_data** Wskazuje bufor zawierający dane wejściowe tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla HMAC SHA256.
- **iv_size** To pole nie jest używane dla HMAC SHA256.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA256 HMAC.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania SHA256 HMAC używanego w *_nx_crypto_method_hmac_sha256_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku SHA256 HMAC rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA256_HMAC)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA OPERACJĘ SHA256 HMAC.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA256 HMAC.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a>_nx_crypto_method_hmac_sha256_cleanup

Wyczyść blok sterowania SHA256 HMAC.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania SHA256 HMAC po ustaleniu, że ta funkcja nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania SHA256 HMAC używanego w *_nx_crypto_method_hmac_sha256_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA256 HMAC.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

## <a name="_nx_crypto_method_hmac_sha512_init"></a>_nx_crypto_method_hmac_sha512_init

Inicjuje blok sterowania kryptografią SHA512 HMAC

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

Ta funkcja inicjuje blok sterowania SHA512 HMAC z danym ciągiem klucza. Po zainicjowaniu bloku sterowania SHA512 HMAC kolejna operacja SHA512 jest używana w tym samym bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących SHA512 HMAC, każdy reprezentuje sesję. Inicjalizacja bloku sterowania SH512 HMAC uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania SHA512 HMAC porzuca bieżącą sesję i gwiazdy nową z nowym kluczem.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną SHA512. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_hmac_sha384*
  - *crypto_method_hmac_sha512*
- **klucz** Wskazuje na klucz. Nie ma ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA512 HMAC. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku SHA512 HMAC rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA512_HMAC)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania SHA512 HMAC przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_hmac_sha512_operation"></a>_nx_crypto_method_hmac_sha512_operation

Wykonywanie operacji skrótu SHA512 HMAC

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

Ta funkcja wykonuje operację mieszania SHA512. Blok sterowania SHA512 HMAC musi być zainicjowany przy użyciu _ *nx_crypto_method_hmac_sha512_init ()*. Algorytm SHA512 HMAC ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .

Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 64 bajtów dla SHA512 lub 48 bajtów dla SHA384.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej HMAC SHA512. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_hmac_sha512_init _ ().*
- **klucz** Wskazuje na klucz. Nie ma ograniczeń dotyczących buforu kluczy.
- **key_size_in_bits** Rozmiar klucza w bitach.
- **input_data** Wskazuje bufor zawierający dane wejściowe tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane dla HMAC SHA512.
- **iv_size** To pole nie jest używane dla HMAC SHA512.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA512 HMAC.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach.
- **crypto_metadata** Wskaźnik do bloku sterowania SHA512 HMAC używanego w *_nx_crypto_method_hmac_sha512_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku SHA512 HMAC rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA512_HMAC)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA OPERACJĘ SHA512 HMAC.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA512 HMAC.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a>_nx_crypto_method_hmac_sha512_cleanup

Wyczyść blok sterowania SHA512 HMAC.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby wyczyścić blok sterowania SHA512 HMAC po ustaleniu, że ta funkcja nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania SHA512 HMAC używanego w *_nx_crypto_method_hmac_sha512_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA512 HMAC.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

### <a name="example"></a>Przykład 

## <a name="_nx_crypto_method_md5_init"></a>_nx_crypto_method_md5_init

Inicjuje blok kontroli kryptograficznej MD5

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

Ta funkcja inicjuje blok kontroli MD5 z danym ciągiem klucza. Po zainicjowaniu bloku kontroli MD5 kolejna operacja MD5 będzie używać tego samego bloku sterowania.

Aplikacja może tworzyć wiele bloków kontroli MD5, każda reprezentuje sesję. Inicjalizacja bloku kontroli MD5 uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku kontroli MD5 porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej MD5. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_md5*
- **klucz** To pole nie jest używane w przypadku algorytmu MD5.
- **key_size_in_bits** To pole nie jest używane dla algorytmu MD5
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku kontroli MD5. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu MD5 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_MD5)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku kontroli MD5 przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

### <a name="example"></a>Przykład

## <a name="_nx_crypto_method_md5_operation"></a>_nx_crypto_method_md5_operation

Wykonaj operację mieszania MD5.

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

Ta funkcja wykonuje operację mieszania MD5. Blok kontroli MD5 musi być zainicjowany przy użyciu _ *nx_crypto_method_md5_init ()*. Algorytm MD5 ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .

Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 16 bajtów.

Ta operacja nie zachowuje informacji o stanie i nie zmienia materiału klucza w bloku kontroli MD5.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej MD5. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_md5_init _ ().*
- **input_data** Wskazuje bufor zawierający dane wejściowe tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane w przypadku algorytmu MD5.
- **iv_size** To pole nie jest używane w przypadku algorytmu MD5.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu MD5.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. W przypadku algorytmu MD5 rozmiar buforu musi wynosić 16 bajtów.
- **crypto_metadata** Wskaźnik do bloku kontroli MD5 używanego w *_nx_crypto_method_md5_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu MD5 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_MD5)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm MD5.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_md5_cleanup"></a>_nx_crypto_method_md5_cleanup

Wyczyść blok kontroli MD5.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok kontroli MD5 po ustaleniu, że ta sesja MD5 nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku kontroli MD5 używanego w *_nx_crypto_method_md5_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję MD5.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

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

Ta funkcja inicjuje blok sterowania SHA1 z danym ciągiem klucza. Po zainicjowaniu bloku sterowania SHA1 kolejna operacja SHA1 będzie używać tego samego bloku sterowania.

Aplikacja może tworzyć wiele bloków sterowania SHA1, każdy reprezentuje sesję. Inicjalizacja bloku sterowania SHA1 uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania SHA1 porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku kontroli metody kryptograficznej SHA1. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_sha1*
- **klucz** To pole nie jest używane na potrzeby algorytmu SHA1.
- **key_size_in_bits** To pole nie jest używane na potrzeby algorytmu SHA1
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA1. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu SHA1 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA1)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku SHA1control z rozmiarem klucza i klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_sha1_operation"></a>_nx_crypto_method_sha1_operation

Wykonywanie operacji skrótu SHA1

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

Ta funkcja wykonuje operację mieszania SHA1. Blok sterowania SHA1 musi być zainicjowany przy użyciu _ *nx_crypto_method_sha1_init ()*. Algorytm SHA1 ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metody* .

Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 20 bajtów.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA1. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_sha1_init ().*
- **input_data** Wskazuje bufor zawierający dane wejściowe tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane na potrzeby algorytmu SHA1.
- **iv_size** To pole nie jest używane na potrzeby algorytmu SHA1.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA1.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. W przypadku algorytmu SHA1 rozmiar buforu musi wynosić 20 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania algorytmem SHA1 używanym w *_nx_crypto_method_sha1_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku algorytmu SHA1 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA1)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA1.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

### <a name="example"></a>Przykład

## <a name="_nx_crypto_method_sha1_cleanup"></a>_nx_crypto_method_sha1_cleanup

Wyczyść blok sterowania SHA1.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania SHA1 po ustaleniu, że ta sesja SHA1 nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania algorytmem SHA1 używanym w *_nx_crypto_method_sha1_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA1.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

## <a name="_nx_crypto_method_sha256_init"></a>_nx_crypto_method_sha256_init

Inicjuje blok kontroli kryptografii SHA256

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

Ta funkcja inicjuje blok sterowania SHA256 z danym ciągiem klucza. Po zainicjowaniu bloku sterowania SHA256 kolejna operacja SHA256 będzie używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących SHA256, każda reprezentuje sesję. Inicjalizacja bloku sterowania SHA256 uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania SHA256 porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną SHA256. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_sha256*
  - *crypto_method_sha224*
- **klucz** To pole nie jest używane w przypadku SHA256.
- **key_size_in_bits** To pole nie jest używane w przypadku SHA256
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA256. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku SHA256 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA256)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania SHA256 przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_sha256_operation"></a>_nx_crypto_method_sha256_operation

Wykonywanie operacji skrótu SHA256

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

Ta funkcja wykonuje operację mieszania SHA256. Blok sterowania SHA256 musi zostać zainicjowany przy użyciu _ ***nx_crypto_method_sha256_init ()***. Algorytm SHA256 ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .

Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi wynosić 32 bajtów dla SHA256 lub 28 bajtów dla SHA224.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA256. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_sha256_init _ ().*
- **input_data** Wskazuje bufor zawierający dane wejściowe tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane w przypadku SHA256.
- **iv_size** To pole nie jest używane w przypadku SHA256.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA256.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. W przypadku SHA256 rozmiar buforu musi wynosić 32 bajtów. W przypadku SHA224 rozmiar buforu musi wynosić 28 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania algorytmu SHA2 używany w *_nx_crypto_method_sha2_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku SHA256 rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA256)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA256.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_sha256_cleanup"></a>_nx_crypto_method_sha256_cleanup

Wyczyść blok sterowania SHA256.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania SHA256 po ustaleniu, że ta sesja SHA256 nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania SHA256 używany w *_nx_crypto_method_sha256_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA256.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.

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

Ta funkcja inicjuje blok sterowania SHA512 z danym ciągiem klucza. Po zainicjowaniu bloku sterowania SHA512 kolejna operacja SHA512 będzie używać tego samego bloku sterowania.

Aplikacja może utworzyć wiele bloków sterujących SHA512, każda reprezentuje sesję. Inicjalizacja bloku sterowania SHA512 uruchamia nową sesję obliczeń skrótu. Ponowne inicjowanie bloku sterowania SHA512 porzuca bieżącą sesję i gwiazdy nowe.

### <a name="parameters"></a>Parametry

- **Metoda** Wskaźnik do prawidłowego bloku sterowania metodą kryptograficzną SHA512. Dostępne są następujące wstępnie zdefiniowane metody kryptograficzne:
  - *crypto_method_sha512*
  - *crypto_method_sha384*
- **klucz** To pole nie jest używane w przypadku SHA512.
- **key_size_in_bits** To pole nie jest używane w przypadku SHA512
- **Obsługa** Ta usługa zwraca dojście do obiektu wywołującego. Dojście jest zależne od implementacji i nie jest używane w tej implementacji. Aplikacja przekaże wartość NULL dla dojścia.
- **crypto_metadata** Wskaźnik na prawidłowy obszar pamięci dla bloku sterowania SHA512. Adres początkowy miejsca w pamięci musi być wyrównany 4-bajtowy.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku SHA512 rozmiar metadanych musi mieć wartość *sizeof (NX_CRYPTO_SHA512)*

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) Pomyślne inicjowanie bloku sterowania SHA512 przy użyciu klucza i rozmiaru klucza.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do klucza lub nieprawidłowy crypto_metadata lub crypto_metadata_size lub crypto_metadata nie ma 4-bajtowego wyrównania.

## <a name="_nx_crypto_method_sha512_operation"></a>_nx_crypto_method_sha512_operation

Wykonywanie operacji skrótu SHA512

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

Ta funkcja wykonuje operację mieszania SHA512. Blok sterowania SHA512 musi zostać zainicjowany przy użyciu _ *nx_crypto_method_sha512_init ()*. Algorytm SHA512 ma być wykonywany na podstawie algorytmu określonego w bloku sterowania *metodami* .

Dla ostatecznej operacji *NX_CRYPTO_HASH_CALCULATE* rozmiar buforu wyjściowego musi być 64 bajtów dla SHA512 lub 48 bajtów dla SHA384.

### <a name="parameters"></a>Parametry

- **operacja** Typ operacji do wykonania. Prawidłowa operacja:
  - *NX_CRYPTO_HASH_INITIALIZE*
  - *NX_CRYPTO_HASH_UPDATE*
  - *NX_CRYPTO_HASH_CALCULATE*
- **Obsługa** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **Metoda** Wskaźnik do prawidłowej metody kryptograficznej SHA512. Metoda kryptograficzna użyta w tym miejscu musi być taka sama, jak w *nx_crypto_method_sha512_init _ ().*
- **input_data** Wskazuje bufor zawierający dane wejściowe tekstu. Bufor wejściowy nie zawiera żadnych ograniczeń.
- **input_data_size** Rozmiar danych wejściowych w bajtach.
- **iv_ptr** To pole nie jest używane w przypadku SHA512.
- **iv_size** To pole nie jest używane w przypadku SHA512.
- **output_buffer** Wskaźnik do obszaru pamięci dla wygenerowanego skrótu SHA512.
- **output_buffer_size** Rozmiar buforu wyjściowego w bajtach. W przypadku SHA512 rozmiar buforu musi wynosić 64 bajtów. W przypadku SHA384 rozmiar buforu musi wynosić 48 bajtów.
- **crypto_metadata** Wskaźnik do bloku sterowania SHA512 używany w *_nx_crypto_method_sha512_init ()*.
- **crypto_metadata_size** Rozmiar (w bajtach) obszaru crypto_metadata. W przypadku SHA512 rozmiar metadanych musi być *sizeof (NX_CRYPTO_SHA512)*
- **packet_ptr** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.
- **nx_crypto_hw_process_callback** To pole nie jest używane w implementacji oprogramowania biblioteki kryptograficznej NetX. Wszystkie przesyłane wartości są dyskretnie ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie WYKONAŁA operację SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy lub nieprawidłowa długość.
- **NX_CRYPTO_INVALID_ALGORITHM** (0x20004) określono nieprawidłowy algorytm SHA512.
- **NX_CRYPTO_INVALID_BUFFER_SIZE** (0X20005) Nieprawidłowy rozmiar buforu wyjściowego.

## <a name="_nx_crypto_method_sha512_cleanup"></a>_nx_crypto_method_sha512_cleanup

Wyczyść blok sterowania SHA512.

### <a name="prototype"></a>Prototype

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a>Opis

Aplikacja wywołuje tę funkcję, aby oczyścić blok sterowania SHA512 po ustaleniu, że ta sesja SHA512 nie jest już wymagana.

### <a name="parameters"></a>Parametry

- **crypto_metadata** Wskaźnik do bloku sterowania SHA512 używany w *_nx_crypto_method_sha512_init ()*.

### <a name="return-values"></a>Wartości zwrócone

- **NX_CRYPTO_SUCCESS** (0X00) pomyślnie wyczyszczono sesję SHA512.
- **NX_CRYPTO_INVALID_LIBRARY** (0x20001) Biblioteka kryptograficzna jest w nieprawidłowym stanie i nie można jej użyć.