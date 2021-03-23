---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Secure
description: Ten rozdział zawiera wprowadzenie do usługi Azure RTO NetX Secure oraz opis jej aplikacji i korzyści.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f4c7a97564cd2f702f9887181b36297b42fa492
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821588"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-secure"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Secure

Usługa Azure RTO NetX Secure to oparta na czasie rzeczywistym implementacja standardów zabezpieczeń sieci kryptograficznych, w tym protokołów TLS/SSL przeznaczonych wyłącznie dla wbudowanych aplikacji opartych na ThreadX. Ten rozdział zawiera wprowadzenie do NetX bezpiecznego i opis swoich aplikacji oraz korzyści.

## <a name="netx-secure-unique-features"></a>NetX bezpieczne funkcje

W przeciwieństwie do większości innych implementacji protokołu TLS, NetX Secure została zaprojektowana od podstaw do obsługi szerokiej gamy wbudowanych platform sprzętowych i umożliwia łatwe skalowanie z małych aplikacji mikrokontrolerów do najbardziej zaawansowanych dostępnych procesorów osadzonych. Kod jest zapisywana z ograniczoną ilością zasobów w systemach osadzonych i zawiera szereg opcji konfiguracji w celu zmniejszenia ilości pamięci wymaganej do zapewnienia bezpiecznej komunikacji sieciowej za pośrednictwem protokołu TLS.

## <a name="rfcs-supported-by-netx-secure"></a>Specyfikacje RFC obsługiwane przez NetX Secure 

NetX Secure obsługuje następujące protokoły związane z protokołem TLS. Lista nie zawsze jest kompletna, ponieważ istnieje wiele dokumentów RFC dotyczących protokołu TLS i kryptografii. NetX zabezpieczeń są zgodne ze wszystkimi ogólnymi zaleceniami i podstawowymi wymaganiami w ramach ograniczeń systemu operacyjnego w czasie rzeczywistym z małą ilością pamięci i wydajnym wykonywaniem.

| RFC      | Opis                                                                                                 | Strona |
|----------|-------------------------------------------------------------------------------------------------------------|------|
| RFC 2104 | HMAC: Keyed-Hashing uwierzytelniania komunikatów                                                              | 33   |
| RFC 2246 | Protokół TLS w wersji 1,0                                                                                | 19   |
| RFC 3268 | Advanced Encryption Standard (AES) Ciphersuites dla Transport Layer Security (TLS)                          | 31   |
| RFC 3447 | #1 standardy kryptografii Public-Key (PKCS): specyfikacje kryptografii RSA w wersji 2,1                    | 32   |
| RFC 4279 | Ciphersuites klucza wstępnego dla protokołu TLS                                                                         | 39   |
| RFC 4346 | Protokół Transport Layer Security (TLS) w wersji 1,1                                                     | 19   |
| RFC 5246 | Protokół Transport Layer Security (TLS) w wersji 1,2                                                     | 19   |
| RFC 5280 | Certyfikaty PKI X. 509 (wersja 3)                                                                                 | 41   |
| RFC 5746 | Rozszerzenie wskazania renegocjacji Transport Layer Security (TLS)                                           |      |
| RFC 5869 | Funkcja wyznaczania klucza wyodrębniania i rozwijania opartego na procesorze HMAC (HKDF)                                                | 19   |
| RFC 6066<sup>1</sup> | Rozszerzenia Transport Layer Security (TLS): definicje rozszerzeń                                            | 19   |
| RFC 6234 | Bezpieczne algorytmy wyznaczania wartości skrótu (algorytmu SHA i algorytmem SHA-based HKDF)                                                 | 33   |
| RFC 8443 | Zestawy krzywej eliptyczna Cryptography (ECC) dla Transport Layer Security (TLS) w wersji 1,2 i starszych |      |
| RFC 8446 | Protokół Transport Layer Security (TLS) w wersji 1,3                                                     | 19   |

1. Począwszy od wersji 6,0, tylko rozszerzenie Oznaczanie nazwy serwera (SNI) ze specyfikacji RFC 6066 jest w pełni obsługiwane.

## <a name="netx-secure-requirements"></a>NetX bezpieczne wymagania

Aby zapewnić prawidłowe działanie, biblioteka NetX bezpiecznego uruchomieniowego wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto, w zależności od aplikacji, wymagany jest co najmniej jeden certyfikat cyfrowy X. 509 szyfrowany algorytmem DER w celu zidentyfikowania wystąpienia protokołu TLS lub zweryfikowania certyfikatów pochodzących z hosta zdalnego. Pakiet bezpieczny NetX nie ma żadnych dalszych wymagań.

## <a name="netx-secure-constraints"></a>NetX bezpieczne ograniczenia

Bezpieczny protokół NetX implementuje wymagania RFC 5246 Standard (s) dla protokołów TLS 1,2 i RFC 8446 for TLS 1,3, a także zapewnia opcjonalne (domyślnie wyłączone) zgodność z poprzednimi wersjami ze standardami RFC 4346 (TLS 1,1) i 2246 (TLS 1,0). Istnieją jednak następujące ograniczenia:

- W przypadku protokołu TLS 1,2 i TLS 1,3 są obsługiwane tylko ciphersuites z algorytmem SHA-256. W wersjach wcześniejszych niż TLS 1,2, uzgadnianie TLS używa stałej procedury tworzenia skrótów, aby sprawdzić, czy komunikaty uzgadniania TLS nie zostały naruszone. Począwszy od wersji 1,2, uzgadnianie używa procedury skrótu dostarczonej z ciphersuite. Protokół TLS nie wie przed czasem użycia procedury mieszania i musi buforować komunikaty uzgadniania. Przez naprawianie skrótu do algorytmu SHA-256, NetX Secure TLS może działać z mniejszą ilością pamięci RAM niż inne implementacje protokołu TLS. To ograniczenie zostanie usunięte w przyszłej wersji, gdy będzie można właściwie rozwiązać użycie pamięci. * WAŻNA Uwaga: to ograniczenie dotyczy **tylko** wyboru ciphersuite. Podpisy certyfikatu X. 509 nie podlegają tym samym ograniczeniu i mogą być używane wszystkie obsługiwane procedury skrótów.
- Ze względu na charakter urządzeń osadzonych niektóre aplikacje mogą nie mieć zasobów do obsługi maksymalnego rozmiaru rekordu TLS 16 KB. NetX Secure może obsługiwać rekordy 16 KB na urządzeniach z wystarczającą ilością zasobów. Bufor ponownego asemblowania protokołu TLS (zobacz odwołanie do interfejsu API dla *nx_secure_tls_session_packet_buffer_set*) **może** być ustawiony na wartość mniejszą niż 16 KB w przypadku problemów z współdziałaniem. Jeśli otrzymasz prawidłowy rekord TLS, który jest większy niż bufor ponownego zestawu, NetX Secure TLS spowoduje przerwanie sesji TLS z błędem. Ogólnie rzecz biorąc bufor powinien być zawsze ustawiony na co najmniej 18KB (16 KB protokołu TLS o rozmiarze + 2KB na potrzeby uzupełnienia szyfrowania) i tylko mniejszy w ustawieniach kontrolowanych (np. host zdalny gwarantuje maksymalny rozmiar rekordu TLS).
  > [!NOTE]
  > Ogólnie rzecz biorąc, bufor ponownego zestawu pakietów nigdy nie powinien być mniejszy niż maksymalny rozmiar rekordu TLS. Jeśli jednak właściwości hosta zdalnego są dobrze znane (np. w całkowicie zamkniętym systemie), rozmiar można zmniejszyć, aby odzyskać część pamięci RAM.
- Minimalna weryfikacja certyfikatu. NetX Secure będzie przeprowadzać podstawową weryfikację łańcucha X. 509 na certyfikacie, aby upewnić się, że certyfikat jest prawidłowy i podpisany przez zaufany urząd certyfikacji, i może podać nazwę pospolitą certyfikatu dla aplikacji, która będzie porównywana z Top-Level nazwą domeny hosta zdalnego. Jeśli jest dostępny zegar w czasie rzeczywistym, można go użyć do sprawdzenia daty wygaśnięcia certyfikatu (zobacz Interfejs API nx_secure_tls_session_time_function_set). Jednak weryfikacja rozszerzeń certyfikatów i innych danych jest odpowiedzialna za realizatora aplikacji.
- Kryptografia oparta na oprogramowaniu jest intensywnym procesorem. NetX bezpieczne procedury kryptograficzne oparte na oprogramowaniu zostały zoptymalizowane pod kątem wydajności, ale w zależności od możliwości procesora docelowego wydajność może spowodować długotrwałe operacje. Gdy kryptografia oparta na sprzęcie jest dostępna, należy ją stosować w celu uzyskania optymalnej wydajności usługi NetX Secure TLS.
- Fragmentacja rekordu uzgadniania protokołu TLS nie jest obsługiwana. Jeśli niektóre komunikaty rekordu uzgadniania TLS są zbyt duże, mogą zostać podzielone między wiele rekordów protokołu TLS — NetX Secure TLS jest obecnie traktowany jako błąd. Wymagania dotyczące pamięci dla systemów osadzonych oznaczają, że komunikat o większym uzgadnianiu nie może zostać obsłużony mimo to, ale ograniczenie może prowadzić do błędów podczas komunikacji z niektórymi hostami TLS, które używają nadmiernie dużych łańcuchów certyfikatów.
- Serwer TLS nie obsługuje wyboru certyfikatu dynamicznego, gdy istnieje wiele certyfikatów w magazynie lokalnym. 
- Nie zaobserwowano użycia certyfikatu x509. 
- ECDH ciphersuites nie są obsługiwane. Zamiast tego użyj ECDHE.
