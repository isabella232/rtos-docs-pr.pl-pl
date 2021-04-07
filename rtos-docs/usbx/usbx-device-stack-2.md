---
title: Rozdział 2 — Instalacja stosu urządzeń usługi Azure RTO USBX
description: Dowiedz się, jak zainstalować stos urządzeń usługi Azure RTO USBX, a także ważne zagadnienia dotyczące hosta, które należy wziąć pod uwagę przed zainstalowaniem programu.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd58f77130fa252be9163bd70c29f7deee400d30
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549780"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a>Rozdział 2 — Instalacja stosu urządzeń usługi Azure RTO USBX

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

### <a name="computer-type"></a>Typ komputera

Projektowanie osadzone jest zwykle wykonywane na komputerach hosta z systemem Windows lub UNIX. Gdy aplikacja zostanie skompilowana, połączona i umieszczona na hoście, zostanie pobrana na docelowy sprzęt do wykonania.

### <a name="download-interfaces"></a>Pobierz interfejsy

Zazwyczaj pobieranie docelowe odbywa się za pośrednictwem interfejsu szeregowego RS-232, chociaż interfejsy równoległe, USB i Ethernet są coraz bardziej popularne. Zobacz dokumentację narzędzia deweloperskiego, aby poznać dostępne opcje.

### <a name="debugging-tools"></a>Narzędzia debugowania

Debugowanie odbywa się zwykle nad tym samym łączem, co w przypadku pobierania obrazu programu. Istnieje wiele różnych debugerów, począwszy od małych programów monitorujących uruchomionych w miejscu docelowym za pomocą narzędzia Monitor debugowania w tle (BDM) i In-Circuit emulatora (lodem). Narzędzie do ELIMINACJi oprogramowania zapewnia najbardziej niezawodne debugowanie rzeczywistego sprzętu docelowego.

### <a name="required-hard-disk-space"></a>Wymagane miejsce na dysku twardym

Kod źródłowy dla USBX jest dostarczany w formacie ASCII i wymaga około 500 KB miejsca na dysku twardym komputera hosta.

### <a name="target-considerations"></a>Zagadnienia dotyczące obiektów docelowych

USBX wymaga od 24 kilobajtów do 64 kilobajtów pamięci tylko do odczytu (ROM) w obszarze docelowym w trybie hosta. Wymagana ilość pamięci zależy od typu używanego kontrolera i klas USB połączonych z USBX. Do USBX globalnych struktur danych i puli pamięci wymagane są inne 32 kilobajty pamięci docelowej (RAM). Tę pulę pamięci można również dostosować w zależności od oczekiwanej liczby urządzeń USB i typu kontrolera USB. Po stronie urządzenia USBX wymagane jest około 10-12 K pamięci ROM w zależności od typu kontrolera urządzenia. Użycie pamięci RAM zależy od typu klasy emulowanej przez urządzenie.

USBX opiera się również na semaforach ThreadX, muteksach i wątkach na potrzeby ochrony wielu wątków oraz zawieszania operacji we/wy i okresowego przetwarzania dla monitorowania topologii magistrali USB.

### <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO USBX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/usbx/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium.

* ***ux_api. h***: ten plik nagłówka C zawiera wszystkie równe systemowe, struktury danych i prototypy usługi.
* ***ux_port. h***: ten plik nagłówkowy C zawiera wszystkie definicje i struktury danych specyficzne dla narzędzia deweloperskiego.
* ***UX. lib***: jest to wersja binarna biblioteki USBX C. Jest dystrybuowana z pakietem standardowym.
* ***demo_usbx. c***: plik c zawierający prostą wersję DEMONSTRACYJNą USBx

Wszystkie nazwy plików są małymi literami. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformę deweloperskią systemu UNIX.

## <a name="usbx-installation"></a>Instalacja USBX

USBX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium USBX na komputerze:

```c
    git clone https://github.com/azure-rtos/usbx
```

Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.

Znajdziesz również instrukcje dotyczące tworzenia biblioteki USBX na stronie frontonu repozytorium online.

Poniższe instrukcje ogólne dotyczą niemal każdej instalacji:

1. Użyj tego samego katalogu, w którym wcześniej zainstalowano ThreadX na dysku twardym hosta. Wszystkie nazwy USBX są unikatowe i nie zakłócają instalacji poprzedniej USBX.
1. Dodaj wywołanie do ***ux_system_initialize** _ lub blisko początku _ *_tx_application_define_* *. Jest to miejsce, w którym zainicjowano zasoby USBX.
1. Dodaj wywołanie do ***ux_device_stack_initialize *.**
1. Dodaj co najmniej jedno wywołanie, aby zainicjować wymagane klasy USBX (klasy hosta i/lub urządzeń)
1. Dodaj co najmniej jedno wywołanie w celu zainicjowania kontrolera urządzenia dostępnego w systemie.
1. Może być konieczne zmodyfikowanie pliku tx_low_level_initialize. c, aby dodać inicjalizację sprzętu niskiego poziomu i Routing wektora przerwania. Jest to specyficzne dla platformy sprzętowej i nie zostanie omówiona w tym miejscu. |
1. Kompiluj kod źródłowy aplikacji i linki z bibliotekami czasu wykonywania USBX i ThreadX (FileX i/lub NetX mogą być również wymagane, jeśli Klasa magazynu USB i/lub klasy sieci USB mają być kompilowane), UX. a (lub UX. lib) i TX. a (lub TX. lib). Wyniki można pobrać do elementu docelowego i wykonać!

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania biblioteki USBX. Wszystkie opcje znajdują się w ***ux_user. h***.

Poniższa lista zawiera szczegóły każdej opcji konfiguracji.

| &nbsp;Opcja konfiguracji | Opis |
| --- | --- |
| **UX_PERIODIC_RATE** | Ta wartość reprezentuje liczbę taktów (w sekundach) dla określonej platformy sprzętowej. Wartość domyślna to 1000 wskazujący 1 takt na milisekundy. |
| **UX_THREAD_STACK_SIZE** | Ta wartość to rozmiar stosu w bajtach dla wątków USBX. Może to być zwykle 1024 bajtów lub 2048 bajtów w zależności od używanego procesora i kontrolera hosta. |
| **UX_THREAD_PRIORITY_ENUM** | Jest to wartość priorytetu ThreadX dla wątków wyliczenia USBX, które monitorują topologię magistrali. |
| **UX_THREAD_PRIORITY_CLASS** | Jest to wartość priorytetu ThreadX dla standardowych wątków USBX. |
| **UX_THREAD_PRIORITY_KEYBOARD** | Jest to wartość priorytetu ThreadX dla klasy klawiatury HID USBX. |
| **UX_THREAD_PRIORITY_DCD** | Jest to wartość priorytetu ThreadX dla wątku kontrolera urządzenia. |
| **UX_NO_TIME_SLICE** | Ta wartość w rzeczywistości definiuje wycinek czasu, który będzie używany dla wątków. Na przykład, jeśli określono wartość 0, port docelowy ThreadX nie korzysta z wycinków czasu. |
| **UX_MAX_SLAVE_CLASS_DRIVER** | Jest to maksymalna liczba klas USBX, które mogą być rejestrowane za pośrednictwem ux_device_stack_class_register. |
| **UX_MAX_SLAVE_LUN** | Ta wartość reprezentuje bieżącą liczbę jednostek logicznych SCSI przedstawionych w sterowniku klasy magazynu urządzeń. |
| **UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC** | W przypadku zdefiniowania klasy Storage będzie obsługiwać polecenia wielonośnikowe (MMC), czyli DVD-ROM. |
| **UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES** | Ta wartość reprezentuje liczbę pakietów NetX w puli pakietów przechwytywania zmian-ECM. Wartość domyślna to 16. |
| **UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH** | Ta wartość reprezentuje maksymalną liczbę bajtów odebranych w punkcie końcowym kontrolki w stosie urządzeń. Wartość domyślna to 256 bajtów, ale można ją zmniejszyć w środowiskach ograniczeń pamięci. |
| **UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH** | Ta wartość reprezentuje maksymalną długość w bajtach raportu HID. |
| **UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE** | Ta wartość reprezentuje maksymalną liczbę raportów HID, które mogą być umieszczone w kolejce jednocześnie. |
| **UX_SLAVE_REQUEST_DATA_MAX_LENGTH** | Ta wartość reprezentuje maksymalną liczbę bajtów odebranych w zbiorczym punkcie końcowym w stosie urządzeń. Wartość domyślna to 4096 bajtów, ale można ją zmniejszyć w środowiskach ograniczeń pamięci. |

## <a name="source-code-tree"></a>Drzewo kodu źródłowego

Pliki USBX są dostępne w kilku katalogach.

![Drzewo kodu źródłowego](media/usbx-device-stack/source-code-tree.png)

Aby pliki były rozpoznawane według ich nazw, przyjęto następującą konwencję:

| Nazwa sufiksu pliku  | Opis pliku                          |
| ----------------- | ----------------------------------------- |
| ux_host_stack   | podstawowe pliki stosu hosta USBx                |
| ux_host_class   | pliki klas stosu hosta USBx             |
| ux_hcd           | pliki sterowników kontrolera stosu hosta USBx   |
| ux_device_stack | podstawowe pliki stosu urządzeń USBx              |
| ux_device_class | pliki klas stosu urządzeń USBx           |
| ux_dcd           | pliki sterowników kontrolera stosu urządzeń USBx |
| ux_otg           | pliki powiązane z sterownikiem kontrolera OTG USBx  |
| ux_pictbridge    | Pliki USBx PictBridge                     |
| ux_utility       | funkcje narzędzia USBx                    |
| demo_usbx        | pliki demonstracyjne dla USBX              |

## <a name="initialization-of-usbx-resources"></a>Inicjowanie zasobów USBX

USBX ma własny Menedżer pamięci. Pamięć należy przydzielyć do USBX przed zainicjowaniem hosta lub po stronie urządzenia USBX. Menedżer pamięci USBX może obsługiwać systemy, w których pamięć może być buforowana.

Poniższa funkcja inicjuje zasoby pamięci USBX z 128 K zwykłej pamięci i nie ma oddzielnej puli pamięci podręcznej w bezpiecznym miejscu:

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

Prototyp ux_system_initialize jest następujący:

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

Parametry wejściowe:

| Parametr                          | Opis                             |
| ---------------------------------- | --------------------------------------- |
| VOID * regular_memory_pool_start    | Początek zwykłej puli pamięci    |
| ULONG regular_memory_size          | Rozmiar zwykłej puli pamięci         |
| VOID * cache_safe_memory_pool_start | Początek bezpiecznej puli pamięci podręcznej |
| ULONG cache_safe_memory_size       | Rozmiar bezpiecznej puli pamięci podręcznej      |

Nie wszystkie systemy wymagają definicji bezpiecznej pamięci podręcznej. W takim systemie wartości przesyłane podczas inicjalizacji wskaźnika pamięci będą ustawione na UX_NULL i rozmiar puli do 0. Następnie USBX będzie używać zwykłej puli pamięci w miejsce pamięci podręcznej w bezpiecznej puli.

W systemie, w którym zwykła pamięć nie jest bezpieczna w pamięci podręcznej, a kontroler wymaga przeprowadzenia pamięci DMA, należy zdefiniować pulę pamięci w bezpiecznej strefie pamięci podręcznej.

## <a name="uninitialization-of-usbx-resources"></a>Odinicjowanie zasobów USBX

USBX można przerwać, zwalniając jego zasoby. Przed zakończeniem USBx należy prawidłowo zakończyć wszystkie klasy i zasoby kontrolerów. Następująca funkcja nie inicjuje USBX zasobów pamięci:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

Prototyp ux_system_initialize jest następujący:

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a>Definicja kontrolera urządzenia USB

W dowolnym momencie można zdefiniować tylko jeden kontroler urządzenia USB do działania w trybie urządzenia. Plik inicjujący aplikacji powinien zawierać tę definicję. W poniższym wierszu jest wykonywana definicja ogólnego kontrolera USB:

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
| ULONG dcd_io            | Adres operacji we/wy kontrolera     |
| ULONG dcd_irq           | Przerwanie używane przez kontroler |
| ULONG dcd_vbus_address | Adres VBUS GPIO         |

Poniższy przykład to Inicjalizacja USBX w trybie urządzenia z klasą urządzenia magazynującego i ogólnym kontrolerem:

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

USBX jest dostarczany z plikiem demonstracyjnym i środowiskiem symulacji. Zawsze dobrym pomysłem jest rozpoczęcie od pierwszego uruchomienia platformy demonstracyjnej — na sprzęcie docelowym lub na określonej platformie demonstracyjnej.

## <a name="usbx-version-id"></a>Identyfikator wersji USBX

Bieżąca wersja programu USBX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji w czasie wykonywania. Programista może uzyskać wersję USBX z badania pliku ***ux_port. h** _. Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję USBX, badając ciąg globalny _ _ *_ux_version_id_* _, który jest zdefiniowany w _ *_ux_port. h_* *.
