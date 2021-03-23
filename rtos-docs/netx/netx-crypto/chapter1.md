---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Crypto
description: Kryptografia NetX to wysoce wydajna implementacja algorytmów kryptograficznych w czasie rzeczywistym zaprojektowana w celu zapewnienia usług szyfrowania i uwierzytelniania danych.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0bde9be472584308894cfd702ccd014578afe753
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821499"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Crypto

Usługa Azure RTO NetX Cryptographic to implementacja algorytmów kryptograficznych w czasie rzeczywistym w celu zapewnienia usług szyfrowania i uwierzytelniania danych. Kryptografia NetX została zaprojektowana w celu podłączenia do modułów NetX Secure TLS, DTLS i IPsec. Aplikacje mogą również używać kryptografii NetX jako autonomicznego modułu poza zabezpieczeniami sieci.

## <a name="netx-crypto-unique-features"></a>NetX funkcje kryptograficzne

Kryptografia NetX jest implementowana w standardowym języku C (C99), zgodnym z praktycznie wszystkimi kompilatorami C/C++. Jego Modularna konstrukcja umożliwia aplikacji łączenie tylko z algorytmami kryptograficznymi, które muszą zostać użyte, a tym samym osiągnięcie minimalnego rozmiaru kodu. Implementacja została zaprojektowana tak, aby działała z większością mikroprocesorów 32-bitowych i używa tylko podstawowych operacji matematycznych (dodawania, odejmowania, mnożenia, dzielenia, logicznego i lub bitowego przesunięcia). Wszystkie te operacje są używane z 32-bitowymi ilościami, dzięki czemu Kryptografia NetX jest przenośna przez większość mikroprocesorów 32-bitowych. Implementacja jest ściśle zoptymalizowana pod kątem uruchamiania w ograniczonych mikroprocesorach zasobów, ukierunkowanych na aplikacje głęboko osadzone.

## <a name="algorithms-supported-by-netx-crypto"></a>Algorytmy obsługiwane przez kryptografię NetX

Kryptografia NetX obsługuje następujące algorytmy kryptograficzne. Kryptografia NetX jest zgodna ze wszystkimi ogólnymi zaleceniami i podstawowymi wymaganiami w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym i platform wymagających niewielkiej ilości pamięci i wydajnego wykonania.

| Algorytm       | Długość klucza (bity)      |
| --------------- | ---------------------- |
| AES (CBC, ROB)   | 128, 192, 256          |
| AES (XCBC)       | 128                    |
| AES — CCM 8       | 128                    |
| ALGORYTM 3DES (CBC)       | 192                    |
| HMAC-SHA1       | Dowolna Długość             |
| HMAC-SHA224     | Dowolna Długość             |
| HMAC-SHA256     | Dowolna Długość             |
| HMAC-SHA384     | Dowolna Długość             |
| HMAC-SHA512     | Dowolna Długość             |
| HMAC-SHA512/224 | Dowolna Długość             |
| HMAC-SHA512/256 | Dowolna Długość             |
| HMAC-MD5        | Dowolna Długość             |
| RSA             | 1024, 2048, 3072, 4096 |

| Algorytm       | Długość podsumowania (bity) | Rozmiar bloku (bity) |
| --------------- | -------------------- | ----------------- |
| SHA1            | 160                  | 512               |
| SHA224          | 224                  | 512               |
| SHA256          | 256                  | 512               |
| SHA384          | 384                  | 1024              |
| SHA512          | 512                  | 1024              |
| MD5             | 128                  | 512               |
| HMAC-SHA1       | 160                  | 512               |
| HMAC-SHA224     | 224                  | 512               |
| HMAC-SHA256     | 256                  | 512               |
| HMAC-SHA384     | 384                  | 1024              |
| HMAC-SHA512     | 512                  | 1024              |
| HMAC-SHA512/224 | 224                  | 1024              |
| HMAC-SHA512/256 | 256                  | 1024              |
| HMAC-MD5        | 128                  | 512               |
| Krzywa eliptyczna  | P192/224/256/384/521 |                   |

## <a name="netx-crypto-requirements"></a>Wymagania kryptograficzne NetX

TBD: wymaganie dotyczące pamięci... Przerwanie/ponowne użytkowanie z sejfem? Wymaga dyskusji

## <a name="netx-crypto-constraints"></a>NetX ograniczenia kryptograficzne

Brak.
