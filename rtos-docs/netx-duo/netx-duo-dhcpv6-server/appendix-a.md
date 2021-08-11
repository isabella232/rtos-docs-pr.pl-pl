---
title: Dodatek A — Azure RTOS opcji NetX Duo DHCPv6
description: Ten rozdział zawiera opis wszystkich kodów opcji DHCPv6 netx Duo
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 58b6e36fab4de02a9fb973894500a48f2656809ec2baa3dfc65fcd80ae33b832
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791837"
---
# <a name="appendix-a--azure-rtos-netx-duo-dhcpv6-option-codes"></a>Dodatek A — Azure RTOS opcji NetX Duo DHCPv6

| Opcja              | Kod            | Opis |
| ------------------- | ------------------- | --------------- |
| Identyfikator klienta DUID | 1 | Unikatowo identyfikuje hosta klienta w sieci |
| Identyfikator serwera (DUID) | 2 | Unikatowo identyfikuje hosta DHCPv6Server w sieci |
| Skojarzenie tożsamości dla adresów innych niż tymczasowe (IANA) | 3 | Parametry nie tymczasowego przypisania adresu IP |
| Skojarzenie tożsamości dla adresów tymczasowych (IATA) | 4 | Parametry tymczasowego przypisania adresu IP |
| Adres IA | 5 | Rzeczywiste okresy istnienia adresów IPv6 i IPv6, które mają być przypisane do klienta |
| Żądanie opcji | 6 | Lista żądań informacji w celu uzyskania informacji o sieci, takich jak serwer DNS i inne parametry konfiguracji sieci. |
| Preferencji | 7 | Zawarte w serwerze Anonsowanie komunikatu klientowi, aby wpłynąć na wybór serwerów przez klienta. Klient musi wybrać serwer z wyższą wartością preferencji niż inne serwery. 255 to wartość maksymalna, a zero oznacza, że klient może wybrać dowolny serwer, który odpowiada |
| Czas | 8 | Zawiera czas (w 0,01 sekundy), kiedy klient inicjuje wymiany DHCPv6 z serwerem. Używany przez serwera pomocnicze do określenia, czy serwer podstawowy odpowiada w czasie na żądanie klienta. |
| Komunikat przekaźnika | 9 | Zawiera oryginalny komunikat w komunikacie usługi Relay | 
| Authentication | 11 | Zawiera informacje na temat uwierzytelniania tożsamości i zawartości komunikatów DHCPv6 |
| Emisja pojedyncza serwera | 12 | Serwer wysyła tę opcję, aby klient wiedział, że serwer będzie akceptować komunikaty emisji pojedynczej bezpośrednio z klienta zamiast multiemisji. |

Opcje IATA, Komunikat przekaźnika, Uwierzytelnianie i Emisja pojedyncza serwera nie są obsługiwane w tej wersji serwera NetX Duo DHCPv6. Bieżący kod opcji protokołu DHCPv6 10 pozostaje niezdefiniowany w dokumencie RFC 3315.