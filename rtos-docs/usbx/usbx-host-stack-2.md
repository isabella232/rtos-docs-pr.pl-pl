---
title: Rozdział 2 — Instalacja stosu hosta usługi Azure RTO USBX
description: Dowiedz się, jak zainstalować stos hosta USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377088"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a>Rozdział 2 — Instalacja stosu hosta usługi Azure RTO USBX

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

### <a name="computer-type"></a>Typ komputera

Projektowanie osadzone jest zwykle wykonywane na komputerach hosta z systemem Windows lub UNIX. Gdy aplikacja zostanie skompilowana, połączona i umieszczona na hoście, zostanie pobrana na docelowy sprzęt do wykonania.

### <a name="download-interfaces"></a>Pobierz interfejsy

Zazwyczaj pobieranie docelowe odbywa się za pośrednictwem interfejsu szeregowego RS-232, chociaż interfejsy równoległe, USB i Ethernet są coraz bardziej popularne. Zobacz dokumentację narzędzia deweloperskiego, aby poznać dostępne opcje.

### <a name="debugging-tools"></a>Narzędzia debugowania

Debugowanie odbywa się zwykle nad tym samym łączem, co w przypadku pobierania obrazu programu. Istnieje wiele różnych debugerów, począwszy od małych programów monitorujących uruchomionych w miejscu docelowym za pomocą narzędzia Monitor debugowania w tle (BDM) i In-Circuit emulatora (lodem). Narzędzie do ELIMINACJi oprogramowania zapewnia najbardziej niezawodne debugowanie rzeczywistego sprzętu docelowego.

### <a name="required-hard-disk-space"></a>Wymagane miejsce na dysku twardym

Kod źródłowy dla USBX jest dostarczany w formacie ASCII i wymaga około 500 KB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące obiektów docelowych

USBX wymaga od 24 kilobajtów do 64 kilobajtów pamięci tylko do odczytu (ROM) w obszarze docelowym w trybie hosta. Wymagana ilość pamięci zależy od typu używanego kontrolera i klas USB połączonych z USBX. Do USBX globalnych struktur danych i puli pamięci wymagane są inne 32 kilobajty pamięci docelowej (RAM). Tę pulę pamięci można również dostosować w zależności od oczekiwanej liczby urządzeń USB i typu kontrolera USB. Po stronie urządzenia USBX wymagane jest około 10-12 K pamięci ROM w zależności od typu kontrolera urządzenia. Użycie pamięci RAM zależy od typu klasy emulowanej przez urządzenie.

USBX opiera się również na semaforach ThreadX, muteksach i wątkach na potrzeby ochrony wielu wątków oraz zawieszania operacji we/wy i okresowego przetwarzania dla monitorowania topologii magistrali USB.

### <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO USBX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/usbx/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium:

- ***ux_api. h***: ten plik nagłówka C zawiera wszystkie równe systemowe, struktury danych i prototypy usługi.
- ***ux_port. h***: ten plik nagłówkowy C zawiera wszystkie definicje i struktury danych specyficzne dla narzędzia deweloperskiego.
- ***UX. lib***: jest to wersja binarna biblioteki USBX C. Jest dystrybuowana z pakietem standardowym.
- ***demo_usbx. c***: plik c zawierający prostą wersję DEMONSTRACYJNą USBx

Wszystkie nazwy plików są małymi literami. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformę deweloperskią systemu UNIX.

## <a name="usbx-installation"></a>Instalacja USBX

USBX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium USBX na komputerze:

```powershell
    git clone https://github.com/azure-rtos/usbx
```

Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.

Znajdziesz również instrukcje dotyczące tworzenia biblioteki USBX na stronie frontonu repozytorium online.

Poniższe instrukcje ogólne dotyczą niemal każdej instalacji:

1. Użyj tego samego katalogu, w którym wcześniej zainstalowano ThreadX na dysku twardym hosta. Wszystkie nazwy USBX są unikatowe i nie zakłócają instalacji poprzedniej USBX.
2. Dodaj wywołanie do ***ux_system_initialize** _ lub blisko początku _ *_tx_application_define_.* * Jest to miejsce, w którym zainicjowano zasoby USBX.
3. Dodaj wywołanie do ***ux_host_stack_initialize *.**
4. Dodaj co najmniej jedno wywołanie, aby zainicjować wymagane USBX.
5. Dodaj co najmniej jedno wywołanie w celu zainicjowania kontrolerów hosta dostępnych w systemie.
6. Może być konieczne zmodyfikowanie pliku tx_low_level_initialize. c, aby dodać inicjalizację sprzętu niskiego poziomu i Routing wektora przerwania. Jest to specyficzne dla platformy sprzętowej i nie zostanie omówiona w tym miejscu.
7. Kompiluj kod źródłowy aplikacji i linki z bibliotekami czasu wykonywania USBX i ThreadX (FileX i/lub NetX mogą być również wymagane, jeśli Klasa magazynu USB i/lub klasy sieci USB mają być kompilowane), UX. a (lub UX. lib) i TX. a (lub TX. lib). Wyniki można pobrać do elementu docelowego i wykonać.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji do kompilowania biblioteki USBX. Wszystkie opcje znajdują się w ***ux_user. h***.

Poniższa lista zawiera szczegóły każdej opcji konfiguracji.


- **UX_PERIODIC_RATE**: Ta wartość reprezentuje liczbę taktów na sekundę dla określonej platformy sprzętowej. Wartość domyślna to 1000 wskazujący jeden takt na milisekund.
- **UX_MAX_CLASS_DRIVER**: Ta wartość to maksymalna liczba klas, które mogą być ładowane przez USBX. Ta wartość reprezentuje kontener klasy, a nie liczbę wystąpień klasy. Na przykład jeśli określona implementacja USBX wymaga klasy centrów, klasy drukarki i klasy magazynu, wartość UX_MAX_CLASS_DRIVER można ustawić na 3 niezależnie od liczby urządzeń należących do tych klas.
- **UX_MAX_HCD**: Ta wartość reprezentuje liczbę różnych kontrolerów hosta dostępnych w systemie. W przypadku obsługi USB 1,1 Ta wartość będzie w większości równa 1. Dla magistrali USB 2,0 ta wartość może być większa niż 1. Ta wartość reprezentuje liczbę współbieżnych kontrolerów hosta uruchomionych w tym samym czasie. Jeśli na przykład istnieją dwa wystąpienia z OHCI lub jeden EHCI i jeden kontroler OHCI z systemem, wartość UX_MAX_HCD powinna być ustawiona na 2. 
- **UX_MAX_DEVICES**: Ta wartość reprezentuje maksymalną liczbę urządzeń, które mogą być dołączone do portu USB. Zwykle teoretyczna maksymalna liczba na jednym urządzeniu USB to 127. Ta wartość może być skalowana w dół w celu zaoszczędność pamięci. Należy zauważyć, że ta wartość reprezentuje całkowitą liczbę urządzeń bez względu na liczbę magistrali USB w systemie.
- **UX_MAX_ED**: Ta wartość reprezentuje maksymalną liczbę raportów EDS w puli kontrolerów. Ta liczba jest przypisana tylko do jednego kontrolera. Jeśli istnieją wiele wystąpień kontrolerów, ta wartość jest używana przez poszczególne kontrolery.
- **UX_MAX_TD i UX_MAX_ISO_TD**: Ta wartość reprezentuje maksymalną liczbę Isochronous TDS w puli kontrolerów. Ta liczba jest przypisana tylko do jednego kontrolera. Jeśli istnieją wiele wystąpień kontrolerów, ta wartość jest używana przez poszczególne kontrolery.
- **UX_THREAD_STACK_SIZE**: wartość jest rozmiar stosu w bajtach dla wątków USBX. Może to być zwykle 1024 bajtów lub 2048 bajtów w zależności od używanego procesora i kontrolera hosta.
- **UX_HOST_ENUM_THREAD_STACK_SIZE**: wartość to rozmiar stosu dla wątku WYLICZENIA hosta USB. Jeśli ten symbol nie jest ustawiony, rozmiar stosu dla wątku wyliczenia hosta USBX jest ustawiony na **UX_THREAD_STACK_SIZE**. 
- **UX_HOST_HCD_THREAD_STACK_SIZE**: wartość to rozmiar stosu wątku HCD hosta USB. Jeśli ten symbol nie jest ustawiony, rozmiar stosu wątku HCD hosta USBX jest ustawiony na **UX_THREAD_STACK_SIZE**.
- **UX_THREAD_PRIORITY_ENUM**: jest to wartość priorytetu ThreadX dla wątków wyliczenia USBX, które monitorują topologię magistrali.
- **UX_THREAD_PRIORITY_CLASS**: jest to wartość priorytetu ThreadX dla standardowych wątków USBX.
- **UX_THREAD_PRIORITY_KEYBOARD**: jest to wartość priorytetu ThreadX dla klasy klawiatury HID USBX.
- **UX_THREAD_PRIORITY_HCD**: jest to wartość priorytetu ThreadX dla wątku kontrolera hosta.
- **UX_NO_TIME_SLICE**: Ta wartość w rzeczywistości definiuje wycinek czasu, który będzie używany dla wątków. Na przykład, jeśli określono wartość 0, port docelowy ThreadX nie korzysta z wycinków czasu.
- **UX_MAX_HOST_LUN**: Ta wartość reprezentuje maksymalną liczbę jednostek logicznych SCSI przedstawionych w sterowniku klasy magazynu hosta.
- **UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: Jeśli jest zdefiniowany, ta wartość obejmuje kod obsługujący urządzenia magazynujące korzystające z protokołu CB lub CBI (na przykład dyskietek). Jest ona domyślnie wyłączona, ponieważ te protokoły są przestarzałe i zastępowane przez transport tylko zbiorczy (protokół BOT, który praktycznie wszystkie nowoczesne urządzenia magazynujące używają.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: Jeśli jest zdefiniowana, ta wartość powoduje, że ux_host_class_hid_keyboard_key_get tylko do raportowania zmian kluczy, które są, naciśnięcia kluczy i wydań klawiszy. Domyślnie jest on raportowany tylko wtedy, gdy klucz nie działa.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: używany tylko wtedy, gdy **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowany. Jeśli jest zdefiniowany, powoduje, że ux_host_class_hid_keyboard_key_get tylko do zmian naciśniętego klucza raportu lub w dół. wydane klucze/zmiany nie są zgłaszane.
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: używany tylko wtedy, gdy **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowany. Jeśli jest zdefiniowany, powoduje, że ux_host_class_hid_keyboard_key_get do raportu zmiany klucza blokady (CapsLock/NumLock/ScrollLock).
- **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: używany tylko wtedy, gdy **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowany. Jeśli jest zdefiniowany, powoduje, że zmiany w ux_host_class_hid_keyboard_key_get na klucz modyfikujący raport (Ctrl/Alt/Shift/GUI).
- **UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: Jeśli jest zdefiniowana, ta wartość reprezentuje liczbę pakietów w klasie hosta przechwytywania zmian-ECM. Wartość domyślna to 16.

## <a name="source-code-tree"></a>Drzewo kodu źródłowego

Pliki USBX są dostępne w kilku katalogach.

![Drzewo kodu źródłowego](media/usbx-host-stack/source-code-tree.png)

Aby pliki były rozpoznawane według ich nazw, przyjęto następującą konwencję:

| Nazwa sufiksu pliku | Opis pliku                          |
| ---------------- | ----------------------------------------- |
| ux_host_stack    | podstawowe pliki stosu hosta USBx                |
| ux_host_class    | pliki klas stosu hosta USBx             |
| ux_hcd           | pliki sterowników kontrolera stosu hosta USBx   |
| ux_device_stack  | podstawowe pliki stosu urządzeń USBx              |
| ux_device_class  | pliki klas stosu urządzeń USBx           |
| ux_dcd           | pliki sterowników kontrolera stosu urządzeń USBx |
| ux_otg           | pliki powiązane z sterownikiem kontrolera OTG USBx  |
| ux_pictbridge    | Pliki USBx PictBridge                     |
| ux_utility       | funkcje narzędzia USBx                    |
| demo_usbx        | pliki demonstracyjne dla USBX              |

## <a name="initialization-of-usbx-resources"></a>Inicjowanie zasobów USBX

USBX ma własny Menedżer pamięci. Pamięć należy przydzielyć do USBX przed zainicjowaniem hosta lub po stronie urządzenia USBX. Menedżer pamięci USBX może obsługiwać systemy, w których pamięć może być buforowana.

Poniższa funkcja inicjuje zasoby pamięci USBX z 128Kem zwykłej pamięci i nie ma oddzielnej puli pamięci podręcznej w bezpiecznym miejscu:

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

Prototyp ux_system_initialize jest następujący.

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
- **cache_safe_memory_pool_start** Początek bezpiecznego buforowania pamięci podręcznej.
- **cache_safe_memory_size** Rozmiar bezpiecznej puli pamięci podręcznej.    |

Nie wszystkie systemy wymagają definicji bezpiecznej pamięci podręcznej. W takim systemie wartości przesyłane podczas inicjalizacji wskaźnika pamięci będą ustawione na UX_NULL i rozmiar puli do 0. Następnie USBX będzie używać zwykłej puli pamięci w miejsce pamięci podręcznej w bezpiecznej puli.

W systemie, w którym zwykła pamięć nie jest bezpieczna w pamięci podręcznej, a kontroler wymaga przeprowadzenia pamięci DMA (podobnie jak w przypadku OHCI, kontrolerów EHCI między innymi), konieczne jest zdefiniowanie puli pamięci w bezpiecznym obszarze pamięci podręcznej.

## <a name="uninitialization-of-usbx-resources"></a>Odinicjowanie zasobów USBX

USBX można przerwać, zwalniając jego zasoby. Przed zakończeniem USBx należy prawidłowo zakończyć wszystkie klasy i zasoby kontrolerów. Następująca funkcja nie inicjuje USBX zasobów pamięci:

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

Prototyp ux_system_initialize jest następujący.

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a>Definicja kontrolerów hosta USB

Należy zdefiniować co najmniej jeden kontroler hosta USB dla USBX do działania w trybie hosta. Plik inicjujący aplikacji powinien zawierać tę definicję. W poniższym wierszu jest wykonywana definicja ogólnego kontrolera hosta.

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

Ux_host_stack_hcd_register ma następujący prototyp.

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

Funkcja ux_host_stack_hcd_register ma następujące parametry.

- **hcd_name**: ciąg nazwy kontrolera
- **hcd_initialize_function**: Funkcja inicjowania kontrolera
- **hcd_param1**: zazwyczaj wartość operacji we/wy lub pamięć używana przez kontroler
- **hcd_param2**: zwykle przerwanie używane przez kontroler

W poprzednim przykładzie:

- "ux_hcd_controller" jest nazwą kontrolera
- "ux_hcd_controller_initialize" to procedura inicjowania kontrolera hosta
- 0xd0000 to adres, pod którym rejestry kontrolera hosta są widoczne w pamięci
- i 0x0A to PRZERWAnie używane przez kontroler hosta.

Poniżej znajduje się przykład inicjalizacji USBX w trybie hosta z jednym kontrolerem hosta i kilkoma klasami.

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

## <a name="definition-of-host-classes"></a>Definicja klas hosta

Należy zdefiniować co najmniej jedną klasę hosta z USBX. Klasa USB jest wymagana do podłączenia urządzenia USB po skonfigurowaniu urządzenia USB przez stos USB. Klasa USB jest specyficzna dla urządzenia. W zależności od liczby interfejsów zawartych w deskryptorach urządzeń USB może być wymagana co najmniej jedna Klasa.

Jest to przykład rejestracji klasy centrum.

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

Funkcja ux_host_class_register ma następujący prototyp.

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- **class_name** jest nazwą klasy
- **class_entry_address** jest punktem wejścia klasy

Przykład inicjowania klasy centrum:

- "ux_host_class_hub" jest nazwą klasy centrum
- ux_host_class_hub_entry jest punktem wejścia klasy centrum.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

USBX jest dostarczany z plikiem demonstracyjnym i środowiskiem symulacji. Zawsze dobrym pomysłem jest rozpoczęcie od pierwszego uruchomienia platformy demonstracyjnej — na sprzęcie docelowym lub na określonej platformie demonstracyjnej.

Jeśli system demonstracyjny nie działa, spróbuj wykonać następujące czynności, aby zawęzić problem.

## <a name="usbx-version-id"></a>Identyfikator wersji USBX

Bieżąca wersja programu USBX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji w czasie wykonywania. Programista może uzyskać wersję USBX z badania pliku ***ux_port. h** _. Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję USBX, badając ciąg globalny _ _ *_ux_version_id_* _, który jest zdefiniowany w _ *_ux_port. h_* *.
