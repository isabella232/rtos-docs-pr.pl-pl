---
title: Interfejs API klas hostów USBX
description: Ten rozdział obejmuje wszystkie widoczne interfejsy API klas hostów USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28e733e37b06da7053f238e23e2b8b8046df2dd9940e50cd0321ccf15c27ec47
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802111"
---
# <a name="chapter-2-usbx-host-classes-api"></a>Rozdział 2: Interfejs API klas hostów USBX

Ten rozdział obejmuje wszystkie widoczne interfejsy API klas hostów USBX. Poniższe interfejsy API dla każdej klasy zostały szczegółowo opisane.

- Printer, klasa
- Klasa audio
- Asix, klasa
- Pima/PTP, klasa
- Prolific, klasa
- Ogólna klasa szeregowa

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

Odczyt z interfejsu drukarki.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje z interfejsu drukarki. Wywołanie jest blokowane i zwracane tylko wtedy, gdy wystąpi błąd lub gdy transfer zostanie ukończony. Odczyt jest dozwolony tylko na drukarkach dwukierunkowych.

### <a name="parameters"></a>Parametry

- **printer:** wskaźnik do wystąpienia klasy drukarki.
- **data_pointer:** Wskaźnik do adresu buforu ładunku danych.
- **requested_length:** długość do odebrania.
- **actual_length:** odebrana długość.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Ukończono transfer danych.
- **UX_FUNCTION_NOT_SUPPORTED:**(0x54) Funkcja nie jest obsługiwana, ponieważ drukarka nie jest dwukierunkowa.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Limit czasu transferu, odczytywanie niekompletne.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

Zapis w interfejsie drukarki.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja zapisuje w interfejsie drukarki. Wywołanie jest blokowane i zwracane tylko wtedy, gdy wystąpi błąd lub gdy transfer zostanie ukończony.

### <a name="parameters"></a>Parametry

- **printer:** wskaźnik do wystąpienia klasy drukarki.
- **data_pointer:** Wskaźnik do adresu buforu ładunku danych.
- **requested_length:** długość do wysłania.
- **actual_length:** długość rzeczywiście wysyłana.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Ukończono transfer danych.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Limit czasu transferu, zapis nieukończony.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

Wykonaj resetowanie programowe do drukarki.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>Opis

Ta funkcja wykonuje resetowanie nie soft do drukarki.

### <a name="input-parameter"></a>Parametr wejściowy

- **printer:** wskaźnik do wystąpienia klasy drukarki.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00)Resetowanie zostało ukończone.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Limit czasu transferu, nie ukończono resetowania.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

Uzyskiwanie stanu drukarki

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje stan drukarki. Stan drukarki jest podobny do stanu LPT (standard 1284).

### <a name="parameters"></a>Parametry

- **printer:** wskaźnik do wystąpienia klasy drukarki.
- **printer_status:** Adres stanu do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00): Resetowanie zostało ukończone.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci do wykonania operacji.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Limit czasu transferu, nie ukończono resetowania

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a>ux_host_class_printer_device_id_get

Pobierz identyfikator urządzenia drukarki.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje ciąg identyfikatora urządzenia IEEE 1284 drukarki (w tym długość w pierwszych dwóch bajtach w big endian formacie).

### <a name="parameters"></a>Parametry

- **printer:** wskaźnik do wystąpienia klasy drukarki.
- **descriptor_buffer:** wskaźnik do buforu w celu wypełnienia ciągu identyfikatora urządzenia IEEE 1284 (z uwzględnieniem długości w pierwszych dwóch bajtach w formacie BE) 
- **length:** długość buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00): operacja powiodła się.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci do wykonania operacji.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Limit czasu transferu, żądanie nie zostało ukończone
- **UX_TRANSFER_NOT_READY:**(0x25) Urządzenie było w nieprawidłowym stanie — musi być DOŁĄCZONE, ADRESOWANE lub SKONFIGUROWANE.
- **UX_TRANSFER_STALL:**(0x21) Transfer został zatrzymany.
- **TX_WAIT_ABORTED** (0x1A) Zostało przerwane przez inny wątek, czasomierz lub ISR.
- **TX_SEMAPHORE_ERROR** (0x0C) Nieprawidłowy wskaźnik zliczania semafora.
- **TX_WAIT_ERROR** (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z wątku niewątkowego.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

Odczyt z interfejsu audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje z interfejsu audio. Wywołanie nie jest blokujące. Aplikacja musi upewnić się, że wybrano odpowiednie alternatywne ustawienie dla interfejsu przesyłania strumieniowego audio.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia klasy audio.
- **audio_transfer_request:** Wskaźnik do struktury transferu audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED**" (0x54) Function not supported (Funkcja UX_FUNCTION_NOT_SUPPORTED " (0x54) nie jest obsługiwana

### <a name="example"></a>Przykład

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

Zapis w interfejsie audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>Opis

Ta funkcja zapisuje dane w interfejsie audio. Wywołanie nie jest blokujące. Aplikacja musi upewnić się, że wybrano odpowiednie alternatywne ustawienie dla interfejsu przesyłania strumieniowego audio.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia klasy audio
- **audio_transfer_request:** Wskaźnik do struktury transferu audio

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_FUNCTION_NOT_SUPPORTED:** funkcja (0x54) nie jest obsługiwana.
- **ux_host_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interfejs jest nieprawidłowy.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a>ux_host_class_audio_control_get

Pobierz określoną kontrolkę z interfejsu sterowania audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje określoną kontrolkę z interfejsu sterowania audio.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia klasy audio
- **audio_control:** Wskaźnik do struktury sterowania dźwiękami

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED:** funkcja (0x54) nie jest obsługiwana
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interfejs jest nieprawidłowy

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

Ustaw określoną kontrolkę na interfejs sterowania audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

**Opis **

Ta funkcja ustawia określoną kontrolkę na interfejs sterowania audio.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia klasy audio
- **audio_control:** Wskaźnik do struktury sterowania dźwiękami

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED:** funkcja (0x54) nie jest obsługiwana
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interfejs jest nieprawidłowy

### <a name="example"></a>Przykład

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

Ustaw interfejs ustawień alternatywnych interfejsu przesyłania strumieniowego audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>Opis

Ta funkcja ustawia odpowiedni alternatywny interfejs ustawień interfejsu przesyłania strumieniowego audio zgodnie z określoną strukturą próbkowania.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia klasy audio.
- **audio_sampling:** Wskaźnik do struktury próbkowania audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED:** funkcja (0x54) nie jest obsługiwana
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interfejs jest nieprawidłowy
- **UX_NO_ALTERNATE_SETTING:**(0x5e) Brak alternatywnego ustawienia dla wartości próbkowania

### <a name="example"></a>Przykład

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

Pobieranie możliwych ustawień próbkowania interfejsu przesyłania strumieniowego audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>Opis

Ta funkcja pobiera po jednym po sobie wszystkie możliwe ustawienia próbkowania dostępne w każdym z alternatywnych ustawień interfejsu przesyłania strumieniowego audio. Gdy funkcja jest używana po raz pierwszy, należy zresetować wszystkie pola we wskaźniku wywołującej struktury. Funkcja zwróci określony zestaw wartości przesyłania strumieniowego po zwróceniu, chyba że zostanie osiągnięty koniec alternatywnych ustawień. Gdy ta funkcja zostanie ponownie użyta, poprzednie wartości próbkowania zostaną użyte do znalezienia następnych wartości próbkowania.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia klasy audio.
- **audio_sampling:** Wskaźnik do struktury próbkowania audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED:** funkcja (0x54) nie jest obsługiwana
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE:**(0x81) Interfejs jest nieprawidłowy
- **UX_NO_ALTERNATE_SETTING:**(0x5e) Brak alternatywnego ustawienia dla wartości próbkowania

### <a name="example"></a>Przykład

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

Odczyt z interfejsu asix.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje z interfejsu asix. Wywołanie jest blokowane i zwracane tylko wtedy, gdy wystąpi błąd lub gdy transfer zostanie ukończony.

### <a name="parameters"></a>Parametry

- **asix:** wskaźnik do wystąpienia klasy asix.
- **data_pointer:** Wskaźnik do adresu buforu ładunku danych.
- **requested_length:** długość do odebrania.
- **actual_length:** odebrana długość.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Limit czasu transferu, odczytywanie niekompletne.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

Zapisz w interfejsie asix.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>Opis

Ta funkcja zapisuje w interfejsie asix. Wywołanie nie jest blokujące.

### <a name="parameters"></a>Parametry

- **asix:** wskaźnik do wystąpienia klasy asix.
- **pakiet**: pakiet danych Netx

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_ERROR:**(0xFF) Nie można zażądać transferu.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

Otwórz sesję między inicjatorem i responderem.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Opis

Ta funkcja otwiera sesję między inicjatorem PIMA i responderem PIMA. Po pomyślnym otwarciu sesji można wykonać większość poleceń PIMA.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima.
- **pima_sessio:** Wskaźnik do sesji PIMA<

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Sesja została pomyślnie otwarta
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED:**(0x201E) Sesja jest już otwarta

### <a name="example"></a>Przykład

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

Zamknij sesję między inicjatorem i responderem.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Opis

Ta funkcja zamyka sesję, która została wcześniej otwarta między inicjatorem PIMA i responderem PIMA. Po zamknięciu sesji większość poleceń PIMA nie może być już wykonywana.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Sesja została zamknięta.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta.

### <a name="example"></a>Przykład

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

Uzyskaj tablicę identyfikatorów magazynu z obiektów odpowiadających.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje tablicę identyfikatorów magazynu od responder.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA
- **storage_ids_array:** tablica, w której będą zwracane identyfikatory magazynu
- **storage_id_length:** długość tablicy magazynowej

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Tablica identyfikatorów magazynu została wypełniona
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

Uzyskaj informacje o magazynie z responder.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje informacje o magazynie dla kontenera magazynu o wartości *storage_id*.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA
- **storage_id:** identyfikator kontenera magazynu
- **storage:** wskaźnik do kontenera informacji o magazynie

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Pobrano informacje o magazynie
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_MEMORY_INSUFFICIENT** (0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a>ux_host_class_pima_num_objects_get

Uzyskaj liczbę obiektów w kontenerze magazynu z obiektu odpowiada.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje liczbę obiektów przechowywanych w określonym kontenerze magazynu o wartości storage_id zgodnym z kodem określonego formatu. Liczba obiektów jest zwracana w polu : ux_host_class_pima_session_nb_objects struktury pima_session danych.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA
- **storage_id:** identyfikator kontenera magazynu
- **object_format_code:** Obiekty formatuje filtr kodu.

Kod formatu obiektu może mieć jedną z następujących wartości.

| Kod formatu obiektu               | Opis   |     Kod USBX                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | Niezdefiniowany niezdefiniowany obiekt niebędący obrazem | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | Skojarzenie (np. folder) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | Skrypt skryptu specyficznego dla modelu urządzenia | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | Wykonywalny plik wykonywalny specyficzny dla modelu urządzenia | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | Plik tekstowy  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | Plik HTML języka znaczników hypertext (tekst) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | Plik formatu zamówienia drukowania cyfrowego DPOF (tekst) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | Klip dźwiękowy AIFF  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | Klip dźwiękowy WAV   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | Klip audio MP3   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | KLIP WIDEO AVI   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | KLIP WIDEO MPEG  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | Zaawansowany format przesyłania strumieniowego USŁUGI ASF firmy Microsoft (wideo) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | Niezdefiniowany nieznany obiekt obrazu | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | Format pliku wymiany EXIF/JPEG, standard JEIDA | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | Format pliku obrazu tagu TIFF/EP dla elektronicznej firmy | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | Format obrazu Storage Flash Pixel | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | Plik mapy bitowej Windows Microsoft BMP | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | Format pliku obrazu aparatu CIFF Canon | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | Niezdefiniowane zarezerwowane |  |
| 0x3807                           | GIF Graphics Interchange Format | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | Format wymiany pliku JPEG JFIF | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PCD PhotoCD Image Pac | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | Format obrazu quickdraw PICT | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | PNG Portable Network Graphics | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | Niezdefiniowane zarezerwowane |   |
| 0x380D                           | TIFF Tag Image File Format | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | Format pliku obrazu tagu TIFF/IT dla technologii informatycznych (grafika) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | Format pliku odniesienia JPEG2000 JP2 | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | Rozszerzony format pliku JPEG2000 JPX | UX_HOST_CLASS_PIMA_OFC_JPX         |
| Wszystkie inne kody z msn 0011 | Wszelkie niezdefiniowane zarezerwowane do użytku w przyszłości |                                    |
| Wszystkie inne kody z msn 1011 | Dowolny typ zdefiniowany przez dostawcę: Obraz |                                    |

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a>ux_host_class_pima_object_handles_get

Uzyskaj dojścia obiektu z obiektu odpowiada.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a>Opis

Zwraca tablicę dojść obiektu obecnych w kontenerze magazynu wskazywanym przez storage_id parametr. Jeśli zagregowana lista wszystkich sklepów jest pożądana, ta wartość musi być ustawiona na 0xFFFFFFFF.

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA
- **object_handes_array:** tablica, w której zwracane są dojścia
- **object_handles_length:** długość tablicy
- **storage_id:** identyfikator kontenera magazynu
- **object_format_code:** formatowanie kodu dla obiektu (zobacz tabelę dla funkcji ux_host_class_pima_num_objects_get)
- **object_handle_association:** Opcjonalna wartość skojarzenia obiektu

Skojarzenie dojścia obiektu może być jedną z wartości z poniższej tabeli:

| AssociationCode                        | Associationtype      | Interpretacja       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | Niezdefiniowane            | Niezdefiniowane            |
| 0x0001                                 | GenericFolder        | Nieużywane               |
| 0x0002                                 | Album                | Zarezerwowany             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | Nieużywane               |
| 0x0005                                 | VerticalPanoramic    | Nieużywane               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | Dane pomocnicze        | Niezdefiniowane            |
| Wszystkie inne wartości z bitem 15 ustawionym na 0  | Zarezerwowany             | Niezdefiniowane            |
| Wszystkie wartości z bitem 15 ustawionym na 1        | Zdefiniowane przez dostawcę       | Zdefiniowane przez dostawcę       |

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

Uzyskaj informacje o obiekcie z obiektu odpowiada.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje informacje o obiekcie dla dojścia obiektu.

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA
- **object_handle:** Dojście obiektu
- **object**: Wskaźnik do kontenera informacji o obiekcie

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

Wyślij informacje o obiekcie do obiektu odpowiada.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Opis

Ta funkcja wysyła informacje o magazynie dla kontenera magazynu o wartości storage_id. Inicjator powinien użyć tego polecenia przed wysłaniem obiektu do obiektu reagującego.

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA.
- **storage_id:** identyfikator magazynu docelowego.
- **parent_object_id:** Parent ObjectHandle on Responder where object should be placed (Obiekt nadrzędny ObjectHandle w obiekcie odpowiedzi, w którym należy umieścić obiekt).
- **object**: Wskaźnik do kontenera informacji o obiekcie.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a>ux_host_class_pima_object_open

Otwórz obiekt przechowywany w obiekcie odpowiadającym.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Opis

Ta funkcja otwiera obiekt obiektu obiektu odpowiada przed odczytem lub zapisem.

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA.
- **object_handle:** uchwyt obiektu.
- **objec:** wskaźnik do kontenera informacji o obiekcie.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED:**(0x2021) Obiekt jest już otwarty.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

Pobierz obiekt przechowywany w obiekcie odpowiadającym.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a>Opis

Ta funkcja pobiera obiekt na obiekt odpowiedzi.

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA
- **object_handle:** dojście obiektu
- **object**: Wskaźnik do kontenera informacji o obiekcie
- **object_buffer:** Adres danych obiektu
- **object_buffer_length:** żądana długość obiektu
- **object_actual_length:** Długość zwracanego obiektu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Obiekt został przeniesiony
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED:**(0x2023) Obiekt nie jest otwarty.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED:**(0x200f) Odmowa dostępu do obiektu
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) Transfer jest niekompletny
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.
- **UX_TRANSFER_ERROR:**(0x23) Błąd transferu podczas odczytywania obiektu

### <a name="example"></a>Przykład

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a>ux_host_class_pima_object_send

Wyślij obiekt przechowywany w obiekcie odpowiadającym.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a>Opis

Ta funkcja wysyła obiekt do obiektu odpowiada.

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_sessio:** Wskaźnik do sesji PIMA
- **object_handle:** dojście obiektu
- **object**: Wskaźnik do kontenera informacji o obiekcie
- **object_buffer:** Adres danych obiektu
- **object_buffer_length:** żądana długość obiektu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED:**(0x2023) Obiekt nie jest otwarty.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED:**(0x200f) Odmowa dostępu do obiektu
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) Transfer jest niekompletny
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.
- **UX_TRANSFER_ERROR:**(0x23) Błąd transferu podczas pisania obiektu

### <a name="example"></a>Przykład

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

Pobierz obiekt kciuka przechowywany w obiekcie odpowiadającym.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a>Opis

Ta funkcja pobiera obiekt kciuka w obiekcie odpowiadającym.

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA.
- **object_handle:** uchwyt obiektu.
- **object**: Wskaźnik do kontenera informacji o obiekcie.
- **thumb_buffer:** adres danych obiektu miniatury.
- **thumb_buffer_length:** żądana długość obiektu miniatury.
- **thumb_actual_length:** długość zwróconego obiektu kciuka.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED:**(0x2023) Obiekt nie jest otwarty.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED:**(0x200f) Odmowa dostępu do obiektu.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER:**(0x2007) Transfer jest niekompletny.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.
- **UX_TRANSFER_ERROR:**(0x23) Błąd transferu podczas odczytywania obiektu.

### <a name="example"></a>Przykład

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

Usuń obiekt przechowywany w obiekcie odpowiadającym.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a>Opis

Ta funkcja usuwa obiekt w obiekcie odpowiadającym

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA
- **object_handle:** dojście obiektu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Obiekt został usunięty.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED:**(0x200f) Nie można usunąć obiektu.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

Zamykanie obiektu przechowywanego w obiekcie odpowiadającym

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Opis

Ta funkcja zamyka obiekt w obiekcie odpowiadającym.

### <a name="parameters"></a>Parametry

- **pima:** wskaźnik do wystąpienia klasy pima.
- **pima_session:** Wskaźnik do sesji PIMA.
- **object_handle:** Uchwyt obiektu.
- **object**: Wskaźnik do obiektu.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Obiekt został zamknięty.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN:**(0x2003) Sesja nie jest otwarta.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED:**(0x2023) Obiekt nie jest otwarty.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci, aby utworzyć polecenie PIMA.

### <a name="example"></a>Przykład

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

Odczyt z ogólnego interfejsu szeregowego.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje z ogólnego interfejsu szeregowego. Wywołanie jest blokujące i zwracane tylko wtedy, gdy wystąpi błąd lub gdy transfer zostanie ukończony.

### <a name="parameters"></a>Parametry

- **gser:** wskaźnik do wystąpienia klasy gser.
- **interface_index:** Indeks interfejsu do odczytu.
- **data_pointer:** wskaźnik do adresu buforu ładunku danych.
- **requested_length:** długość do odebrania.
- **actual_length:** długość rzeczywiście odebranych.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Limit czasu transferu, odczytywanie niekompletne.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

Zapis w ogólnym interfejsie szeregowym.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja zapisuje w ogólnym interfejsie szeregowym. Wywołanie jest blokujące i zwracane tylko wtedy, gdy wystąpi błąd lub gdy transfer zostanie ukończony.

### <a name="parameters"></a>Parametry

- **gser:** wskaźnik do wystąpienia klasy gser.
- **interface_index:** interfejs, w którym ma być zapisywany.
- **data_pointer:** wskaźnik do adresu buforu ładunku danych.
- **requested_length:** długość do wysłania.
- **actual_length:** długość rzeczywiście wysłana.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Transfer danych został ukończony.
- **UX_TRANSFER_TIMEOUT:**(0x5c) Limit czasu transferu, zapis jest niekompletny.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a>ux_host_class_gser_ioctl

Wykonaj funkcję IOCTL do ogólnego interfejsu szeregowego.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a>Opis

Ta funkcja wykonuje określoną funkcję ioctl w interfejsie gser. Wywołanie jest blokujące i zwracane tylko wtedy, gdy wystąpi błąd lub gdy polecenie zostanie zakończone.

### <a name="parameters"></a>Parametry

- **gser:** wskaźnik do wystąpienia klasy gser.
- **ioctl_function:** funkcja ioctl do wykonania. W poniższej tabeli przedstawiono jedną z dozwolonych funkcji ioctl.
- **parametr**: Wskaźnik do parametru specyficznego dla ioctl

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS:**(0x00) Ukończono transfer danych.
- **UX_MEMORY_INSUFFICIENT:**(0x12) Za mało pamięci.
- **UX_HOST_CLASS_UNKNOWN:**(0x59) Nieprawidłowe wystąpienie klasy
- **UX_FUNCTION_NOT_SUPPORTED:**(0x54) Unknown IOCTL, funkcja.

### <a name="ioctl-functions"></a>Funkcje IOCTL

- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK
- UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a>ux_host_class_gser_reception_start

Uruchamianie odbioru w ogólnym interfejsie szeregowym

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Opis

Ta funkcja uruchamia sygnał w interfejsie ogólnej klasy szeregowej. Ta funkcja umożliwia nieblokowanie odbioru. Po otrzymaniu buforu wywołanie zwrotne w wywołaniu do aplikacji.

### <a name="parameters"></a>Parametry

- **gser** Wskaźnik do wystąpienia klasy gser.
- **gser_reception** Struktura zawierająca parametry odbioru

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_UNKNOWN** (0x59) Nieprawidłowe wystąpienie klasy
- **błąd UX_ERROR** (0x01)

### <a name="example"></a>Przykład

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a>ux_host_class_gser_reception_stop

Zatrzymywanie odbioru w ogólnym interfejsie szeregowym

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Opis

Ta funkcja zatrzymuje sygnał w interfejsie ogólnej klasy szeregowej.

### <a name="parameters"></a>Parametry

- **gser** Wskaźnik do wystąpienia klasy gser.
- **gser_reception** Struktura zawierająca parametry odbioru

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Transfer danych został ukończony.
- **UX_HOST_CLASS_UNKNOWN** (0x59) Nieprawidłowe wystąpienie klasy
- **błąd UX_ERROR** (0x01)

### <a name="example"></a>Przykład

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
