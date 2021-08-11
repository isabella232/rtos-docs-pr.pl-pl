---
title: Prosty przykładowy Project
description: W tym rozdziale opisano sposób tworzenia przykładowego projektu w programie GUIX Studio i wykonywania przykładu w graficznym interfejsie użytkownika.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 8981bed62d2929703e4233d6a3ee31b692226c26d046875a235bf3aca32a7573
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786655"
---
# <a name="chapter-10-example-project"></a>Rozdział 10. Przykładowa Project

W tym rozdziale opisano sposób tworzenia przykładowego projektu w programie GUIX Studio i wykonywania przykładu w graficznym interfejsie użytkownika.

## <a name="create-new-project"></a>Tworzenie nowego projektu

Pierwszym krokiem jest utworzenie nowego projektu i skonfigurowanie języków i wyświetlanych w projekcie. Po pierwszym uruchomieniu programu GUIX Studio zostanie wyświetlony ekran ***Ostatnie projekty:***

![Zrzut ekranu przedstawiający okno dialogowe GuiX Studio Recent Projects (Ostatnie projekty w programie GUIX Studio).](./media/guix-studio/recent_projects.png)

**Rysunek 10.1**

Kliknij pozycję ***Utwórz nowy Project** _... , aby rozpocząć nowy projekt. Zostanie wyświetlone okno dialogowe *__New GUIX Project_** (Nowy interfejs GUIX), które pokazano poniżej:

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie nowego Project GUIX Studio.](./media/guix-studio/create_new_project.png)

**Rysunek 10.2**

Wpisz nazwę "***new_example***" jako nazwę projektu. Project nazwy powinny używać standardowych reguł nazewnictwa zmiennych języka C, czyli znaków specjalnych ani zastrzeżonych. Wpisz ścieżkę do lokalizacji, w której ma zostać zapisany projekt. Ścieżka musi być prawidłowym katalogiem systemu plików, co oznacza, że program GUIX Studio nie utworzy katalogu, jeśli nie istnieje. Kliknij przycisk "OK", aby utworzyć projekt.

Następny wyświetlany ekran to ekran konfiguracji Project, pokazany poniżej:

![Zrzut ekranu przedstawiający okno dialogowe konfigurowanie Project GUIX Studio.](./media/guix-studio/config_new_project.png)

**Rysunek 10.3**

To okno dialogowe umożliwia określenie, ile ekranów będzie obsługinych przez projekt, i nadaj nazwę każdemu wyświetlanemu ekranowi. Należy określić format kolorów obsługiwany przez każdy ekran i opcjonalnie wpisać nazwę ścieżki dla plików wyjściowych generowanych przez program Studio dla każdego ekranu. Domyślny katalog plików wyjściowych to "***. \\***", co oznacza, że pliki wyjściowe języka C są zapisywane w tym samym katalogu co sam projekt.

W tym przykładzie pozostaw wartość ***Liczba** ekranów _ ustawioną na "1", wpisz nazwę "_*_main_display_*_" w polu nazwy wyświetlanej i zaznacz pole "_*_przydziel_*_ pamięć kanwy ". Pozostaw wartości domyślne w polach rozpoznawania, formatu kolorów i katalogu, a następnie kliknij przycisk _*_OK_**.

Projekt powinien być teraz otwarty w środowiskach IDE programu Studio, jak pokazano na rysunku 10.4:

![Zrzut ekranu przedstawiający projekt otwarty za pomocą środowiska IDE programu Studio.](./media/guix-studio/initial_screen.png)

**Rysunek 10.4**

Podczas tworzenia nowego projektu program GUIX Studio automatycznie tworzy okno domyślne jako punkt początkowy projektu. To szare pole jest domyślnym oknem utworzonym dla Ciebie, wyśrodkowane w *widoku docelowym*.

Jeśli to okno nie jest zaznaczone, kliknij je, aby wokół okna narysowane było pole wyboru kreskowane. Teraz w widoku ***właściwości** _zmień nazwę widżetu _*_,_*_ identyfikator _*_widżetu_*_ _*_,_*_ lewy , _*_górny,_*_ _*_górny,_*_ szerokość, _*_wysokość_*_ i *___* obramowanie *, aby dopasować te ustawienia, które przedstawiono poniżej. Gdy wprowadzasz te zmiany, zmiany powinny zostać natychmiast wprowadzone w widoku docelowym.

![Zrzut ekranu przedstawiający okno dialogowe Widok właściwości.](./media/guix-studio/initial_window_properties.png)

**Rysunek 10.5**

Następnie dodamy zasób pixelmap, który będzie używany w **widżecie*** GX_ICON _. Z dystrybucją programu GUIX Studio jest dostarczanych kilka ikon, które będą działać prawidłowo w tym przykładzie. Rozwiń _*_kartę Pixelmaps_*_ Widok zasobów kliknij przycisk _ *_Dodaj nową_* mapę pikseli *:

![Zrzut ekranu przedstawiający przycisk Dodaj nową mapę pikseli.](./media/guix-studio/image74.jpg)

Przejdź do folderu instalacyjnego programu GUIX Studio, a następnie w folderze ***./graphics/icons** _ wybierz plik o _*_nazwiei_history_lg.png_*_. Kliknij _*_przycisk Otwórz,_*_ aby dodać ten zasób do projektu. W twoim pliku _ *_Pixelmaps_** Widok zasobów powinien teraz zostać wyświetlony podgląd nowo dodanego obrazu ikony:

![Zrzut ekranu przedstawiający mapę pikseli Widok zasobów.](./media/guix-studio/example_add_pixelmap.png)

**Rysunek 10.6**

Użyjemy tego nowego zasobu obrazu później w ramach naszego projektu interfejsu użytkownika.

Podobnie jak w przypadku dodawania zasobu pixelmap, dodamy nowy zasób czcionki do naszego przybornika, aby można było użyć tej czcionki w dalszej części naszego projektu. Rozwiń **ikonę*** Czcionki _ Widok zasobów i kliknij przycisk _*_Dodaj nową czcionkę._*_ Ta akcja spowoduje wywołanie okna _*_dialogowego Dodaj/Edytuj_*_ czcionkę. Następnie przejdź do podanych czcionek GUIX w folderze instalacyjnym programu GUIX _*_ Studio. \\ czcionki \\ verasans_ *_, a następnie wybierz plik czcionki TrueType o nazwie _*_VeraIt.ttf._*_Wpisz czcionkę nazwa czcionki "_*_MEDIUM_ITALIC_" w polu nazwy czcionki, a następnie wpisz _"30_**" w polu height.** Okno dialogowe powinno teraz wyglądać tak:

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie czcionki.](./media/guix-studio/example_add_font.png)

**Rysunek 10.7**

Kliknij ***przycisk OK,*** aby dodać tę czcionkę do projektu. Powinna być teraz widać czcionkę w Widok zasobów:

![Zrzut ekranu przedstawiający czcionki w Widok zasobów.](./media/guix-studio/example_font_added.png)

**Rysunek 10.8**

Użyjemy tej nowej czcionki w dalszej części naszego projektu interfejsu użytkownika.

Teraz, gdy mamy już dostępne nowe zasoby, musimy dodać do ekranu niektóre podrzędne widżety, które mogą korzystać z tych zasobów. Wybierz utworzone wcześniej okno o nazwie "***hello_world** _", klikając prawym przyciskiem myszy okno w widoku docelowym. W wyświetlonym menu podręcznym wybierz polecenie menu _*_Wstaw, Tekst,_*_ Monituj, aby wstawić nowy widżet _ *_GX_PROMPT_** i dołączyć widżet do okna tła. Okno powinno teraz wyglądać tak:

![Zrzut ekranu przedstawiający menu podręczne z wyborem Monituj](./media/guix-studio/image78.jpg)

**Rysunek 10.9**

Kliknij czcionkę o nazwie "***MEDIUM_ITALIC** _" w obszarze _ *_Czcionki_** Widok zasobów, a następnie przeciągnij i upuść czcionkę w widżecie monitu. Następnie edytuj właściwości monitu, jak pokazano na rysunku 10.10, aby zmienić rozmiar monitu, ustawić przezroczystość monitu oraz zmienić tekst i styl monitu:

![Zrzut ekranu przedstawiający widok właściwości monitu.](./media/guix-studio/image79.jpg)

**Rysunek 10.10**

Może być konieczne przewinięcie w pionie w widoku właściwości, aby wyświetlić każde z tych ustawień w zależności od rozdzielczości ekranu. Po w związku z wprowadzeniem tych zmian widok docelowy powinien teraz wyglądać tak:

![Zrzut ekranu przedstawiający menu podręczne z Hello world menu podręcznego.](./media/guix-studio/image80.jpg)

**Rysunek 10.11**

Następnie na ekranie zostanie umieść widżet stylu przycisku ikony. Wybierz okno tła, klikając je, a następnie użyj menu najwyższego poziomu lub menu podręcznego dostępnego po kliknięciu prawym _**_ przyciskiem myszy, aby wybrać pozycję ***Wstaw, Przycisk,** Przycisk ikony _, aby dodać nową GX_ICON_BUTTON do okna. Kliknij ikonę o nazwie _ *_I_HISTORY_LG_** dodaną wcześniej i przeciągnij ją do przycisku ikony. Korzystając z widoku właściwości, dostosuj położenie i rozmiar ikony, jak podano poniżej:

![Zrzut ekranu przedstawiający widok właściwości widżetu stylu przycisku ikony.](./media/guix-studio/image81.jpg)

**Rysunek 10.12**

Ekran powinien teraz wyglądać tak:

![Zrzut ekranu przedstawiający menu podręczne z ikoną Hello world i schowka.](./media/guix-studio/image82.jpg)

**Rysunek 10.13**

Ta kompletna nazwa zostanie nazwana dla prostego przykładowego projektu ekranu. Rzeczywiste ekrany aplikacji będą prawdopodobnie znacznie bardziej zaawansowane, ale to wystarczy, aby pokazać, jak używać programu GUIX Studio do tworzenia własnych ekranów aplikacji.

## <a name="generate-resource-and-application-code"></a>Generowanie kodu zasobu i aplikacji

Następnym krokiem jest wygenerowanie pliku zasobów i pliku specyfikacji definiującego osadzony interfejs użytkownika w czasie uruchamiania GUIX. Aby wygenerować pliki wyjściowe, kliknij prawym przyciskiem myszy węzeł ***main_display** _ w widoku Project, a następnie wybierz polecenie *___* Generuj pliki zasobów *. Zostanie wyświetlone okno informacji, które wskazuje, że pliki zasobów zostały wygenerowane, jak pokazano na rysunku 10.14:

![Zrzut ekranu przedstawiający okno dialogowe powiadomienia.](./media/guix-studio/image83.jpg)

**Rysunek 10.14**

Kliknij przycisk *** OK** _, aby odrzucić to powiadomienie, i użyj tej samej procedury, aby kliknąć prawym przyciskiem _*_myszy_*_ węzeł main_display i wybrać polecenie _ Generuj *_pliki specyfikacji_**. Powinno zostać zaobserwowane podobne okno powiadomień. Masz teraz wygenerowane proste pliki aplikacji interfejsu użytkownika.

## <a name="create-user-supplied-code"></a>Tworzenie kodu dostarczonego przez użytkownika

Następnym krokiem jest utworzenie własnego pliku aplikacji, który będzie wywoływać projekt ekranu wygenerowany przez program GUIX Studio. Za pomocą preferowanego edytora utwórz plik źródłowy o ***nazwie new_example.c*** i wprowadź w tym pliku następujący kod źródłowy:

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

Powyższy kod źródłowy tworzy typowy wątek ThreadX o nazwie `GUIX New Example Thread` o rozmiarze stosu 4K bajtów. Interesująca praca rozpoczyna się w funkcji o ***nazwie new_example_thread_entry***. W tej funkcji rozpoczyna się uruchamianie wątku specyficznego dla graficznego interfejsu użytkownika.

Pierwsze wywołanie jest wywołaniem funkcji o ***nazwie gx_system_initialize***. To wywołanie jest zawsze wymagane przed wywołaniem jakichkolwiek innych interfejsów API GUIX w celu przygotowania biblioteki GUIX do pierwszego użycia.

Następnie przykład wywołuje funkcję ***gx_studio_display_configure***. Ta funkcja tworzy wystąpienie wyświetlania GUIX, instaluje żądany język tabeli ciągów aplikacji, instaluje żądany motyw z zasobów wyświetlania i zwraca wskaźnik do głównego okna, które zostało utworzone dla tego wyświetlenia. Okno główne jest używane jako element nadrzędny wszystkich ekranów najwyższego poziomu, które będą wyświetlane w naszej aplikacji.

Następnie przykład wywołuje element ***gx_studio_named_widget_create** _, aby utworzyć wystąpienie naszego ekranu _ *_hello_world_**. Ta funkcja używa struktur danych i zasobów tworzymy przez program GUIX Studio, aby utworzyć wystąpienie ekranu zgodnie z jego definicją. Przekażemy wskaźnik okna głównego jako drugi parametr do wywołania tej funkcji, co oznacza, że chcemy, aby ekran był natychmiast dołączony do okna głównego. Ostatni parametr jest opcjonalnym wskaźnikiem powrotu, którego można użyć, jeśli chcemy zachować wskaźnik do utworzonego ekranu.

Następny ***gx_widget_show** _ jest wywoływany, co sprawia, że okno główne i wszystkie jego dzieci, w tym ekran _ *_hello_world_** , jest widoczny.

Na koniec przykład wywołuje ***gx_system_start***. Ta funkcja rozpoczyna wykonywanie pętli przetwarzania zdarzeń systemu GUIX.

## <a name="build-and-run-the-example"></a>Kompilowanie i uruchamianie przykładu

Kompilowanie i uruchamianie przykładu jest specyficzne dla narzędzi i środowiska kompilacji. Możemy jednak zdefiniować ogólny proces:

1. Tworzenie nowego projektu katalogu i aplikacji
1. Dodaj następujące pliki do projektu:

    **new_example_resources.c**

    **new_example_specification.c**

    **new_example.c**

1. Dodaj pliki obsługi systemu Win32 w czasie uruchamiania ze ścieżki instalacji programu GUIX Studio ***./win32_runtime***. Dotyczy to nagłówków ThreadX i GUIX Win32 oraz plików bibliotek uruchomieniowych.
1. Dodawanie biblioteki GUIX Win32 ***(gx.lib***) do projektu
1. Dodawanie biblioteki ThreadX Win32 ***(tx.lib***) do projektu
1. Skompiluj, połącz i uruchom aplikację!
