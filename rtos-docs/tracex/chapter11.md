---
title: Rozdział 11 — Format buforu śledzenia zdarzeń
description: ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich Azure RTOS ThreadX, zmian stanu wątku i zdarzeń zdefiniowanych przez użytkownika.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: b230a6207cec3a0968d88b197455896881e5ef7a0d8b93d4b1fb5a37696a7b6c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802145"
---
# <a name="chapter-11---format-of-event-trace-buffer"></a>Rozdział 11 — Format buforu śledzenia zdarzeń

Azure RTOS ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich usług ThreadX, zmian stanu wątku i zdarzeń zdefiniowanych przez użytkownika. Aby użyć śledzenia zdarzeń, po prostu skompilować biblioteki  ThreadX, NetX i FileX ze zdefiniowanymi TX_ENABLE_EVENT_TRACE i włączyć śledzenie, wywołując **_funkcję tx_trace_enable._** W tym rozdziale opisano ten proces.

## <a name="event-trace-format"></a>Format śledzenia zdarzeń

Format buforu śledzenia zdarzeń ThreadX jest podzielony na trzy sekcje: nagłówek kontrolki, rejestr obiektów i wpisy śledzenia. Poniżej opisano ogólny układ buforu śledzenia zdarzeń ThreadX:

**Nagłówek kontrolki**

**Wpis rejestru obiektów 0**

**…**

**Wpis rejestru obiektów "n"**

**Wpis śledzenia zdarzeń 0**

**…**

**Wpis śledzenia zdarzeń "n"**

### <a name="event-trace-control-header"></a>Nagłówek kontrolki śledzenia zdarzeń

Nagłówek kontrolki definiuje dokładny układ buforu śledzenia zdarzeń. Obejmuje to, ile obiektów ThreadX można zarejestrować, a także ile zdarzeń może być rejestrowanych. Ponadto nagłówek kontrolki definiuje, gdzie znajduje się każdy z elementów buforu śledzenia. Następująca struktura danych definiuje nagłówek kontrolki:

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

Identyfikator nagłówka kontrolki składa się z 32-bitowej wartości SZESNASTKOWEJ 0x54585442, która odpowiada znakom ***ASCII TXTB.*** Ponieważ ta wartość jest zapisywana jako 32-bitowa zmienna niepodpisana, może być również używana do wykrywania endianness buforu śledzenia zdarzeń. Jeśli na przykład wartość w pierwszych czterech byes pamięci to 0x54, 0x58, 0x54, 0x42, bufor śledzenia zdarzeń został zapisany w big endian formacie. W przeciwnym razie bufor śledzenia zdarzeń został zapisany w little endian formacie.

### <a name="timer-valid-mask"></a>Prawidłowa maska czasomierza

Prawidłowa maska czasomierza definiuje, ile bitów znacznika czasu w rzeczywistych wpisach śledzenia zdarzeń jest prawidłowych. Jeśli na przykład źródło sygnatury czasowej ma 16-bitowe, wartość w tym polu powinna być 0xFFFF. 32-bitowe źródło sygnatury czasowej będzie miało wartość 0xFFFFFFFF. Ta wartość jest definiowana przez **stałą*** TX_TRACE_TIME_MASK _ w _*_tx_port.h_**.

### <a name="trace-base-address"></a>Podstawowy adres śledzenia

Adres podstawowy buforu śledzenia to adres określony przez aplikację jako początek buforu śledzenia w ***wywołaniu tx_trace_enable*** śledzenia. Ten adres jest utrzymywany wyłącznie za pomocą narzędzia do analizy w celu uzyskania przesunięcia buforowego dla różnych elementów w buforze. Na przykład względne przesunięcie buforu bieżącego zdarzenia w buforze śledzenia jest obliczane przez proste odejmowanie adresu podstawowego od bieżącego adresu zdarzenia.

### <a name="registry-start-and-end-pointers"></a>Wskaźniki początku i końca rejestru

Wskaźnik uruchamiania rejestru wskazuje adres pierwszego wpisu rejestru obiektów, a wskaźnik końcowy rejestru wskazuje na adres im.. /mediately po ostatnim wpisie rejestru. Te wartości są konfigurowe *podczas tx_trace_enable* i nie są zmieniane w czasie trwania śledzenia.

### <a name="registry-name-size"></a>Rozmiar nazwy rejestru

Rozmiar nazwy rejestru definiuje maksymalny rozmiar w bajtach dla każdej nazwy obiektu we wpisie rejestru i jest definiowany przez symbol ***** TX_TRACE_OBJECT_REGISTRY_NAME _. Wartość domyślna to 32 i jest zdefiniowana w _*_tx_trace.h._*_ Nazwa obiektu odpowiada nazwie nadanych przez aplikację podczas tworzenia obiektu. Na przykład nazwa rejestru obiektów dla wątku jest nazwą podaną przez aplikację do wywołania __*_ tx_thread_create **.

### <a name="buffer-start-and-end-pointers"></a>Wskaźniki rozpoczęcia i zakończenia buforu

Wskaźnik startowy buforu śledzenia zdarzeń wskazuje adres pierwszego wpisu śledzenia, a wskaźnik końcowy rejestru wskazuje na adres im.. /mediately po ostatnim wpisie śledzenia. Te wartości są konfigurowe ***podczas tx_trace_enable</przetwarzania*** i nie są zmieniane w czasie trwania śledzenia.

### <a name="current-buffer-pointer"></a>Wskaźnik bieżącego buforu

Bieżący wskaźnik bufora śledzenia zdarzeń wskazuje adres najstarszego wpisu śledzenia. Ponieważ wpisy śledzenia są utrzymywane na liście cyklicznej, bieżący wskaźnik buforu jest również reprezentuje następny wpis śledzenia, który ma zostać zapisany. |

## <a name="event-trace-object-registry"></a>Rejestr obiektów śledzenia zdarzeń

Rejestr obiektów śledzenia zdarzeń zawiera wpisy rejestru obiektów ***n** _, które odpowiadają obiektom utworzonym przez aplikację. Głównym celem rejestru obiektów jest skorelowanie rzeczywistych nazw obiektów z adresami obiektów wpisów buforu śledzenia za pomocą narzędzi do analizy zewnętrznej. Liczba wpisów rejestru jest określana przez aplikację w wywołaniu _ *_tx_trace_enable_**.

Każdy wpis rejestru obiektów zawiera informacje o określonym obiekcie ThreadX utworzonym wcześniej przez aplikację. Następująca struktura danych definiuje każdy wpis rejestru obiektów:

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

### <a name="object-available-flag"></a>Flaga dostępnych obiektów

Flaga dostępnych obiektów jest ustawiona na 1, jeśli wpis rejestru obiektów jest dostępny. W przeciwnym razie, jeśli wartość nie jest 1, wpis rejestru obiektów nie jest dostępny. Należy pamiętać, że wpis może nadal zawierać prawidłowe informacje, nawet jeśli jest dostępny.

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

Wskaźnik obiektu określa adres obiektu, który jest używany do uzyskiwania dostępu do obiektu przy użyciu interfejsu API ThreadX.

### <a name="object-reserved-fields"></a>Pola zarezerwowane obiektów

W przypadku wszystkich obiektów innych niż wątki te zastrzeżone pola powinny mieć 0. W przypadku wątków priorytet wątku w momencie jego wprowadzeniu do rejestru jest umieszczany w tych dwóch zastrzeżonych polach.

### <a name="object-parameters"></a>Parametry obiektu

Parametry obiektu zawierają dodatkowe informacje o obiekcie. Poniżej opisano dodatkowe informacje dla każdego obiektu ThreadX:

| **Typ obiektu**        | **Parametr 1**  | **Parametr 2** |
|----------------------- | ---------------- | --------------- |
| Thread                 | Początek stosu      | Rozmiar stosu |
| Czasomierz                  | Początkowe takty | Ponowne harmonogramy takt |
| Kolejka                  | Rozmiar kolejki | Rozmiar komunikatu |
| Semaphore              | Wystąpienia początkowe | - |
| Mutex                  | Flaga dziedziczenia | - |
| Grupa flag zdarzeń      | - | - |
| Blokowa pula             | Łączna liczba bloków | Rozmiar bloku |
| Pula bajtów              | Całkowita liczba bajtów | - |
| .. /media                  | Rozmiar pamięci podręcznej Fat | Rozmiar pamięci podręcznej sektora |
| Plik                   | - | - |
| Adres IP                     | Początek stosu | Rozmiar stosu |
| Pula pakietów            | Rozmiar pakietu | Liczba pakietów |
| Gniazdo TCP             | Adres IP | Rozmiar okna |
| Gniazdo UDP             | Adres IP | Maksymalna liczba kolejek RX |

### <a name="object-name"></a>Nazwa obiektu

Nazwa obiektu zawiera nazwę obiektu ThreadX. Nazwa jest nazwą podaną dla ThreadX w momencie utworzenia obiektu. Domyślnie nazwa obiektu ma maksymalnie 32 znaki. Rzeczywiste nazwy większe niż 32 znaki są obcinane.

## <a name="event-trace-entries"></a>Wpisy śledzenia zdarzeń

Wpisy śledzenia zdarzeń znajdują się w dolnej części buforu śledzenia zdarzeń. Wpisy są utrzymywane na cyklicznej liście, z bieżącym wskaźnikiem wpisu, który wskazuje na najstarszy wpis. Liczba wpisów na liście jest obliczana przez wywołanie ***tx_trace_enable*** .

Każdy wpis rejestru obiektów zawiera informacje o określonym zdarzeniu śledzenia ThreadX. Następująca struktura danych definiuje każdy wpis zdarzenia śledzenia:

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

Wskaźnik wątku zawiera adres wątku uruchomionego w czasie tego zdarzenia. Jeśli zdarzenie wystąpiło podczas inicjowania (nie jest uruchomiony wątek), wartość tego wskaźnika jest 0xF0F0F0F0. Jeśli zdarzenie wystąpiło podczas procedury usługi przerwań (ISR), wartość tego wskaźnika jest 0xFFFFFFFF. Jeśli wpis nie został jeszcze użyty, wartość tego wskaźnika wynosi 0.

### <a name="thread-priority"></a>Priorytet wątku

Pole priorytetu wątku zawiera priorytet wątku i próg wywłaszczenia wątku, który był uruchomiony w czasie tego zdarzenia. Jeśli kontekst przerwania jest obecny (wskaźnik wątku jest 0xFFFFFFFF), wartość tego pola nie jest  priorytetem, ale _tx_thread_current_ptr w czasie zdarzenia. W przeciwnym razie wartość tego pola wynosi 0.

### <a name="event-id"></a>Identyfikator zdarzenia

Identyfikator zdarzenia określa zdarzenie, które miało miejsce. Prawidłowe identyfikatory zdarzeń śledzenia ThreadX zakres od 1 do 1024. Wartości zaczynające się od 1025 lub więcej są zarezerwowane dla zdarzeń specyficznych dla użytkownika. Pełną definicję identyfikatorów zdarzeń ThreadX można znaleźć w pliku ***tx_trace.h.***</td>

### <a name="information-fields-1-4"></a>Pola informacji (1–4)

Pola informacji zawierają dodatkowe informacje o określonym zdarzeniu. Pełny opis pól informacji dla każdego ze zdefiniowanych identyfikatorów zdarzeń ThreadX można znaleźć w pliku ***tx_trace.h.***