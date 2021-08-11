---
title: Rozdział 5 — Interfejsy API menedżera modułów
author: philmea
description: Ten artykuł zawiera podsumowanie interfejsów API menedżera modułów dostępnych dla rezydualnej części aplikacji.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e8e4da0f9591fd0b5d6249292f00266d96ccb67923c42632a4cfd8c39fa1f129
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799119"
---
# <a name="chapter-5---module-manager-apis"></a>Rozdział 5 — Interfejsy API menedżera modułów

## <a name="summary-of-module-manager-apis"></a>Podsumowanie interfejsów API menedżera modułów

Istnieje kilka dodatkowych interfejsów API dostępnych dla rezydualnej części aplikacji w następujący sposób.

- ***txm_module_manager_external_memory_enable** _ — _Enable dostępu do współdzielonych przestrzeni pamięci*
- ***txm_module_manager_file_load** _ — _Load z pliku za pośrednictwem pliku FileX*
- ***txm_module_manager_in_place_load** _ — _Load danych modułu, wykonaj w miejscu*
- ***txm_module_manager_initialize** _ — _Initialize menedżera modułów*
- ***txm_module_manager_mm_initialize** _ — _Initialize sprzętu do zarządzania pamięcią*
- ***txm_module_manager_maximum_module_priority_set** _ — _Set maksymalny dozwolony priorytet wątku w module*
- ***txm_module_manager_memory_fault_notify** _ — _Register wywołania zwrotnego aplikacji w przypadku błędu pamięci*
- ***txm_module_manager_memory_load** _ — _Load moduł z pamięci*
- ***txm_module_manager_object_pool_create** _ — _Create puli obiektów dla modułów*
- ***txm_module_manager_properties_get** _ — _Get modułu*
- ***txm_module_manager_start** _ — _Start wykonania określonego modułu*
- ***txm_module_manager_stop** _ — _Stop wykonania określonego modułu*
- ***txm_module_manager_unload** _ — _Unload modułu*

---

## <a name="txm_module_manager_external_memory_enable"></a>txm_module_manager_external_memory_enable

Włącz moduł, aby uzyskać dostęp do przestrzeni pamięci współdzielonych.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a>Opis

Ta usługa tworzy wpis w tabeli sprzętu do zarządzania pamięcią dla regionu pamięci współdzielonych, do których moduł może uzyskać dostęp.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **start_address** Adres początkowy regionu pamięci współdzielonych.
- **długość** Długość regionu pamięci współdzielonych.
- **atrybuty** Atrybuty regionu pamięci (pamięć podręczna, odczyt, zapis itp.). Atrybuty są specyficzne dla portu; Zobacz [dodatek](appendix.md) dla formatu atrybutów.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pamięci został utworzony pomyślnie.
- **TX_NOT_AVAILABLE** (0x1D) Manager nie został zainicjowany lub funkcja nie jest dostępna.
- **TX_PTR_ERROR** (0x03) Nieprawidłowe wystąpienie modułu.
- **TX_START_ERROR** (0x10) Module nie jest w stanie załadowanym.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Nieprawidłowe wyrównanie adresu startowego.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Niezgodne właściwości.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

Załaduj moduł z pliku za pomocą pliku FileX.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a>Opis

Ta usługa ładuje obraz binarny modułu zawartego w określonym pliku do obszaru pamięci modułu i przygotowuje go do wykonania. Zakłada się, że dostarczony nośnik jest już otwarty.

> [!NOTE]
> System FileX jest wykorzystywany do ładowania pliku. Aby włączyć dostęp do pliku FileX, moduł, biblioteka modułów, Menedżer modułów i biblioteka ThreadX (ze źródłami Menedżera modułów) muszą być budowane przy **użyciu** FX_FILEX_PRESENT zdefiniowanych w projektach.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **module_name** Nazwa modułu.
- **media_ptr** Wskaźnik do już otwartego nośnika FileX.
- **file_name** Nazwa pliku binarnego modułu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne ładowanie modułu.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.
- **TX_NOT_AVAILABLE** (0x1D) Manager nie został zainicjowany.
- **TX_NO_MEMORY** (0x10) Za mało pamięci do załadowania modułu.
- **TX_NOT_DONE** (0x20) Nośnik nie jest otwarty, nie znaleziono pliku lub plik jest nieprawidłowy.
- **TX_PTR_ERROR** (0x03) Nieprawidłowy wskaźnik modułu.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Nieprawidłowe wyrównanie.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) module (0xF1) został już załadowany.
- **TXM_MODULE_INVALID** (0xF2) | Nieprawidłowy moduł.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Niezgodne właściwości.

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

Ładowanie tylko danych modułu, wykonywanie modułu w istniejącej lokalizacji.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a>Opis

Ta usługa ładuje obszar danych modułu tylko do obszaru pamięci modułu i przygotowuje go do wykonania. Wykonanie kodu modułu będzie na miejscu, czyli od przesunięcia adresu określonego przez moduł w podanej lokalizacji.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **module_name** Nazwa modułu.
- **lokalizacja** Wskaźnik do obszaru kodu modułu, najpierw do obszaru kodu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne ładowanie modułu.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.
- **TX_NOT_AVAILABLE** (0x1D) Manager nie został zainicjowany.
- **TX_NO_MEMORY** (0x10) Za mało pamięci do załadowania modułu.
- **TX_PTR_ERROR** (0x03) Nieprawidłowy wskaźnik, wystąpienie modułu lub błąd modułu.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Nieprawidłowe wyrównanie.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) module (0xF1) został już załadowany.
- **TXM_MODULE_INVALID** (0xF2) Nieprawidłowy moduł.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Niezgodne właściwości.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

Zaimicjuj menedżera modułów.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a>Opis

Ta usługa inicjuje wewnętrzne zasoby menedżera modułów, w tym obszar pamięci używany do ładowania modułów.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_memory_start** Wskaźnik do początku pamięci modułu.
- **module_memory_size** Rozmiar w bajtach pamięci modułu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne inicjowanie.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

Inicjowanie sprzętu do zarządzania pamięcią.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a>Opis

Ta usługa inicjuje mmu.

### <a name="input-parameters"></a>Parametry wejściowe

brak

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne inicjowanie.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

- **TX_SUCCESS** (0x00) Pomyślne inicjowanie.
- **TX_NOT_AVAILABLE** (0x1D) Menedżer nie został zainicjowany.
- **TX_PTR_ERROR** (0x03) Nieprawidłowe wystąpienie modułu.
- **TX_START_ERROR** (0x10) Module nie jest w stanie załadowanym.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="example"></a>Przykład

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a>txm_module_manager_memory_fault_notify

Rejestrowanie wywołania zwrotnego aplikacji w przypadku błędu pamięci.

### <a name="prototype"></a>Prototype

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a>Opis

Ta usługa rejestruje określoną funkcję wywołania zwrotnego powiadomień o błędach pamięci aplikacji za pomocą menedżera modułów. W przypadku wystąpienia błędu pamięci ta funkcja jest wywoływana ze wskaźnikiem do obrażających wątku i wystąpienia modułu odpowiadającego incydującej wątku. Przetwarzanie Menedżera modułów automatycznie kończy obrażający wątek, ale pozostawia wszystkie inne wątki w module bez zmian. To aplikacja decyduje o tym, co należy zrobić z modułem skojarzonym z błędem pamięci.

Zapoznaj się z **wewnętrzną _txm_module_manager_memory_fault_info,** aby uzyskać szczegółowe informacje na temat samego błędu pamięci.

> [!NOTE]
> Funkcja wywołania zwrotnego powiadomień o błędach pamięci jest wykonywana bezpośrednio z wyjątku błędu pamięci, więc można wywołać tylko interfejsy API ThreadX dozwolone z procedur usługi przerwania. W związku z tym, aby zatrzymać i zwolnić moduł, wywołanie zwrotne powiadomienia aplikacji musi wysłać sygnał do zadania aplikacji, aby moduł można było zatrzymać i zwolnić.

### <a name="input-parameters"></a>Parametry wejściowe

- **notify_function** Wskaźnik funkcji do wywołania zwrotnego powiadomienia o błędach pamięci aplikacji. Dostarczenie wartości NULL powoduje wyłączenie powiadomienia o błędach pamięci.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślna rejestracja funkcji powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

Ta usługa ładuje kod i obszar danych modułu do obszaru pamięci modułu, który ***został*** txm_module_manager_initialize i przygotowuje go do wykonania.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **module_name** Nazwa modułu.
- **lokalizacja** Wskaźnik do obszaru kodu modułu, najpierw przejmij.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne ładowanie modułu.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.
- **TX_NOT_AVAILABLE** (0x1D) Menedżer nie został zainicjowany.
- **TX_NO_MEMORY** (0x10) Za mało pamięci do załadowania modułu.
- **TX_PTR_ERROR** (0x03) Nieprawidłowy wskaźnik, wystąpienie modułu lub błąd modułu.
- **TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Nieprawidłowe wyrównanie.
- **TXM_MODULE_ALREADY_LOADED** (0xF1) Module (moduł 0xF1) został już załadowany.
- **TXM_MODULE_INVALID** (0xF2) Nieprawidłowy moduł.
- **TXM_MODULE_INVALID_PROPERTIES** (0xF3) Niezgodne właściwości.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

Ta usługa tworzy pulę pamięci obiektów menedżera modułów, z których moduły mogą przydzielać obiekty ThreadX/NetX, dzięki czemu obiekt systemowy jest poza obszarem pamięci modułu.

### <a name="input-parameters"></a>Parametry wejściowe

- **pool_memory_start** Wskaźnik do początku pamięci obiektu.
- **pool_memory_size** Rozmiar w bajtach puli pamięci obiektów.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne inicjowanie.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

Ta usługa zwraca właściwości (określone w pamięci) modułu.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.
- **module_properties_ptr** Wskaźnik do miejsca docelowego właściwości modułu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne inicjowanie.
- **TX_PTR_ERROR** (0x03) Nieprawidłowy wskaźnik.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.

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

Ta usługa rozpoczyna wykonywanie określonego, już załadowanego modułu.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wcześniej załadowanego wystąpienia modułu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne uruchomienie modułu.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.
- **TX_NOT_AVAILABLE** (0x1D) Manager nie został zainicjowany.
- **TX_PTR_ERROR** (0x03) Nieprawidłowy wskaźnik lub wystąpienie modułu.
- **TX_START_ERROR** (0x10) module (0x10) module (Moduł 0x10) został już uruchomiony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

Ta usługa zatrzymuje moduł, który został wcześniej załadowany i uruchomiony. Zatrzymanie modułu obejmuje wykonanie opcjonalnego wątku zatrzymania modułu, zakończenie wszystkich wątków i usunięcie wszystkich zasobów skojarzonych z modułem.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** (0x00) Pomyślne zatrzymanie modułu.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.
- **TX_NOT_AVAILABLE** (0x1D) Manager nie został zainicjowany.
- **TX_PTR_ERROR** (0x03) Nieprawidłowy wskaźnik lub wystąpienie modułu.
- **TX_START_ERROR** (0x10) Module not started (Nie uruchomiliśmy modułu 0x10).

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

Ta usługa zwalnia wcześniej załadowany i zatrzymany moduł, zwalniając wszystkie skojarzone zasoby pamięci modułu.

### <a name="input-parameters"></a>Parametry wejściowe

- **module_instance** Wskaźnik do wystąpienia modułu.

### <a name="return-values"></a>Wartości zwracane

- **TX_SUCCESS** 0x00) Pomyślne zwolnienie modułu.
- **TX_CALLER_ERROR** (0x13) Nieprawidłowy wywołujący.
- **TX_NOT_AVAILABLE** (0x1D) Manager nie został zainicjowany.
- **TX_NOT_DONE** (0x20) Nieprawidłowy moduł lub moduł nie został zatrzymany.
- **TX_PTR_ERROR** (0x03) Nieprawidłowy wskaźnik lub wystąpienie modułu.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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
