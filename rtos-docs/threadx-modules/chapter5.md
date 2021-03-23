---
title: Rozdział 5 — interfejsy API Menedżera modułów
author: philmea
description: Ten artykuł zawiera podsumowanie interfejsów API Menedżera modułów dostępnych dla rezydentnej części aplikacji.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821390"
---
# <a name="chapter-5---module-manager-apis"></a>Rozdział 5 — interfejsy API Menedżera modułów

## <a name="summary-of-module-manager-apis"></a>Podsumowanie interfejsów API Menedżera modułów

Istnieje kilka dodatkowych interfejsów API, które są dostępne dla rezydentnej części aplikacji w następujący sposób.

- ***txm_module_manager_external_memory_enable** _ _Enable dostępu do modułu do udostępnionej przestrzeni pamięci *
- ***txm_module_manager_file_load** _-_Load moduł z pliku za pośrednictwem FileX *
- ***txm_module_manager_in_place_load** _-_Load dane modułu, wykonaj w miejscu *
- ***txm_module_manager_initialize** _-_Initialize Menedżera modułów *
- ***txm_module_manager_mm_initialize** _-_Initialize sprzęt zarządzania pamięcią *
- ***txm_module_manager_maximum_module_priority_set** _-_Set maksymalny priorytet wątku dozwolony w module *
- ***txm_module_manager_memory_fault_notify** _-_Register wywołanie zwrotne aplikacji dotyczące błędu pamięci *
- ***txm_module_manager_memory_load** _-_Load module z pamięci *
- ***txm_module_manager_object_pool_create** _-_Create pulę obiektów dla modułów *
- ***txm_module_manager_properties_get** _-_Get właściwości modułu *
- ***txm_module_manager_start** _-_Start wykonywanie określonego modułu *
- ***txm_module_manager_stop** _-_Stop wykonywanie określonego modułu *
- ***txm_module_manager_unload** _-_Unload module *

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

Włącz moduł, aby uzyskać dostęp do udostępnionej przestrzeni pamięci.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>Opis

Ta usługa tworzy wpis w tabeli sprzętowej zarządzania pamięcią dla regionu pamięci współdzielonej, do którego moduł może uzyskać dostęp.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **start_address** Adres początkowy obszaru pamięci udostępnionej.
- **Długość** Długość regionu pamięci współdzielonej.
- **atrybuty** Atrybuty regionu pamięci (pamięć podręczna, Odczyt, zapis itp.). Atrybuty są specyficzne dla portu; Zobacz [dodatek](appendix.md) dla formatu atrybutów.

### <a name="return-values"></a>Wartości zwracane

- Pomyślnie utworzono wpis pamięci **TX_SUCCESS** (0x00).
- Menedżer **TX_NOT_AVAILABLE** (0x1D) nie został zainicjowany lub funkcja jest niedostępna.
- **TX_PTR_ERROR** (0X03) nieprawidłowe wystąpienie modułu.
- Moduł **TX_START_ERROR** (0x10) nie jest w stanie załadowania.
- **TXM_MODULE_ALIGNMENT_ERROR** (0XF0) nieprawidłowe wyrównanie adresu początkowego.
- Niezgodne właściwości **TXM_MODULE_INVALID_PROPERTIES** (0xF3).

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a>txm_module_manager_file_load

Załaduj moduł z pliku za pośrednictwem FileX.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>Opis

Ta usługa ładuje obraz binarny modułu zawartego w określonym pliku do obszaru pamięci modułu i przygotowuje go do wykonania. Przyjęto, że dostarczony nośnik jest już otwarty.

> [!NOTE]
> System FileX jest używany do ładowania pliku. Aby można było włączyć dostęp do FileX, moduł, biblioteka modułów, Menedżer modułów i Biblioteka ThreadX (ze źródłami Menedżera modułów) muszą zostać skompilowane przy użyciu **FX_FILEX_PRESENT** zdefiniowanych w projektach.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **module_name** Nazwa modułu.
- **media_ptr** Wskaźnik do już otwartego nośnika FileX.
- **file_name** Nazwa pliku binarnego modułu.

### <a name="return-values"></a>Wartości zwracane

- Załadowanie modułu zakończyło się **TX_SUCCESS** (0x00).
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.
- Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).
- **TX_NO_MEMORY** (0x10) za mało pamięci do załadowania modułu.
- **TX_NOT_DONE** (0x20) nie jest otwarty, nie znaleziono pliku lub plik jest nieprawidłowy.
- **TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik modułu.
- **TXM_MODULE_ALIGNMENT_ERROR** (0XF0) nieprawidłowe wyrównanie.
- Moduł **TXM_MODULE_ALREADY_LOADED** (0xF1) jest już załadowany.
- **TXM_MODULE_INVALID** (0xF2) | Nieprawidłowa Preambuła modułu.
- Niezgodne właściwości **TXM_MODULE_INVALID_PROPERTIES** (0xF3).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_in_place_load"></a>txm_module_manager_in_place_load

Załaduj tylko dane modułu, wykonaj moduł w istniejącej lokalizacji.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Opis

Ta usługa ładuje obszar danych modułu tylko do obszaru pamięci modułu i przygotowuje go do wykonania. Wykonanie kodu modułu będzie w miejscu, czyli od przesunięcia adresu określonego przez numer preambuły modułu w podanej lokalizacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **module_name** Nazwa modułu.
- **Lokalizacja** Wskaźnik do obszaru kodu modułu, najpierw preambuły.

### <a name="return-values"></a>Wartości zwracane

- Załadowanie modułu zakończyło się **TX_SUCCESS** (0x00).
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.
- Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).
- **TX_NO_MEMORY** (0x10) za mało pamięci do załadowania modułu.
- **TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik, wystąpienie modułu lub Preambuła modułu.
- **TXM_MODULE_ALIGNMENT_ERROR** (0XF0) nieprawidłowe wyrównanie.
- Moduł **TXM_MODULE_ALREADY_LOADED** (0xF1) jest już załadowany.
- **TXM_MODULE_INVALID** (0XF2) Nieprawidłowa Preambuła modułu.
- Niezgodne właściwości **TXM_MODULE_INVALID_PROPERTIES** (0xF3).

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_file_load
- txm_module_manager_memory_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_initialize"></a>txm_module_manager_initialize

Zainicjuj Menedżera modułów.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>Opis

Ta usługa inicjuje wewnętrzne zasoby Menedżera modułów, w tym obszar pamięci używany do ładowania modułów.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_memory_start** Wskaźnik na początek pamięci modułu.
- **module_memory_size** Rozmiar w bajtach pamięci modułu.

### <a name="return-values"></a>Wartości zwracane

- Pomyślnie zainicjowano **TX_SUCCESS** (0x00).
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_object_pool_create

---

## <a name="txm_module_manager_initialize_mmu"></a>txm_module_manager_initialize_mmu

Zainicjuj sprzęt zarządzania pamięcią.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>Opis

Ta usługa inicjuje pamięcią.

### <a name="input-parameters"></a>Parametry wejściowe

brak

### <a name="return-values"></a>Wartości zwracane

- Pomyślnie zainicjowano **TX_SUCCESS** (0x00).
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a>txm_module_manager_maximum_module_priority_set

Ustaw maksymalny priorytet wątku dozwolony w module.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a>Opis

Ta usługa ustawia maksymalny priorytet wątku dozwolony w module.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **priorytet** Maksymalny priorytet wątku.

### <a name="return-values"></a>Wartości zwracane

- Pomyślnie zainicjowano **TX_SUCCESS** (0x00).
- Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).
- **TX_PTR_ERROR** (0X03) nieprawidłowe wystąpienie modułu.
- Moduł **TX_START_ERROR** (0x10) nie jest w stanie załadowania.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a>txm_module_manager_memory_fault_notify

Zarejestruj wywołanie zwrotne aplikacji dla błędu pamięci.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>Opis

Ta usługa rejestruje określoną funkcję wywołania zwrotnego powiadomień o błędach pamięci aplikacji za pomocą Menedżera modułów. Jeśli wystąpi błąd pamięci, ta funkcja jest wywoływana ze wskaźnikiem do wątku, którego to dotyczy, i wystąpieniem modułu odpowiadającemu wątkowi, którego to dotyczy. Przetwarzanie przez Menedżera modułów automatycznie kończy działanie wątku, ale pozostawia wszystkie inne wątki w module bez zmian. Do aplikacji można zdecydować, co należy zrobić z modułem skojarzonym z błędem pamięci.

Zapoznaj się z wewnętrzną strukturą **_txm_module_manager_memory_fault_info** , aby uzyskać szczegółowe informacje dotyczące samego błędu pamięci.

> [!NOTE]
> Funkcja wywołania zwrotnego powiadomienia o błędzie pamięci jest wykonywana bezpośrednio z powodu wyjątku błędu pamięci, więc można wywołać tylko interfejsy API ThreadX dozwolone z procedur usługi przerwania. W związku z tym w celu zatrzymania i zwolnienia nieprawidłowego modułu wywołanie zwrotne powiadomienia aplikacji musi wysłać sygnał do zadania aplikacji, aby można było zatrzymać i zwolnić moduł.

### <a name="input-parameters"></a>Parametry wejściowe

- **notify_function** Wskaźnik funkcji do wywołania zwrotnego powiadomienia o błędzie pamięci aplikacji. Podanie wartości NULL powoduje wyłączenie powiadomienia o błędzie pamięci.

### <a name="return-values"></a>Wartości zwracane

- Rejestracja funkcji powiadomień pomyślnych **TX_SUCCESS** (0x00).

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a>txm_module_manager_memory_load

Załaduj moduł z pamięci.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Opis

Ta usługa ładuje kod modułu i obszar danych do obszaru pamięci modułu skonfigurowanym przez ***txm_module_manager_initialize*** i przygotowuje go do wykonania.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **module_name** Nazwa modułu.
- **Lokalizacja** Wskaźnik do obszaru kodu modułu, najpierw preambuły.

### <a name="return-values"></a>Wartości zwracane

- Załadowanie modułu zakończyło się **TX_SUCCESS** (0x00).
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.
- Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).
- **TX_NO_MEMORY** (0x10) za mało pamięci do załadowania modułu.
- **TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik, wystąpienie modułu lub Preambuła modułu.
- **TXM_MODULE_ALIGNMENT_ERROR** (0XF0) nieprawidłowe wyrównanie.
- Moduł **TXM_MODULE_ALREADY_LOADED** (0xF1) jest już załadowany.
- **TXM_MODULE_INVALID** (0XF2) Nieprawidłowa Preambuła modułu.
- Niezgodne właściwości **TXM_MODULE_INVALID_PROPERTIES** (0xF3).

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_unload

---

## <a name="txm_module_manager_object_pool_create"></a>txm_module_manager_object_pool_create

Utwórz pulę obiektów dla modułów.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy pulę pamięci obiektu menedżera modułów, z której moduły mogą przydzielić obiekty ThreadX/NetX z, a tym samym zachować obiekt system z obszaru pamięci modułu.

### <a name="input-parameters"></a>Parametry wejściowe

- **pool_memory_start** Wskaźnik na początek pamięci obiektu.
- **pool_memory_size** Rozmiar w bajtach puli pamięci obiektu.

### <a name="return-values"></a>Wartości zwracane

- Pomyślnie zainicjowano **TX_SUCCESS** (0x00).
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_initialize

---

## <a name="txm_module_manager_properties_get"></a>txm_module_manager_properties_get

Pobierz właściwości modułu.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca właściwości (określone w preambule) modułu.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **module_properties_ptr** Wskaźnik do miejsca docelowego dla właściwości modułu.

### <a name="return-values"></a>Wartości zwracane

- Pomyślnie zainicjowano **TX_SUCCESS** (0x00).
- **TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik.
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a>txm_module_manager_start

Rozpocznij wykonywanie modułu.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Opis

Ta usługa uruchamia wykonywanie określonego, już załadowanego modułu.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do poprzednio załadowanego wystąpienia modułu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0X00) pomyślne uruchomienie modułu.
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.
- Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).
- **TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik lub wystąpienie modułu.
- Moduł **TX_START_ERROR** (0x10) jest już uruchomiony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_stop

---

## <a name="txm_module_manager_stop"></a>txm_module_manager_stop

Zatrzymaj wykonywanie modułu.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Opis

Ta usługa umożliwia zatrzymanie modułu, który został wcześniej załadowany i uruchomiony. Zatrzymywanie modułu obejmuje wykonanie opcjonalnego wątku zatrzymania modułu, zakończenie wszystkich wątków i usunięcie wszystkich zasobów skojarzonych z modułem.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.

### <a name="return-values"></a>Wartości zwracane

- Zakończono pomyślne zatrzymywanie modułu **TX_SUCCESS** (0x00).
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.
- Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).
- **TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik lub wystąpienie modułu.
- Moduł **TX_START_ERROR** (0x10) nie został uruchomiony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_start

---

## <a name="txm_module_manager_unload"></a>txm_module_manager_unload

Zwolnij moduł.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a>Opis

Ta usługa zwalnia poprzednio załadowany i zatrzymany moduł, zwalniając wszystkie skojarzone zasoby pamięci modułu.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** 0x00) załadowanie modułu zakończone powodzeniem.
- **TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący.
- Nie zainicjowano Menedżera **TX_NOT_AVAILABLE** (0x1D).
- **TX_NOT_DONE** (0X20) nieprawidłowy moduł lub moduł nie został zatrzymany.
- **TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik lub wystąpienie modułu.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a>Zobacz także

- txm_module_manager_file_load
- txm_module_manager_in_place_load
- txm_module_manager_memory_load
- txm_module_manager_stop
