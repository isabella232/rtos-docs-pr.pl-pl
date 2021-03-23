---
title: Dodatek B — kody stanu serwera DHCPv6 usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich kodów stanu serwera DHCPv6 NetX Duo
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c79a0c0bc9acfcfca69c7333d30cd7cab35ba5f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821961"
---
# <a name="appendix-b---azure-rtos-netx-duo-dhcpv6-server-status-codes"></a>Dodatek B — kody stanu serwera DHCPv6 usługi Azure RTO NetX Duo

| Nazwa              | Kod            | Opis |
| ------------------- | ------------------- | --------------- |
| Powodzenie | 0 | Powodzenie |
| Nieokreślony błąd | 1 | Niepowodzenie, przyczyna nieokreślona; Ten kod stanu jest ustawiany przez serwer w celu wskazania ogólnego błędu podczas udzielania żądania klienta niezgodnego z innymi kodami |
| Brak dostępnego adresu | 2 | Serwer nie ma żadnych adresów dostępnych do przypisania do klienta |
| NoBinding | 3 | Adres IA klienta (Binding) nie jest dostępny, np. żądany adres IP nie jest dostępny dla serwera do dzierżawy lub przypisany innemu klientowi. |
| NotOnLink | 4 | Prefiks adresu wskazuje, że adres IP nie jest adresem linku |
| UseMulticast | 5 | Wysyłany przez serwer w odpowiedzi na odebranie komunikatu klienta przy użyciu adresu emisji pojedynczej serwera zamiast adresu multiemisji *All_DHCP_Relay_Agents_and_Servers* |