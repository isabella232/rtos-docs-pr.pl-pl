---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Crypto
description: NetX Crypto to wysoko wydajnościowa implementacja algorytmów kryptograficznych zaprojektowanych w czasie rzeczywistym w celu zapewnienia usług szyfrowania i uwierzytelniania danych.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1b5ee0336ba9e867a628dc5db4f0c029f68ff45c81d68ceb6299e3469d5e2b49
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796807"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Crypto

Azure RTOS NetX Crypto to implementacja algorytmów kryptograficznych o wysokiej wydajności w czasie rzeczywistym, która zapewnia usługi szyfrowania i uwierzytelniania danych. Oprogramowanie NetX Crypto zostało zaprojektowane pod kątem wtyczek dla modułów NetX Secure TLS, DTLS i IPsec. Aplikacje mogą również używać usługi NetX Crypto jako autonomicznego modułu poza zabezpieczeniami sieci.

## <a name="netx-crypto-unique-features"></a>Unikatowe funkcje kryptograficzne NetX

Oprogramowanie NetX Crypto jest implementowane w standardowym języku C (C99), zgodnym z praktycznie wszystkimi kompilatorami C/C++. Jej modularna konstrukcja umożliwia aplikacji łączenie tylko z algorytmami kryptograficznymi, których potrzebuje, w związku z tym osiągnięcie minimalnego rozmiaru kodu. Implementacja jest przeznaczona do pracy z większość 32-bitowych mikroprocesorów i używa tylko podstawowych operacji matematycznych (dodawanie, odejmowanie, mnożenie, dzielenie, logiczne AND, OR, NOR i bitowe operacje przesunięcia). Wszystkie te operacje są używane z ilościami 32-bitowymi, dzięki czemu kryptografia NetX jest przenośna w większości 32-bitowych mikroprocesorów. Implementacja jest specjalnie zoptymalizowana pod kątem uruchamiania na mikroprocesorach z ograniczeniami zasobów, przeznaczonych dla aplikacji głęboko osadzonych.

## <a name="algorithms-supported-by-netx-crypto"></a>Algorytmy obsługiwane przez usługę NetX Crypto

Oprogramowanie NetX Crypto obsługuje następujące algorytmy kryptograficzne. Program NetX Crypto jest zgodny ze wszystkimi ogólnymi zaleceniami i podstawowymi wymaganiami w ramach ograniczeń systemu operacyjnego i platform działających w czasie rzeczywistym, które wymagają niewielkiej ilości pamięci i wydajnego wykonywania.

| Algorytm       | Długość klucza (bity)      |
| --------------- | ---------------------- |
| AES(CBC, CTR)   | 128, 192, 256          |
| AES(XCBC)       | 128                    |
| AES-CCM 8       | 128                    |
| 3DES(CBC)       | 192                    |
| HMAC-SHA1       | Dowolna długość             |
| HMAC-SHA224     | Dowolna długość             |
| HMAC-SHA256     | Dowolna długość             |
| HMAC-SHA384     | Dowolna długość             |
| HMAC-SHA512     | Dowolna długość             |
| HMAC-SHA512/224 | Dowolna długość             |
| HMAC-SHA512/256 | Dowolna długość             |
| HMAC-MD5        | Dowolna długość             |
| RSA             | 1024, 2048, 3072, 4096 |

| Algorytm       | Długość skrótu (bity) | Rozmiar bloku (bity) |
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
| Krzywa wielokropka  | P192/224/256/384/521 |                   |

## <a name="netx-crypto-requirements"></a>Wymagania dotyczące kryptografii NetX

TBD: Wymaganie dotyczące pamięci. Przerywanie/ponowne przerywanie bezpieczeństwa? Omówienie potrzeb

## <a name="netx-crypto-constraints"></a>Ograniczenia kryptograficzne NetX

Brak.
