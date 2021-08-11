---
title: Azure Real-Time Operating System (RTOS) GUIX Studio Przewodnik Szybki start
description: Ten przewodnik zawiera krótkie wprowadzenie do korzystania z aplikacji Azure RTOS GUIX Studio , opartego na platformie Microsoft Windows środowiska deweloperskiej szybkiego interfejsu użytkownika zaprojektowanego specjalnie dla biblioteki środowiska uruchomieniowego Azure RTOS GUIX firmy Microsoft.
author: philmea
ms.author: philmea
ms.date: 7/20/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 9ab4dfb2edd8990692ee3dc134207f43e4c757538dbc738f6f406bf40864bfb3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785428"
---
# <a name="azure-rtos-guix-studio-quick-start-guide"></a>Azure RTOS GUIX Studio Przewodnik Szybki start

Ten przewodnik zawiera krótkie wprowadzenie do korzystania z Azure RTOS GUIX Studio. GUIX Studio to oparta Windows interfejsu użytkownika aplikacja przeznaczona do użycia z biblioteką Azure RTOS środowiska uruchomieniowego GUIX firmy Microsoft. 

Jest ona przeznaczona dla osadzonego dewelopera oprogramowania w czasie rzeczywistym przy użyciu systemu operacyjnego ThreadX Real-Time (RTOS) i biblioteki uruchomieniowej interfejsu użytkownika Azure RTOS GUIX. Deweloper powinien znać standardowe pojęcia związane z Azure RTOS ThreadX i Azure RTOS GUIX.

## <a name="summary"></a>Podsumowanie

Azure RTOS GUIX Studio zawiera wszystko, czego potrzebujesz do tworzenia, kompilowania i uruchamiania własnego projektu interfejsu graficznego. Jeśli oceniasz program GUIX Studio, zestaw ewaluatora został zaprojektowany tak, aby umożliwić skompilowanie i uruchomienie projektu GUIX jako autonomicznej aplikacji klasycznej Windows do celów testowych i ewaluatorowych. Ponieważ graficzny interfejs użytkownika (GUIX) jest przeznaczony do użycia w niemal każdym osadzonym celu umożliwiającym graficzne dane wyjściowe, pracę i projekty tworzone na pulpicie można zawsze kompilować i uruchamiać na osadzonym celu bez zmiany jakiegokolwiek oprogramowania aplikacji.
Instalator programu GUIX Studio umieszcza w systemie dewelopera kilka składników:

- Aplikacja GUIX Studio.
- Kilka przykładowych projektów GUIX.
- Wszystkie zasoby graficzne i czcionki używane w przykładowych projektach.
- Pliki rozwiązań i pliki projektu do budowania w środowisku Windows przy użyciu Microsoft Visual Studio IDE.
- Wstępnie skompilowane biblioteki GUIX i ThreadX dla systemu Win32, umożliwiające tworzenie i uruchamianie własnych aplikacji na komputerze.
- Pliki nagłówkowe interfejsu API GUIX i ThreadX.

## <a name="prerequisites"></a>Wymagania wstępne

Instalator Azure RTOS GUIX Studio zawiera kilka prostych przykładowych projektów i oczekujemy, że rozpoczniesz od zmodyfikowania, sbudowania i uruchomienia tych przykładów, gdy dowiesz się, jak korzystać z aplikacji GUIX Studio. Do skompilowania i uruchomienia przykładów na komputerze Windows potrzebny jest Microsoft Visual Studio kompilator. Te narzędzia można pobrać z następującej lokalizacji:

https://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4

Jeśli nie masz zainstalowanych narzędzi programistyczych firmy Microsoft, możesz nadal ćmignąć łaziki i użyć aplikacji GUIX Studio do utworzenia własnego projektu interfejsu i przeanalizowania kodu źródłowego. Nie będzie można jednak skompilować ani uruchomić projektu jako aplikacji autonomicznej.

## <a name="running-the-examples"></a>Uruchamianie przykładów

Po uruchomieniu instalatora programu GUIX Studio znajdziesz kilka przykładowych projektów i plików kompilacji, które znajdują się w zainstalowanej zawartości. Aby sprawdzić, czy narzędzia pulpitu są zainstalowane i działają prawidłowo, zalecamy rozpoczęcie od sbudowania i uruchomienia każdego z podanych przykładów w stanie, w ile jest. Katalog instalacyjny zostanie nazwany , w takim przypadku należy użyć przeglądarki plików i przejść do \<root> \<root> katalogu /GUIX_Studio_6.x/examples. W tym katalogu powinien zostać wyświetlonych kilka prostych przykładowych programów, takich jak demo_guix_calculator, demo_guix_car_infotainment, demo_guix__home_automation, demo_guix_widget_types i inne.

## <a name="building-an-example"></a>Tworzenie przykładu

W każdym przykładowym folderze powinien znaleźć się podkatalog o nazwie *build.* Ten kierunek obejmuje wstępnie skonfigurowane projekty dla każdego obsługiwanego zestawu narzędzi. Możesz na przykład przejść do strony /GUIX_Studio_6.x/examples/meter/build/vs_2019 i znaleźć wstępnie skonfigurowany plik rozwiązania i plik projektu rozwiązania Microsoft Visual Studio gotowy do załadowania i uruchomienia w programie \<root> Visual Studio IDE. Jeśli chcesz użyć innego zestawu narzędzi, skontaktuj się z azure_rtos_support [.](https://docs.microsoft.com/azure/azure-portal/supportability/how-to-create-azure-support-request#create-a-support-request)

Zalecamy uruchomienie środowiska IDE Microsoft Visual C++ i otwarcie co najmniej jednego z tych przykładów. Naciśnij klawisz , aby skompilować przykładowy projekt, a następnie naciśnij klawisz , aby \<F7> \<F5> uruchomić program po pomyślnym skompilowaniu. Powinien zostać wyświetlony interfejs użytkownika GUIX uruchomiony w oknie Windows Microsoft.

## <a name="designing-and-running-your-own-user-interface"></a>Projektowanie i uruchamianie własnych Interfejs użytkownika

Ten przewodnik Szybki start nie zastępuje podręcznika użytkownika programu GUIX Studio ani podręcznika użytkownika GUIX, ale pokażemy Ci wystarczająco, aby rozpocząć pracę i zachęcamy do kontynuowania pracy, korzystając z podręcznika użytkownika programu GUIX Studio, aby uzyskać bardziej szczegółowe informacje.

Istnieją dwie metody tworzenia i modyfikowania własnego interfejsu użytkownika. Możesz zbadać podręcznik programowania biblioteki GUIX i użyć interfejsu API GUIX bezpośrednio z poziomu oprogramowania aplikacji, aby w pełni zaimplementować projekt. Częściej będziesz używać aplikacji GUIX Studio do wykonywania większości zadań projektowania i układu elementów ekranu, a następnie ukończyć obsługę zdarzeń i inną logikę aplikacji wymaganą do rzeczywistego wykonania pracy interfejsu użytkownika.

Każdy z podanych przykładów został utworzony przy użyciu aplikacji do projektowania interfejsu GUIX Studio. Po uruchomieniu instalatora programu GUIX Studio na pulpicie powinna być wyświetlana ikona programu GUIX Studio 6.x.x.x.  Uruchom teraz program GUIX Studio i otwórz projekt o nazwie "demo_guix_widget_types\guix_widget_types.gxp". Pokaz *widget_types* przykładowy, który demonstruje kilka odmian najpopularniejszych typów widżetów GUIX.

Po otwarciu projektu kliknij przycisk "+", aby otworzyć węzeł drzewa o nazwie "Primary" (Podstawowy) w widoku Project w lewym górnym rogu środowiska IDE, a następnie kliknij okno najwyższego poziomu w tym folderze o nazwie "Menu_Screen". Projekt nie powinien wyglądać tak, jak pokazano poniżej:

![Zrzut ekranu przedstawiający program Studio z otwartym projektem.](./media/guix-studio/qs_project_open.png)

## <a name="guix-studio-views"></a>Widoki GUIX Studio

Program GUIX Studio IDE składa się z kilku ***widoków.*** Każdy widok ma na celu pomoc w nawigowanie po projekcie i wprowadzenie zmian w tym projekcie.

### <a name="project-view"></a>Project Widok

Widok w lewym górnym rogu nosi nazwę widoku Project widoku. Ten widok przedstawia wszystkie fizyczne ekrany uwzględnione w projekcie (większość projektów ma tylko jeden ekran) oraz ekrany i widżety podrzędne, które zostały zaprojektowane do uruchamiania na tym ekranie.

### <a name="properties-view"></a>Widok właściwości

Poniżej Project widoku właściwości. Jak wskazuje nazwa Widok właściwości, ten widok umożliwia modyfikowanie widżetów przez zmianę różnych skojarzonych z nimi właściwości.

### <a name="target-view"></a>Widok docelowy

Centralny obszar wyświetlania jest nazywany widokiem docelowym. Ten widok to widok WYSIWYG interfejsu użytkownika. Ponieważ biblioteka GUIX rysuje w widoku docelowym, ten widok jest dokładną reprezentacją wyglądu projektu podczas wykonywania na osadzonym celu. Jeśli klikniesz różne widżety w widoku Project lub centralnym widoku docelowym, zobaczysz wartości wyświetlane w widoku właściwości, aby wyświetlić właściwości wybranego widżetu.

### <a name="resource-view"></a>Widok zasobów

Na koniec po prawej stronie zobaczysz, co nazywa się Widok zasobów. Ten widok umożliwia wybieranie, dodawanie, usuwanie i modyfikowanie kolorów, czcionek, map pikseli i ciągów zawartych w projekcie.

## <a name="modifying-the-example"></a>Modyfikowanie przykładu

Program GUIX Studio został zaprojektowany tak, aby był intuicyjny. Aby przenieść jeden z widżetów pokazanych powyżej, wystarczy kliknąć ten widżet w widoku docelowym i przeciągnąć go do nowej lokalizacji. Aby zmienić kolory widżetu, kliknij żądany element widget i zmień kolory wyświetlane w widoku właściwości. Aby zmienić czcionkę używaną przez widżet wyświetlania tekstu, wystarczy kliknąć żądaną czcionkę w obszarze Widok zasobów i przeciągnąć i upuścić czcionkę do żądanego widżetu docelowego. Ujmij wskaźnik myszy wzdłuż przycisków paska narzędzi, aby wyświetlić szybką pomoc dotyczącą operacji, które wykonuje każdy przycisk.

Poeksperymentuj samodzielnie i wprowadzaj drobne zmiany w przykładzie. Możesz na przykład przeciągnąć widżet do nowej lokalizacji, zmienić kolor tła okna lub zmienić rozmiar przycisku. Nie zalecamy usuwania żadnych widżetów z przykładu, dopóki nie uzyskasz więcej doświadczenia w pracy z graficznym interfejsem użytkownika, ponieważ usunięcie widżetów może wymagać skojarzonych modyfikacji kodu źródłowego aplikacji.

## <a name="running-the-application-within-studio"></a>Uruchamianie aplikacji w programie Studio

Możesz użyć funkcji edytowania | Uruchom polecenie menu Aplikacja (lub przycisk Uruchom aplikację na pasku przycisku), aby uruchomić aplikację natychmiast w nowym oknie pulpitu. Niestandardowe funkcje rysowania i inny kod aplikacji nie będą wywoływane przy użyciu tej metody, ale umożliwia szybkie nawigowanie po projekcie interfejsu użytkownika i uzyskiwanie ogólnego pojęcia wyglądu i działania aplikacji, w tym nawigacji między ekranami.

## <a name="generating-source-files"></a>Generowanie plików źródłowych

Po w związku z wprowadzeniem zmian należy wywołać polecenia menu programu GUIX Studio w celu wygenerowania nowych plików źródłowych dla projektu. Następnie możesz ponownie skompilować przykładowy program, aby zobaczyć zmiany w działaniu. Aby wygenerować pliki źródłowe, użyj poleceń menu GUIX Studio Project| Generowanie plików zasobów i Project| Generuj pliki specyfikacji (możesz również kliknąć prawym przyciskiem myszy ekran w widoku Project, aby wykonać te polecenia).

Podczas generowania tych nowych plików źródłowych powinien zostać wyświetlony komunikat z potwierdzeniem informujący, że pliki źródłowe skojarzone z projektem zostały zaktualizowane. Jeśli nie obserwujesz tego komunikatu potwierdzenia, upewnij się, że masz uprawnienia do zapisu w katalogu, w którym znajduje się projekt. Teraz możesz zamknąć aplikację GUIX Studio. Jeśli w projekcie wproszą się zmiany, program GUIX Studio zapyta, czy chcesz zapisać te zmiany. Zapisz zmiany. Te przykłady są przeznaczone do użycia i eksperymentowania z nim podczas nauki korzystania z programu GUIX Studio.

### <a name="building-and-running-the-application"></a>Budowania i uruchamiania aplikacji

Teraz, gdy program GUIX Studio wygenerował pliki wyjściowe projektu, możesz skompilować plik i połączyć go, aby utworzyć autonomiczny plik wykonywalny Win32. Ponadto w celu uwzględnienia wszelkich niestandardowych rysowania lub obsługi zdarzeń zdefiniowanych w aplikacji należy skompilować i połączyć pliki wyjściowe wygenerowane przez program GUIX Studio z własnym oprogramowaniem aplikacji. Jako przykładu użyjemy Microsoft Visual C++ narzędzi, ale w przypadku tworzenia i uruchamiania dla zamierzonego celu jest używana dokładnie ta sama procedura.

- Uruchom MSVC IDE i otwórz rozwiązanie \<root> /GUIX_Studio_5.x/examples/demo_guix_widget_types/build/vs_2019/guix_widget_types.sln.

- Użyj klucza \<F7> , aby ponownie skompilować rozwiązanie.
- Użyj \<F5> klucza , aby uruchomić program.
 
Powinien zostać wyświetlony uruchomiony program ze zmianami wprowadzonymi w programie Studio.

### <a name="learning-more"></a>Dodatkowe informacje

Podręcznik **użytkownika programu GUIX Studio jest** dostępny na stronie [azrtos-guix-studio-user-guide.](https://docs.microsoft.com/azure/rtos/guix/about-guix-studio) Podręcznik użytkownika programu GUIX Studio zawiera znacznie bardziej szczegółowe informacje na temat korzystania z programu GUIX Studio.

Ponadto podręcznik użytkownika **GUIX jest** dostępny na stronie [azrtos-guix-user-guide.](https://docs.microsoft.com/azure/rtos/guix/about-guix)  Ten przewodnik zawiera znacznie bardziej szczegółowe informacje o tym, co dzieje się "Pod maską" po wykonaniu aplikacji GUIX. Aby w pełni wykorzystać możliwości biblioteki środowiska uruchomieniowego GUIX i programu GUIX Studio, należy odwołać się do obu tych przewodników.

## <a name="customer-support-center"></a>Centrum obsługi klienta

Aby uzyskać pytania lub pomoc, prześlij bilet pomocy technicznej za pośrednictwem witryny Azure Portal. W wiadomości e-mail należy podać następujące informacje, abyśmy w bardziej wydajny sposób rozwiązali Twój wniosek o pomoc techniczną:

- Szczegółowy opis problemu, w tym częstotliwość występowania i sposób jego niezawodnego odtworzenia.
- Dołącz plik śledzenia, który powoduje problem.
- Wersja programu Azure RTOS GUIX Studio, z których korzystasz (wyświetlana w lewym górnym rogu ekranu).
- Wersja programu Azure RTOS GUIX, z uwzględnieniem _gx_version_idstring **i** **_gx_build_options** graficznego.
