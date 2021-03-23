---
title: Rozdział 3 — Opis funkcjonalny klienta LWM2M
description: Ten rozdział zawiera opis funkcjonalny klienta programu LWM2M.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 24b7ff66fb4d060075eb6bc81bed45b3479e18dc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821841"
---
# <a name="chapter-3--functional-description-of-lwm2m-client"></a>Rozdział 3 funkcjonalny opis klienta LWM2M

> Ten rozdział zawiera opis funkcjonalny klienta programu LWM2M.

## <a name="lwm2m-client-initialization"></a>LWM2M inicjowanie klienta

Klient LWM2M jest inicjowany przez wywołanie usługi ***nx_lwm2m_client_create*** . Klient LWM2M działa we własnym wątku i może zgłosić pewne zdarzenia do aplikacji za pomocą wywołań zwrotnych lub przez wywołanie metod niestandardowych obiektów wdrożonych przez aplikację.

Ponadto należy utworzyć sesje klienta LWM2M przez wywołanie ***nx_lwm2m_client_session_create*** w celu włączenia komunikacji z co najmniej jednym serwerem. Sesja może komunikować się z dwoma różnymi typami serwerów: serwerem Bootstrap lub serwerem LWM2M (Zarządzanie urządzeniami).

### <a name="bootstrap-server-session"></a>Sesja serwera Bootstrap

Sesja komunikacji z serwerem Bootstrap służy do aprowizacji najważniejszych informacji w kliencie LWM2M, aby umożliwić klientowi LWM2M wykonywanie operacji "Register" z co najmniej jednym serwerem LWM2M. Ten typ serwera jest używany podczas inicjowania klienta i inicjowanego przez serwer trybów ładowania początkowego.

Aplikacja może uruchomić sesję ładowania początkowego przez wywołanie ***nx_lwm2m_client_session_bootstrap** _ lub _*_nx_lwm2m_client_session_bootstrap_dtls_*_, musi podać adres IP i numer portu serwera oraz opcjonalny identyfikator wystąpienia obiektu zabezpieczeń. Funkcja _*_nx_lwm2m_client_session_bootstrap_*_ używa niezabezpieczonej komunikacji, natomiast _ *_nx_lwm2m_client_session_bootstrap_dtls_** nawiązuje bezpieczne połączenie DTLS z serwerem.

Jeśli operacja ładowania początkowego zakończyła się powodzeniem, serwer Bootstrap powinien mieć utworzone wystąpienia obiektów zabezpieczeń dla serwerów Bootstrap i LWM2M oraz wystąpienia obiektów serwera dla serwerów LWM2M. Aplikacja może wywoływać ***nx_lwm2m_client_session_register_info_get*** , aby uzyskać informacje o serwerach lwm2m i użyć tych informacji do ustanowienia sesji z serwerem lwm2m.

Dane ładowania początkowego powinny zostać zapisane w pamięci nieulotnej przez aplikację w celu skonfigurowania klienta LWM2M przy następnym ponownym uruchomieniu urządzenia.

### <a name="lwm2m-server-session"></a>Sesja serwera LWM2M

Sesja komunikacji z serwerem LWM2M jest używana do rejestracji, zarządzania urządzeniami i włączania usług.

Aplikacja może zarejestrować klienta LWM2M na serwerze, wywołując ***nx_lwm2m_client_session_register** _ lub _*_nx_lwm2m_client_session_register_dtls_*_, musi podać adres IP i numer portu serwera oraz krótki identyfikator serwera, który odpowiada istniejącemu wystąpieniu obiektu serwera. Funkcja _*_nx_lwm2m_client_session_register_*_ używa niezabezpieczonej komunikacji, natomiast _ *_nx_lwm2m_client_session_register_dtls_** nawiązuje bezpieczne połączenie DTLS z serwerem.

Aplikacja może wyrejestrować klienta LWM2M przez wywołanie ***nx_lwm2m_client_session_deregister** _ i poproszenie klienta o wysłanie komunikatu "Update" przez wywołanie _ *_nx_lwm2m_client_session_update_* *.

### <a name="session-state-callback"></a>Wywołanie zwrotne stanu sesji

Aplikacja rejestruje wywołanie zwrotne podczas tworzenia sesji, która jest wywoływana w momencie aktualizacji stanu sesji, funkcja wywołania zwrotnego **NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK** ma następujący prototyp.

typedef VOID ( \* NX_LWM2M_CLIENT_SESSION_STATE_CALLBACK) (NX_LWM2M_CLIENT_SESSION \* SESSION_PTR, uint State);

Zdefiniowane są następujące Stany.

| &nbsp;Stan sesji | Opis |
| --- | --- |
| **NX_LWM2M_CLIENT_SESSION_INIT** | Stan początkowy po utworzeniu sesji. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_WAITING** | Klient czeka na wygaśnięcie czasomierza "wstrzymanie" lub zainicjowanie serwera Bootstrap. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_REQUESTING** | Klient wysłał komunikat "żądanie" do serwera Bootstrap (zainicjowany przez klienta). |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_INITIATED** | Klient otrzymuje dane z serwera Bootstrap. |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_FINISHED** | Serwer ładowania początkowego wysłał komunikat "gotowe". |
| **NX_LWM2M_CLIENT_SESSION_BOOTSTRAP_ERROR** | Sesja ładowania początkowego zakończyła się niepowodzeniem. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERING** | Klient wysłał komunikat "Register" do serwera LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_REGISTERED** | Klient jest zarejestrowany na serwerze LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_UPDATING** | Klient wysłał komunikat "Update" do serwera LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERING** | Klient wysłał komunikat "de-Register" do serwera LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DEREGISTERED** | Klient zostanie wyrejestrowany z serwera LWM2M. |
| **NX_LWM2M_CLIENT_SESSION_DISABLED** | Serwer LWM2M jest wyłączony. Po wygaśnięciu czasomierza Wyłącz zostanie wysłany komunikat "Register". |
| **NX_LWM2M_CLIENT_SESSION_ERROR** | Operacja rejestracji lub aktualizacji na serwerze LWM2M nie powiodła się. |
| **NX_LWM2M_CLIENT_SESSION_DELETED** | Wystąpienie obiektu serwera odpowiadające serwerowi LWM2M zostało usunięte. |

W przypadku błędu aplikacja może pobrać przyczynę błędu przez wywołanie ***nx_lwm2m_client_session_error_get***.

## <a name="local-device-management"></a>Zarządzanie urządzeniami lokalnymi

Aplikacja może uzyskiwać dostęp do obiektów klienta LWM2M za pomocą funkcji zarządzania urządzeniami lokalnymi. Dostępne są następujące funkcje.

| &nbsp;Nazwa funkcji | Opis |
| --- | --- |
| ***nx_lwm2m_client_object_read*** | Odczytaj zasoby z wystąpienia obiektu. |
| ***nx_lwm2m_client_object_discover*** | Pobierz listę zasobów wystąpienia obiektu.
| ***nx_lwm2m_client_object_write*** | Zapisz zasoby do wystąpienia obiektu. |
| ***nx_lwm2m_client_object_execute*** | Wykonaj operację wykonywania na zasobie wystąpienia obiektu. |
| ***nx_lwm2m_client_object_create*** | Utwórz nowe wystąpienie obiektu. |
| ***nx_lwm2m_client_object_delete*** | Usuń istniejące wystąpienie obiektu. |
| ***nx_lwm2m_client_object_next_get*** | Pobierz następny identyfikator obiektu przez klienta LWM2M. |
| ***nx_lwm2m_client_object_instance_next_get*** | Pobierz następne wystąpienie obiektu. |

## <a name="resource-information"></a>Informacje o zasobach

Podczas odczytywania i zapisywania do obiektów zasób jest reprezentowany przez strukturę NX_LWM2M_CLIENT_RESOURCE. Ta struktura zawiera identyfikator zasobu/wystąpienia i jego wartość.

Następujące funkcje są dostępne do ustawiania informacji o zasobach i wartości.

| &nbsp;Nazwa funkcji | Opis |
| --- | --- |
| ***nx_lwm2m_client_resource_info_set*** | Ustawianie informacji o zasobie: Identyfikator zasobu i operacja: Odczyt, zapis, plik WYKONYWALNy. |
| ***nx_lwm2m_client_resource_string_set*** | Ustaw wartość zasobu jako ciąg. |
| ***nx_lwm2m_client_resource_integer32_set*** | Ustaw wartość zasobu jako 32-bitową liczbę całkowitą. |
| ***nx_lwm2m_client_resource_integer64_set*** | Ustaw wartość zasobu jako 64-bitową liczbę całkowitą. |
| ***nx_lwm2m_client_resource_float32_set*** | Ustaw wartość zasobu jako 32-bitową zmiennoprzecinkową. |
| ***nx_lwm2m_client_resource_float64_set*** | Ustaw wartość zasobu jako 64-bitową zmiennoprzecinkową. |
| ***nx_lwm2m_client_resource_boolean_set*** | Ustaw wartość zasobu jako logiczną. |
| ***nx_lwm2m_client_resource_objlnk_set*** | Ustaw wartość zasobu jako link do obiektu. |
| ***nx_lwm2m_client_resource_opaque_set*** | Ustaw wartość zasobu jako nieprzezroczystą. |
| ***nx_lwm2m_client_resource_instance_set*** | Ustaw wartość zasobu jako wystąpienie dla wielu zasobów. |
| ***nx_lwm2m_client_resource_dim_set*** | Ustaw wymiar zasobu dla wielu zasobów na potrzeby odnajdywania. |

Do pobierania informacji o zasobach i wartości są dostępne następujące funkcje.

| &nbsp;Nazwa funkcji | Opis |
| --- | --- |
| ***nx_lwm2m_client_resource_info_get*** | Pobierz informacje o zasobie: Identyfikator zasobu i operacja: Odczyt, zapis, plik WYKONYWALNy. |
| ***nx_lwm2m_client_resource_string_get*** | Pobierz wartość zasobu ciągu. |
| ***nx_lwm2m_client_resource_integer32_get*** | Pobierz wartość 32-bitowego zasobu liczby całkowitej. |
| ***nx_lwm2m_client_resource_integer64_get*** | Pobierz wartość dla zasobu liczby całkowitej B4-bitowej. |
| ***nx_lwm2m_client_resource_float32_get*** | Pobierz wartość 32-bitowego zasobu zmiennoprzecinkowego. |
| ***nx_lwm2m_client_resource_float64_get*** | Pobierz wartość 64-bitowego zasobu zmiennoprzecinkowego. |
| ***nx_lwm2m_client_resource_boolean_get*** | Pobierz wartość zasobu logicznego. |
| ***nx_lwm2m_client_resource_objlnk_get*** | Pobierz wartość zasobu linku do obiektu. |
| ***nx_lwm2m_client_resource_opaque_get*** | Pobierz wartość nieprzezroczystego zasobu. |
| ***nx_lwm2m_client_resource_instance_get*** | Pobierz wystąpienie zasobu dla wielu zasobów. |
| ***nx_lwm2m_client_resource_dim_get*** | Pobierz wymiar zasobu dla wielu zasobów. |

## <a name="object-implementation"></a>Implementacja obiektu

Klient LWM2M implementuje wymagane obiekty LWM2M OMA: Security (0), Server (1), Access Control (2) i Device (3). Inne obiekty specyficzne dla urządzenia muszą być implementowane przez aplikację.

Do zdefiniowania obiektu służą dwie struktury danych: Struktura NX_LWM2M_CLIENT_OBJECT definiuje implementację obiektu, łącznie z IDENTYFIKATORem obiektu i metodami obiektu, a struktura NX_LWM2M_CLIENT_OBJECT_INSTANCE zawiera dane wystąpienia obiektu.

Dostępne są następujące funkcje.

| &nbsp;Nazwa funkcji | Opis |
| --- | --- |
| ***nx_lwm2m_client_object_add*** | Dodaj implementację obiektu do klienta LwM2M. |
| ***nx_lwm2m_client_object_remove*** | Usuń implementację obiektu z klienta LwM2M. |
| ***nx_lwm2m_client_object_instance_add*** | Dodaj wystąpienie obiektu do obiektu. |
| ***nx_lwm2m_client_object_instance_remove*** | Usuń wystąpienie obiektu z obiektu. |

Funkcja wywołania zwrotnego metody obiektu ma sygnaturę pokazaną poniżej.

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

### <a name="the-read-method"></a>Metoda "read"

Metoda "read" służy do odczytywania wartości zasobów z wystąpienia obiektu. Parametry są zdefiniowane w następujący sposób.

| Parametr | Opis |
| --- | --- |
| **operacje** | **NX_LWM2M_CLIENT_OBJECT_READ** |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasoby** | Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania. Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami. |
| **resource_count** | Wskaźnik na liczbę zasobów do odczytania. |
| **args_ptr** | Nieużywany parametr do odczytu. |
| **args_length** | Nieużywany parametr do odczytu. |

### <a name="the-discover-method"></a>Metoda "Discovery"

Metoda "Discovery" służy do pobierania listy wszystkich zasobów implementowanych przez obiekt. Parametry są zdefiniowane w następujący sposób.

| Parametr | Opis |
| --- | --- |
| **operacje** | **NX_LWM2M_CLIENT_OBJECT_DISCOVER** |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasoby** | Wskaźnik do tablicy NX_LWM2M_CLIENT_RESOURCE. Po powrocie tablica jest wypełniana odpowiednimi informacjami o zasobach. |
| **resource_count** | Wskaźnik na liczbę zasobów do odnalezienia. W przypadku zwracania ten parametr należy zaktualizować jako wartość true. |
| **args_ptr** | Nieużywany parametr do odnajdowania. |
| **args_length** | Nieużywany parametr do odnajdowania. |

### <a name="the-write-method"></a>Metoda "Write"

Metoda "Write" służy do aktualizowania lub zastępowania zasobów wystąpienia obiektu. Parametry są zdefiniowane w następujący sposób.

| Parametr  | Opis |
| --- | --- |
| **operacje** | **NX_LWM2M_CLIENT_OBJECT_WRITE** |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasoby** | Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania. Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami. |
| **resource_count** | Wskaźnik na liczbę zasobów do odnalezienia. |
| **args_ptr** | Zapisz flagi. |
| **args_length** | Długość argumentów. |

Do parametru *flag* można określić następujące operacje zapisu.

| Operacja | Akcja | Opis |
| --- | ---| --- |
| 0 | Aktualizacja częściowa | Dodaje lub aktualizuje zasoby podane w nowej wartości i pozostawia inne istniejące zasoby bez zmian.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_INSTANCE** | Zamień wystąpienie | Zamienia wystąpienie obiektu na nowe podane wartości zasobów.
| **NX_LWM2M_CLIENT_OBJECT_WRITE_REPLACE_RESOURCE** |  Zastąp zasób | Zamienia zasoby na nowe podane wartości zasobów (używane do zastępowania wielu zasobów). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_CREATE** | Utwórz wystąpienie | Inicjuje nowo utworzone wystąpienie obiektu o podanych wartościach zasobów (wywołanych z metody **_nx_lwm2m_object_create_** ). |
| **NX_LWM2M_CLIENT_OBJECT_WRITE_BOOTSTRAP** | Zapis ładowania początkowego | Wywoływana podczas sekwencji ładowania początkowego. |

### <a name="the-execute-method"></a>Metoda "Execute"

Metoda "Execute" implementuje wykonywanie zasobu obiektu.

Parametry wejściowe są zdefiniowane w następujący sposób.

| Parametr  | Opis |
| --- | --- |
| **operacje** | NX_LWM2M_CLIENT_OBJECT_EXECUTE |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasoby** | Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania. Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami. |
| **resource_count** | Wskaźnik na liczbę zasobów do odnalezienia. |
| **args_ptr** | Wskaźnik do argumentów. |
| **args_length** | Długość argumentów.  |

Funkcja musi zwrócić **NX_LWM2M_CLIENT_NOT_FOUND** , jeśli identyfikator zasobu nie istnieje lub **NX_LWM2M_CLIENT_METHOD_NOT_ALLOWED** , jeśli nie obsługuje wykonywania.

### <a name="the-create-method"></a>Metoda "Create"

Metoda "Create" implementuje Tworzenie nowego wystąpienia obiektu.

Parametry wejściowe są zdefiniowane w następujący sposób.

| Parametr  | Opis |
| --- | --- |
| **operacje** | **NX_LWM2M_CLIENT_OBJECT_CREATE** |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Nieużywany parametr. |
| **zasoby** | Wskaźnik do tablicy **NX_LWM2M_CLIENT_RESOURCE** zawierającej identyfikatory zasobów do odczytania. Po powrocie tablica jest wypełniana odpowiednimi typami i wartościami. |
| **resource_count** | Wskaźnik na liczbę zasobów do odnalezienia. |
| **args_ptr** | Identyfikator wystąpienia obiektu. |
| **args_length** | Długość argumentów. |

### <a name="the-delete-method"></a>Metoda "Delete"

Metoda "Delete" implementuje usuwanie wystąpienia obiektu. parametry wejściowe są zdefiniowane w następujący sposób.

| Parametr  | Opis |
| --- | --- |
| **operacje** | NX_LWM2M_CLIENT_OBJECT_DELETE |
| **object_ptr** | Wskaźnik do implementacji obiektu. |
| **instance_ptr** | Wskaźnik do wystąpienia obiektu. |
| **zasoby** | Nieużywany parametr. |
| **resource_count** | Nieużywany parametr. |
| **args_ptr** | Nieużywany parametr. |
| **args_length** | Nieużywany parametr. |

Po powodzeniu obiekt musi zwolnić dane wystąpienia obiektu i wszelkie inne zasoby przydzielone przez wystąpienie.

## <a name="example-of-lwm2m-client-application"></a>Przykład aplikacji klienckiej LWM2M

Poniższy kod jest przykładem prostej aplikacji klienckiej LWM2M, która implementuje urządzenie niestandardowe składające się z czujnika temperatury i przełącznika oświetlenia.

Urządzenie umożliwia serwerowi Odczytywanie wartości czujnika temperatury i stanu logicznego przełącznika światła oraz ustawienie opcji przełączania światła na Włącz/Wyłącz.

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