---
title: Rozdział 1 — wprowadzenie do Azure RTOS NetX Duo SNMP
description: Implementacja NetX Duo SNMP jest implementacją agenta SNMP. Agent jest odpowiedzialny za odpowiadanie na polecenia menedżera SNMP i wysyłanie pułapek sterowanych zdarzeniami.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bf18efacc5ff7773e038a5140fc886e978ebd1ca59cc9b861139b3ce2d9ada6
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797872"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a>Rozdział 1 — wprowadzenie do Azure RTOS NetX Duo SNMP

Protokół Simple Network Management Protocol (SNMP) to protokół przeznaczony do zarządzania urządzeniami w Internecie. SNMP to protokół, który wykorzystuje usługi UDP (Connectionless User Datagram Protocol) do wykonywania funkcji zarządzania. Implementacja Azure RTOS SNMP NetX Duo jest implementacją agenta SNMP. Agent jest odpowiedzialny za odpowiadanie na polecenia menedżera SNMP i wysyłanie pułapek sterowanych zdarzeniami. 

Protokół NetX Duo SNMP obsługuje komunikację zarówno Z menedżerami SNMP, jak i IPv4 i IPv6. Aplikacje NetX SNMP powinny być kompilowane i uruchamiane w NetX Duo SNMP. Zachęcamy jednak dewelopera do przenoszenia istniejących aplikacji SNMP do korzystania z równoważnych usług "duetu". Na przykład podczas wysyłania komunikatów pułapek SNMP następujące usługi "duo" powinny zastąpić ich odpowiedniki NetX:

*nxd_snmp_object_trap_send*

*nxd_snmp_object_trapv2_send*

*nxd_snmp_object_trapv3_send*

Aby uzyskać więcej informacji, zobacz **Opis usług agenta SNMP** w innym miejscu tego podręcznika użytkownika.

## <a name="netx-duo-snmp-agent-requirements"></a>Wymagania dotyczące agenta SNMP NetX Duo

Pakiet NetX Duo SNMP wymaga, aby wystąpienie adresu IP zostało już utworzone. Ponadto protokół UDP musi być włączony w tym samym wystąpieniu adresu IP.

Agent NetX Duo SNMP ma kilka dodatkowych wymagań. Najpierw wymaga dostępu do portu 161 w celu obsługi wszystkich żądań menedżera SNMP. Wymaga również dostępu do portu 162 w celu wysyłania komunikatów pułapek do menedżera.

Aby używać agenta NetX Duo SNMP z użyciem protokołu IPv6 i uzyskiwać obiekty IPv6, należy włączyć protokół IPv6 w programie NetX Duo. Aby uzyskać szczegółowe informacje na temat włączania wystąpienia adresu IP dla usług IPv6, zobacz NetX Duo User Guide (Podręcznik użytkownika ***netX Duo).***

## <a name="netx-duo-snmp-constraints"></a>Ograniczenia NETX Duo SNMP

Protokół NetX Duo SNMP implementuje snmp w wersji 1, 2 i 3. Implementacja SNMPv3 obsługuje uwierzytelnianie MD5 i SHA oraz szyfrowanie DES. Ta wersja agenta NetX Duo SNMP ma następujące ograniczenia:

1. Jeden agent SNMP na wystąpienie ip NetX
2. Brak obsługi RMON
3. Komunikaty z komunikatami informacyjmi SNMP v3 nie są obsługiwane
4. Typy danych NIEPRZEZROCZYSTE i NSAP nie są obsługiwane
5. Adresy IPv6 są zdefiniowane jako ciągi oktetowe, a sprawdzanie formatu jest pozostawiane aplikacji.

## <a name="snmp-object-names"></a>Nazwy obiektów SNMP

Protokół SNMP jest przeznaczony do zarządzania urządzeniami w Internecie. W tym celu każde urządzenie zarządzane przez protokół SNMP ma zestaw obiektów zdefiniowanych przez strukturę informacji zarządzania (SMI, Structure of Management Information) zdefiniowaną w dokumencie RFC 1155. Struktura jest hierarchicznym typem drzewa struktury, który wygląda następująco:

![Diagram struktury informacji o zarządzaniu.](media/image3.png)

Każdy węzeł w drzewie jest obiektem. Obiekt "dod" w drzewie jest identyfikowany przez notację 1.3.6, a obiekt "Internet" w drzewie jest identyfikowany za pomocą notacji 1.3.6.1. Wszystkie nazwy obiektów SNMP zaczynają się od notacji 1.3.6.

Menedżer SNMP używa tej notacji obiektu do określenia obiektu w urządzeniu, które ma pobrać lub ustawić. Agent SNMP NetX Duo interpretuje takie żądania menedżera i udostępnia mechanizmy, za które aplikacja może wykonać żądaną operację.

## <a name="snmp-manager-requests"></a>Żądania menedżera SNMP

Protokół SNMP ma prosty mechanizm zarządzania urządzeniami. Istnieje zestaw standardowych poleceń SNMP, które są wydawane przez Menedżera SNMP dla urządzenia SNMP na *porcie 161.* Poniżej przedstawiono niektóre z podstawowych poleceń menedżera SNMP:

| SnMP, polecenie | Znaczenie                                                        |
|--------------|----------------------------------------------------------------|
| GET          | *Pobierz określony obiekt*                                       |
| Getnext      | *Pobierz następny obiekt logiczny po określonym identyfikatorze obiektu*      |
| GETBULK      | *Pobierz wiele obiektów logicznych po określonym identyfikatorze obiektu* |
| SET          | *Ustawianie określonego obiektu*                                       |

Te polecenia są kodowane w formacie Abstract Syntax Notation One (ASN.1) i znajdują się w ładunku pakietu UDP wysyłanego przez menedżera SNMP. Agent SNMP NetX Duo przetwarza żądanie, a następnie wywołuje odpowiednią procedurę obsługi określoną w ***wywołaniu nx_snmp_agent_create*** żądania.

## <a name="netx-duo-snmp-agent-traps"></a>Pułapki agentów SNMP NetX Duo

Agent SNMP NetX Duo umożliwia również asynchroniczne powiadamianie menedżera SNMP o zdarzeniach. Odbywa się to za pomocą polecenia pułapki SNMP. Dla każdej wersji snmp jest unikatowy interfejs API do wysyłania pułapek do menedżera SNMP. Domyślnie pułapki są wysyłane do Menedżera SNMP na porcie 162.

Agent SNMP NetX Duo udostępnia oddzielne klucze zabezpieczeń dla komunikatów pułapek SNMPv3. W tym celu aplikacja SNMP musi utworzyć oddzielny zestaw kluczy od tych, które są stosowane do odpowiedzi na żądania menedżera. Zabezpieczenia pułapek umożliwiają agentowi SNMP używanie tych samych lub różnych haseł do uwierzytelniania i ochrony prywatności. Aby uzyskać więcej informacji na temat tworzenia kluczy zabezpieczeń, zobacz **NetX Duo SNMP Authentication and Encryption (Uwierzytelnianie i szyfrowanie SNMP netX Duo)** w następnej sekcji.

Lista standardowych zmiennych pułapek SNMP jest wyliczana w górnej *części nxd_snmp.h:*

| Zmienne                                 | Wartość  |
|-------------------------------------------|---|
| #define NX_SNMP_TRAP_COLDSTART            | 0 |
| #define NX_SNMP_TRAP_WARMSTART            | 1 |
| #define NX_SNMP_TRAP_LINKDOWN             | 2 |
| #define NX_SNMP_TRAP_LINKUP               | 3 |
| #define NX_SNMP_TRAP_AUTHENTICATE_FAILURE | 4 |
| #define NX_SNMP_TRAP_EGPNEIGHBORLOSS      | 5 |
| #define NX_SNMP_TRAP_ENTERPRISESPECIFIC   | 6 |

Aby uwzględnić te zmienne w komunikacie pułapki, argument wejściowy usługi trap_type w adresie *nx_snmp_agent_trapv2_send* (SNMPv2) lub *nx_snmp_agent_trapv3_send* (SNMPv3) jest ustawiony na wyliczoną wartość tych zmiennych. Poniżej przedstawiono przykład dla protokołu SNMPv2 w celu powiadamiania Menedżera SNMP o zdarzeniu zimnym startu:

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

Aby uwzględnić zastrzeżone zmienne w komunikacie pułapki, argument wejściowy trap_type jest ustawiony na wartość NX_SNMP_TRAP_CUSTOM, a argument wejściowy listy pułapek zawiera zastrzeżone dane. Należy pamiętać, że komunikat pułapki będzie zawierać jako czas pracy systemu (1.3.6.1.6.3.1.1.4.1.0). Poniżej przedstawiono przykład dla protokołu SNMPv2:

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

## <a name="netx-duo-snmp-authentication-and-encryption"></a>NetX Duo SNMP Authentication and Encryption

Istnieją dwa rodzaje uwierzytelniania: *podstawowy i* *skrótowy*. Uwierzytelnianie podstawowe jest odpowiednikiem prostego uwierzytelniania za pomocą nazwy *użytkownika w* postaci zwykłego tekstu, które można znaleźć w wielu protokołach. W przypadku uwierzytelniania podstawowego SNMP użytkownik po prostu sprawdza, czy podana nazwa użytkownika jest prawidłowa do wykonywania operacji SNMP. Uwierzytelnianie podstawowe jest jedyną opcją w przypadku protokołu SNMP w wersji 1 i 2.

Główną wadą uwierzytelniania podstawowego jest to, że nazwa użytkownika jest przesyłana w postaci zwykłego tekstu. Uwierzytelnianie szyfrowane SNMPv3 rozwiązuje ten problem, nigdy nie przesyłając nazwy użytkownika w postaci zwykłego tekstu. Zamiast tego algorytm jest używany do wyprowadzenia 96-bitowego "skrótu" z nazwy użytkownika, aparatu kontekstu i innych informacji. Agent NetX Duo SNMP obsługuje algorytmy skrótu MD5 i SHA.

Aby włączyć uwierzytelnianie, agent SNMP musi ustawić swój identyfikator aparatu kontekstu przy użyciu *nx_snmp_agent_context_engine_set* usługi. Identyfikator aparatu kontekstu jest używany podczas tworzenia klucza uwierzytelniania.

Szyfrowanie danych SNMPv3 jest dostępne przy użyciu algorytmu DES. Szyfrowanie wymaga włączonego uwierzytelniania (nie można zaszyfrować danych bez ustawienia parametrów uwierzytelniania).

Aby utworzyć klucze uwierzytelniania i ochrony prywatności, używane są następujące interfejsy API:

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

Następnie należy skonfigurować agenta SNMP do używania tych kluczy. Aby zarejestrować klucz przy użyciu agenta SNMP, używany jest następujący interfejs API:

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

Dla komunikatów pułapek można tworzyć oddzielne klucze. Aby zastosować klucze dla komunikatów pułapek, dostępny jest następujący interfejs API:

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

Aby wyłączyć uwierzytelnianie lub szyfrowanie komunikatów odpowiedzi i wysyłania pułapek, użyj tych usług z wejściowym wskaźnikiem klucza ustawionym na wartość NULL.

## <a name="netx-duo-snmp-community-strings"></a>Ciągi Community SNMP NetX Duo

Agent NetX Duo SNMP obsługuje zarówno publiczne, jak i prywatne ciągi społeczności. Ciąg publiczny jest ustawiany za pomocą *nx_snmp_agent _public_string_set* service. Prywatny ciąg agenta SNMP NetX Duo jest ustawiany przy użyciu *nx_snmp_agent_private_string_set* service.

## <a name="netx-duo-snmp-username-callback"></a>Wywołanie zwrotne nazwy użytkownika SNMP NetX Duo

Pakiet agenta SNMP NetX Duo umożliwia aplikacji określenie (za pośrednictwem wywołania ***nx_snmp_agent_create)*** wywołania zwrotnego nazwy użytkownika wywoływanego na początku obsługi każdego żądania klienta SNMP.

Procedura wywołania zwrotnego udostępnia agentowi SNMP NetX Duo nazwę użytkownika. Jeśli podana nazwa użytkownika jest prawidłowa lub jeśli nie jest wymagane sprawdzenie nazwy użytkownika w celu odpowiedzi na **żądanie,** wywołanie zwrotne nazwy użytkownika powinno zwrócić wartość NX_SUCCESS . W przeciwnym razie procedura powinna **zwrócić** NX_SNMP_ERROR, aby wskazać, że określona nazwa użytkownika jest nieprawidłowa.

Format procedury wywołania zwrotnego nazwy użytkownika aplikacji jest zdefiniowany poniżej:

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr | Znaczenie                                              |
|-----------|------------------------------------------------------|
| *agent_ptr* | Wskaźnik do wywoływania agenta SNMP                        |
| nazwa użytkownika  | Miejsce docelowe wskaźnika do wymaganej nazwy użytkownika |

W przypadku sesji SNMPv1 i SNMPv2/v2C aplikacja będzie chcieć sprawdzić ciąg społeczności w przychodzącym żądaniu SNMP, aby określić, czy żądanie SNMP ma prawidłowy ciąg społeczności. Aplikacja SNMP może to zrobić w kilku usługach.

Aplikacja SNMP może sprawdzić, czy bieżące żądanie menedżera SNMP jest żądaniem GET (np. GET, GETNEXT lub GETBULK) lub typem ZESTAWU żądania przy użyciu tej usługi:

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

Jeśli żądanie jest typem GET, aplikacja będzie chciała porównać wejściowy ciąg społeczności z ciągiem publicznym agenta SNMP:

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

Podobnie jeśli żądanie ma typ SET, aplikacja będzie chciała porównać wejściowy ciąg społeczności z ciągiem prywatnym agenta SNMP:

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

Wartości is_public i is_private wskazują odpowiednio, czy wejściowy ciąg społeczności jest prawidłowym publicznym, czy prywatnym ciągiem społeczności.

Wartość zwracana przez procedurę wywołania zwrotnego nazwy użytkownika wskazuje, czy nazwa użytkownika jest prawidłowa. Wartość jest **NX_SUCCESS** zwracana, jeśli nazwa użytkownika jest prawidłowa, lub **NX_SNMP_ERROR,** jeśli nazwa użytkownika jest nieprawidłowa.

## <a name="netx-duo-snmp-agent-get-callback"></a>NetX Duo SNMP Agent GET Callback

Aplikacja musi ustawić procedurę wywołania zwrotnego do obsługi żądań obiektów GET z menedżera SNMP. Wywołanie zwrotne pobiera wartość obiektu określonego w żądaniu.

Poniżej zdefiniowano procedurę wywołania zwrotnego żądania GET aplikacji:

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr        | Znaczenie |
|------------------|----------------------------------|
| *agent_ptr*        | Wskaźnik do wywoływania agenta SNMP |
| object_requested | Ciąg ASCII reprezentujący identyfikator obiektu dla operacji GET. |
| object_data      | Struktura danych do przechowywania wartości pobranej przez wywołanie zwrotne. Można to ustawić za pomocą serii interfejsów API SNMP NetX Duo opisanych poniżej. |

> [!NOTE]
> *W przypadku ciągów oktetowych obiektowi należy przypisać długość, aby funkcja wewnętrzna wiedziała, jak długo jest długość, ponieważ samo wywołanie zwrotne nie ma argumentu length:*

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Ponieważ typ danych nie jest znany wywołaniu zwrotnego GET, nie ma potrzeby sprawdzania typu danych. Długość nie będzie mieć żadnego wpływu na typy liczbowe lub ciągi, które są rozdzielane wartością null.

Następnie wywołaj funkcję wewnętrzną:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Jeśli funkcja wywołania zwrotnego nie może znaleźć żądanego obiektu, **NX_SNMP_ERROR_NOSUCHNAME** powinien zostać zwrócony kod błędu. Jeśli zostanie wykryty inny błąd, **NX_SNMP_ERROR** powinna zostać zwrócona.

## <a name="netx-duo-snmp-agent-getnext-callback"></a>NetX Duo SNMP Agent GETNEXT Callback

Aplikacja musi również ustawić procedurę wywołania zwrotnego dla żądań obiektu GETNEXT z menedżera SNMP. Wywołanie zwrotne GETNEXT pobiera wartość następnego obiektu określonego przez żądanie.

Poniżej zdefiniowano procedurę wywołania zwrotnego żądania GETNEXT aplikacji:

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr        | Znaczenie |
|------------------|-------------------------------------------|
| *agent_ptr*        | Wskaźnik do wywoływania agenta SNMP |
| object_requested | Ciąg ASCII reprezentujący identyfikator obiektu dla operacji GETNEXT. |
| object_data      | Struktura danych do przechowywania wartości pobranej przez wywołanie zwrotne. Można to ustawić za pomocą serii interfejsów API SNMP NetX Duo opisanych poniżej. |

Podobnie jak w przypadku wywołań zwrotnych GET, obiekty z ciągiem oktetowym muszą mieć przypisaną długość, aby funkcja wewnętrzna wiedziała, jak długo jest długość, ponieważ samo wywołanie zwrotne nie ma argumentu length:

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

Ponieważ typ danych nie jest znany wywołaniu zwrotnego GET, nie ma potrzeby sprawdzania typu danych. Długość nie będzie mieć żadnego wpływu na typy liczbowe lub ciągi, które są rozdzielane wartością null.

Następnie wywołaj funkcję wewnętrzną:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

Jeśli funkcja wywołania zwrotnego nie może znaleźć żądanego obiektu, **NX_SNMP_ERROR_NOSUCHNAME** powinien zostać zwrócony kod błędu. Jeśli zostanie wykryty inny błąd, **NX_SNMP_ERROR** powinna zostać zwrócona.

## <a name="netx-duo-snmp-agent-set-callback"></a>Wywołanie zwrotne SET agenta SNMP NetX Duo

Aplikacja powinna ustawić procedurę wywołania zwrotnego do obsługi żądań obiektu SET z menedżera SNMP. Wywołanie zwrotne SET ustawia wartość obiektu określonego przez żądanie.

Poniżej zdefiniowano procedurę wywołania zwrotnego żądania SET aplikacji:

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

Parametry wejściowe są zdefiniowane w następujący sposób:

| Parametr        | Znaczenie |
|------------------|-------- |
| *agent_ptr*      | Wskaźnik do wywoływania agenta SNMP |
| object_requested | Ciąg ASCII reprezentujący identyfikator obiektu dla operacji SET. |
| object_data      | Struktura danych zawierająca nową wartość dla określonego obiektu. Rzeczywistą operację można wykonać przy użyciu interfejsu API SNMP NetX Duo opisanego poniżej. |

Należy pamiętać, że w przypadku ciągów oktetowych wywołanie zwrotne SET powinno zaktualizować tabelę MIB o długość danych, ponieważ agent SNMP przejmuje dane oraz zna typ i długość:

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

Jeśli funkcja wywołania zwrotnego nie może znaleźć żądanego obiektu, **NX_SNMP_ERROR_NOSUCHNAME** powinien zostać zwrócony kod błędu.

Jeśli host NetX Duo SNMP utworzył prywatne ciągi społeczności, a nadawca SNMP żądania SET nie ma pasującego ciągu prywatnego, może zostać zwrócony NX_SNMP_ERROR_NOACCESS **błąd.** Jeśli zostanie wykryty inny błąd, **NX_SNMP_ERROR** powinna zostać zwrócona.

> [!NOTE]
> *Mimo że agent NetX Duo SNMP dostarcza bazę danych SNMP MIB z dystrybucją, jest głównie przeznaczony do celów testowania i testowania. Deweloper będzie prawdopodobnie wymagał własnościowej bazy danych MIB dla profesjonalnej aplikacji SNMP.*

## <a name="changing-snmp-version-at-run-time"></a>Zmiana wersji SNMP w czasie uruchamiania

Host agenta SNMP może zmienić wersję SNMP dla każdej z trzech wersji w czasie uruchamiania przy *użyciu nx_snmp_agent_set_version* usługi. Agent SNMP jest domyślnie włączony dla wszystkich trzech wersji po utworzeniu agenta SNMP w *programie nx_snmp_agent_create*. Jednak aplikacja może ograniczyć ją do podzestawu wszystkich wersji.

> [!NOTE]
> *Jeśli opcje konfiguracji NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 i/lub NX_SNMP_DISABLE_V3, ta funkcja nie będzie mieć wpływu na włączanie wersji, których dotyczy problem.*

Agent SNMP może pobrać wersję SNMP najnowszego pakietu SNMP odebranego przy użyciu *nx_snmp_agent_get_current_version* sieci.

## <a name="snmpv3-discovery"></a>Odnajdywanie SNMPv3

Agent SNMP, jeśli jest włączony dla protokołu SNMPv3, będzie odpowiadać na żądania odnajdywania z Menedżera SNMP. Takie żądanie zawiera dane parametrów zabezpieczeń z wartościami null dla identyfikatora aparatu autorytatywnego, nazwy użytkownika, liczby rozruchu i czasu rozruchu. Parametry uwierzytelniania nie są stosowane do komunikatu ODNAJDYWANIE. Lista powiązań zmiennych w żądaniu jest pusta (zawiera zero elementów). Agent SNMP odpowiada zerowym czasem rozruchu i zliczaną wartością oraz listą powiązań zmiennych zawierającą 1 element *usmStatsUnknownEngineIDs,* czyli liczbę żądań odebranych z nieznanym identyfikatorem aparatu (null). W kolejnym żądaniu GETNEXT z przeglądarki/menedżera dane rozruchu i parametry zabezpieczeń są wypełniane tylko wtedy, gdy zabezpieczenia są włączone. Jeśli tak, spowoduje to również wysłanie aktualizacji danych NotInTime w pdu. Parametry zabezpieczeń, np. uwierzytelnianie, udowadniają tożsamość agenta menedżerowi.

Bardziej szczegółowe informacje na temat uwierzytelniania SNMPv3 są dostępne w dokumencie RFC 3414 "User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)".

## <a name="netx-duo-snmp-rfcs"></a>NetX Duo SNMP RFC

NetX Duo SNMP jest zgodny ze standardami RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 i powiązanymi ZFC.
