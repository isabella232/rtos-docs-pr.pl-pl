---
title: Rozdział 3 — Opis funkcjonalny Azure RTOS NetX CELUM2M
description: Ten rozdział zawiera opis funkcjonalny Azure RTOS NetX CELUM2M.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6424023a02aedf43c7433c9adc09231b8c146af13b9bddc15ebd1f2fc02e8c8a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784941"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-lwm2m"></a>Rozdział 3 — Opis funkcjonalny Azure RTOS NetX CELUM2M

Ten rozdział zawiera opis funkcjonalny Azure RTOS NetX CELUM2M.

## <a name="lwm2m-client-initialization"></a>Inicjalizacja klienta w programie CELUM2M

Klient THESM2M jest inicjowany przez wywołanie ***nx_lwm2m_client_create*** usługi. Klient THESM2M działa we własnym wątku i może zgłaszać niektóre zdarzenia do aplikacji za pomocą wywołań zwrotnych lub wywołując metody obiektów niestandardowych implementowane przez aplikację.

Ponadto sesje klienta ZESM2M muszą  zostać utworzone przez wywołanie nx_lwm2m_client_session_create w celu umożliwienia komunikacji z jednym lub większą ich liczby serwerami. Sesja może komunikować się z dwoma różnymi typami serwerów: serwerem Bootstrap lub serwerem DHCPM2M (Zarządzanie urządzeniami).

### <a name="bootstrap-server-session"></a>Sesja serwera bootstrap

Sesja komunikacji z serwerem Bootstrap służy do aprowizowania podstawowych informacji w kliencie SYSTEMM2M w celu umożliwienia klientowi SYSTEMU SYSTEMM2M wykonania operacji "Zarejestruj" przy użyciu jednego lub większej liczby serwerów SYSTEMM2M. Ten typ serwera jest używany w trybach bootstrap inicjowanych przez klienta i inicjowanych przez serwer.

Aplikacja może uruchomić sesję bootstrap, wywołując element ***nx_lwm2m_client_session_bootstrap** _ lub nx_lwm2m_client_session_bootstrap_dtls , musi _*_podać_*_ adres IP i numer portu serwera oraz opcjonalny identyfikator wystąpienia obiektu zabezpieczeń. Funkcja _*_nx_lwm2m_client_session_bootstrap_*_ używa niezabezpieczoną komunikację, natomiast funkcja _ *_nx_lwm2m_client_session_bootstrap_dtls_** ustanawia bezpieczne połączenie DTLS z serwerem.

Jeśli operacja bootstrap powiedzie się, serwer bootstrap powinien utworzyć wystąpienia obiektów zabezpieczeń dla serwerów Bootstrap i DSM2M oraz wystąpienia obiektów serwera dla serwerów THEM2M. Aplikacja musi użyć tych informacji do ustanowienia sesji z serwerami THEM2M.

Dane ładowania początkowego powinny być zapisywane w pamięci trwałej przez aplikację w celu skonfigurowania klienta SYSTEMM2M przy następnym ponownym uruchomieniu urządzenia.

### <a name="lwm2m-server-session"></a>SESJAM2M Sesji serwera

Sesja komunikacji z serwerem SYSTEMM2M służy do rejestracji, Zarządzanie urządzeniami i włączania usługi.

Aplikacja może zarejestrować klienta SIECI 2M na serwerze, wywołując adres ***nx_lwm2m_client_session_register** _ lub nx_lwm2m_client_session_register_dtls , _*_musi podać_*_ adres IP i numer portu serwera oraz krótki identyfikator serwera, który odpowiada istniejącemu wystąpieniu obiektu serwera. Funkcja _*_nx_lwm2m_client_session_register_*_ używa bezpiecznej komunikacji, natomiast funkcja _ *_nx_lwm2m_client_session_register_dtls_** ustanawia bezpieczne połączenie DTLS z serwerem.

Aplikacja może wyrejestrować klienta WIĘCM2M, wywołując element ***nx_lwm2m_client_session_deregister** _, i poprosić klienta o wysłanie komunikatu "Update" przez wywołanie funkcji __*_ nx_lwm2m_client_session_update **.

### <a name="session-state-callback"></a>Wywołanie zwrotne stanu sesji

Aplikacja rejestruje wywołanie zwrotne podczas tworzenia sesji, która jest wywoływana po zaktualizowaniu stanu sesji, funkcja wywołania zwrotnego NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK ma następujący prototyp:

```c
typedef VOID (*NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)
        (NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state);
```

Zdefiniowane są następujące stany:

- **NX_LWM2M_CLIENT_SESSION_INIT:** początkowy stan po utworzeniu sesji.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING:** klient oczekuje na wygaśnięcie czasomierza "Hold Off" lub zainicjowanego przez serwer ładowania początkowego.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:** klient wysłał komunikat "Żądanie" do serwera Bootstrap (proces bootstrap zainicjowany przez klienta).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:** klient odbiera dane z serwera Bootstrap.

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:** Serwer bootstrap wysłał komunikat "Finished" (Zakończono).

- **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:** Sesja ładowania początkowego nie powiodła się.

- **NX_LWM2M_CLIENT_SESSION_REGISTERING:** klient wysłał komunikat "Zarejestruj" do serwera THEM2M.

- **NX_LWM2M_CLIENT_SESSION_REGISTERED:** klient jest zarejestrowany na serwerze THEM2M.

- **NX_LWM2M_CLIENT_SESSION_UPDATING:** klient wysłał komunikat "Update" do serweraOWIEM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERING:** klient wysłał komunikat "De-register" do serwera THEM2M.

- **NX_LWM2M_CLIENT_SESSION_DEREGISTERED:** klient jest cokońcem zarejestrowanym z serwera THEM2M.

- **NX_LWM2M_CLIENT_SESSION_DISABLED:** Serwer JEST wyłączony. Po upływie czasu wyłączenia czasomierza zostanie wysłany znak "Zarejestruj".

- **NX_LWM2M_CLIENT_SESSION_ERROR:** Operacja rejestracji lub aktualizacji na serwerze THEM2M nie powiodła się.

- **NX_LWM2M_CLIENT_SESSION_DELETED:** Wystąpienie obiektu serwera odpowiadające serwerowi THEM2M zostało usunięte. W przypadku wystąpienia błędu aplikacja może pobrać przyczynę błędu, wywołując **_nx_lwm2m_client_session_error_get_**.

## <a name="local-device-management"></a>Lokalne Zarządzanie urządzeniami

Aplikacja może uzyskać dostęp do obiektów klienta URZĄDZENIA2M przy użyciu funkcji zarządzania urządzeniami lokalnymi. Dostępne są następujące funkcje:

- ***nx_lwm2m_client_object_read:*** odczyt zasobów z wystąpienia obiektu.

- ***nx_lwm2m_client_object_discover:*** pobierz listę zasobów wystąpienia obiektu.

- ***nx_lwm2m_client_object_write:*** zapis zasobów w wystąpieniu obiektu

- ***nx_lwm2m_client_object_execute:*** wykonaj operację Execute na zasobie wystąpienia obiektu.

- ***nx_lwm2m_client_object_create:*** utwórz nowe wystąpienie obiektu.

- ***nx_lwm2m_client_object_delete:*** usuń istniejące wystąpienie obiektu.

- ***nx_lwm2m_client_object_get_next:*** Pobierz następny identyfikator obiektu zaimplementowany przez klienta KOMPUTERA 2M.

- ***nx_lwm2m_client_object_instance_get_next:*** Pobierz następne wystąpienie obiektu.

## <a name="resource-information"></a>Informacje o zasobie

Podczas odczytywania i zapisywania w obiektach zasób jest reprezentowany przez NX_LWM2M_RESOURCE struktury. Ta struktura zawiera identyfikator zasobu/wystąpienia i jego wartość. Kodowanie wartości zależy od jej typu i źródła (aplikacji lub sieci).

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

- **nx_lwm2m_resource_id:** identyfikator zasobu lub wystąpienia.
- **nx_lwm2m_resource_type:** typ wartości, zobacz poniżej.
- **nx_lwm2m_resource_value:** wartość zasobu zależy od typu wartości.

Definiowany jest następujący typ wartości:

- **NX_LWM2M_RESOURCE_NONE:** pusty zasób.

- **NX_LWM2M_RESOURCE_STRING:** wartość ciągu UTF-8 z zakończeniem o wartości null przechowywana w *nx_lwm2m_resource_stringdata*.

- **NX_LWM2M_RESOURCE_INTEGER32:** wartość 32-bitowej liczby całkowitej przechowywana w *nx_lwm2m_resource_integer32data*.

- **NX_LWM2M_RESOURCE_INTEGER64:** 64-bitowa wartość całkowita przechowywana w *nx_lwm2m_resource_integer64data*.

- **NX_LWM2M_RESOURCE_FLOAT32:** 32-bitowa wartość zmiennoprzecinkowa przechowywana *w nx_lwm2m_resource_float32data*.

- **NX_LWM2M_RESOURCE_FLOAT64:** 64-bitowa wartość zmiennoprzecinkowa przechowywana *w nx_lwm2m_resource_float64data*.

- **NX_LWM2M_RESOURCE_BOOLEAN:** wartość logiczna przechowywana w nx_lwm2m_resource_booleandata *.*

- **NX_LWM2M_RESOURCE_OPAQUE:** nieprzezroczysta wartość zdefiniowana przez *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_OBJLNK:** wartość linku obiektu przechowywana w *nx_lwm2m_resource_objlnkdata*.

- **NX_LWM2M_RESOURCE_TLV:** wartość zakodowana w formacie TLV zdefiniowana przez *nx_lwm2m_resource_bufferdata*.

- **NX_LWM2M_RESOURCE_TEXT:** wartość Plain-Text zdefiniowana przez nx_lwm2m_resource_bufferdata *.*

- **NX_LWM2M_RESOURCE_MULTIPLE:** wiele zasobów zdefiniowanych przez *nx_lwm2m_resource_multipledata*. *nx_lwm2m_resource_multiple_ptr* jest wskaźnikiem do tablicy struktur **NX_LWM2M_RESOURCE** zawierających informacje o poszczególnych wystąpieniach zasobów.

- **NX_LWM2M_RESOURCE_MULTIPLE_TLV:** wiele zasobów zdefiniowanych *przez* nx_lwm2m_resource_multipledata . *nx_lwm2m_resource_multiple_ptr* jest wskaźnikiem do buforu zakodowane w formacie TLV.

Funkcje wygodne są dostępne do pobierania wartości i sprawdzania jej typu. Aplikacja nigdy nie powinna bezpośrednio uzyskać dostępu do pola *nx_lwm2m_resource_value* podczas pobierania wartości z NX_LWM2M_RESOURCE danych. Zdefiniowano następujące funkcje:

- ***nx_lwm2m_resource_get_:*** pobierz wartość o danym typie.
- ***nx_lwm2m_resource_multiple_get_:*** pobierz wartość o danym typie z zasobu wiele.

Za pomocą **NX_LWM2M_RESOURCE_IS_MULTIPLE**(typu) można sprawdzić, czy typ zasobu to wiele zasobów.

## <a name="object-implementation"></a>Implementacja obiektu

Klient SYSTEMM2M implementuje obowiązkowe obiekty OMAOWIEM2M: zabezpieczenia (0), serwer (1), Access Control (2) i urządzenie (3). Inne obiekty specyficzne dla urządzenia muszą zostać zaimplementowane przez aplikację.

Do definiowania obiektu są używane dwie struktury danych: struktura NX_LWM2M_OBJECT definiuje implementację obiektu, w tym identyfikator obiektu i metody obiektów, a struktura NX_LWM2M_OBJECT_INSTANCE zawiera dane wystąpienia obiektu.

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

- **nx_lwm2m_object_next:** następny obiekt na liście.
- **nx_lwm2m_object_id:** identyfikator obiektu.
- **nx_lwm2m_object_read:** Metoda "Read", zobacz poniżej.
- **nx_lwm2m_object_discover:** Metoda "Discover", zobacz poniżej.
- **nx_lwm2m_object_write:** Metoda "Write", zobacz poniżej.
- **nx_lwm2m_object_execute:** Metoda "Execute", zobacz poniżej.
- **nx_lwm2m_object_create:** Metoda "Create", zobacz poniżej.
- **nx_lwm2m_object_delete:** Metoda "Delete", zobacz poniżej.
- **nx_lwm2m_object_instances:** lista wystąpień obiektów, których działanie kończy się wartością NULL.

Struktura NX_LWM2M_OBJECT_INSTANCE ma następującą definicję:

```c
typedef struct NX_LWM2M_OBJECT_INSTANCE_STRUCT
{
    NX_LWM2M_OBJECT_INSTANCE * nx_lwm2m_object_instance_next;
    NX_LWM2M_ID nx_lwm2m_object_instance_id;
} NX_LWM2M_OBJECT_INSTANCE;
```

- **nx_lwm2m_object_instance_next:** Następne wystąpienie na liście.
- **nx_lwm2m_object_instance_id:** identyfikator wystąpienia obiektu.

Obiekt musi implementować metody odpowiadające operacji zdefiniowanych przez interfejs interfejsu Zarządzanie urządzeniami OWIETM2M: "Read", "Discover", "Write", "Execute", "Create" i "Delete". Metody "Create" i "Delete" można ustawić na wartość NULL, jeśli obiekt nie obsługuje dynamicznego tworzenia wystąpień.

### <a name="the-read-method"></a>Metoda "Read"

Metoda "Read" służy do odczytywania wartości zasobów z wystąpienia obiektu, a funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_read(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    NX_LWM2M_RESOURCE *values_ptr);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr:** Wskaźnik do implementacji obiektu.

- **instance_ptr:** wskaźnik do wystąpienia obiektu.

- **num_values:** liczba zasobów do odczytania.

- **values_ptr:** wskaźnik do tablicy NX_LWM2M_RESOURCE zawierającej identyfikatory zasobów do odczytania. Po zwróceniu tablica jest wypełniana odpowiednimi typami i wartościami.

### <a name="the-discover-method"></a>Metoda "Discover"

Metoda "Discover" służy do pobierania listy wszystkich zasobów zaimplementowanych przez obiekt . Funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_discover(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT *num_resources_ptr,
    NX_LWM2M_RESOURCE_INFO *resources_ptr);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr:** Wskaźnik do implementacji obiektu.

- **instance_ptr:** wskaźnik do wystąpienia obiektu.

- **num_resources_ptr:** po wejściu rozmiaru buforu docelowego, w danych wyjściowych liczba elementów zapisywanych w buforze.

- **resources_ptr:** wskaźnik do buforu docelowego.

Informacje o zasobie są zwracane w strukturze NX_LWM2M_RESOURCE_INFO zdefiniowanej w następujący sposób:

```c
typedef struct NX_LWM2M_RESOURCE_INFO_STRUCT
{
    NX_LWM2M_ID     nx_lwm2m_resource_info_id;
    USHORT          nx_lwm2m_resource_info_flags;
    UINT            nx_lwm2m_resource_info_dim;
} NX_LWM2M_RESOURCE_INFO;
```

- **nx_lwm2m_resource_info_id:** identyfikator zasobu.

- **nx_lwm2m_resource_info_flags:** zobacz poniżej.

- **nx_lwm2m_resource_info_dim:** wymiar wielu zasobów, jeśli ustawiono NX_LWM2M_RESOURCE_INFO_MULTIPLE flagi.

Pole *nx_lwm2m_resource_flags* mieć następujące wartości:

- 0: pojedynczy zasób, który można odczytać.

- **NX_LWM2M_RESOURCE_INFO_MULTIPLE:** należy zdefiniować *wiele nx_lwm2m_resource_info_dim* zasobów.

- **NX_LWM2M_RESOURCE_INFO_EXECUTABLE:** zasób wykonywalny lub nieczylny.

### <a name="the-write-method"></a>Metoda "Write"

Metoda "Write" służy do aktualizowania lub zastępowania zasobów wystąpienia obiektu. Funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_write(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, UINT num_values,
    const NX_LWM2M_RESOURCE *values_ptr, UINT write_op);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr:** Wskaźnik do implementacji obiektu.
- **instance_ptr:** wskaźnik do wystąpienia obiektu.
- **num_values:** liczba zasobów do zapisu.
- **values_ptr:** Wskaźnik do wartości zasobów.
- **write_op:** typ operacji zapisu.

Następujące operacje zapisu można określić w *parametrze write_op* :

- 0 Częściowa aktualizacja: dodaje lub aktualizuje zasoby podane w nowej wartości i &mdash; pozostawia inne istniejące zasoby bez zmian.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_INSTANCE** &mdash; Zastąp wystąpienie: zastępuje wystąpienie obiektu nowymi dostarczonymi wartościami zasobów.

- **NX_LWM2M_OBJECT_WRITE_REPLACE_RESOURCE** &mdash; Zastąp zasób: zastępuje zasoby nowymi wartościami zasobów (używanymi do zastępowania wielu zasobów).

- **NX_LWM2M_OBJECT_WRITE_CREATE** &mdash; Utwórz wystąpienie: inicjuje nowo utworzone wystąpienie obiektu przy użyciu podanych wartości zasobów (wywoływanych z *nx_lwm2m_object_create* metody ).

- **NX_LWM2M_OBJECT_WRITE_BOOTSTRAP** &mdash; Zapis bootstrap: wywoływany podczas sekwencji bootstrap.

### <a name="the-execute-method"></a>Metoda "Execute"

Metoda "Execute" implementuje wykonywanie zasobu obiektu, a funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_execute(NX_LWM2M_OBJECT *object_ptr,
    NX_LWM2M_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_ID resource_id,
    const CHAR *arguments_ptr);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr:** wskaźnik do implementacji obiektu
- **instance_ptr:** wskaźnik do wystąpienia obiektu.
- **resource_id:** identyfikator zasobu.
- **arguments_ptr:** wskaźnik do argumentów operacji wykonywania. Może mieć wartość *NULL, arguments_length* wartość zero.
- **arguments_length:** długość argumentów.

Funkcja musi zwrócić NX_LWM2M_NOT_FOUND, jeśli identyfikator zasobu nie istnieje, lub NX_LWM2M_METHOD_NOT_ALLOWED jeśli nie obsługuje wykonywania.

### <a name="the-create-method"></a>Metoda "Create"

Metoda "Create" implementuje tworzenie nowego wystąpienia obiektu, a funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_create(NX_LWM2M_OBJECT * object_ptr,
    NX_LWM2M_ID instance_id, UINT num_values, const NX_LWM2M_RESOURCE *values_ptr,
    NX_LWM2M_OBJECT_INSTANCE **instance_ptr, NX_LWM2M_BOOL bootstrap);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr:** Wskaźnik do implementacji obiektu.
- **instance_id:** identyfikator nowego wystąpienia.
- **num_values:** liczba zasobów do zainicjowania.
- **values_ptr:** Wskaźnik do wartości zasobów.
- **instance_ptr:** wskaźnik do wskaźnika docelowego utworzonego wystąpienia.
- **bootstrap:** wartość true, jeśli zostanie wywołana z sekwencji bootstrap.

Obiekt musi przydzielić i zainicjować nowe wystąpienie obiektu przy użyciu podanej listy wartości zasobów.

### <a name="the-delete-method"></a>Metoda "Delete"

Metoda "Delete" implementuje usuwanie wystąpienia obiektu, a funkcja ma następującą definicję:

```c
UINT nx_lwm2m_object_delete(NX_LWM2M_OBJECT *object_ptr,
                NX_LWM2M_OBJECT_INSTANCE *instance_ptr);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

- **object_ptr:** Wskaźnik do implementacji obiektu.
- **instance_ptr:** wskaźnik do wystąpienia obiektu.

W przypadku powodzenia obiekt musi zwolnić dane wystąpienia obiektu i wszelkie inne zasoby przydzielone przez wystąpienie.

### <a name="adding-object-implementations-and-instances-to-the-lwm2m-client"></a>Dodawanie implementacji obiektów i wystąpień do klienta PROJEKTUM2M

Aplikacja może dodać nową implementację obiektu do klienta ***---nx_lwm2m_client_object_add-***

Jeśli obiekt nie obsługuje dynamicznego tworzenia wystąpień, na przykład jeśli jest to obiekt tylko pojedynczego wystąpienia, pole *nx_lwm2m_object_instances* struktury obiektów powinno wskazać listę struktur wystąpień statycznych.

Jeśli obiekt obsługuje dynamiczne  tworzenie wystąpień, nx_lwm2m_object_instances należy ustawić wartość NULL, a zamiast tego należy użyć usługi ***nx_lwm2m_client_object_create*** w celu wywołania metody "Create" obiektu .

## <a name="example-of-lwm2m-client-application"></a>Przykład aplikacji klienckiej DOM2M

Poniższy kod jest przykładem prostej aplikacji klienckiej PRZEŁĄCZNIKM2M, która implementuje niestandardowe urządzenie składające się z czujnika temperatury i przełącznika światła.

Urządzenie umożliwia serwerowi odczytywanie wartości czujnika temperatury i stanu logicznych przełącznika światła oraz włączanie/wyłączanie przełącznika światła.

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
