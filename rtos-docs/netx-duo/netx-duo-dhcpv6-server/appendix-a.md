---
title: Dodatek A — kody opcji protokołu DHCPv6 platformy Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich kodów opcji protokołu DHCPv6 NetX Duo
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 36d673c34479ec2d476eeaa094c0dc02714ee010
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821967"
---
# <a name="appendix-a--azure-rtos-netx-duo-dhcpv6-option-codes"></a>Dodatek A — kody opcji protokołu DHCPv6 platformy Azure RTO NetX Duo

| Opcja              | Kod            | Opis |
| ------------------- | ------------------- | --------------- |
| Identyfikator DUID identyfikatora klienta | 1 | Unikatowy identyfikator hosta klienta w sieci |
| Identyfikator serwera (DUID) | 2 | Unikatowy identyfikator hosta DHCPv6Server w sieci |
| Skojarzenie tożsamości dla adresów innych niż tymczasowe (IANA) | 3 | Parametry dla przypisania nie tymczasowego adresu IP |
| Skojarzenie tożsamości dla adresów tymczasowych (IATA) | 4 | Parametry przydziału tymczasowego adresu IP |
| Adres IA | 5 | Rzeczywisty adres IPv6 i okresy istnienia adresów IPv6, które mają być przypisane do klienta |
| Żądanie opcji | 6 | Lista żądań informacji w celu uzyskania informacji sieciowych, takich jak serwer DNS i inne parametry konfiguracji sieci. |
| Równy | 7 | Uwzględniono w komunikacie anonsowania serwera klientowi wpływ na wybór serwerów przez klienta. Klient musi wybrać serwer o wyższej wartości preferencji na innych serwerach. 255 jest wartością maksymalną, natomiast zero oznacza, że klient może wybrać dowolny serwer odpowiadający na nie |
| Czas, który upłynął | 8 | Zawiera czas (0,01 w sekundach), po którym klient inicjuje wymianę DHCPv6 z serwerem. Używane przez serwery pomocnicze w celu ustalenia, czy serwer podstawowy odpowiada na żądanie klienta. |
| Komunikat przekaźnika | 9 | Zawiera oryginalną wiadomość w komunikacie przekazywania | 
| Authentication | 11 | Zawiera informacje do uwierzytelniania tożsamości i zawartości komunikatów protokołu DHCPv6 |
| Serwer emisji pojedynczej | 12 | Serwer wysyła tę opcję, aby umożliwić klientowi określenie, że serwer będzie akceptować komunikaty emisji pojedynczej bezpośrednio z klienta zamiast multiemisji. |

Opcje IATA, Message Relay, Authentication i Server unicast nie są obsługiwane w tej wersji serwera DHCPv6 NetX Duo. Bieżący kod opcji protokołu DHCPv6 10 jest pozostawiony niezdefiniowany w dokumencie RFC 3315.