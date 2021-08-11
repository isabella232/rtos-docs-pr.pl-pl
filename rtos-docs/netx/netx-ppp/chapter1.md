---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Point-to-Point Protocol (PPP)
description: Zazwyczaj aplikacje NetX łączą się z rzeczywistą siecią fizyczną za pośrednictwem sieci Ethernet.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4027d79f80928804a757e5801c74865389ab1d0237510e63348945ebe2b30045
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801975"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-point-to-point-protocol-ppp"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Point-to-Point Protocol (PPP)

Zazwyczaj aplikacje NetX łączą się z rzeczywistą siecią fizyczną za pośrednictwem sieci Ethernet. Zapewnia to szybki i wydajny dostęp do sieci. Istnieją jednak sytuacje, w których aplikacja nie ma dostępu do sieci Ethernet. W takich przypadkach aplikacja może nadal łączyć się z siecią za pośrednictwem interfejsu szeregowego podłączonego bezpośrednio do innego członka sieci. Najbardziej powszechnym protokołem oprogramowania używanym do zarządzania takim połączeniem jest protokół Point-to-Point Protocol (PPP).

Mimo że komunikacja szeregowa jest stosunkowo prosta, protokół PPP jest nieco złożony. Protokół PPP w rzeczywistości składa się z wielu protokołów, takich jak protokół kontroli linków (LCP), IpCP (Internet Protocol Control Protocol), Password Authentication Protocol (PAP) i Challenge-Handshake Authentication Protocol (CHAP). Punkt połączenia sieciowego jest głównym protokołem dla protokołu PPP. W tym miejscu są dynamicznie negocjowane podstawowe składniki łącza w sposób równorzędny. Po pomyślnym wynegocjowania podstawowych cech połączenia protokół PAP i/lub CHAP są używane w celu zapewnienia prawidłowego połączenia równorzędnego. Jeśli obie sieci równorzędne są prawidłowe, ipcp jest następnie używany do negocjowania adresów IP używanych przez równorzędnych. Po zakończeniu procesu IPCP protokół PPP będzie mógł wysyłać i odbierać pakiety IP.

NetX widoki PPP głównie jako sterownik urządzenia. Funkcja *nx_ppp_driver* jest dostarczana do funkcji tworzenia adresu IP NetX, *nx_ip_create*. W przeciwnym razie NetX nie ma bezpośredniej wiedzy na temat protokołu PPP.

## <a name="ppp-serial-communication"></a>Komunikacja szeregowa PPP

Pakiet NETX PPP wymaga, aby aplikacja dostarczała sterownik komunikacji szeregowej. Sterownik musi obsługiwać znaki 8-bitowe i może również stosować sterowanie przepływem oprogramowania. Aplikacja odpowiada za zainicjowanie sterownika, co należy wykonać przed utworzeniem wystąpienia PROTOKOŁU PPP.

Aby wysyłać pakiety PPP, należy podać procedurę bajtów wyjściowych sterownika szeregowego do protokołu PPP (określoną w *nx_ppp_create* funkcji). Ta procedura danych wyjściowych bajtów sterownika szeregowego będzie wywoływana powtarzalnie w celu przesyłania całego pakietu PPP. Sterownik szeregowy jest odpowiedzialny za buforowanie danych wyjściowych. Po stronie odbierania sterownik szeregowy aplikacji musi wywołać funkcję *nx_ppp_byte_receive* PPP za każdym razem, gdy pojawi się nowy bajt. Zwykle odbywa się to w kontekście procedury usługi przerwań (ISR, Interrupt Service Routine). Funkcja *nx_ppp_byte_receive* umieszcza bajt przychodzący w buforze cyklicznym i powiadamia protokół PPP o jego obecności.

## <a name="ppp-over-ethernet-communication"></a>Komunikacja za pośrednictwem protokołu PPP przez Sieć Ethernet

NetX PPP może również przesyłać komunikat PPP za pośrednictwem sieci Ethernet. W takiej sytuacji pakiet PPP NetX wymaga, aby aplikacja dostarczała sterownik komunikacji Ethernet.

Aby wysyłać pakiety PPP za pośrednictwem sieci Ethernet, należy podać procedurę wyjściową do protokołu PPP (określoną w *nx_ppp_packet_send_set* protokołu ). Ta procedura wyjściowa będzie wywoływana powtarzalnie w celu przesyłania całego pakietu PPP. Po stronie odbierania odbiornik aplikacji musi wywołać funkcję PPP *nx_ppp_packet_receive* przy każdym przychodzącym nowym pakiecie.

## <a name="ppp-packet"></a>Pakiet PPP

Protokół PPP używa ramek AHDLC (podzestawu HDLC) do hermetyzacji całej kontroli protokołu PPP i danych użytkownika. Ramka AHDLC wygląda następująco:

|**Flaga**|**Addr**|**Ctrl**|**Informacje**|**Crc**|**Flaga**|
|--------|--------|--------|---------------|-------|--------|
|7E |Ff|03|[0–1502 bajty]|2-bajtowy| 7E|

Każda ramka PPP ma taki ogólny wygląd. Pierwsze dwa bajty pola informacji zawierają typ protokołu PPP. Prawidłowe wartości są zdefiniowane w następujący sposób:

- C021: LCP
- 8021: IPCP
- C023: PAP
- C223: CHAP
- 0021: Pakiet danych IP

Jeśli typ 0x0021 jest obecny, pakiet IP następuje natychmiast. W przeciwnym razie, jeśli istnieje jeden z innych protokołów, następujące bajty odpowiadają konkretnemu protokołowi.

W celu zapewnienia unikatowego 0x7E znaczników początku/końca ramki oraz obsługi sterowania przepływem oprogramowania, program AHDLC używa sekwencji ucieczki do reprezentowania różnych wartości bajtów. Wartość 0x7D określa, że następujący znak jest kodowany, czyli zasadniczo oryginalny znak wyłączny ORed z 0x20. Na przykład wartość 0x03 pola Ctrl w nagłówku jest reprezentowana przez sekwencję dwóch bajtów: 7D 23. Domyślnie wartości mniejsze niż 0x20 są konwertowane na sekwencję ucieczki, a także wartości 0x7E i 0x7D w polu Informacje. Należy pamiętać, że sekwencje ucieczki mają również zastosowanie do pola CRC.

## <a name="link-control-protocol-lcp"></a>protokół kontroli linków (LCP)

Punkt połączenia sieciowego jest podstawowym protokołem PPP i jest pierwszym protokołem do uruchomienia. Protokół LCP jest odpowiedzialny za negocjowanie różnych parametrów PPP, w tym maksymalnej jednostki odbierania (MRU) i protokołu uwierzytelniania (PAP, CHAP lub none) do użycia. Gdy obie strony protokołu LCP uzgodnią parametry PROTOKOŁU PPP, protokoły uwierzytelniania — jeśli są — rozpocznij działanie.

## <a name="password-authentication-protocol-pap"></a>Protokół uwierzytelniania haseł (PAP)

PAP to stosunkowo prosty protokół, który opiera się na nazwie i hasłach dostarczanych przez jedną stronę połączenia (negocjowane podczas LCP). Druga strona następnie weryfikuje te informacje. Jeśli to prawda, komunikat akceptacji jest zwracany do nadawcy, a protokół PPP może przejść do maszyny stanu IPCP. W przeciwnym razie, jeśli nazwa lub hasło są nieprawidłowe, połączenie zostanie odrzucone.

>[!NOTE]
> Obie strony interfejsu mogą żądać certyfikatu PAP, ale pap jest zwykle używana tylko w jednym kierunku.

## <a name="challenge-handshake-authentication-protocol-chap"></a>Challenge-Handshake uwierzytelniania (CHAP)

Protokół CHAP jest bardziej złożonym protokołem uwierzytelniania niż PAP. Wystawca uwierzytelniacza PROTOKOŁU CHAP dostarcza swój elementu równorzędnego z nazwą i wartością. Następnie element równorzędny używa podanej nazwy, aby znaleźć wspólny "klucz tajny" między dwiema jednostkami. Obliczenia są następnie wykonywane na identyfikatorze, wartości i "kluczu tajnym". Wynik tego obliczenia jest zwracany w odpowiedzi. Jeśli jest to poprawne, protokół PPP może przejść do maszyny stanu IPCP. W przeciwnym razie, jeśli wynik jest niepoprawny, połączenie zostanie odrzucone.

Innym interesującym aspektem protokołu CHAP jest to, że może on wystąpić w losowych odstępach czasu po nawiązaniu połączenia. Służy to do zapobiegania przejmowaniu połączenia — po jego uwierzytelnieniu. Jeśli wyzwanie zakończy się niepowodzeniem w jednym z tych losowych czasów, połączenie zostanie natychmiast przerwane.

>[!NOTE]
> Obie strony interfejsu mogą żądać protokołu CHAP, ale protokół CHAP jest zwykle używany tylko w jednym kierunku.

## <a name="internet-protocol-control-protocol-ipcp"></a>Protokół IPCP (Internet Protocol Control Protocol)

IPCP jest ostatnim protokołem do wykonania, zanim komunikacja PPP będzie dostępna dla transferu danych NETX IP. Głównym celem tego protokołu jest poinformowanie drugiego elementu równorzędnego o jego adresie IP. Po konfiguracji adresu IP transfer danych NETX IP jest włączony.

## <a name="data-transfer"></a>Transfer danych

Jak wspomniano wcześniej, pakiety danych NETX IP znajdują się w ramkach PPP z identyfikatorem protokołu 0x0021. Wszystkie odebrane pakiety danych są umieszczane w co najmniej jednej NX_PACKET i przesyłane do przetwarzania odbierania NetX. Podczas transmisji zawartość pakietu NetX jest umieszczana w ramce AHDLC i przesyłana.

## <a name="ppp-rfcs"></a>RFC PPP

NetX PPP jest zgodny ze specyfikacjami RFC1332, RFC1334, RFC1661, RFC1994 i powiązanymi RFC.