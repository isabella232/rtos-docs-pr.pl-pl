---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX — klient POP3
description: Interfejs API klienta POP3 usługi Azure RTO NetX udostępnia system transportu poczty dla małych stacji roboczych, aby uzyskać dostęp do maildrops klienta na serwerach POP3 na potrzeby pobierania poczty klienta.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 135530f11f8f54acd6d093a05332056dbdc32be3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822573"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-pop3-client"></a><span data-ttu-id="1b88e-103">Rozdział 1 — wprowadzenie do usługi Azure RTO NetX — klient POP3</span><span class="sxs-lookup"><span data-stu-id="1b88e-103">Chapter 1 - Introduction to Azure RTOS NetX POP3 Client</span></span>

<span data-ttu-id="1b88e-104">Protokół Post Office w wersji 3 (POP3) to protokół zaprojektowany w celu zapewnienia systemu transportu poczty dla małych stacji roboczych, aby uzyskać dostęp do maildrops klienta na serwerach POP3 na potrzeby pobierania poczty klienta.</span><span class="sxs-lookup"><span data-stu-id="1b88e-104">The Post Office Protocol Version 3 (POP3) is a protocol designed to provide a mail transport system for small workstations to access Client maildrops on POP3 Servers for retrieving Client mail.</span></span> <span data-ttu-id="1b88e-105">POP3 wykorzystuje usługi Transmission Control Protocol (TCP) do przeprowadzenia transferu poczty.</span><span class="sxs-lookup"><span data-stu-id="1b88e-105">POP3 utilizes Transmission Control Protocol (TCP) services to perform mail transfer.</span></span> <span data-ttu-id="1b88e-106">W związku z tym usługa POP3 jest wysoce niezawodnym protokołem transferu zawartości.</span><span class="sxs-lookup"><span data-stu-id="1b88e-106">Because of this, POP3 is a highly reliable content transfer protocol.</span></span>

<span data-ttu-id="1b88e-107">Jednak usługa POP3 nie zapewnia obszernych operacji na obsłudze poczty.</span><span class="sxs-lookup"><span data-stu-id="1b88e-107">However, POP3 is does not provide extensive operations on mail handling.</span></span> <span data-ttu-id="1b88e-108">Zwykle poczta jest pobierana przez klienta, a następnie usuwana z maildrop serwera.</span><span class="sxs-lookup"><span data-stu-id="1b88e-108">Typically, mail is downloaded by the Client and then deleted from the Server's maildrop.</span></span>

## <a name="netx-pop3-client-requirements"></a><span data-ttu-id="1b88e-109">Wymagania dotyczące klienta NetX POP3</span><span class="sxs-lookup"><span data-stu-id="1b88e-109">NetX POP3 Client Requirements</span></span>

### <a name="client-requirements"></a><span data-ttu-id="1b88e-110">Wymagania dotyczące klienta</span><span class="sxs-lookup"><span data-stu-id="1b88e-110">Client Requirements</span></span>

<span data-ttu-id="1b88e-111">Interfejs API klienta POP3 usługi Azure RTO NetX wymaga utworzonego wcześniej wystąpienia adresu IP NetX przy użyciu *nx_ip_create* i wcześniej utworzonej puli pakietów NetX przy użyciu *nx_packet_pool_create*.</span><span class="sxs-lookup"><span data-stu-id="1b88e-111">The Azure RTOS NetX POP3 Client API requires a previously created NetX IP instance using *nx_ip_create* and a previously created NetX packet pool using *nx_packet_pool_create*.</span></span> <span data-ttu-id="1b88e-112">Ponieważ klient POP3 NetX korzysta z usług TCP, należy włączyć protokół TCP z wywołaniem *nx_tcp_enable* przed użyciem usługi klienta POP3 NetX w tym samym wystąpieniu IP.</span><span class="sxs-lookup"><span data-stu-id="1b88e-112">Because the NetX POP3 Client utilizes TCP services, TCP must be enabled with the *nx_tcp_enable* call prior to using the NetX POP3 Client services on that same IP instance.</span></span> <span data-ttu-id="1b88e-113">Klient POP3 używa gniazda TCP, aby nawiązać połączenie z serwerem POP3 na porcie POP3 serwera.</span><span class="sxs-lookup"><span data-stu-id="1b88e-113">The POP3 Client uses a TCP socket to connect to a POP3 Server on the Server's POP3 port.</span></span> <span data-ttu-id="1b88e-114">Jest to zwykle ustawiane na *dobrze znanym porcie 110, chociaż nie jest wymagane, aby używać tego portu ani klienta POP3, ani serwer.*</span><span class="sxs-lookup"><span data-stu-id="1b88e-114">This is typically set at the *well-known port 110, though neither POP3 Client nor Server is required to use this port.*</span></span>

<span data-ttu-id="1b88e-115">Rozmiar puli pakietów użyty podczas tworzenia klienta POP3 jest konfigurowany przez użytkownika w postaci ładunku pakietów i liczby dostępnych pakietów.</span><span class="sxs-lookup"><span data-stu-id="1b88e-115">The size of the packet pool used in creating the POP3 Client is user configurable in terms of packet payload and number of packets available.</span></span> <span data-ttu-id="1b88e-116">Jeśli pakiet jest używany tylko w usłudze Klient POP3, ładunek pakietu nie może mieć więcej niż 100-120 bajtów w zależności od długości nazwy użytkownika i hasła lub APOP Digest.</span><span class="sxs-lookup"><span data-stu-id="1b88e-116">If the packet is used only in the POP3 Client create service, the packet payload need not be more than 100-120 bytes depending on the length of username and password, or APOP digest.</span></span> <span data-ttu-id="1b88e-117">Polecenie użytkownika z nazwą użytkownika hosta lokalnego jest prawdopodobnie największym komunikatem wysłanym przez klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="1b88e-117">The USER command with the local host's user name is probably the largest message sent by the POP3 Client.</span></span> <span data-ttu-id="1b88e-118">Istnieje możliwość udostępnienia tej samej puli pakietów w nx_ip_create (domyślna pula pakietów IP), ponieważ wewnętrzne operacje IP nie wymagają bardzo dużego ładunku pakietu do wysyłania i otrzymywania danych kontroli TCP.</span><span class="sxs-lookup"><span data-stu-id="1b88e-118">It is possible to share the same packet pool in the nx_ip_create (IP default packet pool) since the IP internal operations do not require a very large packet payload for sending and receiving TCP control data.</span></span>

<span data-ttu-id="1b88e-119">Jednak użycie tej samej puli pakietów jako puli pakietów klienta POP3 może nie być korzystne.</span><span class="sxs-lookup"><span data-stu-id="1b88e-119">However, it may not be advantageous for the network driver to use the same packet pool as the POP3 Client packet pool.</span></span> <span data-ttu-id="1b88e-120">Ogólnie rzecz biorąc, ładunek ładunku puli pakietów odbioru jest ustawiony na wartość jednostki MTU wystąpienia IP (zwykle 1500 bajtów) interfejsu sieciowego, który jest znacznie większy niż komunikaty klienta POP3.</span><span class="sxs-lookup"><span data-stu-id="1b88e-120">Generally, the payload of the receive packet pool payload is set the IP instance MTU (typically 1500 bytes) of the network interface which is much larger than POP3 Client messages.</span></span> <span data-ttu-id="1b88e-121">Przychodzące komunikaty POP3 zazwyczaj mają znacznie większe dane, a następnie wychodzące komunikaty klienta POP3</span><span class="sxs-lookup"><span data-stu-id="1b88e-121">Incoming POP3 messages would usually be much larger data then outgoing POP3 Client messages</span></span>

## <a name="netx-pop3-client-creation"></a><span data-ttu-id="1b88e-122">NetX tworzenie klienta POP3</span><span class="sxs-lookup"><span data-stu-id="1b88e-122">NetX POP3 Client Creation</span></span>

<span data-ttu-id="1b88e-123">Klient POP3 tworzy usługę, *nx_pop3_client_create* utworzyć gniazdo TCP i nawiązać połączenie z serwerem POP3.</span><span class="sxs-lookup"><span data-stu-id="1b88e-123">The POP3 Client create service, *nx_pop3_client_create* create the TCP socket and connect with the POP3 server.</span></span>

<span data-ttu-id="1b88e-124">Po nawiązaniu połączenia z serwerem POP3 aplikacja kliencka POP3 może wywoływać *nx_pop3_client _mail_items_get* , aby uzyskać liczbę elementów poczty znajdujących się w jego maildrop Box:</span><span class="sxs-lookup"><span data-stu-id="1b88e-124">After connecting with the POP3 server, the POP3 Client application can call *nx_pop3_client _mail_items_get* to obtain the number of mail items sitting in its maildrop box:</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

<span data-ttu-id="1b88e-125">Jeśli co najmniej jeden element znajduje się w maildrop klienta, aplikacja może uzyskać rozmiar określonego elementu poczty przy użyciu usługi *nx_pop3_client_get_mail_item* :</span><span class="sxs-lookup"><span data-stu-id="1b88e-125">If one or more items are in the Client maildrop, the application can obtain the size of a specific mail item, using the *nx_pop3_client_get_mail_item* service:</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item,
                                ULONG *item_size)
```

<span data-ttu-id="1b88e-126">Pierwszy element poczty w maildrop ma indeks 1.</span><span class="sxs-lookup"><span data-stu-id="1b88e-126">The first mail item in the maildrop is at index 1.</span></span>

<span data-ttu-id="1b88e-127">Aby uzyskać rzeczywistą wiadomość e-mail, aplikacja może wywołać usługę *nx_pop3_client_mail_item_get_message_data* w celu pobrania pakietów wiadomości e-mail do momentu, gdy usługa wskaże ostatni pakiet odebrany przez argument wejściowy final_packet:</span><span class="sxs-lookup"><span data-stu-id="1b88e-127">To get the actual mail message, the application can call the *nx_pop3_client_mail_item_get_message_data* service to retrieve the mail message packets until the service indicates the last packet is received by the final_packet input argument:</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                        NX_POP3_CLIENT *client_ptr,
                        NX_PACKET **recv_packet_ptr,
                        ULONG *bytes_retrieved,
                        UINT *final_packet)
```

<span data-ttu-id="1b88e-128">Aby usunąć określony element poczty, aplikacja wywołuje *nx_pop3_client_mail_item_delete* z tym samym indeksem, które są używane w poprzednim wywołaniu *nx_pop3_client_get_mail_item* .</span><span class="sxs-lookup"><span data-stu-id="1b88e-128">To delete a specific mail item, the application calls *nx_pop3_client_mail_item_delete* with the same index as used in the preceding *nx_pop3_client_get_mail_item* call.</span></span>

<span data-ttu-id="1b88e-129">Klienta można usunąć za pomocą usługi *nx_pop3_client_delete* .</span><span class="sxs-lookup"><span data-stu-id="1b88e-129">The Client can be deleted using the *nx_pop3_client_delete* service.</span></span> <span data-ttu-id="1b88e-130">Zwróć uwagę na to, że aplikacja może usunąć pulę pakietów klienta POP3 przy użyciu usługi *nx_packet_pool_delete* nie ma już do niej zastosowania.</span><span class="sxs-lookup"><span data-stu-id="1b88e-130">Note it is up to the application to delete the POP3 Client packet pool using the *nx_packet_pool_delete* service there is no longer has any use for it.</span></span>

## <a name="netx-pop3-client-constraints"></a><span data-ttu-id="1b88e-131">NetX ograniczenia klienta POP3</span><span class="sxs-lookup"><span data-stu-id="1b88e-131">NetX POP3 Client Constraints</span></span>

<span data-ttu-id="1b88e-132">Implementacja klienta POP3 NetX ma pewne ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="1b88e-132">There are some constraints in the NetX POP3 Client implementation:</span></span>

1. <span data-ttu-id="1b88e-133">Klient POP3 NetX nie obsługuje polecenia AUTH, chociaż implementuje uwierzytelnianie APOP przy użyciu skrótu DIGEST-MD5 do wymiany uwierzytelniania serwera klienta.</span><span class="sxs-lookup"><span data-stu-id="1b88e-133">The NetX POP3 Client does not support the AUTH command although it does implement APOP authentication using DIGEST-MD5 for the Client Server authentication exchange.</span></span>

1. <span data-ttu-id="1b88e-134">Klient POP3 NetX nie implementuje wszystkich poleceń POP3 (np. poleceń TOP lub UIDL).</span><span class="sxs-lookup"><span data-stu-id="1b88e-134">NetX POP3 Client does not implement all POP3 commands (e.g. the TOP or UIDL commands).</span></span> <span data-ttu-id="1b88e-135">Poniżej znajduje się lista poleceń, które obsługuje:</span><span class="sxs-lookup"><span data-stu-id="1b88e-135">Below is a list of commands it does support:</span></span>
   - <span data-ttu-id="1b88e-136">AKTUALIZUJĄCY nie działa</span><span class="sxs-lookup"><span data-stu-id="1b88e-136">NOOP</span></span>
   - <span data-ttu-id="1b88e-137">RSET</span><span class="sxs-lookup"><span data-stu-id="1b88e-137">RSET</span></span>

## <a name="netx-pop3-client-login"></a><span data-ttu-id="1b88e-138">NetX logowania klienta POP3</span><span class="sxs-lookup"><span data-stu-id="1b88e-138">NetX POP3 Client Login</span></span>

<span data-ttu-id="1b88e-139">Aby uzyskać dostęp do usługi maildrop, klient POP3 NetX musi uwierzytelnić się na serwerze POP3.</span><span class="sxs-lookup"><span data-stu-id="1b88e-139">A NetX POP3 Client must authenticate itself (login) to a POP3 Server to access a maildrop.</span></span> <span data-ttu-id="1b88e-140">Można to zrobić za pomocą poleceń USER/PASS i podając nazwę użytkownika i hasło znane serwerowi POP3 lub korzystając z polecenia APOP i skrótu MD5 opisanego poniżej.</span><span class="sxs-lookup"><span data-stu-id="1b88e-140">It can do so either by using the USER/PASS commands and providing a username and password known to the POP3 Server, or by using the APOP command and MD5 digest described below.</span></span>

<span data-ttu-id="1b88e-141">Nazwa użytkownika jest zwykle w pełni kwalifikowaną nazwą domeny (zawiera lokalną część i nazwę domeny oddzieloną znakiem "@").</span><span class="sxs-lookup"><span data-stu-id="1b88e-141">The username is typically a fully qualified domain name (contains a local-part and a domain name, separated by an '@' character).</span></span> <span data-ttu-id="1b88e-142">W przypadku korzystania z poleceń POP3 użytkownika i PASSu klient wysyła swoją nazwę użytkownika i hasło, które nie są szyfrowane przez Internet.</span><span class="sxs-lookup"><span data-stu-id="1b88e-142">When using the POP3 commands USER and PASS, the Client is sending its username and password unencrypted over the Internet.</span></span>

<span data-ttu-id="1b88e-143">Aby uniknąć zagrożenia bezpieczeństwa dla nazwy użytkownika i hasła w postaci zwykłego tekstu, można skonfigurować klienta usługi NetX POP3 do korzystania z uwierzytelniania APOP przez ustawienie parametru *APOP_authentication* w usłudze *nx_pop3_client_create* :</span><span class="sxs-lookup"><span data-stu-id="1b88e-143">To avoid the security risk of clear texting username and password, the NetX POP3 Client can be configured to use APOP authentication by setting the *APOP_authentication* parameter in the *nx_pop3_client_create* service:</span></span>

```c
UINT  nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            NXD_ADDRESS *server_ip_address, ULONG server_port,
                            CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="1b88e-144">Lub tylko dla aplikacji IPv4, usługa *nx_pop3_client_create* :</span><span class="sxs-lookup"><span data-stu-id="1b88e-144">Or for IPv4 only applications, the *nx_pop3_client_create* service:</span></span>

```c
UINT  nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                            UINT APOP_authentication,
                            NX_IP *ip_ptr,
                            NX_PACKET_POOL *packet_pool_ptr,
                            ULONG server_ip_address,
                            ULONG server_port, CHAR *client_name,
                            CHAR *client_password)
```

<span data-ttu-id="1b88e-145">Gdy klient wysyła polecenie APOP, przyjmuje skrót MD5 zawierający domenę serwera, czas lokalny i identyfikator procesu wyodrębnione z powitania serwera oraz hasło klienta.</span><span class="sxs-lookup"><span data-stu-id="1b88e-145">When the Client sends the APOP command, it takes an MD5 digest containing the server domain, local time and process ID extracted from the Server greeting, plus the Client password.</span></span> <span data-ttu-id="1b88e-146">Serwer POP3 utworzy skrót MD5 zawierający te same informacje i jeśli jego skrót MD5 jest zgodny ze skrótem MD5 klienta, klient zostanie uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="1b88e-146">The POP3 Server will create an MD5 digest containing the same information and if its MD5 digest matches the Client's MD5 digest, the Client is authenticated.</span></span>

<span data-ttu-id="1b88e-147">Jeśli uwierzytelnianie APOP nie powiedzie się, NetX klient POP3 podejmie próbę uwierzytelnienia użytkownika/przekazanie.</span><span class="sxs-lookup"><span data-stu-id="1b88e-147">If APOP authentication fails, NetX POP3 Client will attempt USER/PASS authentication.</span></span>

## <a name="the-pop3-client-maildrop"></a><span data-ttu-id="1b88e-148">Klient POP3 maildrop</span><span class="sxs-lookup"><span data-stu-id="1b88e-148">The POP3 Client Maildrop</span></span>

<span data-ttu-id="1b88e-149">Poczta klienta jest przechowywana na serwerze POP3 w skrzynce pocztowej lub "maildrop".</span><span class="sxs-lookup"><span data-stu-id="1b88e-149">Client mail is stored on a POP3 Server in a mailbox or "maildrop."</span></span> <span data-ttu-id="1b88e-150">Klient maildrop na serwerze POP3 jest reprezentowany przez 1 listę elementów poczty.</span><span class="sxs-lookup"><span data-stu-id="1b88e-150">A Client maildrop on a POP3 Server is represented as a 1 based list of mail items.</span></span> <span data-ttu-id="1b88e-151">Oznacza to, że każda poczta jest określana przez swój indeks na liście maildrop przy użyciu pierwszego elementu poczty w indeksie 1 (nie zero).</span><span class="sxs-lookup"><span data-stu-id="1b88e-151">That is, each mail is referred to by its index in the maildrop list with the first mail item at index 1 (not zero).</span></span> <span data-ttu-id="1b88e-152">Polecenia POP3 odwołują się do określonych elementów poczty według ich indeksu na tej liście.</span><span class="sxs-lookup"><span data-stu-id="1b88e-152">POP3 commands refer to specific mail items by their index in this list.</span></span>

## <a name="the-pop3-protocol-state-machine"></a><span data-ttu-id="1b88e-153">Komputer stanu protokołu POP3</span><span class="sxs-lookup"><span data-stu-id="1b88e-153">The POP3 Protocol State Machine</span></span>

<span data-ttu-id="1b88e-154">Protokół POP3 wymaga, aby zarówno klient, jak i serwer utrzymują stan sesji POP3.</span><span class="sxs-lookup"><span data-stu-id="1b88e-154">The POP3 protocol requires that both Client and Server maintain the state of the POP3 session.</span></span> <span data-ttu-id="1b88e-155">Po pierwsze klient próbuje nawiązać połączenie z serwerem POP3.</span><span class="sxs-lookup"><span data-stu-id="1b88e-155">First, the Client attempts to connect to the POP3 Server.</span></span> <span data-ttu-id="1b88e-156">Po pomyślnym przejściu do protokołu POP3, który ma trzy odrębne Stany zdefiniowane przez RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="1b88e-156">If successful it enters into the POP3 protocol which has three distinct states defined by RFC 1939.</span></span> <span data-ttu-id="1b88e-157">Stan początkowy jest stanem autoryzacji, w którym musi identyfikować się na serwerze.</span><span class="sxs-lookup"><span data-stu-id="1b88e-157">The initial state is the Authorization state in which it must identify itself to the Server.</span></span> <span data-ttu-id="1b88e-158">W stanie autoryzacji klient POP3 może wystawiać tylko użytkownika i polecenia PASS, a w tej kolejności lub polecenie APOP.</span><span class="sxs-lookup"><span data-stu-id="1b88e-158">In the Authorization state, the POP3 Client can only issue the USER and the PASS commands, and in that order, or the APOP command.</span></span>

<span data-ttu-id="1b88e-159">Po uwierzytelnieniu klienta POP3 sesja klienta przechodzi do stanu transakcji.</span><span class="sxs-lookup"><span data-stu-id="1b88e-159">Once the POP3 Client is authenticated, the Client session enters the Transaction state.</span></span> <span data-ttu-id="1b88e-160">W tym stanie klient może pobrać i zażądać usunięcia poczty.</span><span class="sxs-lookup"><span data-stu-id="1b88e-160">In this state, the Client can download and request mail deletion.</span></span> <span data-ttu-id="1b88e-161">Polecenia dozwolone w stanie transakcji to LIST, STAT, RETR, &, RSET i QUIT.</span><span class="sxs-lookup"><span data-stu-id="1b88e-161">The commands allowed in the Transaction state are LIST, STAT, RETR, DELE, RSET and QUIT.</span></span> <span data-ttu-id="1b88e-162">Zwykle klient POP3 wysyła polecenie STAT, a następnie szereg poleceń RETR (jeden dla każdego elementu poczty w jego maildrop).</span><span class="sxs-lookup"><span data-stu-id="1b88e-162">Typically the POP3 Client sends a STAT command followed by a series of RETR commands (one for each mail item in its maildrop).</span></span>

<span data-ttu-id="1b88e-163">Gdy klient wystawia polecenie QUIT, sesja POP3 przechodzi w stan aktualizacji, w którym inicjuje połączenie TCP z serwerem.</span><span class="sxs-lookup"><span data-stu-id="1b88e-163">Once the Client issues the QUIT command, the POP3 session enters the Update state in which it initiates the TCP disconnect from the Server.</span></span> <span data-ttu-id="1b88e-164">Aby później pobrać pocztę, aplikacja kliencka POP3 może wywoływać w `nx_pop3_client_mail_items_get` dowolnym momencie, aby sprawdzić nową pocztę w maildrop.</span><span class="sxs-lookup"><span data-stu-id="1b88e-164">To download mail later, the POP3 Client application may call `nx_pop3_client_mail_items_get` at any time to check for new mail in the maildrop.</span></span>

### <a name="pop3-server-reply-codes"></a><span data-ttu-id="1b88e-165">Kody odpowiedzi serwera POP3</span><span class="sxs-lookup"><span data-stu-id="1b88e-165">POP3 Server Reply Codes</span></span>

- <span data-ttu-id="1b88e-166">**+ OK**: serwer używa tej odpowiedzi, aby zaakceptować polecenie klienta.</span><span class="sxs-lookup"><span data-stu-id="1b88e-166">**+OK**: The Server uses this reply to accept a Client command.</span></span> <span data-ttu-id="1b88e-167">Serwer może zawierać dodatkowe informacje po "+ OK", ale nie może założyć, że klient będzie przetwarzać te informacje, chyba że w przypadku pobierania danych wiadomości e-mail lub poleceń LIST lub &.</span><span class="sxs-lookup"><span data-stu-id="1b88e-167">The Server can include additional information after the '+OK' but cannot assume the Client will process this information, except in the case of downloading mail message data or the LIST or DELE commands.</span></span> <span data-ttu-id="1b88e-168">W tym drugim przypadku "argument" po poleceniu odwołuje się do indeksu elementu poczty w maildrop klienta.</span><span class="sxs-lookup"><span data-stu-id="1b88e-168">In the latter case, the 'argument' after the command references the index of the mail item in the Client maildrop.</span></span>

- <span data-ttu-id="1b88e-169">**-ERR**: serwer używa tej odpowiedzi, aby odrzucić polecenie klienta.</span><span class="sxs-lookup"><span data-stu-id="1b88e-169">**-ERR**: The Server uses this reply to reject a Client command.</span></span> <span data-ttu-id="1b88e-170">Serwer może wysłać dodatkowe informacje po "-ERR", ale nie może założyć, że klient będzie przetwarzać te informacje.</span><span class="sxs-lookup"><span data-stu-id="1b88e-170">The Server may send additional information following the '-ERR' but cannot assume the Client will process this information.</span></span>

### <a name="sample-pop3-client---server-session"></a><span data-ttu-id="1b88e-171">Przykładowy klient POP3 — sesja serwera</span><span class="sxs-lookup"><span data-stu-id="1b88e-171">Sample POP3 Client - Server Session</span></span>

<span data-ttu-id="1b88e-172">**Podstawowy przykład POP3 korzystający z użytkownika/PRZEBIEGu:**</span><span class="sxs-lookup"><span data-stu-id="1b88e-172">**Basic POP3 example using USER/PASS:**</span></span>

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

<span data-ttu-id="1b88e-173">**Podstawowy przykład POP3 przy użyciu APOP (i listy zamiast STAT):**</span><span class="sxs-lookup"><span data-stu-id="1b88e-173">**Basic POP3 example using APOP (and LIST instead of STAT):**</span></span>

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

## <a name="rfcs-supported-by-netx-pop3-client"></a><span data-ttu-id="1b88e-174">Specyfikacje RFC obsługiwane przez klienta POP3 NetX</span><span class="sxs-lookup"><span data-stu-id="1b88e-174">RFCs Supported by NetX POP3 Client</span></span>

<span data-ttu-id="1b88e-175">NetX klient POP3 jest zgodny ze standardem RFC 1939.</span><span class="sxs-lookup"><span data-stu-id="1b88e-175">NetX Client POP3 is compliant with RFC 1939.</span></span>
