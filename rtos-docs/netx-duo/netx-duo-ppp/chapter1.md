---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo Point-to-Point Protocol (PPP)
description: W tym rozdziale przedstawiono moduł Point-to-Point Protocol (PPP) usługi Azure RTO NetX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f439cf66e6619652ae8ab9097b2de5e584d78c59
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821744"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-point-to-point-protocol-ppp"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo Point-to-Point Protocol (PPP)

Zazwyczaj aplikacje NetX łączą się z rzeczywistą siecią fizyczną za pomocą sieci Ethernet. Zapewnia to szybki i wydajny dostęp do sieci. Istnieją jednak sytuacje, w których aplikacja nie ma dostępu do sieci Ethernet. W takich przypadkach aplikacja może nadal łączyć się z siecią za pomocą interfejsu szeregowego połączonego bezpośrednio z innym członkiem sieci. Najbardziej typowym protokołem oprogramowania używanym do zarządzania takimi połączeniami jest Point-to-Point Protocol (PPP).

Mimo że komunikacja szeregowa jest stosunkowo prosta, protokół PPP jest dość skomplikowany. Protokół PPP ma w rzeczywistości wiele protokołów, takich jak protokół kontroli linku (LCP), Protokół kontroli protokołu (IPCP), protokół uwierzytelniania hasła (PAP) i protokół uwierzytelniania Challenge-Handshake (CHAP). LCP jest głównym protokołem dla protokołu PPP. Jest to miejsce, w którym podstawowe składniki łącza są dynamicznie negocjowane w sposób komunikacji równorzędnej. Po pomyślnym wynegocjowaniu podstawowych charakterystyk linku protokoły PAP i/lub CHAP są używane do zapewnienia, że połączony element równorzędny jest prawidłowy. Jeśli oba elementy równorzędne są prawidłowe, protokół IPCP jest następnie używany do negocjowania adresów IP używanych przez elementy równorzędne. Po zakończeniu protokołu IPCP protokół PPP będzie w stanie wysyłać i odbierać pakiety IP.

NetX przegląda protokół PPP głównie jako sterownik urządzenia. Funkcja *nx_ppp_driver* jest dostarczana do funkcji tworzenia NetX IP, *nx_ip_create*. W przeciwnym razie NetX nie ma żadnej bezpośredniej znajomości protokołu PPP.

## <a name="ppp-serial-communication"></a>Komunikacja szeregowa PPP

Pakiet NetX PPP wymaga, aby aplikacja zapewniała sterownik komunikacji szeregowej. Sterownik musi obsługiwać 8-bitowe znaki i może również wykorzystywać kontrolę przepływu oprogramowania. Jest on odpowiedzialny za zainicjowanie sterownika, który należy wykonać przed utworzeniem wystąpienia protokołu PPP.

Aby można było wysyłać pakiety PPP, należy podać procedurę bajtów wyjściowych sterownika szeregowego do PPP (określony w funkcji *nx_ppp_create* ). Ta procedura wyjściowa bajtu sterownika szeregowego zostanie wywołana kilkukrotnie w celu przesłania całego pakietu protokołu PPP. Jest on odpowiedzialny za przebuforowanie danych wyjściowych sterownika szeregowego. Po stronie odbierającej sterownik szeregowy aplikacji musi wywoływać funkcję PPP *nx_ppp_byte_receive* przy każdym odebraniu nowego bajtu. Zwykle jest to wykonywane z kontekstu procedury usługi przerwania (ISR). Funkcja *nx_ppp_byte_receive* umieszcza przychodzący bajt w buforze cyklicznym i ostrzega wątek odbioru protokołu PPP o obecności.

## <a name="ppp-over-ethernet-communication"></a>Komunikacja PPP przez Ethernet

NetX PPP również może przesyłać komunikaty PPP przez sieć Ethernet, w takiej sytuacji pakiet protokołu PPP NetX wymaga, aby aplikacja zapewniała sterownik komunikacyjny Ethernet.

Aby można było wysyłać pakiety PPP za pośrednictwem sieci Ethernet, należy podać procedurę wyjściową PPP (określoną w funkcji *nx_ppp_packet_send_set* ). Ta procedura wyjściowa będzie wywoływana wielokrotnie w celu przesłania całego pakietu protokołu PPP. Po stronie odbierającej odbiornik aplikacji musi wywoływać funkcję PPP *nx_ppp_packet_receive* przy każdym nadejściu nowego pakietu.

## <a name="ppp-packet"></a>Pakiet PPP

Protokół PPP wykorzystuje AHDLC ramek (podzestaw HDLC) do hermetyzacji wszystkich kontroli protokołu PPP i danych użytkownika. Ramka AHDLC wygląda następująco:

|**Flaga**|**Adresowe**|**Przytrzymaj**|**Informacje**|**CRC**|**Flaga**|
|--------|--------|--------|---------------|-------|--------|
|7E |ZZ|03|[0-1502 bajtów]|2 bajty| 7E|

Każda klatka PPP ma ten ogólny wygląd. Pierwsze dwie bajty pola informacji zawierają typ protokołu PPP. Prawidłowe wartości są zdefiniowane w następujący sposób:

- C021: LCP
- 8021: IPCP
- C023: PAP
- C223: CHAP
- 0021: pakiet danych IP

Jeśli typ protokołu 0x0021 jest obecny, pakiet IP następuje natychmiast. W przeciwnym razie, jeśli jeden z innych protokołów jest obecny, następujące bajty odpowiadają określonemu protokołowi.

Aby zapewnić unikatową 0x7E znaczników początku/końca ramki oraz obsługę sterowania przepływem oprogramowania, AHDLC używa sekwencji unikowych do reprezentowania różnych wartości bajtowych. Wartość 0x7D określa, że znak następujący jest zakodowany, który jest zasadniczo pierwotnym znakiem wyłącznych logicznie z 0x20. Na przykład wartość 0x03 dla pola Ctrl w nagłówku jest reprezentowana przez dwubajtową sekwencję: 7D 23. Domyślnie wartości mniejsze niż 0x20 są konwertowane na sekwencję ucieczki, a także wartości 0x7E i 0x7D Znalezione w polu informacje. Należy zauważyć, że sekwencje unikowe mają również zastosowanie do pola CRC.

## <a name="link-control-protocol-lcp"></a>Protokół kontroli łączy (LCP)

LCP jest podstawowym protokołem PPP i jest pierwszym protokołem do uruchomienia. Protokół LCP jest odpowiedzialny za negocjowanie różnych parametrów PPP, łącznie z maksymalną jednostką odbioru (MRU) i protokołem uwierzytelniania (PAP, CHAP lub None) do użycia. Po obu stronach protokołu LCP zgadzają się na parametry PPP, protokoły uwierzytelniania — jeśli istnieją, a następnie zaczynają działać.

## <a name="password-authentication-protocol-pap"></a>Protokół uwierzytelniania hasła (PAP)

Protokół PAP jest stosunkowo prostym protokołem, który opiera się na nazwie i haśle dostarczanym przez jedną stronę połączenia (jako negocjowane w protokole LCP). Druga strona weryfikuje te informacje. Jeśli jest poprawna, do nadawcy jest zwracany komunikat o akceptacji, a następnie protokół PPP może przechodzić do komputera stanu IPCP. W przeciwnym razie, jeśli nazwa lub hasło są nieprawidłowe, połączenie zostanie odrzucone.

>[!NOTE]
> Obie strony interfejsu mogą żądać protokołu PAP, ale protokół PAP jest zazwyczaj używany tylko w jednym kierunku.

## <a name="challenge-handshake-authentication-protocol-chap"></a>Protokół uwierzytelniania Challenge-Handshake (CHAP)

Protokół CHAP jest bardziej złożonym protokołem uwierzytelniania niż PAP. Wystawca uwierzytelnienia protokołu CHAP dostarcza jego element równorzędny przy użyciu nazwy i wartości. Element równorzędny następnie używa podanej nazwy, aby znaleźć współużytkowany "klucz tajny" między tymi dwoma jednostkami. Obliczenia są następnie wykonywane nad IDENTYFIKATORem, wartością i "wpisem tajnym". Wynik tego obliczenia jest zwracany w odpowiedzi. W przypadku poprawnego protokołu PPP można przechodzić do komputera stanu IPCP. W przeciwnym razie, jeśli wynik jest niepoprawny, połączenie zostanie odrzucone.

Innym interesującym aspektem protokołu CHAP jest to, że może wystąpić w losowych odstępach czasu po nawiązaniu połączenia. Służy do zapobiegania przechwyceniu połączenia — po jego uwierzytelnieniu. Jeśli wyzwanie nie powiedzie się w jednym z tych losowo, połączenie zostanie natychmiast przerwane.

>[!NOTE]
> Obie strony interfejsu mogą żądać protokołu CHAP, ale protokół CHAP jest zazwyczaj używany tylko w jednym kierunku.

## <a name="internet-protocol-control-protocol-ipcp"></a>Protokół kontroli protokołu internetowego (IPCP)

Wartość IPCP to ostatni protokół, który należy wykonać przed udostępnieniem komunikacji PPP na potrzeby transferu danych IP NetX. Główny cel tego protokołu jest przeznaczony dla jednego elementu równorzędnego w celu poinformowania o innym adresie IP. Po skonfigurowaniu adresu IP NetX transfer danych IP jest włączony.

## <a name="data-transfer"></a>Transfer danych

Jak wspomniano wcześniej, NetX pakiety danych IP znajdują się w ramkach PPP z IDENTYFIKATORem protokołu 0x0021. Wszystkie odebrane pakiety danych są umieszczane w co najmniej jednej strukturze NX_PACKET i przesyłane do NetXego przetwarzania. W przypadku transmisji zawartość pakietu NetX jest umieszczana w ramce AHDLC i przesyłana.

## <a name="ppp-rfcs"></a>Specyfikacje RFC protokołu PPP

NetX PPP jest zgodny z RFC1332, RFC1334, RFC1661, RFC1994 i powiązanymi specyfikacjami RFC.