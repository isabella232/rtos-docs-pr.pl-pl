---
title: Rozdział 3-funkcjonalne składniki stosu hosta USBX
description: Ten rozdział zawiera opis stosu o wysokiej wydajności USBX osadzonych portów USB z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 17b8d884dd2c71d60e91f5fcec40c360060f4fe8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824271"
---
# <a name="chapter-3---functional-components-of-usbx-host-stack"></a>Rozdział 3-funkcjonalne składniki stosu hosta USBX

Ten rozdział zawiera opis stosu o wysokiej wydajności USBX osadzonych portów USB z perspektywy funkcjonalnej.

## <a name="execution-overview"></a>Przegląd wykonywania

USBX składa się z kilku składników:

- Inicjalizacja
- Wywołania interfejsu aplikacji
- Główny koncentrator
- Hub — Klasa
- Klasy hostów
- Stos hosta USB
- Kontroler hosta

Na poniższym diagramie przedstawiono stos hosta USBX.

![Stos hosta USBX](./media/usbx-host-stack/usbx-host-stack.png)

### <a name="initialization"></a>Inicjalizacja

W celu aktywowania USBX należy wywołać funkcję ***ux_system_initialize*** . Ta funkcja inicjuje zasoby pamięci z USBX.

W celu aktywowania obiektów hosta USBX należy wywołać funkcję ***ux_host_stack_initialize*** . Ta funkcja spowoduje zainicjowanie wszystkich zasobów używanych przez stos hosta USBX, takich jak wątki ThreadX, muteksy i semafory.

Aby aktywować co najmniej jeden kontroler hosta USB i co najmniej jedną klasę USB, należy do inicjowania aplikacji. Gdy klasy zostały zarejestrowane na stosie, a funkcja inicjowania kontrolerów hosta została wywołana, magistrala jest aktywna i można uruchomić odnajdowanie urządzeń. Jeśli główny koncentrator kontrolera hosta wykryje dołączone urządzenie, wątek wyliczania USB, który jest odpowiedzialny za topologię USB, zostanie wznowiony i będzie mógł wyliczyć urządzenia.

Istnieje możliwość, ze względu na charakter koncentratora głównego i koncentratorów podrzędnych, że wszystkie dołączone urządzenia USB mogą nie zostać skonfigurowane w całości, gdy funkcja inicjowania kontrolera hosta zwróci wartość. Wyliczenie wszystkich urządzeń USB może potrwać kilka sekund, zwłaszcza jeśli istnieje co najmniej jeden koncentrator między głównym koncentratorem a urządzeniami USB.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Istnieją dwa poziomy interfejsów API w USBX.

- Interfejsy API stosu hosta USB
- Interfejsy API klasy hosta USB

Zwykle aplikacja USBX nie powinna wywołać żadnych funkcji interfejsu API stosu hosta USB. Większość aplikacji będzie uzyskiwać dostęp tylko do funkcji interfejsu API klasy USB.

### <a name="usb-host-stack-apis"></a>Interfejsy API stosu hosta USB

Funkcje interfejsu API stosu hosta są odpowiedzialne za rejestrację składników USBX (klasy hosta i kontrolery hosta), konfigurację urządzeń oraz żądania transferu dla dostępnych punktów końcowych urządzeń.

### <a name="usb-host-class-api"></a>Interfejs API klasy hosta USB

Interfejsy API klas są bardzo specyficzne dla każdej klasy USB. Większość typowych funkcji interfejsu API dla klas USB zapewnia usługi, takie jak otwieranie/zamykanie urządzenia oraz odczytywanie i zapisywanie na urządzeniu.

### <a name="root-hub"></a>Główny koncentrator

Każde wystąpienie kontrolera hosta ma jeden lub więcej głównych koncentratorów USB. Liczba centrów głównych jest określana przez charakter kontrolera lub może być pobierana przez odczytanie określonych rejestrów z kontrolera.

### <a name="hub-class"></a>Hub — Klasa

Klasa Hub jest odpowiedzialna za kierowanie koncentratorów USB. Koncentrator USB może być koncentratorem autonomicznym lub w ramach urządzenia złożonego, takiego jak klawiatura lub monitor. Koncentrator może być samodzielny lub napędzany przez magistralę. Koncentratory zasilane magistralą mają maksymalnie cztery porty podrzędne i mogą zezwalać tylko na połączenia urządzeń, które są urządzeniami samoobsługowymi lub magistrali, które używają mniej niż 100mA zasilania. Centra można kaskadowo. Maksymalnie pięć centrów można połączyć ze sobą.

### <a name="usb-host-stack"></a>Stos hosta USB

Stos hosta USB to filarem USBX. Ma trzy główne funkcje.

- Zarządzanie topologią USB.
- Powiąż urządzenie USB z jedną lub wieloma klasami.
- Podaj interfejs API do klas, aby wykonać transportowe i transfery za pośrednictwem deskryptora urządzenia.

### <a name="topology-manager"></a>Menedżer topologii

Wątek topologii stosu USB jest wyłączany, gdy nowe urządzenie jest połączone lub gdy urządzenie zostało odłączone. Koncentrator główny lub zwykłe centrum może akceptować połączenia urządzeń. Po połączeniu urządzenia z urządzeniem USB Menedżer topologii pobierze deskryptora urządzenia. Ten deskryptor będzie zawierać liczbę możliwych konfiguracji dostępnych dla tego urządzenia. Większość urządzeń ma tylko jedną konfigurację. Niektóre urządzenia mogą działać inaczej, zgodnie z dostępną mocą dostępną na porcie, do którego jest podłączony. W takim przypadku urządzenie będzie miało wiele konfiguracji, które można wybrać w zależności od dostępnej mocy. Gdy urządzenie jest skonfigurowane przez Menedżera topologii, jest to dozwolone do narysowania ilości mocy określonej w deskryptorze konfiguracji.

## <a name="usb-class-binding"></a>Powiązanie klasy USB

Po skonfigurowaniu urządzenia Menedżer topologii zezwoli, aby Menedżer klas kontynuował odnajdywanie urządzeń, przeglądając deskryptory interfejsu urządzenia. Urządzenie może mieć co najmniej jeden deskryptor interfejsu.

Interfejs reprezentuje funkcję w urządzeniu. Na przykład głośnik USB ma trzy interfejsy, jeden do przesyłania strumieniowego audio, jeden dla kontrolki audio i jeden do zarządzania różnymi przyciskami głośników.

Menedżer klas ma dwa mechanizmy przyłączania interfejsów urządzenia do jednej lub kilku klas. Może użyć kombinacji identyfikatora PID/VID (identyfikator produktu i identyfikator dostawcy) znajdującego się w deskryptorze interfejsu lub kombinacji klasy/podklasy/protokołu.

Kombinacja identyfikatora PID/VID jest prawidłowa dla interfejsów, które nie mogą być sterowane przez klasę generyczną. Kombinacja klasy/podklasy/protokołu jest używana przez interfejsy należące do klasy certyfikowanej USB, takiej jak drukarka, Hub, Storage, audio lub HID.

Menedżer klas zawiera listę zarejestrowanych klas z inicjalizacji USBX. Menedżer klas będzie wywoływał każdą klasę pojedynczo do momentu zaakceptowania przez jedną klasę do zarządzania interfejsem dla tego urządzenia. Klasa może zarządzać tylko jednym interfejsem. Na przykład głośnika audio USB Menedżer klas wywoła wszystkie klasy dla każdego z interfejsów.

Gdy Klasa akceptuje interfejs, tworzone jest nowe wystąpienie tej klasy. Menedżer klas będzie następnie szukać domyślnego ustawienia alternatywnego dla interfejsu. Urządzenie może mieć co najmniej jedno alternatywne ustawienia dla każdego interfejsu. Ustawienie alternatywne 0 będzie używane domyślnie do momentu, gdy Klasa zdecyduje się ją zmienić.

W przypadku domyślnego ustawienia alternatywnego Menedżer klas zainstaluje wszystkie punkty końcowe zawarte w ustawieniu alternatywnym. W przypadku pomyślnego zamontowania każdego punktu końcowego Menedżer klas ukończy zadanie, zwracając do klasy, która ukończy inicjalizację interfejsu.

### <a name="usbx-apis"></a>Interfejsy API USBX

Stos USB eksportuje określoną liczbę interfejsów API dla klas USB, aby przełączać urządzenia i transfery USB w określonych punktach końcowych. Te funkcje interfejsu API są szczegółowo opisane w tym podręczniku.

### <a name="host-controller"></a>Kontroler hosta

Sterownik kontrolera hosta jest odpowiedzialny za kierowanie określonego typu kontrolera USB. Kontroler hosta USB może mieć wiele kontrolerów wewnątrz. Na przykład niektóre chipsety PC firmy Intel zawierają dwa kontrolery UHCI. Niektóre kontrolery USB 2,0 zawierają wiele wystąpień kontrolera OHCI oprócz jednego wystąpienia kontrolera EHCI.

Kontroler hosta będzie zarządzać wieloma wystąpieniami tylko tego samego kontrolera. Aby można było uzyskać większość kontrolerów hosta USB 2,0, będzie wymagane zainicjowanie kontrolera OCHI i kontrolera EHCI podczas inicjowania USBX.

Kontroler hosta jest odpowiedzialny za zarządzanie następującymi.

- Główny koncentrator
- Zarządzanie energią
- Punkty końcowe
- Sunięcia

### <a name="root-hub"></a>Główny koncentrator

Główne Zarządzanie centrami jest odpowiedzialne za działanie wszystkich portów kontrolera i określanie, czy urządzenie zostało wstawione. Ta funkcja jest używana przez USBX Generic Root Hub do przejrzeć portów podrzędnych kontrolera.

### <a name="power-management"></a>Zarządzanie energią

Przetwarzanie zarządzania mocą zapewnia obsługę sygnałów zawieszenia/wznowienia w trybie gang, w związku z czym ma wpływ na wszystkie porty podrzędne kontrolera w tym samym czasie lub indywidualnie, Jeśli kontroler oferuje tę funkcję.

### <a name="endpoints"></a>Punkty końcowe

Zarządzanie punktami końcowymi umożliwia tworzenie i niszczenie fizycznych punktów końcowych do kontrolera. Fizyczne punkty końcowe są jednostkami pamięci, które są analizowane przez kontroler, Jeśli kontroler obsługuje główny serwer DMA lub jest zapisany w kontrolerze. Fizyczne punkty końcowe zawierają informacje o transakcjach, które mają być wykonywane przez kontroler.

### <a name="transfers"></a>Sunięcia

Zarządzanie transferem zapewnia klasy do wykonywania transakcji na wszystkich utworzonych punktach końcowych. Każdy logiczny punkt końcowy zawiera składnik o nazwie żądanie transferu dla żądań transferu USB. ŻĄDANIE transferu jest używane przez stos do opisywania transakcji. To żądanie transferu jest następnie przekazywane do stosu i do kontrolera, co może podzielić go na kilka transakcji podrzędnych w zależności od możliwości kontrolera.

## <a name="usb-device-framework"></a>Architektura urządzenia USB

Urządzenie USB jest reprezentowane przez drzewo deskryptorów. Istnieje sześć głównych typów deskryptorów.

- Deskryptory urządzeń
- Deskryptory konfiguracji
- Deskryptory interfejsów
- Deskryptory punktów końcowych
- Deskryptory ciągów
- Deskryptory funkcjonalne

Urządzenie USB może mieć bardzo prosty opis i wygląda następująco.
![Proste urządzenie USB](./media/usbx-host-stack/usb-device-simple.png)

Na powyższej ilustracji urządzenie ma tylko jedną konfigurację. Do tej konfiguracji jest dołączony pojedynczy interfejs wskazujący, że urządzenie ma tylko jedną funkcję i ma tylko jeden punkt końcowy. Dołączony do deskryptora urządzenia jest deskryptorem ciągu dostarczającym widoczną identyfikację urządzenia.

Jednak urządzenie może być bardziej skomplikowane i może wyglądać w następujący sposób.

![Złożone urządzenie USB](./media/usbx-host-stack/usb-device-complex.png)

Na powyższej ilustracji urządzenie ma dwa deskryptory konfiguracji dołączone do deskryptora urządzenia. To urządzenie może wskazywać, że ma dwa tryby zasilające lub mogą być sterowane przez klasy standardowe lub własnościowe klasy.

Dołączone do pierwszej konfiguracji są dwa interfejsy wskazujące, że urządzenie ma dwie funkcje logiczne. Pierwsza funkcja ma 3 deskryptory punktów końcowych i deskryptor funkcjonalny. Deskryptor funkcjonalny może być używany przez klasę odpowiedzialną za interfejs, aby uzyskać dodatkowe informacje o tym interfejsie, które zwykle nie są dostępne przez deskryptor generyczny.

### <a name="device-descriptors"></a>Deskryptory urządzeń

Każde urządzenie USB ma jeden deskryptor jednego urządzenia. Ten deskryptor zawiera identyfikator urządzenia, liczbę obsługiwanych konfiguracji oraz charakterystykę domyślnego punktu końcowego sterowania używanego do konfigurowania urządzenia.

| Przesunięcie | Pole              | Rozmiar | Wartość    | Opis                             |
| ------ | ------------------ | ---- | -------- | --------------------------------------- |
| 0      | BLength            | 1    | Liczba   | Rozmiar tego deskryptora w bajtach |
| 1      | bDescriptorType    | 1    | Stała | Typ deskryptora urządzenia |
| 2      | bcdUSB             | 2    | MAGAZYNU      | Numer wydania specyfikacji USB w BinaryCoded gru<br />Przykład: 2,10 jest równoważne 0x210. To pole Identyfikuje wydanie specyfikacji USB, z którą urządzenie i jego deskryptory są zgodne. |
| 4      | bDeviceClass       | 1    | Klasa    | Kod klasy (przypisany przez USB-IF).<br />Jeśli to pole zostanie zresetowane do wartości 0, każdy interfejs w ramach konfiguracji określa własne informacje o klasie i różne interfejsy działają niezależnie.<br />Jeśli to pole jest ustawione na wartość z zakresu od 1 do 0xFE, urządzenie obsługuje inne specyfikacje klasy w różnych interfejsach, a interfejsy mogą nie działać niezależnie. Ta wartość Określa definicję klasy używaną dla interfejsów agregujących.<br />Jeśli to pole jest ustawione na wartość 0xFF, Klasa urządzenia jest specyficzna dla dostawcy. |
| 5      | bDeviceSubClass    | 1    | Podklasa | Kod podklasy (przypisany przez USB-IF).<br />Te kody są kwalifikowane przez wartość pola bDeviceClass. Jeśli pole bDeviceClass zostanie zresetowane do wartości 0, to pole musi również zostać zresetowane do wartości 0. Jeśli pole bDeviceClass nie jest ustawione na wartość 0xFF, wszystkie wartości są zastrzeżone do przypisania przez USB. |
| 6      | bDeviceProtocol    | 1    | Protokół | Kod protokołu (przypisany przez USB-IF).<br />Kody te są kwalifikowane przez wartość bDeviceClass i pola bDeviceSubClass. Jeśli urządzenie obsługuje protokoły specyficzne dla klasy na podstawie urządzenia, a nie na podstawie interfejsu, ten kod identyfikuje protokoły używane przez urządzenie zgodnie ze specyfikacją klasy urządzenia. Jeśli to pole zostanie zresetowane do wartości 0, urządzenie nie korzysta z protokołów określonych dla klasy na podstawie urządzenia.<br />Może jednak używać protokołów specyficznych dla klasy na podstawie interfejsu.<br />Jeśli to pole jest ustawione na wartość 0xFF, urządzenie używa protokołu określonego dla dostawcy na podstawie urządzenia. |
| 7      | bMaxPacketSize0    | 1    | Liczba   | Maksymalny rozmiar pakietu dla punktu końcowego zero (prawidłowe rozmiary to 8, 16, 32 lub 64) |
| 8      | idVendor           | 2    | ID (Identyfikator)       | Identyfikator dostawcy (przypisany przez USB — Jeśli) |
| 10     | idProduct          | 2    | ID (Identyfikator)       | Identyfikator produktu (przypisany przez producenta) |
| 12     | bcdDevice          | 2    | MAGAZYNU      | Numer wydania urządzenia w postaci dziesiętnej kodowanej binarnie |
| 14     | iManufacturer      | 1    | Indeks    | Indeks deskryptora ciągu opisujący producenta |
| 15     | iProduct           | 1    | Indeks    | Indeks deskryptora ciągu opisujący produkt |
| 16     | iSerialNumbe       | 1    | Indeks    | Indeks deskryptora ciągu opisujący numer seryjny urządzenia |
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

- **ux_device_handle**: uchwyt urządzenia. Jest to zazwyczaj adres wystąpienia tej struktury dla urządzenia.
- **ux_device_type**: wartość przestarzała. Nieużywany.
- **ux_device_state**: stan urządzenia, który może mieć jedną z następujących wartości:
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
- **ux_device_address**: adres urządzenia po zaakceptowaniu polecenia **SET_ADDRESS** (od 1 do 127).
- **ux_device_speed**: szybkość urządzenia:
    - **UX_LOW_SPEED_DEVICE**      0
    - **UX_FULL_SPEED_DEVICE**     1
    - **UX_HIGH_SPEED_DEVICE**     2
- **ux_device_port_location**: indeks portu urządzenia nadrzędnego (głównego koncentratora lub koncentratora).
- **ux_device_max_power**: Maksymalna moc w przypadku, gdy urządzenie może przyjąć wybraną konfigurację.
- **ux_device_power_source**: może być jedną z dwóch następujących wartości:
    - **UX_DEVICE_BUS_POWERED**     1
    - **UX_DEVICE_SELF_POWERED**    2
- **ux_device_current_configuration**: indeks bieżącej konfiguracji używanej przez to urządzenie.
- **ux_device_parent**: wskaźnik kontenera urządzenia nadrzędnego dla tego urządzenia. Jeśli wskaźnik ma wartość null, obiekt nadrzędny jest głównym koncentratorem kontrolera.
- **ux_device_class**: wskaźnik do typu klasy, który jest właścicielem tego urządzenia.
- **ux_device_class_instance**: wskaźnik do wystąpienia klasy należącej do tego urządzenia.
- **ux_device_hcd**: wystąpienie kontrolera hosta USB, z którym jest dołączone to urządzenie.
- **ux_device_first_configuration**: wskaźnik do pierwszego kontenera konfiguracji dla tego urządzenia.
- **ux_device_next_device**: wskaźnik do następnego urządzenia na liście urządzeń na dowolnej magistrali wykrytej przez USBX.
- **ux_device_descriptor**: deskryptor urządzenia USB.
- **ux_device_control_endpoint**: deskryptor domyślnego punktu końcowego kontrolki używanego przez to urządzenie.
- **ux_device_hub_tt**: tablica TTs usługi Hub dla urządzenia

### <a name="configuration-descriptors"></a>Deskryptory konfiguracji

Deskryptor konfiguracji zawiera informacje dotyczące konkretnej konfiguracji urządzenia. Urządzenie USB może zawierać co najmniej jeden deskryptor konfiguracji. Pole **bNumConfigurations** w deskryptorze urządzenia wskazuje liczbę deskryptorów konfiguracji. Deskryptor zawiera pole **bConfigurationValue** o wartości, która, gdy jest używany jako parametr do żądania konfiguracji zestawu, powoduje, że urządzenie przyjmuje opisaną konfigurację.

Deskryptor opisuje liczbę interfejsów dostarczonych przez konfigurację. Każdy interfejs reprezentuje funkcję logiczną w urządzeniu i może działać niezależnie. Na przykład głośniki audio USB mogą mieć trzy interfejsy, jeden do przesyłania strumieniowego audio, jeden dla kontrolki audio i jeden interfejs HID do zarządzania przyciskami głośników.

Gdy host wystawia żądanie GET_DESCRIPTOR dla deskryptora konfiguracji, zwracane są wszystkie powiązane deskryptory interfejsu i punktu końcowego.

| Przesunięcie | Pole               | Rozmiar | Wartość    | Opis                       |
| ------ | ------------------- | ---- | -------- | --------------------------------- |
| 0      | bLength             | 1    | Liczba   | Rozmiar tego deskryptora w bajtach. |
| 1      | bDescriptorType     | 1    | Stała | KONFIGURACJA                     |
| 2      | wTotalLength        | 2    | Liczba   | Łączna długość danych zwróconych dla tej konfiguracji. Obejmuje łączną długość wszystkich deskryptorów (konfiguracji, interfejsu, punktu końcowego i konkretnej klasy lub dostawcy) zwróconych dla tej konfiguracji. |
| 4      | bNumInterfaces      | 1    | Liczba   | Liczba interfejsów obsługiwanych przez tę konfigurację. |
| 5      | bConfigurationValue | 1    | Liczba   | Wartość, która ma być używana jako argument do ustawienia<br/>Konfiguracja, aby wybrać tę konfigurację. |
| 6      | iConfiguration      | 1    | Indeks    | Indeks deskryptora ciągu opisujący tę konfigurację. |
| 7      | bMAttributes        | 1    | Mapy   | Charakterystyki konfiguracji D7 magistrali<br />D6 samoobsługowy<br />Zdalne wznowienie nabudzenia<br />D4.. 0 zarezerwowane (Resetowanie do 0)<br />Konfiguracja urządzenia korzystająca z mocy z magistrali i lokalnych źródeł ustawia zarówno D7, jak i D6. Rzeczywiste źródło napięcia w środowisku uruchomieniowym można określić przy użyciu żądania pobrania stanu urządzenia.<br />Jeśli konfiguracja urządzenia obsługuje wznawianie zdalne, nadano wartość 1. |
| 8      | MaxPower            | 1    | Ruchom       | Maksymalne zużycie mocy przez urządzenie USB z magistrali w tej konkretnej konfiguracji, gdy urządzenie jest w pełni funkcjonalne.<br />Wyrażony w 2 jednostkach (np. 50 = 100 mA).<br />Uwaga: Konfiguracja urządzenia wskazuje, czy konfiguracja jest napędzana magistralą, czy samodzielna.<br />Stan urządzenia informuje o tym, czy urządzenie jest obecnie zasilane samoobsługowo. Jeśli urządzenie zostanie odłączone od jego zewnętrznego źródła zasilania, aktualizuje stan urządzenia, aby wskazać, że nie jest on już samodzielny. |

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

- **ux_configuration_handle**: dojście do konfiguracji. Jest to zazwyczaj adres wystąpienia tej struktury dla konfiguracji.
- **ux_configuration_state**: stan konfiguracji.
- **ux_configuration_descriptor**: deskryptor urządzenia USB.
- **ux_configuration_first_interface**: wskaźnik do pierwszego interfejsu dla tej konfiguracji.
- **ux_configuration_next_configuration**: wskaźnik do następnej konfiguracji dla tego samego urządzenia.
- **ux_configuration_device**: wskaźnik do właściciela urządzenia w tej konfiguracji.

### <a name="interface-descriptors"></a>Deskryptory interfejsów

Deskryptor interfejsu opisuje określony interfejs w konfiguracji. Interfejs jest funkcją logiczną na urządzeniu USB. Konfiguracja zawiera jeden lub więcej interfejsów, z których każdy ma zero lub więcej deskryptorów punktów końcowych opisujących unikatowy zestaw punktów końcowych w ramach konfiguracji. Jeśli konfiguracja obsługuje więcej niż jeden interfejs, deskryptory punktów końcowych dla określonego interfejsu są zgodne ze skryptem interfejsu w danych zwróconych przez żądanie **GET_DESCRIPTOR** dla określonej konfiguracji.

Deskryptor interfejsu jest zawsze zwracany jako część deskryptora konfiguracji. Deskryptora interfejsu nie można uzyskać dostępu bezpośrednio przez żądanie GET_DESCRIPTOR.

Interfejs może zawierać alternatywne ustawienia, które pozwalają zmieniać punkty końcowe i/lub ich charakterystyki po skonfigurowaniu urządzenia. Ustawienie domyślne dla interfejsu zawsze jest alternatywnym ustawieniem zero. Klasa może wybrać zmianę bieżącego ustawienia alternatywnego, aby zmienić zachowanie interfejsu i charakterystykę skojarzonych punktów końcowych. Żądanie SET_INTERFACE służy do wybrania alternatywnego ustawienia lub przywrócenia ustawienia domyślnego.

Ustawienia alternatywne umożliwiają zróżnicowanie konfiguracji urządzenia, gdy inne interfejsy pozostają w działaniu. Jeśli konfiguracja ma alternatywne ustawienia dla co najmniej jednego z jego interfejsów, dla każdego ustawienia są uwzględniane oddzielne deskryptory interfejsu i skojarzone z nimi punkty końcowe.

Jeśli konfiguracja urządzenia zawiera jeden interfejs z dwoma ustawieniami alternatywnymi, żądanie GET_DESCRIPTOR dla konfiguracji zwróci deskryptor konfiguracji, a następnie deskryptora interfejsu z polami **bInterfaceNumber** i **bAlternateSetting** ustawioną na zero, a następnie dla tego ustawienia, po którym następuje inny deskryptor interfejsu i skojarzone z nim kodery punktów końcowych. W drugim polu **bInterfaceNumber** deskryptora interfejsu zostanie również ustawiona wartość zero, ale w polu **bAlternateSetting** drugiego deskryptora interfejsu zostanie ustawiona wartość 1 wskazująca, że to ustawienie alternatywne należy do pierwszego interfejsu.

Z interfejsem nie są skojarzone żadne punkty końcowe, w takim przypadku tylko domyślny punkt końcowy kontrolki jest prawidłowy dla tego interfejsu.

Ustawienia alternatywne są używane głównie do zmiany wymaganej przepustowości dla okresowych punktów końcowych skojarzonych z interfejsem. Na przykład interfejs przesyłania strumieniowego dla głośników USB powinien mieć pierwsze ustawienie alternatywne z przepustowością 0 w punkcie końcowym Isochronous. Inne ustawienia alternatywne mogą wybrać różne wymagania dotyczące przepustowości w zależności od częstotliwości przesyłania strumieniowego audio.

Deskryptor USB dla interfejsu jest następujący:

| Przesunięcie | Pole              | Rozmiar | Wartość     | Opis                              |
| ------ | ------------------ | ---- | --------- | --------------------------------------- |
| 0      | bLength            | 1    | Liczba    | Rozmiar tego deskryptora w bajtach.       |
| 1      | bDescriptorType    | 1    | Stała  | Typ deskryptora interfejsu               |
| 2      | bInterfaceNumber   | 1    | Liczba    | Liczba interfejsów. Wartość zerowa, identyfikująca indeks w tablicy współbieżnych interfejsów obsługiwanych przez tę konfigurację. |
| 3      | bAltenateSetting   | 1    | Liczba    | Wartość używana do wybrania alternatywnego ustawienia dla interfejsu zidentyfikowanego w poprzednim polu. |
| 4      | bNumEndpoints      | 1    | Liczba    | Liczba punktów końcowych używanych przez ten interfejs (z wyjątkiem punktu końcowego zero). Jeśli ta wartość wynosi 0, ten interfejs używa tylko punktu końcowego zero. |
| 5      | bInterfaceClass    | 1    | Klasa     | Kod klasy (przypisany przez USB)<br />Jeśli to pole zostanie zresetowane do wartości 0, interfejs nie należy do żadnej określonej klasy urządzeń USB.<br />Jeśli to pole jest ustawione na wartość 0xFF, Klasa interfejsu jest specyficzna dla dostawcy.<br />Wszystkie inne wartości są zastrzeżone do przypisania przez USB. |
| 6      | bInterfaceSubClass | 1    | Podklasa  | Kod podklasy (przypisany przez USB).<br />Te kody są kwalifikowane przez wartość pola bInterfaceClass. Jeśli pole bInterfaceClass zostanie zresetowane do wartości 0, to pole musi również zostać zresetowane do wartości 0. Jeśli pole bInterfaceClass nie jest ustawione na wartość 0xFF, wszystkie wartości są zastrzeżone do przypisania przez USB. |
| 7      | bInterfaceProtocol | 1    | Protokół  | Kod protokołu (przypisany przez USB). Kody te są kwalifikowane przez wartość bInterfaceClass i pola bInterfaceSubClass. Jeśli interfejs obsługuje żądania specyficzne dla klasy, ten kod identyfikuje protokoły używane przez urządzenie zgodnie ze specyfikacją klasy urządzenia.<br />W przypadku zresetowania tego pola do wartości 0 urządzenie nie korzysta z protokołu określonego dla klasy w tym interfejsie. Jeśli to pole jest ustawione na wartość 0xFF, urządzenie używa protokołu określonego dla dostawcy dla tego interfejsu. |
| 8      | iInterface         | 1    | Indeks     | Indeks deskryptora ciągu opisujący ten interfejs. |

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

- **ux_interface_handle**: uchwyt interfejsu. Jest to zazwyczaj adres wystąpienia tej struktury dla interfejsu.
- **ux_interface_state**: stan interfejsu.
- **ux_interface_descriptor**: deskryptor interfejsu USB.
- **ux_interface_class**: wskaźnik do typu klasy, który jest właścicielem tego interfejsu.
- **ux_interface_class_instance**: wskaźnik do wystąpienia klasy, która jest właścicielem tego interfejsu.
- **ux_interface_first_endpoint**: wskaźnik do pierwszego punktu końcowego zarejestrowanego w tym interfejsie.
- **ux_interface_next_interface**: wskaźnik do następnego interfejsu skojarzonego z konfiguracją.
- **ux_interface_configuration**: wskaźnik do właściciela konfiguracji tego interfejsu.

### <a name="endpoint-descriptors"></a>Deskryptory punktów końcowych

Każdy punkt końcowy skojarzony z interfejsem ma swój własny deskryptor punktu końcowego. Ten deskryptor zawiera informacje wymagane przez stos hosta do określenia wymagań dotyczących przepustowości dla każdego punktu końcowego, maksymalnego ładunku skojarzonego z punktem końcowym, jego okresowości i kierunku. Deskryptor punktu końcowego jest zawsze zwracany przez GET_DESCRIPTOR polecenie dla konfiguracji.

Domyślny punkt końcowy sterowania skojarzony z deskryptorem urządzenia nie jest liczony jako część punktów końcowych skojarzonych z interfejsem i w związku z tym nie są zwracane w tym deskryptorze.

Gdy oprogramowanie hosta żąda zmiany ustawienia alternatywnego dla interfejsu, wszystkie skojarzone punkty końcowe i ich zasoby USB są modyfikowane zgodnie z nowym ustawieniem alternatywnym.

Poza domyślnymi punktami końcowymi kontrolek punkty końcowe nie mogą być współużytkowane między interfejsami.

| Przesunięcie | Pole            | Rozmiar | Wartość    | Opis                       |
| ------ | ---------------- | ---- | -------- | --------------------------------- |
| 0      | bLength          | 1    | Liczba   | Rozmiar tego deskryptora w bajtach. |
| 1      | bDescriptorType  | 1    | Stała | Typ deskryptora punktu końcowego. |
| 2      | bEndpointAddress | 1    | Punkt końcowy | Adres punktu końcowego na urządzeniu USB opisany przez ten deskryptor. Adres jest zakodowany w następujący sposób:<br />Bit 3... 0: numer punktu końcowego<br />Bit 6... 4: zarezerwowany, Reset do zera<br />Bit 7: kierunek ignorowany dla punktów końcowych kontrolki<br />0 = punkt końcowy OUT<br />1 = w punkcie końcowym |
| 3      | bmAttributes     | 1    | Mapy   | W tym polu opisano atrybuty punktu końcowego, gdy jest on konfigurowany przy użyciu pola **bConfigurationValue** . Bity 1.. 0: typ transferu<br />00 = kontrolka<br />01 = Isochronous<br />10 = bulk<br />11 = przerwanie<br />Jeśli nie jest punktem końcowym Isochronous, bity 5.. 2 są zarezerwowane i muszą mieć wartość zero. Jeśli Isochronous, są one zdefiniowane w następujący sposób:<br />Bity 3.. 2: typ synchronizacji<br />00 = brak synchronizacji<br />01 = asynchroniczny<br />10 = adaptacyjne<br />11 = synchroniczne<br />Bity 5.. 4: typ użycia<br />00 = punkt końcowy danych<br />01 = punkt końcowy opinii<br />10 = niejawny punkt końcowy danych opinii<br />11 = zarezerwowane |
| 4      | wMaxPacketSize   | 2    | Liczba   | Maksymalny rozmiar pakietu, który ten punkt końcowy może wysłać lub odebrać, gdy ta konfiguracja jest wybrana.<br />W przypadku punktów końcowych Isochronous ta wartość jest używana w celu zarezerwowania czasu magistrali zgodnie z harmonogramem, który jest wymagany dla ładunków danych ramek na (mikro). Potok może, na bieżąco, faktycznie używać mniejszej przepustowości niż zarezerwowana. Urządzenie zgłasza, w razie potrzeby, rzeczywistą przepustowość używaną przez normalne mechanizmy, które nie są zdefiniowane przez USB.<br />Dla wszystkich punktów końcowych usługa BITS 10.0 określa maksymalny rozmiar pakietu (w bajtach).<br />Dla szybkich punktów końcowych Isochronous i przerwań:<br />Bity 12.. 11 Określ liczbę dodatkowych możliwości transakcji na mikroramkę: 00 = Brak (1 transakcja na mikroramkę)<br />01 = 1 dodatkowe (2 na mikroramkę)<br />10 = 2 dodatkowe (3 na mikroramkę)<br />11 = zarezerwowane<br />Bity 15.13 są zarezerwowane i muszą mieć wartość zero. |
| 6      | bInterval        | 1     | Liczba   | Interwał liczby punktów końcowych sondowania dla transferów danych.<br />Wyrażony w klatkach lub mikroramkach w zależności od szybkości działania urządzenia (tj. 1 milisekund lub 125 s).<br />W przypadku punktów końcowych pełnej/High-Speed Isochronous ta wartość musi należeć do zakresu od 1 do 16. **BInterval** jest używany jako wykładnik dla wartości 2bInterval-1; np. **bInterval** 4 oznacza okres 8 (24-1).<br />W przypadku punktów końcowych przerwań/Low-Speed wartość tego pola może wynosić od 1 do 255.<br />Dla punktów końcowych przerwań o dużej szybkości **bInterval** jest używany jako wykładnik dla wartości 2bInterval-1; np. **bInterval** 4 oznacza okres 8 (24-1). Ta wartość musi należeć do przemieścić od 1 do 16.<br />W przypadku przepływów końcowych o dużej szybkości zbiorczej/kontroli **bInterval** określa maksymalną nak punktu końcowego. Wartość 0 oznacza, że punkt końcowy nigdy nie NAKs. Inne wartości wskazują maksymalnie jedną NAK każdego **bInterval** mikroramek.<br />Ta wartość musi należeć do zakresu od 0 do 255. |

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

Deskryptor punktu końcowego USB jest częścią kontenera punktów końcowych, który został opisany w następujący sposób.

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

- **ux_endpoint_handle**: uchwyt punktu końcowego. Jest to zazwyczaj adres wystąpienia tej struktury dla punktu końcowego.
- **ux_endpoint_state**: stan punktu końcowego.
- **ux_endpoint_ed**: wskaźnik do fizycznego punktu końcowego w warstwie kontrolera hosta.
- **ux_endpoint_descriptor**: deskryptor punktu końcowego USB.
- **ux_endpoint_next_endpoint**: wskaźnik do następnego punktu końcowego, który należy do tego samego interfejsu.
- **ux_endpoint_interface**: wskaźnik do interfejsu, który jest właścicielem tego interfejsu punktu końcowego.
- **ux_endpoint_device**: wskaźnik do kontenera urządzeń nadrzędnych.
- **żądanie ux_endpoint_transfer**: żądanie transferu USB używane do wysyłania/odbierania danych z urządzenia na urządzenie.

### <a name="string-descriptors"></a>Deskryptory ciągów

Deskryptory ciągów są opcjonalne. Jeśli urządzenie nie obsługuje deskryptorów ciągów, wszystkie odwołania do deskryptorów ciągów w obrębie urządzeń, konfiguracji i deskryptorów interfejsów muszą zostać zresetowane do zera.

Deskryptory ciągów używają kodowania UNICODE, dzięki czemu można obsługiwać kilka zestawów znaków. Ciągi na urządzeniu USB mogą obsługiwać wiele języków. Podczas żądania deskryptora ciągu Obiekt żądający określa żądany język przy użyciu identyfikatora języka zdefiniowanego przez port USB. Listę obecnie zdefiniowanych LANGIDs USB można znaleźć w dodatku USBX??.
Indeks ciągu zero dla wszystkich języków zwraca deskryptor ciągu, który zawiera tablicę kodów LANGID dwubajtowych obsługiwanych przez urządzenie. Należy zauważyć, że ciąg UNICODE nie jest zakończony zerem. Zamiast tego rozmiar tablicy ciągów jest obliczany przez odjęcie dwóch od rozmiaru tablicy zawartej w pierwszym bajcie deskryptora.

Deskryptor ciągu USB 0 jest zakodowany w następujący sposób.

| Przesunięcie | Pole           | Rozmiar | Wartość    | Opis                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | N + 2      | Rozmiar tego deskryptora w bajtach |
| 1      | bDescriptorType | 1    | Stała | Typ deskryptora ciągu           |
| 2      | wLANGID [0]      | 2    | Liczba   | Kod LANGID 0                    |
| ...    | ...]            | ...  | ...      | ...                              |
| N      | wLANGID [n]      | 2    | Liczba   | Kod LANGID n                    |

Inne deskryptory ciągu USB są kodowane w następujący sposób.

| Przesunięcie | Pole           | Rozmiar | Wartość    | Opis                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | Liczba   | Rozmiar tego deskryptora w bajtach |
| 1      | bDescriptorType | 1    | Stała | Typ deskryptora ciągu           |
| 2      | bStre         | n    | Liczba   | Ciąg zakodowany w formacie UNICODE           |

USBX definiuje deskryptor ciągu USB o wartości innej niż zero w następujący sposób:

```c
typedef struct UX_STRING_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT bString[1];
} UX_STRING_DESCRIPTOR;
```

### <a name="functional-descriptors"></a>Deskryptory funkcjonalne

Deskryptory funkcjonalne są również znane jako deskryptory charakterystyczne dla klasy. Zwykle wykorzystują one te same podstawowe struktury jako ogólne deskryptory i umożliwiają udostępnienie dodatkowych informacji dla klasy. Na przykład w przypadku głośnika audio USB, specyficzne dla klasy deskryptory umożliwiają pobranie klasy audio dla każdego alternatywnego ustawienia Typ obsługiwanej częstotliwości audio.

### <a name="usbx-device-descriptor-framework-in-memory"></a>Struktura deskryptora urządzenia USBX w pamięci

USBX utrzymuje większość deskryptorów urządzeń w pamięci, czyli wszystkie deskryptory oprócz deskryptorów ciągów i funkcjonalnych. Na poniższym diagramie przedstawiono, w jaki sposób te deskryptory są przechowywane i powiązane.

![Struktura deskryptora urządzenia USBX w pamięci](./media/usbx-host-stack/usbx-device-descriptor-framework.png)
