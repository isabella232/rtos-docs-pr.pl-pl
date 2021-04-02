---
title: Rozdział 2 — zagadnienia dotyczące klas urządzeń USBX
description: Klasa RNDIS urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem Ethernet. Ta klasa jest oparta na implementacji zastrzeżonej firmy Microsoft i jest zależna od platformy systemu Windows.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 035492644a911eba3b1c62a79572bc7d4c55f6dd
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082221"
---
# <a name="chapter-2---usbx-device-class-considerations"></a>Rozdział 2 — zagadnienia dotyczące klas urządzeń USBX

## <a name="usb-device-rndis-class"></a>Klasa RNDIS urządzenia USB

Klasa RNDIS urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem Ethernet. Ta klasa jest oparta na implementacji zastrzeżonej firmy Microsoft i jest zależna od platformy systemu Windows.

Architektura urządzenia zgodna z RNDIS musi być zadeklarowana przez stos urządzeń. Poniżej znajduje się przykład.

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

Klasa RNDIS używa bardzo podobnego podejścia do deskryptora urządzenia do przechwytywania danych typu reklasy — ACM i przechwytywania-ECM, a także wymaga deskryptora IAD. Zapoznaj się z klasą przechwytywania zmian-ACM dla definicji i wymagań dla deskryptora urządzenia.

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

Podobnie jak w przypadku opcji Przeciąganie do ECM, Klasa RNDIS wymaga 2 węzłów, jednego lokalnego i jednego zdalnego, ale nie wymaga się posiadania deskryptora ciągu opisującego węzeł zdalny.

Jednak ze względu na własny mechanizm obsługi komunikatów firmy Microsoft wymagane są pewne dodatkowe parametry. Najpierw należy przesłać identyfikator dostawcy. Podobnie wersja sterownika RNDIS. Należy również udzielić ciągu dostawcy.

Klasa RNDIS ma wbudowane interfejsy API do przesyłania danych w obu kierunkach, ale są ukryte dla aplikacji, ponieważ aplikacja użytkownika komunikuje się z urządzeniem USB Ethernet za pośrednictwem usługi NetX.

Klasa USBX RNDIS jest ściśle związana z stosem sieci usługi Azure RTO NetX. Aplikacja, która korzysta z klasy NetX i USBX RNDIS, będzie aktywować stos sieci NetX w zwykły sposób, ale dodatkowo należy aktywować stos sieci USB w następujący sposób.

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

Stos sieci USB musi być aktywowany tylko raz i nie jest specyficzny dla RNDIS, ale jest wymagany przez dowolną klasę USB wymagającą usług NetX Services.

Klasa RNDIS nie zostanie rozpoznana przez hosty z systemem MAC OS i Linux zgodnie z konkretnymi systemami operacyjnymi firmy Microsoft. Na platformach systemu Windows plik inf musi znajdować się na hoście, który jest zgodny z deskryptorem urządzenia. Firma Microsoft dostarcza szablon klasy RNDIS i znajduje się w katalogu usbx_windows_host_files. W przypadku nowszej wersji systemu Windows należy użyć pliku RNDIS_Template. inf. Ten plik musi zostać zmodyfikowany w celu odzwierciedlenia identyfikatora PID/VID używanego przez urządzenie. Identyfikator PID/VID będzie charakterystyczny dla klienta końcowego, gdy firma i produkt zostaną zarejestrowane przy użyciu portu USB. W pliku inf pola do zmodyfikowania znajdują się tutaj.

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

W środowisku urządzenia urządzenia RNDIS Identyfikator PID/VID jest przechowywany w deskryptorze urządzenia (patrz deskryptor urządzenia zadeklarowany powyżej)

W przypadku odnajdywania urządzenia USB RNDIS przez systemy hosta USB program zainstaluje interfejs sieciowy, a urządzenie może być używane z stosem protokołu sieciowego. Aby uzyskać informacje, zobacz system operacyjny hosta.

## <a name="usb-device-dfu-class"></a>Klasa DFU urządzenia USB

Klasa DFU urządzenia USB umożliwia systemowi hosta USB aktualizowanie oprogramowania układowego urządzenia w oparciu o aplikację hosta. Klasa DFU jest klasą standardową USB.

Klasa USBX DFU jest stosunkowo prosta. Deskryptor urządzenia IT nie wymaga żadnego punktu końcowego kontrolki. W większości przypadków ta klasa zostanie osadzona w urządzeniu kompozytowym USB. Urządzenie może być takie samo jak urządzenie magazynujące lub urządzenie komunikacyjne, a dodany interfejs DFU może poinformować hosta, że urządzenie może być zaktualizowane przez oprogramowanie układowe na bieżąco.

Klasa DFU działa w 3 krokach. Najpierw urządzenie jest instalowane jako normalne przy użyciu wyeksportowanej klasy. Aplikacja na hoście (Windows lub Linux) będzie korzystać z klasy DFU i wysyłać żądania resetowania urządzenia do trybu DFU. Urządzenie pozostanie nieprzerwanie z magistrali przez krótki czas (wystarczające dla hosta i urządzenia w celu wykrycia sekwencji RESETowania), a po ponownym uruchomieniu urządzenie będzie działać wyłącznie w trybie DFU, czekając na wysłanie przez aplikację hosta uaktualnienia oprogramowania układowego. Po zakończeniu uaktualniania oprogramowania układowego aplikacja hosta resetuje urządzenie i po ponownym wyliczeniu zostanie przywrócone jego normalne działanie z nowym oprogramowaniem układowym.

Platforma urządzeń DFU będzie wyglądać następująco.

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

W tym przykładzie deskryptor DFU nie jest skojarzony z żadną inną klasą. Ma prosty deskryptor interfejsu i nie dołączono do niego żadnych punktów końcowych. Istnieje deskryptor funkcjonalny opisujący szczegóły możliwości DFU urządzenia.

Opis funkcji DFU są następujące.

| Nazwa             | Przesunięcie  | Rozmiar | typ      | Opis |
|------------------|----------|------|-----------|------------|
| bmAttributes  | 2     | 1   | Pole bitowe | Bit 3: urządzenie przeprowadzi sekwencję odłączania do magistrali, gdy odbierze żądanie DFU_DETACH. Host nie może wydać resetu USB. (bitWillDetach) 0 = No 1 = Yes bit 2: urządzenie może komunikować się za pośrednictwem portu USB po fazie manifestu. (bitManifestationTolerant) 0 = nie, należy zobaczyć Resetowanie magistrali 1 = Yes bit 1: możliwe do przekazania (bitCanUpload) 0 = 1 = Yes bit 0: pobieranie z obsługą (bitCanDnload) 0 = No 1 = tak  |
| wDetachTimeOut  | 3      | 2  | liczba    | Czas (w milisekundach), po upływie którego urządzenie będzie oczekiwać po odebraniu żądania DFU_DETACH. Jeśli ten czas upłynie bez resetowania USB, urządzenie zakończy fazę ponownej konfiguracji i wróci do normalnego działania. Oznacza to maksymalny czas oczekiwania urządzenia (w zależności od jego czasomierzy itp.). USBX ustawia tę wartość na 1000 ms.  |
| wTransferSize  | 5      | 2  | liczba    | Maksymalna liczba bajtów akceptowanych przez urządzenie dla \- operacji zapisu kontroli. USBX ustawia tę wartość na 64 bajtów. |

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

Klasa DFU musi współpracować z aplikacją oprogramowania układowego urządzenia specyficzną dla elementu docelowego. W związku z tym definiuje kilka wywołań z powrotem do odczytu i zapisu bloków oprogramowania układowego oraz do pobierania stanu z aplikacji oprogramowania układowego. Klasa DFU ma również funkcję powiadamiania zwrotnego, aby poinformować aplikację, gdy wystąpi rozpoczęcie i zakończenie transferu oprogramowania układowego.

Poniżej znajduje się opis typowego przepływu aplikacji DFU.

![Przepływ aplikacji DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

Najważniejszym wyzwaniem klasy DFU jest uzyskanie odpowiedniej aplikacji na hoście w celu przeprowadzenia pobierania oprogramowania układowego. Firma Microsoft nie oferuje aplikacji ani magistrali USB — Jeśli nie. Niektóre "shareware" istnieją i działają odpowiednio w systemie Linux i w mniejszym stopniu w przypadku systemu Windows.

W systemie Linux jeden z nich może używać DFU-narzędzia, które można znaleźć tutaj: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) wiele informacji na temat DFU można znaleźć na tym linku: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)

Implementacja systemu Linux DFU wykonuje prawidłowo sekwencję resetowania między hostem i urządzeniem, dlatego nie trzeba tego robić. System Linux może akceptować bmAttributes *bitWillDetach* na 0. System Windows po drugiej stronie wymaga, aby urządzenie przeprowadził Reset.

W systemie Windows rejestr USB musi być w stanie skojarzyć urządzenie USB z jego identyfikatorem PID/VID i biblioteką USB, która będzie używana przez aplikację DFU. Można to łatwo zrobić przy użyciu bezpłatnego narzędzia Zadig, które można znaleźć tutaj: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) .

Po pierwszym uruchomieniu programu Zadig zostanie wyświetlony następujący ekran:

![Uruchamianie Zadig po raz pierwszy](./media/usbx-device-stack-supplemental/zadig.png)

Z listy urządzeń Znajdź urządzenie i skojarz je z libusbm sterownikiem systemu Windows. Spowoduje to powiązanie identyfikatora PID/VID urządzenia z biblioteką USB systemu Windows używaną przez narzędzia DFU.

Aby obsłużyć polecenie DFU, po prostu Rozpakuj spakowane narzędzia DFU do katalogu, aby upewnić się, że biblioteka libusb dll znajduje się w tym samym katalogu. Narzędzia DFU muszą być uruchamiane z okna DOS w wierszu polecenia.

Najpierw wpisz polecenie **DFU-util – l** , aby określić, czy urządzenie jest wyświetlane. Jeśli nie, uruchom program Zadig, aby upewnić się, że urządzenie jest wyświetlane i skojarzone z biblioteką USB. Powinien zostać wyświetlony ekran w następujący sposób:

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

Następnym krokiem będzie przygotowanie pliku do pobrania. Klasa USBX DFU nie wykonuje żadnej weryfikacji dla tego pliku i jest niezależny od jej format wewnętrzny. Ten plik oprogramowania układowego jest bardzo specyficzny dla elementu docelowego, ale nie do DFU ani do USBX.

Następnie DFU-util można wysłać do pliku, wpisując następujące polecenie:

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

DFU-util powinien wyświetlić proces pobierania pliku, dopóki oprogramowanie układowe nie zostanie całkowicie pobrane.

## <a name="usb-device-pima-class-ptp-responder"></a>Klasa PIMA urządzenia USB (obiekt odpowiadający PTP)

Klasa PIMA urządzenia USB umożliwia systemowi hosta USB (inicjator) łączenie się z

Urządzenie PIMA (Resonder) do transferowania plików multimedialnych. Klasa USBX Pima jest zgodna z klasą protokołu PTP, jeśli PIMA 15740, zwaną również klasą NNTP (w celu przesyłania obrazów).

Klasa PIMA po stronie urządzenia USBX obsługuje następujące operacje.

| Kod operacji                                    | Wartość | Opis                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO    | 0x1001  | Uzyskaj obsługiwane operacje i zdarzenia dotyczące urządzeń                                                         |
| UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION        | 0x1002  | Otwieranie sesji między hostem i urządzeniem                                                            |
| UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION       | 0x1003  | Zamykanie sesji między hostem a urządzeniem                                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS    | 0x1004  | Zwraca identyfikator magazynu dla urządzenia. USBX PIMA używa tylko jednego identyfikatora magazynu |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO   | 0x1005  | Zwróć informacje o obiekcie magazynu, takie jak Maksymalna pojemność i wolne miejsce                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS    | 0x1006  | Zwróć liczbę obiektów zawartych w urządzeniu magazynującym                                              |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES | 0x1007  | Zwróć tablicę dojść do obiektów na urządzeniu magazynującym                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO    | 0x1008  | Zwracają informacje dotyczące obiektu, takie jak nazwa obiektu, jego Data utworzenia, Data modyfikacji |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT          | 0x1009  | Zwracanie danych odnoszących się do określonego obiektu                                                         |
| UX_DEVICE_CLASS_PIMA_OC_GET_THUMB           | 0x100A  | Wyślij miniaturę, jeśli jest dostępna o obiekcie                                                           |
| UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT       | 0x100B  | Usuwanie obiektu na nośniku                                                                             |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO   | 0x100C  | Wyślij do informacji o urządzeniu dla jego utworzenia na nośniku                              |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT         | 0x100D  | Wyślij dane dla obiektu do urządzenia                                                                     |
| UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE        | 0x100F  | Czyszczenie nośnika urządzenia                                                                                    |
| UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE        | 0x0110  | Zresetuj urządzenie docelowe                                                                                   |

| Kod operacji                                         | Wartość | Opis |
|--------------------------------------------------------|-------|-----------------------------------------|
| UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION       | 0x4001  | Anuluje bieżącą transakcję                                                 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED             | 0x4002  | Obiekt został dodany do nośnika urządzenia i może być pobrany przez host\. |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED           | 0x4003  | Usunięto obiekt z nośnika urządzenia                                |
| UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED              | 0x4004  | Dodano nośnik do urządzenia                                            |
| UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED            | 0x4005  | Usunięto nośnik z urządzenia                                        |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED     | 0x4006  | Zmieniono właściwości urządzenia                                                  |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED     | 0x4007  | Informacje o obiekcie zostały zmienione                                               |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE      | 0x4008  | Urządzenie zostało zmienione                                                            |
| UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER | 0x4009  | Urządzenie żąda transferu obiektu z hosta                     |
| UX_DEVICE_CLASS_PIMA_EC_STORE_FULL               | 0x400A  | Urządzenie raportuje nośnik jest zapełniony                                                |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET             | 0x400B  | Raporty urządzenia, które zostały zresetowane                                                     |
| UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED    | 0x400C  | Informacje o magazynie zostały zmienione na urządzeniu                                   |
| UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE         | 0x400D  | Przechwytywanie zostało zakończone                                                            |

Klasa urządzenia USBX PIMA używa wątku TX do nasłuchiwania poleceń PIMA z hosta.

Polecenie PIMA składa się z bloku poleceń, bloku danych i fazy stanu.

Funkcja ux_device_class_pima_thread ogłasza żądanie do stosu, aby otrzymać polecenie PIMA ze strony hosta. Polecenie PIMA jest zdekodowane i zweryfikowane pod kątem zawartości. Jeśli blok poleceń jest prawidłowy, rozgałęzienia do odpowiedniej procedury obsługi poleceń.

Większość poleceń PIMA można wykonać tylko wtedy, gdy sesja została otwarta przez hosta. Jedynym wyjątkiem jest polecenie **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**. W przypadku implementacji USBX PIMA można otworzyć tylko jedną sesję między inicjatorem a obiektem odpowiadającym w dowolnym momencie. Wszystkie transakcje w ramach jednej sesji są blokowane i nie można rozpocząć nowej transakcji przed ukończeniem poprzedniej.

Transakcje PIMA składają się z 3 faz, fazy polecenia, opcjonalnej fazy danych i fazy odpowiedzi. Jeśli faza danych jest obecna, może ona znajdować się tylko w jednym kierunku.

Inicjator zawsze określa przepływ operacji PIMA, ale obiekt odpowiadający może inicjować zdarzenia z powrotem do inicjatora, aby poinformować o zmianach stanu, które wystąpiły podczas sesji.

Na poniższym diagramie przedstawiono transfer obiektu danych między hostem a klasą urządzenia PIMA.

![PIMA transakcji](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a>Inicjalizacja klasy urządzenia PIMA

Klasa urządzenia PIMA wymaga pewnych parametrów dostarczonych przez aplikację podczas inicjalizacji.

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

Klasa PIMA wymaga również rejestracji wywołania zwrotnego w aplikacji w celu powiadomienia aplikacji o określonych zdarzeniach lub pobrania/przechowania danych z/do nośnika lokalnego. Wywołania zwrotne są następujące.

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

Poniższy przykład pokazuje, jak zainicjować po stronie klienta PIMA. Ten przykład używa technologii PictBridge jako klienta dla PIMA.

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

Ta funkcja jest wywoływana, gdy Klasa PIMA musi dodać obiekt i poinformować hosta.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima
- **object_handle**: uchwyt obiektu.

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

Ta funkcja jest wywoływana, gdy Klasa PIMA musi pobierać liczbę obiektów w systemie lokalnym i wysyłać ją z powrotem do hosta.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima
- **object_number**: adres liczby obiektów do zwrócenia

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

Zwróć tablicę uchwytów obiektów

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

Ta funkcja jest wywoływana, gdy Klasa PIMA musi pobrać obiekt obsługujący tablicę w systemie lokalnym i wysyłać ją z powrotem do hosta.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **object_handles_format_code**: Formatuj kod dla uchwytów
- **object_handles_association**: Kod powiązania obiektu
- **object_handle_array**: adres, na którym mają być przechowywane uchwyty
- **object_handles_max_number**: Maksymalna liczba dojść w tablicy

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

Zwróć informacje o obiekcie

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy Klasa PIMA musi pobrać obiekt obsługujący tablicę w systemie lokalnym i wysyłać ją z powrotem do hosta.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **object_handles**: uchwyt obiektu
- **obiekt**: adres wskaźnika obiektu

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

Ta funkcja jest wywoływana, gdy Klasa PIMA musi pobrać dane obiektu w systemie lokalnym i wysłać je z powrotem do hosta.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima.
- **object_handle**: uchwyt obiektu
- **object_buffer**: adres buforu obiektów
- **object_length_requested**: długość danych obiektu żądana przez klienta do aplikacji
- **object_actual_length**: długość danych obiektu zwracana przez aplikację

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

Ta funkcja jest wywoływana, gdy Klasa PIMA musi odbierać informacje o obiekcie w systemie lokalnym w celu przechowywania w przyszłości.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima
- **Object**: wskaźnik do obiektu
- **object_handle**: uchwyt obiektu

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

Ta funkcja jest wywoływana, gdy Klasa PIMA musi odbierać dane obiektów w systemie lokalnym dla magazynu.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima
- **object_handle**: uchwyt obiektu
- **faza**: faza transferu (aktywna lub ukończona)
- **object_buffer**: adres buforu obiektów
- **object_offset**: adres danych
- **object_length**: długość danych obiektu wysłana przez aplikację

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

Ta funkcja jest wywoływana, gdy Klasa PIMA musi usunąć obiekt z magazynu lokalnego.

### <a name="parameters"></a>Parametry

- **Pima**: wskaźnik do wystąpienia klasy Pima
- **object_handle**: uchwyt obiektu

### <a name="example"></a>Przykład

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a>Klasa audio urządzenia USB

Klasa audio urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem audio. Ta klasa jest oparta na standardowym standardzie USB i USB audio klasy 1,0 lub 2,0.

Architektura urządzenia zgodna z dźwiękiem USB musi być zadeklarowana przez stos urządzeń. Przykładowy głośnik audio 2,0:

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

Klasa audio używa złożonej struktury urządzenia do grupowania interfejsów (kontroli i przesyłania strumieniowego). W związku z tym należy wziąć pod uwagę podczas definiowania deskryptora urządzenia. USBX opiera się na deskryptorze IAD, aby wiedzieć, jak powiązać interfejsy. Deskryptor IAD należy zadeklarować przed interfejsami (interfejsem AudioControl, po którym następuje co najmniej jeden interfejs AudioStreaming) i zawierać pierwszy interfejs klasy audio (interfejs AudioControl) oraz liczbę podłączonych interfejsów.

Sposób działania klasy audio zależy od tego, czy urządzenie wysyła lub odbierało dźwięk, ale oba przypadki używają FIFO do przechowywania buforów ramek audio: Jeśli urządzenie wysyła dźwięk do hosta, aplikacja dodaje bufory ramki audio do FIFO, które są później wysyłane do hosta przez USBX; Jeśli urządzenie odbiera dźwięk z hosta, USBX dodaje bufory ramki audio otrzymane od hosta do FIFO, które są później odczytywane przez aplikację. Każdy strumień audio ma własną FIFO, a każdy bufor ramki audio składa się z wielu przykładów.

Inicjalizacja klasy audio oczekuje następujących części.

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

   Zdefiniowane przez aplikację wywołanie zwrotne żądania sterowania (***ux_device_class_audio_control_process***; ustawione w poprzednim przykładzie) jest wywoływane, gdy stos odbiera żądanie sterowania od hosta. Jeśli żądanie zostało zaakceptowane i obsłużone (potwierdzone lub zawiesić), wywołanie zwrotne musi zwracać sukces, w przeciwnym razie błąd powinien zostać zwrócony.

   Proces żądania kontroli specyficzny dla klasy jest zdefiniowany jako wywołanie zwrotne zdefiniowane przez aplikację, ponieważ żądania sterujące są bardzo różne w różnych wersjach audio USB, a duża część procesu żądania odnosi się do platformy urządzeń. Aplikacja powinna prawidłowo obsługiwać żądania, aby zapewnić funkcjonalność urządzenia.

   Ze względu na to, że w przypadku urządzenia audio dyski, wyciszenie i częstotliwość próbkowania są typowymi żądaniami kontroli, proste, zdefiniowane wewnętrznie wywołania zwrotne dla różnych wersji audio USB są wprowadzane w kolejnych sekcjach dla aplikacji, które mają być używane. Aby uzyskać więcej informacji, zobacz ***ux_device_class_audio10_control_process** _ i _ *_ux_device_class_audio_control_request_**.

W środowisku urządzenia audio Identyfikator PID/VID jest przechowywany w deskryptorze urządzenia (patrz deskryptor urządzenia zadeklarowany powyżej).

Gdy system hosta USB odnajduje urządzenie audio USB i instaluje klasę audio, urządzenie może być używane z dowolnym odtwarzaczem audio lub rejestratorem (w zależności od platformy). Aby uzyskać informacje, zobacz system operacyjny hosta.

Interfejsy API klasy audio są zdefiniowane poniżej.

## <a name="ux_device_class_audio_read_thread_entry"></a>ux_device_class_audio_read_thread_entry

Wpis wątku służący do odczytywania danych dla funkcji audio.

### <a name="prototype"></a>Prototype

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Opis

Ta funkcja jest przenoszona do parametru inicjowania strumienia audio, jeśli jest wymagane odczytanie dźwięku z hosta. Wewnętrznie wątek jest tworzony za pomocą tej funkcji jako funkcji Wejścia; sam wątek odczytuje dane audio za pomocą punktu końcowego Isochronous OUT w funkcji audio.

### <a name="parameters"></a>Parametry

- **audio_stream**: wskaźnik do wystąpienia strumienia audio.

### <a name="example"></a>Przykład

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a>ux_device_class_audio_write_thread_entry

Wpis wątku służący do zapisywania danych dla funkcji audio

### <a name="prototype"></a>Prototype

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Opis

Ta funkcja jest przenoszona do parametru inicjowania strumienia audio, jeśli jest wymagane zapisanie dźwięku na hoście. Wewnętrznie wątek jest tworzony za pomocą tej funkcji jako funkcji Wejścia; sam wątek zapisuje dane audio za pomocą Isochronous w punkcie końcowym w funkcji audio.

### <a name="parameters"></a>Parametry

- **audio_stream**: wskaźnik do wystąpienia strumienia audio.

### <a name="example"></a>Przykład

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a>ux_device_class_audio_stream_get

Pobierz określone wystąpienie strumienia dla funkcji audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a>Opis

Ta funkcja służy do uzyskiwania wystąpienia strumienia klasy audio.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia audio
- **stream_index**: indeks wystąpienia strumienia na podstawie 0
- **Stream**: wskaźnik do buforu do przechowywania wskaźnika wystąpienia strumienia audio

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a>ux_device_class_audio_reception_start

Rozpocznij odbieranie danych audio dla strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Opis

Ta funkcja służy do uruchamiania odczytywania danych audio w strumieniach audio.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) jest pełny.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a>ux_device_class_audio_sample_read8

Odczytaj 8-bitowy przykład ze strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a>Opis

Ta funkcja odczytuje 8-bitowe dane audio próbki z określonego strumienia.

W każdym przypadku odczytuje przykładowe dane z bieżącego buforu klatek audio w tabeli FIFO. Po odczytaniu ostatniego przykładu w ramce audio ramka zostanie automatycznie zwolniona, aby mogła zostać użyta w celu zaakceptowania większej ilości danych z hosta.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.
- **bufor**: wskaźnik do buforu w celu zapisania przykładowego bajtu.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a>ux_device_class_audio_sample_read16

Odczytaj 16-bitowy przykład ze strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a>Opis

Ta funkcja odczytuje 16-bitowe dane audio z określonego strumienia.

W każdym przypadku odczytuje przykładowe dane z bieżącego buforu klatek audio w tabeli FIFO. Po odczytaniu ostatniego przykładu w ramce audio ramka zostanie automatycznie zwolniona, aby mogła zostać użyta w celu zaakceptowania większej ilości danych z hosta.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.
- **bufor**: wskaźnik do buforu, aby zapisać próbkę 16-bitową.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a>ux_device_class_audio_sample_read24

Przeczytaj przykład 24-bitowy ze strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Opis

Ta funkcja odczytuje dane 24-bitowe audio z określonego strumienia.

W każdym przypadku odczytuje przykładowe dane z bieżącego buforu klatek audio w tabeli FIFO. Po odczytaniu ostatniego przykładu w ramce audio ramka zostanie automatycznie zwolniona, aby mogła zostać użyta w celu zaakceptowania większej ilości danych z hosta.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.
- **bufor**: wskaźnik do buforu w celu zapisania przykładu 3-bajtowego.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a>ux_device_class_audio_sample_read32

Odczytaj 32-bitowy przykład ze strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Opis

Ta funkcja odczytuje 32-bitowe dane audio z określonego strumienia.

W każdym przypadku odczytuje przykładowe dane z bieżącego buforu klatek audio w tabeli FIFO. Po odczytaniu ostatniego przykładu w ramce audio ramka zostanie automatycznie zwolniona, aby mogła zostać użyta w celu zaakceptowania większej ilości danych z hosta.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.
- **bufor**: wskaźnik do buforu, aby zapisać dane 4-bajtowe.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.
- Błąd **UX_ERROR** (0xFF) z funkcji

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

Ta funkcja zwraca pierwszy bufor ramki audio i jego długość z kolejki FIFO określonego strumienia. Gdy aplikacja zakończy przetwarzanie danych, ux_device_class_audio_read_frame_free musi być używana do zwolnienia bufora ramek w FIFO.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.
- **frame_data**: wskaźnik do wskaźnika danych, na który ma zostać zwrócony wskaźnik danych.
- **frame_length**: wskaźnik do buforu, aby zapisać długość ramki w liczbie bajtów.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a>ux_device_class_audio_read_frame_free

Zwolnij bufor ramki dźwiękowej w strumieniu audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Opis

Ta funkcja zwalnia bufor ramki dźwiękowej na przedniej stronie FIFO określonego strumienia, aby mógł odbierać dane z hosta.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a>ux_device_class_audio_transmission_start

Rozpocznij transmisję danych audio dla strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Opis

Ta funkcja służy do rozpoczynania wysyłania danych audio zapisanych do FIFO w klasie audio.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a>ux_device_class_audio_frame_write

Napisz ramkę audio do strumienia audio

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a>Opis

Ta funkcja zapisuje ramkę do kolejki FIFO strumienia audio. Dane ramki są kopiowane do dostępnego buforu w tabeli FIFO, aby można było je wysyłać do hosta.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.
- **ramka**: wskaźnik do danych ramek.
- **frame_length** Długość ramki w liczbie bajtów.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) jest pełny.
- Błąd **UX_ERROR** (0xFF) z funkcji

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

Ta funkcja pobiera adres ostatniego buforu ramki audio FIFO; Pobiera również długość buforu ramki audio. Gdy aplikacja wypełni bufor ramki audio odpowiednimi danymi, ***ux_device_class_audio_write_frame_commit*** musi być używana do dodawania/zatwierdzania bufora RAMEK do FIFO.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.
- **frame_data**: wskaźnik do wskaźnika danych ramek, który ma zwracać wskaźnik danych ramki w.
- **frame_length** Wskaźnik do buforu, aby zapisać długość ramki w liczbie bajtów.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) jest pełny.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a>ux_device_class_audio_write_frame_commit

Zatwierdź bufor ramki audio w strumieniu audio.

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a>Opis

Ta funkcja dodaje/zatwierdza ostatni bufor ramki audio do FIFO, aby bufor był gotowy do przekazania do hosta; Należy zauważyć, że ostatni bufor ramki audio powinien zostać wypełniony za pośrednictwem ux_device_class_write_frame_get.

### <a name="parameters"></a>Parametry

- **Stream**: wskaźnik do wystąpienia strumienia audio.
- **Długość**: liczba bajtów gotowych w buforze.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.
- Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) to fssull.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a>ux_device_class_audio10_control_process

Przetwarzanie żądań kontroli audio USB 1,0

### <a name="prototype"></a>Prototype

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a>Opis

Ta funkcja zarządza żądaniami podstawowymi wysyłanymi przez hosta w punkcie końcowym kontroli przy użyciu określonego typu USB audio 1,0.

Funkcje audio 1,0 dla woluminów i wyciszania żądań są przetwarzane w funkcji. Podczas przetwarzania żądań, wstępnie zdefiniowane dane przesyłane przez ostatni parametr (Grupa) są używane do odpowiedzi na żądania i zmiany kontroli magazynu.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia audio.
- **transfer**: wskaźnik do wystąpienia żądania transferu.
- **Grupa**: Grupa danych dla procesu żądania.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- Błąd **UX_ERROR** (0xFF) z funkcji

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

Przetwarzanie żądań kontroli audio USB 1,0

### <a name="prototype"></a>Prototype
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a>Opis

Ta funkcja zarządza żądaniami podstawowymi wysyłanymi przez hosta w punkcie końcowym kontroli przy użyciu określonego typu USB audio 2,0.

Częstotliwość próbkowania audio 2,0 (przyjęto pojedynczą stałą częstotliwość), funkcje woluminu i wyciszania są przetwarzane w funkcji. Podczas przetwarzania żądań, wstępnie zdefiniowane dane przesyłane przez ostatni parametr (Grupa) są używane do odpowiedzi na żądania i zmiany kontroli magazynu.

### <a name="parameters"></a>Parametry

- **audio**: wskaźnik do wystąpienia audio.
- **transfer**: wskaźnik do wystąpienia żądania transferu.
- **Grupa**: Grupa danych dla procesu żądania.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- Błąd **UX_ERROR** (0xFF) z funkcji

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
