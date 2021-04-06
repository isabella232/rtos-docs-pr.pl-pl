---
title: Rozdział 2 — Instalowanie obsługi ThreadX dla ARMv8-M
description: W tym rozdziale wyjaśniono, jak zainstalować i używać kodu źródłowego ThreadX dla architektury ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377593"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>Rozdział 2 Instalowanie obsługi ThreadX dla ARMv8-M

Istnieją dodatkowe pliki kodu źródłowego ThreadX do obsługi architektury ARMv8-M.

Jeśli ThreadX ma być uruchamiany w trybie zabezpieczonym, te dodatkowe pliki i interfejsy API nie są konieczne. Aby uruchomić ThreadX w trybie zabezpieczonym, zdefiniuj symbol **TX_SECURE_EXECUTION** w górnej części **_tx_port. h_*_ lub w wierszu polecenia lub w ustawieniach projektu. Upewnij* się, że TX_SECURE_EXECUTION** jest zdefiniowany dla wszystkich plików c i Assembly. ThreadX i aplikacja użytkownika zostanie wykonana w trybie zabezpieczonym.

Aby uruchomić program ThreadX i aplikację użytkownika w trybie niezabezpieczonym i obsłużyć niezabezpieczone funkcje zabezpieczeń, należy wykonać następujące czynności.

Plik ***tx_thread_secure_stack. c*** należy dodać do bezpiecznej aplikacji.

Do biblioteki ThreadX należy dodać następujące pliki.

- ***tx_secure_interface. h***
- ***txe_thread_secure_stack_allocate. c***
- ***txe_thread_secure_stack_free. c***
- ***tx_thread_secure_stack_allocate. s***
- ***tx_thread_secure_stack_free. s***

Poniższe dwa pliki zastępują pliki ogólne w bibliotece ThreadX.

- ***tx_thread_stack_error_handler. c***
- ***tx_thread_stack_error_notify. c***

## <a name="additional-threadx-sources-for-armv8-m"></a>Dodatkowe źródła ThreadX dla ARMv8-M

Dodatkowe pliki ThreadX dla architektury ARMv8-M TrustZone zostały opisane poniżej.

  | **Nazwa pliku**                            | **Zawartość**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface. h***              | Plik dołączany, który definiuje funkcje, które nie są bezpiecznie wywoływane ThreadX. |
  | ***txe_thread_secure_stack_allocate. c*** |  Sprawdzanie błędów pliku dla interfejsu API alokacji bezpiecznego stosu. |
  | ***txe_thread_secure_stack_free. c***     |  Sprawdzanie błędów pliku dla bezpłatnego interfejsu API bezpiecznego stosu. |
  | ***tx_thread_secure_stack_allocate. s***  |  Niezabezpieczona Veneer dla usługi alokacji bezpiecznego stosu. |
  | ***tx_thread_secure_stack_free. s***      |  Niezabezpieczona Veneer dla bezpłatnej usługi bezpiecznego stosu. |
  | ***tx_thread_stack_error_handler. c***    |  Procedura obsługi błędów stosu wątków. |
  | ***tx_thread_stack_error_notify. c***     |  Zarejestruj wywołanie zwrotne powiadomienia, aby obsłużyć błędy stosu wątków. |
