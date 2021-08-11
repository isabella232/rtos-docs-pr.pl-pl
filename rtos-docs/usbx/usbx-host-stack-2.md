---
title: Rozdział 2 — Azure RTOS stosu hosta USBX
description: Dowiedz się, jak zainstalować stos hosta USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 77df2c4e4bf4ef38403fe78eb98f18820de4325aadb941fc69275e4c77754212
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790970"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a>Rozdział 2 — Azure RTOS stosu hosta USBX

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

### <a name="computer-type"></a>Typ komputera

Tworzenie aplikacji osadzonych odbywa się zwykle na komputerach Windows komputerach stacjonarnych lub komputerach hostów z systemem Unix. Gdy aplikacja zostanie skompilowana, połączona i zlokalizowana na hoście, zostanie pobrana na docelowy sprzęt w celu wykonania.

### <a name="download-interfaces"></a>Interfejsy pobierania

Zazwyczaj docelowy pobieranie odbywa się za pośrednictwem interfejsu szeregowego RS-232, chociaż interfejsy równoległe, USB i Ethernet stają się bardziej popularne. Aby uzyskać dostępne opcje, zobacz dokumentację narzędzia dewelopera.

### <a name="debugging-tools"></a>Narzędzia debugowania

Debugowanie odbywa się zwykle za pośrednictwem tego samego linku co pobieranie obrazu programu. Istnieje wiele debugerów, od małych programów monitorów uruchomionych w środowisku docelowym za pośrednictwem monitora debugowania w tle (BDM) i In-Circuit Emulator (ICE). Narzędzie ICE zapewnia najbardziej niezawodne debugowanie rzeczywistego docelowego sprzętu.

### <a name="required-hard-disk-space"></a>Wymagane miejsce na dysku twardym

Kod źródłowy USBX jest dostarczany w formacie ASCII i wymaga około 500 KB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące celu

UsbX wymaga od 24 KB do 64 KB pamięci tylko do odczytu (ROM) na docelowym w trybie hosta. Ilość wymaganej pamięci zależy od typu używanego kontrolera i klas USB połączonych z USBX. Kolejne 32 KB pamięci RAM (Random Access Memory) obiektu docelowego są wymagane dla globalnych struktur danych USBX i puli pamięci. Tę pulę pamięci można również dostosować w zależności od oczekiwanej liczby urządzeń na dysku USB i typu kontrolera USB. Strona urządzenia USBX wymaga około 10–12 K pamięci ROM w zależności od typu kontrolera urządzenia. Użycie pamięci RAM zależy od typu klasy emulowanej przez urządzenie.

UsbX opiera się również na semaforach ThreadX, mutexach i wątkach w celu ochrony wielu wątków oraz zawieszania we/wy i okresowego przetwarzania w celu monitorowania topologii magistrali USB.

### <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS USBX można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie <https://github.com/azure-rtos/usbx/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium:

- ***ux_api.h:*** ten plik nagłówka C zawiera wszystkie elementy systemowe, struktury danych i prototypy usług.
- ***ux_port.h:*** ten plik nagłówkowy języka C zawiera wszystkie definicje i struktury danych specyficzne dla narzędzia deweloperskich.
- ***ux.lib:*** jest to wersja binarna biblioteki USBX C. Jest on dystrybuowany za pomocą pakietu standardowego.
- ***demo_usbx.c:*** plik C zawierający prostą demonstrację USBX

Wszystkie nazwy plików są małe. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy programowe Unix.

## <a name="usbx-installation"></a>Instalacja USBX

Dysk USBX jest instalowany przez GitHub repozytorium na komputer lokalny. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium USBX na komputerze:

```powershell
    git clone https://github.com/azure-rtos/usbx
```

Możesz też pobrać kopię repozytorium przy użyciu przycisku pobierania na GitHub głównej.

Instrukcje dotyczące tworzenia biblioteki USBX można również znaleźć na pierwszej stronie repozytorium online.

Poniższe ogólne instrukcje dotyczą praktycznie każdej instalacji:

1. Użyj tego samego katalogu, w którym wcześniej zainstalowano ThreadX na dysku twardym hosta. Wszystkie nazwy USBX są unikatowe i nie będą zakłócać poprzedniej instalacji USBX.
2. Dodaj wywołanie funkcji ***ux_system_initialize** _ na początku lub w pobliżu początku tx_application_define *.* * W tym miejscu są inicjowanie zasobów USBX.
3. Dodaj wywołanie do ***ux_host_stack_initialize*.**
4. Dodaj jedno lub więcej wywołań w celu zainicjowania wymaganego dysku USBX.
5. Dodaj jedno lub więcej wywołań w celu zainicjowania kontrolerów hosta dostępnych w systemie.
6. Może być konieczne zmodyfikowanie pliku tx_low_level_initialize.c w celu dodania inicjowania sprzętu niskiego poziomu i routingu wektorów przerwań. Jest to specyficzne dla platformy sprzętowej i nie zostanie tu omówione.
7. Kompilowanie kodu źródłowego aplikacji i łączenie z bibliotekami czasu uruchamiania USBX i ThreadX (FileX i/lub Netx może być również wymagane, jeśli klasa magazynu USB i/lub klasy sieci USB mają być skompilowane), ux.a (lub ux.lib) i tx.a (lub tx.lib). Wynikowe dane można pobrać do obiektu docelowego i wykonać.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do tworzenia biblioteki USBX. Wszystkie opcje znajdują się w ***ux_user.h.***

Na poniższej liście przedstawiono szczegółowo każdą opcję konfiguracji.


- **UX_PERIODIC_RATE:** ta wartość reprezentuje liczbę takt na sekundę dla określonej platformy sprzętowej. Wartość domyślna to 1000, co oznacza jeden takt na milisekundę.
- **UX_MAX_CLASS_DRIVER:** ta wartość to maksymalna liczba klas, które mogą być ładowane przez USBX. Ta wartość reprezentuje kontener klasy, a nie liczbę wystąpień klasy. Jeśli na przykład określonej implementacji USBX wymaga klasy koncentratora, klasy drukarki i klasy magazynu, wartość UX_MAX_CLASS_DRIVER można ustawić na 3 niezależnie od liczby urządzeń należących do tych klas.
- **UX_MAX_HCD:** ta wartość reprezentuje liczbę różnych kontrolerów hostów, które są dostępne w systemie. W przypadku obsługi usb 1.1 ta wartość będzie w większości wynosić 1. W przypadku obsługi usb 2.0 ta wartość może być większa niż 1. Ta wartość reprezentuje liczbę współbieżnych kontrolerów hostów uruchomionych w tym samym czasie. Jeśli na przykład istnieją dwa wystąpienia systemu OHCI z systemem lub jeden kontroler EHCI i jeden z uruchomionych kontrolerów OHCI, UX_MAX_HCD ustawić wartość 2. 
- **UX_MAX_DEVICES:** ta wartość reprezentuje maksymalną liczbę urządzeń, które można podłączyć do portu USB. Zwykle teoretyczna maksymalna liczba na jednym usb to 127 urządzeń. Tę wartość można skalować w dół, aby zaoszczędzić pamięć. Należy zauważyć, że ta wartość reprezentuje łączną liczbę urządzeń niezależnie od liczby sterowników USB w systemie.
- **UX_MAX_ED:** ta wartość reprezentuje maksymalną liczbę identyfikatorów ED w puli kontrolerów. Ten numer jest przypisywany tylko do jednego kontrolera. Jeśli istnieje wiele wystąpień kontrolerów, ta wartość jest używana przez każdy pojedynczy kontroler.
- **UX_MAX_TD i UX_MAX_ISO_TD:** ta wartość reprezentuje maksymalną liczbę zwykłych i izochronnych identyfikatorów TD w puli kontrolerów. Ten numer jest przypisywany tylko do jednego kontrolera. Jeśli istnieje wiele wystąpień kontrolerów, ta wartość jest używana przez każdy pojedynczy kontroler.
- **UX_THREAD_STACK_SIZE:** ta wartość to rozmiar stosu w bajtach dla wątków USBX. Może to być zazwyczaj 1024 bajty lub 2048 bajtów w zależności od używanego procesora i kontrolera hosta.
- **UX_HOST_ENUM_THREAD_STACK_SIZE:** ta wartość jest rozmiar stosu wątku wyliczenia hosta USB. Jeśli ten symbol nie jest ustawiony, rozmiar stosu wątku wyliczenia hosta USBX jest ustawiony na **UX_THREAD_STACK_SIZE**. 
- **UX_HOST_HCD_THREAD_STACK_SIZE:** ta wartość jest rozmiar stosu wątku HCD hosta USB. Jeśli ten symbol nie jest ustawiony, rozmiar stosu wątku HOSTA USBX HCD jest ustawiony **na UX_THREAD_STACK_SIZE**.
- **UX_THREAD_PRIORITY_ENUM:** jest to wartość priorytetu ThreadX dla wątków wyliczenia USBX, które monitorują topologię magistrali.
- **UX_THREAD_PRIORITY_CLASS:** jest to wartość priorytetu ThreadX dla standardowych wątków USBX.
- **UX_THREAD_PRIORITY_KEYBOARD:** jest to wartość priorytetu ThreadX dla klasy klawiatury USBX HID.
- **UX_THREAD_PRIORITY_HCD:** jest to wartość priorytetu ThreadX wątku kontrolera hosta.
- **UX_NO_TIME_SLICE:** ta wartość faktycznie definiuje wycinek czasu, który będzie używany dla wątków. Jeśli na przykład zdefiniowano wartość 0, port docelowy ThreadX nie używa wycinków czasu.
- **UX_MAX_HOST_LUN:** ta wartość reprezentuje maksymalną liczbę jednostek logicznych SCSI reprezentowanych w sterowniku klasy magazynu hosta.
- **UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT:** jeśli ta wartość jest zdefiniowana, ta wartość zawiera kod do obsługi urządzeń magazynujących, które używają protokołu CB LUB CBI (na przykład dyskietek). Jest ona domyślnie wyłączona, ponieważ te protokoły są przestarzałe i są one nadsyłane przez protokół BOT (Bulk Only Transport), z którego korzystają praktycznie wszystkie nowoczesne urządzenia magazynu.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE:** Jeśli ta wartość jest zdefiniowana, powoduje, że ux_host_class_hid_keyboard_key_get tylko raportować zmiany kluczy, czyli naciśnięcia klawiszy i wydań klawiszy. Domyślnie raporty są raporty tylko wtedy, gdy klucz nie jest włączona.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY:** używana tylko **wtedy, UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowana. Jeśli ta jest zdefiniowana, ux_host_class_hid_keyboard_key_get zgłaszać tylko zmiany naciśnięte/w dół klawiszy; zmiany wydanego/up klucza nie są zgłaszane.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS:** używana tylko **wtedy, UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowana. Jeśli ta jest zdefiniowana, ux_host_class_hid_keyboard_key_get zgłaszać zmiany klucza blokady (CapsLock/NumLock/ScrollLock).
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS:** używana tylko **wtedy, UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowana. Jeśli jest zdefiniowana, ux_host_class_hid_keyboard_key_get zgłaszać zmiany klawisza modyfikującego (Ctrl/Alt/Shift/GUI).
- **UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES:** Jeśli jest zdefiniowana, ta wartość reprezentuje liczbę pakietów w klasie hosta CDC-ECM. Wartość domyślna to 16.

## <a name="source-code-tree"></a>Drzewo kodu źródłowego

Pliki USBX są dostępne w kilku katalogach.

![Drzewo kodu źródłowego](media/usbx-host-stack/source-code-tree.png)

Aby pliki były rozpoznawalne na podstawie ich nazw, przyjęto następującą konwencję:

| Nazwa sufiksu pliku | Opis pliku                          |
| ---------------- | ----------------------------------------- |
| ux_host_stack    | Pliki podstawowe stosu hosta usbx                |
| ux_host_class    | pliki klas stosu hosta usbx             |
| ux_hcd           | Pliki sterowników kontrolera stosu hosta usbx   |
| ux_device_stack  | Pliki podstawowe stosu urządzenia usbx              |
| ux_device_class  | pliki klas stosów urządzeń usbx           |
| ux_dcd           | Pliki sterowników kontrolera stosu urządzeń usbx |
| ux_otg           | Pliki powiązane ze sterownikami kontrolera usbx otg  |
| ux_pictbridge    | pliki usbx pictbridge                     |
| ux_utility       | Funkcje narzędziowe usbx                    |
| demo_usbx        | pliki demonstracyjne dla USBX              |

## <a name="initialization-of-usbx-resources"></a>Inicjowanie zasobów USBX

USBX ma własny menedżer pamięci. Pamięć musi zostać przydzielona do USBX przed zainicjowaniem strony hosta lub urządzenia USBX. Menedżer pamięci USBX może pomieścić systemy, w których pamięć może być buforowana.

Następująca funkcja inicjuje zasoby pamięci USBX z 128 000 pamięci regularnej i braku oddzielnej puli dla pamięci podręcznej:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

Prototyp dla tej ux_system_initialize jest następujący.

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a>Parametry wejściowe:

- **regular_memory_pool_start** Początek zwykłej puli pamięci.
- **regular_memory_size** Rozmiar zwykłej puli pamięci.
- **cache_safe_memory_pool_start** Początek puli bezpiecznej pamięci podręcznej.
- **cache_safe_memory_size** Rozmiar puli bezpiecznej pamięci podręcznej.    |

Nie wszystkie systemy wymagają definicji bezpiecznej pamięci podręcznej. W takim systemie wartości przekazane podczas inicjowania wskaźnika pamięci zostaną ustawione na wartość UX_NULL, a rozmiar puli na 0. Następnie USBX użyje zwykłej puli pamięci zamiast puli bezpiecznej pamięci podręcznej.

W systemie, w którym zwykła pamięć nie jest bezpieczna w pamięci podręcznej, a kontroler wymaga wykonania pamięci DMA (na przykład kontrolerów OHCI, EHCI), należy zdefiniować pulę pamięci w strefie bezpiecznej pamięci podręcznej.

## <a name="uninitialization-of-usbx-resources"></a>Uninitializacja zasobów USBX

Działanie USBX można zakończyć, zwalniając jego zasoby. Przed zakończeniem działania interfejsu usbx wszystkie klasy i zasoby kontrolera muszą zostać prawidłowo zakończone. Następująca funkcja uninitializuje zasoby pamięci USBX:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

Prototyp dla tej ux_system_initialize jest następujący.

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a>Definicja kontrolerów hosta USB

Aby dysk USBX działał w trybie hosta, należy zdefiniować co najmniej jeden kontroler hosta USB. Plik inicjowania aplikacji powinien zawierać tę definicję. Poniższy wiersz wykonuje definicję ogólnego kontrolera hosta.

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

Ten ux_host_stack_hcd_register ma następujący prototyp.

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

Funkcja ux_host_stack_hcd_register ma następujące parametry.

- **hcd_name:** ciąg nazwy kontrolera
- **hcd_initialize_function:** funkcja inicjowania kontrolera
- **hcd_param1:** zwykle wartość we/wy lub pamięć używana przez kontroler
- **hcd_param2:** zwykle irq używane przez kontroler

W naszym poprzednim przykładzie:

- "ux_hcd_controller" to nazwa kontrolera
- "ux_hcd_controller_initialize" to procedura inicjowania dla kontrolera hosta
- 0xd0000 to adres, pod którym kontroler hosta jest widoczny w pamięci
- i 0x0a to irq używane przez kontroler hosta.

Poniżej znajduje się przykład inicjowania USBX w trybie hosta z jednego kontrolera hosta i kilka klas.

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a>Definicja klas hostów

Wymagane jest zdefiniowanie jednej lub większej liczby klas hostów za pomocą dysku USBX. Klasa USB jest wymagana do zasilania urządzenia USB po skonfigurowaniu urządzenia USB przez stos USB. Klasa USB jest specyficzna dla urządzenia. Do obsługi urządzenia USB może być wymagana co najmniej jedna klasa w zależności od liczby interfejsów zawartych w deskryptorach urządzenia USB.

Jest to przykład rejestracji klasy HUB.

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

Funkcja ux_host_class_register ma następujący prototyp.

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- **class_name** to nazwa klasy
- **class_entry_address** to punkt wejścia klasy

W przykładzie inicjowania klasy HUB:

- "ux_host_class_hub" to nazwa klasy centrum
- ux_host_class_hub_entry to punkt wejścia klasy HUB.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

UsbX jest dostarczany z plikiem demonstracyjnym i środowiskiem symulacji. Zawsze dobrym pomysłem jest uruchomienie najpierw platformy demonstracyjnej — na sprzęcie docelowym lub na określonej platformie demonstracyjnej.

Jeśli system demonstracyjny nie działa, spróbuj wykonać następujące czynności, aby zawęzić problem.

## <a name="usbx-version-id"></a>Identyfikator wersji USBX

Bieżąca wersja dysku USBX jest dostępna zarówno dla użytkownika, jak i dla oprogramowania aplikacji w czasie uruchamiania. Programista może uzyskać wersję USBX z badania pliku ***ux_port.h_.** Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję USBX, sprawdzając ciąg globalny _ *__ ux_version_id_* _, który jest zdefiniowany w _*_ux_port.h_**.
