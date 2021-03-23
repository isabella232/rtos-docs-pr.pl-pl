---
title: Interfejs API klas hosta USBX
description: W tym rozdziale opisano wszystkie uwidocznione interfejsy API klas hosta USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39f3a71c28dd14e0093f72d1a3b1ff6837c6f1f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824018"
---
# <a name="chapter-2-usbx-host-classes-api"></a>Rozdział 2: interfejs API klas hosta USBX

W tym rozdziale opisano wszystkie uwidocznione interfejsy API klas hosta USBX. Poniższe interfejsy API dla każdej klasy są szczegółowo opisane.

- Klasa drukarki
- Klasa audio
- Klasa ASIX
- Pima/PTP — Klasa
- Klasa mnóstwo
- Ogólna Klasa szeregowa

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

Odczytaj z interfejsu drukarki.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje z interfejsu drukarki. Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu. Odczyt jest dozwolony tylko na drukarkach dwukierunkowych.

### <a name="parameters"></a>Parametry

- **drukarka**: wskaźnik do wystąpienia klasy drukarki.
- **data_pointer**: wskaźnik na adres buforu ładunku danych.
- **requested_length**: długość do odebrania.
- **actual_length**: długość rzeczywiście odebrana.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana, ponieważ drukarka nie jest dwukierunkowa.
- **UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, odczytywanie niekompletne.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

Zapisz w interfejsie drukarki.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja zapisuje w interfejsie drukarki. Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.

### <a name="parameters"></a>Parametry

- **drukarka**: wskaźnik do wystąpienia klasy drukarki.
- **data_pointer**: wskaźnik na adres buforu ładunku danych.
- **requested_length**: długość do wysłania.
- **actual_length**: długość faktycznie wysłana.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_TRANSFER_TIMEOUT**: (0x5c) limit czasu transferu, zapisywanie niekompletne.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

Wykonaj resetowanie miękkie do drukarki.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>Opis

Ta funkcja wykonuje funkcję resetowania miękkiego do drukarki.

### <a name="input-parameter"></a>Parametr wejściowy

- **drukarka**: wskaźnik do wystąpienia klasy drukarki.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) Resetowanie zostało zakończone.
- **UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, Resetowanie nie zostało ukończone.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

Pobierz stan drukarki

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje stan drukarki. Stan drukarki jest podobny do stanu LPT (1284 standard).

### <a name="parameters"></a>Parametry

- **drukarka**: wskaźnik do wystąpienia klasy drukarki.
- **printer_status**: adres, który ma zostać zwrócony.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00): Resetowanie zostało zakończone.
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci do wykonania operacji.
- **UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, Resetowanie nie zostało ukończone

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

Ta funkcja uzyskuje ciąg identyfikatora urządzenia IEEE 1284 (łącznie z długością w pierwszych dwóch bajtach w formacie big endian).

### <a name="parameters"></a>Parametry

- **drukarka**: wskaźnik do wystąpienia klasy drukarki.
- **descriptor_buffer**: wskaźnik do buforu, aby wypełnić ciąg identyfikatora urządzenia IEEE 1284 (łącznie z długością w ciągu pierwszych dwóch bajtów w formacie) 
- **Długość**: długość buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00): operacja zakończyła się pomyślnie.
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci do wykonania operacji.
- **UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, żądanie nie zostało ukończone
- **UX_TRANSFER_NOT_READY**: (0x25) urządzenie było w nieprawidłowym stanie — musi być dołączone, rozkierowane lub skonfigurowane.
- **UX_TRANSFER_STALL**: (0x21) zatrzymano transfer.
- Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- **TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik zliczania semafora.
- **TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

Odczytaj z interfejsu audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje z interfejsu audio. Wywołanie nie jest blokowane. Aplikacja musi upewnić się, że dla interfejsu audio streaming została wybrana opcja alternatywnego ustawienia.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia klasy audio.
- **audio_transfer_request**: wskaźnik do struktury transferu audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony
- Funkcja **UX_FUNCTION_NOT_SUPPORTED**"(0x54) nie jest obsługiwana

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

Zapisz w interfejsie audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>Opis

Ta funkcja zapisuje dane w interfejsie audio. Wywołanie nie jest blokowane. Aplikacja musi upewnić się, że dla interfejsu audio streaming została wybrana opcja alternatywnego ustawienia.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia klasy audio
- **audio_transfer_request**: wskaźnik do struktury transferu audio

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana.
- **ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Nieprawidłowy interfejs.

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

Uzyskaj konkretną kontrolę z interfejsu sterowania dźwiękiem.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje konkretną kontrolę z interfejsu sterowania dźwiękiem.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia klasy audio
- **audio_control**: wskaźnik do struktury kontrolki audio

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — Nieprawidłowy interfejs

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

Ustaw konkretną kontrolę interfejsu sterowania dźwiękiem.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

* * Description * *

Ta funkcja ustawia konkretną kontrolę interfejsu sterowania dźwiękiem.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia klasy audio
- **audio_control**: wskaźnik do struktury kontrolki audio

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — Nieprawidłowy interfejs

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

Ustaw alternatywny interfejs ustawień interfejsu audio streaming.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>Opis

Ta funkcja ustawia odpowiedni interfejs ustawienia alternatywnego interfejsu audio streaming zgodnie z określoną strukturą próbkowania.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia klasy audio.
- **audio_sampling**: wskaźnik do struktury próbkowania audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — Nieprawidłowy interfejs
- **UX_NO_ALTERNATE_SETTING**: (0X5e) brak alternatywnego ustawienia dla wartości próbkowania

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

Pobierz możliwe ustawienia próbkowania interfejsu audio streaming.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>Opis

Ta funkcja pobiera jedną z nich, wszystkie możliwe ustawienia próbkowania dostępne w każdym z ustawień alternatywnych interfejsu audio streaming. Przy pierwszym użyciu funkcji, należy zresetować wszystkie pola wskaźnika struktury wywołującej. Funkcja zwróci określony zestaw wartości przesyłania strumieniowego po zwrocie, chyba że zostanie osiągnięty koniec ustawień alternatywnych. Gdy ta funkcja jest ponownie używana, poprzednie wartości próbkowania będą używane do znajdowania następnych wartości próbkowania.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia klasy audio.
- **audio_sampling**: wskaźnik do struktury próbkowania audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony
- **UX_FUNCTION_NOT_SUPPORTED**: (0X54) funkcja nie jest obsługiwana
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — Nieprawidłowy interfejs
- **UX_NO_ALTERNATE_SETTING**: (0X5e) brak alternatywnego ustawienia dla wartości próbkowania

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

Odczytaj z interfejsu ASIX.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja odczytuje z interfejsu ASIX. Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.

### <a name="parameters"></a>Parametry

- **ASIX**: wskaźnik do wystąpienia klasy ASIX.
- **data_pointer**: wskaźnik na adres buforu ładunku danych.
- **requested_length**: długość do odebrania.
- **actual_length**: długość rzeczywiście odebrana.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, odczytywanie niekompletne.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

Zapisz w interfejsie ASIX.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>Opis

Ta funkcja zapisuje w interfejsie ASIX. Wywołanie nie blokuje się.

### <a name="parameters"></a>Parametry

- **ASIX**: wskaźnik do wystąpienia klasy ASIX.
- **pakiet**: pakiet danych NetX

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_ERROR**: (0xFF) nie można zażądać przeniesienia.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

Otwórz sesję między inicjatorem a obiektem odpowiadającym.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Opis

Ta funkcja otwiera sesję między inicjatorem PIMA a obiektem odpowiadającym PIMA. Po pomyślnym otwarciu sesji można wykonać większość poleceń PIMA.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_sessio**: wskaźnik do sesji Pima<

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) pomyślnie otwarto sesję
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0X201E) sesja została już otwarta

### <a name="example"></a>Przykład

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

Zamknij sesję między inicjatorem a obiektem odpowiadającym.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Opis

Ta funkcja zamyka sesję, która została wcześniej otwarta między inicjatorem PIMA a obiektem odpowiadającym PIMA. Po zamknięciu sesji większość poleceń PIMA nie można już wykonywać.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) sesja została zamknięta.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: nie otwarto sesji (0x2003).

### <a name="example"></a>Przykład

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

Uzyskaj tablicę identyfikatorów magazynu od obiektu odpowiadającego.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje tablicę identyfikatorów magazynu od obiektu odpowiadającego.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima
- **storage_ids_array**: tablica, w której zostaną zwrócone identyfikatory magazynu
- **storage_id_length**: długość tablicy magazynowej

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) tablica identyfikatorów magazynu została wypełniona
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.

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

Uzyskaj informacje o magazynie z obiektu odpowiadającego.

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

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima
- **storage_id**: Identyfikator kontenera magazynu
- **Magazyn**: wskaźnik do kontenera informacji o magazynie

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) informacje o magazynie zostały pobrane
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- **UX_MEMORY_INSUFFICIENT** (0x12) za mało pamięci, aby utworzyć polecenie Pima.

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

Uzyskaj liczbę obiektów w kontenerze magazynu od obiektu odpowiadającego.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje liczbę obiektów przechowywanych w określonym kontenerze magazynu o wartości storage_id pasujących do określonego kodu formatu. W polu jest zwracana liczba obiektów: ux_host_class_pima_session_nb_objects struktury pima_session.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima
- **storage_id**: Identyfikator kontenera magazynu
- **object_format_code**: obiekty formatują filtr kodu.

Kody formatu obiektów mogą mieć jedną z następujących wartości.

| Kod formatu obiektu               | Opis   |     Kod USBX                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | Niezdefiniowany niezdefiniowany obiekt niebędący obrazem | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | Skojarzenie skojarzenia (np. folder) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | Skrypt specyficzny dla modelu urządzenia | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | Plik wykonywalny specyficzny dla modelu urządzenia | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | Plik tekstowy tekstu  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | Plik HTML HyperText Markup Language (tekst) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | Plik formatu porządkowania cyfrowych DPOF (tekst) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | Klip audio AIFF  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | Klip audio WAV   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | Klip audio MP3   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | Klip wideo AVI   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | Klip wideo MPEG  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | Microsoft Advanced Streaming format (wideo) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | Niezdefiniowany nieznany obiekt obrazu | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | Format pliku EXIF/JPEG z wymianą, JEIDA Standard | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | Format pliku obrazu znacznika TIFF/EP dla fotografii elektronicznych | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | Format obrazu magazynu strukturalnego FlashPix | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | BMP plik mapy bitowej systemu Microsoft Windows | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | Format pliku obrazu aparatu CIFF firmy Canon | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | Niezdefiniowane zarezerwowane |  |
| 0x3807                           | Graphics Interchange Format GIF | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | Format wymiany plików w formacie JFIF | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PCD PhotoCD Image PAC | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | Format obrazu PICT QUICKDRAW | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | Portable Network Graphics PNG | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | Niezdefiniowane zarezerwowane |   |
| 0x380D                           | Format pliku obrazu znacznika TIFF | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | Format TIFF/tag obrazu dla technologii informatycznych (grafiki sztuki) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | Format pliku bazowego JP2 JPEG2000 | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | Rozszerzony format pliku JPX JPEG2000 | UX_HOST_CLASS_PIMA_OFC_JPX         |
| Wszystkie inne kody z usługą MSN of 0011 | Wszystkie niezdefiniowane zarezerwowane do użytku w przyszłości |                                    |
| Wszystkie inne kody z usługą MSN of 1011 | Dowolny zdefiniowany przez dostawcę typ zdefiniowany przez dostawcę: obraz |                                    |

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.

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

Uzyskaj uchwyty obiektów z obiektu odpowiadającego.

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

Zwraca tablicę dojść do obiektów znajdujących się w kontenerze magazynu wskazanym przez parametr storage_id. Jeśli wymagana jest lista zagregowana we wszystkich sklepach, ta wartość jest ustawiana na 0xFFFFFFFF.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima
- **object_handes_array**: zwrócono tablicę, w której są dojścia
- **object_handles_length**: długość tablicy
- **storage_id**: Identyfikator kontenera magazynu
- **object_format_code**: Formatuj kod dla obiektu (patrz tabela dla funkcji ux_host_class_pima_num_objects_get)
- **object_handle_association**: opcjonalna wartość skojarzenia obiektu

Skojarzenie uchwytu obiektu może być jedną z wartości z poniższej tabeli:

| AssociationCode                        | Obiekt AssociationType      | Interpretacja       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | Niezdefiniowane            | Niezdefiniowane            |
| 0x0001                                 | GenericFolder        | Nieużywane               |
| 0x0002                                 | Albumu                | Zarezerwowany             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | Nieużywane               |
| 0x0005                                 | VerticalPanoramic    | Nieużywane               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | AncillaryData        | Niezdefiniowane            |
| Wszystkie inne wartości z bit 15 ustawione na 0  | Zarezerwowany             | Niezdefiniowane            |
| Wszystkie wartości z bit 15 ustawiony na 1        | Zdefiniowany przez dostawcę       | Zdefiniowany przez dostawcę       |

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.

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

Uzyskaj informacje o obiekcie z obiektu odpowiadającego.

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Opis

Ta funkcja uzyskuje informacje o obiekcie dla uchwytu obiektu.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima
- **object_handle**: uchwyt obiektu
- **Object**: wskaźnik do kontenera informacji o obiekcie

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.

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

Wyślij informacje o obiekcie do obiektu odpowiadającego.

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

Ta funkcja wysyła informacje o magazynie dla kontenera magazynu o wartości storage_id. Inicjator powinien użyć tego polecenia przed wysłaniem obiektu do obiektu odpowiadającego.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima.
- **storage_id**: docelowy identyfikator magazynu.
- **parent_object_id**: element nadrzędny ObjectHandle na obiekcie odpowiadającym, na którym ma zostać umieszczony obiekt.
- **Object**: wskaźnik do kontenera informacji o obiekcie.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.

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

Ta funkcja otwiera obiekt obiektu odpowiadającego przed odczytem lub zapisem.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima.
- **object_handle**: uchwyt obiektu.
- **objec**: wskaźnik do kontenera informacji o obiekcie.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- Obiekt **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) jest już otwarty.
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.

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

Ta funkcja pobiera obiekt obiektu odpowiadającego.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima
- **object_handle**: uchwyt obiektu
- **Object**: wskaźnik do kontenera informacji o obiekcie
- **object_buffer**: adres danych obiektu
- **object_buffer_length**: Żądana długość obiektu
- **object_actual_length**: długość zwróconego obiektu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) obiekt został przeniesiony
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- Nie otwarto obiektu **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023).
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) dostęp do obiektu odmowa
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) transfer jest niekompletny
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.
- **UX_TRANSFER_ERROR**: błąd transferu (0x23) podczas odczytywania obiektu

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

Ta funkcja wysyła obiekt do obiektu odpowiadającego.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_sessio**: wskaźnik do sesji Pima
- **object_handle**: uchwyt obiektu
- **Object**: wskaźnik do kontenera informacji o obiekcie
- **object_buffer**: adres danych obiektu
- **object_buffer_length**: Żądana długość obiektu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) nie otwarto sesji
- Nie otwarto obiektu **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023).
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) dostęp do obiektu odmowa
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) transfer jest niekompletny
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.
- **UX_TRANSFER_ERROR**: (0x23) błąd transferu podczas zapisywania obiektu

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

Ta funkcja pobiera obiekt kciuka na obiekt odpowiadający.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima.
- **object_handle**: uchwyt obiektu.
- **Object**: wskaźnik do kontenera informacji o obiekcie.
- **thumb_buffer**: adres danych obiektu kciuka.
- **thumb_buffer_length**: Żądana długość obiektu kciuka.
- **thumb_actual_length**: długość zwróconego obiektu kciuka.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: nie otwarto sesji (0x2003).
- Nie otwarto obiektu **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023).
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) dostęp do obiektu odmowa.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0X2007) transfer jest niekompletny.
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.
- **UX_TRANSFER_ERROR**: (0x23) błąd transferu podczas odczytywania obiektu.

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

Ta funkcja usuwa obiekt obiektu odpowiadającego

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima
- **object_handle**: uchwyt obiektu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) obiekt został usunięty.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: nie otwarto sesji (0x2003).
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) nie można usunąć obiektu.
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.

### <a name="example"></a>Przykład

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

Zamknij obiekt przechowywany w obiekcie odpowiadającym

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Opis

Ta funkcja zamyka obiekt obiektu odpowiadającego.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **pima_session**: wskaźnik do sesji Pima.
- **object_handle**: uchwyt obiektu.
- **Object**: wskaźnik do obiektu.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) obiekt został zamknięty.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: nie otwarto sesji (0x2003).
- Nie otwarto obiektu **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023).
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci, aby utworzyć polecenie Pima.

### <a name="example"></a>Przykład

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

Odczytaj z ogólnego interfejsu szeregowego.

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

Ta funkcja odczytuje z ogólnego interfejsu szeregowego. Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.

### <a name="parameters"></a>Parametry

- **gser**: wskaźnik do wystąpienia klasy gser.
- **interface_index**: indeks interfejsu, z którego ma zostać odczytany.
- **data_pointer**: wskaźnik na adres buforu ładunku danych.
- **requested_length**: długość do odebrania.
- **actual_length**: długość rzeczywiście odebrana.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_TRANSFER_TIMEOUT**: (0x5c) upłynął limit czasu transferu, odczytywanie niekompletne.

### <a name="example"></a>Przykład

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

Zapisz w ogólnym interfejsie szeregowym.

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

Ta funkcja zapisuje do ogólnego interfejsu szeregowego. Wywołanie jest blokowane i zwraca tylko wtedy, gdy wystąpi błąd lub po zakończeniu transferu.

### <a name="parameters"></a>Parametry

- **gser**: wskaźnik do wystąpienia klasy gser.
- **interface_index**: interfejs, który ma zostać zapisany.
- **data_pointer**: wskaźnik na adres buforu ładunku danych.
- **requested_length**: długość do wysłania.
- **actual_length**: długość faktycznie wysłana.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_TRANSFER_TIMEOUT**: (0x5c) limit czasu transferu, zapisywanie niekompletne.

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

Ta funkcja wykonuje konkretną funkcję IOCTL do interfejsu gser. Wywołanie jest blokowane i zwraca tylko wtedy, gdy występuje błąd lub po zakończeniu polecenia.

### <a name="parameters"></a>Parametry

- **gser**: wskaźnik do wystąpienia klasy gser.
- **ioctl_function**: funkcja IOCTL, która ma zostać wykonana. W poniższej tabeli znajduje się jedna z dozwolonych funkcji IOCTL.
- **parametr**: Pointerto parametr specyficzny dla elementu IOCTL

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0x00) transfer danych został ukończony.
- **UX_MEMORY_INSUFFICIENT**: (0x12) za mało pamięci.
- **UX_HOST_CLASS_UNKNOWN**: (0X59) złe wystąpienie klasy
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) nieznana funkcja IOCTL.

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

Rozpocznij odbieranie w ogólnym interfejsie szeregowym

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Opis

Ta funkcja uruchamia odbieranie w interfejsie klasy uniwersalnej. Ta funkcja umożliwia odbiór nieblokujący. Po odebraniu buforu wywołanie zwrotne jest wywoływane do aplikacji.

### <a name="parameters"></a>Parametry

- **gser** Wskaźnik do wystąpienia klasy gser.
- **gser_reception** Struktura zawierająca parametry odbioru

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_UNKNOWN** (0X59) złe wystąpienie klasy
- Błąd **UX_ERROR** (0x01)

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

Zatrzymaj odbieranie w ogólnym interfejsie szeregowym

### <a name="prototype"></a>Prototype

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Opis

Ta funkcja przerywa odbieranie w interfejsie uniwersalnej klasy szeregowej.

### <a name="parameters"></a>Parametry

- **gser** Wskaźnik do wystąpienia klasy gser.
- **gser_reception** Struktura zawierająca parametry odbioru

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) transfer danych został ukończony.
- **UX_HOST_CLASS_UNKNOWN** (0X59) złe wystąpienie klasy
- Błąd **UX_ERROR** (0x01)

### <a name="example"></a>Przykład

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
