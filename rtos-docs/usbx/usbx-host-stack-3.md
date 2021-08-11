---
title: Rozdział 3 — Składniki funkcjonalne stosu hosta USBX
description: Ten rozdział zawiera opis stosu hosta USBX embedded USB o wysokiej wydajności z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a3cbbb2e26d66d3db26144a47a1b6cbb11387c7b5b2ba5e19d35df026e5e3598
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790892"
---
# <a name="chapter-3---functional-components-of-usbx-host-stack"></a>Rozdział 3 — Składniki funkcjonalne stosu hosta USBX

Ten rozdział zawiera opis stosu hosta USBX embedded USB o wysokiej wydajności z perspektywy funkcjonalnej.

## <a name="execution-overview"></a>Omówienie wykonywania

Dysk USBX składa się z kilku składników:

- Inicjalizacja
- Wywołania interfejsu aplikacji
- Centrum główne
- Klasa koncentratora
- Klasy hostów
- Stos hosta USB
- Kontroler hosta

Na poniższym diagramie przedstawiono stos hosta USBX.

![Stos hosta USBX](./media/usbx-host-stack/usbx-host-stack.png)

### <a name="initialization"></a>Inicjalizacja

Aby można było aktywować usbx, ***należy ux_system_initialize*** funkcję. Ta funkcja inicjuje zasoby pamięci USBX.

Aby aktywować obiekty hosta USBX, należy ***ux_host_stack_initialize*** funkcję. Ta funkcja z kolei inicjuje wszystkie zasoby używane przez stos hosta USBX, takie jak wątki ThreadX, mutexes i semafory.

Do inicjowania aplikacji należy aktywowanie co najmniej jednego kontrolera hosta USB i co najmniej jednej klasy USB. Gdy klasy zostały zarejestrowane w stosie, a funkcja inicjowania kontrolerów hostów została wywołana, magistrala jest aktywna i można uruchomić odnajdywanie urządzeń. Jeśli główny koncentrator kontrolera hosta wykryje dołączone urządzenie, wątek wyliczenia USB odpowiedzialny za topologię USB zostanie wznowiony i przejdzie do wyliczenia urządzeń.

Ze względu na charakter koncentratora głównego i koncentratora podrzędnego istnieje możliwość, że wszystkie dołączone urządzenia USB mogą nie zostać całkowicie skonfigurowane po powrocie funkcji inicjowania kontrolera hosta. Wyliczenie wszystkich urządzeń USB może potrwać kilka sekund, zwłaszcza jeśli między koncentratorem głównym a urządzeniem USB znajduje się co najmniej jeden koncentrator.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Istnieją dwa poziomy interfejsów API w USBX.

- Interfejsy API stosu hosta USB
- Interfejsy API klas hostów USB

Zwykle aplikacja USBX nie powinna wymagać wywołania żadnej funkcji interfejsu API stosu hosta USB. Większość aplikacji będzie mieć dostęp tylko do funkcji interfejsu API klasy USB.

### <a name="usb-host-stack-apis"></a>Interfejsy API stosu hosta USB

Funkcje interfejsu API stosu hosta są odpowiedzialne za rejestrację składników USBX (klas hostów i kontrolerów hostów), konfigurację urządzeń i żądania transferu dla dostępnych punktów końcowych urządzenia.

### <a name="usb-host-class-api"></a>Interfejs API klasy hosta USB

Interfejsy API klas są bardzo specyficzne dla każdej klasy USB. Większość typowych funkcji interfejsu API dla klas USB zapewnia usługi, takie jak otwieranie/zamykanie urządzenia oraz odczytywanie z i zapisywanie na urządzeniu.

### <a name="root-hub"></a>Centrum główne

Każde wystąpienie kontrolera hosta ma co najmniej jeden koncentrator główny USB. Liczba centrów głównych jest określana przez charakter kontrolera lub może zostać pobrana przez odczytanie określonych rejestrów z kontrolera.

### <a name="hub-class"></a>Klasa koncentratora

Klasa koncentratora jest odpowiedzialny za kierowanie koncentratorami USB. Koncentrator USB może być autonomicznym koncentratorem lub jako część złożonego urządzenia, takiego jak klawiatura lub monitor. Koncentrator może być samodzielny lub oparty na magistrali. Koncentratory oparte na magistrali mają maksymalnie cztery porty podrzędne i mogą zezwalać tylko na połączenia urządzeń, które są urządzeniami z własnym zasilaniem lub magistralą, które używają mocy mniejszej niż 100 mA. Koncentratory mogą być kaskadowo. Można połączyć ze sobą maksymalnie pięć koncentratorów.

### <a name="usb-host-stack"></a>Stos hosta USB

Stos hosta USB jest środkowym USBX. Ma trzy główne funkcje.

- Zarządzanie topologią dysku USB.
- Powiąż urządzenie USB z co najmniej jedną klasą.
- Udostępnij klasom interfejs API do wykonywania interskrypcji deskryptora urządzeń i transferów USB.

### <a name="topology-manager"></a>Topology Manager

Wątek topologii stosu USB jest odsłaniany po podłączeniu nowego urządzenia lub odłączeniu urządzenia. Centrum główne lub zwykłe centrum mogą akceptować połączenia urządzeń. Po podłączeniu urządzenia do portu USB menedżer topologii pobierze deskryptor urządzenia. Ten deskryptor będzie zawierać liczbę możliwych konfiguracji dostępnych dla tego urządzenia. Większość urządzeń ma tylko jedną konfigurację. Niektóre urządzenia mogą działać inaczej w zależności od dostępnego zasilania na porcie, na którym jest podłączone. W takim przypadku urządzenie będzie mieć wiele konfiguracji, które można wybrać w zależności od dostępnego zasilania. Po skonfigurowaniu urządzenia przez menedżera topologii może ono rysować ilość energii określoną w deskryptorze konfiguracji.

## <a name="usb-class-binding"></a>Powiązanie klasy USB

Po skonfigurowaniu urządzenia menedżer topologii umożliwia menedżerowi klas kontynuowanie odnajdywania urządzeń, patrząc na deskryptory interfejsu urządzenia. Urządzenie może mieć co najmniej jeden deskryptor interfejsu.

Interfejs reprezentuje funkcję w urządzeniu. Na przykład głośnik USB ma trzy interfejsy: jeden do przesyłania strumieniowego audio, jeden do sterowania dźwiękami i jeden do zarządzania różnymi przyciskami osoby mówiącej.

Menedżer klas ma dwa mechanizmy dołączania interfejsów urządzeń do co najmniej jednej klasy. Można użyć kombinacji identyfikatora PID/VID (identyfikatora produktu i identyfikatora dostawcy) znalezionego w deskryptorze interfejsu lub kombinacji klasy/podklasy/protokołu.

Kombinacja PID/VID jest prawidłowa dla interfejsów, które nie mogą być sterowane przez klasę ogólną. Kombinacja klasy/podklasy/protokołu jest używana przez interfejsy należące do certyfikowanej klasy USB-IF, takiej jak drukarka, koncentrator, magazyn, dźwięk lub HID.

Menedżer klas zawiera listę zarejestrowanych klas z inicjowania USBX. Menedżer klas będzie wywołać każdą klasę po jednej na raz, dopóki jedna klasa nie zaakceptuje zarządzania interfejsem dla tego urządzenia. Klasa może zarządzać tylko jednym interfejsem. W przypadku przykładu głośnika audio USB menedżer klas wywoła wszystkie klasy dla każdego z interfejsów.

Gdy klasa zaakceptuje interfejs, tworzone jest nowe wystąpienie tej klasy. Menedżer klas wyszuka następnie domyślne alternatywne ustawienie interfejsu. Urządzenie może mieć jedno lub więcej alternatywnych ustawień dla każdego interfejsu. Alternatywne ustawienie 0 będzie włączone domyślnie używane, dopóki klasa nie zdecyduje się go zmienić.

W przypadku domyślnego ustawienia alternatywnego menedżer klas zainstaluje wszystkie punkty końcowe zawarte w ustawieniu alternatywnym. Jeśli instalowanie każdego punktu końcowego zakończy się powodzeniem, menedżer klas zakończy zadanie, wracając do klasy, która zakończy inicjowanie interfejsu.

### <a name="usbx-apis"></a>Interfejsy API USBX

Stos USB eksportuje pewną liczbę interfejsów API dla klas USB do wykonywania interrogacji na urządzeniu i transferów USB w określonych punktach końcowych. Te funkcje interfejsu API zostały szczegółowo opisane w tym podręczniku.

### <a name="host-controller"></a>Kontroler hosta

Sterownik kontrolera hosta jest odpowiedzialny za prowadzenie określonego typu kontrolera USB. Kontroler hosta USB może mieć wiele kontrolerów wewnątrz. Na przykład niektóre mikroukłady komputera Intel zawierają dwa kontrolery UHCI. Niektóre kontrolery USB 2.0 zawierają wiele wystąpień kontrolera OHCI oprócz jednego wystąpienia kontrolera EHCI.

Kontroler hosta będzie zarządzać wieloma wystąpieniami tego samego kontrolera. W celu sterowania większość kontrolerów hosta USB 2.0, będzie wymagane do zainicjowania zarówno kontroler OCHI i kontroler EHCI podczas inicjowania USBX.

Kontroler hosta jest odpowiedzialny za zarządzanie następującymi.

- Centrum główne
- Zarządzanie energią
- Punkty końcowe
- Transfery

### <a name="root-hub"></a>Centrum główne

Zarządzanie koncentratorem głównym jest odpowiedzialne za zasilanie każdego portu kontrolera i określenie, czy urządzenie zostało wstawione, czy nie. Ta funkcja jest używana przez ogólny koncentrator główny USBX do interrogacji portów podrzędnego kontrolera.

### <a name="power-management"></a>Zarządzanie energią

Przetwarzanie zarządzania energią zapewnia obsługę wstrzymania/wznowienia sygnałów w trybie bandy, w związku z tym wpływa na wszystkie porty podrzędne kontrolera w tym samym czasie lub indywidualnie, jeśli kontroler oferuje tę funkcję.

### <a name="endpoints"></a>Punkty końcowe

Zarządzanie punktami końcowymi umożliwia tworzenie lub niszczenie fizycznych punktów końcowych na kontrolerze. Fizyczne punkty końcowe to jednostki pamięci, które są analizowane przez kontroler, jeśli kontroler obsługuje główny program DMA lub są zapisywane w kontrolerze. Fizyczne punkty końcowe zawierają informacje o transakcjach, które mają być wykonywane przez kontroler.

### <a name="transfers"></a>Transfery

Zarządzanie transferem umożliwia klasie wykonywanie transakcji na każdym z utworzonych punktów końcowych. Każdy logiczny punkt końcowy zawiera składnik o nazwie ŻĄDANIE TRANSFERU dla żądań transferu USB. Żądanie transferu jest używany przez stos do opisywania transakcji. To żądanie transferu jest następnie przekazywane do stosu i do kontrolera, który może podzielić go na kilka transakcji sub w zależności od możliwości kontrolera.

## <a name="usb-device-framework"></a>USB Device Framework

Urządzenie USB jest reprezentowane przez drzewo deskryptorów. Istnieje sześć głównych typów deskryptorów.

- Deskryptory urządzeń
- Deskryptory konfiguracji
- Deskryptory interfejsu
- Deskryptory punktów końcowych
- Deskryptory ciągów
- Deskryptory funkcjonalne

Urządzenie USB może mieć bardzo prosty opis i wygląda następująco.
![Proste urządzenie USB](./media/usbx-host-stack/usb-device-simple.png)

Na powyższej ilustracji urządzenie ma tylko jedną konfigurację. Do tej konfiguracji jest dołączony jeden interfejs wskazujący, że urządzenie ma tylko jedną funkcję i ma tylko jeden punkt końcowy. Dołączony do deskryptora urządzenia jest deskryptorem ciągu zapewniającym widoczną identyfikację urządzenia.

Jednak urządzenie może być bardziej złożone i może wyglądać w następujący sposób.

![Złożone urządzenie USB](./media/usbx-host-stack/usb-device-complex.png)

Na powyższej ilustracji urządzenie ma dwa deskryptory konfiguracji dołączone do deskryptora urządzenia. To urządzenie może wskazywać, że ma dwa tryby zasilania lub może być sterowane przez klasy standardowe lub zastrzeżone.

Dołączone do pierwszej konfiguracji są dwa interfejsy wskazujące, że urządzenie ma dwie funkcje logiczne. Pierwsza funkcja ma 3 deskryptory punktu końcowego i funkcjonalny deskryptor. Deskryptor funkcjonalny może być używany przez klasę odpowiedzialną za obsługę interfejsu w celu uzyskania dalszych informacji o tym interfejsie zwykle nie odnalezionych przez deskryptor ogólny.

### <a name="device-descriptors"></a>Deskryptory urządzeń

Każde urządzenie USB ma jeden deskryptor urządzenia. Ten deskryptor zawiera identyfikację urządzenia, liczbę obsługiwanych konfiguracji oraz charakterystykę domyślnego punktu końcowego sterowania używanego do konfigurowania urządzenia.

| Przesunięcie | Pole              | Rozmiar | Wartość    | Opis                             |
| ------ | ------------------ | ---- | -------- | --------------------------------------- |
| 0      | BLength            | 1    | Liczba   | Rozmiar tego deskryptora w bajtach |
| 1      | bDescriptorType    | 1    | Stała | Typ deskryptora URZĄDZENIA |
| 2      | bcdUSB             | 2    | Bcd      | Numer wydania specyfikacji USB w pliku BinaryCoded dec<br />Przykład: 2.10 jest odpowiednikiem 0x210. To pole określa wydanie specyfikacji USB, z które urządzenie i jego deskryptory są zgodne. |
| 4      | bDeviceClass       | 1    | Klasa    | Kod klasy (przypisany przez USB-IF).<br />Jeśli to pole zostanie zresetowane do wartości 0, każdy interfejs w konfiguracji określa własne informacje o klasie, a różne interfejsy działają niezależnie.<br />Jeśli to pole jest ustawione na wartość z zakresu od 1 do 0xFE, urządzenie obsługuje różne specyfikacje klas w różnych interfejsach i interfejsy mogą nie działać niezależnie. Ta wartość identyfikuje definicję klasy używaną dla interfejsów agregowania.<br />Jeśli to pole jest ustawione na 0xFF, klasa urządzenia jest specyficzna dla dostawcy. |
| 5      | bDeviceSubClass    | 1    | Podklasy | Kod podklasy (przypisany przez USB-IF).<br />Te kody są kwalifikowane przez wartość pola bDeviceClass. Jeśli pole bDeviceClass jest resetowane do 0, to pole musi być również zresetowane do 0. Jeśli pole bDeviceClass nie jest ustawione na wartość 0xFF, wszystkie wartości są zarezerwowane do przypisania przez USB. |
| 6      | bDeviceProtocol    | 1    | Protokół | Kod protokołu (przypisany przez USB-IF).<br />Te kody są kwalifikowane według wartości pól bDeviceClass i bDeviceSubClass. Jeśli urządzenie obsługuje protokoły specyficzne dla klasy na podstawie urządzenia, a nie interfejsu, ten kod identyfikuje protokoły używane przez urządzenie zgodnie ze specyfikacją klasy urządzenia. Jeśli to pole zostanie zresetowane do wartości 0, urządzenie nie będzie używać protokołów specyficznych dla klasy na podstawie urządzenia.<br />Może jednak używać protokołów specyficznych dla klasy na podstawie interfejsu.<br />Jeśli to pole jest ustawione na wartość 0xFF, urządzenie używa protokołu specyficznego dla dostawcy na podstawie urządzenia. |
| 7      | bMaxPacketSize0    | 1    | Liczba   | Maksymalny rozmiar pakietu dla punktu końcowego zero (prawidłowe są tylko rozmiary bajtów 8, 16, 32 lub 64) |
| 8      | idVendor           | 2    | ID (Identyfikator)       | Identyfikator dostawcy (przypisany przez USB-IF) |
| 10     | idProduct          | 2    | ID (Identyfikator)       | Identyfikator produktu (przypisany przez producenta) |
| 12     | bcdDevice          | 2    | Bcd      | Numer wydania urządzenia z kodem binarnym dziesiętnym |
| 14     | iManufacturer      | 1    | Indeks    | Indeks deskryptora ciągu opisującego producenta |
| 15     | iProduct (iProduct)           | 1    | Indeks    | Indeks deskryptora ciągów opisujących produkt |
| 16     | iSerialNumbe       | 1    | Indeks    | Indeks deskryptora ciągów opisujących numer seryjny urządzenia |
| 17     | bNumConfigurations | 1    | Liczba   | Liczba możliwych konfiguracji |

USBX definiuje deskryptor urządzenia USB w następujący sposób:

```c
typedef struct UX_DEVICE_DESCRIPTOR_STRUCT
{
    UINT      bLength;
    UINT      bDescriptorType;
    USHORT    bcdUSB;
    UINT      bDeviceClass;
    UINT      bDeviceSubClass;
    UINT      bDeviceProtocol;
    UINT      bMaxPacketSize0;
    USHORT    idVendor;
    USHORT    idProduct;
    USHORT    bcdDevice;
    UINT      iManufacturer;
    UINT      iProduct;
    UINT      iSerialNumber;
    UINT      bNumConfigurations;
} UX_DEVICE_DESCRIPTOR;
```

Deskryptor urządzenia USB jest częścią kontenera urządzenia opisanego jako:

```c
typedef struct UX_DEVICE_STRUCT
{
    ULONG ux_device_handle;
    ULONG ux_device_type;
    ULONG ux_device_state;
    ULONG ux_device_address;
    ULONG ux_device_speed;
    ULONG ux_device_port_location;
    ULONG ux_device_max_power;
    ULONG ux_device_power_source;
    UINT ux_device_current_configuration;

    TX_SEMAPHORE ux_device_protection_semaphore;
    struct UX_DEVICE_STRUCT *ux_device_parent; 
    struct UX_HOST_CLASS_STRUCT *ux_device_class; 
    VOID *ux_device_class_instance;
    struct UX_HCD_STRUCT *ux_device_hcd;
    struct UX_CONFIGURATION_STRUCT *ux_device_first_configuration; 
    struct UX_DEVICE_STRUCT *ux_device_next_device;
    struct UX_DEVICE_DESCRIPTOR_STRUCT ux_device_descriptor;
    struct UX_ENDPOINT_STRUCT ux_device_control_endpoint;
    struct UX_HUB_TT_STRUCT ux_device_hub_tt[UX_MAX_TT];
} UX_DEVICE;
```

- **ux_device_handle:** Uchwyt urządzenia. Zazwyczaj jest to adres wystąpienia tej struktury dla urządzenia.
- **ux_device_type:** Przestarzała wartość. Nieużywany.
- **ux_device_state:** Stan urządzenia, które może mieć jedną z następujących wartości:
    - **UX_DEVICE_RESET**                0
    - **UX_DEVICE_ATTACHED**             1
    - **UX_DEVICE_ADDRESSED**            2
    - **UX_DEVICE_CONFIGURED**           3
    - **UX_DEVICE_SUSPENDED**            4
    - **UX_DEVICE_RESUMED**              5
    - **UX_DEVICE_SELF_POWERED_STATE**   6
    - **UX_DEVICE_SELF_POWERED_STATE**   7
    - **UX_DEVICE_REMOTE_WAKEUP**        8
    - **UX_DEVICE_BUS_RESET_COMPLETED**  9
    - **UX_DEVICE_REMOVED**              10
    - **UX_DEVICE_FORCE_DISCONNECT**     11
- **ux_device_address:** adres urządzenia po zaakceptowaniu **polecenia SET_ADDRESS** (od 1 do 127).
- **ux_device_speed:** szybkość urządzenia:
    - **UX_LOW_SPEED_DEVICE**      0
    - **UX_FULL_SPEED_DEVICE**     1
    - **UX_HIGH_SPEED_DEVICE**     2
- **ux_device_port_location:** indeks portu urządzenia nadrzędnego (głównego centrum lub koncentratora).
- **ux_device_max_power:** maksymalna moc w menedżerze mA, która może zająć urządzenie w wybranej konfiguracji.
- **ux_device_power_source:** może być jedną z dwóch następujących wartości:
    - **UX_DEVICE_BUS_POWERED**     1
    - **UX_DEVICE_SELF_POWERED**    2
- **ux_device_current_configuration:** indeks bieżącej konfiguracji używanej przez to urządzenie.
- **ux_device_parent:** wskaźnik kontenera urządzenia elementu nadrzędnego tego urządzenia. Jeśli wskaźnik ma wartość null, element nadrzędny jest głównym koncentratorem kontrolera.
- **ux_device_class:** wskaźnik do typu klasy, który jest właścicielem tego urządzenia.
- **ux_device_class_instance:** wskaźnik do wystąpienia klasy, która jest właścicielem tego urządzenia.
- **ux_device_hcd:** wystąpienie kontrolera hosta USB, do którego to urządzenie jest dołączone.
- **ux_device_first_configuration:** Wskaźnik do pierwszego kontenera konfiguracji dla tego urządzenia.
- **ux_device_next_device:** wskaźnik do następnego urządzenia na liście urządzeń na dowolnym busie wykrytym przez USBX.
- **ux_device_descriptor:** deskryptor urządzenia USB.
- **ux_device_control_endpoint:** Deskryptor domyślnego punktu końcowego kontrolki używanego przez to urządzenie.
- **ux_device_hub_tt:** tablica węzłów TS centrum dla urządzenia

### <a name="configuration-descriptors"></a>Deskryptory konfiguracji

Deskryptor konfiguracji opisuje informacje o określonej konfiguracji urządzenia. Urządzenie USB może zawierać co najmniej jeden deskryptor konfiguracji. Pole **bNumConfigurations** w deskryptorze urządzenia wskazuje liczbę deskryptorów konfiguracji. Deskryptor zawiera pole **bConfigurationValue** z wartością, która po użyciu jako parametru żądania Ustaw konfigurację powoduje, że urządzenie przyjmuje opisaną konfigurację.

Deskryptor opisuje liczbę interfejsów dostarczonych przez konfigurację. Każdy interfejs reprezentuje funkcję logiczną w urządzeniu i może działać niezależnie. Na przykład głośnik audio USB może mieć trzy interfejsy: jeden do przesyłania strumieniowego audio, jeden do sterowania dźwiękami i jeden interfejs HID do zarządzania przyciskami osoby mówiącej.

Gdy host wydaje żądanie GET_DESCRIPTOR deskryptora konfiguracji, zwracane są wszystkie powiązane deskryptory interfejsu i punktu końcowego.

| Przesunięcie | Pole               | Rozmiar | Wartość    | Opis                       |
| ------ | ------------------- | ---- | -------- | --------------------------------- |
| 0      | bLength             | 1    | Liczba   | Rozmiar tego deskryptora w bajtach. |
| 1      | bDescriptorType     | 1    | Stała | KONFIGURACJA                     |
| 2      | wTotalLength        | 2    | Liczba   | Łączna długość danych zwracanych dla tej konfiguracji. Zawiera łączona długość wszystkich deskryptorów (konfiguracji, interfejsu, punktu końcowego i klasy lub dostawcy) zwróconych dla tej konfiguracji. |
| 4      | bNumInterfaces      | 1    | Liczba   | Liczba interfejsów obsługiwanych przez tę konfigurację. |
| 5      | bConfigurationValue | 1    | Liczba   | Wartość do użycia jako argument do ustawienia<br/>Konfiguracja w celu wybrania tej konfiguracji. |
| 6      | iConfiguration      | 1    | Indeks    | Indeks deskryptora ciągów opisujący tę konfigurację. |
| 7      | bMAttributes        | 1    | Bitmapy   | Charakterystyka konfiguracji Obsługiwane przez magistralę D7<br />D6 z samodzielnym zasilaniem<br />Zdalne wznawianie D5<br />D4. 0 Zarezerwowane (resetowanie do 0)<br />Konfiguracja urządzenia, która używa zasilania z magistrali i lokalnego źródła, ustawia zarówno D7, jak i D6. Rzeczywiste źródło zasilania w czasie wykonywania można określić przy użyciu żądania urządzenia Pobierz stan.<br />Jeśli konfiguracja urządzenia obsługuje zdalne wznawianie, dla opcji D5 ustawiono wartość 1. |
| 8      | MaxPower            | 1    | mA       | Maksymalne zużycie energii przez urządzenie USB z magistrali w tej konkretnej konfiguracji, gdy urządzenie jest w pełni operacyjne.<br />Wyrażona w 2 jednostkach mA (np. 50 = 100 mA).<br />Uwaga: Konfiguracja urządzenia informuje o tym, czy konfiguracja jest samodzielnie czy samodzielnie zasilana z magistrali.<br />Stan urządzenia informuje o tym, czy urządzenie jest obecnie zasilane samodzielnie. Jeśli urządzenie zostanie odłączone od zewnętrznego źródła zasilania, aktualizuje stan urządzenia, aby wskazać, że nie jest już zasilane samodzielnie. |

USBX definiuje deskryptor konfiguracji USB w następujący sposób.

```c
typedef struct UX_CONFIGURATION_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT wTotalLength;
    UINT bNumInterfaces;
    UINT bConfigurationValue;
    UINT iConfiguration;
    UINT bmAttributes;
    UINT MaxPower;
} UX_CONFIGURATION_DESCRIPTOR;
```

Deskryptor konfiguracji USB jest częścią kontenera konfiguracji opisanego poniżej.

```c
typedef struct UX_CONFIGURATION_STRUCT
{
    ULONG ux_configuration_handle;
    ULONG ux_configuration_state;
    struct UX_CONFIGURATION_DESCRIPTOR_STRUCT ux_configuration_descriptor;
    struct UX_INTERFACE_STRUCT *ux_configuration_first_interface;
    struct UX_CONFIGURATION_STRUCT *ux_configuration_next_configuration;
    struct UX_DEVICE_STRUCT *ux_configuration_device;
} UX_CONFIGURATION;
```

- **ux_configuration_handle:** Obsługa konfiguracji. Zazwyczaj jest to adres wystąpienia tej struktury dla konfiguracji.
- **ux_configuration_state:** stan konfiguracji.
- **ux_configuration_descriptor:** deskryptor urządzenia USB.
- **ux_configuration_first_interface:** wskaźnik do pierwszego interfejsu dla tej konfiguracji.
- **ux_configuration_next_configuration:** Wskaźnik do następnej konfiguracji dla tego samego urządzenia.
- **ux_configuration_device:** wskaźnik do właściciela urządzenia tej konfiguracji.

### <a name="interface-descriptors"></a>Deskryptory interfejsu

Deskryptor interfejsu opisuje określony interfejs w ramach konfiguracji. Interfejs jest funkcją logiczną w urządzeniu USB. Konfiguracja udostępnia jeden lub więcej interfejsów, z których każdy ma zero lub więcej deskryptorów punktów końcowych opisujących unikatowy zestaw punktów końcowych w ramach konfiguracji. Jeśli konfiguracja obsługuje więcej niż jeden interfejs, deskryptory punktu końcowego dla określonego interfejsu postępują zgodnie z deskryptorem interfejsu w danych zwracanych przez żądanie GET_DESCRIPTOR **dla** określonej konfiguracji.

Deskryptor interfejsu jest zawsze zwracany jako część deskryptora konfiguracji. Deskryptor interfejsu nie może uzyskać bezpośredniego dostępu przez żądanie GET_DESCRIPTOR interfejsu.

Interfejs może zawierać ustawienia alternatywne, które umożliwiają zmianę punktów końcowych i/lub ich cech po skonfigurowaniu urządzenia. Domyślnym ustawieniem interfejsu jest zawsze alternatywne ustawienie o wartości zero. Klasa może zmienić bieżące alternatywne ustawienie, aby zmienić zachowanie interfejsu i charakterystykę skojarzonych punktów końcowych. Żądanie SET_INTERFACE służy do wybierania ustawienia alternatywnego lub do powrotu do ustawienia domyślnego.

Ustawienia alternatywne umożliwiają zmianę części konfiguracji urządzenia, podczas gdy inne interfejsy pozostają w działaniu. Jeśli konfiguracja ma alternatywne ustawienia dla co najmniej jednego interfejsu, dla każdego ustawienia jest dołączony oddzielny deskryptor interfejsu i skojarzone z nim punkty końcowe.

Jeśli konfiguracja urządzenia zawiera jeden interfejs z dwoma alternatywnymi ustawieniami, żądanie GET_DESCRIPTOR konfiguracji zwróci deskryptor konfiguracji, następnie deskryptor interfejsu z polami **bInterfaceNumber** i **bAlternateSetting** ustawionymi na zero, a następnie deskryptory punktu końcowego dla tego ustawienia, a następnie inny deskryptor interfejsu i skojarzone z nim deskryptory punktu końcowego. Pole **bInterfaceNumber** drugiego deskryptora interfejsu również miałoby wartość zero, ale pole **bAlternateSetting** drugiego deskryptora interfejsu miałoby wartość 1, co wskazuje, że to alternatywne ustawienie należy do pierwszego interfejsu.

Z interfejsem mogą nie być skojarzone żadne punkty końcowe. W takim przypadku tylko domyślny punkt końcowy kontrolki jest prawidłowy dla tego interfejsu.

Ustawienia alternatywne są używane głównie do zmiany żądanej przepustowości dla okresowych punktów końcowych skojarzonych z interfejsem. Na przykład interfejs przesyłania strumieniowego usb powinien mieć pierwsze alternatywne ustawienie z zapotrzebowaniem na przepustowość 0 na jego izochroniczny punkt końcowy. Inne ustawienia alternatywne mogą wybrać różne wymagania dotyczące przepustowości w zależności od częstotliwości przesyłania strumieniowego dźwięku.

Deskryptor USB interfejsu jest następujący:

| Przesunięcie | Pole              | Rozmiar | Wartość     | Deskryptora                              |
| ------ | ------------------ | ---- | --------- | --------------------------------------- |
| 0      | bLength            | 1    | Liczba    | Rozmiar tego deskryptora w bajtach.       |
| 1      | bDescriptorType    | 1    | Stała  | Typ deskryptora INTERFEJSU               |
| 2      | bInterfaceNumber   | 1    | Liczba    | Liczba interfejsów. Wartość od zera identyfikująca indeks w tablicy współbieżnych interfejsów obsługiwanych przez tę konfigurację. |
| 3      | bAltenateSetting   | 1    | Liczba    | Wartość używana do wybierania alternatywnego ustawienia dla interfejsu zidentyfikowanego w wcześniejszym polu. |
| 4      | bNumEndpoints      | 1    | Liczba    | Liczba punktów końcowych używanych przez ten interfejs (z wyjątkiem punktu końcowego zero). Jeśli ta wartość wynosi 0, ten interfejs używa tylko punktu końcowego zero. |
| 5      | bInterfaceClass    | 1    | Klasa     | Kod klasy (przypisany przez USB)<br />Jeśli to pole zostanie zresetowane do wartości 0, interfejs nie należy do żadnej klasy urządzeń określonej przez port USB.<br />Jeśli to pole jest ustawione na 0xFF, klasa interfejsu jest specyficzna dla dostawcy.<br />Wszystkie inne wartości są zarezerwowane do przypisania przez port USB. |
| 6      | bInterfaceSubClass | 1    | Podklasy  | Kod podklasy (przypisany przez USB).<br />Te kody są kwalifikowane przez wartość pola bInterfaceClass. Jeśli pole bInterfaceClass jest resetowane do 0, to pole musi być również zresetowane do 0. Jeśli pole bInterfaceClass nie jest ustawione na wartość 0xFF, wszystkie wartości są zarezerwowane do przypisania przez USB. |
| 7      | bInterfaceProtocol | 1    | Protokół  | Kod protokołu (przypisany przez USB). Te kody są kwalifikowane według wartości pól bInterfaceClass i bInterfaceSubClass. Jeśli interfejs obsługuje żądania specyficzne dla klasy, ten kod identyfikuje protokoły używane przez urządzenie zgodnie ze specyfikacją klasy urządzenia.<br />Jeśli to pole zostanie zresetowane do wartości 0, urządzenie nie będzie używać protokołu specyficznego dla klasy w tym interfejsie. Jeśli to pole jest ustawione na wartość 0xFF, dla tego interfejsu urządzenie używa protokołu specyficznego dla dostawcy. |
| 8      | Iinterface         | 1    | Indeks     | Indeks deskryptora ciągów opisujący ten interfejs. |

USBX definiuje deskryptor interfejsu USB w następujący sposób.

```c
typedef struct UX_INTERFACE_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bInterfaceNumber;
    UINT bAlternateSetting;
    UINT bNumEndpoints;
    UINT bInterfaceClass
    UINT bInterfaceSubClass;
    UINT bInterfaceProtocol;
    UINT iInterface;
} UX_INTERFACE_DESCRIPTOR;
```

Deskryptor interfejsu USB jest częścią kontenera interfejsu opisanego w następujący sposób.

```c
typedef struct UX_INTERFACE_STRUCT
{
    ULONG ux_interface_handle;
    ULONG ux_interface_state;
    ULONG ux_interface_current_alternate_setting;
    struct UX_INTERFACE_DESCRIPTOR_STRUCT ux_interface_descriptor;
    struct UX_HOST_CLASS_STRUCT    *ux_interface_class;
    VOID    *ux_interface_class_instance;
    struct UX_ENDPOINT_STRUCT    *ux_interface_first_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_interface_next_interface;
    struct UX_CONFIGURATION_STRUCT    *ux_interface_configuration;
} UX_INTERFACE;
```

- **ux_interface_handle:** Dojście do interfejsu. Zazwyczaj jest to adres wystąpienia tej struktury dla interfejsu.
- **ux_interface_state:** stan interfejsu.
- **ux_interface_descriptor:** deskryptor interfejsu USB.
- **ux_interface_class:** wskaźnik do typu klasy, który jest właścicielem tego interfejsu.
- **ux_interface_class_instance:** wskaźnik do wystąpienia klasy, która jest właścicielem tego interfejsu.
- **ux_interface_first_endpoint:** Wskaźnik do pierwszego punktu końcowego zarejestrowanego w tym interfejsie.
- **ux_interface_next_interface:** wskaźnik do następnego interfejsu skojarzonego z konfiguracją.
- **ux_interface_configuration:** wskaźnik do właściciela konfiguracji tego interfejsu.

### <a name="endpoint-descriptors"></a>Deskryptory punktów końcowych

Każdy punkt końcowy skojarzony z interfejsem ma własny deskryptor punktu końcowego. Ten deskryptor zawiera informacje wymagane przez stos hosta do określenia wymagań dotyczących przepustowości poszczególnych punktów końcowych, maksymalnego ładunku skojarzonego z punktem końcowym, jego okresowości i kierunku. Deskryptor punktu końcowego jest zawsze zwracany przez GET_DESCRIPTOR polecenia konfiguracji.

Domyślny punkt końcowy kontroli skojarzony z deskryptorem urządzenia nie jest liczony jako część punktów końcowych skojarzonych z interfejsem i dlatego nie jest zwracany w tym deskryptorze.

Gdy oprogramowanie hosta żąda zmiany alternatywnego ustawienia interfejsu, wszystkie skojarzone punkty końcowe i ich zasoby USB są modyfikowane zgodnie z nowym ustawieniem alternatywnym.

Z wyjątkiem domyślnych punktów końcowych kontroli punkty końcowe nie mogą być współużytkują między interfejsami.

| Przesunięcie | Pole            | Rozmiar | Wartość    | Opis                       |
| ------ | ---------------- | ---- | -------- | --------------------------------- |
| 0      | bLength          | 1    | Liczba   | Rozmiar tego deskryptora w bajtach. |
| 1      | bDescriptorType  | 1    | Stała | Typ deskryptora punktu końcowego. |
| 2      | bEndpointAddress | 1    | Punkt końcowy | Adres punktu końcowego na urządzeniu USB opisany przez ten deskryptor. Adres jest kodowany w następujący sposób:<br />Bit 3...0: Numer punktu końcowego<br />Bit 6...4: Zarezerwowane, resetowanie do zera<br />Bit 7. Kierunek, ignorowany dla punktów końcowych kontroli<br />0 = punkt końcowy OUT<br />1 = punkt końcowy IN |
| 3      | bmAttributes     | 1    | Bitmapy   | W tym polu opisano atrybuty punktu końcowego, gdy jest on konfigurowany przy użyciu **pola bConfigurationValue.** Bity 1..0: typ transferu<br />00 = Kontrolka<br />01 = izochroniczne<br />10 = zbiorcze<br />11 = Przerwanie<br />Jeśli nie jest to izochroniczny punkt końcowy, bity 5..2 są zarezerwowane i muszą być ustawione na zero. W przypadku izochroniczne są one zdefiniowane w następujący sposób:<br />Bity 3..2: typ synchronizacji<br />00 = Brak synchronizacji<br />01 = Asynchroniczne<br />10 = adaptacyjne<br />11 = synchroniczne<br />Bity 5..4: typ użycia<br />00 = Punkt końcowy danych<br />01 = Punkt końcowy opinii<br />10 = niejawny punkt końcowy danych opinii<br />11 = Zarezerwowane |
| 4      | wMaxPacketSize   | 2    | Liczba   | Maksymalny rozmiar pakietu, który ten punkt końcowy może wysyłać lub odbierać po wybraniu tej konfiguracji.<br />W przypadku izochronnych punktów końcowych ta wartość jest używana do zarezerwowania czasu magistrali w harmonogramie, wymaganego dla ładunków danych ramek dla per-(micro)frame. Potok może na bieżąco wykorzystywać mniejszą przepustowość niż zarezerwowana. W razie potrzeby urządzenie zgłasza rzeczywistą przepustowość używaną za pośrednictwem normalnych, zdefiniowanych mechanizmów innych niż USB.<br />Dla wszystkich punktów końcowych bity 10..0 określają maksymalny rozmiar pakietu (w bajtach).<br />W przypadku szybkich punktów końcowych izochroniczne i przerwania:<br />Bity 12..11 określają liczbę dodatkowych szans transakcji na mikroframe: 00 = Brak (1 transakcja na mikroframe)<br />01 = 1 dodatkowy (2 na mikroframe)<br />10 = 2 dodatkowe (3 na mikroframe)<br />11 = Zarezerwowane<br />Bity 15..13 są zarezerwowane i muszą być ustawione na zero. |
| 6      | bInterval        | 1     | Liczba   | Interwał liczby dla punktu końcowego sondowania transferów danych.<br />Wyrażona w ramkach lub mikroframe w zależności od szybkości operacyjnej urządzenia (tj. 1 milisekunda lub 125 jednostek μs).<br />W przypadku pełnego/szybkiego izochroniczne punkty końcowe ta wartość musi być w zakresie od 1 do 16. Wartość **bInterval** jest używana jako wykładnik dla wartości 2bInterval-1; np. **bInterval** 4 oznacza okres 8 (24-1).<br />W przypadku punktów końcowych przerwań o pełnej/niskiej szybkości wartość tego pola może być z zakresu od 1 do 255.<br />W przypadku punktów końcowych przerwań o dużej szybkości **wartość bInterval** jest używana jako wykładnik dla wartości 2bInterval-1; np. **bInterval** 4 oznacza okres 8 (24-1). Ta wartość musi być z 1 do 16.<br />W przypadku szybkich punktów końcowych operacji zbiorczych/kontroli out **wartość bInterval** określa maksymalną szybkość nak dla punktu końcowego. Wartość 0 wskazuje, że punkt końcowy nigdy nie ma nakierów na sieci. Inne wartości wskazują co najwyżej jeden nak na **każdy bInterval** mikroframe.<br />Ta wartość musi być w zakresie od 0 do 255. |

USBX definiuje deskryptor punktu końcowego USB w następujący sposób:

```c
typedef struct UX_ENDPOINT_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bEndpointAddress;
    UINT bmAttributes;
    USHORT wMaxPacketSize;
    UINT bInterval;
} UX_ENDPOINT_DESCRIPTOR;
```

Deskryptor punktu końcowego USB jest częścią kontenera punktu końcowego, który został opisany w następujący sposób.

```c
typedef struct UX_ENDPOINT_STRUCT {
    ULONG    ux_endpoint_handle;
    ULONG    ux_endpoint_state;
    VOID    *ux_endpoint_ed;
    struct UX_ENDPOINT_DESCRIPTOR_STRUCT    ux_endpoint_descriptor;
    struct UX_ENDPOINT_STRUCT    *ux_endpoint_next_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_endpoint_interface;
    struct UX_DEVICE_STRUCT    *ux_endpoint_device;
    struct UX_TRANSFER REQUEST_STRUCT    ux_endpoint_transfer request;
} UX_ENDPOINT;

```

- **ux_endpoint_handle:** Dojście do punktu końcowego. Zazwyczaj jest to adres wystąpienia tej struktury dla punktu końcowego.
- **ux_endpoint_state:** stan punktu końcowego.
- **ux_endpoint_ed:** wskaźnik do fizycznego punktu końcowego w warstwie kontrolera hosta.
- **ux_endpoint_descriptor:** Deskryptor punktu końcowego USB.
- **ux_endpoint_next_endpoint:** Wskaźnik do następnego punktu końcowego, który należy do tego samego interfejsu.
- **ux_endpoint_interface:** wskaźnik do interfejsu, który jest właścicielem tego interfejsu punktu końcowego.
- **ux_endpoint_device:** wskaźnik do kontenera urządzenia nadrzędnego.
- **ux_endpoint_transfer żądania:** żądanie transferu USB używane do wysyłania/odbierania danych z/do urządzenia.

### <a name="string-descriptors"></a>Deskryptory ciągów

Deskryptory ciągów są opcjonalne. Jeśli urządzenie nie obsługuje deskryptorów ciągów, wszystkie odwołania do deskryptorów ciągów w obrębie urządzenia, konfiguracji i deskryptorów interfejsu muszą zostać zresetowane do zera.

Deskryptory ciągów używają kodowania UNICODE, co umożliwia obsługę kilku zestawów znaków. Ciągi w urządzeniu USB mogą obsługiwać wiele języków. Żądając deskryptora ciągu, żądający określa żądany język przy użyciu identyfikatora języka zdefiniowanego przez USB-IF. Listę obecnie zdefiniowanych dysków LANGID USB można znaleźć w załączniku USBX ??.
Indeks ciągu zero dla wszystkich języków zwraca deskryptor ciągu zawierający tablicę dwu bajtowych kodów LANGID obsługiwanych przez urządzenie. Należy zauważyć, że ciąg UNICODE nie jest zakończony 0. Zamiast tego rozmiar tablicy ciągów jest obliczany przez odjęcie dwóch od rozmiaru tablicy zawartej w pierwszym bajtze deskryptora.

Deskryptor ciągu USB 0 jest kodowany w następujący sposób.

| Przesunięcie | Pole           | Rozmiar | Wartość    | Opis                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | N +2      | Rozmiar tego deskryptora w bajtach |
| 1      | bDescriptorType | 1    | Stała | Typ deskryptora STRING           |
| 2      | wLANGID[0]      | 2    | Liczba   | Kod LANGID 0                    |
| ...    | ...]            | ...  | ...      | ...                              |
| N      | wLANGID[n]      | 2    | Liczba   | Kod LANGID n                    |

Inne deskryptory ciągów USB są kodowane w następujący sposób.

| Przesunięcie | Pole           | Rozmiar | Wartość    | Opis                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | Liczba   | Rozmiar tego deskryptora w bajtach |
| 1      | bDescriptorType | 1    | Stała | Typ deskryptora STRING           |
| 2      | bString         | n    | Liczba   | Ciąg zakodowany w formacie UNICODE           |

USBX definiuje deskryptor ciągu USB o długości niezerowej w następujący sposób:

```c
typedef struct UX_STRING_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT bString[1];
} UX_STRING_DESCRIPTOR;
```

### <a name="functional-descriptors"></a>Deskryptory funkcjonalne

Deskryptory funkcjonalne są również nazywane deskryptorami specyficznym dla klasy. Zwykle używają one tych samych podstawowych struktur co deskryptory ogólne i umożliwiają dostęp do dodatkowych informacji dla klasy. Na przykład w przypadku głośnika audio USB deskryptory specyficzne dla klasy umożliwiają klasie audio pobieranie dla każdego alternatywnego ustawienia obsługiwanego typu częstotliwości dźwięku.

### <a name="usbx-device-descriptor-framework-in-memory"></a>USBX Device Descriptor Framework in Memory

USBX przechowuje większość deskryptorów urządzeń w pamięci, czyli wszystkie deskryptory z wyjątkiem deskryptorów ciągów i funkcjonalnych. Na poniższym diagramie pokazano, jak te deskryptory są przechowywane i powiązane.

![USBX Device Descriptor Framework in Memory](./media/usbx-host-stack/usbx-device-descriptor-framework.png)
