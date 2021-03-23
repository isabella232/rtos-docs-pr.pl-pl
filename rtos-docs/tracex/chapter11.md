---
title: Rozdział 11 — format buforu śledzenia zdarzeń
description: ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich usług Azure RTO ThreadX Services, zmian stanu wątku i zdarzeń zdefiniowanych przez użytkownika.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: d11b827558e9c96df44f462329b7807a500a64a4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823479"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a>Rozdział 11 — format buforu śledzenia zdarzeń

Usługa Azure RTO ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich usług ThreadX Services, zmian stanu wątku i zdarzeń zdefiniowanych przez użytkownika. Aby użyć śledzenia zdarzeń, należy po prostu skompilować biblioteki ThreadX, NetX i FileX za pomocą **TX_ENABLE_EVENT_TRACE** zdefiniowanych i Włącz śledzenie, wywołując funkcję **_tx_trace_enable_** . Ten rozdział zawiera opis tego procesu.

## <a name="event-trace-format"></a>Format śledzenia zdarzeń

Format buforu śledzenia zdarzeń ThreadX jest podzielony na trzy sekcje, mianowicie nagłówek formantu, rejestr obiektów i wpisy śledzenia. Poniżej opisano ogólny układ buforu śledzenia zdarzeń ThreadX:

**Nagłówek formantu**

**Wpis rejestru obiektu 0**

**…**

**Wpis rejestru obiektu "n"**

**Wpis śledzenia zdarzeń 0**

**…**

**Wpis śledzenia zdarzeń "n"**

### <a name="event-trace-control-header"></a>Nagłówek formantu śledzenia zdarzeń

Nagłówek formantu definiuje dokładny układ buforu śledzenia zdarzeń. Obejmuje to liczbę obiektów ThreadX, a także liczbę zdarzeń, które mogą być rejestrowane. Ponadto nagłówek kontrolki definiuje, gdzie znajdują się poszczególne elementy buforu śledzenia. Następująca struktura danych definiuje nagłówek formantu:

```c
typedef struct TX_TRACE_CONTROL_HEADER_STRUCT
{
    ULONG    tx_trace_control_header_id;
    ULONG    tx_trace_control_header_timer_valid_mask;
    ULONG    tx_trace_control_header_trace_base_address;
    ULONG    tx_trace_control_header_object_registry_start_pointer;
    USHORT   tx_trace_control_header_reserved1;
    USHORT   tx_trace_control_header_object_registry_name_size;
    ULONG    tx_trace_control_header_object_registry_end_pointer;
    ULONG    tx_trace_control_header_buffer_start_pointer;
    ULONG    tx_trace_control_header_buffer_end_pointer;
    ULONG    tx_trace_control_header_buffer_current_pointer;
    ULONG    tx_trace_control_header_reserved2;
    ULONG    tx_trace_control_header_reserved3;
    ULONG    tx_trace_control_header_reserved4;
} TX_TRACE_CONTROL_HEADER;
```

### <a name="control-header-id"></a>Identyfikator nagłówka kontrolki

Identyfikator nagłówka kontrolki składa się z 32-bitowej wartości SZESNASTKOWej 0x54585442, która odnosi się do znaków ASCII ***TXTB***. Ponieważ ta wartość jest zapisywana jako 32-bitowa zmienna bez znaku, może być również używana do wykrywania endian w buforze śledzenia zdarzeń. Na przykład jeśli wartość w pierwszym cztery wartości bTak pamięci to 0x54, 0x58, 0x54, 0x42, bufor śledzenia zdarzeń został zapisany w formacie big endian. W przeciwnym razie bufor śledzenia zdarzeń został zapisany w formacie little endian.

### <a name="timer-valid-mask"></a>Prawidłowa maska czasomierza

Prawidłowa maska czasomierza określa, ile bitów sygnatury czasowej w rzeczywistych wpisach śledzenia zdarzeń są prawidłowe. Na przykład, jeśli źródło sygnatury czasowej ma 16 bitów, wartość w tym polu powinna być równa 0xFFFF. 32-bitowe Źródło sygnatury czasowej będzie miało wartość 0xFFFFFFFF. Ta wartość jest definiowana przez znak ***TX_TRACE_TIME_MASK** _ w _ *_tx_port. h_* *.

### <a name="trace-base-address"></a>Adres podstawowy śledzenia

Adres podstawowy bufora śledzenia to adres określony przez aplikację jako początek buforu śledzenia w wywołaniu ***tx_trace_enable*** . Ten adres jest obsługiwany wyłącznie w celu wygenerowania przesunięć bufferrelative dla różnych elementów w buforze przy użyciu narzędzia do analizy. Na przykład względne przesunięcie buforu bieżącego zdarzenia w buforze śledzenia jest obliczane przez proste odejmowanie adresu podstawowego od bieżącego adresu zdarzenia.

### <a name="registry-start-and-end-pointers"></a>Wskaźniki początku i końca rejestru

Wskaźnik rozpoczęcia rejestru wskazuje adres pierwszego wpisu rejestru obiektu, podczas gdy wskaźnik końcowy rejestru wskazuje na adres wiadomości błyskawicznych. /mediately po ostatnim wpisie rejestru. Te wartości są skonfigurowane podczas przetwarzania *tx_trace_enable* i nie są zmieniane w czasie trwania śledzenia.

### <a name="registry-name-size"></a>Rozmiar nazwy rejestru

Rozmiar nazwy rejestru definiuje maksymalny rozmiar w bajtach dla każdej nazwy obiektu w wpisie rejestru i jest zdefiniowany przez symbol ***TX_TRACE_OBJECT_REGISTRY_NAME** _. Wartość domyślna to 32 i jest definiowana w _*_tx_trace. h_*_. Nazwa obiektu odpowiada nazwie podanej przez aplikację podczas tworzenia obiektu. Na przykład nazwa rejestru obiektu dla wątku jest nazwą dostarczoną przez aplikację w wywołaniu _ *_tx_thread_create_* *.

### <a name="buffer-start-and-end-pointers"></a>Wskaźniki początku i końca buforu

Wskaźnik startowy buforu śledzenia zdarzeń wskazuje adres pierwszego wpisu śledzenia, podczas gdy wskaźnik końcowy rejestru wskazuje na adres wiadomości błyskawicznych. /mediately po ostatnim wpisie śledzenia. Te wartości są skonfigurowane podczas ***tx_trace_enable</*** przetwarzania i nie są zmieniane w czasie trwania śledzenia.

### <a name="current-buffer-pointer"></a>Bieżący wskaźnik buforu

Bieżący wskaźnik buforu śledzenia zdarzeń wskazuje na adres najstarszego wpisu śledzenia. Ponieważ wpisy śledzenia są przechowywane na liście cyklicznej, bieżący wskaźnik buforu również reprezentuje Następny wpis śledzenia do zapisania. |

## <a name="event-trace-object-registry"></a>Rejestr obiektów śledzenia zdarzeń

Rejestr obiektu śledzenia zdarzeń zawiera ***n** _ wpisów rejestru obiektów, które odpowiadają obiektom utworzonymi przez aplikację. Głównym celem rejestru obiektu jest dla zewnętrznych narzędzi do analizy skorelowanie rzeczywistych nazw obiektów z adresami obiektów wpisów buforu śledzenia. Liczba wpisów rejestru jest określana przez aplikację w wywołaniu _ *_tx_trace_enable_**.

Każdy wpis w rejestrze obiektów zawiera informacje o konkretnym obiekcie ThreadX, który został wcześniej utworzony przez aplikację. Następująca struktura danych definiuje każdy wpis rejestru obiektów:

```c
typedef struct TX_TRACE_OBJECT_REGISTRY_ENTRY_STRUCT
{
    UCHAR    tx_trace_object_registry_entry_object_available**;
    UCHAR    tx_trace_object_registry_entry_object_type**;
    UCHAR    tx_trace_object_registry_entry_object_reserved1;
    UCHAR    tx_trace_object_registry_entry_object_reserved2;
    ULONG    tx_trace_thread_registry_entry_object_pointer;
    ULONG    tx_trace_object_registry_entry_object_parameter_1;
    ULONG    tx_trace_object_registry_entry_object_parameter_2;
    UCHAR    tx_trace_thread_registry_entry_object_name[TX_TRACE_OBJECT_REGISTRY_NAME];

} TX_TRACE_OBJECT_REGISTRY_ENTRY;
```

### <a name="object-available-flag"></a>Flaga dostępnego obiektu

Flaga dostępnego obiektu jest ustawiona na 1, Jeśli wpis rejestru obiektów jest dostępny. W przeciwnym razie, jeśli wartość nie jest równa 1, wpis rejestru obiektu jest niedostępny. Należy zauważyć, że wpis może nadal zawierać prawidłowe informacje, nawet jeśli jest dostępny.

### <a name="object-entry-type"></a>Typ wpisu obiektu

Typ wpisu obiektu identyfikuje typ obiektu w tym wpisie. Poniżej znajduje się lista prawidłowych typów obiektów:

| **Wartość** | **Typ obiektu** |
|---------- | --------------- |
| 0         | Nieprawidłowy       |
| 1         | Thread          |
| 2         | Czasomierz |
| 3         | Kolejka |
| 4         | Semaphore |
| 5         | Mutex |
| 6         | Grupa flag zdarzeń |
| 7         | Blokuj pulę |
| 8         | Pula bajtów |
| 9         | .. /media |
| 10        | Plik |
| 11        | Adres IP |
| 12        | Pula pakietów |
| 13        | Gniazdo TCP |
| 14        | Gniazdo UDP |
| 15-20     | Zarezerwowany |  
| 21        | Urządzenie stosu hosta USB |
| 22        | Interfejs stosu hosta USB |
| 23        | Punkt końcowy hosta USB |
| 24        | Klasa hosta USB |
| 25        | Urządzenie USB |
| 26        | Interfejs urządzenia USB |
| 27        | Punkt końcowy urządzenia USB |
| 28        | Klasa urządzenia USB |

### <a name="object-pointer"></a>Wskaźnik obiektu

Wskaźnik obiektu określa adres obiektu, który jest używany do uzyskiwania dostępu do obiektu za pomocą interfejsu API ThreadX.

### <a name="object-reserved-fields"></a>Pola zarezerwowane dla obiektu

Dla wszystkich obiektów innych niż wątki pola zarezerwowane powinny mieć wartość 0. W przypadku wątków priorytet wątku w czasie wprowadzania do rejestru jest umieszczany w tych dwóch zastrzeżonych polach.

### <a name="object-parameters"></a>Parametry obiektu

Parametry obiektu zawierają dodatkowe informacje na temat obiektu. Poniżej opisano dodatkowe informacje dla każdego obiektu ThreadX:

| **Typ obiektu**        | **Parametr 1**  | **Parametr 2** |
|----------------------- | ---------------- | --------------- |
| Thread                 | Rozpoczęcie stosu      | Rozmiar stosu |
| Czasomierz                  | Początkowe Takty | Zaplanuj ponownie Takty |
| Kolejka                  | Rozmiar kolejki | Rozmiar komunikatu |
| Semaphore              | Początkowe wystąpienia | - |
| Mutex                  | Flaga dziedziczenia | - |
| Grupa flag zdarzeń      | - | - |
| Blokuj pulę             | Łączna liczba bloków | Rozmiar bloku |
| Pula bajtów              | Łączna liczba bajtów | - |
| .. /media                  | Rozmiar pamięci podręcznej FAT | Rozmiar pamięci podręcznej sektora |
| Plik                   | - | - |
| Adres IP                     | Rozpoczęcie stosu | Rozmiar stosu |
| Pula pakietów            | Rozmiar pakietu | Liczba pakietów |
| Gniazdo TCP             | Adres IP | Rozmiar okna |
| Gniazdo UDP             | Adres IP | Maksymalna liczba kolejek RX |

### <a name="object-name"></a>Nazwa obiektu

Nazwa obiektu zawiera nazwę obiektu ThreadX. Nazwa jest nazwą dostarczoną do ThreadX w momencie utworzenia obiektu. Domyślnie nazwa obiektu ma maksymalnie 32 znaków. Rzeczywiste nazwy większe niż 32 znaków są obcinane.

## <a name="event-trace-entries"></a>Wpisy śledzenia zdarzeń

Wpisy śledzenia zdarzeń znajdują się w dolnej części buforu śledzenia zdarzeń. Wpisy są przechowywane na liście cyklicznej, przy czym wskaźnik bieżącego wpisu wskazuje na najstarszą pozycję. Liczba wpisów na liście jest obliczana przez wywołanie ***tx_trace_enable*** .

Każdy wpis w rejestrze obiektów zawiera informacje o określonym zdarzeniu śledzenia ThreadX. Następująca struktura danych definiuje każdy wpis zdarzenia śledzenia:

```c
typedef struct TX_TRACE_BUFFER_ENTRY_STRUCT
{
    ULONG     tx_trace_buffer_entry_thread_pointer;
    ULONG     tx_trace_buffer_entry_thread_priority;
    ULONG     tx_trace_buffer_entry_event_id;
    ULONG     tx_trace_buffer_entry_time_stamp;
    ULONG     tx_trace_buffer_entry_information_field_1;
    ULONG     tx_trace_buffer_entry_information_field_2;
    ULONG     tx_trace_buffer_entry_information_field_3;
    ULONG     tx_trace_buffer_entry_information_field_4;
} TX_TRACE_BUFFER_ENTRY;
```

### <a name="thread-pointer"></a>Wskaźnik wątku

Wskaźnik wątku zawiera adres wątku uruchomionego w czasie tego zdarzenia. Jeśli zdarzenie wystąpiło podczas inicjowania (brak działającego wątku), wartość tego wskaźnika to 0xF0F0F0F0. Jeśli zdarzenie wystąpiło w trakcie procedury usługi przerwania (ISR), wartość tego wskaźnika to 0xFFFFFFFF. Jeśli wpis nie został jeszcze użyty, wartość tego wskaźnika wynosi 0.

### <a name="thread-priority"></a>Priorytet wątku

Pole priorytet wątku zawiera priorytet wątku i zastępujący — próg wątku, który był uruchomiony w czasie tego zdarzenia. Jeśli jest obecny kontekst przerwania (wskaźnik wątku to 0xFFFFFFFF), wartość tego pola nie jest priorytetem, ale zamiast wartości ***_tx_thread_current_ptr*** w czasie zdarzenia. W przeciwnym razie wartość tego pola wynosi 0.

### <a name="event-id"></a>Identyfikator zdarzenia

Identyfikator zdarzenia określa zdarzenie, które miało miejsce. Prawidłowe identyfikatory zdarzeń śledzenia ThreadX mieszczą się w zakresie od 1 do 1024. Wartości zaczynające się od 1025 i powyżej są zarezerwowane dla zdarzeń specyficznych dla użytkownika. Zapoznaj się z plikiem ***tx_trace. h*** , aby uzyskać pełną definicję identyfikatorów zdarzeń ThreadX.</td>

### <a name="information-fields-1-4"></a>Pola informacji (1-4)

Pola informacji zawierają dodatkowe informacje o konkretnym zdarzeniu. Zapoznaj się z plikiem ***tx_trace. h*** , aby uzyskać pełny opis pól informacji dla każdego ze zdefiniowanych identyfikatorów zdarzeń ThreadX.