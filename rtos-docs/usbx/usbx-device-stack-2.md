---
title: Rozdział 2 — Azure RTOS instalacji stosu urządzenia USBX
description: Dowiedz się, jak zainstalować Azure RTOS urządzenia USBX, a także ważne zagadnienia dotyczące hosta, które należy wziąć pod uwagę przed zainstalowaniem.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: abe3e43e090890a5e51700fc2f587c59619fcdad5b71681fd4071c614dab5ce6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791412"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a>Rozdział 2 — Azure RTOS instalacji stosu urządzenia USBX

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

### <a name="computer-type"></a>Typ komputera

Tworzenie aplikacji osadzonych odbywa się zwykle na komputerach Windows komputerach stacjonarnych lub komputerach hostów z systemem Unix. Gdy aplikacja zostanie skompilowana, połączona i zlokalizowana na hoście, zostanie pobrana na docelowy sprzęt w celu wykonania.

### <a name="download-interfaces"></a>Interfejsy pobierania

Zazwyczaj docelowy pobieranie odbywa się za pośrednictwem interfejsu szeregowego RS-232, chociaż interfejsy równoległe, USB i Ethernet stają się bardziej popularne. Aby uzyskać dostępne opcje, zobacz dokumentację narzędzia dewelopera.

### <a name="debugging-tools"></a>Narzędzia debugowania

Debugowanie odbywa się zwykle za pośrednictwem tego samego linku co pobieranie obrazu programu. Istnieje wiele debugerów, od małych programów monitorów uruchomionych w docelowym środowisku za pośrednictwem monitora debugowania w tle (BDM) i In-Circuit Emulator (ICE). Narzędzie ICE zapewnia najbardziej niezawodne debugowanie rzeczywistego docelowego sprzętu.

### <a name="required-hard-disk-space"></a>Wymagane miejsce na dysku twardym

Kod źródłowy USBX jest dostarczany w formacie ASCII i wymaga około 500 KB miejsca na dysku twardym komputera hosta.

### <a name="target-considerations"></a>Zagadnienia dotyczące celu

UsbX wymaga od 24 KB do 64 KB pamięci tylko do odczytu (ROM) na docelowym w trybie hosta. Ilość wymaganej pamięci zależy od typu używanego kontrolera i klas USB połączonych z USBX. Kolejne 32 KB pamięci RAM (Random Access Memory) obiektu docelowego są wymagane dla globalnych struktur danych USBX i puli pamięci. Tę pulę pamięci można również dostosować w zależności od oczekiwanej liczby urządzeń na dysku USB i typu kontrolera USB. Strona urządzenia USBX wymaga około 10–12 K pamięci ROM w zależności od typu kontrolera urządzenia. Użycie pamięci RAM zależy od typu klasy emulowanej przez urządzenie.

UsbX opiera się również na semaforach ThreadX, mutexach i wątkach w celu ochrony wielu wątków oraz zawieszania we/wy i okresowego przetwarzania w celu monitorowania topologii magistrali USB.

### <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS USBX można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie <https://github.com/azure-rtos/usbx/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium.

* ***ux_api.h:*** ten plik nagłówkowy języka C zawiera wszystkie elementy systemowe, struktury danych i prototypy usług.
* ***ux_port.h:*** ten plik nagłówkowy języka C zawiera wszystkie definicje i struktury danych specyficzne dla narzędzia deweloperskich.
* ***ux.lib:*** jest to wersja binarna biblioteki USBX C. Jest on dystrybuowany za pomocą pakietu standardowego.
* ***demo_usbx.c:*** plik C zawierający prostą demonstrację USBX

Wszystkie nazwy plików są małe. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy programowe Unix.

## <a name="usbx-installation"></a>Instalacja USBX

Dysk USBX jest instalowany przez GitHub repozytorium danych na komputer lokalny. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium USBX na komputerze:

```c
    git clone https://github.com/azure-rtos/usbx
```

Możesz też pobrać kopię repozytorium przy użyciu przycisku pobierania na stronie GitHub głównej.

Instrukcje dotyczące tworzenia biblioteki USBX można również znaleźć na pierwszej stronie repozytorium online.

Poniższe ogólne instrukcje dotyczą praktycznie każdej instalacji:

1. Użyj tego samego katalogu, w którym wcześniej zainstalowano ThreadX na dysku twardym hosta. Wszystkie nazwy USBX są unikatowe i nie będą zakłócać poprzedniej instalacji USBX.
1. Dodaj wywołanie ***ux_system_initialize** _ na początku lub w pobliżu początku _*_tx_application_define_**. W tym miejscu są inicjowane zasoby USBX.
1. Dodaj wywołanie ***ux_device_stack_initialize*.**
1. Dodaj jedno lub więcej wywołań w celu zainicjowania wymaganych klas USBX (klas hostów i/lub urządzeń)
1. Dodaj jedno lub więcej wywołań w celu zainicjowania kontrolera urządzenia dostępnego w systemie.
1. Może być konieczne zmodyfikowanie pliku tx_low_level_initialize.c w celu dodania inicjowania sprzętu niskiego poziomu i routingu wektorów przerwań. Jest to specyficzne dla platformy sprzętowej i nie zostanie tu omówione.|
1. Kompilowanie kodu źródłowego aplikacji i łączenie z bibliotekami czasu uruchamiania USBX i ThreadX (FileX i/lub Netx może być również wymagane, jeśli klasa magazynu USB i/lub klasy sieci USB mają być skompilowane), ux.a (lub ux.lib) i tx.a (lub tx.lib). Wynikowy kod można pobrać do obiektu docelowego i wykonać.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia biblioteki USBX. Wszystkie opcje znajdują się w ***ux_user.h.***

Na poniższej liście przedstawiono szczegółowo każdą opcję konfiguracji.

| Opcja &nbsp; konfiguracji | Opis |
| --- | --- |
| **UX_PERIODIC_RATE** | Ta wartość reprezentuje liczbę takt na sekundę dla określonej platformy sprzętowej. Wartość domyślna to 1000, co oznacza 1 takt na milisekundę. |
| **UX_THREAD_STACK_SIZE** | Ta wartość to rozmiar stosu w bajtach dla wątków USBX. Może to być zazwyczaj 1024 bajty lub 2048 bajtów w zależności od używanego procesora i kontrolera hosta. |
| **UX_THREAD_PRIORITY_ENUM** | Jest to wartość priorytetu ThreadX dla wątków wyliczenia USBX, które monitorują topologię magistrali. |
| **UX_THREAD_PRIORITY_CLASS** | Jest to wartość priorytetu ThreadX dla standardowych wątków USBX. |
| **UX_THREAD_PRIORITY_KEYBOARD** | Jest to wartość priorytetu ThreadX dla klasy klawiatury USBX HID. |
| **UX_THREAD_PRIORITY_DCD** | Jest to wartość priorytetu ThreadX dla wątku kontrolera urządzenia. |
| **UX_NO_TIME_SLICE** | Ta wartość w rzeczywistości definiuje wycinek czasu, który będzie używany dla wątków. Jeśli na przykład zdefiniowano wartość 0, port docelowy ThreadX nie używa wycinków czasu. |
| **UX_MAX_SLAVE_CLASS_DRIVER** | Jest to maksymalna liczba klas USBX, które można zarejestrować za pośrednictwem ux_device_stack_class_register. |
| **UX_MAX_SLAVE_LUN** | Ta wartość reprezentuje bieżącą liczbę jednostek logicznych SCSI reprezentowanych w sterowniku klasy magazynu urządzeń. |
| **UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC** | Jeśli jest zdefiniowana, klasa magazynu będzie obsługiwać polecenia multi-Media Commands (MMC), czyli DVD-ROM. |
| **UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES** | Ta wartość reprezentuje liczbę pakietów NetX w puli pakietów klasy CDC-ECM. Wartość domyślna to 16. |
| **UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH** | Ta wartość reprezentuje maksymalną liczbę bajtów odebranych w punkcie końcowym kontrolki w stosie urządzenia. Wartość domyślna to 256 bajtów, ale można ją zmniejszyć w środowiskach ograniczeń pamięci. |
| **UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH** | Ta wartość reprezentuje maksymalną długość w bajtach raportu HID. |
| **UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE** | Ta wartość reprezentuje maksymalną liczbę raportów HID, które można dodać do kolejki jednocześnie. |
| **UX_SLAVE_REQUEST_DATA_MAX_LENGTH** | Ta wartość reprezentuje maksymalną liczbę bajtów odebranych w zbiorczym punkcie końcowym w stosie urządzenia. Wartość domyślna to 4096 bajtów, ale można ją zmniejszyć w środowiskach ograniczeń pamięci. |

## <a name="source-code-tree"></a>Drzewo kodu źródłowego

Pliki USBX są dostępne w kilku katalogach.

![Drzewo kodu źródłowego](media/usbx-device-stack/source-code-tree.png)

Aby pliki były rozpoznawalne na podstawie ich nazw, przyjęto następującą konwencję:

| Nazwa sufiksu pliku  | Opis pliku                          |
| ----------------- | ----------------------------------------- |
| ux_host_stack   | Pliki podstawowe stosu hosta usbx                |
| ux_host_class   | pliki klas stosu hosta usbx             |
| ux_hcd           | Pliki sterowników kontrolera stosu hosta usbx   |
| ux_device_stack | pliki podstawowe stosu urządzenia usbx              |
| ux_device_class | pliki klas stosów urządzeń usbx           |
| ux_dcd           | pliki sterowników kontrolera stosu urządzeń usbx |
| ux_otg           | pliki związane ze sterownikami kontrolera usbx otg  |
| ux_pictbridge    | pliki pictbridge usbx                     |
| ux_utility       | funkcje narzędziowe usbx                    |
| demo_usbx        | pliki demonstracyjne dla USBX              |

## <a name="initialization-of-usbx-resources"></a>Inicjowanie zasobów USBX

USBX ma własnego menedżera pamięci. Pamięć musi zostać przydzielona do USBX przed zainicjowaniem strony hosta lub urządzenia USBX. Menedżer pamięci USBX może pomieścić systemy, w których pamięć może być buforowana.

Następująca funkcja inicjuje zasoby pamięci USBX z 128 K zwykłej pamięci i nie ma oddzielnej puli dla pamięci podręcznej bezpiecznej:

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

Prototyp dla tej ux_system_initialize jest następujący:

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

Parametry wejściowe:

| Parametr                          | Opis                             |
| ---------------------------------- | --------------------------------------- |
| VOID *regular_memory_pool_start    | Początek zwykłej puli pamięci    |
| ULONG regular_memory_size          | Rozmiar zwykłej puli pamięci         |
| VOID *cache_safe_memory_pool_start | Początek puli bezpiecznej pamięci podręcznej |
| ULONG cache_safe_memory_size       | Rozmiar puli pamięci podręcznej bezpiecznej      |

Nie wszystkie systemy wymagają definicji bezpiecznej pamięci podręcznej. W takim systemie wartości przekazane podczas inicjowania wskaźnika pamięci zostaną ustawione na UX_NULL, a rozmiar puli na 0. Następnie USBX użyje zwykłej puli pamięci zamiast puli bezpiecznej pamięci podręcznej.

W systemie, w którym zwykła pamięć nie jest bezpieczna w pamięci podręcznej, a kontroler wymaga wykonania pamięci DMA, należy zdefiniować pulę pamięci w strefie bezpiecznej pamięci podręcznej.

## <a name="uninitialization-of-usbx-resources"></a>Uninitializacja zasobów USBX

Działanie USBX można zakończyć, zwalniając jego zasoby. Przed zakończeniem działania interfejsu usbx wszystkie klasy i zasoby kontrolera muszą zostać prawidłowo zakończone. Następująca funkcja uninitializuje zasoby pamięci USBX:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

Prototyp dla tej ux_system_initialize jest następujący:

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a>Definicja kontrolera urządzenia USB

W dowolnym momencie można zdefiniować tylko jeden kontroler urządzenia USB do pracy w trybie urządzenia. Plik inicjowania aplikacji powinien zawierać tę definicję. Poniższy wiersz wykonuje definicję ogólnego kontrolera USB:

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

Inicjalizacja urządzenia USB ma następujący prototyp:

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

z następującymi parametrami:

| Pararmeter               | Opis                      |
| ------------------------ | -------------------------------- |
| ULONG dcd_io            | Adres we/wy kontrolera     |
| ULONG dcd_irq           | Przerwanie używane przez kontroler |
| ULONG dcd_vbus_address | Adres zasad grupy VBUS         |

Poniższy przykład to inicjowanie dysku USBX w trybie urządzenia z klasą urządzenia magazynującego i kontrolerem ogólnym:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a>Rozwiązywanie problemów

UsbX jest dostarczany z plikiem pokazowym i środowiskiem symulacji. Zawsze dobrym pomysłem jest uruchomienie platformy demonstracyjnej jako pierwszej — na sprzęcie docelowym lub na określonej platformie demonstracyjnej.

## <a name="usbx-version-id"></a>Identyfikator wersji USBX

Bieżąca wersja usbx jest dostępna dla użytkownika i oprogramowania aplikacji w czasie uruchamiania. Programista może uzyskać wersję USBX z badania pliku ***ux_port.h_.** Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję USBX, sprawdzając ciąg globalny _ *__ ux_version_id_* _, który jest zdefiniowany w _*_ux_port.h_**.
