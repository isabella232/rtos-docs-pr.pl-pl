---
title: Rozdział 1 — Wprowadzenie do bezpiecznego Azure RTOS DTLS netx
description: Azure RTOS NetX Secure DTLS to implementacja protokołu Datagram Transport Layer Security przeznaczona dla osadzonych aplikacji opartych na technologii ThreadX w czasie rzeczywistym.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a7fe51fd1e141c0c525a98986ca3058732b61843f8bd79bf24fc5ac986147501
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797045"
---
# <a name="chapter-1-introduction-to-azure-rtos-netx-secure-dtls"></a>Rozdział 1: Wprowadzenie do bezpiecznego Azure RTOS DTLS netx

Azure RTOS NetX Secure DTLS to implementacja protokołu Datagram Transport Layer Security w czasie rzeczywistym o wysokiej wydajności przeznaczona wyłącznie dla osadzonych aplikacji opartych na technologii ThreadX. Ten rozdział zawiera wprowadzenie do bezpiecznego dtls NetX oraz opis jego aplikacji i korzyści.

## <a name="netx-secure-unique-features"></a>NetX Secure Unique Features

W przeciwieństwie do większości innych implementacji TLS/DTLS, oprogramowanie NetX Secure zostało zaprojektowane od podstaw w celu obsługi szerokiej gamy osadzonych platform sprzętowych i łatwo skaluje się od małych aplikacji mikrokontrolerów po najbardziej zaawansowane procesory osadzone. Kod jest napisany z myślą o ograniczonych zasobach systemów osadzonych i udostępnia szereg opcji konfiguracji w celu zmniejszenia ilości pamięci potrzebnej do zapewnienia bezpiecznej komunikacji sieciowej za pośrednictwem TLS lub DTLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFC obsługiwane przez NetX Secure

NetX Secure obsługuje następujące protokoły związane z protokołami TLS i DTLS. Lista nie musi być wyczerpująca, ponieważ istnieje wiele RFC związanych z TLS/DTLS i kryptografią. NetX Secure jest zgodny ze wszystkimi ogólnymi zaleceniami i podstawowymi wymaganiami w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym, z małym zużyciem pamięci i wydajnym wykonywaniem.


| RFC | Opis |
| --- | ----------- |
| RFC 6347 | Datagram Transport Layer Security wersji 1.2. |
| RFC 2246 | Protokół TLS w wersji 1.0|
| RFC 4346 | Protokół Transport Layer Security (TLS) w wersji 1.1 |
| RFC 5246 | Protokół Transport Layer Security (TLS) w wersji 1.2 |
| RFC 5280 | X.509 Certyfikaty PKI (wersja 3) |
| RFC 3268 | Advanced Encryption Standard (AES) Ciphersuites for Transport Layer Security (TLS) |
| RFC 3447 | Public-Key Cryptography Standards (PKCS) #1: RSA Cryptography Specifications Version 2.1 (Specyfikacje kryptografii RSA w wersji 2.1) |
| RFC 2104 | HMAC: Keyed-Hashing do uwierzytelniania komunikatów |
| RFC 6234 | US Secure Hash Algorithms (SHA and SHA-based HMAC and HKDF) |
| RFC 4279 | Pre-Shared Key Ciphersuites for TLS |

## <a name="netx-secure-dtls-requirements"></a>Wymagania bezpiecznego dtls netx

Aby zapewnić prawidłowe działanie, biblioteka środowisk uruchomieniowych NetX Secure wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto w zależności od aplikacji będzie wymagany co najmniej jeden certyfikat cyfrowy X.509 zakodowany w formacie DER w celu zidentyfikowania wystąpienia TLS/DTLS lub zweryfikowania certyfikatów pochodzących z hosta zdalnego. Pakiet NetX Secure nie ma dodatkowych wymagań.

## <a name="netx-secure-dtls-constraints"></a>NetX Secure DTLS Constraints

Protokół NetX Secure DTLS implementuje wymagania standardu RFC 6347 dla protokołu DTLS 1.2. Istnieją jednak następujące ograniczenia:

1. Ze względu na charakter urządzeń osadzonych niektóre aplikacje mogą nie mieć zasobów do obsługi maksymalnego rozmiaru rekordu TLS/DTLS 16 KB. NetX Secure może obsługiwać 16 KB rekordów na urządzeniach z wystarczającymi zasobami.
2. Minimalna weryfikacja certyfikatu. Usługa NetX Secure wykona podstawową weryfikację łańcuchową X.509 na certyfikacie, aby upewnić się, że certyfikat jest prawidłowy i podpisany przez zaufany urząd certyfikacji, i może podać nazwę pospolitą certyfikatu dla aplikacji do porównania z nazwą domeny Top-Level hosta zdalnego. Jednak odpowiedzialność za weryfikację rozszerzeń certyfikatów i innych danych spoczywa na implementatorze aplikacji.
3. Kryptografia oparta na oprogramowaniu intensywnie obciąża procesor. Procedury kryptograficzne oparte na oprogramowaniu NetX Secure zostały zoptymalizowane pod kątem wydajności, ale w zależności od mocy procesora docelowego ta wydajność może skutkować bardzo długimi operacjami. Gdy kryptografia oparta na sprzęcie jest dostępna, powinna być używana w celu uzyskania optymalnej wydajności bezpiecznego szyfrowania DTLS NetX.
