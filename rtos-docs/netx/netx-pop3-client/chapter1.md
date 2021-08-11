---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX POP3 Client
description: Interfejs API Azure RTOS POP3 platformy NetX udostępnia system transportu poczty dla małych stacji roboczych w celu uzyskiwania dostępu do poczty klienta na serwerach POP3 w celu pobierania poczty klienta.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6abaa778da6203d0df367894165cb29ca629ab5e24403a35af1995f032cf0d4c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798813"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX POP3 Client

Post Office Protocol w wersji 3 (POP3) to protokół zaprojektowany w celu zapewnienia systemu transportu poczty dla małych stacji roboczych do uzyskiwania dostępu do poczty klienta na serwerach POP3 do pobierania poczty klienta. Pop3 wykorzystuje usługi Transmission Control Protocol (TCP) do wykonywania transferu poczty e-mail. W związku z tym POP3 to wysoce niezawodny protokół transferu zawartości.

Jednak pop3 nie zapewnia rozbudowanych operacji obsługi poczty e-mail. Zazwyczaj poczta jest pobierana przez klienta, a następnie usuwana z usługi maildrop serwera.

## <a name="netx-pop3-client-requirements"></a>NetX POP3 Client Requirements

### <a name="client-requirements"></a>Wymagania dotyczące klienta

Interfejs API Azure RTOS POP3 NetX wymaga utworzonego wcześniej wystąpienia adresu IP NetX przy użyciu programu *nx_ip_create* i utworzonej wcześniej puli pakietów NetX przy użyciu nx_packet_pool_create *.* Ponieważ klient NetX POP3 korzysta z usług TCP, protokół TCP musi być włączony przy użyciu *wywołania nx_tcp_enable* przed użyciem usług klienta NETX POP3 w tym samym wystąpieniu adresu IP. Klient POP3 używa gniazda TCP do nawiązywania połączenia z serwerem POP3 na porcie POP3 serwera. Zwykle jest on ustawiany na dobrze znanym *porcie 110,* chociaż do korzystania z tego portu nie jest wymagany ani klient POP3, ani serwer.

Rozmiar puli pakietów używanej do tworzenia klienta POP3 jest konfigurowalny przez użytkownika pod względem ładunku pakietów i liczby dostępnych pakietów. Jeśli pakiet jest używany tylko w usłudze tworzenia klienta POP3, ładunek pakietu nie musi być większy niż 100–120 bajtów w zależności od długości nazwy użytkownika i hasła lub skrótu APOP. Polecenie USER z nazwą użytkownika hosta lokalnego jest prawdopodobnie największym komunikatem wysyłanym przez klienta POP3. Istnieje możliwość współużytkowania tej samej puli pakietów w puli pakietów nx_ip_create (domyślna pula pakietów IP), ponieważ operacje wewnętrzne ip nie wymagają bardzo dużego ładunku pakietu do wysyłania i odbierania danych sterujących TCP.

Jednak użycie tej samej puli pakietów co pula pakietów klienta POP3 przez sterownik sieciowy może nie być korzystne. Ogólnie rzecz biorąc, ładunek puli pakietów odbioru jest ustawiany na jednostkę MTU wystąpienia adresu IP (zwykle 1500 bajtów) interfejsu sieciowego, który jest znacznie większy niż komunikaty klienta POP3. Przychodzące komunikaty POP3 byłyby zwykle znacznie większe niż wychodzące komunikaty klienta POP3

## <a name="netx-pop3-client-creation"></a>Tworzenie klienta NETX POP3

Usługa tworzenia klienta POP3 *nx_pop3_client_create* gniazda TCP i nawiązywanie połączenia z serwerem POP3.

Po nałączeniu się z serwerem POP3 aplikacja  klienta POP3 może wywołać nx_pop3_client _mail_items_get, aby uzyskać liczbę elementów poczty e-mail, które są w jego polu poczty:

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

Jeśli co najmniej jeden element jest w maildrop klienta, aplikacja może uzyskać rozmiar określonego elementu poczty przy użyciu *nx_pop3_client_get_mail_item* mail:

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

Pierwszy element poczty w maildrop znajduje się w indeksie 1.

Aby uzyskać rzeczywistą wiadomość e-mail, aplikacja może wywołać usługę *nx_pop3_client_mail_item_get_message_data* w celu pobrania pakietów wiadomości e-mail, dopóki usługa nie wskaże, że ostatni pakiet został odebrany przez argument final_packet wejściowego:

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

Aby usunąć określony element poczty,  aplikacja wywołuje nx_pop3_client_mail_item_delete z takim samym indeksem, jak w poprzednim *wywołaniu nx_pop3_client_get_mail_item* mail.

Klienta można usunąć za pomocą *usługi nx_pop3_client_delete* service. Należy pamiętać, że aplikacja musi usunąć pulę pakietów klienta POP3 przy użyciu usługi *nx_packet_pool_delete,* która nie jest już do jej używania.

## <a name="netx-pop3-client-constraints"></a>NetX POP3 Client Constraints

Implementacja klienta NetX POP3 ma pewne ograniczenia:

1. Klient NETX POP3 nie obsługuje polecenia AUTH, mimo że implementuje uwierzytelnianie APOP przy użyciu protokołu DIGEST-MD5 do wymiany uwierzytelniania serwera klienta.

1. Klient NETX POP3 nie implementuje wszystkich poleceń POP3 (np. poleceń TOP lub UIDL). Poniżej znajduje się lista poleceń, które obsługuje:
   - Noop
   - Zestaw RSET

## <a name="netx-pop3-client-login"></a>Logowanie klienta NetX POP3

Klient NETX POP3 musi uwierzytelnić się (zalogować) na serwerze POP3, aby uzyskać dostęp do usługi maildrop. Można to zrobić za pomocą poleceń USER/PASS oraz podać nazwę użytkownika i hasło znane serwerowi POP3 lub przy użyciu polecenia APOP i skrótu MD5 opisanego poniżej.

Nazwa użytkownika jest zazwyczaj w pełni kwalifikowaną nazwą domeny (zawiera część lokalną i nazwę domeny oddzieloną znakiem "@"). W przypadku korzystania z poleceń POP3 USER i PASS klient wysyła swoją nazwę użytkownika i hasło niezaszyfrowane przez Internet.

Aby uniknąć ryzyka związanego z bezpieczeństwem związanego z nazwą użytkownika i hasłem w tekście, można skonfigurować klienta POP3 netx do korzystania z uwierzytelniania APOP, ustawiając parametr *APOP_authentication* w *usłudze nx_pop3_client_create* service:

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

Lub tylko dla aplikacji protokołu IPv4 usługa *nx_pop3_client_create* usługi:

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

Gdy klient wysyła polecenie APOP, przyjmuje skrót MD5 zawierający domenę serwera, identyfikator czasu lokalnego i procesu wyodrębniony z powitania serwera oraz hasło klienta. Serwer POP3 utworzy skrót MD5 zawierający te same informacje, a jeśli jego skrót MD5 jest taki sam jak skrót MD5 klienta, klient jest uwierzytelniany.

Jeśli uwierzytelnianie APOP nie powiedzie się, klient NETX POP3 podejmie próbę uwierzytelnienia USER/PASS.

## <a name="the-pop3-client-maildrop"></a>The POP3 Client Maildrop

Poczta klienta jest przechowywana na serwerze POP3 w skrzynce pocztowej lub "maildrop". Poczta klienta na serwerze POP3 jest reprezentowana jako lista elementów poczty oparta na 1. Oznacza to, że każda poczta jest określana przez jej indeks na liście maildrop z pierwszym elementem poczty o indeksie 1 (a nie zeru). Polecenia POP3 odwołują się do określonych elementów poczty według indeksu na tej liście.

## <a name="the-pop3-protocol-state-machine"></a>Komputer stanu protokołu POP3

Protokół POP3 wymaga, aby klient i serwer zachowywały stan sesji POP3. Najpierw klient próbuje nawiązać połączenie z serwerem POP3. W przypadku powodzenia wprowadza on protokół POP3, który ma trzy odrębne stany zdefiniowane przez RFC 1939. Stan początkowy to stan autoryzacji, w którym musi się identyfikować z serwerem. W stanie autoryzacji klient POP3 może wystawiać tylko polecenia USER i PASS oraz w tej kolejności lub polecenie APOP.

Po uwierzytelnieniu klienta POP3 sesja klienta przechodzi w stan Transakcja. W tym stanie klient może pobrać wiadomość e-mail i zażądać jej usunięcia. Polecenia dozwolone w stanie Transakcji to LIST, STAT, RETR, DELE, RSET i QUIT. Zazwyczaj klient POP3 wysyła polecenie STAT, po którym następuje szereg poleceń RETR (po jednym dla każdego elementu poczty w jego maildrop).

Gdy klient wydaje polecenie QUIT, sesja POP3 przechodzi w stan aktualizacji, w którym inicjuje rozłączenie TCP z serwerem. Aby później pobrać wiadomość e-mail, aplikacja klienta POP3 może w dowolnym momencie wywołać usługę w celu sprawdzenia, czy w wiadomości e-mail nie ma nowej `nx_pop3_client_mail_items_get` wiadomości e-mail.

### <a name="pop3-server-reply-codes"></a>Kody odpowiedzi serwera POP3

- **+OK:** serwer używa tej odpowiedzi do akceptowania polecenia klienta. Serwer może zawierać dodatkowe informacje po przycisku "+OK", ale nie może założyć, że klient będzie przetwarzał te informacje, z wyjątkiem pobierania danych wiadomości e-mail lub poleceń LIST lub DELE. W drugim przypadku "argument" po poleceniu odwołuje się do indeksu elementu poczty w ropie maildrop klienta.

- **-ERR:** serwer używa tej odpowiedzi do odrzucania klienta polecenia. Serwer może wysłać dodatkowe informacje po błędzie "-ERR", ale nie może założyć, że klient będzie przetwarzał te informacje.

### <a name="sample-pop3-client---server-session"></a>Przykładowy klient POP3 — sesja serwera

**Podstawowy przykład POP3 z użyciem funkcji USER/PASS:**

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: USER mrose
S: +OK mrose is valid
C: PASS mvan99
S: +OK mrose is logged in
C: STAT
S: +OK 2 320
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

**Podstawowy przykład POP3 korzystający z apop (i list zamiast STAT):**

```c
S: <wait for connection on TCP port 110>
C: <open connection>
S: +OK POP3 server ready <1896.697170952@dbc.mtview.ca.us>
C: APOP mrose c4c9334bac560ecc979e58001b3e22fb
S: +OK mrose's maildrop has 2 messages (320 octets)
C: LIST
S: +OK 2 messages (320 octets)
S: 1 120
S: 2 200
S: .
C: RETR 1
S: +OK 120 octets
S: <the POP3 server sends message 1>
S: .
C: DELE 1
S: +OK message 1 deleted
C: RETR 2
S: +OK 200 octets
S: <the POP3 server sends message 2>
S: .
C: DELE 2
S: +OK message 2 deleted
C: QUIT
S: +OK dewey POP3 server signing off (maildrop empty)
C: <close connection>
S: <wait for next connection>
```

## <a name="rfcs-supported-by-netx-pop3-client"></a>RFC obsługiwane przez netx POP3 klienta

Klient NetX POP3 jest zgodny ze standardem RFC 1939.
