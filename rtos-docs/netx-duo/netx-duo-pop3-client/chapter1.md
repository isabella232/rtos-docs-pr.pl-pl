---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX POP3
description: Interfejs API klienta POP3 NetX Duo został zaprojektowany w celu zapewnienia systemowi transportu poczty dla małych stacji roboczych, aby uzyskać dostęp do maildrops klienta na serwerach POP3 w celu pobrania poczty klienta.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4d41da1e1e87e59c5c40674a58b288ac62ec8c78
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821751"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX POP3

Protokół Post Office w wersji 3 (POP3) to protokół zaprojektowany w celu zapewnienia systemu transportu poczty dla małych stacji roboczych, aby uzyskać dostęp do maildrops klienta na serwerach POP3 na potrzeby pobierania poczty klienta. POP3 wykorzystuje usługi Transmission Control Protocol (TCP) do przeprowadzenia transferu poczty. W związku z tym usługa POP3 jest wysoce niezawodnym protokołem transferu zawartości.

Jednak usługa POP3 nie zapewnia obszernych operacji na obsłudze poczty. Zwykle poczta jest pobierana przez klienta, a następnie usuwana z maildrop serwera.

## <a name="netx-duo-pop3-client-requirements"></a>Wymagania dotyczące klienta POP3 NetX Duo

### <a name="client-requirements"></a>Wymagania dotyczące klienta

Interfejs API klienta usługi NetX POP3 wymaga utworzonego wcześniej wystąpienia protokołu IP NetX Duo przy użyciu *nx_ip_create* i utworzonego wcześniej puli pakietów NetX przy użyciu *nx_packet_pool_create*. Ponieważ klient POP3 NetX Duo korzysta z usług TCP, należy włączyć protokół TCP z wywołaniem *nx_tcp_enable* przed użyciem interfejsu API klienta usługi POP3 NetX Duo dla tego samego wystąpienia IP. Klient POP3 używa gniazda TCP, aby nawiązać połączenie z serwerem POP3 na porcie POP3 serwera. Jest to zwykle ustawiane na *dobrze znanym porcie 110, chociaż nie jest wymagane użycie tego portu przez klienta POP3 ani serwer.*

Rozmiar puli pakietów użyty podczas tworzenia klienta POP3 jest konfigurowany przez użytkownika w postaci ładunku pakietów i liczby dostępnych pakietów. Jeśli pakiet jest używany tylko w usłudze Klient POP3, ładunek pakietu nie może mieć więcej niż 100-120 bajtów w zależności od długości nazwy użytkownika i hasła lub APOP Digest. Polecenie użytkownika z nazwą użytkownika hosta lokalnego jest prawdopodobnie największym komunikatem wysłanym przez klienta POP3. Istnieje możliwość udostępnienia tej samej puli pakietów w nx_ip_create (domyślna pula pakietów IP), ponieważ wewnętrzny operatiosn IP nie wymaga bardzo dużego ładunku pakietu do wysyłania i otrzymywania danych kontroli TCP.

Nie jest to jednak ogólnie korzystne dla sterownika Ethernet do używania tej samej puli pakietów jako puli pakietów klienta POP3. Ogólnie rzecz biorąc, ładunek ładunku puli pakietów odbioru jest ustawiony na wartość jednostki MTU wystąpienia IP (zwykle 1500 bajtów) interfejsu sieciowego, który jest znacznie większy niż komunikaty klienta POP3. Przychodzące komunikaty POP3 zwykle mają znacznie większy rozmiar danych, a następnie wychodzące komunikaty klienta POP3

## <a name="netx-duo-pop3-client-creation"></a>Tworzenie klienta POP3 NetX Duo

Istnieją dwie usługi do tworzenia klienta POP3. Zalecana usługa to *nxd_pop3_client_create* , która przyjmuje typ danych adresu NXD_ADDRESS, który akceptuje adresy IPv4 lub IPv6 dla serwera POP3. Inna usługa klienta POP3, *nx_pop3_client_create* akceptuje tylko adresy IPv4 dla serwera POP3. Obie usługi powiążą port gniazda TCP i nawiązują połączenie z serwerem POP3.

Po nawiązaniu połączenia z serwerem POP3 aplikacja kliencka POP3 może wywoływać *nx_pop3_client _mail_items_get* , aby uzyskać liczbę elementów poczty znajdujących się w jego maildrop Box:

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items, ULONG *maildrop_total_size);
```

Jeśli co najmniej jeden element znajduje się w maildrop klienta, aplikacja może uzyskać rozmiar określonego elementu poczty przy użyciu usługi *nx_pop3_client_get_mail_item* :

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

Pierwszy element poczty w maildrop ma indeks 1.

Aby uzyskać rzeczywistą wiadomość e-mail, aplikacja może wywołać usługę *nx_pop3_client_mail_item_get_message_data* w celu pobrania pakietów wiadomości e-mail do momentu, gdy usługa wskaże ostatni pakiet odebrany przez argument wejściowy final_packet:

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

Aby usunąć określony element poczty, aplikacja wywołuje *nx_pop3_client_mail_item_delete* z tym samym indeksem, które są używane w poprzednim wywołaniu *nx_pop3_client_get_mail_item* .

Klienta można usunąć za pomocą usługi *nx_pop3_client_delete* . Zwróć uwagę na to, że aplikacja może usunąć pulę pakietów klienta POP3 przy użyciu usługi *nx_packet_pool_delete* nie ma już do niej zastosowania.

## <a name="netx-duo-pop3-client-constraints"></a>Ograniczenia klienta POP3 NetX Duo

Implementacja klienta POP3 NetX Duo zawiera pewne ograniczenia:

1. Klient POP3 NetX Duo nie obsługuje polecenia AUTH, mimo że implementuje uwierzytelnianie APOP przy użyciu skrótu DIGEST-MD5 do wymiany uwierzytelniania serwera klienckiego.
2. Klient POP3 NetX Duo nie implementuje wszystkich poleceń POP3 (np. poleceń TOP lub UIDL). Poniżej znajduje się lista poleceń, które obsługuje:
   - AKTUALIZUJĄCY nie działa
   - RSET

## <a name="netx-duo-pop3-client-login"></a>Logowanie klienta POP3 NetX Duo

Klient POP3 NetX Duo musi uwierzytelnić się na serwerze POP3, aby uzyskać dostęp do maildrop. Można to zrobić za pomocą poleceń USER/PASS i podając nazwę użytkownika i hasło znane serwerowi POP3 lub korzystając z polecenia APOP i skrótu MD5 opisanego poniżej.

Nazwa użytkownika jest zwykle w pełni kwalifikowaną nazwą domeny (zawiera lokalną część i nazwę domeny oddzieloną znakiem "@"). W przypadku korzystania z poleceń POP3 użytkownika i PASSu klient wysyła swoją nazwę użytkownika i hasło, które nie są szyfrowane przez Internet.

Aby uniknąć zagrożenia bezpieczeństwa dla nazwy użytkownika i hasła w postaci zwykłego tekstu, klient POP3 NetX Duo można skonfigurować tak, aby korzystał z uwierzytelniania APOP przez ustawienie parametru *APOP_authentication* w usłudze *nxd_pop3_client_create* :

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication,
    NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address, ULONG server_port,
    CHAR *client_name,
    CHAR *client_password);
```

Lub tylko dla aplikacji IPv4, usługa *nx_pop3_client_create* :

```C
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address,
    ULONG server_port, CHAR *client_name,
    CHAR *client_password);
```

Gdy klient wysyła polecenie APOP, przyjmuje jako jedyny argument skrót MD5 zawierający domenę serwera, czas lokalny i identyfikator procesu wyodrębnione z powitania serwera oraz hasło klienta. Serwer POP3 utworzy skrót MD5 zawierający te same informacje i jeśli jego skrót MD5 jest zgodny ze skrótem MD5 klienta, klient zostanie uwierzytelniony.

Jeśli uwierzytelnianie APOP nie powiedzie się, klient POP3 NetX Duo podejmie próbę uwierzytelnienia użytkownika/przejścia.

## <a name="the-pop3-client-maildrop"></a>Klient POP3 maildrop

Poczta klienta jest przechowywana na serwerze POP3 w skrzynce pocztowej lub "maildrop". Klient maildrop na serwerze POP3 jest reprezentowany przez 1 listę elementów poczty. Oznacza to, że każda poczta jest określana przez swój indeks na liście maildrop przy użyciu pierwszego elementu poczty w indeksie 1 (nie zero). Polecenia POP3 odwołują się do określonych elementów poczty według ich indeksu na tej liście.

## <a name="the-pop3-protocol-state-machine"></a>Komputer stanu protokołu POP3

Protokół POP3 wymaga, aby zarówno klient, jak i serwer utrzymują stan sesji POP3. Po pierwsze klient próbuje nawiązać połączenie z serwerem POP3. Po pomyślnym przejściu do protokołu POP3, który ma trzy odrębne Stany zdefiniowane przez RFC 1939. Stan początkowy jest stanem autoryzacji, w którym musi identyfikować się na serwerze. W stanie autoryzacji klient POP3 może wystawiać tylko użytkownika i polecenia PASS, a w tej kolejności lub polecenie APOP.

Po uwierzytelnieniu klienta POP3 sesja klienta przechodzi do stanu transakcji. W tym stanie klient może pobrać i zażądać usunięcia poczty. Polecenia dozwolone w stanie transakcji to LIST, STAT, RETR, &, RSET i QUIT. Zwykle klient POP3 wysyła polecenie STAT, a następnie szereg poleceń RETR (jeden dla każdego elementu poczty w jego maildrop).

Gdy klient wystawia polecenie QUIT, sesja POP3 przechodzi w stan aktualizacji, w którym inicjuje połączenie TCP z serwerem. Aby pobrać pocztę w innym momencie, aplikacja kliencka POP3 może wywoływać nx_pop3_client_mail_items_get, aby sprawdzić nową pocztę w maildrop.

### <a name="pop3-server-reply-codes"></a>Kody odpowiedzi serwera POP3

- + OK serwer używa tej odpowiedzi, aby zaakceptować polecenie klienta. Serwer może zawierać dodatkowe informacje po "+ OK", ale nie może założyć, że klient będzie przetwarzać te informacje, chyba że w przypadku pobierania danych wiadomości e-mail lub poleceń LIST lub &. W tym drugim przypadku "argument" po poleceniu odwołuje się do indeksu elementu poczty w maildrop klienta.
- -BŁĄD serwer używa tej odpowiedzi, aby odrzucić polecenie klienta. Serwer może wysłać dodatkowe informacje po "-ERR", ale nie może założyć, że klient będzie przetwarzać te informacje.

### <a name="sample-pop3-client---server-session"></a>Przykładowy klient POP3 — sesja serwera

**Podstawowy przykład POP3 korzystający z użytkownika/PRZEBIEGu:**

```
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

**Podstawowy przykład POP3 przy użyciu APOP (i listy zamiast STAT):**

```
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

## <a name="rfcs-supported-by-netx-duo-pop3-client"></a>Specyfikacje RFC obsługiwane przez klienta POP3 NetX Duo

Program NetX Duo Client POP3 jest zgodny ze standardem RFC 1939.
