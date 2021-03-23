---
title: Azure Real-Time Operating System (RTO) GUIX Studio Przewodnik Szybki start
description: Ten przewodnik zawiera krótkie wprowadzenie do korzystania z aplikacji Azure RTO GUIX Studio, szybkiego środowiska programistycznego interfejsu użytkownika opartego na systemie Microsoft Windows przeznaczonego specjalnie dla biblioteki środowiska uruchomieniowego GUIX platformy Azure RTO firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 7/20/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: eedd53867b56312b53f4e9509136ee856acabfd7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823016"
---
# <a name="azure-rtos-guix-studio-quick-start-guide"></a>Usługa Azure RTO GUIX Studio Przewodnik Szybki start

Ten przewodnik zawiera krótkie wprowadzenie do korzystania z usługi Azure RTO GUIX Studio. GUIX Studio to oparta na systemie Windows aplikacja projektowania interfejsu użytkownika przeznaczona do użycia z biblioteką środowiska uruchomieniowego GUIX platformy Azure RTO firmy Microsoft. 

Jest ona przeznaczona dla wbudowanego dewelopera oprogramowania w czasie rzeczywistym przy użyciu systemu operacyjnego ThreadX Real-Time (RTO) i biblioteki wykonawczej interfejsu użytkownika platformy Azure RTO GUIX. Deweloper powinien znać standardowe pojęcia dotyczące platformy Azure RTO ThreadX i platformy Azure RTO GUIX.

## <a name="summary"></a>Podsumowanie

Usługa Azure RTO GUIX Studio zawiera wszystko, czego potrzebujesz, aby tworzyć, kompilować i uruchamiać własny projekt interfejsu graficznego. Jeśli oceniasz program GUIX Studio, zestaw ewaluacyjny został zaprojektowany tak, aby umożliwiać Kompilowanie i uruchamianie projektu GUIX jako autonomicznej aplikacji klasycznej systemu Windows na potrzeby testowania i oceny. Ponieważ GUIX jest przeznaczony do użycia na niemal dowolnym osadzonym miejscu docelowym, który umożliwia wykonywanie graficznych danych wyjściowych, wykonywane czynności i projekty tworzone na pulpicie zawsze mogą być kompilowane i uruchamiane w osadzonym miejscu docelowym bez zmiany oprogramowania aplikacji.
Instalator programu GUIX Studio umieszcza kilka składników w systemie deweloperskim:

- Aplikacja GUIX Studio.
- Kilka przykładowych projektów GUIX.
- Wszystkie zasoby grafiki i czcionki używane w przykładowych projektach.
- Pliki rozwiązań i pliki projektu do kompilowania w środowisku klasycznym systemu Windows przy użyciu Microsoft Visual Studio IDE.
- Wstępnie skompilowane biblioteki GUIX i ThreadX dla systemu Win32, dzięki czemu można tworzyć i uruchamiać własne aplikacje na komputerze.
- GUIX i ThreadX plików nagłówkowych interfejsu API.

## <a name="prerequisites"></a>Wymagania wstępne

Instalator usługi Azure RTO GUIX Studio zawiera kilka prostych przykładowych projektów. oczekujemy, że rozpocznie się od zmodyfikowania, skompilowania i uruchomienia tych przykładów, ponieważ dowiesz się, jak korzystać z aplikacji GUIX Studio. Aby można było skompilować i uruchomić przykłady na pulpicie systemu Windows, potrzebny będzie kompilator Microsoft Visual Studio. Te narzędzia można pobrać z następującej lokalizacji:

https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4

Jeśli nie masz zainstalowanych narzędzi programistycznych firmy Microsoft, możesz nadal uruchamiać te opony i korzystać z aplikacji GUIX Studio, aby utworzyć własny projekt interfejsu i przeanalizować utworzony kod źródłowy. Nie będzie jednak można kompilować i uruchamiać projektu jako aplikacji autonomicznej.

## <a name="running-the-examples"></a>Uruchamianie przykładów

Po uruchomieniu Instalatora programu GUIX Studio w zainstalowanej zawartości znajduje się kilka przykładowych projektów i plików kompilacji. Aby sprawdzić, czy narzędzia pulpitu są zainstalowane i działają prawidłowo, zalecamy rozpoczęcie od skompilowania i uruchomienia każdego z podanych przykładów jako-is. Odwołujemy się do katalogu instalacyjnego \<root> , w takim przypadku należy użyć przeglądarki plików i przeszukać \<root> /GUIX_Studio_6. x/przykłady. W tym katalogu powinny być widoczne kilka prostych przykładowych programów, takich jak demo_guix_calculator, demo_guix_car_infotainment, demo_guix__home_automation, demo_guix_widget_types i innych.

## <a name="building-an-example"></a>Tworzenie przykładu

Podkatalog o nazwie *Build* powinien znajdować się w każdym z przykładowych folderów. Ten kierunek obejmuje wstępnie skonfigurowane projekty dla każdego z obsługiwanych łańcucha narzędzi. Na przykład możesz przejść do \<root> /GUIX_Studio_6. x/przykłady/termometr/kompilacja/vs_2019 i znaleźć wstępnie skonfigurowany plik rozwiązania Microsoft Visual Studio i plik projektu, gotowy do załadowania i uruchomienia w środowisku IDE programu Visual Studio. Jeśli chcesz użyć innego łańcucha narzędzi, skontaktuj się z [azure_rtos_support](https://docs.microsoft.com/azure/azure-portal/supportability/how-to-create-azure-support-request#create-a-support-request).

Zalecamy uruchomienie Microsoft Visual C++ IDE i otwarcie co najmniej jednego z tych przykładów. Naciśnij klawisz \<F7> , aby skompilować przykładowy projekt, a następnie naciśnij klawisz, \<F5> Aby uruchomić program po pomyślnym skompilowaniu. Powinien być teraz widoczny interfejs użytkownika GUIX uruchomiony w oknie Microsoft Windows.

## <a name="designing-and-running-your-own-user-interface"></a>Projektowanie i uruchamianie własnego interfejsu użytkownika

Ten przewodnik Szybki Start nie jest zamiennikiem podręcznika użytkownika programu GUIX Studio ani podręcznikiem użytkownika GUIX, ale postanowimy Cię o tym, aby rozpocząć pracę i zachęcamy do kontynuowania, przenosząc się do podręcznika użytkownika programu GUIX Studio, aby uzyskać bardziej szczegółowe informacje.

Istnieją dwie metody tworzenia i modyfikowania własnego interfejsu użytkownika. Możesz badać Podręcznik programowania biblioteki GUIX i używać interfejsu API GUIX bezpośrednio z poziomu oprogramowania aplikacji, aby w pełni zaimplementować swój projekt. W większości przypadków aplikacja GUIX Studio jest używana do wykonywania większości zadań związanych z projektowaniem i układem elementów ekranu, a następnie dokończ obsługę zdarzeń i inną logikę aplikacji, która jest wymagana, aby interfejs użytkownika wykonywał rzeczywistą pracę.

Każdy z podanych przykładów został utworzony przy użyciu aplikacji projektowej interfejsu GUIX Studio. Po uruchomieniu Instalatora programu GUIX Studio należy mieć na pulpicie ikonę programu GUIX Studio 6. x. x. x.  Uruchom teraz program GUIX Studio i Otwórz projekt o nazwie "demo_guix_widget_types \ guix_widget_types. GXP". Demonstracja *widget_types* jest przykładowym projektem, który ilustruje kilka różnych typów widżetów GUIX.

Po otwarciu projektu kliknij przycisk "+", aby otworzyć węzeł drzewa o nazwie "podstawowa" w widoku projektu w lewym górnym rogu IDE, a następnie kliknij okno najwyższego poziomu w tym folderze o nazwie "Menu_Screen". Projekt nie powinien wyglądać tak, jak pokazano poniżej:

![Zrzut ekranu programu Studio z otwartym projektem.](./media/guix-studio/qs_project_open.png)

## <a name="guix-studio-views"></a>Widoki GUIX Studio

Środowisko IDE programu GUIX Studio składa się z kilku ***widoków***. Każdy widok został zaprojektowany, aby pomóc w nawigowaniu po projekcie i wprowadzaniu zmian w projekcie.

### <a name="project-view"></a>Widok projektu

Widok w lewym górnym rogu nosi nazwę widoku projektu. Ten widok przedstawia każdy z ekranów fizycznych, które są zawarte w projekcie (większość projektów ma tylko jeden ekran), a ekrany i podrzędne elementy widget, które zostały zaprojektowane do uruchamiania na tym ekranie.

### <a name="properties-view"></a>Widok właściwości

Poniżej widoku projektu znajduje się widok właściwości. Jak widok Właściwości nazwy wskazuje, ten widok pozwala modyfikować widżety przez zmianę różnych właściwości skojarzonych z nimi.

### <a name="target-view"></a>Widok docelowy

Centralny obszar wyświetlania jest nazywany widokiem docelowym. Ten widok jest widokiem WYSIWYG interfejsu użytkownika. Ponieważ biblioteka GUIX jest narysowaniem w widoku docelowym, ten widok jest dokładną reprezentacją pikseli, jak projekt będzie wyglądał po wykonaniu na osadzonym miejscu docelowym. Jeśli klikniesz inne widżety w widoku projektu lub centralnym widoku docelowym, zobaczysz wartości wyświetlane w widoku właściwości Zmień, aby wyświetlić właściwości wybranego widżetu.

### <a name="resource-view"></a>Widok zasobów

Na koniec po prawej stronie zobaczysz, co jest nazywane Widok zasobów. Ten widok umożliwia wybranie, dodanie, usunięcie i zmodyfikowanie kolorów, czcionek, pixelmaps i ciągów zawartych w projekcie.

## <a name="modifying-the-example"></a>Modyfikowanie przykładu

GUIX Studio została zaprojektowana jako intuicyjne. Aby przenieść jedno z elementów widget przedstawionych powyżej, wystarczy kliknąć ten widżet w widoku docelowym i przeciągnąć go do nowej lokalizacji. Aby zmienić kolory widżetu, kliknij odpowiedni widżet i Zmień kolory wyświetlane w widoku właściwości. Aby zmienić czcionkę używaną przez widżet wyświetlania tekstu, po prostu kliknij odpowiednią czcionkę w Widok zasobów i przeciągnij czcionkę i upuść ją na żądany widżet docelowy. Przepływaj myszą na przyciski paska narzędzi, aby zobaczyć szybką pomoc dotyczącą operacji wykonywanej przez poszczególne przyciski.

Eksperymentuj i wprowadzaj drobne zmiany do przykładu. Na przykład możesz przeciągnąć widżet do nowej lokalizacji, zmienić kolor tła okna lub zmienić rozmiar przycisku. Nie zalecamy usuwania żadnych elementów widget z przykładu, dopóki nie uzyskasz więcej doświadczenia w pracy z usługą GUIX, ponieważ usuwanie widżetów może wymagać skojarzonych modyfikacji kodu źródłowego aplikacji.

## <a name="running-the-application-within-studio"></a>Uruchamianie aplikacji w programie Studio

Możesz użyć Edytuj | Uruchom polecenie menu aplikacji (lub przycisk Uruchom aplikację na pasku przycisku), aby uruchomić aplikację natychmiast w nowym oknie pulpitu. Niestandardowe funkcje rysowania i inny kod aplikacji nie będą wywoływane przy użyciu tej metody, ale pozwalają na szybkie nawigowanie po projekcie interfejsu użytkownika i uzyskanie ogólnego pomysłu na wygląd i działanie aplikacji, w tym nawigację z jednego ekranu do następnego.

## <a name="generating-source-files"></a>Generowanie plików źródłowych

Po wprowadzeniu zmian należy wywołać polecenia menu programu GUIX Studio, aby generować nowe pliki źródłowe dla projektu. Można następnie ponownie skompilować Przykładowy program, aby zobaczyć zmiany w akcji. Aby wygenerować pliki źródłowe, użyj projektu poleceń menu GUIX Studio | Generowanie plików zasobów i projektu | Generuj pliki specyfikacji (można również kliknąć prawym przyciskiem myszy w widoku projektu, aby wykonać te polecenia).

Podczas generowania tych nowych plików źródłowych należy zaobserwować komunikat z potwierdzeniem informujący, że pliki źródłowe skojarzone z projektem zostały zaktualizowane. Jeśli nie obserwujesz tego komunikatu potwierdzającego, upewnij się, że masz uprawnienia do zapisu w katalogu, w którym znajduje się ten projekt. Teraz możesz zamknąć aplikację GUIX Studio. Jeśli w projekcie wprowadzono zmiany, program GUIX Studio wyświetli zapytanie, czy chcesz zapisać te zmiany. Zaoszczędź i Zapisz zmiany, te przykłady są przeznaczone do użycia i eksperymentowanie z usługą GUIX Studio.

### <a name="building-and-running-the-application"></a>Kompilowanie i uruchamianie aplikacji

Teraz, gdy program GUIX Studio wygenerował pliki wyjściowe projektu, można skompilować i utworzyć link do tworzenia autonomicznego pliku wykonywalnego Win32. Ponadto, aby uwzględnić niestandardowe rysunki lub obsługę zdarzeń zdefiniowane w aplikacji, należy skompilować i połączyć pliki wyjściowe wygenerowane przez GUIX Studio z oprogramowaniem aplikacji. Będziemy używać Microsoft Visual C++ łańcucha narzędzi jako przykładu, ale ta sama procedura jest używana, jeśli tworzysz i uruchamiasz dla zamierzonego celu.

- Uruchom środowisko IDE MSVC i Otwórz rozwiązanie \<root> /GUIX_Studio_5. x/przykłady/demo_guix_widget_types/build/vs_2019/guix_widget_types. sln.

- Użyj \<F7> klucza, aby ponownie skompilować rozwiązanie.
- Użyj \<F5> klucza, aby uruchomić program.
 
Powinien być teraz widoczny uruchomiony program z zmianami wprowadzonymi w programie Studio.

### <a name="learning-more"></a>Dodatkowe informacje

**Podręcznik użytkownika programu GUIX Studio** jest dostępny w witrynie [azrtos-GUIX-Studio-User-Guide](https://docs.microsoft.com/azure/rtos/guix/about-guix-studio). Podręcznik użytkownika programu GUIX Studio to bardziej dokładniejszy Przewodnik dotyczący korzystania z programu GUIX Studio.

Ponadto **Podręcznik użytkownika GUIX** jest dostępny w [podręczniku azrtos-GUIX-User-Guide](https://docs.microsoft.com/azure/rtos/guix/about-guix).  Ten przewodnik zawiera wiele bardziej szczegółowych informacji na temat tego, co dzieje się w "pod okapem" podczas wykonywania aplikacji GUIX. Aby w pełni wykorzystać możliwości biblioteki środowiska uruchomieniowego GUIX i programu GUIX Studio, należy odwołać się do obu tych przewodników.

## <a name="customer-support-center"></a>Centrum pomocy technicznej

Prosimy o przesłanie biletu pomocy technicznej za pośrednictwem witryny Azure Portal w celu uzyskania pytań lub pomocy przy korzystaniu z tych kroków. Podaj następujące informacje w wiadomości e-mail, aby skuteczniej rozwiązywać Twoje żądanie pomocy technicznej:

- Szczegółowy opis problemu, w tym częstotliwość występowania i sposób niezawodnego wygenerowania.
- Dołącz plik śledzenia, który powoduje problem.
- Używana wersja platformy Azure RTO GUIX Studio (pokazana w lewym górnym rogu ekranu).
- Używana wersja usługi Azure RTO GUIX, w tym zmienna **_gx_version_idstring** i **_gx_build_options** .
