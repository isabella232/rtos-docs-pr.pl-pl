---
title: Rozdział 2 — Zagadnienia dotyczące klas urządzeń USBX
description: Klasa RNDIS urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzenie ethernet. Ta klasa jest oparta na zastrzeżonej implementacji firmy Microsoft i jest specyficzna dla Windows platform.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2a28196c8f0e29ad94ef9f2d65b143459bf0214f48c345e6bb0d4ea71d520dfd
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802635"
---
# <a name="chapter-2---usbx-device-class-considerations"></a>Rozdział 2 — Zagadnienia dotyczące klas urządzeń USBX

## <a name="usb-device-rndis-class"></a>Klasa RNDIS urządzenia USB

Klasa RNDIS urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzenie ethernet. Ta klasa jest oparta na zastrzeżonej implementacji firmy Microsoft i jest specyficzna dla Windows platform.

Framework urządzeń zgodnych ze standardem RNDIS musi być zadeklarowana przez stos urządzenia. Przykład można znaleźć poniżej.

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

Klasa RNDIS używa bardzo podobnego podejścia do deskryptora urządzeń do dysków CDC-ACM i CDC-ECM, a także wymaga deskryptora IAD. Zobacz klasę CDC-ACM, aby uzyskać definicję i wymagania dotyczące deskryptora urządzenia.

Aktywacja klasy RNDIS jest następująca.

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

Podobnie jak w przypadku CDC-ECM, klasa RNDIS wymaga 2 węzłów, jednego lokalnego i jednego zdalnego, ale nie jest wymagany deskryptor ciągu opisujący węzeł zdalny.

Jednak ze względu na zastrzeżony mechanizm obsługi komunikatów firmy Microsoft wymagane są pewne dodatkowe parametry. Najpierw należy przekazano identyfikator dostawcy. Podobnie wersja sterownika RNDIS. Należy również podać ciąg dostawcy.

Klasa RNDIS ma wbudowane interfejsy API do przesyłania danych na oba sposoby, ale są one ukryte w aplikacji, ponieważ aplikacja użytkownika będzie komunikować się z urządzeniem USB Ethernet za pośrednictwem systemu NetX.

Klasa USBX RNDIS jest ściśle powiązana Azure RTOS stosem sieciowym NetX. Aplikacja używająca klasy NetX i USBX RNDIS aktywuje stos sieci NetX w zwykły sposób, ale dodatkowo musi aktywować stos sieciowy USB w następujący sposób.

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

Stos sieciOWY USB musi być aktywowany tylko raz i nie jest specyficzny dla RNDIS, ale jest wymagany przez dowolną klasę USB, która wymaga usług NetX.

Klasa RNDIS nie zostanie rozpoznana przez hosty MAC OS i Linux, ponieważ jest specyficzna dla systemów operacyjnych firmy Microsoft. Na platformach Windows plik inf musi być obecny na hoście, który odpowiada deskryptorze urządzenia. Firma Microsoft dostarcza szablon dla klasy RNDIS i można go znaleźć w usbx_windows_host_files katalogu. W przypadku najnowszej wersji Windows należy użyć pliku RNDIS_Template.inf. Ten plik należy zmodyfikować, aby odzwierciedlał identyfikator PID/VID używany przez urządzenie. Identyfikator PID/VID będzie specyficzny dla klienta końcowego, gdy firma i produkt zostaną zarejestrowane przy użyciu portu USB-IF. W pliku inf pola do zmodyfikowania znajdują się tutaj.

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

W ramach struktury urządzeń urządzenia RNDIS identyfikator PID/VID jest przechowywany w deskryptorze urządzenia (zobacz deskryptor urządzenia zadeklarowany powyżej)

Gdy system hosta USB odnajduje urządzenie USB RNDIS, zainstaluje interfejs sieciowy, a urządzenie może być używane ze stosem protokołu sieciowego. Aby uzyskać informacje referencyjne, zobacz system operacyjny hosta.

## <a name="usb-device-dfu-class"></a>Klasa DFU urządzenia USB

Klasa DFU urządzenia USB umożliwia systemowi hosta USB aktualizowanie oprogramowania układowego urządzenia na podstawie aplikacji hosta. Klasa DFU jest standardową klasą USB-IF.

Klasa USBX DFU jest stosunkowo prosta. Deskryptor urządzenia nie wymaga niczego oprócz punktu końcowego kontroli. W większości przypadków ta klasa będzie osadzona w urządzeniu złożonym USB. Urządzeniem może być coś, na przykład urządzenie magazynujące lub urządzenie comm, a dodany interfejs DFU może poinformować hosta, że jego oprogramowanie układowe może być aktualizowane na bieżąco.

Klasa DFU działa w 3 krokach. Najpierw urządzenie zainstaluje się w zwykły sposób przy użyciu wyeksportowanych klas. Aplikacja na hoście (Windows lub Linux) będzie wykonywać klasę DFU i wysyłać żądanie zresetowania urządzenia do trybu DFU. Urządzenie zniknie z magistrali przez krótki czas (wystarczająco, aby host i urządzenie wykryło sekwencję RESET), a po ponownym uruchomieniu będzie wyłącznie w trybie DFU, czekając na wysłanie uaktualnienia oprogramowania układowego przez aplikację hosta. Po zakończeniu uaktualniania oprogramowania układowego aplikacja hosta resetuje urządzenie, a po jego ponownej wyliczeniu urządzenie powraca do normalnego działania z nowym oprogramowaniem układowym.

Platformę urządzeń DFU będzie wyglądać tak.

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

W tym przykładzie deskryptor DFU nie jest skojarzony z żadnymi innymi klasami. Ma prosty deskryptor interfejsu i nie ma dołączonych innych punktów końcowych. Istnieje deskryptor funkcjonalny opisujący specyfikę funkcji DFU urządzenia.

Opis funkcji DFU jest następujący.

| Nazwa             | Przesunięcie  | Rozmiar | typ      | Opis |
|------------------|----------|------|-----------|------------|
| bmAttributes  | 2     | 1   | Pole bitowe | Bit 3: urządzenie wykona sekwencję odłączania magistrali po otrzymaniu DFU_DETACH żądania. Host nie może wystawiać resetu USB. (bitWillDetach) 0 = nie 1 = tak Bit 2: urządzenie może komunikować się za pośrednictwem portu USB po fazie erudycyjną. (bitManifestationTolerant) 0 = nie, musi być wyświetlony reset magistrali 1 = tak Bit 1: możliwość przekazywania (bitCanUpload) 0 = nie 1 = tak Bit 0: możliwość pobierania (bitCanDnload) 0 = nie 1 = tak  |
| wDetachTimeOut  | 3      | 2  | liczba    | Czas (w milisekundach) oznacza, że urządzenie będzie czekać po odebraniu DFU_DETACH żądania. Jeśli ten czas upłynie bez zresetowania usb, urządzenie zakończy fazę rekonfiguracji i wróci do normalnego działania. Reprezentuje to maksymalny czas oczekiwania urządzenia (w zależności od jego czasomierzy itp.). UsbX ustawia tę wartość na 1000 ms.  |
| wTransferSize  | 5      | 2  | liczba    | Maksymalna liczba bajtów akceptowanych przez urządzenie na operację zapisu \- kontrolki. USBX ustawia tę wartość na 64 bajty. |

Deklaracja klasy DFU jest następująca:

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

Klasa DFU musi współpracować z aplikacją oprogramowania układowego urządzenia specyficzną dla obiektu docelowego. W związku z tym definiuje kilka wywołań do odczytu i zapisu bloków oprogramowania układowego oraz do uzyskania stanu z aplikacji do aktualizacji oprogramowania układowego. Klasa DFU ma również funkcję wywołania zwrotnego powiadamiania, która informuje aplikację o rozpoczęciu i zakończeniu transferu oprogramowania układowego.

Poniżej znajduje się opis typowego przepływu aplikacji DFU.

![Przepływ aplikacji DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

Głównym wyzwaniem klasy DFU jest uzyskanie na hoście odpowiedniej aplikacji do pobrania oprogramowania układowego. Firma Microsoft nie dostarcza aplikacji ani usb-IF. Niektóre oprogramowanie shareware istnieje i działają względnie dobrze w systemie Linux i w mniejszym stopniu Windows.

W systemie Linux można użyć dfu-utils, które można znaleźć tutaj: Wiele informacji na temat dfu utils można również znaleźć pod [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) tym linkiem: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)

Implementacja DFU systemu Linux prawidłowo wykonuje sekwencję resetowania między hostem a urządzeniem, dlatego urządzenie nie musi tego robić. System Linux może zaakceptować wartość 0 dla *bitWillDetach* bmAttributes. Windows po drugiej stronie wymaga zresetowania urządzenia.

Na Windows rejestru USB musi być w stanie skojarzyć urządzenie USB z jego PID/VID i biblioteki USB, który będzie z kolei używany przez aplikację DFU. Można to łatwo zrobić za pomocą bezpłatnego narzędzia Zadig, które można znaleźć tutaj: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) .

Uruchomienie zadig po raz pierwszy spowoduje pokazanie tego ekranu:

![Uruchamianie zadig po raz pierwszy](./media/usbx-device-stack-supplemental/zadig.png)

Na liście urządzeń znajdź urządzenie i skojarz je ze sterownikiem systemu Windows libusb. Spowoduje to powiązanie identyfikatorów PID/VID urządzenia z biblioteką Windows USB używaną przez narzędzia DFU.

Aby uruchomić polecenie DFU, po prostu rozpakuj zamapowane narzędzia dfu do katalogu, upewniaj się, że biblioteka libusb dll również znajduje się w tym samym katalogu. Narzędzia DFU muszą być uruchamiane z pola DOS w wierszu polecenia.

Najpierw wpisz polecenie **dfu-util –l,** aby określić, czy urządzenie znajduje się na liście. Jeśli nie, uruchom zadig, aby upewnić się, że urządzenie znajduje się na liście i jest skojarzone z biblioteką USB. Powinien zostać wyświetlony ekran w następujący sposób:

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

Następnym krokiem będzie przygotowanie pliku do pobrania. Klasa USBX DFU nie wykonuje żadnej weryfikacji tego pliku i jest niezależny od jego formatu wewnętrznego. Ten plik oprogramowania układowego jest bardzo specyficzny dla obiektu docelowego, ale nie do DFU ani USBX.

Następnie można poinstruować dfu-util, aby wysłać plik, wpisując następujące polecenie:

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

Dfu-util powinien wyświetlać proces pobierania pliku, dopóki oprogramowanie układowe nie zostanie całkowicie pobrane.

## <a name="usb-device-pima-class-ptp-responder"></a>Klasa PIMA urządzenia USB (responder PTP)

Klasa PIMA urządzenia USB umożliwia systemowi hosta USB (inicjatorowi) połączenie z

Urządzenie PIMA (Resonder) do transferu plików multimedialnych. Klasa USBX Pima jest zgodna z klasą USB-IF PIMA 15740 znaną również jako klasa PTP (dla protokołu Picture Transfer Protocol).

Klasa PIMA po stronie urządzenia USBX obsługuje następujące operacje.

| Kod operacji                                    | Wartość | Opis                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO    | 0x1001  | Uzyskiwanie obsługiwanych operacji i zdarzeń urządzenia                                                         |
| UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION        | 0x1002  | Otwieranie sesji między hostem a urządzeniem                                                            |
| UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION       | 0x1003  | Zamykanie sesji między hostem a urządzeniem                                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS    | 0x1004  | Zwraca identyfikator magazynu dla urządzenia. UsbX PIMA używa tylko jednego identyfikatora magazynu |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO   | 0x1005  | Zwracanie informacji o obiekcie magazynu, takich jak maksymalna pojemność i wolne miejsce                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS    | 0x1006  | Zwracanie liczby obiektów zawartych w urządzeniu magazynującego                                              |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES | 0x1007  | Zwracanie tablicy uchwytów obiektów na urządzeniu magazynu                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO    | 0x1008  | Zwracanie informacji o obiekcie, takich jak nazwa obiektu, jego data utworzenia, data modyfikacji |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT          | 0x1009  | Zwracanie danych dotyczących określonego obiektu                                                         |
| UX_DEVICE_CLASS_PIMA_OC_GET_THUMB           | 0x100A  | Wysyłanie miniatury, jeśli jest dostępna dla obiektu                                                           |
| UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT       | 0x100B  | Usuwanie obiektu na nośniku                                                                             |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO   | 0x100C  | Wysyłanie do urządzenia informacji o obiekcie w celu jego utworzenia na nośniku                              |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT         | 0x100D  | Wysyłanie danych dla obiektu do urządzenia                                                                     |
| UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE        | 0x100F  | Czyszczenie nośnika urządzenia                                                                                    |
| UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE        | 0x0110  | Resetowanie urządzenia docelowego                                                                                   |

| Kod operacji                                         | Wartość | Opis |
|--------------------------------------------------------|-------|-----------------------------------------|
| UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION       | 0x4001  | Anuluje bieżącą transakcję                                                 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED             | 0x4002  | Obiekt został dodany do nośnika urządzenia i może zostać pobrany przez hosta\. |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED           | 0x4003  | Obiekt został usunięty z nośnika urządzenia                                |
| UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED              | 0x4004  | Nośnik został dodany do urządzenia                                            |
| UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED            | 0x4005  | Nośnik został usunięty z urządzenia                                        |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED     | 0x4006  | Właściwości urządzenia zostały zmienione                                                  |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED     | 0x4007  | Informacje o obiekcie uległy zmianie                                               |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE      | 0x4008  | Urządzenie zostało zmienione                                                            |
| UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER | 0x4009  | Urządzenie żąda przeniesienia obiektu z hosta                     |
| UX_DEVICE_CLASS_PIMA_EC_STORE_FULL               | 0x400A  | Raporty urządzenia: nośnik jest pełny                                                |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET             | 0x400B  | Raporty dotyczące urządzenia, które zostało zresetowane                                                     |
| UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED    | 0x400C  | Storage informacje na urządzeniu zostały zmienione                                   |
| UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE         | 0x400D  | Przechwytywanie jest ukończone                                                            |

Klasa urządzenia USBX PIMA używa wątku TX do nasłuchiwać poleceń PIMA z hosta.

Polecenie PIMA składa się z bloku poleceń, bloku danych i fazy stanu.

Funkcja ux_device_class_pima_thread publikuje żądanie do stosu w celu otrzymania polecenia PIMA po stronie hosta. Polecenie PIMA jest zdekodowane i zweryfikowane pod tematem zawartości. Jeśli blok poleceń jest prawidłowy, jest odgałęzienia do odpowiedniej procedury obsługi poleceń.

Większość poleceń PIMA można wykonać tylko wtedy, gdy sesja została otwarta przez hosta. Jedynym wyjątkiem jest polecenie **,** UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO . W przypadku implementacji USBX PIMA w dowolnym momencie można otworzyć tylko jedną sesję między inicjatorem i responderem. Wszystkie transakcje w ramach jednej sesji są blokowane i nie można rozpocząć nowej transakcji przed ukończeniem poprzedniej.

Transakcje PIMA składają się z 3 faz: fazy poleceń, opcjonalnej fazy danych i fazy odpowiedzi. Jeśli istnieje faza danych, może być tylko w jednym kierunku.

Inicjator zawsze określa przepływ operacji PIMA, ale responder może inicjować zdarzenia z powrotem do inicjatora, aby poinformować o zmianach stanu, które miały miejsce podczas sesji.

Na poniższym diagramie przedstawiono transfer obiektu danych między hostem a klasą urządzenia PIMA.

![Transakcje PIMA](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a>Inicjowanie klasy urządzenia PIMA

Klasa urządzenia PIMA wymaga pewnych parametrów dostarczonych przez aplikację podczas inicjowania.

Poniższe parametry opisują informacje o urządzeniu i magazynie.

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

Klasa PIMA wymaga również rejestracji wywołania zwrotnego w aplikacji w celu informowania aplikacji o niektórych zdarzeniach lub pobierania/przechowywania danych z/do nośnika lokalnego. Wywołania zwrotne są następujące.

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

W poniższym przykładzie pokazano, jak zainicjować stronę klienta PIMA. W tym przykładzie użyto aplikacji Pictbridge jako klienta dla systemu PIMA.

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

Dodawanie obiektu i wysyłanie zdarzenia do hosta

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa PIMA musi dodać obiekt i poinformować hosta.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima
- **object_handle:** uchwyt obiektu.

### <a name="example"></a>Przykład

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a>ux_device_class_pima_object_number_get

Pobieranie numeru obiektu z aplikacji

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa PIMA musi pobrać liczbę obiektów w systemie lokalnym i wysłać ją z powrotem do hosta.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima
- **object_number:** Adres liczby obiektów do zwrócenia

### <a name="example"></a>Przykład

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a>ux_device_class_pima_object_handles_get

Zwracanie tablicy uchwytów obiektu

### <a name="prototype"></a>Prototype

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa PIMA musi pobrać obiekt obsługuje tablicę w systemie lokalnym i wysłać ją z powrotem do hosta.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima.
- **object_handles_format_code:** formatowanie kodu dla uchwytów
- **object_handles_association:** Kod skojarzenia obiektu
- **object_handle_array:** adres miejsca przechowywania dojść
- **object_handles_max_number:** maksymalna liczba dojść w tablicy

### <a name="example"></a>Przykład

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a>ux_device_class_pima_object_info_get

Zwracanie informacji o obiekcie

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa PIMA musi pobrać obiekt obsługuje tablicę w systemie lokalnym i wysłać ją z powrotem do hosta.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima.
- **object_handles:** Dojście do obiektu
- **object**: Adres wskaźnika obiektu

### <a name="example"></a>Przykład

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

Zwracanie danych obiektu

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa PIMA musi pobrać dane obiektu w systemie lokalnym i wysłać je z powrotem do hosta.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima.
- **object_handle:** Dojście do obiektu
- **object_buffer:** Adres buforu obiektu
- **object_length_requested:** Długość danych obiektu żądana przez klienta w aplikacji
- **object_actual_length:** Długość danych obiektu zwrócona przez aplikację

### <a name="example"></a>Przykład

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

Host wysyła informacje o obiekcie

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa PIMA musi odbierać informacje o obiekcie w systemie lokalnym na potrzeby przechowywania w przyszłości.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima
- **object**: Wskaźnik do obiektu
- **object_handle:** Dojście do obiektu

### <a name="example"></a>Przykład

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

Host wysyła dane obiektu

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa PIMA musi odbierać dane obiektu w systemie lokalnym na potrzeby magazynu.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima
- **object_handle:** Dojście do obiektu
- **faza**: faza transferu (aktywna lub ukończona)
- **object_buffer:** Adres buforu obiektu
- **object_offset:** Adres danych
- **object_length:** Długość danych obiektu wysyłanych przez aplikację

### <a name="example"></a>Przykład

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

Usuwanie obiektu lokalnego

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klasa PIMA musi usunąć obiekt w magazynie lokalnym.

### <a name="parameters"></a>Parametry

- **pima:** Wskaźnik do wystąpienia klasy pima
- **object_handle:** Dojście obiektu

### <a name="example"></a>Przykład

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a>Klasa audio urządzenia USB

Klasa Audio urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem audio. Ta klasa jest oparta na standardzie USB i USB Audio Class 1.0 lub 2.0 Standard.

Platformę urządzeń zgodnych z dźwiękami USB należy zadeklarować w stosie urządzenia. Poniżej podano przykładową prelegentę audio 2.0:

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

Klasa Audio używa złożonej struktury urządzeń do grupowania interfejsów (sterowania i przesyłania strumieniowego). W związku z tym należy zachować ostrożność podczas definiowania deskryptora urządzenia. UsbX opiera się na deskryptorze IAD, aby wiedzieć wewnętrznie, jak powiązać interfejsy. Deskryptor IAD należy zadeklarować przed interfejsami (interfejsem AudioControl, po którym następuje co najmniej jeden interfejs AudioStreaming) i zawierać pierwszy interfejs klasy Audio (interfejs AudioControl) oraz ile interfejsów jest dołączonych.

Sposób działania klasy audio zależy od tego, czy urządzenie wysyła, czy odbiera dźwięk, ale w obu przypadkach używa standardu FIFO do przechowywania buforów ramek audio: jeśli urządzenie wysyła dźwięk do hosta, aplikacja dodaje bufory ramek audio do pliku FIFO, które są później wysyłane do hosta przez USBX; Jeśli urządzenie odbiera dźwięk z hosta, usbx dodaje bufory ramek audio odebrane z hosta do pliku FIFO, które są później odczytywane przez aplikację. Każdy strumień audio ma własny tryb FIFO, a każdy bufor ramek dźwiękowych składa się z wielu próbek.

Inicjowanie klasy Audio oczekuje następujących części.

1. Klasa audio oczekuje następujących parametrów przesyłania strumieniowego:

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. Klasa audio oczekuje następujących parametrów funkcji.

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_audio_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   Wywołanie zwrotne żądania sterowania zdefiniowane przez aplikację ***(ux_device_class_audio_control_process ;*** ustawione w poprzednim przykładzie) jest wywoływane, gdy stos odbiera żądanie sterowania z hosta. Jeśli żądanie zostanie zaakceptowane i obsłużone (potwierdzone lub wstrzymane), wywołanie zwrotne musi zwrócić powodzenie, w przeciwnym razie powinien zostać zwrócony błąd.

   Proces żądania sterowania specyficzny dla klasy jest definiowany jako wywołanie zwrotne zdefiniowane przez aplikację, ponieważ żądania sterowania bardzo różnią się między wersjami audio USB, a duża część procesu żądania odnosi się do struktury urządzenia. Aplikacja powinna poprawnie obsługiwać żądania, aby urządzenie działało.

   Ponieważ w przypadku urządzenia audio częstotliwość regulacji głośności, wyciszenia i próbkowania to typowe żądania sterowania, proste, wewnętrznie zdefiniowane wywołania zwrotne dla różnych wersji audio USB są wprowadzane w kolejnych sekcjach dla aplikacji do użycia. Aby uzyskać więcej **informacji, zobacz*** ux_device_class_audio10_control_process _ i _ *_ux_device_class_audio_control_request_**.

W ramach struktury urządzenia Audio urządzenie PID/VID są przechowywane w deskryptorze urządzenia (zobacz deskryptor urządzenia zadeklarowany powyżej).

Gdy system hosta USB odnajduje urządzenie AUDIO USB i zainstaluje klasę audio, urządzenie może być używane z dowolnym odtwarzaczem audio lub rejestratorem (w zależności od struktury). Aby uzyskać informacje, zobacz system operacyjny hosta.

Interfejsy API klasy Audio są zdefiniowane poniżej.

## <a name="ux_device_class_audio_read_thread_entry"></a>ux_device_class_audio_read_thread_entry

Wpis wątku do odczytywania danych dla funkcji Audio.

### <a name="prototype"></a>Prototype

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Opis

Ta funkcja jest przekazywana do parametru inicjowania strumienia audio, jeśli wymagane jest odczytanie dźwięku z hosta. Wewnętrznie wątek jest tworzony z tą funkcją jako funkcją wpisu; Sam wątek odczytuje dane audio za pośrednictwem izochronicznego punktu końcowego OUT w funkcji Audio.

### <a name="parameters"></a>Parametry

- **audio_stream:** wskaźnik do wystąpienia strumienia audio.

### <a name="example"></a>Przykład

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a>ux_device_class_audio_write_thread_entry

Wpis wątku do zapisywania danych dla funkcji Audio

### <a name="prototype"></a>Prototype

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Opis

Ta funkcja jest przekazywana do parametru inicjowania strumienia audio, jeśli wymagane jest zapisywanie dźwięku na hoście. Wewnętrznie wątek jest tworzony z tą funkcją jako funkcją wpisu; Sam wątek zapisuje dane audio za pośrednictwem izochronicznego punktu końcowego IN w funkcji Audio.

### <a name="parameters"></a>Parametry

- **audio_stream:** wskaźnik do wystąpienia strumienia audio.

### <a name="example"></a>Przykład

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a>ux_device_class_audio_stream_get

Uzyskiwanie określonego wystąpienia strumienia dla funkcji Audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a>Opis

Ta funkcja służy do uzyskania wystąpienia strumienia klasy audio.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia audio
- **stream_index:** Stream instance index based on 0 (Indeks wystąpienia usługi Stream oparty na 0)
- **strumień:** wskaźnik do buforu do przechowywania wskaźnika wystąpienia strumienia audio

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a>ux_device_class_audio_reception_start

Uruchamianie odbierania danych audio dla strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Opis

Ta funkcja służy do uruchamiania odczytywania danych audio w strumieniach audio.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO jest pełny.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a>ux_device_class_audio_sample_read8

Odczytywanie przykładu 8-bitowego ze strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a>Opis

Ta funkcja odczytuje przykładowe dane 8-bitowego dźwięku z określonego strumienia.

W szczególności odczytuje przykładowe dane z bieżącego bufora ramek audio w fifo. Podczas odczytywania ostatniej próbki w ramce audio ramka zostanie automatycznie wyzwizowana, aby można było jej użyć do akceptowania większej liczby danych z hosta.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.
- **bufor:** wskaźnik do buforu, aby zapisać bajt próbki.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO ma wartość null.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a>ux_device_class_audio_sample_read16

Odczytywanie przykładu 16-bitowego ze strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a>Opis

Ta funkcja odczytuje przykładowe dane 16-bitowego audio z określonego strumienia.

W szczególności odczytuje przykładowe dane z bieżącego bufora ramek audio w fifo. Podczas odczytywania ostatniej próbki w ramce audio ramka zostanie automatycznie wyzwizowana, aby można było jej użyć do akceptowania większej liczby danych z hosta.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.
- **buffer**: wskaźnik do buforu w celu zapisania przykładu 16-bitowego.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO ma wartość null.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a>ux_device_class_audio_sample_read24

Odczytywanie przykładu 24-bitowego ze strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Opis

Ta funkcja odczytuje przykładowe dane 24-bitowego dźwięku z określonego strumienia.

W szczególności odczytuje przykładowe dane z bieżącego bufora ramki audio w fifo. Podczas odczytywania ostatniej próbki w ramce dźwiękowej ramka zostanie automatycznie wyzwizowana, aby można było jej użyć do akceptowania większej liczby danych z hosta.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.
- **buffer**: wskaźnik do buforu, aby zapisać próbkę 3-bajtową.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO ma wartość null.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a>ux_device_class_audio_sample_read32

Odczytywanie przykładu 32-bitowego ze strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Opis

Ta funkcja odczytuje przykładowe dane 32-bitowego dźwięku z określonego strumienia.

W szczególności odczytuje przykładowe dane z bieżącego bufora ramki audio w fifo. Podczas odczytywania ostatniej próbki w ramce dźwiękowej ramka zostanie automatycznie wyzwizowana, aby można było jej użyć do akceptowania większej liczby danych z hosta.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.
- **bufor:** wskaźnik do buforu, aby zapisać dane 4-bajtowe.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO ma wartość null.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a>ux_device_class_audio_read_frame_get

Uzyskiwanie dostępu do ramki audio w strumieniu audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Opis

Ta funkcja zwraca pierwszy bufor ramek audio i jego długość w funkcji FIFO określonego strumienia. Po przetworzeniu danych przez aplikację należy ux_device_class_audio_read_frame_free w celu usunięcia buforu ramki w fifo.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.
- **frame_data:** Wskaźnik do wskaźnika danych, w który ma być zwracany wskaźnik danych.
- **frame_length:** wskaźnik do buforu, aby zapisać długość ramki w bajtach.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO ma wartość null.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a>ux_device_class_audio_read_frame_free

Free an audio frame buffer in Audio stream (Wolne buforu ramki audio w strumieniu audio)

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Opis

Ta funkcja pozwala uwolnić bufor ramek audio z przodu obrazu FIFO określonego strumienia, dzięki czemu może odbierać dane z hosta.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO ma wartość null.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a>ux_device_class_audio_transmission_start

Uruchamianie transmisji danych audio dla strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Opis

Ta funkcja jest używana do rozpoczęcia wysyłania danych audio zapisywanych do fifo w klasie audio.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO ma wartość null.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a>ux_device_class_audio_frame_write

Zapis ramki audio do strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a>Opis

Ta funkcja zapisuje ramkę w funkcji FIFO strumienia audio. Dane ramek są kopiowane do buforu dostępnego w fifo, aby można je było wysłać do hosta.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.
- **frame:** wskaźnik do danych ramek.
- **frame_length** Długość ramki w bajtach.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO jest pełny.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a>ux_device_class_audio_write_frame_get

Uzyskiwanie dostępu do ramki audio w strumieniu audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Opis

Ta funkcja pobiera adres ostatniego bufora ramki dźwiękowej fifo; Pobiera również długość buforu ramki audio. Po wypełnieniu przez aplikację buforu ramki  dźwiękowej żądanym ux_device_class_audio_write_frame_commit należy użyć ux_device_class_audio_write_frame_commit do dodania/zatwierdzenia buforu ramki do fifo.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.
- **frame_data:** Wskaźnik do wskaźnika danych ramki, aby zwrócić wskaźnik danych ramki.
- **frame_length** Wskaźnik do buforu, aby zaoszczędzić długość ramki w liczbie bajtów .

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO jest pełny.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a>ux_device_class_audio_write_frame_commit

Zatwierdzanie buforu ramek audio w strumieniu audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a>Opis

Ta funkcja dodaje/zatwierdza ostatni bufor ramki dźwiękowej do fifo, aby bufor był gotowy do przeniesienia do hosta; Zanotuj, że ostatni bufor ramek dźwiękowych powinien zostać wypełniony za pośrednictwem ux_device_class_write_frame_get.

### <a name="parameters"></a>Parametry

- **stream:** wskaźnik do wystąpienia strumienia audio.
- **length:** liczba bajtów gotowych do użycia w buforze.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Interfejs nie istnieje.
- **UX_BUFFER_OVERFLOW** (0x5d) FIFO to fssull.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a>ux_device_class_audio10_control_process

Przetwarzanie żądań sterowania USB Audio 1.0

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a>Opis

Ta funkcja zarządza podstawowymi żądaniami wysyłanymi przez hosta w punkcie końcowym sterowania przy użyciu określonego typu USB Audio 1.0.

Funkcje audio 1.0 woluminu i wyciszania żądań są przetwarzane w funkcji. Podczas przetwarzania żądań wstępnie zdefiniowane dane przekazane przez ostatni parametr (grupę) są używane do odpowiadania na żądania i przechowywania zmian kontroli.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia audio.
- **transfer:** wskaźnik do wystąpienia żądania przeniesienia.
- **group**: Grupa danych dla procesu żądania.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a>ux_device_class_audio20_control_process

Przetwarzanie żądań sterowania USB Audio 1.0

### <a name="prototype"></a>Prototype
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a>Opis

Ta funkcja zarządza podstawowymi żądaniami wysyłanymi przez hosta w punkcie końcowym sterowania przy użyciu określonego typu USB Audio 2.0.

Częstotliwość próbkowania audio 2.0 (zakładana jedna stała częstotliwość), funkcje woluminu i wyciszania żądań są przetwarzane w funkcji . Podczas przetwarzania żądań wstępnie zdefiniowane dane przekazane przez ostatni parametr (grupę) są używane do odpowiadania na żądania i przechowywania zmian kontroli.

### <a name="parameters"></a>Parametry

- **audio:** wskaźnik do wystąpienia audio.
- **transfer:** wskaźnik do wystąpienia żądania przeniesienia.
- **group**: Grupa danych dla procesu żądania.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
