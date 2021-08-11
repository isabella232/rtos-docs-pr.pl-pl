---
title: Dodatek B — Azure RTOS stanu serwera NetX Duo DHCPv6
description: Ten rozdział zawiera opis wszystkich kodów stanu serwera NetX Duo DHCPv6
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8b9795607c0fed80646ee01e36edf4ecd2aaadad7f0a023e6979e123b81e1660
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791775"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a>Dodatek B — Azure RTOS stanu serwera NetX Duo DHCPv6

| Nazwa              | Kod            | Opis |
| ------------------- | ------------------- | --------------- |
| Powodzenie | 0 | Powodzenie |
| Nieokreślony błąd | 1 | Niepowodzenie, przyczyna nieokreślona; Ten kod stanu jest ustawiany przez serwer w celu wskazania ogólnego błędu podczas udzielania żądania klienta, które nie pasuje do innych kodów |
| Dostępny noAddress | 2 | Serwer nie ma dostępnych adresów do przypisania do klienta |
| NoBinding | 3 | Adres IA klienta (powiązanie) jest niedostępny, np. żądany adres IP nie jest dostępny dla serwera do dzierżawy lub przypisany do innego klienta. |
| NotOnLink | 4 | Prefiks adresu wskazuje, że adres IP nie jest adresem linku |
| UseMulticast | 5 | Wysyłane przez serwer w odpowiedzi na odebranie komunikatu klienta przy użyciu adresu emisji pojedynczej serwera zamiast adresu *All_DHCP_Relay_Agents_and_Servers* multiemisji |