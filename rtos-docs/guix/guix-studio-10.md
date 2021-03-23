---
title: Prosty przykładowy projekt
description: W tym rozdziale opisano sposób tworzenia przykładowego projektu w programie GUIX Studio i wykonywania przykładu na GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3661396f097e0ed7bd872fae01a7bec9212001b9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822332"
---
# <a name="chapter-10-example-project"></a>Rozdział 10: przykładowy projekt

W tym rozdziale opisano sposób tworzenia przykładowego projektu w programie GUIX Studio i wykonywania przykładu na GUIX.

## <a name="create-new-project"></a>Tworzenie nowego projektu

Pierwszym krokiem jest utworzenie nowego projektu i skonfigurowanie ekranów i języków, które będą obsługiwane przez projekt. Po pierwszym uruchomieniu GUIX Studio zobaczysz ekran ***ostatnie projekty*** :

![Zrzut ekranu przedstawiający okno dialogowe GUIX Studio ostatnich projektów.](./media/guix-studio/recent_projects.png)

**Rysunek 10,1**

Kliknij pozycję ***Utwórz nowy projekt** _... , aby rozpocząć nowy projekt. Zostanie wyświetlone okno dialogowe _ *_New GUIX Project_**, pokazane tutaj:

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie nowego projektu w programie GUIX Studio.](./media/guix-studio/create_new_project.png)

**Rysunek 10,2**

Wpisz nazwę "***new_example***" jako nazwę projektu. Nazwy projektów powinny zawierać standardowe reguły nazewnictwa języka C, czyli nie znaki specjalne ani zastrzeżone. Wpisz ścieżkę do lokalizacji, w której ma być zapisany projekt. Ścieżka musi być prawidłowym katalogiem systemu plików, czyli GUIX Studio nie utworzy katalogu, jeśli nie istnieje. Kliknij przycisk OK, aby utworzyć projekt.

Następnym wyświetlonym ekranem jest ekran Konfiguracja projektu, przedstawiony tutaj:

![Zrzut ekranu przedstawiający okno dialogowe Konfigurowanie projektu programu GUIX Studio.](./media/guix-studio/config_new_project.png)

**Rysunek 10,3**

To okno dialogowe pozwala określić, ile wyświetla projekt będzie obsługiwał, i nadaj nazwę każdemu wyświetlaczowi. Należy określić format koloru obsługiwany przez każdy ekran i opcjonalnie wpisać nazwę ścieżki dla plików wyjściowych generowanych przez Studio dla każdego ekranu. Domyślnym katalogiem plików wyjściowych jest "***. \\***", co oznacza, że pliki wyjściowe C są zapisywane w tym samym katalogu co projekt.

Na potrzeby tego przykładu pozostaw ***liczba wyświetleń** _ o wartości "1", wpisz nazwę "_*_main_display_*_" w polu Nazwa wyświetlana i zaznacz opcję "_*_Przydziel pamięć kanwy_*_". Pozostaw wartości domyślne w polach rozdzielczość, format koloru i katalog, a następnie kliknij _ *_OK_* *.

Zobaczysz teraz projekt otwarty za pomocą środowiska IDE programu Studio, jak pokazano na rysunku 10,4:

![Zrzut ekranu projektu otwarty za pomocą programu Studio IDE.](./media/guix-studio/initial_screen.png)

**Rysunek 10,4**

Podczas tworzenia nowego projektu GUIX Studio automatycznie tworzy domyślne okno jako punkt początkowy dla projektu. To szare pole jest domyślnym oknem utworzonym dla Ciebie, wyśrodkowanym w *widoku docelowym*.

Jeśli to okno nie jest zaznaczone, kliknij okno, aby narysować kreskowane pole zaznaczenia wokół okna. Teraz w widoku ***Właściwości** _ Zmień _*_nazwę widżetu_*_, _*_identyfikator widżetu_*_, _*_lewy_*_, _*_górny_*_, _*_Szerokość_*_, _*_wysokość_*_ i _ *_obramowanie_**, aby dopasować te ustawienia poniżej. Po wprowadzeniu tych zmian w widoku docelowym powinny zostać wyświetlone zmiany od razu.

![Zrzut ekranu przedstawiający okno dialogowe Widok właściwości.](./media/guix-studio/initial_window_properties.png)

**Rysunek 10,5**

Następnie dodamy zasób Pixelmap, który będzie używany w elemencie widget ***GX_ICON** _. Dla tego przykładu udostępniono kilka ikon z dystrybucją programu GUIX Studio. Rozwiń _*_Pixelmaps_*_ widok zasobów i kliknij przycisk _ *_Dodaj nowy Pixelmap_**:

![Zrzut ekranu przedstawiający przycisk Dodaj nowy Pixelmap.](./media/guix-studio/image74.jpg)

Przejdź do folderu instalacji programu GUIX Studio i w folderze ***./Graphics/Icons** _ wybierz plik o nazwie _*_i_history_lg.png_*_. Kliknij przycisk _*_Otwórz_*_ , aby dodać ten zasób do projektu. Element _ *_Pixelmaps_** widok zasobów powinien teraz zawierać Podgląd nowo dodanego obrazu ikony:

![Zrzut ekranu przedstawiający Widok zasobów Pixelmaps.](./media/guix-studio/example_add_pixelmap.png)

**Rysunek 10,6**

Nowy zasób obrazu zostanie użyty później w ramach naszego projektu interfejsu użytkownika.

Podobnie jak w przypadku dodawania zasobów Pixelmap, dodamy nowy zasób czcionki do naszego przybornika, aby można było użyć tej czcionki w dalszej części tego projektu. Rozwiń pozycję ***Fonts** _ widok zasobów i kliknij przycisk _*_Dodaj nową czcionkę_*_ . Ta akcja spowoduje wywołanie okna dialogowego _*_Dodawanie/edytowanie_*_ czcionki. Następnie przejdź do dostarczonych czcionek GUIX w folderze instalacyjnym programu GUIX Studio _*_ . \\ czcionki \\ verasans_ *_ i wybierz plik czcionek TrueType o nazwie _*_VeraIt. ttf_*_. Wpisz Font nazwa czcionki "_*_MEDIUM_ITALIC_*_" w polu Nazwa czcionki i wpisz "_*_30_* *" w polu height. Okno dialogowe powinno teraz wyglądać następująco:

![Zrzut ekranu przedstawiający okno dialogowe Edycja czcionki.](./media/guix-studio/example_add_font.png)

**Rysunek 10,7**

Kliknij przycisk ***OK*** , aby dodać tę czcionkę do projektu. Teraz powinna zostać wyświetlona Czcionka w Widok zasobów:

![Zrzut ekranu przedstawiający czcionki w Widok zasobów.](./media/guix-studio/example_font_added.png)

**Rysunek 10,8**

Będziemy używać nowej czcionki później w naszym projekcie interfejsu użytkownika.

Teraz, gdy dostępne są nowe zasoby, musimy dodać do naszego ekranu elementy widgetowe, które mogą korzystać z tych zasobów. Wybierz wcześniej utworzone okno o nazwie "***hello_world** _", klikając prawym przyciskiem myszy okno w widoku docelowym. W wyświetlonym menu podręcznym wybierz polecenie menu _*_Wstaw, tekst, Monituj,_*_ aby wstawić nowy _ *_GX_PROMPT_** widżet i dołączyć widżet do okna tła. Okno powinno teraz wyglądać następująco:

![Zrzut ekranu przedstawiający menu podręczne z wybranym monitem](./media/guix-studio/image78.jpg)

**Rysunek 10,9**

Kliknij czcionkę o nazwie "***MEDIUM_ITALIC** _" w polu _ *_fonts_** widok zasobów i przeciągnij czcionkę i upuść ją w widżecie monit. Następnie Edytuj właściwości monitu, jak pokazano na rysunku 10,10 Aby zmienić rozmiar monitu, ustaw przezroczystość monitu i Zmień tekst i styl monitu:

![Zrzut ekranu przedstawiający widok właściwości dla monitu.](./media/guix-studio/image79.jpg)

**Rysunek 10,10**

Może być konieczne przewinięcie w pionie w widoku właściwości, aby zobaczyć wszystkie te ustawienia w zależności od rozdzielczości ekranu. Po wprowadzeniu tych zmian widok docelowy powinien teraz wyglądać następująco:

![Zrzut ekranu przedstawiający menu podręczne z zaznaczonym Hello world.](./media/guix-studio/image80.jpg)

**Rysunek 10,11**

Następnie umieścimy widżet styl przycisku ikony na ekranie. Zaznacz okno tła, klikając je, a następnie użyj menu najwyższego poziomu lub menu podręcznego kliknij prawym przyciskiem myszy, aby wybrać pozycję ***Wstaw, przycisk, przycisk ikony** _, aby dodać nową _*_GX_ICON_BUTTON_*_ do okna. Kliknij ikonę o nazwie _ *_I_HISTORY_LG_**, która została dodana wcześniej i przeciągnij ją na przycisk ikony. Korzystając z widoku właściwości, Dostosuj położenie i rozmiar ikony, tak jak pokazano poniżej:

![Zrzut ekranu przedstawiający widok Właściwości widżet stylu przycisku ikony.](./media/guix-studio/image81.jpg)

**Rysunek 10,12**

Ekran powinien teraz wyglądać następująco:

![Zrzut ekranu przedstawiający menu podręczne z ikoną Hello world i Schowka.](./media/guix-studio/image82.jpg)

**Rysunek 10,13**

Zostanie to wykonane dla prostego przykładowego projektu ekranu. Rzeczywiste ekrany aplikacji prawdopodobnie będą znacznie bardziej zaawansowane, ale wystarczy, aby zobaczyć, jak używać programu GUIX Studio do tworzenia własnych ekranów aplikacji.

## <a name="generate-resource-and-application-code"></a>Generowanie kodu zasobu i aplikacji

Następnym krokiem jest utworzenie pliku zasobów i pliku specyfikacji, który definiuje osadzony interfejs użytkownika czasu wykonywania GUIX. Aby wygenerować pliki wyjściowe, należy kliknąć prawym przyciskiem myszy węzeł ***main_display** _ w widoku projektu i wybrać polecenie _ *_Generuj pliki zasobów_**. Zobaczysz okno informacji wskazujące pliki zasobów, które zostały wygenerowane, jak pokazano na rysunku 10,14:

![Zrzut ekranu okna dialogowego powiadomienia.](./media/guix-studio/image83.jpg)

**Rysunek 10,14**

Kliknij przycisk ***OK**, aby odrzucić to powiadomienie, i Użyj tej samej procedury, aby kliknąć prawym przyciskiem myszy węzeł _*_main_display_*_ i wybierz polecenie _ *_Generuj pliki specyfikacji_**. Należy obserwować podobne okno powiadomień. Pliki prostej aplikacji interfejsu użytkownika zostały już wygenerowane.

## <a name="create-user-supplied-code"></a>Utwórz kod dostarczony przez użytkownika

Następnym krokiem jest utworzenie własnego pliku aplikacji, który wywoła projekt ekranu wygenerowany przez program GUIX Studio. Korzystając z preferowanego edytora, Utwórz plik źródłowy o nazwie ***new_example. c*** i wprowadź następujący kod źródłowy do tego pliku:

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

Powyższy kod źródłowy tworzy typowy wątek ThreadX o nazwie `GUIX New Example Thread` o rozmiarze 4 KB. Interesujące zadania zaczynają się w funkcji o nazwie ***new_example_thread_entry***. Ta funkcja to miejsce, w którym rozpoczyna się GUIX określony wątek.

Pierwsze wywołanie jest funkcją o nazwie ***gx_system_initialize***. To wywołanie jest zawsze wymagane, zanim inne interfejsy API GUIX są wywoływane w celu przygotowania biblioteki GUIX do pierwszego użycia.

Następnie przykład wywołuje funkcję ***gx_studio_display_configure***. Ta funkcja tworzy wystąpienie wyświetlania GUIX, instaluje żądany język tabeli ciągów aplikacji, instaluje żądany motyw z zasobów wyświetlanych i zwraca wskaźnik do głównego okna, które zostało utworzone dla tego ekranu. Główne okno służy jako element nadrzędny wszystkich ekranów najwyższego poziomu, które będą wyświetlane w aplikacji.

Kolejne przykładowe wywołania ***gx_studio_named_widget_create** _ w celu utworzenia wystąpienia naszego ekranu _ *_hello_world_**. Ta funkcja korzysta ze struktur danych i zasobów wytwarzanych przez program GUIX Studio, aby utworzyć wystąpienie ekranu, zgodnie z definicją. Przekazujemy wskaźnik głównego okna jako drugi parametr do tego wywołania funkcji, co oznacza, że ekran ma być natychmiast dołączony do okna głównego. Ostatni parametr jest opcjonalnym wskaźnikiem powrotu, którego można użyć, jeśli chcemy zachować wskaźnik do tworzonego ekranu.

Następny ***gx_widget_show** _ jest wywoływany, co sprawia, że główne okno i wszystkie jego elementy podrzędne, w tym ekran _ *_hello_world_**, widoczne.

Na koniec przykład wywołuje ***gx_system_start***. Ta funkcja rozpoczyna wykonywanie pętli przetwarzania zdarzeń systemu GUIX.

## <a name="build-and-run-the-example"></a>Kompiluj i uruchamiaj przykład

Kompilowanie i uruchamianie przykładu jest specyficzne dla narzędzi i środowiska kompilacji. Można jednak zdefiniować ogólny proces:

1. Tworzenie nowego katalogu i projektu aplikacji
1. Dodaj te pliki do projektu:

    **new_example_resources. c**

    **new_example_specification. c**

    **new_example. c**

1. Dodaj pliki obsługi środowiska uruchomieniowego Win32 ze ścieżki instalacji programu GUIX Studio ***./win32_runtime***. Obejmuje to nagłówek Win32 i pliki bibliotek uruchomieniowych ThreadX i GUIX.
1. Dodawanie biblioteki Win32 GUIX (***GX. lib***) do projektu
1. Dodawanie biblioteki Win32 ThreadX (***TX. lib***) do projektu
1. Kompiluj, łącz i uruchamiaj aplikację.
