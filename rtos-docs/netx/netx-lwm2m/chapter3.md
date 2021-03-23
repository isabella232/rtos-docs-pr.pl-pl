---
title: Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX LWM2M
description: Ten rozdział zawiera opis funkcjonalny usługi Azure RTO NetX LWM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f49a4f5f4c899dfa461a9d57a8b56e4503d6acd4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822584"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX LWM2M

Ten rozdział zawiera opis funkcjonalny usługi Azure RTO NetX LWM2M.

## <a name="lwm2m-client-initialization"></a>LWM2M inicjowanie klienta

Klient LWM2M jest inicjowany przez wywołanie usługi ***nx_lwm2m_client_create*** . Klient LWM2M działa we własnym wątku i może zgłosić pewne zdarzenia do aplikacji za pomocą wywołań zwrotnych lub przez wywołanie metod niestandardowych obiektów wdrożonych przez aplikację.

Ponadto należy utworzyć sesje klienta LWM2M przez wywołanie ***nx_lwm2m_client_session_create*** w celu włączenia komunikacji z co najmniej jednym serwerem. Sesja może komunikować się z dwoma różnymi typami serwerów: serwerem Bootstrap lub serwerem LWM2M (Zarządzanie urządzeniami).

### <a name="bootstrap-server-session"></a>Sesja serwera Bootstrap

Sesja komunikacji z serwerem Bootstrap służy do aprowizacji najważniejszych informacji w kliencie LWM2M, aby umożliwić klientowi LWM2M wykonywanie operacji "Register" z co najmniej jednym serwerem LWM2M. Ten typ serwera jest używany podczas inicjowania klienta i inicjowanego przez serwer trybów ładowania początkowego.

Aplikacja może uruchomić sesję ładowania początkowego przez wywołanie ***nx_lwm2m_client_session_bootstrap** _ lub _*_nx_lwm2m_client_session_bootstrap_dtls_*_, musi podać adres IP i numer portu serwera oraz opcjonalny identyfikator wystąpienia obiektu zabezpieczeń. Funkcja _*_nx_lwm2m_client_session_bootstrap_*_ używa niezabezpieczonej komunikacji, natomiast _ *_nx_lwm2m_client_session_bootstrap_dtls_** nawiązuje bezpieczne połączenie DTLS z serwerem.

Jeśli operacja ładowania początkowego zakończyła się powodzeniem, serwer Bootstrap powinien mieć utworzone wystąpienia obiektów zabezpieczeń dla serwerów Bootstrap i LWM2M oraz wystąpienia obiektów serwera dla serwerów LWM2M. Aplikacja musi używać tych informacji do ustanawiania sesji z serwerami LWM2M.

Dane ładowania początkowego powinny zostać zapisane w pamięci nieulotnej przez aplikację w celu skonfigurowania klienta LWM2M przy następnym ponownym uruchomieniu urządzenia.

### <a name="lwm2m-server-session"></a>Sesja serwera LWM2M

Sesja komunikacji z serwerem LWM2M jest używana do rejestracji, zarządzania urządzeniami i włączania usług.

Aplikacja może zarejestrować klienta LWM2M na serwerze, wywołując ***nx_lwm2m_client_session_register** _ lub _*_nx_lwm2m_client_session_register_dtls_*_, musi podać adres IP i numer portu serwera oraz krótki identyfikator serwera, który odpowiada istniejącemu wystąpieniu obiektu serwera. Funkcja _*_nx_lwm2m_client_session_register_*_ używa niezabezpieczonej komunikacji, natomiast _ *_nx_lwm2m_client_session_register_dtls_** nawiązuje bezpieczne połączenie DTLS z serwerem.

Aplikacja może wyrejestrować klienta LWM2M przez wywołanie ***nx_lwm2m_client_session_deregister** _ i poproszenie klienta o wysłanie komunikatu "Update" przez wywołanie _ *_nx_lwm2m_client_session_update_* *.

### <a name="session-state-callback"></a>Wywołanie zwrotne stanu sesji

Aplikacja rejestruje wywołanie zwrotne podczas tworzenia sesji, która jest wywoływana w momencie aktualizacji stanu sesji, funkcja wywołania zwrotnego NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK ma następujący prototyp:

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

Zdefiniowane są następujące stany:

- **NX_LWM2M_CLIENT_SESSION_INIT**: stan początkowy po utworzeniu sesji.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING**: klient czeka na zakończenie okresu ważności czasomierza "wstrzymanie" lub zainicjowanie serwera.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING**: klient wysłał komunikat "Request" do serwera Bootstrap (zainicjowany przez klienta).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED**: klient otrzymuje dane z serwera Bootstrap.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED**: serwer ładowania początkowego wysłał komunikat "gotowe".

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR**: sesja ładowania początkowego zakończyła się niepowodzeniem.

- **NX_LWM2M_CLIENT_SESSION_REGISTERING**: klient wysłał komunikat "Register" do serwera LWM2M.

- **NX_LWM2M_CLIENT_SESSION_REGISTERED**: klient jest zarejestrowany na serwerze LWM2M.

- **NX_LWM2M_CLIENT_SESSION_UPDATING**: klient wysłał komunikat "Update" do serwera LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING**: klient wysłał komunikat "de-Register" do serwera LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED**: klient jest Wyrejestrowanie z serwera LWM2M.

- **NX_LWM2M_CLIENT_SESSION_DISABLED**: serwer LWM2M jest wyłączony. Po wygaśnięciu czasomierza Wyłącz zostanie wysłany komunikat "Register".

- **NX_LWM2M_CLIENT_SESSION_ERROR**: operacja rejestracji lub aktualizacji na serwerze LWM2M nie powiodła się.

- **NX_LWM2M_CLIENT_SESSION_DELETED**: wystąpienie obiektu serwera odpowiadające serwerowi LWM2M zostało usunięte. W przypadku błędu aplikacja może pobrać przyczynę błędu przez wywołanie **_nx_lwm2m_client_session_error_get_**.

## <a name="local-device-management"></a>Zarządzanie urządzeniami lokalnymi

Aplikacja może uzyskiwać dostęp do obiektów klienta LWM2M za pomocą funkcji zarządzania urządzeniami lokalnymi. Dostępne są następujące funkcje:

- ***nx_lwm2m_client_object_read***: Odczytuj zasoby z wystąpienia obiektu.

- ***nx_lwm2m_client_object_discover***: Pobierz listę zasobów wystąpienia obiektu.

- ***nx_lwm2m_client_object_write***: zapisywanie zasobów do wystąpienia obiektu

- ***nx_lwm2m_client_object_execute***: wykonaj operację EXECUTE na zasobie wystąpienia obiektu Object.

- ***nx_lwm2m_client_object_create***: Utwórz nowe wystąpienie obiektu.

- ***nx_lwm2m_client_object_delete***: Usuń istniejące wystąpienie obiektu.

- ***nx_lwm2m_client_object_get_next***: Pobierz następny identyfikator obiektu zaimplementowany przez klienta lwm2m.

- ***nx_lwm2m_client_object_instance_get_next***: Pobierz następne wystąpienie obiektu.

## <a name="resource-information"></a>Informacje o zasobach

Podczas odczytywania i zapisywania do obiektów zasób jest reprezentowany przez strukturę NX_LWM2M_RESOURCE. Ta struktura zawiera identyfikator zasobu/wystąpienia i jego wartość. Kodowanie wartości zależy od jego typu i jego pochodzenia (aplikacji lub sieci).

Struktura NX_LWM2M_RESOURCE ma następującą definicję:

```c
typedef struct NX_LWM2M_RESOURCE_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_id;
    UCHAR           nx_lwm2m_resource_type;
    union
    {
        struct
        {
            const VOID *     nx_lwm2m_resource_buffer_ptr;
            UINT             nx_lwm2m_resource_buffer_length;
        } nx_lwm2m_resource_bufferdata;
        const CHAR *         nx_lwm2m_resource_stringdata;
        NX_LWM2M_INT32       nx_lwm2m_resource_integer32data;
        NX_LWM2M_INT64       nx_lwm2m_resource_integer64data;
        NX_LWM2M_FLOAT32     nx_lwm2m_resource_float32data;
        NX_LWM2M_FLOAT64     nx_lwm2m_resource_float64data;
        NX_LWM2M_BOOL        nx_lwm2m_resource_booleandata;
        NX_LWM2M_OBJLNK      nx_lwm2m_resource_objlnkdata;
        
        struct
        {
            const VOID *     nx_lwm2m_resource_multiple_ptr;
            UINT             nx_lwm2m_resource_multiple_dim;
        } nx_lwm2m_resource_multipledata;
    } nx_lwm2m_resource_value;
} NX_LWM2M_RESOURCE;
```

- **nx_lwm2m_resource_id**: Identyfikator zasobu lub wystąpienia.
- **nx_lwm2m_resource_type**: typ wartości, zobacz poniżej.
- **nx_lwm2m_resource_value**: wartość zasobu zależy od typu wartości.

Zdefiniowano następujący typ wartości:

- **NX_LWM2M_RESOURCE_NONE**: pusty zasób.

- **NX_LWM2M_RESOURCE_STRING**: wartość ciągu UTF-8 zakończona wartością null jest przechowywana w *nx_lwm2m_resource_stringdata*.

- **NX_LWM2M_RESOURCE_INTEGER32**: 32-bitowej wartości całkowitej przechowywanej w *nx_lwm2m_resource_integer32data*.

- **NX_LWM2M_RESOURCE_INTEGER64**: 64-bitowej wartości całkowitej przechowywanej w *nx_lwm2m_resource_integer64data*.

- **NX_LWM2M_RESOURCE_FLOAT32**: 32-bitowej wartości zmiennoprzecinkowej przechowywanej w *nx_lwm2m_resource_float32data*.

- **NX_LWM2M_RESOURCE_FLOAT64**: 64-bitowej wartości zmiennoprzecinkowej przechowywanej w *nx_lwm2m_resource_float64data*.

- **NX_LWM2M_RESOURCE_BOOLEAN**: wartość logiczna przechowywana w *nx_lwm2m_resource_booleandata*.

- **NX_LWM2M_RESOURCE_OPAQUE**: wartość nieprzezroczysta zdefiniowana przez *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_OBJLNK**: wartość linku obiektu przechowywana w *nx_lwm2m_resource_objlnkdata*.

- **NX_LWM2M_RESOURCE_TLV**: wartość zakodowana przez element TLV zdefiniowana przez *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_TEXT**: wartość zakodowana Plain-Text zdefiniowana przez *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_MULTIPLE**: wiele zasobów zdefiniowanych przez *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* jest wskaźnikiem do tablicy struktur **NX_LWM2M_RESOURCE** zawierających informacje o poszczególnych wystąpieniach zasobów.

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV**: wiele zasobów zdefiniowanych przez *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* jest wskaźnikiem do buforu zakodowanego za pomocą obiektu TLV.

W celu pobrania wartości i sprawdzenia jej typu aplikacja nie powinna bezpośrednio uzyskiwać dostępu do pola *nx_lwm2m_resource_value* podczas pobierania wartości ze struktury NX_LWM2M_RESOURCE. Zdefiniowane są następujące funkcje:

- ***nx_lwm2m_resource_get_***: Pobierz wartość o podanym typie.
- ***nx_lwm2m_resource_multiple_get_***: Pobierz wartość o danym typie z wielu zasobów.

Makro **NX_LWM2M_RESOURCE_IS_MULTIPLE**(typ) może służyć do sprawdzenia, czy typem zasobu jest wiele zasobów.

## <a name="object-implementation"></a>Implementacja obiektu

Klient LWM2M implementuje wymagane obiekty LWM2M OMA: Security (0), Server (1), Access Control (2) i Device (3). Inne obiekty specyficzne dla urządzenia muszą być implementowane przez aplikację.

Do zdefiniowania obiektu służą dwie struktury danych: Struktura NX_LWM2M_OBJECT definiuje implementację obiektu, łącznie z IDENTYFIKATORem obiektu i metodami obiektu, a struktura NX_LWM2M_OBJECT_INSTANCE zawiera dane wystąpienia obiektu.

Struktura NX_LWM2M_OBJECT ma następującą definicję:

```c
typedef struct NX_LWM2M_OBJECT_STRUCT
{
    NX_LWM2M_OBJECT * nx_lwm2m_object_next;
    NX_LWM2M_ID nx_lwm2m_object_id;
    UINT (*nx_lwm2m_object_read)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
        NX_LWM2M_RESOURCE *values);
    UINT (*nx_lwm2m_object_discover)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources,
        NX_LWM2M_RESOURCE_INFO *resources);
    UINT (*nx_lwm2m_object_write)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values, const
        NX_LWM2M_RESOURCE *values, UINT write_op);
    UINT (*nx_lwm2m_object_execute)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
        const CHAR *args_ptr, UINT args_length);
    UINT (*nx_lwm2m_object_create)(NX_LWM2M_OBJECT * object_ptr,
        NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE
        *values, NX_LWM2M_OBJECT_INSTANCE **instance_ptr);
    UINT (*nx_lwm2m_object_delete)(NX_LWM2M_OBJECT *object_ptr,
        NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instances;
} NX_LWM2M_OBJECT;
```

- **nx_lwm2m_object_next**: Następny obiekt na liście.
- **nx_lwm2m_object_id**: identyfikator obiektu.
- **nx_lwm2m_object_read**: Metoda "read", patrz poniżej.
- **nx_lwm2m_object_discover**: Metoda "Discovery", patrz poniżej.
- **nx_lwm2m_object_write**: Metoda "Write", patrz poniżej.
- **nx_lwm2m_object_execute**: Metoda "Execute", patrz poniżej.
- **nx_lwm2m_object_create**: Metoda "Create", patrz poniżej.
- **nx_lwm2m_object_delete**: Metoda "Delete", patrz poniżej.
- **nx_lwm2m_object_instances**: Lista wystąpień obiektów zakończonych znakiem null.

Struktura NX_LWM2M_OBJECT_INSTANCE ma następującą definicję:

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next**: następne wystąpienie z listy.
- **nx_lwm2m_object_instance_id**: identyfikator wystąpienia obiektu.

Obiekt musi implementować metody odpowiadające operacjom zdefiniowanym przez interfejs zarządzania urządzeniami LWM2M: "read", "Discovery", "Write", "Execute", "Create" i "Delete". Metody "Create" i "Delete" można ustawić na wartość NULL, jeśli obiekt nie obsługuje dynamicznego tworzenia wystąpień.

### <a name="the-read-method"></a>Metoda "read"

Metoda "read" służy do odczytywania wartości zasobów z wystąpienia obiektu, funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr**: wskaźnik do implementacji obiektu.

- **instance_ptr**: wskaźnik do wystąpienia obiektu.

- **num_values**: liczba zasobów do odczytania.

- **values_ptr**: wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania. Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami.

### <a name="the-discover-method"></a>Metoda "Discovery"

Metoda "Discovery" służy do pobierania listy wszystkich zasobów zaimplementowanych przez obiekt, funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr**: wskaźnik do implementacji obiektu.

- **instance_ptr**: wskaźnik do wystąpienia obiektu.

- **num_resources_ptr**: przy wprowadzaniu rozmiaru buforu docelowego w danych wyjściowych liczba elementów WRITEN do buforu.

- **resources_ptr**: wskaźnik do bufora docelowego.

Informacje o zasobie są zwracane w strukturze NX_LWM2M_RESOURCE_INFO zdefiniowanej w następujący sposób:

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id**: Identyfikator zasobu.

- **nx_lwm2m_resource_info_flags**: Zobacz poniżej.

- **nx_lwm2m_resource_info_dim**: wymiar wielu zasobów, jeśli flaga NX_LWM2M_RESOURCE_INFO_MULTIPLE jest ustawiona.

Pole *nx_lwm2m_resource_flags* może mieć następujące wartości:

- 0: pojedynczy możliwy do odczytu zasób.

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE**: należy zdefiniować wiele zasobów, *nx_lwm2m_resource_info_dim* .

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE**: plik wykonywalny lub niemożliwy do odczytu.

### <a name="the-write-method"></a>Metoda "Write"

Metoda "Write" służy do aktualizowania lub zastępowania zasobów wystąpienia obiektu, funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr**: wskaźnik do implementacji obiektu.
- **instance_ptr**: wskaźnik do wystąpienia obiektu.
- **num_values**: liczba zasobów do zapisania.
- **values_ptr**: wskaźnik do wartości zasobów.
- **write_op**: typ operacji zapisu.

Do *write_op* parametru można określić następujące operacje zapisu:

- 0 &mdash; aktualizacja częściowa: dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Zamień wystąpienie: zamienia wystąpienie obiektu na nowe podane wartości zasobów.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Zastąp zasób: zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów).

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Utwórz wystąpienie: inicjuje nowo utworzone wystąpienie obiektu o podanych wartościach zasobów (wywołanych z metody *nx_lwm2m_object_create* ).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Zapis ładowania początkowego: wywoływany podczas sekwencji ładowania początkowego.

### <a name="the-execute-method"></a>Metoda "Execute"

Metoda "Execute" implementuje wykonywanie zasobu obiektu, a funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr**: wskaźnik do implementacji obiektu
- **instance_ptr**: wskaźnik do wystąpienia obiektu.
- **resource_id**: Identyfikator zasobu.
- **arguments_ptr**: wskaźnik do argumentów operacji Execute. Może mieć wartość NULL, jeśli *arguments_length* wynosi zero.
- **arguments_length**: długość argumentów.

Funkcja musi zwrócić NX_LWM2M_NOT_FOUND, jeśli identyfikator zasobu nie istnieje lub NX_LWM2M_METHOD_NOT_ALLOWED, jeśli nie obsługuje wykonywania.

### <a name="the-create-method"></a>Metoda "Create"

Metoda "Create" implementuje Tworzenie nowego wystąpienia obiektu, a funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr**: wskaźnik do implementacji obiektu.
- **instance_ID**: Identyfikator nowego wystąpienia.
- **num_values**: liczba zasobów do zainicjowania.
- **values_ptr**: wskaźnik do wartości zasobów.
- **instance_ptr**: wskaźnik do docelowego wskaźnika utworzonego wystąpienia.
- **Bootstrap**: true, jeśli wywołano z sekwencji Bootstrap.

Obiekt musi przydzielić i initialiaze nowe wystąpienie obiektu przy użyciu podanej listy wartości zasobów.

### <a name="the-delete-method"></a>Metoda "Delete"

Metoda "Delete" implementuje usuwanie wystąpienia obiektu, a funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr**: wskaźnik do implementacji obiektu.
- **instance_ptr**: wskaźnik do wystąpienia obiektu.

Po powodzeniu obiekt musi zwolnić dane wystąpienia obiektu i wszelkie inne zasoby przydzielone przez wystąpienie.

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>Dodawanie implementacji obiektów i wystąpień do klienta LWM2M

Aplikacja może dodać nową implementację obiektu do klienta LWM2M przez wywołanie usługi ***nx_lwm2m_client_object_add*** .

Jeśli obiekt nie obsługuje dynamicznego tworzenia wystąpień, na przykład jeśli jest tylko pojedynczym obiektem wystąpienia, pole *nx_lwm2m_object_instances* struktury obiektów powinno wskazywać na listę struktur wystąpień statycznych.

Jeśli obiekt obsługuje dynamiczne tworzenie wystąpień, *nx_lwm2m_object_instances* powinien mieć wartość null, a usługa ***nx_lwm2m_client_object_create*** powinna być używana zamiast tego w celu wywołania metody "Create" obiektu.

## <a name="example-of-lwm2m-client-application"></a>Przykład aplikacji klienckiej LWM2M

Poniższy kod jest przykładem prostej aplikacji klienckiej LWM2M, która implementuje urządzenie niestandardowe składające się z czujnika temperatury i przełącznika oświetlenia.

Urządzenie umożliwia serwerowi Odczytywanie wartości czujnika temperatury i stanu logicznego przełącznika światła oraz ustawienie opcji przełączania światła na Włącz/Wyłącz.

```c
#include "nx_lwm2m_client.h"

/* Custom Object implementation */
/* Define the Custom Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_OBJECT_INSTANCE     lwm2m;

    /* Resources Data */
    NX_LWM2M_FLOAT32             temperature;
    NX_LWM2M_BOOL                light;
} MYOBJECT_INSTANCE;

/* Define the Resources IDs */
#define MYOBJECT_RES_TEMPERATURE     0 /* temperature sensor */
#define MYOBJECT_RES_LIGHT           1 /* light switch */

/* Define the 'Read' Method */
UINT myobject_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
    UINT num_values, NX_LWM2M_RESOURCE *values)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        switch (values[i].nx_lwm2m_resource_id)
        {
        case MYOBJECT_RES_TEMPERATURE:

            /* return the temperature value */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_FLOAT32;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_float32data =
                ((MYOBJECT_INSTANCE *) instance_ptr)->temperature;
            break;
        case MYOBJECT_RES_LIGHT:

            /* return the state of the light switch */
            values[i].nx_lwm2m_resource_type = NX_LWM2M_RESOURCE_BOOLEAN;
            values[i].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata =
                ((MYOBJECT_INSTANCE *) instance_ptr)->light;
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Discover' method */
UINT myobject_discover(NX_LWM2M_OBJECT *object_ptr, NX_LWM2M_OBJECT_INSTANCE *instance_ptr,
                                    UINT *num_resources, NX_LWM2M_RESOURCE_INFO *resources)
{
    if (*num_resources < 2)
    {
        return NX_LWM2M_BUFFER_TOO_SMALL;
    }

    /* return the list of supported resources IDs */
    *num_resources = 2;
    resources[0].nx_lwm2m_resource_info_id        = MYOBJECT_RES_TEMPERATURE;
    resources[0].nx_lwm2m_resource_info_flags     = 0;
    resources[1].nx_lwm2m_resource_info_id        = MYOBJECT_RES_LIGHT;
    resources[1].nx_lwm2m_resource_info_flags     = 0;
    return NX_SUCCESS;
}

/* Define the 'Write' method */
UINT myobject_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values, UINT flags)
{
    UINT i;
    for (i=0; i<num_values; i++)
    {
        UINT ret;
        switch (values[i].nx_lwm2m_resource_id)
        {

        case MYOBJECT_RES_TEMPERATURE:

            /* read-only resource */
            return NX_LWM2M_METHOD_NOT_ALLOWED;

        case MYOBJECT_RES_LIGHT:

            /* assign boolean value */

            ret = nx_lwm2m_resource_get_boolean(&values[i],
                &((MYOBJECT_INSTANCE *) instance_ptr)->light);

            if (ret != NX_SUCCESS)
            {

                /* invalid value type */
                return ret;
            }
            break;

        default:

            /* unknown resource ID */
            return NX_LWM2M_NOT_FOUND;
        }
    }
    return NX_SUCCESS;
}

/* Define the 'Execute' method */
UINT myobject_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *args_ptr, UINT args_length)
{
    switch (resource_id)
    {

    case MYOBJECT_RES_TEMPERATURE:
    case MYOBJECT_RES_LIGHT:

        /* read-only resource */
        return NX_LWM2M_METHOD_NOT_ALLOWED;

    default:

        /* unknown resource ID */
        return NX_LWM2M_NOT_FOUND;

    }
}

/* NetX data */
NX_IP                       ip;
NX_PACKET_POOL              packet_pool;

/* LWM2M Client data */
NX_LWM2M_CLIENT             client;
ULONG                       client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION     session;

/* Custom Object Data */
NX_LWM2M_OBJECT             myobject;
MYOBJECT_INSTANCE           myinstance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

        /* Bootstrap session done, we can register to the LWM2M Server */
        {
            NX_LWM2M_ID security_id;

            /* find the Security Object Instance of the LWM2M Server */
            security_id = NX_LWM2M_RESERVED_ID;
            while (nx_lwm2m_client_object_instance_get_next(&client,
                NX_LWM2M_SECURITY_OBJECT_ID, &security_id) == NX_SUCCESS)
            {
                NX_LWM2M_RESOURCE res[3];

                /* retrieve instance data: */
                /* Bootstrap server flag */
                res[0].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_BOOTSTRAP_ID;

                /* URI of server */
                res[1].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_URI_ID;

                /* Short Server ID */
                res[2].nx_lwm2m_resource_id = NX_LWM2M_SECURITY_SHORT_SERVER_ID;

                /* Read Object Instance: */
                nx_lwm2m_client_object_read(&client,
                    NX_LWM2M_SECURITY_OBJECT_ID, security_id, 3, res);

                /* Not a bootstrap server? */
                if (!res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata)
                {
                    ULONG ip_addr;
                    UINT udp_port;

                    /* get IP address and UDP port from server URI */
                    parse_uri(res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata, &ip_addr, &udp_port);

                    /* Start registration to the LWM2M server */
                    nx_lwm2m_client_session_register(&session,
                        (NX_LWM2M_ID) res[2].nx_lwm2m_resource_value.
                        nx_lwm2m_resource_integer32data,
                        ip_addr, udp_port);
                    break;
                }
            }
        }
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        break;
    }
}

/* Application main thread */
void application_thread(ULONG info)
{
    NX_LWM2M_RESOURCE res[4];
    NX_LWM2M_ID security_id;

    /* Create the LWM2M client */
    nx_lwm2m_client_create(&client, &ip, &packet_pool, NX_LWM2M_COAP_PORT,
        "mylwm2mclient", NULL, NX_LWM2M_BINDING_U,
        client_stack, sizeof(client_stack));

    /* Define our custom object */
    myobject.nx_lwm2m_object_id           = 1024;
    myobject.nx_lwm2m_object_read         = myobject_read;
    myobject.nx_lwm2m_object_discover     = myobject_discover;
    myobject.nx_lwm2m_object_write        = myobject_write;
    myobject.nx_lwm2m_object_execute      = myobject_execute;
    myobject.nx_lwm2m_object_create       = NULL;
    myobject.nx_lwm2m_object_delete       = NULL;

    /* Define a single instance */
    myobject.nx_lwm2m_object_instances             = (NX_LWM2M_OBJECT_INSTANCE *) &myinstance;
    myinstance.lwm2m.nx_lwm2m_object_instance_id   = 0;
    myinstance.lwm2m.nx_lwm2m_object_instance_next = NULL;
    myinstance.temperature                         = 22.5f;
    myinstance.light                               = NX_FALSE;

    /* Add the object to the LWM2M Client */
    nx_lwm2m_client_object_add(&client, &myobject);

    /* Create a security entry for the bootstrap server */
    security_id = 0;

    /* set the URI of the server */
    res[0].nx_lwm2m_resource_id                                 = NX_LWM2M_SECURITY_URI_ID;
    res[0].nx_lwm2m_resource_type                               = NX_LWM2M_RESOURCE_STRING;
    res[0].nx_lwm2m_resource_value.nx_lwm2m_resource_stringdata = "coap://1.2.3.4";

    /* set the Bootstrap flag */
    res[1].nx_lwm2m_resource_id                                  = NX_LWM2M_SECURITY_BOOTSTRAP_ID;
    res[1].nx_lwm2m_resource_type                                = NX_LWM2M_RESOURCE_BOOLEAN;
    res[1].nx_lwm2m_resource_value.nx_lwm2m_resource_booleandata = NX_TRUE;

    /* set the security mode */
    res[2].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_MODE_ID;
    res[2].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[2].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data =
    NX_LWM2M_SECURITY_MODE_NOSEC;

    /* set the Hold Off timer */
    res[3].nx_lwm2m_resource_id                                    = NX_LWM2M_SECURITY_HOLD_OFF_ID;
    res[3].nx_lwm2m_resource_type                                  = NX_LWM2M_RESOURCE_INTEGER32;
    res[3].nx_lwm2m_resource_value.nx_lwm2m_resource_integer32data = 10;
    nx_lwm2m_client_object_create(&client, NX_LWM2M_SECURITY_OBJECT_ID,
        &security_id, 4, res);

    /* Create a session */
    nx_lwm2m_client_session_create(&session, &client, session_callback);

    /* start bootstrap session */
    nx_lwm2m_client_session_bootstrap(&session, security_id,
                            IP_ADDRESS(1, 2, 3, 4), 5683);

    /* Application main loop */
    while (1)
    {
        /* ...application code... */
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}
```
