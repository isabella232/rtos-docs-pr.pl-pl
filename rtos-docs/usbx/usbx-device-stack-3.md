---
title: Rozdział 3-funkcjonalne składniki stosu urządzeń USBX
description: Ten rozdział zawiera opis stosu urządzenia USB o wysokiej wydajności USBX Embedded z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dc57f3e0f6aa6731f4aaedee8169313ca7276cff
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082204"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a>Rozdział 3-funkcjonalne składniki stosu urządzeń USBX

Ten rozdział zawiera opis stosu urządzenia USB o wysokiej wydajności USBX Embedded z perspektywy funkcjonalnej.

## <a name="execution-overview"></a>Przegląd wykonywania

USBX dla urządzenia składa się z kilku składników.

- Inicjalizacja
- Wywołania interfejsu aplikacji
- Klasy urządzeń
- Stos urządzeń USB
- Kontroler urządzenia
- VBUS Manager

Na poniższym diagramie przedstawiono stos urządzeń USBX.

![Stos urządzeń USBX](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a>Inicjalizacja

W celu aktywowania USBX należy wywołać funkcję ***ux_system_initialize*** . Ta funkcja inicjuje zasoby pamięci z USBX.

Aby można było aktywować urządzenia USBX, należy wywołać funkcję ***ux_device_stack_initialize*** . Ta funkcja spowoduje zainicjowanie wszystkich zasobów używanych przez stos urządzeń USBX, takich jak wątki ThreadX, muteksy i semafory.

Do inicjalizacji aplikacji można aktywować kontroler urządzeń USB i co najmniej jedną klasę USB. W przeciwieństwie do strony hosta USB po stronie urządzenia może być uruchomiony tylko jeden sterownik kontrolera USB w dowolnym momencie. Gdy klasy zostały zarejestrowane na stosie, a funkcja inicjowania kontrolerów urządzeń została wywołana, magistrala jest aktywna, a stos odpowiada na polecenia resetowania magistrali i hosta.

### <a name="application-interface-calls"></a>Wywołania interfejsu aplikacji

Istnieją dwa poziomy interfejsów API w USBX.

- Interfejsy API stosu urządzeń USB
- Interfejsy API klas urządzeń USB

Zwykle aplikacja USBX nie powinna wywołać żadnego z interfejsów API stosu urządzeń USB. Większość aplikacji będzie uzyskiwać dostęp tylko do interfejsów API klasy USB.

### <a name="usb-device-stack-apis"></a>Interfejsy API stosu urządzeń USB

Interfejsy API stosu urządzeń są odpowiedzialne za rejestrację składników urządzeń USBX, takich jak klasy i platforma urządzeń.

### <a name="usb-device-class-apis"></a>Interfejsy API klas urządzeń USB

Interfejsy API klas są bardzo specyficzne dla każdej klasy USB. Większość typowych interfejsów API dla klas USB zapewnia usługi, takie jak otwieranie/zamykanie urządzenia oraz odczytywanie i zapisywanie na urządzeniu. Interfejsy API są podobne do strony hosta.

## <a name="device-framework"></a>Platforma urządzeń

Urządzenie USB jest odpowiedzialne za definicję platformy urządzeń. Platforma urządzeń jest podzielona na trzy kategorie, zgodnie z opisem w poniższych sekcjach.

### <a name="definition-of-the-components-of-the-device-framework"></a>Definicja składników platformy urządzenia

Definicja każdego składnika platformy urządzenia jest związana z charakterem urządzenia i zasobami wykorzystywanymi przez urządzenie. Poniżej przedstawiono główne kategorie.

- Deskryptor urządzenia
- Deskryptor konfiguracji
- Deskryptor interfejsu
- Deskryptor punktu końcowego

USBX obsługuje definicję składnika urządzenia zarówno dla wysokiej, jak i pełnej prędkości (niska szybkość jest traktowana tak samo jak Pełna szybkość). Dzięki temu urządzenie może działać inaczej po połączeniu z hostem o dużej szybkości lub w trybie szybkim. Typowymi różnicami są rozmiary poszczególnych punktów końcowych i moc zużywaną przez urządzenie.

Definicja składnika urządzenia przyjmuje postać ciągu bajtowego, który jest zgodny ze specyfikacją USB. Definicja jest ciągła i kolejność, w jakiej struktura jest reprezentowana w pamięci, będzie taka sama jak wartość zwracana do hosta podczas wyliczania.

Poniżej przedstawiono przykładową platformę urządzenia dla dysku flash USB o dużej szybkości.

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

### <a name="definition-of-the-strings-of-the-device-framework"></a>Definicja ciągów struktury urządzenia

Ciągi są opcjonalne w urządzeniu. Celem jest umożliwienie hostowi USB znajomości producenta urządzenia, nazwy produktu i numeru poprawki za pośrednictwem ciągów Unicode.

Główne ciągi są indeksami osadzonymi w deskryptorach urządzeń. Dodatkowe indeksy ciągów można osadzić w poszczególnych interfejsach.

Zakładając, że powyższa platforma urządzenia ma trzy indeksy ciągu osadzone w deskryptorze urządzenia, Definicja struktury ciągu może wyglądać podobnie jak w przypadku tego przykładowego kodu.

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

Jeśli różne ciągi muszą być używane dla każdej szybkości, należy użyć różnych indeksów, ponieważ indeksy są szybkością niezależny od.

Kodowanie ciągu jest oparte na formacie UNICODE. Aby uzyskać więcej informacji na temat standardu kodowania UNICODE, zapoznaj się z następującą publikacją:

*Standard Unicode, na całym świecie kodowanie znaków, wersja 1,, woluminy 1 i 2, konsorcjum Unicode, Addison-Wesley firmy Publishing, odczyt MA.*

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a>Definicja języków obsługiwanych przez urządzenie dla każdego ciągu

Usługa USBX ma możliwość obsługi wielu języków, chociaż jest to ustawienie domyślne w języku angielskim. Definicja każdego języka dla deskryptorów ciągów ma postać tablicy definicji języka zdefiniowanej w następujący sposób.

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

Aby zapewnić obsługę dodatkowych języków, po prostu Dodaj kod języka podwójnego bajtu po domyślnym kodzie w języku angielskim. Kod języka został zdefiniowany przez firmę Microsoft w dokumencie.

*Opracowywanie międzynarodowego oprogramowania dla systemów Windows 95 i Windows NT, Nadine Kano, Microsoft Press, Redmond WA*

## <a name="vbus-manager"></a>VBUS Manager

W większości projektów urządzeń USB VBUS nie jest częścią podstawowego urządzenia USB, ale nie jest podłączony do zewnętrznego interfejsu GPIO, który monitoruje sygnał liniowy.

W związku z tym VBUS musi być zarządzany niezależnie od sterownika kontrolera urządzenia.

Jest ona do aplikacji, aby zapewnić kontrolerowi urządzenia adres VBUS we/wy. VBUS musi zostać zainicjowany przed inicjalizacją kontrolera urządzenia.

W zależności od specyfikacji platformy dla monitorowania VBUS można pozwolić, aby sterownik kontrolera obsługiwał sygnały VBUS po zainicjowaniu operacji we/wy VBUS lub jeśli nie jest to możliwe, aplikacja musi dostarczyć kod do obsługi VBUS.

Jeśli aplikacja chce obsłużyć VBUS samodzielnie, Jedynym wymaganiem jest wywołanie funkcji ***ux_device_stack_disconnect*** , gdy wykryje, że urządzenie zostało wyodrębnione. Nie jest konieczne informowanie kontrolera, gdy urządzenie zostanie wstawione, ponieważ kontroler zostanie wznowiony, gdy zostanie wykryty sygnał potwierdzenia/potwierdzeń MAGISTRALi.
