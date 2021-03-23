---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Secure DTLS
description: Usługa Azure RTO NetX Secure DTLS to implementacja protokołu dataTransport Layer Security gramów w czasie rzeczywistym zaprojektowana na potrzeby aplikacji opartych na ThreadX.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbd81082524f50787765dfacf494248dda740fd6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822879"
---
# <a name="chapter-1-introduction-to-azure-rtos-netx-secure-dtls"></a>Rozdział 1: wprowadzenie do usługi Azure RTO NetX Secure DTLS

Usługa Azure RTO NetX Secure DTLS to oparta na czasie rzeczywistym implementacja protokołu datagramów Transport Layer Security, zaprojektowana wyłącznie dla wbudowanych aplikacji opartych na ThreadX. Ten rozdział zawiera wprowadzenie do NetX bezpiecznego DTLS i opis jego aplikacji oraz korzyści.

## <a name="netx-secure-unique-features"></a>NetX bezpieczne funkcje

W przeciwieństwie do większości innych implementacji protokołów TLS/DTLS, ochrona NetX została zaprojektowana od podstaw do obsługi szerokiej gamy wbudowanych platform sprzętowych i umożliwia łatwe skalowanie z małych aplikacji mikrokontrolerów do najbardziej zaawansowanych dostępnych procesorów. Kod jest zapisywana z ograniczoną ilością zasobów osadzonych systemów i udostępnia pewną liczbę opcji konfiguracji w celu zmniejszenia ilości pamięci wymaganej do zapewnienia bezpiecznej komunikacji sieciowej za pośrednictwem protokołu TLS lub DTLS.

## <a name="rfcs-supported-by-netx-secure"></a>Specyfikacje RFC obsługiwane przez NetX Secure

NetX Secure obsługuje następujące protokoły związane z protokołem TLS i DTLS. Lista nie zawsze jest kompletna, ponieważ istnieje wiele dokumentów RFC dotyczących protokołu TLS/DTLS i kryptografii. NetX zabezpieczeń są zgodne ze wszystkimi ogólnymi zaleceniami i podstawowymi wymaganiami w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym z małą ilością pamięci i wydajnym wykonywaniem.


| RFC | Opis |
| --- | ----------- |
| RFC 6347 | Datagram Transport Layer Security w wersji 1,2. |
| RFC 2246 | Protokół TLS w wersji 1,0|
| RFC 4346 | Protokół Transport Layer Security (TLS) w wersji 1,1 |
| RFC 5246 | Protokół Transport Layer Security (TLS) w wersji 1,2 |
| RFC 5280 | Certyfikaty PKI X. 509 (wersja 3) |
| RFC 3268 | Advanced Encryption Standard (AES) Ciphersuites dla Transport Layer Security (TLS) |
| RFC 3447 | #1 standardy kryptografii Public-Key (PKCS): specyfikacje kryptografii RSA w wersji 2,1 |
| RFC 2104 | HMAC: Keyed-Hashing uwierzytelniania komunikatów |
| RFC 6234 | Bezpieczne algorytmy wyznaczania wartości skrótu (algorytmu SHA i algorytmem SHA-based HKDF) |
| RFC 4279 | Ciphersuites klucza wstępnego dla protokołu TLS |

## <a name="netx-secure-dtls-requirements"></a>NetX bezpieczne wymagania DTLS

Aby zapewnić prawidłowe działanie, biblioteka NetX bezpiecznego uruchomieniowego wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto, w zależności od aplikacji, wymagany jest co najmniej jeden certyfikat cyfrowy X. 509 szyfrowany algorytmem DER w celu zidentyfikowania wystąpienia protokołu TLS/DTLS lub zweryfikowania certyfikatów pochodzących z hosta zdalnego. Pakiet bezpieczny NetX nie ma żadnych dalszych wymagań.

## <a name="netx-secure-dtls-constraints"></a>NetX bezpieczne DTLS ograniczenia

Protokół NetX Secure DTLS implementuje wymagania RFC 6347 Standard (s) dla DTLS 1,2. Istnieją jednak następujące ograniczenia:

1. Ze względu na charakter urządzeń osadzonych niektóre aplikacje mogą nie mieć zasobów do obsługi maksymalnego rozmiaru rekordu TLS/DTLS 16 KB. NetX Secure może obsługiwać rekordy 16 KB na urządzeniach z wystarczającą ilością zasobów.
2. Minimalna weryfikacja certyfikatu. NetX Secure będzie przeprowadzać podstawową weryfikację łańcucha X. 509 na certyfikacie, aby upewnić się, że certyfikat jest prawidłowy i podpisany przez zaufany urząd certyfikacji, i może podać nazwę pospolitą certyfikatu dla aplikacji, która będzie porównywana z Top-Level nazwą domeny hosta zdalnego. Jednak weryfikacja rozszerzeń certyfikatów i innych danych jest odpowiedzialna za realizatora aplikacji.
3. Kryptografia oparta na oprogramowaniu jest intensywnym procesorem. NetX bezpieczne procedury kryptograficzne oparte na oprogramowaniu zostały zoptymalizowane pod kątem wydajności, ale w zależności od możliwości procesora docelowego wydajność może spowodować długotrwałe operacje. Gdy kryptografia oparta na sprzęcie jest dostępna, należy ją stosować w celu uzyskania optymalnej wydajności NetX Secure DTLS.
