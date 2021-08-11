---
title: Rozdział 3 — Składniki funkcjonalne stosu urządzeń USBX
description: Ten rozdział zawiera opis wysokowydajnych stosów osadzonych urządzeń USB USBX z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 104badcbf1ec682cd8b09008578ba91768834d694473ecccf59e35637dfd9f3c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791361"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a>Rozdział 3 — Składniki funkcjonalne stosu urządzeń USBX

Ten rozdział zawiera opis wysokowydajnych stosów osadzonych urządzeń USB USBX z perspektywy funkcjonalnej.

## <a name="execution-overview"></a>Omówienie wykonywania

Dysk USBX urządzenia składa się z kilku składników.

- Inicjalizacja
- Wywołania interfejsu aplikacji
- Klasy urządzeń
- Stos urządzenia USB
- Kontroler urządzeń
- Menedżer VBUS

Na poniższym diagramie przedstawiono stos urządzenia USBX.

![Stos urządzenia USBX](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a>Inicjalizacja

Aby można było aktywować usbx, ***należy ux_system_initialize*** funkcję. Ta funkcja inicjuje zasoby pamięci USBX.

Aby aktywować urządzenia USBX, należy ***ux_device_stack_initialize*** funkcję. Ta funkcja z kolei inicjuje wszystkie zasoby używane przez stos urządzenia USBX, takie jak wątki ThreadX, mutexes i semafory.

Do inicjowania aplikacji należy aktywowanie kontrolera urządzenia USB i co najmniej jednej klasy USB. W przeciwieństwie do strony hosta USB po stronie urządzenia może być uruchomiony tylko jeden sterownik kontrolera USB w dowolnym momencie. Po zarejestrowaniu klas w stosie i wywołaniu funkcji inicjowania kontrolerów urządzeń magistrala jest aktywna, a stos odpowiada na polecenia resetowania magistrali i wyliczania hostów.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Istnieją dwa poziomy interfejsów API w USBX.

- Interfejsy API stosu urządzeń USB
- Interfejsy API klasy urządzeń USB

Zwykle aplikacja USBX nie powinna wymagać wywołania żadnego z interfejsów API stosu urządzenia USB. Większość aplikacji będzie mieć dostęp tylko do interfejsów API klasy USB.

### <a name="usb-device-stack-apis"></a>Interfejsy API stosu urządzeń USB

Interfejsy API stosu urządzeń są odpowiedzialne za rejestrację składników urządzenia USBX, takich jak klasy i struktury urządzeń.

### <a name="usb-device-class-apis"></a>Interfejsy API klasy urządzeń USB

Interfejsy API klas są bardzo specyficzne dla każdej klasy USB. Większość typowych interfejsów API dla klas USB zapewniała usługi, takie jak otwieranie/zamykanie urządzenia oraz odczytywanie z i zapisywanie na urządzeniu. Interfejsy API są z natury podobne do interfejsów po stronie hosta.

## <a name="device-framework"></a>Device Framework

Po stronie urządzenia USB jest odpowiedzialna za definicję struktury urządzenia. Platformę urządzeń podzielono na trzy kategorie, zgodnie z opisem w poniższych sekcjach.

### <a name="definition-of-the-components-of-the-device-framework"></a>Definicja składników struktury urządzeń

Definicja każdego składnika struktury urządzeń jest powiązana z charakterem urządzenia i zasobami wykorzystywanymi przez urządzenie. Poniżej przedstawiono główne kategorie.

- Deskryptor urządzenia
- Deskryptor konfiguracji
- Deskryptor interfejsu
- Deskryptor punktu końcowego

UsbX obsługuje definicję składnika urządzenia zarówno dla dużej, jak i pełnej szybkości (niska szybkość jest traktowana tak samo jak pełna szybkość). Dzięki temu urządzenie może działać inaczej po podłączeniu do hosta o dużej szybkości lub pełnej szybkości. Typowe różnice to rozmiar każdego punktu końcowego i ilość energii zużywanej przez urządzenie.

Definicja składnika urządzenia ma postać ciągu bajtowego, który jest zgodny ze specyfikacją USB. Definicja jest ciągła, a kolejność, w której framework jest reprezentowana w pamięci, będzie taka sama jak ta, która zostanie zwrócona do hosta podczas wyliczania.

Poniżej przedstawiono przykład struktury urządzeń dla szybkiego dysku flash USB.

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a>Definicja ciągów struktury urządzeń

Ciągi są opcjonalne w urządzeniu. Ich celem jest podaniem hostowi USB informacji o producencie urządzenia, nazwie produktu i numerze poprawki za pośrednictwem ciągów Unicode.

Główne ciągi to indeksy osadzone w deskryptorach urządzeń. Dodatkowe indeksy ciągów można osadzić w poszczególnych interfejsach.

Zakładając, że powyższe struktury urządzeń mają trzy indeksy ciągów osadzone w deskryptorze urządzenia, definicja struktury ciągów może wyglądać jak ten przykładowy kod.

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38
UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

Jeśli dla każdej szybkości muszą być używane różne ciągi, należy użyć różnych indeksów, ponieważ indeksy są niezależne od szybkości.

Kodowanie ciągu jest oparte na standardzie UNICODE. Aby uzyskać więcej informacji na temat standardu kodowania UNICODE, zapoznaj się z następującą publikacją:

*Standard Unicode, kodowanie znaków na całym świecie, wersja 1., woluminy 1 i 2, Konsorcjum Unicode, Addison-Wesley Publishing Company, Reading MA.*

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a>Definicja języków obsługiwanych przez urządzenie dla każdego ciągu

UsbX ma możliwość obsługi wielu języków, chociaż język angielski jest domyślny. Definicja każdego języka dla deskryptorów ciągów ma postać tablicy definicji języków zdefiniowanej w następujący sposób.

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

Aby obsługiwać dodatkowe języki, po prostu dodaj dwu bajtową definicję kodu języka po domyślnym kodzie w języku angielskim. Kod języka został zdefiniowany w dokumencie przez firmę Microsoft.

*Developing International Software for Windows 95 and Windows NT, Na niech kano, Microsoft Press, Redmond WA*

## <a name="vbus-manager"></a>Menedżer VBUS

W większości projektów urządzeń USB magistrala VBUS nie jest częścią rdzenia urządzenia USB, ale jest połączona z zewnętrznym interfejsem GPIO, który monitoruje sygnał liniowy.

W związku z tym magistralą VBUS należy zarządzać niezależnie od sterownika kontrolera urządzenia.

Aplikacja musi podać kontrolerowi urządzenia adres we/wy VBUS. Przed zainicjowaniem kontrolera urządzenia należy zainicjować magistralę VBUS.

W zależności od specyfikacji platformy do monitorowania VBUS sterownik kontrolera może obsługiwać sygnały VBUS po zainicjowaniu VBUS IO lub jeśli nie jest to możliwe, aplikacja musi podać kod do obsługi VBUS.

Jeśli aplikacja chce obsługiwać magistralę VBUS samodzielnie, jedynym wymaganiem jest wywołanie funkcji ***ux_device_stack_disconnect,*** gdy wykryje, że urządzenie zostało wyodrębnione. Nie jest konieczne informowanie kontrolera o wstawieniu urządzenia, ponieważ kontroler wznowi jego działania po wykryciu sygnału asertywnego/deassert zresetowania magistrali.
