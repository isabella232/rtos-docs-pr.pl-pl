---
title: Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX Crypto
description: Ten rozdział zawiera opis funkcjonalny kryptografii NetX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4ecdbfe99daa000d109908f834b139dcaf321491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821498"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a>Rozdział 3 — Opis funkcjonalny usługi Azure RTO NetX Crypto

## <a name="execution-overview"></a>Przegląd wykonywania

Ten rozdział zawiera opis funkcjonalny usługi Azure RTO NetX Crypto. W aplikacji kryptograficznej NetX są dwa podstawowe typy wykonywania programu: inicjalizacja i wywołania interfejsu aplikacji.

*Kryptografia NetX może służyć jako autonomiczna Biblioteka kryptograficzna lub może być używana z ThreadX, NetX i/lub NetX Secure.*

## <a name="aes"></a>AES

- **Algorytm standardowy:**: NetX kryptografii IMPLEMENTUJE algorytm AES zgodnie z PARAMETREM NIST FIPS 197, który można znaleźć w: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)
- **Obsługiwane długości kluczy**: 128, 192, 256
- **Obsługiwane tryby**:
  - CBC, Rob, (długość klucza 128-, 192-, 256-bit)
  - XCBC (długość klucza 128-bitowa),
  - CCM8 (długość klucza 128-bitowa)
- **Wymagania dotyczące pamięci**: aplikacja określa bufor wejściowy i bufor wyjściowy oraz strukturę kontrolki AES. Struktura formantów AES zachowuje stan algorytmu AES między wywołaniami interfejsu API. Bufor wejściowy zawiera dane, które mają być zaszyfrowane lub odszyfrowane, oraz może mieć dowolny rozmiar. Bufor wyjściowy jest używany przez algorytm AES do przechowywania danych przetwarzanych przez algorytm AES. Rozmiar buforu wyjściowego nie może być mniejszy niż rozmiar buforu wejściowego i musi być wielokrotnością 16 bajtów, rozmiar bloku AES. Bufory wejściowe i wyjściowe muszą mieć ciągłą pamięć i nie mogą się nakładać, z wyjątkiem sytuacji, w której jest używane szyfrowanie w miejscu (przy użyciu tej samej pamięci dla danych wejściowych i wyjściowych). Podczas szyfrowania w miejscu bufor wyjściowy jest uruchamiany w dokładnie tej samej lokalizacji co bufor wejściowy i nie może być mniejszy niż bufor wejściowy. Gdy szyfrowanie AES działa w miejscu, nie jest wymagana żadna dodatkowa pamięć zapasowa.

## <a name="3des"></a>3DES

- **Standard algorytmu**: Kryptografia NetX implementuje implementację tripple des (TDES, znaną również jako 3DES) zgodnie z publikacją specjalną NIST 800-67 rev 2: *"Recommendataion dla algorytmu szyfrowania danych Triple Data Encryption (TDES)"*, który można znaleźć w: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)
- **Obsługiwana długość klucza**: 64 * 3 = 192
- **Requreiment pamięci:**: brak

W przypadku kryptografii NetX termin "3DES" jest używany zamiennie z opcją "TDES".

## <a name="md5"></a>MD5

- **Standard algorytmu**: Kryptografia NetX implementuje algorytm MD5 zgodny ze standardem RFC 1321: *"algorytm MD5 Message-Digest"*
- **Wymaganie dotyczące pamięci**: aplikacja musi dostarczyć strukturę bloku kontroli MD5, która jest używana do utrzymania stanu między operacjami MD5.

## <a name="sha1-sha256512"></a>SHA1, SHA256/512

- **Standard algorytmu:** Kryptografia NetX implementuje algorytm SHA1/256/512 zgodnie z publikacją Federal FIPS 180-4: "*Secure Hash Standard*", który można znaleźć w: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
- **Rozmiar bloku skrótu:**:
  - SHA1:160 wartość skrótu usługi BITS
  - SHA 224:224 wartość skrótu usługi BITS
  - SHA 256:256 wartość skrótu usługi BITS
  - SHA 384:384 wartość skrótu usługi BITS
  - SHA 512:512 wartość skrótu usługi BITS
  - Wartość skrótu SHA 512/224:224 BITS
  - Wartość skrótu SHA 512/256:256 BITS

  W przypadku kryptografii NetX procedury SHA256 są używane do hadn SHA256 i SHA224. Procedury SHA512 są używane do SHA512, SHA384, SHA512/224 i SHA512/256.
- **Wymagania dotyczące pamięci:** Aplikacja musi zapewnić strukturę bloku sterowania algorytmem SHA, aby zachować stan między operacjami.

## <a name="rsa"></a>RSA

- **Standard:** Kryptografia NetX implementuje RSA zgodnie ze standardem "*PKCS #1 v 2.2: RSA Cryptography Standard*", który jest publikowany jako RFC 8017 i można go znaleźć w: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)
- **Wymagania dotyczące pamięci:** Aplikacja musi zapewnić strukturę bloku kontroli RSA, aby zachować stan między operacjami i zapewnić niezbędną przestrzeń buforową "Scratch" dla obliczeń pośrednich.

## <a name="hmac"></a>FUNKCJE

- **Standard:** Kryptografia NetX implementuje program HMAC zgodnie ze standardem FIPS PUB 198-1: "*Keyed-Hash kod uwierzytelniania wiadomości (HMAC)*", który można znaleźć w: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)
- **Wymagania dotyczące pamięci:** Aplikacja musi udostępniać strukturę bloku formantów HMAC, aby zachować stan między operacjami. Podany blok kontroli zależy od wymaganej bazowej operacji skrótu (np. SHA1, MD5).

## <a name="elliptic-curve"></a>Krzywa eliptyczna

- **Standard:** Kryptografia NetX implementuje krzywą eliptyczna. Obsługiwane nazwane krzywe to (tylko pole podstawowe):
  - P-192
  - P-224
  - P-256
  - P-384
  - P-521

   > [!TIP]
   > Format unkompresowany jest obsługiwany. Zobacz sekcję 2.3.3 i 2.3.4 of SEC1-V1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)

- **Wymagania dotyczące pamięci:** Dawaj

## <a name="ecdsa"></a>ECDSA

- **Standard:** Kryptografia NetX implementuje ECDSA zgodnie z FIPS PUB 186-4: "*Digital Signature Standard (DSS)*", który można znaleźć w: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)
- **Wymagania dotyczące pamięci:** Aplikacja musi udostępniać strukturę bloku sterowania ECDSA, aby zachować stan między operacjami.

## <a name="ecdh"></a>ECDH

> [!IMPORTANT]
> W usłudze Azure RTO 6,0 procedury ECDH powinny być używane tylko w przypadku kryptografii ECDHE, ponieważ ECDH ze statycznym kluczem prywatnym wymaga, aby Walidacja punktu wejścia była zabezpieczona.

- **Standard:** Kryptografia NetX implementuje ECDH zgodnie z zaleceniami standardu FIPS PUB 800-56Ar2: "zaleceniem do Pair-Wise kluczowych planów tworzenia przy użyciu dyskretnego kryptografii logarytmu", które można znaleźć w: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)
- **Wymagania dotyczące pamięci:** Aplikacja musi udostępniać strukturę bloku sterowania ECDH, aby zachować stan między operacjami.

## <a name="drbg"></a>DRBG

- **Standard:** Kryptografia NetX implementuje DRBG zgodnie z zasadami FIPS PUB 800-90Ar1: "zalecenia dotyczące generowania liczb losowych przy użyciu deterministycznych generatorów losowych", które można znaleźć w: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)
- **Wymagania dotyczące pamięci:** Aplikacja musi udostępniać strukturę bloku sterowania DRBG, aby zachować stan między operacjami.

## <a name="fips-compliant"></a>FIPS-Compliant

NetX kryptografii FIPS 140-2