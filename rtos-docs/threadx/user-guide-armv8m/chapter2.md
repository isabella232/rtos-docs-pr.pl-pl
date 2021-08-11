---
title: Rozdział 2 — Instalowanie obsługi ThreadX dla ARMv8-M
description: W tym rozdziale opisano sposób instalowania i używania kodu źródłowego ThreadX dla architektury ARMv8-M.
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 085310acd5262226e9ff3af440a5f05268c7799e78eda81334a13b736222b95c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801958"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>Rozdział 2 Instalowanie obsługi ThreadX dla ARMv8-M

Istnieją dodatkowe pliki kodu źródłowego ThreadX do obsługi architektury ARMv8-M.

Jeśli threadX ma być uruchamiany w trybie bezpiecznym, te dodatkowe pliki i interfejsy API nie są potrzebne. Aby uruchomić ThreadX w trybie bezpiecznym, zdefiniuj symbol **TX_SECURE_EXECUTION** u góry **_tx_port.h_ _ lub w ustawieniach wiersza polecenia *lub projektu. Upewnij się,* TX_SECURE_EXECUTION** jest zdefiniowany dla wszystkich plików c i zestawu. ThreadX i aplikacja użytkownika będą wykonywane w trybie bezpiecznym.

Aby uruchomić ThreadX i aplikację użytkownika w trybie niezabezpieczonych i obsługiwać niezabezpieczonych wywoływalnych bezpiecznych funkcji, wykonaj następujące czynności.

Plik ***tx_thread_secure_stack.c*** należy dodać do bezpiecznej aplikacji.

Następujące pliki należy dodać do biblioteki ThreadX.

- ***tx_secure_interface.h***
- ***txe_thread_secure_stack_allocate.c***
- ***txe_thread_secure_stack_free.c***
- ***tx_thread_secure_stack_allocate.s***
- ***tx_thread_secure_stack_free.s***

Następujące dwa pliki zastępują pliki ogólne w bibliotece ThreadX.

- ***tx_thread_stack_error_handler.c***
- ***tx_thread_stack_error_notify.c***

## <a name="additional-threadx-sources-for-armv8-m"></a>Dodatkowe źródła ThreadX dla ARMv8-M

Poniżej opisano dodatkowe pliki ThreadX dla architektury ARMv8-M TrustZone.

  | **Nazwa pliku**                            | **Zawartość**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface.h***              | Dołącz plik, który definiuje niezabezpieczonych funkcji wywoływalnych ThreadX. |
  | ***txe_thread_secure_stack_allocate.c*** |  Plik sprawdzania błędów dla interfejsu API przydzielania bezpiecznego stosu. |
  | ***txe_thread_secure_stack_free.c***     |  Plik sprawdzania błędów dla bezpiecznego interfejsu API bez stosu. |
  | ***tx_thread_secure_stack_allocate.s***  |  Niezabezpieczona usługa przydzielania stosu. |
  | ***tx_thread_secure_stack_free.s***      |  Niezabezpieczona usługa bez stosu. |
  | ***tx_thread_stack_error_handler.c***    |  Procedura obsługi błędów stosu wątków. |
  | ***tx_thread_stack_error_notify.c***     |  Rejestrowanie wywołania zwrotnego powiadomień w celu obsługi błędów stosu wątków. |
