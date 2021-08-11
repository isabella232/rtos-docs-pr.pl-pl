---
title: Rozdział 1 — Wprowadzenie do Azure RTOS NetX Secure
description: Ten rozdział zawiera wprowadzenie do Azure RTOS NetX Secure oraz opis jego aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d6b0f23d7353626f340fe0ab93ee1e04800edaaa1f00da49afd83f84339df86
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791605"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-secure"></a>Rozdział 1 — Wprowadzenie do Azure RTOS NetX Secure

Azure RTOS NetX Secure to implementacja kryptograficznych standardów zabezpieczeń sieci w czasie rzeczywistym o wysokiej wydajności, w tym protokołów TLS/SSL przeznaczonych wyłącznie dla osadzonych aplikacji opartych na threadX. Ten rozdział zawiera wprowadzenie do usługi NetX Secure oraz opis jej aplikacji i korzyści.

## <a name="netx-secure-unique-features"></a>NetX Secure Unique Features

W przeciwieństwie do większości innych implementacji TLS, zabezpieczenia NetX Secure zostały zaprojektowane od podstaw w celu obsługi szerokiej gamy osadzonych platform sprzętowych i łatwego skalowania od małych aplikacji mikrokontrolerów po najbardziej zaawansowane dostępne procesory osadzone. Kod jest napisany z myślą o ograniczonych zasobach systemów osadzonych i udostępnia szereg opcji konfiguracji w celu zmniejszenia ilości pamięci potrzebnej do zapewnienia bezpiecznej komunikacji sieciowej za pośrednictwem TLS.

## <a name="rfcs-supported-by-netx-secure"></a>RFC obsługiwane przez NetX Secure 

NetX Secure obsługuje następujące protokoły związane z protokołem TLS. Lista nie musi być wyczerpująca, ponieważ istnieje wiele RFC odnoszących się do szyfrowania TLS i kryptografii. NetX Secure jest zgodny ze wszystkimi ogólnymi zaleceniami i podstawowymi wymaganiami w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym, z małym zużyciem pamięci i wydajnym wykonywaniem.

| RFC      | Opis                                                                                                 | Strona |
|----------|-------------------------------------------------------------------------------------------------------------|------|
| RFC 2104 | HMAC: Keyed-Hashing do uwierzytelniania komunikatów                                                              | 33   |
| RFC 2246 | Protokół TLS w wersji 1.0                                                                                | 19   |
| RFC 3268 | Advanced Encryption Standard (AES) Ciphersuites for Transport Layer Security (TLS)                          | 31   |
| RFC 3447 | Public-Key Cryptography Standards (PKCS) #1: RSA Cryptography Specifications Version 2.1 (Specyfikacje kryptografii RSA w wersji 2.1)                    | 32   |
| RFC 4279 | Pre-Shared Key Ciphersuites for TLS                                                                         | 39   |
| RFC 4346 | Protokół Transport Layer Security (TLS) w wersji 1.1                                                     | 19   |
| RFC 5246 | Protokół Transport Layer Security (TLS) w wersji 1.2                                                     | 19   |
| RFC 5280 | X.509 Certyfikaty PKI (wersja 3)                                                                                 | 41   |
| RFC 5746 | Transport Layer Security (TLS) Renegotiation Indication Extension                                           |      |
| RFC 5869 | Funkcja wyodrębniania i rozwijania klucza oparta na HMAC (HKDF)                                                | 19   |
| RFC 6066<sup>1</sup> | Transport Layer Security (TLS): definicje rozszerzeń                                            | 19   |
| RFC 6234 | Us Secure Hash Algorithms (SHA i SHA oparte na HMAC i HKDF)                                                 | 33   |
| RFC 8443 | Pakiety szyfrowania kryptografii krzywej eliptycznej (ECC) dla Transport Layer Security (TLS) w wersji 1.2 i starszych |      |
| RFC 8446 | Protokół Transport Layer Security (TLS) w wersji 1.3                                                     | 19   |

1. Od wersji 6.0 tylko rozszerzenie Oznaczanie nazwy serwera (SNI) z wersji RFC 6066 jest w pełni obsługiwane.

## <a name="netx-secure-requirements"></a>NetX Secure Requirements

Aby biblioteka środowisk uruchomieniowych NetX Secure działała prawidłowo, wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto w zależności od aplikacji będzie wymagany co najmniej jeden certyfikat cyfrowy X.509 zakodowany w formacie DER w celu zidentyfikowania wystąpienia TLS lub zweryfikowania certyfikatów pochodzących z hosta zdalnego. Pakiet NetX Secure nie ma dodatkowych wymagań.

## <a name="netx-secure-constraints"></a>NetX Secure Constraints

Protokół NetX Secure implementuje wymagania standardu RFC 5246 dla protokołów TLS 1.2 i RFC 8446 dla protokołu TLS 1.3, a także zapewnia opcjonalną (domyślnie wyłączono) zgodność z poprzednimi wersjami z RFC 4346 (TLS 1.1) i 2246 (TLS 1.0). Istnieją jednak następujące ograniczenia:

- W przypadku szyfrowania TLS 1.2 i TLS 1.3 obsługiwane są tylko szyfry używające szyfrowania SHA-256. W wersjach wcześniejszych niż TLS 1.2, uściślić TLS używa stałej procedury wyznaczania wartości skrótu, aby sprawdzić, czy komunikaty uściślinia TLS nie zostały naruszone. Począwszy od wersji 1.2, uściślić używa procedury skrótu dostarczonej z szyfru. TLS nie wie z wyprzedzeniem, jaka procedura wyznaczania wartości skrótu zostanie użyta, i musi buforować komunikaty uściśleń. Po naprawiniu skrótu do algorytmu SHA-256 funkcja NetX Secure TLS może działać z mniejszą pamięcią RAM niż inne implementacje TLS. To ograniczenie zostanie usunięte w przyszłej wersji po prawidłowym usunięciu użycia pamięci. *WAŻNA UWAGA: To ograniczenie dotyczy **tylko** wyboru szyfrowania. Podpisy certyfikatów X.509 nie podlegają tym samym ograniczeniom i można użyć dowolnej z obsługiwanych procedur wyznaczania wartości skrótu.
- Ze względu na charakter urządzeń osadzonych niektóre aplikacje mogą nie mieć zasobów do obsługi maksymalnego rozmiaru rekordu TLS 16 KB. NetX Secure może obsługiwać rekordy 16 KB na urządzeniach z wystarczającą ilość zasobów. Bufor ponownego zestawu TLS (zobacz dokumentacja interfejsu API dla interfejsu *nx_secure_tls_session_packet_buffer_set* **)** może być ustawiony na rozmiar mniejszy niż 16 KB na ryzyko problemów ze współdziałaniem. Jeśli zostanie odebrany prawidłowy rekord TLS, który jest większy niż bufor ponownego zassembly, bezpieczny TLS netx przerwać sesję TLS z błędem. Ogólnie rzecz biorąc, bufor powinien być zawsze ustawiony na co najmniej 18 KB (rozmiar rekordu TLS 16 KB + 2 KB dla wypełnienia szyfrowania) i powinien być mniejszy tylko w kontrolowanych ustawieniach (np. host zdalny gwarantuje maksymalny rozmiar rekordu TLS).
  > [!NOTE]
  > Ogólnie rzecz biorąc bufor ponownego zsadu pakietów nigdy nie powinien być mniejszy niż maksymalny rozmiar rekordu protokołu TLS. Jeśli jednak charakterystyka hosta zdalnego jest dobrze znana (np. w systemie całkowicie zamkniętym), można zmniejszyć rozmiar, aby odzyskać część miejsca w pamięci RAM.
- Minimalna weryfikacja certyfikatu. Usługa NetX Secure wykona podstawową weryfikację łańcuchową X.509 na certyfikacie, aby upewnić się, że certyfikat jest prawidłowy i podpisany przez zaufany urząd certyfikacji, oraz może podać nazwę pospolitą certyfikatu dla aplikacji do porównania z nazwą domeny Top-Level hosta zdalnego. Jeśli zegar czasu rzeczywistego jest dostępny, może służyć do weryfikowania daty wygaśnięcia certyfikatu (zobacz Api nx_secure_tls_session_time_function_set). Jednak za weryfikację rozszerzeń certyfikatów i innych danych odpowiada implementator aplikacji.
- Kryptografia oparta na oprogramowaniu intensywnie obciąża procesor. Programowe procedury kryptograficzne NetX Secure zostały zoptymalizowane pod kątem wydajności, ale w zależności od mocy procesora docelowego ta wydajność może spowodować bardzo długie operacje. Gdy kryptografia oparta na sprzęcie jest dostępna, powinna być używana w celu uzyskania optymalnej wydajności bezpiecznego szyfrowania TLS NetX.
- Fragmentacja rekordu uściślniania TLS nie jest obsługiwana. Jeśli niektóre komunikaty rekordu uściślniania TLS są zbyt duże, mogą zostać podzielone między wiele rekordów TLS — zabezpieczenia NetX TLS obecnie traktują to jako błąd. Wymagania dotyczące pamięci dla systemów osadzonych oznaczają, że komunikat z większym rekordem handshake prawdopodobnie nie może być obsłużony mimo to, ale ograniczenie może prowadzić do błędów podczas komunikacji z niektórymi hostami TLS, które używają zbyt dużych łańcuchów certyfikatów.
- Serwer TLS nie obsługuje dynamicznego wyboru certyfikatów, jeśli w magazynie lokalnym istnieje wiele certyfikatów. 
- Nie zaobserwowano typu X509 Certificate KeyUsage. 
- Szyfry oparte na ecDH nie są obsługiwane. Zamiast tego użyj ecdhe.
