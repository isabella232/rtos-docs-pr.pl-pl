---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo SNMP
description: Implementacja SNMP NetX Duo to Agent SNMP. Agent jest odpowiedzialny za odpowiadanie na polecenia menedżera SNMP i wysyłanie pułapek opartych na zdarzeniach.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821685"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo SNMP

Simple Network Management Protocol (SNMP) to protokół przeznaczony do zarządzania urządzeniami w Internecie. SNMP to protokół, który używa usług UDP (Unported User Datagram Protocol) do wykonywania funkcji zarządzania. Implementacja protokołu SNMP platformy Azure RTO NetX Duo to Agent SNMP. Agent jest odpowiedzialny za odpowiadanie na polecenia menedżera SNMP i wysyłanie pułapek opartych na zdarzeniach. 

NetX Duo SNMP obsługuje komunikację między protokołami IPv4 i IPv6 z menedżerami SNMP. NetX aplikacje SNMP powinny kompilować i uruchamiać w NetX Duo SNMP. Jednak deweloperzy są zachęcani do portów istniejących aplikacji SNMP do korzystania z równoważnych usług "Duo". Na przykład podczas wysyłania komunikatów pułapki SNMP następujące usługi "Duo" powinny zastąpić swój odpowiednik NetX:

*nxd_snmp_object_trap_send*

*nxd_snmp_object_trapv2_send*

*nxd_snmp_object_trapv3_send*

Aby uzyskać więcej informacji, zobacz **Opis usług agenta SNMP** w innym miejscu w tym przewodniku użytkownika, aby uzyskać więcej szczegółów.

## <a name="netx-duo-snmp-agent-requirements"></a>Wymagania dotyczące agenta SNMP NetX Duo

Pakiet SNMP NetX Duo wymaga, aby wystąpienie adresu IP zostało już utworzone. Ponadto należy włączyć protokół UDP dla tego samego wystąpienia IP.

Agent SNMP NetX Duo ma kilka dodatkowych wymagań. Najpierw wymaga dostępu do portu 161 do obsługi wszystkich żądań menedżera SNMP. Wymaga również dostępu do portu 162 do wysyłania komunikatów pułapki do Menedżera.

Aby można było użyć agenta SNMP NetX Duo z użyciem protokołu IPv6 i uzyskać obiektów IPv6, należy włączyć protokół IPv6 w NetX Duo. Szczegółowe informacje na temat włączania wystąpienia protokołu IP dla usług IPv6 można znaleźć w ***podręczniku użytkownika NetX Duo*** .

## <a name="netx-duo-snmp-constraints"></a>Ograniczenia SNMP NetX Duo

Protokół SNMP NetX Duo implementuje SNMP w wersji 1, 2 i 3. Implementacja SNMPv3 obsługuje uwierzytelnianie MD5 i SHA oraz szyfrowanie DES. Ta wersja agenta SNMP NetX Duo ma następujące ograniczenia:

1. Jeden Agent SNMP na wystąpienie NetX IP
2. Brak obsługi dla RMON
3. Komunikaty INFORM protokołu SNMP V3 nie są obsługiwane
4. Typy danych nieprzezroczystych i NSAP nie są obsługiwane
5. Adresy IPv6 są zdefiniowane jako ciągi oktetowe, a sprawdzanie formatu jest pozostawione do aplikacji.

## <a name="snmp-object-names"></a>Nazwy obiektów SNMP

Protokół SNMP jest przeznaczony do zarządzania urządzeniami w Internecie. W tym celu każde urządzenie zarządzane przez protokół SNMP ma zestaw obiektów, które są zdefiniowane przez strukturę informacji o zarządzaniu (SMI) zgodnie z definicją w dokumencie RFC 1155. Struktura jest hierarchicznym typem drzewa struktury, która wygląda następująco:

![Diagram struktury informacji o zarządzaniu.](media/image3.png)

Każdy węzeł drzewa jest obiektem. Obiekt "dod" w drzewie jest identyfikowany przez notację 1.3.6, podczas gdy obiekt "Internet" w drzewie jest identyfikowany przez notację 1.3.6.1. Wszystkie nazwy obiektów SNMP zaczynają się od notacji 1.3.6.

Menedżer SNMP używa tej notacji obiektu, aby określić obiekt na urządzeniu, który ma zostać pobrany lub ustawiony. Agent SNMP NetX Duo interpretuje takie żądania Menedżera i udostępnia mechanizmy dla aplikacji, aby wykonać żądaną operację.

## <a name="snmp-manager-requests"></a>Żądania menedżera SNMP

Protokół SNMP ma prosty mechanizm zarządzania urządzeniami. Istnieje zestaw standardowych poleceń SNMP, które są wydawane przez menedżera SNMP na urządzeniu SNMP na *porcie 161*. Poniżej przedstawiono niektóre z podstawowych poleceń Menedżera SNMP:

| SNMP — polecenie | Znaczenie                                                        |
|--------------|----------------------------------------------------------------|
| GET          | *Pobierz określony obiekt*                                       |
| GETNEXT      | *Pobierz następny obiekt logiczny po określonym IDENTYFIKATORze obiektu*      |
| GetBulk      | *Pobierz wiele obiektów logicznych po określonym IDENTYFIKATORze obiektu* |
| SET          | *Ustaw określony obiekt*                                       |

Te polecenia są zakodowane w formacie składni abstrakcyjnej (ASN. 1) i znajdują się w ładunku pakietu UDP wysyłanego przez menedżera SNMP. Agent SNMP NetX Duo przetwarza żądanie, a następnie wywołuje odpowiadającą procedurę obsługi określoną w wywołaniu ***nx_snmp_agent_create*** .

## <a name="netx-duo-snmp-agent-traps"></a>Pułapki agenta SNMP NetX Duo

Agent SNMP NetX Duo umożliwia także asynchroniczne powiadamianie menedżera SNMP o zdarzeniach. Jest to realizowane za pośrednictwem polecenia SNMP TRAP. Istnieje unikatowy interfejs API dla każdej wersji protokołu SNMP do wysyłania pułapek do menedżera SNMP. Domyślnie pułapki są wysyłane do menedżera SNMP na porcie 162.

Agent SNMP NetX Duo udostępnia oddzielne klucze zabezpieczeń dla komunikatów pułapki SNMPv3. W tym celu aplikacja SNMP musi utworzyć oddzielny zestaw kluczy od tych stosowanych do odpowiedzi na żądania Menedżera. Zabezpieczenia pułapek umożliwiają agentowi SNMP używanie tych samych lub różnych haseł na potrzeby uwierzytelniania i prywatności. Aby uzyskać więcej informacji na temat tworzenia kluczy zabezpieczeń, zobacz **NetX Duo — uwierzytelnianie i szyfrowanie SNMP** w następnej sekcji.

Lista standardowych zmiennych pułapek SNMP jest wyliczana w górnej części *nxd_snmp. h:*

| Zmienne                                 | Wartość  |
|-------------------------------------------|---|
| #define NX_SNMP_TRAP_COLDSTART            | 0 |
| #define NX_SNMP_TRAP_WARMSTART            | 1 |
| #define NX_SNMP_TRAP_LINKDOWN             | 2 |
| #define NX_SNMP_TRAP_LINKUP               | 3 |
| #define NX_SNMP_TRAP_AUTHENTICATE_FAILURE | 4 |
| #define NX_SNMP_TRAP_EGPNEIGHBORLOSS      | 5 |
| #define NX_SNMP_TRAP_ENTERPRISESPECIFIC   | 6 |

Aby uwzględnić te zmienne w komunikacie pułapki, trap_type argument wejściowy w *nx_snmp_agent_trapv2_send* (SNMPv2) lub *nx_snmp_agent_trapv3_send* (SNMPv3) jest ustawiony na wartość wyliczaną tych zmiennych. Poniżej przedstawiono przykład dla protokołu SNMPv2 do powiadamiania menedżera SNMP o zimnym zdarzeniu uruchamiania:

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

Aby uwzględnić zmienne zastrzeżone w komunikacie pułapki, trap_type argument wejściowy jest ustawiony na NX_SNMP_TRAP_CUSTOM, a argument wejściowy listy pułapek zawiera dane zastrzeżone. Należy pamiętać, że komunikat pułapki będzie zawierał jako czas systemowy (1.3.6.1.6.3.1.1.4.1.0). Poniżej przedstawiono przykład dla SNMPv2:

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a>NetX Duo — uwierzytelnianie i szyfrowanie SNMP

Istnieją dwa typy uwierzytelniania, czyli *podstawowe* i *szyfrowane*. Uwierzytelnianie podstawowe jest równoznaczne z prostym uwierzytelnianiem zwykłego *tekstu w* wielu protokołach. W podstawowym uwierzytelnianiu SNMP użytkownik po prostu weryfikuje, czy podana nazwa użytkownika jest prawidłowa do wykonywania operacji SNMP. Uwierzytelnianie podstawowe jest jedyną opcją dla SNMP w wersji 1 i 2.

Główną wadą uwierzytelniania podstawowego jest nazwa użytkownika, która jest przesyłana w postaci zwykłego tekstu. Uwierzytelnianie Digest szyfrowanego rozwiązuje ten problem przez nigdy nie przesyłaj nazwy użytkownika w postaci zwykłego tekstu. Zamiast tego algorytm jest używany do wygenerowania 96-bitowego elementu "Digest" z nazwy użytkownika, aparatu kontekstu i innych informacji. Agent SNMP NetX Duo obsługuje algorytmy szyfrowane MD5 i SHA.

Aby włączyć uwierzytelnianie, Agent SNMP musi ustawić jego identyfikator aparatu kontekstu przy użyciu usługi *nx_snmp_agent_context_engine_set* . Identyfikator aparatu kontekstu jest używany podczas tworzenia klucza uwierzytelniania.

Szyfrowanie danych SNMPv3 jest dostępne przy użyciu algorytmu DES. Szyfrowanie wymaga włączenia uwierzytelniania (jeden nie może szyfrować danych bez ustawiania parametrów uwierzytelniania).

Do utworzenia kluczy uwierzytelniania i prywatności są używane następujące interfejsy API:

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

Następnie Agent SNMP musi być skonfigurowany do korzystania z tych kluczy. Aby zarejestrować klucz za pomocą agenta SNMP, są używane następujące interfejsy API:

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

Osobne klucze można utworzyć dla komunikatów pułapki. Aby zastosować klucze dla komunikatów pułapki, dostępne są następujące interfejsy API:

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

Aby wyłączyć uwierzytelnianie lub szyfrowanie dla komunikatów odpowiedzi i wysyłania pułapek, Użyj tych usług z wartością wejściową wskaźnika klucza ustawioną na wartość NULL.

## <a name="netx-duo-snmp-community-strings"></a>NetX Duo — ciągi społeczności SNMP

Agent SNMP NetX Duo obsługuje zarówno publiczne, jak i prywatne ciągi społeczności. Ciąg publiczny jest ustawiany za pomocą usługi *_public_string_set nx_snmp_agent* . Prywatny ciąg agenta SNMP NetX Duo jest ustawiany przy użyciu usługi *nx_snmp_agent_private_string_set* .

## <a name="netx-duo-snmp-username-callback"></a>Wywołanie zwrotne SNMP nazwy użytkownika NetX Duo

Pakiet agenta SNMP NetX Duo umożliwia aplikacji określenie (za pośrednictwem wywołania ***nx_snmp_agent_create*** ) wywołania zwrotnego nazwy użytkownika, która jest wywoływana na początku obsługi poszczególnych żądań klienta SNMP.

Procedura wywołania zwrotnego zapewnia agentowi SNMP NetX Duo o nazwie użytkownika. Jeśli podana nazwa użytkownika jest prawidłowa lub w przypadku odpowiedzi na żądanie nie jest wymagane sprawdzanie nazwy użytkownika, wywołanie zwrotne nazwy użytkownika powinna zwracać wartość **NX_SUCCESS**. W przeciwnym razie procedura powinna zwracać **NX_SNMP_ERROR** , aby wskazać, że określona nazwa użytkownika jest nieprawidłowa.

Format procedury wywołania zwrotnego nazwy użytkownika aplikacji został zdefiniowany poniżej:

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr | Znaczenie                                              |
|-----------|------------------------------------------------------|
| *agent_ptr* | Wskaźnik do wywoływania agenta SNMP                        |
| nazwa użytkownika  | Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika |

W przypadku sesji SNMPv1 i SNMPv2/v2C aplikacja będzie chciała sprawdzić ciąg identyfikacyjny w przychodzącym żądaniu SNMP, aby określić, czy żądanie SNMP ma prawidłowy ciąg identyfikacyjny. Istnieje kilka usług dla aplikacji SNMP.

Aplikacja SNMP może dowiedzieć się, czy bieżące żądanie menedżera SNMP jest GET (np. GET, GetNext lub GetBulk) lub typu żądania przy użyciu tej usługi:

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

Jeśli żądanie jest typu GET, aplikacja będzie chcieć porównać wejściowy ciąg identyfikacyjny z publicznym ciągiem agenta SNMP:

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

Podobnie jeśli żądanie jest typem zestawu, aplikacja będzie chcieć porównać wejściowy ciąg identyfikacyjny z prywatnym ciągiem agenta SNMP:

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

Is_public i is_private wartości zwracane wskazują odpowiednio, jeśli wejściowy ciąg identyfikacyjny jest prawidłowym publicznym lub prywatnym ciągiem społeczności.

Zwracana wartość procedury wywołania zwrotnego username wskazuje, czy nazwa użytkownika jest prawidłowa. Wartość **NX_SUCCESS** jest zwracana, jeśli nazwa użytkownika jest prawidłowa, lub **NX_SNMP_ERROR** , jeśli nazwa użytkownika jest nieprawidłowa.

## <a name="netx-duo-snmp-agent-get-callback"></a>Wywołanie zwrotne agenta SNMP NetX Duo

Aplikacja musi ustawić procedurę wywołania zwrotnego dla obsługi żądań GET Object z menedżera SNMP. Wywołanie zwrotne Pobiera wartość obiektu określonego w żądaniu.

Procedura wywołania zwrotnego żądania GET aplikacji została zdefiniowana poniżej:

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr        | Znaczenie |
|------------------|----------------------------------|
| *agent_ptr*        | Wskaźnik do wywoływania agenta SNMP |
| object_requested | Ciąg ASCII reprezentujący identyfikator obiektu dla operacji pobierania. |
| object_data      | Struktura danych do przechowywania wartości pobranej przez wywołanie zwrotne. Można to ustawić przy użyciu serii interfejsu API SNMP NetX Duo opisanej poniżej. |

> [!NOTE]
> *W przypadku ciągów oktetowych obiekt musi mieć przypisaną długość, tak aby wewnętrzna funkcja wiedziała, jak długo długość jest równa, ponieważ wywołanie zwrotne nie ma argumentu length:*

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Ponieważ typ danych nie jest znany w wywołaniu wywołania zwrotnego, nie trzeba sprawdzać typu danych. Długość nie będzie miała wpływu na typy liczbowe ani ciągi o wartości null.

Następnie wywołaj funkcję wewnętrzną:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Jeśli funkcja wywołania zwrotnego nie może odnaleźć żądanego obiektu, należy zwrócić **NX_SNMP_ERROR_NOSUCHNAME** kod błędu. W przypadku wykrycia innego błędu należy zwrócić **NX_SNMP_ERROR** .

## <a name="netx-duo-snmp-agent-getnext-callback"></a>NetX Duo — Agent SNMP-następne wywołanie zwrotne

Aplikacja musi również ustawić procedurę wywołania zwrotnego dla żądań GetNext obiektu z menedżera SNMP. To wywołanie zwrotne GetNext Pobiera wartość następnego obiektu określonego przez żądanie.

Procedura wywołania zwrotnego żądania aplikacji GetNext została zdefiniowana poniżej:

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr        | Znaczenie |
|------------------|-------------------------------------------|
| *agent_ptr*        | Wskaźnik do wywoływania agenta SNMP |
| object_requested | Ciąg ASCII reprezentujący identyfikator obiektu dla operacji GetNext. |
| object_data      | Struktura danych do przechowywania wartości pobranej przez wywołanie zwrotne. Można to ustawić przy użyciu serii interfejsu API SNMP NetX Duo opisanej poniżej. |

Analogicznie jak ma wartość true w przypadku wywołań zwrotnych, obiekty z danymi ciągu oktetowego muszą mieć przypisaną długość, tak aby wewnętrzna funkcja wiedziała, jak długo długość jest równa, ponieważ wywołanie zwrotne nie ma argumentu długości:

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Ponieważ typ danych nie jest znany w wywołaniu wywołania zwrotnego, nie trzeba sprawdzać typu danych. Długość nie będzie miała wpływu na typy liczbowe ani ciągi o wartości null.

Następnie wywołaj funkcję wewnętrzną:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Jeśli funkcja wywołania zwrotnego nie może odnaleźć żądanego obiektu, należy zwrócić **NX_SNMP_ERROR_NOSUCHNAME** kod błędu. W przypadku wykrycia innego błędu należy zwrócić **NX_SNMP_ERROR** .

## <a name="netx-duo-snmp-agent-set-callback"></a>Wywołanie zwrotne agenta SNMP zestawu NetX Duo

Aplikacja powinna ustawić procedurę wywołania zwrotnego dla obsługi żądań SET obiektu z menedżera SNMP. Ustawianie wywołania zwrotnego ustawia wartość obiektu określonego przez żądanie.

Procedura wywołania zwrotnego żądania zestawu aplikacji jest definiowana poniżej:

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr        | Znaczenie |
|------------------|-------- |
| *agent_ptr*      | Wskaźnik do wywoływania agenta SNMP |
| object_requested | Ciąg ASCII reprezentujący identyfikator obiektu dla operacji zestawu. |
| object_data      | Struktura danych, która zawiera nową wartość dla określonego obiektu. Rzeczywistą operację można wykonać przy użyciu interfejsu API protokołu SNMP NetX Duo opisanej poniżej. |

Należy pamiętać, że w przypadku ciągów oktetowych Ustaw wywołanie zwrotne powinno zaktualizować tabelę MIB o długość danych, ponieważ Agent SNMP przeanalizuje dane i zna typ i Długość:

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

Jeśli funkcja wywołania zwrotnego nie może odnaleźć żądanego obiektu, należy zwrócić **NX_SNMP_ERROR_NOSUCHNAME** kod błędu.

Jeśli host SNMP NetX Duo utworzył prywatne ciągi społecznościowe, a nadawca protokołu SNMP dla żądania SET nie ma pasującego ciągu prywatnego, może zwrócić błąd **NX_SNMP_ERROR_NOACCESS** . W przypadku wykrycia innego błędu należy zwrócić **NX_SNMP_ERROR** .

> [!NOTE]
> *Mimo że Agent SNMP NetX Duo dostarcza bazę danych SNMP MIB z dystrybucją, jest ona głównie do testowania i programowania. Deweloper będzie prawdopodobnie wymagał zastrzeżonej bazy danych MIB dla profesjonalnej aplikacji SNMP.*

## <a name="changing-snmp-version-at-run-time"></a>Zmiana wersji SNMP w czasie wykonywania

Host agenta SNMP może zmienić wersję protokołu SNMP dla każdej z trzech wersji w czasie wykonywania za pomocą usługi *nx_snmp_agent_set_version* . Agent SNMP jest domyślnie włączony dla wszystkich trzech wersji, gdy zostanie utworzony Agent SNMP w *nx_snmp_agent_create*. Jednak aplikacja może ograniczyć to podzbiór wszystkich wersji.

> [!NOTE]
> *W przypadku zdefiniowania opcji konfiguracji NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 i/lub NX_SNMP_DISABLE_V3 ta funkcja nie będzie miała wpływu na to, że te wersje nie zostaną zastosowane.*

Agent SNMP może pobrać wersję SNMP najnowszego pakietu SNMP otrzymanego przy użyciu usługi *nx_snmp_agent_get_current_version* .

## <a name="snmpv3-discovery"></a>Odnajdywanie SNMPv3

Agent SNMP, jeśli jest włączony dla SNMPv3, będzie odpowiadać na żądania odnajdywania od menedżera SNMP. Takie żądanie zawiera dane parametrów zabezpieczeń z wartościami null dla identyfikatora aparatu autorytatywnego, nazwy użytkownika, liczby rozruchowej i czasu rozruchu. Parametry uwierzytelniania nie są stosowane do komunikatu ODNAJDOWAnia. Lista powiązań zmiennych w żądaniu jest pusta (zawiera zerowe elementy). Agent SNMP reaguje na zero czasu i liczby rozruchów oraz listę powiązań zmiennych zawierającą 1 element, *usmStatsUnknownEngineIDs*, czyli liczbę żądań odebranych z nieznanym (null) identyfikatorem aparatu. Na kolejne żądanie GetNext z przeglądarki/Menedżera, dane rozruchowe i parametry zabezpieczeń są wypełniane tylko wtedy, gdy włączono zabezpieczenia. W takim przypadku wyśle także NotInTimeą aktualizację danych w jednostce PDU. Parametry zabezpieczeń, np. uwierzytelnianie udowadniają tożsamość agenta dla Menedżera.

Bardziej szczegółowe informacje na temat uwierzytelniania SNMPv3 są dostępne w dokumencie RFC 3414 "model zabezpieczeń oparty na użytkownikach (USM) dla wersji 3 Simple Network Management Protocol (SNMPv3)".

## <a name="netx-duo-snmp-rfcs"></a>NetX Duo — specyfikacje RFC protokołu SNMP

NetX Duo SNMP jest zgodne z RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575,, RFC 3414 i powiązane z nimi specyfikacje RFC.
