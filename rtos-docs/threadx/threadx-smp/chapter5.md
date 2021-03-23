---
title: Rozdział 5 — sterowniki urządzeń dla usługi Azure RTO ThreadX SMP
description: Ten rozdział zawiera opis sterowników urządzeń dla usługi Azure RTO ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: acfb54a25cc8bc27b7d0aaeff48956529d90c9e1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823922"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a>Rozdział 5 — sterowniki urządzeń dla usługi Azure RTO ThreadX SMP

Ten rozdział zawiera opis sterowników urządzeń dla usługi Azure RTO ThreadX SMP. Informacje przedstawione w tym rozdziale zaprojektowano w celu ułatwienia deweloperom pisanie sterowników określonych przez aplikację. 

## <a name="device-driver-introduction"></a>Wprowadzenie do sterownika urządzenia

Komunikacja ze środowiskiem zewnętrznym jest ważnym składnikiem większości aplikacji osadzonych. Ta komunikacja jest realizowana za pomocą urządzeń sprzętowych, które są dostępne dla oprogramowania aplikacji osadzonej. Składniki oprogramowania odpowiedzialne za zarządzanie takimi urządzeniami są zwykle nazywane *sterownikami urządzeń*.

Sterowniki urządzeń w osadzonych systemach czasu rzeczywistego są zależne od aplikacji. Jest to prawdziwe w przypadku dwóch głównych przyczyn: ogromnej różnorodności sprzętu docelowego i równie ogromnych wymagań dotyczących wydajności nałożonych na aplikacje w czasie rzeczywistym. Z tego powodu praktycznie niemożliwe jest dostarczenie wspólnego zestawu sterowników, który będzie spełniał wymagania każdej aplikacji. Z tego względu informacje przedstawione w tym rozdziale zaprojektowano w celu ułatwienia użytkownikom dostosowywania sterowników urządzeń SMP *w* ThreadX i pisania własnych sterowników.

## <a name="driver-functions"></a>Funkcje sterownika

Sterowniki urządzeń SMP ThreadX składają się z ośmiu podstawowych obszarów funkcjonalnych w następujący sposób:

- **Inicjowanie sterownika**
- **Kontrolka sterownika**
- **Dostęp do sterownika**
- **Dane wejściowe sterownika**
- **Dane wyjściowe sterownika**
- **Przerwania sterownika**
- **Stan sterownika**
- **Zakończenie sterownika**

Z wyjątkiem inicjalizacji każdy obszar funkcjonalny sterownika jest opcjonalny. Ponadto dokładne przetwarzanie w poszczególnych obszarach jest specyficzne dla sterownika urządzenia.

### <a name="driver-initialization"></a>Inicjowanie sterownika 
Ten obszar funkcjonalny jest odpowiedzialny za Inicjowanie rzeczywistego urządzenia sprzętowego i wewnętrznych struktur danych sterownika. Wywoływanie innych usług sterowników jest niedozwolone do momentu ukończenia inicjalizacji.

> [!IMPORTANT]
> Składnik funkcji inicjowania sterownika jest zazwyczaj wywoływany z funkcji **tx_application_define** lub z wątku inicjującego.

### <a name="driver-control"></a>Kontrolka sterownika 
Po zainicjowaniu sterownika i przygotowaniu go do działania ten obszar funkcjonalny jest odpowiedzialny za kontrolę w czasie wykonywania. Zwykle kontrola w czasie wykonywania składa się z wprowadzania zmian w podstawowym urządzeniu sprzętowym. Przykłady obejmują zmianę szybkości transmisji urządzenia szeregowego lub wyszukanie nowego sektora na dysku.

### <a name="driver-access"></a>Dostęp do sterownika 
Niektóre sterowniki urządzeń są wywoływane tylko z jednego wątku aplikacji. W takich przypadkach ten obszar funkcjonalny nie jest wymagany. Jednak w aplikacjach, w których wiele wątków wymaga jednoczesnego dostępu do sterowników, ich interakcje muszą być kontrolowane przez dodanie funkcji Przypisz/Zwolnij do sterownika urządzenia. Alternatywnie aplikacja może używać semafora do kontrolowania dostępu do sterowników i uniknięcia dodatkowych obciążeń i komplikacji w obrębie sterownika. 

### <a name="driver-input"></a>Dane wejściowe sterownika 
Ten obszar funkcjonalny jest odpowiedzialny za wszystkie dane wejściowe urządzenia. Główne problemy związane z wejściem sterownika zwykle obejmują, jak dane wejściowe są buforowane i jak wątki oczekują na takie dane wejściowe. 

### <a name="driver-output"></a>Dane wyjściowe sterownika 
Ten obszar funkcjonalny jest odpowiedzialny za wszystkie dane wyjściowe urządzenia. Główne problemy związane z danymi wyjściowymi sterowników zwykle obejmują, jak dane wyjściowe są buforowane i jak wątki oczekują na wykonanie danych wyjściowych. 

### <a name="driver-interrupts"></a>Przerwania sterownika 
Większość systemów w czasie rzeczywistym polega na przerwaniu sprzętowym w celu powiadomienia sterownika o zdarzeniach wejściowych, wyjściowych, kontroli i błędach urządzenia. Przerwania zapewniają gwarantowany czas odpowiedzi na takie zdarzenia zewnętrzne. Zamiast przerwań oprogramowanie sterownika może okresowo sprawdzać sprzęt zewnętrzny pod kątem takich zdarzeń. Ta technika jest nazywana *sondowaniem*. Jest mniej w czasie rzeczywistym niż przerwania, ale sondowanie może mieć sens w przypadku niektórych aplikacji w czasie rzeczywistym. 

### <a name="driver-status"></a>Stan sterownika 
Ten obszar funkcji jest odpowiedzialny za zapewnienie stanu środowiska uruchomieniowego i statystyk skojarzonych z operacją sterownika. Informacje zarządzane przez ten obszar funkcji zwykle obejmują następujące elementy: 
- Bieżący stan urządzenia
- Bajty wejściowe
- Bajty wyjściowe
- Liczba błędów urządzeń

### <a name="driver-termination"></a>Zakończenie sterownika 
Ten obszar funkcjonalny jest opcjonalny. Jest to wymagane tylko wtedy, gdy sterownik i/lub fizyczne urządzenie sprzętowe należy wyłączyć. Po zakończeniu należy ponownie wywołać sterownik, dopóki nie zostanie ponownie zainicjowany. 

## <a name="simple-driver-example"></a>Przykład prostego sterownika

Przykładem jest najlepszy sposób opisywania sterownika urządzenia. W tym przykładzie sterownik przyjmuje proste urządzenie szeregowe z rejestrem konfiguracji, rejestrem wejściowym i rejestrem wyjściowym. Ten prosty przykład sterownika ilustruje obszar funkcjonalności inicjalizacji, wejścia, wyjścia i przerwania.

### <a name="simple-driver-initialization"></a>Prosta Inicjalizacja sterownika 
Funkcja ***tx_sdriver_initialize*** prostego sterownika tworzy dwa semafory zliczania, które są używane do zarządzania operacjami wejścia i wyjścia sterownika. Semafor wejściowy jest ustawiany przez wejście w trybie ISR, gdy znak jest odbierany przez urządzenie sprzętowe szeregowe. Z tego powodu semafor wejściowy jest tworzony z początkową liczbą równą zero.

Z drugiej strony semafor wyjściowy wskazuje dostępność rejestru transmisji sprzętu szeregowego. Jest tworzony z wartością jednego, aby wskazać, że rejestr przesyłania jest początkowo dostępny.

Funkcja inicjowania jest również odpowiedzialna za Instalowanie obsługi wektorów przerwania niskiego poziomu na potrzeby powiadomień wejściowych i wyjściowych. Podobnie jak w przypadku innych procedur usługi przerwania SMP ThreadX, obsługa niskiego poziomu musi wywoływać ***_tx_thread_context_save** _ przed wywołaniem prostego procedury ISR sterownika. Po powrocie przez funkcję ISR sterownika procedura obsługi niskiego poziomu musi wywołać _ * _ _tx_thread_context_restore_* *.

> [!IMPORTANT]
> Ważne jest, aby Inicjalizacja była wywoływana przed żadną inną funkcje sterownika. Zazwyczaj Inicjalizacja sterownika jest wywoływana z **tx_application_define**.

Zobacz rysunek 9 na stronie 306 dla kodu źródłowego inicjalizacji prostego sterownika.

```C
VOID     tx_sdriver_initialize(VOID)
{

    /* Initialize the two counting semaphores used to control
       the simple driver I/O. */
    tx_semaphore_create(&tx_sdriver_input_semaphore,
                       "simple driver input semaphore", 0);
    tx_semaphore_create(&tx_sdriver_output_semaphore,
                       "simple driver output semaphore", 1);

    /* Setup interrupt vectors for input and output ISRs.
       The initial vector handling should call the ISRs
       defined in this file. */

    /* Configure serial device hardware for RX/TX interrupt
       generation, baud rate, stop bits, etc. */
}
```
**RYSUNEK 9. Prosta Inicjalizacja sterownika**

### <a name="simple-driver-input"></a>Proste wprowadzanie sterowników 
Dane wejściowe dla prostych centrów sterowników wokół semafora wejściowego. Po odebraniu przerwań wejścia urządzenia szeregowego zostanie ustawiony semafor wejściowy. Jeśli co najmniej jeden wątek oczekuje na znak ze sterownika, wątek czekający najdłuższy zostanie wznowiony. Jeśli żadne wątki nie oczekują, semafor po prostu pozostaje ustawiony do momentu wywołania przez wątek funkcji wejścia stacji.

Istnieje kilka ograniczeń związanych z prostą obsługą wejścia sterownika. Najbardziej znaczącym jest potencjalną przyczyną porzucania znaków wejściowych. Jest to możliwe, ponieważ nie ma możliwości buforowania znaków wejściowych, które docierają przed przetworzeniem poprzedniego znaku. Jest to łatwo obsługiwane przez dodanie wejściowego buforu znaków.

> [!IMPORTANT]
> Tylko wątki mogą wywołać funkcję **tx_sdriver_input** .

Rysunek 10 pokazuje kod źródłowy skojarzony z prostym wejściem sterownika.

```C
UCHAR     tx_sdriver_input(VOID)
{

    /* Determine if there is a character waiting. If not,
        suspend. */
    tx_semaphore_get(&tx_sdriver_input_semaphore,
                                             TX_WAIT_FOREVER;
    /* Return character from serial RX hardware register. */
    return(*serial_hardware_input_ptr);
}

VOID     tx_sdriver_input_ISR(VOID)
{
    /* See if an input character notification is pending. */
    if (!tx_sdriver_input_semaphore.tx_semaphore_count)
    {
        /* If not, notify thread of an input character. */
        tx_semaphore_put(&tx_sdriver_input_semaphore);
    }
}
```
**RYSUNEK 10. Proste wprowadzanie sterowników**

### <a name="simple-driver-output"></a>Proste wyjście sterownika 
Przetwarzanie danych wyjściowych wykorzystuje semafor wyjściowy do sygnalizowania, kiedy rejestr transmisji urządzenia szeregowego jest bezpłatny. Przed faktycznym zapisaniem na urządzeniu znaku wyjściowego zostanie uzyskany semafor wyjściowy. Jeśli ta wartość jest niedostępna, poprzednia Transmisja nie została jeszcze ukończona.

Wyjście ISR jest odpowiedzialne za obsługę przerwania przesyłania. Przetwarzanie ilości danych wyjściowych ISR do ustawiania semafora wyjściowego, co pozwala na wyjście innego znaku.

> [!IMPORTANT]
> Tylko wątki mogą wywołać funkcję **tx_sdriver_output** .

Rysunek 11 przedstawia kod źródłowy skojarzony z prostym wyjściem sterownika.

```C
VOID     tx_sdriver_output(UCHAR alpha)
{

    /* Determine if the hardware is ready to transmit a
       character. If not, suspend until the previous output
        completes. */
    tx_semaphore_get(&tx_sdriver_output_semaphore,
                                            TX_WAIT_FOREVER);
    /* Send the character through the hardware. */
    *serial_hardware_output_ptr = alpha;
}

VOID     tx_sdriver_output_ISR(VOID)
{
    /* Notify thread last character transmit is
        complete. */
    tx_semaphore_put(&tx_sdriver_output_semaphore);
}
```
**RYSUNEK 11. Proste wyjście sterownika**

### <a name="simple-driver-shortcomings"></a>Proste braki sterowników 
Ten prosty przykład sterownika urządzenia ilustruje podstawowy pomysł dotyczący sterownika urządzenia ThreadX SMP. Jednak ponieważ prosty sterownik urządzenia nie rozwiąże buforowania danych ani nie występują żadne problemy, nie reprezentuje w pełni rzeczywistych sterowników SMP ThreadX. W poniższej sekcji opisano niektóre bardziej zaawansowane problemy związane z sterownikami urządzeń.

## <a name="advanced-driver-issues"></a>Zaawansowane problemy ze sterownikiem

Jak wspomniano wcześniej, sterowniki urządzeń mają wymagania, które są unikatowe jako aplikacje. Niektóre aplikacje mogą wymagać nadmiernej ilości buforów danych, a inna aplikacja może wymagać zoptymalizowanego procedury ISR sterownika z powodu przerwań urządzeń o wysokiej częstotliwości.

### <a name="io-buffering"></a>Buforowanie we/wy 
Buforowanie danych w aplikacjach osadzonych w czasie rzeczywistym wymaga znacznego zaplanowania. Niektóre z tych projektów są podyktowane przez bazowe urządzenie sprzętowe. Jeśli urządzenie zapewnia podstawowe bajty we/wy, prawdopodobnie jest to prosty bufor cykliczny. Jeśli jednak urządzenie zapewnia blok, dostęp DMA lub we/wy, prawdopodobnie jest to schemat zarządzania buforem. 

### <a name="circular-byte-buffers"></a>Cykliczne bufory bajtów 
Cykliczne bufory bajtów są zwykle używane w sterownikach, które zarządzają prostym urządzeniem sprzętowym, takim jak UART. Dwa bufory cykliczne są najczęściej używane w takich sytuacjach — jeden dla danych wejściowych i jeden dla danych wyjściowych.

Każdy kolisty bufor bajtowy składa się z obszaru pamięci bajtów (zazwyczaj jest to tablica UCHARs), wskaźnik odczytu i wskaźnik zapisu. Bufor jest uważany za pusty, gdy wskaźnik odczytu i wskaźniki zapisu odwołują się do tej samej lokalizacji pamięci w buforze. Inicjalizacja sterownika ustawia wskaźniki buforu odczytu i zapisu na adres początkowy buforu.

### <a name="circular-buffer-input"></a>Cykliczne wejście buforu 
Bufor wejściowy jest używany do przechowywania znaków, które docierają do tej aplikacji. Po odebraniu znaku wejściowego (zazwyczaj w procedurze usługi przerwania) nowy znak zostanie pobrany z urządzenia sprzętowego i umieszczony w buforze wejściowym w lokalizacji wskazywanej przez wskaźnik zapisu. Wskaźnik zapisu jest zaawansowany do następnej pozycji w buforze. Jeśli następna pozycja znajduje się poza końcem buforu, wskaźnik zapisu jest ustawiany na początku buforu. Pełny warunek kolejki jest obsługiwany przez anulowanie przybierania wskaźnika zapisu, jeśli nowy wskaźnik zapisu jest taki sam jak wskaźnik odczytu.

Żądania bajtów wejściowych aplikacji do sterownika najpierw przeanalizują wskaźniki odczytu i zapisu w buforze wejściowym. Jeśli wskaźniki odczytu i zapisu są identyczne, bufor jest pusty. W przeciwnym razie, jeśli wskaźnik odczytu nie jest taki sam, bajt wskazywany przez wskaźnik odczytu jest kopiowany z buforu wejściowego, a wskaźnik odczytu jest zaawansowany do następnej lokalizacji buforu. Jeśli nowy wskaźnik odczytu znajduje się poza końcem buforu, zostanie zresetowany do początku. Rysunek 12 przedstawia logikę cyklicznego buforu wejściowego.

```C
UCHAR     tx_input_buffer[MAX_SIZE];
UCHAR     tx_input_write_ptr;
UCHAR     tx_input_read_ptr;

/* Initialization.  */
tx_input_write_ptr =  &tx_input_buffer[0];
tx_input_read_ptr =    &tx_input_buffer[0];

/* Input byte ISR... UCHAR alpha has character from device. */
save_ptr =  tx_input_write_ptr;
*tx_input_write_ptr++ =  alpha;
if (tx_input_write_ptr > &tx_input_buffer[MAX_SIZE-1])
    tx_input_write_ptr =  &tx_input_buffer[0];  /* Wrap */
if (tx_input_write_ptr == tx_input_read_ptr)
    tx_input_write_ptr =  save_ptr;  /* Buffer full */

/* Retrieve input byte from buffer... */
if (tx_input_read_ptr != tx_input_write_ptr)
{
    alpha =  *tx_input_read_ptr++;
    if (tx_input_read_ptr > &tx_input_buffer[MAX_SIZE-1])
        tx_input_read_ptr =  &tx_input_buffer[0];
}
```
**RYSUNEK 12. Logika dla cyklicznego buforu wejściowego**

> [!IMPORTANT]
> Aby zapewnić niezawodne działanie, może być konieczne zablokowanie przerwań podczas manipulowania wskaźnikami odczytu i zapisu zarówno wejściowych, jak i wyjściowych buforów cyklicznych.

### <a name="circular-output-buffer"></a>Cykliczny bufor wyjściowy 
Bufor wyjściowy jest używany do przechowywania znaków, które dotarły do danych wyjściowych, zanim urządzenie sprzętowe zakończy wysyłanie poprzedniego bajtu. Przetwarzanie buforu wyjściowego jest podobne do przetwarzania buforu wejściowego, z wyjątkiem tego, że przetwarzanie przerwania przesyłania zostało wykonane, manipuluje wskaźnikiem odczytywania danych wyjściowych, podczas gdy żądanie danych wyjściowych aplikacji wykorzystuje wskaźnik zapisu danych wyjściowych. W przeciwnym razie przetwarzanie buforu wyjściowego jest takie samo. Rysunek 13shows logikę cyklicznego buforu wyjściowego.

```C
UCHAR     tx_output_buffer[MAX_SIZE];
UCHAR     tx_output_write_ptr;
UCHAR     tx_output_read_ptr;

/* Initialization.  */
tx_output_write_ptr =  &tx_output_buffer[0];
tx_output_read_ptr =   &tx_output_buffer[0];

/* Transmit complete ISR... Device ready to send. */
if (tx_output_read_ptr != tx_output_write_ptr)
{
    *device_reg =  *tx_output_read_ptr++;
    if (tx_output_read_reg > &tx_output_buffer[MAX_SIZE-1])
    tx_output_read_ptr =  &tx_output_buffer[0];
}

/* Output byte driver service. If device busy, buffer! */
save_ptr =  tx_output_write_ptr;
*tx_output_write_ptr++ =  alpha;
if (tx_output_write_ptr > &tx_output_buffer[MAX_SIZE-1])
    tx_output_write_ptr =  &tx_output_buffer[0];  /* Wrap */
if (tx_output_write_ptr == tx_output_read_ptr)
    tx_output_write_ptr =  save_ptr;  /* Buffer full!  */
```
**RYSUNEK 13. Logika cyklicznego buforu wyjściowego**

### <a name="buffer-io-management"></a>Zarządzanie buforowaniem we/wy 
Aby zwiększyć wydajność osadzonych mikroprocesorów, wiele urządzeń urządzeń peryferyjnych przesyła i odbiera dane przy użyciu buforów dostarczonych przez oprogramowanie. W niektórych implementacjach wiele buforów może służyć do przesyłania lub odbierania pojedynczych pakietów danych. 

Rozmiar i lokalizacja buforów we/wy jest określana przez oprogramowanie aplikacji i/lub sterownika. Zazwyczaj bufory mają ustalony rozmiar i są zarządzane w puli pamięci ThreadX SMP. Rysunek 14describes typowy bufor we/wy i ThreadXy blok pamięci SMP, który zarządza ich alokacją.

```C
typedef struct TX_IO_BUFFER_STRUCT
{

      struct TX_IO_BUFFER_STRUCT *tx_next_packet;
    struct TX_IO_BUFFER_STRUCT *tx_next_buffer;
      UCHAR  tx_buffer_area[TX_MAX_BUFFER_SIZE];
} TX_IO_BUFFER;

TX_BLOCK_POOL tx_io_block_pool;

/* Create a pool of I/O buffers. Assume that the pointer
   "free_memory_ptr"points to an available memory area that
   is 64 KBytes in size. */

tx_block_pool_create(&tx_io_block_pool,
                  "Sample IO Driver Buffer Pool",
                  free_memory_ptr, 0x10000,
                  sizeof(TX_IO_BUFFER));
```
**RYSUNEK 14. Bufor we/wy**

### <a name="tx_io_buffer"></a>TX_IO_BUFFER 
Element typedef TX_IO_BUFFER składa się z dwóch wskaźników. Wskaźnik ***tx_next_packet** _ służy do łączenia wielu pakietów na liście danych wejściowych lub wyjściowych. Wskaźnik _ *_tx_next_buffer_** służy do łączenia razem buforów, które składają się na pojedynczy pakiet danych z urządzenia. Oba te wskaźniki są ustawione na wartość NULL, gdy bufor jest przypisywany z puli. Ponadto niektóre urządzenia mogą wymagać innego pola, aby wskazać, jaka część obszaru buforowego zawiera dane.

### <a name="buffered-io-advantage"></a>Zalety buforowanej operacji we/wy 
Jakie są zalety schematu we/wy buforu? Największą korzyść polega na tym, że dane nie są kopiowane między rejestrami urządzeń i pamięcią aplikacji. Zamiast tego sterownik dostarcza urządzenie z serią wskaźników buforów. We/wy urządzenia fizycznego jest używana bezpośrednio pamięć buforu.

Użycie procesora do kopiowania pakietów wejściowych lub wyjściowych informacji jest niezwykle kosztowne i należy je unikać w każdej sytuacji dużej przepływności we/wy.

Kolejną zaletą operacji wejścia/wyjścia na sekundę jest to, że listy wejściowe i wyjściowe nie mają pełnych warunków. Wszystkie dostępne bufory mogą znajdować się w dowolnym momencie. Jest to kontrast z prostymi buforami dwubajtowymi przedstawionymi wcześniej w rozdziale. Każdy miał ustalony rozmiar ustalony podczas kompilacji.

### <a name="buffered-driver-responsibilities"></a>Zakresy obowiązków sterownika w buforze 
Buforowane sterowniki urządzeń są objęte wyłącznie zarządzaniem połączonymi listami buforów we/wy. Lista buforów wejściowych jest utrzymywana dla pakietów, które są odbierane, zanim oprogramowanie aplikacji jest gotowe. Z drugiej strony Lista buforów wyjściowych jest utrzymywana dla pakietów wysyłanych szybciej niż urządzenia sprzętowe mogą je obsłużyć. Rysunek 15 na stronie 314 zawiera proste dane wejściowe i wyjściowe połączone listy pakietów danych i buforów, które składają się na każdy pakiet.

![Zakresy obowiązków sterownika w buforze](media/image11.png)

**RYSUNEK 15. Listy Input-Output**

Interfejs aplikacji z buforowanymi sterownikami z takimi samymi buforami we/wy. W przypadku przesyłania oprogramowanie aplikacji udostępnia sterownik z co najmniej jednym buforem do przesłania. Gdy oprogramowanie aplikacji żąda danych wejściowych, sterownik zwraca dane wejściowe w buforach we/wy.

> [!IMPORTANT]
> W niektórych aplikacjach warto utworzyć interfejs wejściowy sterownika, który wymaga, aby aplikacja mogła wymienić bezpłatny bufor dla buforu wejściowego ze sterownika. Może to zmniejszyć część przetwarzania alokacji buforu w ramach sterownika.

### <a name="interrupt-management"></a>Zarządzanie przerwami 
W niektórych aplikacjach częstotliwość przerwań urządzenia może uniemożliwić zapisanie procedury ISR w języku C lub współdziałanie z ThreadX SMP dla każdego przerwania. Na przykład jeśli 25us do zapisywania i przywracania przerwanego kontekstu, nie zaleca się przeprowadzania pełnego kontekstu zapisywania, jeśli częstotliwość przerwań została 50us. W takich przypadkach do obsługi większości przerwań urządzenia jest używany mały język asemblera. Ten lowoverhead ISR będzie współpracujący z ThreadX SMP, gdy będzie to konieczne.

Podobne dyskusje można znaleźć w omówieniu zarządzania przerwami na końcu rozdziału 3.

> [!NOTE]
> Jeśli blokada przerwania ma być używana do ochrony krytycznych sekcji kodu sterownika z poziomu procedury ISR sterownika, kod sterownika poziomu wątku musi zawsze być wykonywany na tym samym rdzeniu, w którym jest przetwarzany proces ISR. W przeciwnym razie podstawowe elementy podstawowe SMP ThreadX, takie jak TX_DISABLE i TX_RESTORE, powinny być używane, które również mają wbudowaną ochronę międzyrdzeniową.

### <a name="thread-suspension"></a>Zawieszenie wątku 
W prostym przykładzie sterownika przedstawionym wcześniej w tym rozdziale, obiekt wywołujący usługi wejściowej zawiesza się, jeśli znak nie jest dostępny. W niektórych aplikacjach może to nie być akceptowalne.

Na przykład jeśli wątek odpowiedzialny za przetwarzanie danych wejściowych z sterownika również ma inne obowiązki, wstrzymanie tylko wejścia sterownika prawdopodobnie nie będzie działało. Zamiast tego sterownik należy dostosować do przetwarzania żądania podobnego do sposobu, w jaki inne żądania przetwarzania są wykonywane do wątku.

W większości przypadków bufor wejściowy jest umieszczany na połączonej liście, a wejściowy komunikat zdarzenia jest wysyłany do kolejki wejściowej wątku.