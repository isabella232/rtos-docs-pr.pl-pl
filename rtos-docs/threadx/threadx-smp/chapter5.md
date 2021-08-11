---
title: Rozdział 5 — Sterowniki urządzeń dla Azure RTOS ThreadX SMP
description: Ten rozdział zawiera opis sterowników urządzeń dla Azure RTOS ThreadX SMP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 706ad47b2c3e7b2979da7262a4de8d681f4fbc53cb1af59a798b34094734060b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792347"
---
# <a name="chapter-5---device-drivers-for-azure-rtos-threadx-smp"></a>Rozdział 5 — Sterowniki urządzeń dla Azure RTOS ThreadX SMP

Ten rozdział zawiera opis sterowników urządzeń dla Azure RTOS ThreadX SMP. Informacje przedstawione w tym rozdziale mają ułatwić deweloperom pisanie sterowników specyficznych dla aplikacji. 

## <a name="device-driver-introduction"></a>Wprowadzenie do sterowników urządzeń

Komunikacja ze środowiskiem zewnętrznym jest ważnym składnikiem większości aplikacji osadzonych. Ta komunikacja jest realizowane za pośrednictwem urządzeń sprzętowych, które są dostępne dla osadzonego oprogramowania aplikacji. Składniki oprogramowania odpowiedzialne za zarządzanie takimi urządzeniami są często nazywane *sterownikami urządzeń.*

Sterowniki urządzeń w systemach osadzonych w czasie rzeczywistym są z założenia zależne od aplikacji. Jest to prawdziwe z dwóch głównych powodów: ogromnej różnorodności sprzętu docelowego i równie ogromnych wymagań dotyczących wydajności nakładanych na aplikacje w czasie rzeczywistym. W związku z tym praktycznie niemożliwe jest zapewnienie wspólnego zestawu sterowników, które będą spełniać wymagania każdej aplikacji. Z tego powodu informacje zawarte w tym rozdziale mają na celu pomoc użytkownikom w dostosowywaniu sterowników urządzeń *ThreadX* SMP i pisaniu własnych sterowników.

## <a name="driver-functions"></a>Funkcje sterowników

Sterowniki urządzeń ThreadX SMP składają się z ośmiu podstawowych obszarów funkcjonalnych w następujący sposób:

- **Inicjowanie sterownika**
- **Kontrola sterowników**
- **Dostęp dla sterowników**
- **Dane wejściowe sterownika**
- **Dane wyjściowe sterownika**
- **Przerwania sterownika**
- **Stan sterownika**
- **Zakończenie działania sterownika**

Z wyjątkiem inicjowania, każdy obszar funkcjonalny sterownika jest opcjonalny. Ponadto dokładne przetwarzanie w każdym obszarze jest specyficzne dla sterownika urządzenia.

### <a name="driver-initialization"></a>Inicjowanie sterownika 
Ten obszar funkcjonalny jest odpowiedzialny za inicjowanie rzeczywistego urządzenia sprzętowego i wewnętrznych struktur danych sterownika. Wywoływanie innych usług sterowników jest niedozwolone do momentu ukończenia inicjowania.

> [!IMPORTANT]
> Składnik funkcji inicjowania sterownika jest zwykle wywoływany z tx_application_define **lub** z wątku inicjalizacji.

### <a name="driver-control"></a>Kontrola sterowników 
Po zainicjowaniu sterownika i przygotowaniu go do działania ten obszar funkcjonalny jest odpowiedzialny za kontrolę w czasie działania. Zazwyczaj kontrola w czasie rzeczywistym obejmuje wprowadzenie zmian w bazowym urządzeniu sprzętowym. Przykłady obejmują zmianę szybkości transmisji urządzenia szeregowego lub szukanie nowego sektora na dysku.

### <a name="driver-access"></a>Dostęp dla sterowników 
Niektóre sterowniki urządzeń są wywoływane tylko z jednego wątku aplikacji. W takich przypadkach ten obszar funkcjonalny nie jest potrzebny. Jednak w aplikacjach, w których wiele wątków wymaga jednoczesnego dostępu sterowników, interakcje z nimi muszą być kontrolowane przez dodanie funkcji przypisywania/zwalniania w sterowniku urządzenia. Alternatywnie aplikacja może używać semafora do kontrolowania dostępu sterowników i uniknięcia dodatkowych narzutów i komplikacji wewnątrz sterownika. 

### <a name="driver-input"></a>Dane wejściowe sterownika 
Ten obszar funkcjonalny jest odpowiedzialny za wszystkie dane wejściowe urządzenia. Główne problemy związane z wprowadzaniem sterowników zwykle obejmują sposób buforowania danych wejściowych i sposób oczekiwania wątków na takie dane wejściowe. 

### <a name="driver-output"></a>Dane wyjściowe sterownika 
Ten obszar funkcjonalny jest odpowiedzialny za wszystkie dane wyjściowe urządzenia. Główne problemy związane z wyjściem sterownika zwykle obejmują sposób buforowania danych wyjściowych i sposób oczekiwania wątków na wykonanie danych wyjściowych. 

### <a name="driver-interrupts"></a>Przerwania sterownika 
Większość systemów czasu rzeczywistego korzysta z przerwań sprzętowych w celu powiadamiania sterownika o zdarzeniach wejścia, wyjścia, kontroli i błędów urządzenia. Przerwania zapewniają gwarantowany czas odpowiedzi na takie zdarzenia zewnętrzne. Zamiast przerwań oprogramowanie sterowników może okresowo sprawdzać sprzęt zewnętrzny pod względu na takie zdarzenia. Ta technika jest nazywana *sondą*. Jest mniej czasu rzeczywistego niż przerwań, ale sondowanie może mieć sens w przypadku niektórych aplikacji mniej czasu rzeczywistego. 

### <a name="driver-status"></a>Stan sterownika 
Ten obszar funkcji jest odpowiedzialny za zapewnienie stanu środowiska uruchomieniowego i statystyk skojarzonych z operacją sterownika. Informacje zarządzane przez ten obszar funkcji zwykle obejmują następujące elementy: 
- Bieżący stan urządzenia
- Bajty wejściowe
- Bajty wyjściowe
- Liczba błędów urządzeń

### <a name="driver-termination"></a>Zakończenie działania sterownika 
Ten obszar funkcjonalny jest opcjonalny. Jest to wymagane tylko wtedy, gdy trzeba zamknąć sterownik i/lub fizyczne urządzenie sprzętowe. Po zakończeniu pracy sterownik nie może zostać ponownie wywołany, dopóki nie zostanie ponownie zainicjowany. 

## <a name="simple-driver-example"></a>Prosty przykład sterownika

Przykładem jest najlepszy sposób opisania sterownika urządzenia. W tym przykładzie sterownik zakłada proste szeregowe urządzenie sprzętowe z rejestrem konfiguracji, rejestrem wejściowym i rejestrem danych wyjściowych. Ten prosty przykład sterownika ilustruje obszary funkcjonalne inicjalizacji, danych wejściowych, wyjściowych i przerwania.

### <a name="simple-driver-initialization"></a>Proste inicjowanie sterownika 
Funkcja ***tx_sdriver_initialize*** prostego sterownika tworzy dwa zliczanie semaforów, które są używane do zarządzania operacją wejściową i wyjściową sterownika. Semafor danych wejściowych jest ustawiany przez wejściowy isr po otrzymaniu znaku przez szeregowe urządzenie sprzętowe. W związku z tym semafor danych wejściowych jest tworzony z początkową licznikiem o wartości zero.

Z kolei semafor danych wyjściowych wskazuje dostępność szeregowego rejestru przesyłania sprzętu. Jest on tworzony z wartością 1, aby wskazać, że rejestr przesyłania jest początkowo dostępny.

Funkcja inicjowania jest również odpowiedzialna za instalowanie programów obsługi wektorów przerwań niskiego poziomu dla powiadomień wejściowych i wyjściowych. Podobnie jak w przypadku innych procedur usługi przerwania SMP ThreadX, procedura obsługi niskiego poziomu musi wywołać ***_tx_thread_context_save** _ przed wywołaniem prostego sterownika ISR. Po powrocie sterownika isr, procedura obsługi niskiego poziomu musi wywołać _*_ _tx_thread_context_restore_**.

> [!IMPORTANT]
> Ważne jest, aby inicjowanie było wywoływane przed dowolną z innych funkcji sterownika. Zazwyczaj inicjowanie sterownika jest wywoływane **z** tx_application_define .

Zobacz rysunek 9 na stronie 306, aby uzyskać kod źródłowy inicjowania prostego sterownika.

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
**RYSUNEK 9. Proste inicjowanie sterownika**

### <a name="simple-driver-input"></a>Proste dane wejściowe sterownika 
Dane wejściowe dla prostych sterowników są wyśrodkowyne wokół semafora wejściowego. Po otrzymaniu przerwania wejściowego urządzenia szeregowego ustawiany jest semafor danych wejściowych. Jeśli co najmniej jeden wątek oczekuje na znak ze sterownika, najdłużej oczekujący wątek jest wznawiany. Jeśli żadne wątki nie oczekują, semafor pozostaje ustawiony, dopóki wątek nie wywoła funkcji wejściowej dysku.

Istnieje kilka ograniczeń dotyczących prostej obsługi danych wejściowych sterownika. Najbardziej istotna jest możliwość porzucania znaków wejściowych. Jest to możliwe, ponieważ nie ma możliwości buforowania znaków wejściowych, które docierają przed przetworzeniem poprzedniego znaku. Jest to łatwo obsługiwane przez dodanie buforu znaków wejściowych.

> [!IMPORTANT]
> Tylko wątki mogą wywołać funkcję **tx_sdriver_input.**

Rysunek 10 przedstawia kod źródłowy skojarzony z prostymi wejściami sterownika.

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
**RYSUNEK 10. Proste dane wejściowe sterownika**

### <a name="simple-driver-output"></a>Proste dane wyjściowe sterownika 
Przetwarzanie danych wyjściowych wykorzystuje semafor danych wyjściowych do sygnalizowania, kiedy rejestr przesyłania urządzenia szeregowego jest wolny. Zanim znak wyjściowy zostanie faktycznie zapisany na urządzeniu, jest uzyskiwany semafor danych wyjściowych. Jeśli nie jest on dostępny, poprzedni przekaz nie jest jeszcze ukończony.

Wyjściowy isr jest odpowiedzialny za obsługę przekazywania pełne przerwanie. Przetwarzanie danych wyjściowych isr ilości do ustawiania semafora danych wyjściowych, dzięki czemu dane wyjściowe innego znaku.

> [!IMPORTANT]
> Tylko wątki mogą wywołać funkcję **tx_sdriver_output.**

Rysunek 11 przedstawia kod źródłowy skojarzony z prostymi wynikami sterownika.

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
**RYSUNEK 11. Proste dane wyjściowe sterownika**

### <a name="simple-driver-shortcomings"></a>Proste wady sterowników 
Ten prosty przykład sterownika urządzenia ilustruje podstawową ideę sterownika urządzenia ThreadX SMP. Jednak ponieważ prosty sterownik urządzenia nie obsługuje buforowania danych ani żadnych problemów z obciążeniem, nie reprezentuje w pełni rzeczywistych sterowników SMP ThreadX. W poniższej sekcji opisano niektóre bardziej zaawansowane problemy związane ze sterownikami urządzeń.

## <a name="advanced-driver-issues"></a>Zaawansowane problemy ze sterownikami

Jak wspomniano wcześniej, wymagania dotyczące sterowników urządzeń są tak unikatowe jak ich aplikacje. Niektóre aplikacje mogą wymagać ogromnej ilości buforowania danych, podczas gdy inna aplikacja może wymagać zoptymalizowanych sterowników isr z powodu przerwań urządzenia o wysokiej częstotliwości.

### <a name="io-buffering"></a>Buforowanie we/wy 
Buforowanie danych w aplikacjach osadzonych w czasie rzeczywistym wymaga znacznego planowania. Część projektu jest określana przez podstawowe urządzenie sprzętowe. Jeśli urządzenie udostępnia podstawowe bajtowe we/wy, prawdopodobnie uporządkowany jest prosty bufor cykliczny. Jeśli jednak urządzenie udostępnia blokowe, DMA lub we/wy pakietów, prawdopodobnie jest uzasadniany schemat zarządzania buforem. 

### <a name="circular-byte-buffers"></a>Cykliczne bufory bajtowe 
Cykliczne bufory bajtowe są zwykle używane w sterownikach, które zarządzają prostym szeregowym urządzeniem sprzętowym, na przykład UART. W takich sytuacjach najczęściej używane są dwa bufory cykliczne — jeden dla danych wejściowych i jeden dla danych wyjściowych.

Każdy cykliczny bufor bajtowy składa się z obszaru pamięci bajtowej (zazwyczaj tablicy WSKAŹNIKÓW), wskaźnika odczytu i wskaźnika zapisu. Bufor jest uznawany za pusty, gdy wskaźnik odczytu i wskaźniki zapisu odwołują się do tej samej lokalizacji pamięci w buforze. Inicjalizacja sterownika ustawia wskaźniki buforu odczytu i zapisu na początkowy adres buforu.

### <a name="circular-buffer-input"></a>Cykliczne dane wejściowe buforu 
Bufor wejściowy służy do przechowywania znaków, które docierają, zanim aplikacja będzie dla nich gotowa. Po otrzymaniu znaku wejściowego (zazwyczaj w procedurie usługi przerywania) nowy znak jest pobierany z urządzenia sprzętowego i umieszczany w buforze wejściowym w lokalizacji wskazywanej przez wskaźnik zapisu. Wskaźnik zapisu jest następnie zaawansowany do następnej pozycji w buforze. Jeśli następna pozycja znajduje się za końcem buforu, wskaźnik zapisu jest ustawiany na początek buforu. Pełny warunek kolejki jest obsługiwany przez anulowanie postępu wskaźnika zapisu, jeśli nowy wskaźnik zapisu jest taki sam jak wskaźnik odczytu.

Żądania bajtów wejściowych aplikacji do sterownika najpierw badają wskaźniki odczytu i zapisu buforu wejściowego. Jeśli wskaźniki odczytu i zapisu są identyczne, bufor jest pusty. W przeciwnym razie, jeśli wskaźnik odczytu nie jest taki sam, bajt wskazywany przez wskaźnik odczytu jest kopiowany z buforu wejściowego, a wskaźnik odczytu jest zaawansowany do następnej lokalizacji buforu. Jeśli nowy wskaźnik odczytu znajduje się za końcem buforu, jest resetowany do początku. Rysunek 12 przedstawia logikę cyklicznego bufora wejściowego.

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
**RYSUNEK 12. Logika cyklicznego bufora wejściowego**

> [!IMPORTANT]
> Aby operacja była niezawodna, może być konieczne zablokowanie przerwań podczas manipulowania wskaźnikami odczytu i zapisu buforów cyklicznych zarówno wejściowych, jak i wyjściowych.

### <a name="circular-output-buffer"></a>Cykliczny bufor wyjściowy 
Bufor wyjściowy służy do przechowywania znaków, które dotarły do danych wyjściowych przed zakończeniem wysyłania poprzedniego bajtu przez urządzenie sprzętowe. Przetwarzanie buforu wyjściowego jest podobne do przetwarzania buforu wejściowego, z tą różnicą, że pełne przetwarzanie przerwań przesyłania manipuluje wskaźnikiem odczytu danych wyjściowych, natomiast żądanie wyjściowe aplikacji wykorzystuje wyjściowy wskaźnik zapisu. W przeciwnym razie przetwarzanie buforu wyjściowego jest takie samo. Rysunek 13wdaje logikę cyklicznego buforu wyjściowego.

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

### <a name="buffer-io-management"></a>Zarządzanie we/wy buforu 
Aby poprawić wydajność osadzonych mikroprocesorów, wiele urządzeń peryferyjnych przesyła i odbiera dane z buforami dostarczonymi przez oprogramowanie. W niektórych implementacjach można użyć wielu buforów do przesyłania lub odbierania poszczególnych pakietów danych. 

Rozmiar i lokalizacja buforów We/Wy jest określana przez aplikację i/lub oprogramowanie sterowników. Zazwyczaj bufory mają stały rozmiar i są zarządzane w puli pamięci blokowej SMP ThreadX. Rysunek 14opisuje typowy bufor we/wy i pulę pamięci blokowej SMP ThreadX, która zarządza alokacją.

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
Typedef TX_IO_BUFFER składa się z dwóch wskaźników. Wskaźnik ***tx_next_packet** _ służy do łączenia wielu pakietów na liście danych wejściowych lub wyjściowych. Wskaźnik _ *_tx_next_buffer_** służy do łączenia ze sobą buforów, które sprawiają, że pojedynczy pakiet danych z urządzenia. Oba te wskaźniki są ustawione na wartość NULL, gdy bufor jest przydzielany z puli. Ponadto niektóre urządzenia mogą wymagać innego pola, aby wskazać, jaka część obszaru buforu faktycznie zawiera dane.

### <a name="buffered-io-advantage"></a>Buforowane korzyści we/wy 
Jakie są zalety schematu we/wy buforu? Największą zaletą jest to, że dane nie są kopiowane między rejestrami urządzenia a pamięcią aplikacji. Zamiast tego sterownik dostarcza urządzeniu serię wskaźników buforu. We/Wy urządzenia fizycznego bezpośrednio wykorzystuje dostarczoną pamięć bufora.

Użycie procesora do kopiowania pakietów wejściowych lub wyjściowych informacji jest niezwykle kosztowne i należy unikać w każdej sytuacji dużej przepływności we/wy.

Inną zaletą buforowanych we/wy jest to, że listy wejściowe i wyjściowe nie mają pełnych warunków. Wszystkie dostępne bufory mogą być na dowolnej liście w dowolnym momencie. Jest to przeciwieńsze proste bajtowe bufory cykliczne przedstawione wcześniej w rozdziale. Każdy z nich miał stały rozmiar określany podczas kompilacji.

### <a name="buffered-driver-responsibilities"></a>Buforowane obowiązki sterowników 
Buforowane sterowniki urządzeń dotyczą tylko zarządzania połączonymi listami buforów we/wy. Lista buforów wejściowych jest zachowywana dla pakietów odbieranych przed gotowością oprogramowania aplikacji. Z kolei lista buforów wyjściowych jest utrzymywana dla pakietów wysyłanych szybciej niż urządzenie sprzętowe może je obsłużyć. Rysunek 15 na stronie 314 przedstawia proste połączone listy danych wejściowych i wyjściowych pakietów danych oraz bufory, które się na nie nakładają.

![Buforowane obowiązki sterowników](media/image11.png)

**RYSUNEK 15. Input-Output listy**

Interfejs aplikacji ze sterownikami buforowanych z tym samym buforem we/wy. Podczas przesyłania oprogramowanie aplikacji zapewnia sterownikowi co najmniej jeden bufor do przesyłania. Gdy oprogramowanie aplikacji żąda danych wejściowych, sterownik zwraca dane wejściowe w buforach We/Wy.

> [!IMPORTANT]
> W niektórych aplikacjach przydatne może być skompilowanie interfejsu wejściowego sterownika, który wymaga, aby aplikacja wymieniała wolny bufor buforu wejściowego ze sterownika. Może to zmniejszyć część przetwarzania alokacji buforu wewnątrz sterownika.

### <a name="interrupt-management"></a>Zarządzanie przerwami 
W niektórych aplikacjach częstotliwość przerwań urządzenia może zabraniać zapisywania isr w języku C lub interakcji z threadX SMP na każdym przerwaniu. Jeśli na przykład zapisanie i przywrócenie przerwanego kontekstu zajmuje 25us, nie zaleca się wykonania pełnego zapisu kontekstu, jeśli częstotliwość przerwań wynosi 50us. W takich przypadkach do obsługi większości przerwań urządzenia jest używany niewielki język zestawu ISR. Ten lowoverhead ISR będzie współdziałać z SMP ThreadX tylko wtedy, gdy jest to konieczne.

Podobne omówienie można znaleźć w dyskusji na temat zarządzania przerwami na końcu rozdziału 3.

> [!NOTE]
> Jeśli blokada przerwań ma być używana do ochrony krytycznych sekcji kodu sterownika przed kodem ISR sterownika, kod sterownika na poziomie wątku musi być zawsze wykonywany na tym samym rdzeniu, na który jest przetwarzany isr. W przeciwnym razie należy użyć wewnętrznych elementów pierwotnych SMP ThreadX, takich jak TX_DISABLE i TX_RESTORE, które również mają wbudowaną ochronę między rdzeniami.

### <a name="thread-suspension"></a>Zawieszenie wątku 
W prostym przykładzie sterownika przedstawionym wcześniej w tym rozdziale wywołujący usługę wejściową zawiesza się, jeśli znak jest niedostępny. W niektórych aplikacjach może to być niedopuszczalne.

Jeśli na przykład wątek odpowiedzialny za przetwarzanie danych wejściowych od sterownika ma również inne obowiązki, wstrzymanie tylko danych wejściowych sterownika prawdopodobnie nie będzie działać. Zamiast tego sterownik należy dostosować do przetwarzania żądań podobny do sposobu, w jaki inne żądania przetwarzania są dokonywane do wątku.

W większości przypadków bufor wejściowy jest umieszczany na połączonej liście, a komunikat zdarzenia wejściowego jest wysyłany do kolejki wejściowej wątku.