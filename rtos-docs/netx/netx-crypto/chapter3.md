---
title: Rozdział 3 — Opis funkcjonalny usługi Azure RTOS NetX Crypto
description: Ten rozdział zawiera opis funkcjonalny usługi NetX Crypto.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8aa49c130dc2802e95620ccdd4f4d9398c3fd2e55f5896d004e47baa72829848
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796754"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a>Rozdział 3 — Opis funkcjonalny usługi Azure RTOS NetX Crypto

## <a name="execution-overview"></a>Omówienie wykonywania

Ten rozdział zawiera opis funkcjonalny usługi Azure RTOS NetX Crypto. Istnieją dwa podstawowe typy wykonywania programu w aplikacji Kryptografia NetX: inicjowanie i wywołania interfejsu aplikacji.

*Biblioteka NetX Crypto może być używana jako autonomiczna biblioteka kryptograficzna lub może być używana z threadX, NetX i/lub NetX Secure.*

## <a name="aes"></a>AES

- **Algorithm Standard:**: NetX Crypto implementuje algorytm AES zgodnie z standardem NIST FIPS 197, który można znaleźć w: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)
- **Obsługiwane długości kluczy:** 128, 192, 256
- **Obsługiwane tryby:**
  - CBC, CTR, (długość klucza 128-, 192-, 256-bitowego)
  - XCBC (tylko 128-bitowa długość klucza),
  - CCM8 (tylko długość klucza 128-bitowa)
- **Wymagania dotyczące pamięci:** aplikacja określa bufor wejściowy i wyjściowy oraz strukturę kontroli AES. Struktura kontroli AES zachowuje stan algorytmu AES między wywołaniami interfejsu API. Bufor wejściowy zawiera dane do zaszyfrowania lub odszyfrowania i może mieć dowolny rozmiar. Bufor wyjściowy jest używany przez system AES do przechowywania danych przetwarzanych przez system AES. Rozmiar buforu wyjściowego nie może być mniejszy niż rozmiar bufora wejściowego i musi być wielokrotnością 16 bajtów, czyli rozmiarem bloku AES. Bufory wejściowe i wyjściowe muszą być pamięcią ciągłą i nie mogą nakładać się na siebie, z wyjątkiem specjalnego przypadku szyfrowania w miejscu (przy użyciu tej samej pamięci dla danych wejściowych i wyjściowych). Podczas szyfrowania w miejscu bufor wyjściowy rozpoczyna się w dokładnie tej samej lokalizacji co bufor wejściowy i nie może być mniejszy niż bufor wejściowy. Gdy szyfrowanie AES działa w miejscu, nie jest wymagana dodatkowa pamięć na potrzeby plików scratch.

## <a name="3des"></a>3DES

- **Algorithm Standard:** NetX Crypto implementuje usługę Tripple DES(TDES, znaną także jako 3DES) zgodnie z publikacją specjalną NIST 800-67 rev 2: *"Recommendataion for the Triple Data Encryption Algorithm (TDES) Block Cipher" (Rekomendacja* szyfrowania blokowego algorytmu TDES), która znajduje się w: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)
- **Obsługiwana długość klucza:** 64 * 3 = 192
- **Requreiment pamięci:**: Brak

W programie NetX Crypto termin "3DES" jest używany zamiennie z "TDES".

## <a name="md5"></a>MD5

- **Algorithm Standard:** NetX Crypto implementuje rozwiązanie MD5 zgodnie ze standardem RFC 1321: *"The MD5 Message-Digest Algorithm"*
- **Wymaganie dotyczące** pamięci: aplikacja musi podać strukturę bloku sterowania MD5 używaną do utrzymywania stanu między operacjami MD5.

## <a name="sha1-sha256512"></a>SHA1, SHA256/512

- **Standard algorytmu:** NetX Crypto implementuje algorytm SHA1/256/512 zgodnie z publikacją NIST FIPS 180-4:*"Secure Hash Standard",* która znajduje się w: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
- **Rozmiar bloku skrótu:**:
  - SHA1: wartość skrótu 160 bitów
  - SHA 224: wartość skrótu 224 bitów
  - SHA 256: wartość skrótu 256 bitów
  - SHA 384: wartość skrótu 384 bitów
  - SHA 512: wartość skrótu 512 bitów
  - SHA 512/224: wartość skrótu 224 bitów
  - SHA 512/256: wartość skrótu 256 bitów

  W programie NetX Crypto procedury SHA256 są używane do algorytmu SHA256 i SHA224. Procedury SHA512 są używane do ręki SHA512, SHA384, SHA512/224 i SHA512/256.
- **Wymaganie dotyczące pamięci:** Aplikacja musi zapewnić strukturę bloku sterowania SHA do utrzymywania stanu między operacjami.

## <a name="rsa"></a>RSA

- **Standardowa:** NetX Crypto implementuje RSA zgodnie ze standardem *" PKCS #1 v2.2: RSA Cryptography Standard*", który jest publikowany jako RFC 8017 i można go również znaleźć w: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)
- **Wymaganie dotyczące pamięci:** Aplikacja musi zapewniać strukturę bloku sterowania RSA do utrzymywania stanu między operacjami i zapewnienia niezbędnego "miejsca buforu na potrzeby obliczeń pośrednich".

## <a name="hmac"></a>Hmac

- **Standardowa:** NetX Crypto implementuje HMAC zgodnie z FIPS PUB 198-1: "*The Keyed-Hash kod uwierzytelniania wiadomości (HMAC)*", który można znaleźć w: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)
- **Wymaganie dotyczące pamięci:** Aplikacja musi zapewnić strukturę bloku sterowania HMAC do utrzymywania stanu między operacjami. Rzeczywisty podany blok sterowania zależy od żądanej podstawowej operacji wyznaczania wartości skrótu (np. SHA1, MD5).

## <a name="elliptic-curve"></a>Krzywa wielokropka

- **Standardowa:** NetX Crypto implementuje krzywą wielokropka. Obsługiwane są nazwane krzywe (tylko pole pierwsze):
  - P-192
  - P-224
  - P-256
  - P-384
  - P-521

   > [!TIP]
   > Format nieskompresowany jest obsługiwany. Zobacz sekcje 2.3.3 i 2.3.4 sec1-v1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)

- **Wymaganie dotyczące pamięci:** Brak

## <a name="ecdsa"></a>Ecdsa

- **Standardowa:** NetX Crypto implementuje ecdsa zgodnie ze standardem FIPS PUB 186-4: "*Digital Signature Standard (DSS),* który można znaleźć w: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)
- **Wymaganie dotyczące pamięci:** Aplikacja musi zapewnić strukturę bloku sterowania ECDSA do utrzymywania stanu między operacjami.

## <a name="ecdh"></a>Ecdh

> [!IMPORTANT]
> W Azure RTOS 6.0 procedury ECDH powinny być używane tylko w przypadku kryptografii ECDHE, ponieważ statyczny klucz prywatny wymaga zabezpieczenia weryfikacji punktu wejściowego.

- **Standardowa:** NetX Crypto implementuje ECDH zgodnie z FIPS PUB 800-56Ar2: "Zalecenie dotyczące schematów ustanowienia klucza Pair-Wise przy użyciu dyskretnych logarytm kryptografii", które można znaleźć w: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)
- **Wymaganie dotyczące pamięci:** Aplikacja musi zapewnić strukturę bloku sterowania ECDH do utrzymywania stanu między operacjami.

## <a name="drbg"></a>DRBG

- **Standardowa:** NetX Crypto implementuje drbg zgodnie z FIPS PUB 800-90Ar1: "Zalecenie dotyczące generowania liczb losowych przy użyciu deterministycznych generatorów bitów losowych", które można znaleźć w: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)
- **Wymaganie dotyczące pamięci:** Aplikacja musi zapewnić strukturę bloku sterowania DRBG do utrzymywania stanu między operacjami.

## <a name="fips-compliant"></a>FIPS-Compliant

NetX Crypto FIPS 140-2