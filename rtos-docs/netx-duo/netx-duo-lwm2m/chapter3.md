---
title: Rozdział 3 — Opis funkcjonalny klienta ZM2M
description: Ten rozdział zawiera funkcjonalny opis klienta KOMPUTERA 2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be6d9d854ce89140ce749fbeb0364678077337bf19ddc1055d286d0f624e8bd5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783462"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>Rozdział 3 Opis funkcjonalny klienta KOMPUTERAM2M

> Ten rozdział zawiera funkcjonalny opis klienta KOMPUTERA 2M.

## <a name="lwm2m-client-initialization"></a>Inicjowanie klienta PRZEZ 2018 r.

Klient SIECI 2M jest inicjowany przez wywołanie ***nx_lwm2m_client_create*** service. KlientOWIEM2M działa we własnym wątku i może zgłaszać niektóre zdarzenia do aplikacji za pomocą wywołań zwrotnych lub wywołując metody obiektów niestandardowych implementowane przez aplikację.

Ponadto należy utworzyć sesje klienta ZAM2M przez wywołanie nx_lwm2m_client_session_create w celu umożliwienia komunikacji z jednym lub większą ich liczby serwerami.  Sesja może komunikować się z dwoma różnymi typami serwerów: serwerem Bootstrap lub serwerem DHCPM2M (Zarządzanie urządzeniami).

### <a name="bootstrap-server-session"></a>Sesja serwera bootstrap

Sesja komunikacji z serwerem Bootstrap służy do aprowizowania podstawowych informacji w kliencie ZIEM2M w celu umożliwienia klientowi THEM2M wykonania operacji "Zarejestruj" na co najmniej jednym serwerze THEM2M. Ten typ serwera jest używany w trybach bootstrap inicjowanych przez klienta i inicjowanych przez serwer.

Aplikacja może uruchomić sesję bootstrap, wywołując element ***nx_lwm2m_client_session_bootstrap** _ lub _*_nx_lwm2m_client_session_bootstrap_dtls_*_, musi podać adres IP i numer portu serwera oraz opcjonalny identyfikator wystąpienia obiektu zabezpieczeń. Funkcja _*_nx_lwm2m_client_session_bootstrap_*_ używa bezpiecznej komunikacji, natomiast funkcja *__nx_lwm2m_client_session_bootstrap_dtls_** ustanawia bezpieczne połączenie DTLS z serwerem.

Jeśli operacja bootstrap powiedzie się, serwer bootstrap powinien utworzyć wystąpienia obiektów zabezpieczeń dla serwerów Bootstrap i ICHM2M oraz wystąpienia obiektów serwera dla serwerów THEM2M. Aplikacja może ***wywołać*** nx_lwm2m_client_session_register_info_get w celu uzyskania informacji o serwerach z programem THEM2M i użyć tych informacji do ustanowienia sesji z serwerami THEM2M.

Dane ładowania początkowego powinny zostać zapisane w pamięci trwałej przez aplikację w celu skonfigurowania klienta z systemem REBOOTM2M przy następnym ponownym uruchomieniu urządzenia.

### <a name="lwm2m-server-session"></a>SESJAM2M Server Session

Sesja komunikacji z serwerem SYSTEMM2M służy do rejestracji, Zarządzanie urządzeniami i włączania usługi.

Aplikacja może zarejestrować klienta SIECI 2M na serwerze, wywołując adres ***nx_lwm2m_client_session_register** _ lub nx_lwm2m_client_session_register_dtls , _*_musi_*_ podać adres IP i numer portu serwera oraz krótki identyfikator serwera, który odpowiada istniejącemu wystąpieniu obiektu serwera. Funkcja _*_nx_lwm2m_client_session_register_*_ używa bezpiecznej komunikacji, natomiast funkcja _ *_nx_lwm2m_client_session_register_dtls_** ustanawia bezpieczne połączenie DTLS z serwerem.

Aplikacja może wyrejestrować klienta ZM2M, wywołując element ***nx_lwm2m_client_session_deregister** _, i poprosić klienta o wysłanie komunikatu "Update", wywołując element _*_nx_lwm2m_client_session_update_**.

### <a name="session-state-callback"></a>Wywołanie zwrotne stanu sesji

Aplikacja rejestruje wywołanie zwrotne podczas tworzenia sesji, która jest wywoływana po zaktualizowaniu stanu sesji, a funkcja wywołania zwrotnego **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** ma następujący prototyp.

typedef VOID ( \* NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK)(NX_LWM2M_CLIENT_SESSION \* session_ptr,stan UINT);

Zdefiniowane są następujące stany.

| Stan &nbsp; sesji | Opis |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | Początkowy stan po utworzeniu sesji. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | Klient oczekuje na wygaśnięcie czasomierza "Hold Off" lub zainicjowanego przez serwer ładowania początkowego. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | Klient wysłał komunikat "Request" do serwera Bootstrap (proces bootstrap zainicjowany przez klienta). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | Klient odbiera dane z serwera Bootstrap. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | Serwer bootstrap wysłał komunikat "Finished" (Zakończono). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | Sesja ładowania początkowego nie powiodła się. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | Klient wysłał komunikat "Zarejestruj" do serwera THEM2M. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | Klient jest zarejestrowany na serwerze THEM2M. |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | Klient wysłał komunikat "Update" do serwera THEM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | Klient wysłał komunikat "De-register" do serwera THEM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | Klient jest rejestrowany z serwera THEM2M. |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | Serwer THEM2M jest wyłączony. Po upływie czasu wyłączenia czasomierza zostanie wysłany znak "Zarejestruj". |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | Operacja rejestracji lub aktualizacji na serwerze THEM2M nie powiodła się. |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | Usunięto wystąpienie obiektu serwera odpowiadające serwerowi THEM2M. |

W przypadku wystąpienia błędu aplikacja może pobrać przyczynę błędu, wywołując ***nx_lwm2m_client_session_error_get***.

## <a name="local-device-management"></a>Lokalne Zarządzanie urządzeniami

Aplikacja może uzyskać dostęp do obiektów klienta URZĄDZENIAM2M za pomocą funkcji zarządzania urządzeniami lokalnymi. Dostępne są następujące funkcje.

| Nazwa &nbsp; funkcji | Opis |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | Odczytywanie zasobów z wystąpienia obiektu. |
| ***nx_lwm2m_client_object_discover*** | Pobierz listę zasobów wystąpienia obiektu.
| ***nx_lwm2m_client_object_write*** | Zapisz zasoby w wystąpieniu obiektu. |
| ***nx_lwm2m_client_object_execute*** | Wykonaj operację Execute na zasobie wystąpienia obiektu. |
| ***nx_lwm2m_client_object_create*** | Utwórz nowe wystąpienie obiektu. |
| ***nx_lwm2m_client_object_delete*** | Usuń istniejące wystąpienie obiektu. |
| ***nx_lwm2m_client_object_next_get*** | Pobierz następny identyfikator obiektu przez klienta ZMIM2M. |
| ***nx_lwm2m_client_object_instance_next_get*** | Pobierz następne wystąpienie obiektu. |

## <a name="resource-information"></a>Informacje o zasobie

Podczas odczytywania i zapisywania w obiektach zasób jest reprezentowany przez NX_LWM2M_CLIENT_RESOURCE struktury. Ta struktura zawiera identyfikator zasobu/wystąpienia i jego wartość.

Następujące funkcje są dostępne do ustawiania informacji o zasobie i wartości.

| Nazwa &nbsp; funkcji | Opis |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | Ustaw informacje o zasobie: identyfikator zasobu i operację: ODCZYT, ZAPIS, PLIK WYKONYWALNY. |
| ***nx_lwm2m_client_resource_string_set*** | Ustaw wartość zasobu jako ciąg. |
| ***nx_lwm2m_client_resource_integer32_set*** | Ustaw wartość zasobu na 32-bitową liczbę całkowitą. |
| ***nx_lwm2m_client_resource_integer64_set*** | Ustaw wartość zasobu na 64-bitową liczbę całkowitą. |
| ***nx_lwm2m_client_resource_float32_set*** | Ustaw wartość zasobu na 32-bitową wartość zmiennoprzecinkową. |
| ***nx_lwm2m_client_resource_float64_set*** | Ustaw wartość zasobu na 64-bitową wartość zmiennoprzecinkową. |
| ***nx_lwm2m_client_resource_boolean_set*** | Ustaw wartość zasobu na wartość logiczną. |
| ***nx_lwm2m_client_resource_objlnk_set*** | Ustaw wartość zasobu jako link obiektu. |
| ***nx_lwm2m_client_resource_opaque_set*** | Ustaw wartość zasobu jako nieprzezroczystą. |
| ***nx_lwm2m_client_resource_instance_set*** | Ustaw wartość zasobu jako wystąpienie dla wielu zasobów. |
| ***nx_lwm2m_client_resource_dim_set*** | Ustaw wymiar zasobu dla wielu zasobów do odnajdywania. |

Następujące funkcje są dostępne do uzyskiwania informacji o zasobie i ich wartości.

| Nazwa &nbsp; funkcji | Opis |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | Uzyskaj informacje o zasobie: identyfikator zasobu i operację: ODCZYT, ZAPIS, PLIK WYKONYWALNY. |
| ***nx_lwm2m_client_resource_string_get*** | Pobierz wartość zasobu ciągu. |
| ***nx_lwm2m_client_resource_integer32_get*** | Pobierz wartość zasobu 32-bitowej liczby całkowitej. |
| ***nx_lwm2m_client_resource_integer64_get*** | Pobierz wartość zasobu liczby całkowitej b4-bitowej. |
| ***nx_lwm2m_client_resource_float32_get*** | Pobierz wartość 32-bitowego zasobu zmiennoprzecinkowa. |
| ***nx_lwm2m_client_resource_float64_get*** | Pobierz wartość 64-bitowego zasobu zmiennoprzecinkowa. |
| ***nx_lwm2m_client_resource_boolean_get*** | Pobierz wartość zasobu logicznych. |
| ***nx_lwm2m_client_resource_objlnk_get*** | Pobierz wartość zasobu linku obiektu. |
| ***nx_lwm2m_client_resource_opaque_get*** | Pobierz wartość nieprzezroczystego zasobu. |
| ***nx_lwm2m_client_resource_instance_get*** | Pobierz wystąpienie zasobu dla wielu zasobów. |
| ***nx_lwm2m_client_resource_dim_get*** | Pobierz wymiar zasobu dla wielu zasobów. |

## <a name="object-implementation"></a>Implementacja obiektu

Klient SYSTEMM2M implementuje obowiązkowe obiekty OMA POM2M: zabezpieczenia (0), serwer (1), Access Control (2) i urządzenie (3). Inne obiekty specyficzne dla urządzenia muszą być implementowane przez aplikację.

Do definiowania obiektu są używane dwie struktury danych: struktura NX_LWM2M_CLIENT_OBJECT definiuje implementację obiektu, w tym identyfikator obiektu i metody obiektów, NX_LWM2M_CLIENT_OBJECT_INSTANCE struktura zawiera dane wystąpienia obiektu.

Dostępne są następujące funkcje.

| Nazwa &nbsp; funkcji | Opis |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | Dodaj implementację obiektu do klienta Systemu Plików 2M. |
| ***nx_lwm2m_client_object_remove*** | Usuń implementację obiektu z klienta ProjektuM2M. |
| ***nx_lwm2m_client_object_instance_add*** | Dodaj wystąpienie obiektu do obiektu . |
| ***nx_lwm2m_client_object_instance_remove*** | Usuń wystąpienie obiektu z obiektu . |

Funkcja wywołania zwrotnego metody obiektu ma podpis pokazany poniżej.

```c
typedef UINT (*NX_LWM2M_CLIENT_OBJECT_OPERATION_CALLBACK)(
    UINT operation, 
    NX_LWM2M_CLIENT_OBJECT *object_ptr,
    NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr,
    NX_LWM2M_CLIENT_RESOURCE *resource,
    UINT *resource_count,
    VOID *args_ptr,
    UINT args_length);
```

### <a name="the-read-method"></a>Metoda "Read"

Metoda "Read" służy do odczytywania wartości zasobów z wystąpienia obiektu. Parametry są zdefiniowane w następujący sposób.

| Parametr | Opis |
| --- | --- |
| **Operacji** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasób** | Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania. Po zwróceniu tablica jest wypełniana odpowiednimi typami i wartościami. |
| **resource_count** | Wskaźnik do liczby odczytywanych zasobów. |
| **args_ptr** | Nieużywany parametr do odczytu. |
| **args_length** | Nieużywany parametr do odczytu. |

### <a name="the-discover-method"></a>Metoda "Discover"

Metoda "Discover" służy do pobierania listy wszystkich zasobów zaimplementowanych przez obiekt. Parametry są zdefiniowane w następujący sposób.

| Parametr | Opis |
| --- | --- |
| **Operacji** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasób** | Wskaźnik do tablicy NX_LWM2M_CLIENT_RESOURCE. Po zwróceniu tablica jest wypełniana odpowiednimi informacjami o zasobie. |
| **resource_count** | Wskaźnik do liczby zasobów do odnajdywania. Po zwróceniu tego parametru należy zaktualizować jako wartość true. |
| **args_ptr** | Nieużywany parametr do odnajdywania. |
| **args_length** | Nieużywany parametr do odnajdywania. |

### <a name="the-write-method"></a>Metoda "Write"

Metoda "Write" służy do aktualizowania lub zastępowania zasobów wystąpienia obiektu. Parametry są zdefiniowane w następujący sposób.

| Parametr  | Opis |
| --- | --- |
| **Operacji** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasób** | Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania. Po zwróceniu tablica jest wypełniana odpowiednimi typami i wartościami. |
| **resource_count** | Wskaźnik do liczby zasobów do odnajdywania. |
| **args_ptr** | Flagi zapisu. |
| **args_length** | Długość argumentów. |

Następujące operacje zapisu można określić dla *parametru flagi.*

| Operacja | Akcja | Opis |
| --- | ---| --- |
| 0 | Aktualizacja częściowa | Dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Zastępowanie wystąpienia | Zamienia wystąpienie obiektu na nowe podane wartości zasobów.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  Zastępowanie zasobu | Zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | Tworzenie wystąpienia | Inicjuje nowo utworzone wystąpienie obiektu przy użyciu podanych wartości zasobów (wywoływanych z **_nx_lwm2m_object_create_** metody ). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Zapis ładowania początkowego | Wywoływana podczas sekwencji bootstrap. |

### <a name="the-execute-method"></a>Metoda "Execute"

Metoda "Execute" implementuje wykonywanie zasobu obiektu.

Parametry wejściowe są zdefiniowane w następujący sposób.

| Parametr  | Opis |
| --- | --- |
| **Operacji** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasób** | Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania. Po zwróceniu tablica jest wypełniana odpowiednimi typami i wartościami. |
| **resource_count** | Wskaźnik do liczby zasobów do odnajdywania. |
| **args_ptr** | Wskaźnik do argumentów. |
| **args_length** | Długość argumentów.  |

Funkcja musi zwrócić **NX_LWM2M_CLIENT_NOT_FOUND,** jeśli identyfikator zasobu nie istnieje, lub NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED jeśli nie obsługuje wykonywania. 

### <a name="the-create-method"></a>Metoda "Create"

Metoda "Create" implementuje tworzenie nowego wystąpienia obiektu.

Parametry wejściowe są zdefiniowane w następujący sposób.

| Parametr  | Opis |
| --- | --- |
| **Operacji** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Nieużywany parametr. |
| **zasób** | Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania. Po zwróceniu tablica jest wypełniana odpowiednimi typami i wartościami. |
| **resource_count** | Wskaźnik do liczby zasobów do odnajdywania. |
| **args_ptr** | Identyfikator wystąpienia obiektu. |
| **args_length** | Długość argumentów. |

### <a name="the-delete-method"></a>Metoda "Delete"

Metoda "Delete" implementuje usuwanie wystąpienia obiektu. Parametry wejściowe są definiowane w następujący sposób.

| Parametr  | Opis |
| --- | --- |
| **Operacji** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasób** | Nieużywany parametr. |
| **resource_count** | Nieużywany parametr. |
| **args_ptr** | Nieużywany parametr. |
| **args_length** | Nieużywany parametr. |

W przypadku powodzenia obiekt musi zwolnić dane wystąpienia obiektu i wszelkie inne zasoby przydzielone przez wystąpienie.

## <a name="example-of-lwm2m-client-application"></a>Przykład aplikacji klienckiej DOM2M

Poniższy kod jest przykładem prostej aplikacji klienckiej PRZEŁĄCZNIKM2M, która implementuje niestandardowe urządzenie składające się z czujnika temperatury i przełącznika światła.

Urządzenie umożliwia serwerowi odczytywanie wartości czujnika temperatury i stanu logicznych przełącznika światła oraz włączanie/wyłączanie przełącznika światła.

```c
#include "nx_lwm2m_client.h"


/* Custom Object implementation. */

/* Temperature Object ID and resource IDs. */
#define IPSO_TEMPERATURE_OBJECT_ID   3303

#define IPSO_RESOURCE_MIN_VALUE      5601
#define IPSO_RESOURCE_MAX_VALUE      5602
#define IPSO_RESOURCE_RESET_MINMAX   5605
#define IPSO_RESOURCE_VALUE          5700
#define IPSO_RESOURCE_UNITS          5701

/* Actuation Object ID and resource IDs. */
#define IPSO_ACTUATION_OBJECT_ID     3306

#define IPSO_RESOURCE_ONOFF          5850

/* Define the Temperature Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_FLOAT32                   temperature;
    NX_LWM2M_FLOAT32                   min_temperature;
    NX_LWM2M_FLOAT32                   max_temperature;

} IPSO_TEMPERATURE_INSTANCE;

/* Define the Actuation Object Instance structure */
typedef struct
{
    /* The LWM2M Object Instance */
    NX_LWM2M_CLIENT_OBJECT_INSTANCE    object_instance;

    /* Resources Data */
    NX_LWM2M_BOOL                      onoff;

} IPSO_ACTUATION_INSTANCE;

/* IPSO Temperature */
/* Define the 'Read' Method */
UINT ipso_temperature_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_MIN_VALUE:

            /* return the minimum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> min_temperature);
            break;

        case IPSO_RESOURCE_MAX_VALUE:

            /* return the maximum measured temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> max_temperature);
            break;

        case IPSO_RESOURCE_VALUE:

            /* return the temperature value */
            nx_lwm2m_client_resource_float32_set(&resource[i], temp -> temperature);
            break;

        case IPSO_RESOURCE_RESET_MINMAX:

            /* Not readable */
            return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

        case IPSO_RESOURCE_UNITS:

            /* return the temperature units */
            nx_lwm2m_client_resource_string_set(&resource[i], "Cel", 3);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the 'Discover' method */
UINT ipso_temperature_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 5)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 5;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_MIN_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[1], IPSO_RESOURCE_MAX_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[2], IPSO_RESOURCE_RESET_MINMAX, NX_LWM2M_CLIENT_RESOURCE_OPERATION_EXECUTABLE);
    nx_lwm2m_client_resource_info_set(&resources[3], IPSO_RESOURCE_VALUE, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);
    nx_lwm2m_client_resource_info_set(&resources[4], IPSO_RESOURCE_UNITS, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ);

    return(NX_SUCCESS);
}

/* Define the 'Execute' method */
UINT ipso_temperature_execute(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, const CHAR *args_ptr, UINT args_length)
{
IPSO_TEMPERATURE_INSTANCE *temp = ((IPSO_TEMPERATURE_INSTANCE *) instance_ptr);
NX_LWM2M_CLIENT_RESOURCE value;
NX_LWM2M_ID resource_id;

    /* Get resource id */
    nx_lwm2m_client_resource_info_get(resource, &resource_id, NX_NULL);

    switch (resource_id)
    {

    case IPSO_RESOURCE_MIN_VALUE:
    case IPSO_RESOURCE_MAX_VALUE:
    case IPSO_RESOURCE_VALUE:
    case IPSO_RESOURCE_UNITS:

        /* read-only resource */
        return(NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED);

    case IPSO_RESOURCE_RESET_MINMAX:

        /* reset min/max values to current temperature */
        nx_lwm2m_client_resource_float32_set(&value, temp -> temperature);
        if (temp -> min_temperature != temp -> temperature)
        {
            temp -> min_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MIN_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }
        if (temp -> max_temperature != temp -> temperature)
        {
            temp -> max_temperature = temp -> temperature;
            nx_lwm2m_client_resource_info_set(&value, IPSO_RESOURCE_MAX_VALUE, NX_NULL);
            nx_lwm2m_client_object_resource_changed(object_ptr, instance_ptr, &value);
        }

        break;

    default:

        /* unknown resource ID */
        return(NX_LWM2M_CLIENT_NOT_FOUND);
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Temperature Object */
UINT ipso_temperature_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_temperature_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_temperature_discover(object_ptr, object_instance_ptr, resource, resource_count);

    case NX_LWM2M_CLIENT_OBJECT_EXECUTE:

        /* Call execute function */
        return ipso_temperature_execute(object_ptr, object_instance_ptr, resource, args_ptr, args_length);
    default:

        /*Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* IPSO Actuation */
/* Define the 'Read' Method */
UINT ipso_actuation_read(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* return the on/off value */
            nx_lwm2m_client_resource_boolean_set(&resource[i], act -> onoff);
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}


/* Define the 'Discover' method */
UINT ipso_actuation_discover(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resources, UINT *resource_count)
{
    if (*resource_count < 1)
    {
        return(NX_LWM2M_CLIENT_BUFFER_TOO_SMALL);
    }

    /* return the list of supported resources IDs */
    *resource_count = 1;
    nx_lwm2m_client_resource_info_set(&resources[0], IPSO_RESOURCE_ONOFF, NX_LWM2M_CLIENT_RESOURCE_OPERATION_READ_WRITE);

    return(NX_SUCCESS);
}

/* Define the 'Write' method */
UINT ipso_actuation_write(NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT resource_count, UINT flags)
{
IPSO_ACTUATION_INSTANCE *act = ((IPSO_ACTUATION_INSTANCE *) instance_ptr);
UINT ret;
NX_LWM2M_BOOL onoff;
UINT i;
NX_LWM2M_ID resource_id;

    for (i = 0 ; i < resource_count; i++)
    {
        nx_lwm2m_client_resource_info_get(&resource[i], &resource_id, NX_NULL);
        switch (resource_id)
        {

        case IPSO_RESOURCE_ONOFF:

            /* assign on/off boolean value */
            ret = nx_lwm2m_client_resource_boolean_get(&resource[i], &onoff);
            if (ret != NX_SUCCESS)
            {
                /* invalid value type */
                return(ret);
            }
            if (onoff != act->onoff)
            {
                act->onoff = onoff;

                printf("Set actuation switch %s\n", onoff ? "On" : "Off");
            }
            break;

        default:

            /* unknown resource ID */
            return(NX_LWM2M_CLIENT_NOT_FOUND);
        }
    }

    return(NX_SUCCESS);
}

/* Define the operation callback function of Actuation Object */
UINT ipso_actuation_operation(UINT operation, NX_LWM2M_CLIENT_OBJECT *object_ptr, NX_LWM2M_CLIENT_OBJECT_INSTANCE *object_instance_ptr, NX_LWM2M_CLIENT_RESOURCE *resource, UINT *resource_count, VOID *args_ptr, UINT args_length)
{
UINT write_op;

    switch (operation)
    {
    case NX_LWM2M_CLIENT_OBJECT_READ:

        /* Call read function */
        return ipso_actuation_read(object_ptr, object_instance_ptr, resource, *resource_count);
    case NX_LWM2M_CLIENT_OBJECT_DISCOVER:

        /* Call discover function */
        return ipso_actuation_discover(object_ptr, object_instance_ptr, resource, resource_count);
    case NX_LWM2M_CLIENT_OBJECT_WRITE:

        /* Get the type of write operation */
        write_op = *(UINT *)args_ptr;

        /* Call write function */
        return ipso_actuation_write(object_ptr, object_instance_ptr, resource, *resource_count, write_op);
    default:

        /* Unsupported operation */
        return(NX_LWM2M_CLIENT_NOT_SUPPORTED);
    }
}


/* NetX data.  */
NX_IP                   ip_0;
NX_PACKET_POOL          pool_0;

/* LWM2M Client data.  */
NX_LWM2M_CLIENT         client;
ULONG                   client_stack[4096 / sizeof(ULONG)];
NX_LWM2M_CLIENT_SESSION session;

/* Objects and instances.  */
NX_LWM2M_CLIENT_OBJECT      temperature_object;
NX_LWM2M_CLIENT_OBJECT      actuation_object;
IPSO_TEMPERATURE_INSTANCE   temperature_instance;
IPSO_ACTUATION_INSTANCE     actuation_instance;

/* Define the session state callback */
void session_callback(NX_LWM2M_CLIENT_SESSION *session_ptr, UINT state)
{
    printf("LWM2M Callback: -> %d\n", state);

    switch (state)
    {

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING:

        printf("Start client initiated bootstrap\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED:

        printf("Got message from boostrap server\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED:

         /* Bootstrap session done, we can register to the LWM2M Server */
        printf( "Boostrap finished.\n");
#ifdef BOOTSTRAP
        tx_semaphore_put(&semaphore_bootstarp_finish);
#endif
        break;

    case NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR:

        /* Failed to Bootstrap the LWM2M Client. */
        printf( "Failed to boostrap device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;

    case NX_LWM2M_CLIENT_SESSION_REGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device registered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DISABLED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device disabled.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_DEREGISTERED:

        /* Registration to the LWM2M Client done. */
        printf( "LWM2M device deregistered.\n");
        break;

    case NX_LWM2M_CLIENT_SESSION_ERROR:

        /* Failed to register to the LWM2M Client. */
        printf( "Failed to register device, error=%02x\n", nx_lwm2m_client_session_error_get(session_ptr));
        break;
    }
}


/* Application main thread */
void application_thread(ULONG info)
{

UINT status;
NX_LWM2M_ID server_id = 0;
NXD_ADDRESS server_addr;
CHAR *server_uri = NX_NULL;
UINT server_uri_len = 0;
UCHAR security_mode = 0;
   
    /* Create the LWM2M client */
    status = nx_lwm2m_client_create(&client, &ip_0, &pool_0, "nxlwm2mclient", sizeof("nxlwm2mclient") - 1, NX_NULL, 0, NX_LWM2M_CLIENT_BINDING_U, client_stack, sizeof(client_stack), 4);
    if (status)
    {
        return;
    }

    /* Define our custom objects: */
    /* Add Temperature Object */
    status = nx_lwm2m_client_object_add(&client, &temperature_object, IPSO_TEMPERATURE_OBJECT_ID, ipso_temperature_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    temperature_instance.temperature = 22.5f;
    temperature_instance.min_temperature = temperature_instance.temperature;
    temperature_instance.max_temperature = temperature_instance.temperature;
    status = nx_lwm2m_client_object_instance_add(&temperature_object, &temperature_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Add Actuation Object */
    status = nx_lwm2m_client_object_add(&client, &actuation_object, IPSO_ACTUATION_OBJECT_ID, ipso_actuation_operation);
    if (status)
    {
        return;
    }

    /* Define a single instance */
    actuation_instance.onoff = NX_FALSE;
    status = nx_lwm2m_client_object_instance_add(&actuation_object, &actuation_instance.object_instance, NX_NULL);
    if (status)
    {
        return;
    }

    /* Create a session */
    status = nx_lwm2m_client_session_create(&session, &client, session_callback);
    if (status)
    {
        return;
}

    /* Set bootstrap server address.  */
    server_addr.nxd_ip_version = NX_IP_VERSION_V4;
    server_addr.nxd_ip_address.v4 = IP_ADDRESS(23, 97, 187, 154);

    printf("Start boostraping\r\n");
    status = nx_lwm2m_client_session_bootstrap(&session, 0, &server_addr, 5783);
    if (status)
    {
        return;
    }

    status = nx_lwm2m_client_session_register_info_get(&session, NX_LWM2M_CLIENT_RESERVED_ID, &server_id, &server_uri, &server_uri_len, &security_mode, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL, NX_NULL);
    if (status || (security_mode != NX_LWM2M_CLIENT_SECURITY_MODE_NOSEC))
    {
        return;
    }

printf("Register to LWM2M server\r\n");
status = nx_lwm2m_client_session_register(&session, server_id, &server_addr, 5683);

    if (status)
    {
        return;
    }

    /* Application main loop */
    while (1)
    {

        /* application code... */
        tx_thread_sleep(NX_IP_PERIODIC_RATE);
    }

    /* Terminate the LWM2M Client */
    nx_lwm2m_client_delete(&client);
}

```