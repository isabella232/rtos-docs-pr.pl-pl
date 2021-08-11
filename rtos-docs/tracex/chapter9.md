---
title: Rozdział 9 — Azure RTOS śledzenia USBX
description: Ten rozdział zawiera opis zdarzeń Azure RTOS USBX wyświetlanych przez traceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 015e5feedd1d5e90c6491e156c2d0d57a9abaa47518868d375a34e618770d4aa
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116793970"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>Rozdział 9 — Azure RTOS śledzenia USBX

Ten rozdział zawiera opis zdarzeń Azure RTOS USBX wyświetlanych przez traceX. 

## <a name="list-of-events-and-icons"></a>Lista zdarzeń i ikon

Poniżej znajduje się lista zdarzeń USBX wyświetlanych przez TraceX.

| Ikona                             | Znaczenie                               |
| -------------------------------- | ------------------------------------- |
| ![Ikona aktywacji klasy urządzenia C D C](./media/user-guide/usbx-events/image1.png)    | **Aktywacja cdc klasy urządzenia** *(ux_device_class_cdc_activate)* |
| ![Ikona dezaktywacji klasy urządzenia C D C](./media/user-guide/usbx-events/image2.png)    | **Dezaktywacja usługi CDC** *klasy urządzenia (ux_device_class_cdc_deactivate)* |
| ![Ikona odczytu klasy urządzenia C D C](./media/user-guide/usbx-events/image3.png)    | **Odczyt z cdc klasy urządzenia** *(ux_device_class_cdc_read)* |
| ![Ikona zapisu klasy urządzenia C D C](./media/user-guide/usbx-events/image4.png)    | **Zapis CDC klasy urządzenia** *(ux_device_class_cdc_write)* |
| ![Ikona aktywacji dpump klasy urządzenia](./media/user-guide/usbx-events/image5.png)    | **Aktywacja dpump klasy urządzenia** *(ux_device_class_dpump_activate)* |
| ![Ikona dezaktywacji dpump klasy urządzenia](./media/user-guide/usbx-events/image6.png)    | **Dezaktywacja dpump klasy** *urządzenia (ux_device_class_dpump_deactivate)* |
| ![Ikona odczytu dpump klasy urządzenia](./media/user-guide/usbx-events/image7.png)    | **Odczyt dpump klasy urządzenia** *(ux_device_class_dpump_read)* |
| ![Ikona zapisu dpump klasy urządzenia](./media/user-guide/usbx-events/image8.png)    | **Device Class Dpump Write** *(ux_device_class_dpump_write)* |
| ![Ikona aktywacji klasy urządzenia Hid](./media/user-guide/usbx-events/image9.png)    | **Aktywacja Hid klasy urządzenia** *(ux_device_class_hid_activate)* |
| ![Ikona Dezaktywacja klasy urządzenia](./media/user-guide/usbx-events/image10.png)    | **Dezaktywacja klasy** urządzenia *(ux_device_class_hid_deactivate)* |
| ![Ikona wysyłania deskryptora Hid klasy urządzenia](./media/user-guide/usbx-events/image11.png)    | **Wysyłanie deskryptora Hid** klasy urządzenia *(ux_device_class_hid_descriptor_send)* |
| ![Ikona Pobierz zdarzenie Hid klasy urządzenia](./media/user-guide/usbx-events/image12.png)    | **Uzyskiwanie zdarzenia Hid klasy urządzenia** *(ux_device_class_hid_event_get)* |
| ![Ikona zestawu zdarzeń Hid klasy urządzenia](./media/user-guide/usbx-events/image13.png)    | **Zestaw zdarzeń Hid klasy urządzenia** *(ux_device_class_hid_event_set)* |
| ![Ikona Pobierz raport Hid klasy urządzenia](./media/user-guide/usbx-events/image14.png)    | **Uzyskiwanie raportu Hid klasy urządzenia** *(ux_device_class_hid_report_get)* |
| ![Ikona zestawu raportów Hid klasy urządzenia](./media/user-guide/usbx-events/image15.png)    | **Zestaw raportów Hid klasy urządzenia** *(ux_device_class_hid_report_set)* |
| ![Ikona aktywacji Pima klasy urządzenia](./media/user-guide/usbx-events/image16.png)    | **Aktywacja Pima klasy urządzenia** *(ux_device_class_pima_activate)* |
| ![Ikona dezaktywacji Pima klasy urządzenia](./media/user-guide/usbx-events/image17.png)    | **Dezaktywacja Pima** klasy *urządzenia (ux_device_class_pima_deactivate)* |
| ![Ikona wysyłania informacji o urządzeniu Pima klasy urządzenia](./media/user-guide/usbx-events/image18.png)    | **Wysyłanie informacji o urządzeniu Pima klasy urządzenia** *(ux_device_class_pima_device_info_send)* |
| ![Ikona Pobierz zdarzenie Pima klasy urządzenia](./media/user-guide/usbx-events/image19.png)    | **Uzyskiwanie zdarzeń Pima klasy urządzenia** *(ux_device_class_pima_event_get)* |
| ![Ikona zestawu zdarzeń Pima klasy urządzenia](./media/user-guide/usbx-events/image20.png)    | **Zestaw zdarzeń Pima klasy urządzenia** *(ux_device_class_pima_event_set)* |
| ![Ikona Dodaj obiekt Pima klasy urządzenia](./media/user-guide/usbx-events/image21.png)    | **Dodawanie obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_add)* |
| ![Ikona Pobierz dane obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image22.png)    | **Pobierz dane obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_data_get)* |
| ![Ikona wysyłania danych obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image23.png)    | **Wysyłanie danych obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_data_send)* |
| ![Ikona usuwania obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image24.png)    | **Usuwanie obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_delete)* |
| ![Ikona Wysyłania uchwytów obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image25.png)    | **Dojścia obiektu Pima** klasy urządzenia *do wysyłania (ux_device_class_pima_object_handles_send)* |
| ![Ikona Pobierz informacje o obiekcie Pima klasy urządzenia](./media/user-guide/usbx-events/image26.png)    | **Uzyskiwanie informacji o obiekcie Pima klasy urządzenia** *(ux_device_class_pima_object_info_get)* |
| ![Ikona wysyłania informacji o obiekcie Pima klasy urządzenia](./media/user-guide/usbx-events/image27.png)    | **Wysyłanie informacji o obiekcie Pima** klasy urządzenia *(ux_device_class_pima_object_info_send)* |
| ![Ikona Wysyłania liczby obiektów Pima klasy urządzenia](./media/user-guide/usbx-events/image28.png)    | **Wysyłanie numeru obiektów Pima klasy urządzenia** *(ux_device_class_pima_objects_number_send)* |
| ![Ikona Pobierz dane częściowego obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image29.png)    | **Pobierz dane częściowego obiektu Pima** klasy urządzenia *(ux_device_class_pima_partial_object_data_get)* |
| ![Ikona wysyłania odpowiedzi Pima klasy urządzenia](./media/user-guide/usbx-events/image30.png)    | **Wysyłanie odpowiedzi Pima klasy urządzenia** *(ux_device_class_pima_response_send)*|
| ![Ikona wysyłania danych Storage Device Class Pima](./media/user-guide/usbx-events/image31.png)    | **Wysyłanie identyfikatora urządzenia klasy Storage Pima** *(ux_device_class_pima_storage_id_send)* |
| ![Ikona wysyłania informacji Storage Device Class Pima](./media/user-guide/usbx-events/image32.png)    | **Wysyłanie informacji o Storage Pima klasy urządzenia** *(ux_device_class_pima_storage_info_send)* |
| ![Ikona aktywacji klasy urządzenia R N D I S](./media/user-guide/usbx-events/image33.png)    | **Aktywacja Rndis klasy urządzenia** *(ux_device_class_rndis_activate)* |
| ![Ikona dezaktywacji klasy urządzenia R N D I S](./media/user-guide/usbx-events/image34.png)    | **Dezaktywacja Rndis klasy** *urządzenia (ux_device_class_rndis_deactivate)* |
| ![Komunikat Device Class R N D I S Keep Aliveicon](./media/user-guide/usbx-events/image35.png)    | **Zachowanie aktywności komunikatu Rndis klasy** urządzenia *(ux_device_class_rndis_msg_keep_alive)* |
| ![Ikona zapytania o komunikat klasy urządzenia R N D I S](./media/user-guide/usbx-events/image36.png)    | **Zapytanie komunikatów Rndis klasy urządzenia** *(ux_device_class_rndis_msg_query)* |
| ![Ikona resetowania komunikatów usługi Device Class R N D I S](./media/user-guide/usbx-events/image37.png)    | **Resetowanie komunikatów Rndis klasy urządzenia** *(ux_device_class_rndis_msg_reset)* |
| ![Device Class R N D I S Message Set icon (Zestaw komunikatów klasy urządzenia R N D I S)](./media/user-guide/usbx-events/image38.png)    | **Zestaw komunikatów Rndis klasy urządzenia** *(ux_device_class_rndis_msg_set)* |
| ![Ikona odbierania pakietów klasy urządzeń R N D I S](./media/user-guide/usbx-events/image39.png)    | **Odbieranie pakietów Rndis klasy urządzenia** *(ux_device_class_rndis_packet_receive)* |
| ![Ikona przesyłania pakietów klas urządzeń R N D I S](./media/user-guide/usbx-events/image40.png)    | **Przesyłanie pakietów Rndis klasy urządzenia** *(ux_device_class_rndis_packet_transmit)* |
| ![Ikona aktywacji Storage Klasy urządzeń](./media/user-guide/usbx-events/image41.png)    | **Aktywacja Storage klas urządzeń** *(ux_device_class_storage_activate)* |
| ![Ikona dezaktywacji Storage Urządzenia](./media/user-guide/usbx-events/image42.png)    | **Dezaktywacja Storage klasy** urządzenia *(ux_device_class_storage_deactivate)* |
| ![Ikona formatu Storage klasy urządzenia](./media/user-guide/usbx-events/image43.png)    | **Format Storage klasy urządzenia** *(ux_device_class_storage_format)* |
| ![Ikona zapytania Storage klasa urządzenia](./media/user-guide/usbx-events/image44.png)    | **Zapytanie dotyczące Storage klas urządzeń** *(ux_device_class_storage_inquiry)* |
| ![Ikona wyboru Storage klasy urządzenia](./media/user-guide/usbx-events/image45.png)    | **Wybór trybu Storage klasy urządzenia** *(ux_device_class_storage_mode_select)* |
| ![Ikona sense Storage Klasy urządzenia](./media/user-guide/usbx-events/image46.png)    | **Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)* |
| ![Ikona Zezwalaj na Storage zezwalaj na usuwanie multimediów w klasie urządzenia](./media/user-guide/usbx-events/image47.png)    | **Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)* |
| ![Ikona odczytu Storage Klasa urządzenia](./media/user-guide/usbx-events/image48.png)    | **Odczyt Storage klasy urządzenia** *(ux_device_class_storage_read)* |
| ![Ikona Odczytuj pojemność Storage Klasa urządzenia](./media/user-guide/usbx-events/image49.png)    | **Pojemność odczytu Storage klas** urządzeń *(ux_device_class_storage_read_capacity)* |
| ![Ikona pojemności Storage Format odczytu klasy urządzenia](./media/user-guide/usbx-events/image50.png)    | **Pojemność formatu odczytu Storage klas urządzeń** *(ux_device_class_storage_read_format_capacity)* |
| ![Ikona odczytywania Storage klasa urządzenia](./media/user-guide/usbx-events/image51.png)    | **Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)* |
| ![Ikona sense żądania Storage Device Class](./media/user-guide/usbx-events/image52.png)    | **Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)* |
| ![Ikona uruchamiania Storage klasy urządzenia](./media/user-guide/usbx-events/image53.png)    | **Uruchamianie/zatrzymywanie Storage klasy** urządzenia *(ux_device_class_storage_start_stop)* |
| ![Ikona Gotowość Storage do testowania klasy urządzenia](./media/user-guide/usbx-events/image54.png)    | **Gotowość do Storage klas urządzeń** *(ux_device_class_storage_test_ready)* |
| ![Ikona weryfikacji Storage klasy urządzenia](./media/user-guide/usbx-events/image55.png)    | **Weryfikacja Storage klasy urządzenia** *(ux_device_class_storage_verify)* |
| ![Ikona zapisu Storage klasy urządzenia](./media/user-guide/usbx-events/image56.png)    | **Zapis Storage klasy urządzenia** *(ux_device_class_storage_write)* |
| ![Ikona Pobierz alternatywne ustawienie stosu urządzeń](./media/user-guide/usbx-events/image57.png)    | **Uzyskiwanie alternatywnych ustawień stosu urządzeń** *(ux_device_stack_alternate_setting_get)* |
| ![Ikona zestawu ustawień alternatywnych stosu urządzeń](./media/user-guide/usbx-events/image58.png)    | **Zestaw alternatywnych ustawień stosu urządzeń** *(ux_device_stack_alternate_setting_set)* |
| ![Ikona Rejestracji klasy stosu urządzeń](./media/user-guide/usbx-events/image59.png)    | **Rejestrowanie klas stosu urządzeń** *(ux_device_stack_class_register)* |
| ![Ikona funkcji Wyczyść stos urządzeń](./media/user-guide/usbx-events/image60.png)    | **Funkcja Wyczyść stos urządzeń** *(ux_device_stack_clear_feature)* |
| ![Ikona Pobierz konfigurację stosu urządzeń](./media/user-guide/usbx-events/image61.png)    | **Uzyskiwanie konfiguracji stosu urządzeń** *(ux_device_stack_configuration_get)* |
| ![Ikona zestawu konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image62.png)    | **Zestaw konfiguracji stosu urządzeń** *(ux_device_stack_configuration_set)* |
| ![Ikona Połączenie stosu urządzeń](./media/user-guide/usbx-events/image63.png)    | **Device Stack Połączenie** *(ux_device_stack_connect)* |
| ![Ikona wysyłania deskryptora stosu urządzeń](./media/user-guide/usbx-events/image64.png)    | **Wysyłanie deskryptora stosu urządzeń** *(ux_device_stack_descriptor_send)* |
| ![Ikona rozłączania stosu urządzeń](./media/user-guide/usbx-events/image65.png)    | **Rozłączanie stosu urządzeń** *(ux_device_stack_disconnect)* |
| ![Ikona zatrzymań punktu końcowego stosu urządzeń](./media/user-guide/usbx-events/image66.png)    | **Wstrzymanie punktu końcowego stosu urządzeń** *(ux_device_stack_endpoint_stall)* |
| ![Ikona Pobierz stan stosu urządzeń](./media/user-guide/usbx-events/image67.png)    | **Uzyskiwanie stanu stosu urządzeń** *(ux_device_stack_get_status)* |
| ![Ikona wznawiania hosta stosu urządzeń](./media/user-guide/usbx-events/image68.png)    | **Wznawianie hosta stosu urządzeń** *(ux_device_stack_host_wakeup)* |
| ![Ikona Inicjowanie stosu urządzeń](./media/user-guide/usbx-events/image69.png)    | **Inicjowanie stosu urządzeń** *(ux_device_stack_initialize)* |
| ![Ikona usuwania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image70.png)    | **Usuwanie interfejsu stosu urządzeń** *(ux_device_stack_interface_delete)* |
| ![Ikona Pobierz interfejs stosu urządzeń](./media/user-guide/usbx-events/image71.png)    | **Uzyskiwanie interfejsu stosu urządzeń** *(ux_device_stack_interface_get)* |
| ![Ikona zestawu interfejsu stosu urządzeń](./media/user-guide/usbx-events/image72.png)    | **Zestaw interfejsu stosu urządzeń** *(ux_device_stack_interface_set)* |
| ![Ikona funkcji zestawu stosu urządzeń](./media/user-guide/usbx-events/image73.png)    | **Funkcja zestawu stosów urządzeń** *(ux_device_stack_set_feature)* |
| ![Ikona przerwania transferu stosu urządzeń](./media/user-guide/usbx-events/image74.png)    | **Przerwanie transferu stosu urządzeń** *(ux_device_stack_transfer_abort)* |
| ![*Ikona przerwania wszystkich żądań transferu stosu urządzeń](./media/user-guide/usbx-events/image75.png)    | **Przenoszenie wszystkich żądań przerwania** stosu urządzeń *(ux_device_stack_transfer_all_request_abort)* |
| ![Ikona żądania transferu stosu urządzeń](./media/user-guide/usbx-events/image76.png)    | **Żądanie transferu stosu urządzeń** *(ux_device_stack_transfer_request)* |
| ![Ikona aktywowania klasy hosta w asix](./media/user-guide/usbx-events/image77.png)    | **Aktywowanie asix klasy hosta** *(ux_host_class_asix_activate)* |
| ![Ikona dezaktywacji klasy hosta Asix](./media/user-guide/usbx-events/image78.png)    | **Dezaktywacja asix klasy** *hosta (ux_host_class_asix_deactivate)* |
| ![Ikona powiadomienia o przerwaniu asix klasy hosta](./media/user-guide/usbx-events/image79.png)    | **Powiadomienie o przerwaniu asix klasy hosta** *(ux_host_class_asix_interrupt_notification)* |
| ![Ikona Read (Asix) klasy hosta](./media/user-guide/usbx-events/image80.png)    | **Odczyt Asix klasy hosta** *(ux_host_class_asix_read)* |
| ![Ikona zapisu Asix klasy hosta](./media/user-guide/usbx-events/image81.png)    | **Host Class Asix Write** *(ux_host_class_asix_write)* |
| ![Ikona aktywowania dźwięku klasy hosta](./media/user-guide/usbx-events/image82.png)    | **Aktywowanie dźwięku klasy hosta** *(ux_host_class_audio_activate)* |
| ![Ikona Pobierz wartość kontrolki audio klasy hosta](./media/user-guide/usbx-events/image83.png)    | **Pobierz wartość kontrolki audio** klasy hosta *(ux_host_class_audio_control_value_get)* |
| ![Ikona zestawu wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image84.png)    | **Zestaw wartości kontrolki audio klasy hosta** *(ux_host_class_audio_control_value_set)* |
| ![Ikona dezaktywacji dźwięku klasy hosta](./media/user-guide/usbx-events/image85.png)    | **Dezaktywacja dźwięku klasy** *hosta (ux_host_class_audio_deactivate)* |
| ![Ikona odczytu dźwięku klasy hosta](./media/user-guide/usbx-events/image86.png)    | **Odczyt audio klasy hosta** *(ux_host_class_audio_read)* |
| ![Ikona Pobierz próbkowanie audio przesyłania strumieniowego klasy hosta](./media/user-guide/usbx-events/image87.png)    | **Pobieranie próbkowania audio przesyłania strumieniowego klasy hosta** *(ux_host_class_audio_streaming_sampling_get)* |
| ![Ikona zestawu próbkowania przesyłania strumieniowego audio klasy hosta](./media/user-guide/usbx-events/image88.png)    | **Zestaw próbkowania audio przesyłania strumieniowego klasy hosta** *(ux_host_class_audio_streaming_sampling_set)* |
| ![Ikona zapisu audio klasy hosta](./media/user-guide/usbx-events/image89.png)    | **Zapis audio klasy hosta** *(ux_host_class_audio_write)* |
| ![Ikona aktywacji klasy hosta C D C A C M](./media/user-guide/usbx-events/image90.png)    | **Aktywowanie klasy hosta Acm cdc** *(ux_host_class_cdc_acm_activate)* |
| ![Ikona dezaktywacji klasy hosta C D C A C M](./media/user-guide/usbx-events/image91.png)    | **Dezaktywacja klasy hosta CDC Acm** *(ux_host_class_cdc_acm_deactivate)* |
| ![Host Class C D C A C M I O C T L In Pipe icon (Klasa hosta C D C A C M I O C T L w potoku)](./media/user-guide/usbx-events/image92.png)    | **Klasa hosta Cdc Acm Ioctl Abort in Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)* |
| ![Host Class C D C A C M I O C T L Abort Out Pipe icon (Klasa hosta C D C A C M I O C T L Przerwania potoku wychodzącego)](./media/user-guide/usbx-events/image93.png)    | **Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)* |
| ![Host Class C D C A C M I O C T L Pobierz ikonę stanu urządzenia](./media/user-guide/usbx-events/image94.png)    | **Host Class CDc Acm Ioctl Get Device Status** *(Pobierz stan urządzenia) (ux_host_class_cdc_acm_ioctl_get_device_status)* |
| ![Host Class C D C A C M I O C T L Ikona kodowania wiersza](./media/user-guide/usbx-events/image95.png)    | **Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)* |
| ![Host Class C D C A C M I O C T L Notification Callback icon (Klasa hosta C D C A C M I O C T L Ikona wywołania zwrotnego powiadomień)](./media/user-guide/usbx-events/image96.png)    | **Wywołanie zwrotne powiadomienia Ioctl klasy hosta CDC Acm** *(ux_host_class_cdc_acm_ioctl_notification_callback)* |
| ![Host Class C D C A C M I O C T L Send Break icon (Klasa hosta C D C A C M I O C T L Send Break)](./media/user-guide/usbx-events/image97.png)    | **Podział wysyłania Ioctl klasy hosta CDC Acm** *(ux_host_class_cdc_acm_ioctl_send_break)* |
| ![Host Class C D C A C M I O C T L Set Line Coding icon (Klasa hosta C D C A C M I O C T L Set Line Coding) ikona](./media/user-guide/usbx-events/image98.png)    | **Host Class CDc Acm Ioctl Set Line Coding** *(ux_host_class_cdc_acm_ioctl_set_line_coding)* |
| ![Host Class C D C A C M I O C T L Set Line State icon (Klasa hosta C D C A C M I O C T L Set Line State) ikona](./media/user-guide/usbx-events/image99.png)    | **Host Class Cdc Acm Ioctl Set Line State** *(Ux_host_class_cdc_acm_ioctl_set_line_state)* |
| ![Host Class C D C A C M Read icon (Klasa hosta C D C A C M ikona odczytu)](./media/user-guide/usbx-events/image100.png)    | **Odczyt Acm klasy hosta cdc** *(ux_host_class_cdc_acm_read)* |
| ![Host Class C D C A C M (Klasa hosta C D A C M ikona rozpoczęcia odbioru)](./media/user-guide/usbx-events/image101.png)    | **Rozpoczęcie odbioru klasy hosta CDC Acm** *(ux_host_class_cdc_acm_reception_start)* |
| ![Host Class C D C A C M Reception Stop icon (Klasa hosta C D C A C M ikona zatrzymania odbioru)](./media/user-guide/usbx-events/image102.png)    | **Zatrzymywanie odbioru klasy hosta CDC Acm** *(ux_host_class_cdc_acm_reception_stop)* |
| ![Host Class C D C A C M Write icon (Klasa hosta C D C A C M Ikona zapisu)](./media/user-guide/usbx-events/image103.png)    | **Zapis Acm Acm klasy** hosta *(ux_host_class_cdc_acm_write)* |
| ![Ikona aktywacji dpump klasy hosta](./media/user-guide/usbx-events/image104.png)    | **Aktywowanie dpump klasy hosta** *(ux_host_class_dpump_activate)* |
| ![Ikona dezaktywacji dpump klasy hosta](./media/user-guide/usbx-events/image105.png)    | **Dezaktywacja dpump klasy** *hosta (ux_host_class_dpump_deactivate)* |
| ![Ikona odczytu dpump klasy hosta](./media/user-guide/usbx-events/image106.png)    | **Odczyt dpump klasy hosta** *(ux_host_class_dpump_read)* |
| ![Ikona zapisu dpump klasy hosta](./media/user-guide/usbx-events/image107.png)    | **Zapis dpump klasy hosta** *(ux_host_class_dpump_write)* |
| ![Ikona aktywowania klasy hosta](./media/user-guide/usbx-events/image108.png)    | **Aktywowanie funkcji Hid klasy hosta** *(ux_host_class_hid_activate)* |
| ![Ikona Rejestracji klienta Hid klasy hosta](./media/user-guide/usbx-events/image109.png)    | **Rejestr klienta Hid klasy hosta** *(ux_host_class_hid_client_register)* |
| ![Ikona dezaktywacji klasy hosta](./media/user-guide/usbx-events/image110.png)    | **Dezaktywacja klasy** hosta *(ux_host_class_hid_deactivate)* |
| ![Ikona Pobierz klasę hosta Hid Idle](./media/user-guide/usbx-events/image111.png)    | **Host Class Hid Idle Get** *(ux_host_class_hid_idle_get)* |
| ![Ikona zestawu bezczynności Hid klasy hosta](./media/user-guide/usbx-events/image112.png)    | **Zestaw bezczynności Hid klasy hosta** *(ux_host_class_hid_idle_set)* |
| ![Klasa hosta Ikona aktywowania klawiatury](./media/user-guide/usbx-events/image113.png)    | **Aktywowanie klawiatury Hid klasy hosta** *(ux_host_class_hid_keyboard_activate)* |
| ![Klasa hosta Ikona dezaktywacji klawiatury](./media/user-guide/usbx-events/image114.png)    | **Klasa hosta Dezaktywacja klawiatury Hid** *(ux_host_class_hid_keyboard_deactivate)* |
| ![Ikona aktywowania myszy w klasie hosta](./media/user-guide/usbx-events/image115.png)    | **Aktywowanie myszy Hid klasy hosta** *(ux_host_class_hid_mouse_activate)* |
| ![Ikona dezaktywacji myszy Hid klasy hosta](./media/user-guide/usbx-events/image116.png)    | **Dezaktywacja myszy Hid klasy** hosta *(ux_host_class_hid_mouse_deactivate)* |
| ![Ikona aktywowania zdalnego sterowania za pomocą funkcji Host Class Hid](./media/user-guide/usbx-events/image117.png)    | **Aktywowanie zdalnego sterowania za pomocą** klasy hosta *(ux_host_class_hid_remote_control_activate)* |
| ![Ikona dezaktywacji zdalnego sterowania ukrywania klasy hosta](./media/user-guide/usbx-events/image118.png)    | **Dezaktywacja zdalnego sterowania przy ukrywaniu** *klasy hosta (ux_host_class_hid_remote_control_deactivate)* |
| ![Ikona Pobierz raport Hid klasy hosta](./media/user-guide/usbx-events/image119.png)    | **Uzyskiwanie raportu Hid klasy hosta** *(ux_host_class_hid_report_get)* |
| ![Ikona zestawu raportów Hid klasy hosta](./media/user-guide/usbx-events/image120.png)    | **Zestaw raportów Hid klasy hosta** *(ux_host_class_hid_report_set)* |
| ![Ikona aktywowania centrum klas hosta](./media/user-guide/usbx-events/image121.png)    | **Aktywowanie centrum klas hosta** *(ux_host_class_hub_activate)* |
| ![Ikona Wykrywania zmian centrum klas hosta](./media/user-guide/usbx-events/image122.png)    | **Wykrywanie zmian centrum klas hosta** *(ux_host_class_hub_change_detect)* |
| ![*Ikona dezaktywacji centrum klas hosta](./media/user-guide/usbx-events/image123.png)    | **Dezaktywacja centrum klas** *hosta (ux_host_class_hub_deactivate)* |
| ![Ikona Procesu zmiany połączenia portu centrum klasy hosta](./media/user-guide/usbx-events/image124.png)    | **Proces zmiany połączenia portu centrum klasy hosta** *(ux_host_class_hub_port_change_connection_process)* |
| ![Ikona Włącz proces zmiany portu centrum klas hosta](./media/user-guide/usbx-events/image125.png)    | **Proces włączania zmiany portu koncentratora klasy hosta** *(ux_host_class_hub_port_change_enable_process)* |
| ![Ikona Zmiany portu centrum klas hosta w 2018 r.](./media/user-guide/usbx-events/image126.png)    | **Zmiana portu centrum klas hosta w bieżącym procesie** *(ux_host_class_hub_port_change_over_current_process)* |
| ![Ikona Procesu resetowania portu centrum klas hosta](./media/user-guide/usbx-events/image127.png)    | **Proces resetowania portu centrum klasy hosta** *(ux_host_class_hub_port_change_reset_process)* |
| ![Ikona wstrzymywania procesu zmiany portu centrum klas hosta](./media/user-guide/usbx-events/image128.png)    | **Proces wstrzymania zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_suspend_process)* |
| ![Ikona aktywowania klasy hosta Pima](./media/user-guide/usbx-events/image129.png)    | **Aktywowanie klasy hosta Pima** *(ux_host_class_prima_activate)* |
| ![Ikona dezaktywacji klasy hosta Pima](./media/user-guide/usbx-events/image130.png)    | **Dezaktywacja klasy hosta Pima** *(ux_host_class_pima_deactivate)* |
| ![Ikona Pobierz informacje o urządzeniu klasy hosta Pima](./media/user-guide/usbx-events/image131.png)    | **Uzyskiwanie informacji o urządzeniu klasy** hosta Pima *(ux_host_class_pima_device_info_get)* |
| ![Ikona resetowania urządzenia klasy hosta Pima](./media/user-guide/usbx-events/image132.png)    | **Resetowanie urządzenia klasy hosta Pima** *(ux_host_class_pima_device_reset)* |
| ![Ikona powiadomienia Pima klasy hosta](./media/user-guide/usbx-events/image133.png)    | **Powiadomienie Pima klasy hosta** *(ux_host_class_pima_notification)* |
| ![Ikona Pobierz obiekty numeru Pima klasy hosta](./media/user-guide/usbx-events/image134.png)    | **Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)* |
| ![Ikona zamknięcia obiektu Pima klasy hosta](./media/user-guide/usbx-events/image135.png)    | **Zamknięcie obiektu Pima klasy hosta** *(ux_host_class_pima_object_close)* |
| ![Ikona kopiowania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image136.png)    | **Kopiowanie obiektu Pima klasy hosta** *(ux_host_class_pima_object_copy)* |
| ![Ikona Usuwania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image137.png)    | **Usuwanie obiektu Pima klasy hosta** *(ux_host_class_pima_object_delete)* |
| ![Ikona Pobierz obiekt Pima klasy hosta](./media/user-guide/usbx-events/image138.png)    | **Pobierz obiekt Pima klasy hosta** *(ux_host_class_pima_object_get)* |
| ![Ikona Pobierz informacje o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image139.png)    | **Uzyskiwanie informacji o obiekcie Pima** klasy hosta *(ux_host_class_pima_object_info_get)* |
| ![Ikona wysyłania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image140.png)    | **Wysyłanie informacji o obiekcie Pima** klasy hosta *(ux_host_class_pima_object_info_send)* |
| ![Ikona przenoszenia obiektu Pima klasy hosta](./media/user-guide/usbx-events/image141.png)    | **Przenoszenie obiektów Pima klasy hosta** *(ux_host_class_pima_object_move)* |
| ![Ikona wysyłania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image142.png)    | **Wysyłanie obiektu Pima klasy hosta** *(ux_host_class_pima_object_send)* |
| ![Ikona przerwania transferu obiektów Pima klasy hosta](./media/user-guide/usbx-events/image143.png)    | **Przerwanie transferu obiektów Pima klasy** hosta *(ux_host_class_object_transfer_abort)* |
| ![Ikona odczytu Pima klasy hosta](./media/user-guide/usbx-events/image144.png)    | **Host Class Pima Read** *(ux_host_class_pima_read)* |
| ![Ikona anulowania żądania Pima klasy hosta](./media/user-guide/usbx-events/image145.png)    | **Anulowanie żądania Pima klasy** hosta *(ux_host_class_pima_request_cancel)* |
| ![Ikona zamknięcia sesji Pima klasy hosta](./media/user-guide/usbx-events/image146.png)    | **Zamknięcie sesji Pima klasy hosta** *(ux_host_class_pima_session_close)* |
| ![Ikona Otwórz sesję Pima klasy hosta](./media/user-guide/usbx-events/image147.png)    | **Otwarta sesja Pima klasy hosta** *(ux_host_class_pima_session_open)* |
| ![Host Class Pima Storage Ids (Pobierz identyfikatory klasy hosta)](./media/user-guide/usbx-events/image148.png)    | **Pobierz identyfikatory identyfikatorów Storage Host Class Pima** *(ux_host_class_pima_storage_ids_get)* |
| ![Ikona pobierz informacje o Storage Pima klasy hosta](./media/user-guide/usbx-events/image149.png)    | **Uzyskiwanie informacji o Storage Pima klasy hosta** *(ux_host_class_pima_storage_info_get)* |
| ![Ikona Pobierz miniaturę Pima klasy hosta](./media/user-guide/usbx-events/image150.png)    | **Host Class Pima Thumb Get** *(ux_host_class_pima_thumb_get)* |
| ![Ikona zapisu Pima klasy hosta](./media/user-guide/usbx-events/image151.png)    | **Host Class Pima Write** *(ux_host_class_pima_write)* |
| ![Ikona aktywowania drukarki klasy hosta](./media/user-guide/usbx-events/image152.png)    | **Aktywowanie drukarki klasy hosta** *(ux_host_class_printer_activate)* |
| ![Ikona dezaktywacji drukarki klasy hosta](./media/user-guide/usbx-events/image153.png)    | **Dezaktywacja drukarki** *klasy hosta (ux_host_class_printer_deactivate)* |
| ![Ikona Pobierz nazwę drukarki klasy hosta](./media/user-guide/usbx-events/image154.png)    | **Uzyskiwanie nazwy drukarki klasy hosta** *(ux_host_class_printer_name_get)* |
| ![Ikona odczytu drukarki klasy hosta](./media/user-guide/usbx-events/image155.png)    |  **Odczyt drukarki klasy hosta** *(ux_host_class_printer_read)* |
| ![Ikona nie soft resetu drukarki klasy hosta](./media/user-guide/usbx-events/image156.png)    | **Resetowanie nie soft resetu drukarki** *klasy hosta (ux_host_class_printer_soft_reset)* |
| ![Ikona Pobierz stan drukarki klasy hosta](./media/user-guide/usbx-events/image157.png)    | **Uzyskiwanie stanu drukarki klasy hosta** *(ux_host_class_printer_status_get)* |
| ![Ikona zapisu drukarki klasy hosta](./media/user-guide/usbx-events/image158.png)    | **Zapis drukarki klasy hosta** *(ux_host_class_printer_write)* |
| ![Ikona aktywacji prolific klasy hosta](./media/user-guide/usbx-events/image159.png)    | **Aktywowanie prolific klasy hosta** *(ux_host_class_prolific_activate)* |
| ![Ikona dezaktywacji klasy hosta](./media/user-guide/usbx-events/image160.png)    | **Dezaktywacja klasy hosta** *(ux_host_class_prolific_deactivate)* |
| ![Ikona przerwania klasy hosta W potoku](./media/user-guide/usbx-events/image161.png)    | **Przerwanie prolific Ioctl klasy** hosta w *potoku (ux_host_class_prolific_ioctl_abort_in_pipe)* |
| ![Ikona potoku wychodzącego przerwania klasy hosta](./media/user-guide/usbx-events/image162.png)    | **Potok wychodzący z przerwania prolific klasy** hosta *(ux_host_class_prolific_ioctl_abort_out_pipe)* |
| ![Ikona Pobierz stan urządzenia dla klasy hosta](./media/user-guide/usbx-events/image163.png)    | Pobierz stan urządzenia **dla prolific Ioctl** klasy *hosta (ux_host_class_prolific_ioctl_get_device_status)* |
| ![Ikona Kodowanie liniowe dla klasy hosta](./media/user-guide/usbx-events/image164.png)    | **Kodowanie z wiersza get (Get Line Coding) dla prolific Ioctl** klasy *hosta (ux_host_class_prolific_ioctl_get_line_coding)* |
| ![Ikona przeczyszczania klas hostów](./media/user-guide/usbx-events/image165.png)    | **Czyszczenie prolific Ioctl** klasy hosta *(ux_host_class_prolific_ioctl_purge)* |
| ![Ikona zmiany stanu urządzenia raportu klasy hosta](./media/user-guide/usbx-events/image166.png)    | **Zgłaszaj zmianę stanu** urządzenia w raporcie Ioctl klasy hosta *(ux_host_class_prolific_ioctl_report_device_status_change)* |
| ![Ikona przerwy wysyłania klas hostów](./media/user-guide/usbx-events/image167.png)    | **Przerwy wysyłania ioctl** klasy *hosta (ux_host_class_prolific_ioctl_send_break)* |
| ![Ikona kodowania liniowego zestawu klas hostów](./media/user-guide/usbx-events/image168.png)    | **Prolific Ioctl Ioctl Set Line Coding** *(ux_host_class_prolific_ioctl_set_line_coding)* |
| ![Ikona stanu wiersza zestawu klas hostów](./media/user-guide/usbx-events/image169.png)    | **Stan wiersza zestawu zestawu klas** hostów *(ux_host_class_prolific_ioctl_set_line_state)* |
| ![Ikona Prolific Read klasy hosta](./media/user-guide/usbx-events/image170.png)    | **Profesjonalny odczyt klasy hosta** *(ux_host_class_prolific_read)* |
| ![Ikona Uruchamiania fikcyjnego odbioru klasy hosta](./media/user-guide/usbx-events/image171.png)    | **Rozpoczęcie odbioru w klasie hosta** *(ux_host_class_prolific_reception_start)* |
| ![Ikona fikcyjnego zatrzymania odbioru klasy hosta](./media/user-guide/usbx-events/image172.png)    | **Fikcyjne zatrzymanie odbioru klasy hosta** *(ux_host_class_prolific_reception_stop)* |
| ![Ikona fikcyjnego zapisu klasy hosta](./media/user-guide/usbx-events/image173.png)    | **Fikcyjny zapis klasy hosta** *(ux_host_class_prolific_write)* |
| ![Ikona aktywacji Storage klasy hosta](./media/user-guide/usbx-events/image174.png)    | **Aktywowanie Storage klasy hosta** *(ux_host_class_storage_activate)* |
| ![Ikona dezaktywacji Storage klasy hosta](./media/user-guide/usbx-events/image175.png)    | **Dezaktywacja Storage klasy** hosta (*ux_host_class_storage_deactivate)* |
| ![Ikona Pobierz pojemność Storage klasy hosta](./media/user-guide/usbx-events/image176.png)    | **Uzyskiwanie pojemności Storage klasy hosta** *(ux_host_class_storage_media_capacity_get)* |
| ![Ikona Pobierz pojemność formatu nośnika Storage hostów](./media/user-guide/usbx-events/image177.png)    | **Uzyskiwanie pojemności formatu nośnika Storage klasy hosta** *(ux_host_class_storage_media_format_capacity_get)* |
| ![Ikona instalacji nośnika Storage klasy hosta](./media/user-guide/usbx-events/image178.png)    | **Host Class Storage Media Mount** (ux_host_class_storage_media_mount)* |
| ![Ikona Otwórz Storage klasy hosta](./media/user-guide/usbx-events/image179.png)    | **Host Class Storage Media Open** *(ux_host_class_storage_media_open)* |
| ![Ikona odczytu Storage klasy hosta](./media/user-guide/usbx-events/image180.png)    | **Odczyt nośnika Storage klasy hosta** *(ux_host_class_storage_media_read)* |
| ![Ikona zapisu Storage klasy hosta](./media/user-guide/usbx-events/image181.png)    | **Zapis multimediów Storage klasy hosta** *(ux_host_class_storage_media_write)* |
| ![Ikona sense Storage klasy hosta](./media/user-guide/usbx-events/image182.png)    | **Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)* |
| ![Ikona uruchamiania Storage klasy hosta](./media/user-guide/usbx-events/image183.png)    | **Uruchamianie Storage klasy hosta** *(ux_host_class_storage_start_stop)* |
| ![Ikona Testu gotowej jednostki Storage hostów](./media/user-guide/usbx-events/image184.png)    | **Test gotowości jednostki Storage hostów** *(ux_host_class_storage_activate)* |
| ![Ikona Tworzenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image185.png)    | **Tworzenie wystąpienia klasy stosu hosta** *(ux_host_stack_class_instance_create)* |
| ![Ikona niszczenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image186.png)    | **Niszczenie wystąpienia klasy stosu hosta** *(ux_host_stack_class_instance_destroy)* |
| ![Ikona Usuń konfigurację stosu hosta](./media/user-guide/usbx-events/image187.png)    | **Usuwanie konfiguracji stosu hosta** *(ux_host_stack_configuration_delete)* |
| ![Ikona wyliczenia konfiguracji stosu hosta](./media/user-guide/usbx-events/image188.png)    | **Wyliczanie konfiguracji stosu hosta** *(ux_host_stack_configuration_enumerate)* |
| ![Ikona Tworzenia wystąpienia konfiguracji stosu hosta](./media/user-guide/usbx-events/image189.png)    | **Tworzenie wystąpienia konfiguracji stosu hosta** *(ux_host_stack_configuration_instance_create)* |
| ![Ikona Usuń wystąpienie konfiguracji stosu hosta](./media/user-guide/usbx-events/image190.png)    | **Usuwanie wystąpienia konfiguracji stosu hosta** *(ux_host_stack_configuration_instance_delete)* |
| ![Ikona zestawu konfiguracji stosu hosta](./media/user-guide/usbx-events/image191.png)    | **Zestaw konfiguracji stosu hosta** *(ux_host_stack_configuration_set)* |
| ![Ikona zestawu adresów urządzeń stosu hosta](./media/user-guide/usbx-events/image192.png)    | **Zestaw adresów urządzeń stosu hosta** *(ux_host_stack_device_set)* |
| ![Ikona Pobierz konfigurację urządzenia stosu hosta](./media/user-guide/usbx-events/image193.png)    | **Uzyskiwanie konfiguracji urządzenia stosu hosta** *(ux_host_stack_device_configuration_get)* |
| ![Konfiguracja urządzenia stosu hosta Ikona wybierz](./media/user-guide/usbx-events/image194.png)    | **Wybór konfiguracji urządzenia stosu hosta** *(ux_host_stack_device_configuration_select)* |
| ![Ikona Odczytuj deskryptor urządzenia stosu hosta](./media/user-guide/usbx-events/image195.png)    | **Odczyt deskryptora urządzenia** stosu hosta *(ux_host_stack_device_descriptor_read)* |
| ![Ikona Pobierz urządzenie stosu hosta](./media/user-guide/usbx-events/image196.png)    | **Uzyskiwanie urządzenia stosu hosta** (ux_host_stack_device_get) |
| ![Ikona Usuń urządzenie stosu hosta](./media/user-guide/usbx-events/image197.png)    | **Usuwanie urządzenia stosu hosta** (ux_host_stack_device_get) |
| ![Ikona Bezpłatna zasób urządzenia stosu hosta](./media/user-guide/usbx-events/image198.png)    | **Host Stack Device Resource Free** (ux_host_stack_device_resource_free) |
| ![Ikona Tworzenia wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image199.png)    | **Tworzenie wystąpienia punktu końcowego stosu** hosta (ux_host_stack_endpoint_instance_create) |
| ![Ikona Usuwania wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image200.png)    | **Usuwanie wystąpienia punktu końcowego stosu hosta** (ux_host_stack_endpoint_instance_delete) |
| ![Ikona resetowania punktu końcowego stosu hosta](./media/user-guide/usbx-events/image201.png)    | **Resetowanie punktu końcowego stosu hosta** (ux_host_stack_endpoint_reset) |
| ![Ikona przerwania transferu punktu końcowego stosu hosta](./media/user-guide/usbx-events/image202.png)    | **Przerwanie transferu punktu końcowego stosu** hosta (ux_host_stack_endpoint_transfer_abort) |
| ![Ikona rejestrowania kontrolera hosta stosu hosta](./media/user-guide/usbx-events/image203.png)    | **Rejestrowanie kontrolera hosta stosu hosta** *(ux_host_stack_hcd_register)* |
| ![Ikona Inicjowanie stosu hosta](./media/user-guide/usbx-events/image204.png)    | **Inicjowanie stosu hosta** *(ux_host_stack_initialize)* |
| ![Ikona Pobierz punkt końcowy interfejsu stosu hosta](./media/user-guide/usbx-events/image205.png)    | **Uzyskiwanie punktu końcowego interfejsu stosu hosta** *(ux_host_stack_interface_endpoint_get)* |
| ![Ikona Tworzenia wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image206.png)    | **Tworzenie wystąpienia interfejsu stosu hosta** *(ux_host_stack_interface_instance_create)* |
| ![Ikona Usuwania wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image207.png)    | **Usuwanie wystąpienia interfejsu stosu hosta** *(ux_host_stack_interface_instance_delete)* |
| ![Ikona zestawu interfejsów stosu hosta](./media/user-guide/usbx-events/image208.png)    | **Zestaw interfejsu stosu hosta** *(ux_host_stack_interface_set)* |
| ![Ikona Wyboru ustawienia interfejsu stosu hosta](./media/user-guide/usbx-events/image209.png)    | **Wybieranie ustawienia interfejsu stosu hosta** *(ux_host_stack_interface_setting_select)* |
| ![Ikona Tworzenia nowej konfiguracji stosu hosta](./media/user-guide/usbx-events/image210.png)    | **Tworzenie nowej konfiguracji stosu hosta** *(ux_host_stack_new_configuration_create)* |
| ![Ikona Tworzenia nowego urządzenia w stosie hosta](./media/user-guide/usbx-events/image211.png)    | **Tworzenie nowego urządzenia stosu hosta** *(ux_host_stack_new_device_create)* |
| ![Ikona Tworzenia nowego punktu końcowego stosu hosta](./media/user-guide/usbx-events/image212.png)    | **Tworzenie nowego punktu końcowego stosu hosta** *(ux_host_stack_new_endpoint_create)* |
| ![Ikona procesu zmiany głównego centrum stosu hosta](./media/user-guide/usbx-events/image213.png)    | **Proces zmiany głównego centrum** stosu hosta *(ux_host_stack_rh_change_process)* |
| ![Ikona wyodrębniania urządzenia głównego centrum stosu hosta](./media/user-guide/usbx-events/image214.png)    | **Wyodrębnianie urządzeń z głównym koncentratorem** stosu hosta *(ux_host_stack_rh_device_extraction)* |
| ![Ikona wstawiania urządzenia głównego centrum stosu hosta](./media/user-guide/usbx-events/image215.png)    | **Wstawianie urządzenia głównego centrum stosu** hosta *(ux_host_stack_rh_device_insertion)* |
| ![Ikona żądania przeniesienia stosu hosta](./media/user-guide/usbx-events/image216.png)    | **Żądanie transferu stosu hosta** *(ux_host_stack_transfer_request)* |
| ![Ikona przerwania żądania przeniesienia stosu hosta](./media/user-guide/usbx-events/image217.png)    | **Przerwanie żądania transferu stosu** hosta *(ux_host_stack_transfer_request_abort)* |
| ![Ikona błędu U S B X](./media/user-guide/usbx-events/image218.png)    | **Błąd USBX** *(ux_error)* |

## <a name="event-descriptions"></a>Opisy zdarzeń

Na poniższych stronach opisano zdarzenia śledzenia USBX.

### <a name="device-class-cdc-activate"></a>Aktywacja CDC klasy urządzenia 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**Ikona** ![ Ikona aktywacji klasy urządzenia C D C](./media/user-guide/usbx-events/image1.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji CDC klasy urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-cdc-deactivate"></a>Dezaktywacja cdc klasy urządzenia 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**Ikona** ![ Ikona dezaktywacji klasy urządzenia C D C](./media/user-guide/usbx-events/image2.png)

**Opis**

To zdarzenie reprezentuje dezaktywację klasy urządzeń USBX CDC.

Pola informacji 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-cdc-read"></a>Odczyt cdc klasy urządzenia 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**Ikona** ![ Ikona odczytu klasy urządzenia C D C](./media/user-guide/usbx-events/image3.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu CDC klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="device-class-cdc-write"></a>Zapis CDC klasy urządzenia 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**Ikona** ![ Ikona zapisu klasy urządzenia C D C](./media/user-guide/usbx-events/image4.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu CDC klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="device-class-dpump-activate"></a>Aktywacja dpump klasy urządzenia 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**Ikona** ![ Ikona aktywacji dpump klasy urządzenia](./media/user-guide/usbx-events/image5.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji dpump klasy urządzeń USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-dpump-deactivate"></a>Dezaktywacja dpump klasy urządzenia 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**Ikona** ![ Ikona dezaktywacji dpump klasy urządzenia](./media/user-guide/usbx-events/image6.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji dpump klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-dpump-read"></a>Klasa urządzenia Dpump Read 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**Ikona** ![ Ikona odczytu dpump klasy urządzenia](./media/user-guide/usbx-events/image7.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu dpump klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Bufor.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="device-class-dpump-write"></a>Device Class Dpump Write 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**Ikona** ![ Ikona zapisu dpump klasy urządzenia](./media/user-guide/usbx-events/image8.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu dpump klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="device-class-hid-activate"></a>Aktywacja Hid klasy urządzenia 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**Ikona** ![ Ikona aktywacji Hid klasy urządzenia](./media/user-guide/usbx-events/image9.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji Hid klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-hid-deactivate"></a>Dezaktywacja klasy urządzeń 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**Ikona** ![ Ikona Dezaktywacja klasy urządzenia](./media/user-guide/usbx-events/image10.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy urządzeń USBX Hid.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-hid-descriptor-send"></a>Wysyłanie deskryptora Hid klasy urządzenia 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**Ikona** ![ Ikona wysyłania deskryptora Hid klasy urządzenia](./media/user-guide/usbx-events/image11.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania deskryptora Hid klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: typ deskryptora.
- Pole informacji 3: żądanie indeksu.
- Pole informacji 4: nie jest używane.

### <a name="device-class-hid-event-get"></a>Uzyskiwanie zdarzenia Hid klasy urządzenia 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**Ikona** ![ Ikona Get zdarzenia Hid klasy urządzenia](./media/user-guide/usbx-events/image12.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get klasy urządzenia USBX Hid.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-hid-event-set"></a>Zestaw zdarzeń Hid klasy urządzenia 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**Ikona** ![ Ikona zestawu zdarzeń Hid klasy urządzenia](./media/user-guide/usbx-events/image13.png)

**Opis**

To zdarzenie reprezentuje zestaw zdarzeń Hid klasy urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-hid-report-get"></a>Uzyskiwanie raportu Hid klasy urządzeń 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**Ikona** ![ Ikona Pobierz raport Hid klasy urządzenia](./media/user-guide/usbx-events/image14.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get raportu Hid klasy urządzeń USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: typ deskryptora.
- Pole informacji 3: żądanie indeksu.
- Pole informacji 4: nie jest używane.

### <a name="device-class-hid-report-set"></a>Zestaw raportów Hid klasy urządzeń 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**Ikona** ![ Ikona zestawu raportów Hid klasy urządzenia](./media/user-guide/usbx-events/image15.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu raportów Hid klasy urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: typ deskryptora.
- Pole informacji 3: żądanie indeksu.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-activate"></a>Aktywacja Pima klasy urządzenia

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**Ikona** ![ Ikona aktywacji Pima klasy urządzenia](./media/user-guide/usbx-events/image16.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji Pima klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-deactivate"></a>Dezaktywacja Pima klasy urządzenia 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**Ikona** ![ Ikona dezaktywacji Pima klasy urządzenia](./media/user-guide/usbx-events/image17.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji Pima klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-device-info-send"></a>Wysyłanie informacji o urządzeniu klasy urządzenia Pima 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**Ikona** ![ Ikona wysyłania informacji o urządzeniu klasy urządzenia Pima](./media/user-guide/usbx-events/image18.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania informacji o urządzeniu usbX klasy urządzenia Pima.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.

### <a name="device-class-pima-event-get"></a>Uzyskiwanie zdarzenia Pima klasy urządzenia 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**Ikona** ![ Ikona Pobierz zdarzenie Pima klasy urządzenia](./media/user-guide/usbx-events/image19.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get klasy urządzenia USBX Pima.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Zdarzenie Pima.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-event-set"></a>Zestaw zdarzeń Pima klasy urządzenia 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**Ikona** ![ Ikona zestawu zdarzeń Pima klasy urządzenia](./media/user-guide/usbx-events/image20.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu zdarzeń Pima klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Zdarzenie Pima.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-object-add"></a>Dodawanie obiektu Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**Ikona** ![ Ikona dodawania obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image21.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dodawania obiektu Pima klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-object-data-get"></a>Uzyskiwanie danych obiektu Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**Ikona** ![ Ikona Pobierz dane obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image22.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get danych obiektu Pima klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-object-data-send"></a>Wysyłanie danych obiektu Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**Ikona** ![ Ikona wysyłania danych obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image23.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania danych obiektu Pima klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-object-delete"></a>Usuwanie obiektu Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**Ikona** ![ Ikona usuwania obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image24.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia obiektu Pima klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-object-handles-send"></a>Wysyłanie uchwytów obiektu Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**Ikona** ![ Ikona Wysyłania uchwytów obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image25.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania obiektu Pima klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Storage identyfikator.
- Pole informacji 3: Kod formatu obiektu.
- Pole informacji 4: Skojarzenie obiektu.

### <a name="device-class-pima-object-info-get"></a>Uzyskiwanie informacji o obiekcie Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ikona** ![ Ikona Pobierz informacje o obiekcie Pima klasy urządzenia](./media/user-guide/usbx-events/image26.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get informacji o obiekcie Pima klasy urządzenia USBX.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-object-info-send"></a>Wysyłanie informacji o obiekcie Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ikona** ![ Ikona wysyłania informacji o obiekcie Pima klasy urządzenia](./media/user-guide/usbx-events/image27.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania informacji o obiekcie Pima klasy urządzenia USBX.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-objects-number-send"></a>Wysyłanie liczby obiektów Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**Ikona** ![ Ikona Wysyłania liczby obiektów Pima klasy urządzenia](./media/user-guide/usbx-events/image28.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania numeru obiektu Pima klasy urządzenia USBX.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Storage identyfikator.
- Info Field 3: Object format code (Pole informacyjne 3: kod formatu obiektu).
- Pole informacji 4: Skojarz obiekt.

### <a name="device-class-pima-partial-object-data-get"></a>Pobierz dane obiektu częściowego Pima klasy urządzenia

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**Ikona** ![ Ikona Pobierz dane częściowego obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image29.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get danych częściowych obiektu USBX klasy urządzenia Pima.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: Żądane przesunięcie.
- Pole informacji 4: żądana długość.

### <a name="device-class-pima-response-send"></a>Wysyłanie odpowiedzi Pima klasy urządzenia 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**Ikona** ![ Ikona wysyłania odpowiedzi Pima klasy urządzenia](./media/user-guide/usbx-events/image30.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania odpowiedzi Pima klasy urządzenia USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Info Field 2: Response code (Pole informacyjne 2: kod odpowiedzi).
- Info Field 3: Number parameter (Pole informacyjne 3: parametr liczbowy).
- Pole informacyjne 4: parametr Pima 1.

### <a name="device-class-pima-storage-id-send"></a>Wysyłanie identyfikatora urządzenia Storage Pima klasy urządzenia 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**Ikona** ![ Ikona wysyłania identyfikatora Storage Device Class Pima](./media/user-guide/usbx-events/image31.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Pima Storage Id Send Event.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-pima-storage-info-send"></a>Wysyłanie informacji o Storage Pima klasy urządzenia 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**Ikona** ![ Ikona wysyłania informacji Storage Device Class Pima](./media/user-guide/usbx-events/image32.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Pima Storage zdarzeń wysyłania informacji.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-rndis-activate"></a>Aktywacja Rndis klasy urządzenia 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**Ikona** ![ Ikona aktywacji Rndis klasy urządzenia](./media/user-guide/usbx-events/image33.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji Rndis klasy urządzenia USBX.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-rndis-deactivate"></a>Dezaktywacja Rndis klasy urządzenia 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**Ikona** ![ Ikona dezaktywacji Rndis klasy urządzenia](./media/user-guide/usbx-events/image34.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy urządzenia USBX.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-rndis-message-keep-alive"></a>Zachowanie aktywności komunikatu Rndis klasy urządzenia 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>ux_device_class_rndis_msg_keep_alive

**Ikona** ![ Ikona podtrzymania aktywności komunikatu Rndis klasy urządzenia](./media/user-guide/usbx-events/image35.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Rndis klasy urządzenia USBX dla komunikatu o aktywności.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-rndis-message-query"></a>Zapytanie komunikatów Rndis klasy urządzenia 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**Ikona** ![ Ikona zapytania komunikatu Rndis klasy urządzenia](./media/user-guide/usbx-events/image36.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapytania komunikatów Rndis klasy urządzenia USBX.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Rndis OID.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-rndis-message-reset"></a>Resetowanie komunikatów Rndis klasy urządzenia 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**Ikona** ![ Ikona resetowania komunikatów Rndis klasy urządzenia](./media/user-guide/usbx-events/image37.png)

**Opis**

To zdarzenie reprezentuje zdarzenie resetowania komunikatów Rndis klasy urządzenia USBX.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.

### <a name="device-class-rndis-message-set"></a>Zestaw komunikatów Rndis klasy urządzeń 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**Ikona** ![ Ikona zestawu komunikatów Rndis klasy urządzenia](./media/user-guide/usbx-events/image38.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu komunikatów Rndis klasy urządzenia USBX.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Rndis OID.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-rndis-packet-receive"></a>Odbieranie pakietów Rndis klasy urządzenia 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**Ikona** ![ Ikona odbierania pakietów Rndis klasy urządzenia](./media/user-guide/usbx-events/image39.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odbierania pakietów Rndis klasy urządzenia USBX.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-rndis-packet-transmit"></a>Przesyłanie pakietów Rndis klasy urządzenia 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**Ikona** ![ Ikona przesyłania pakietów Rndis klasy urządzenia](./media/user-guide/usbx-events/image40.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przesyłania pakietów Rndis klasy urządzenia USBX.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-activate"></a>Aktywacja klasy Storage urządzeń 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**Ikona** ![ Ikona aktywacji Storage klasy urządzenia](./media/user-guide/usbx-events/image41.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage uaktywnienie zdarzenia.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-deactivate"></a>Dezaktywacja Storage klasy urządzenia 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**Ikona** ![ Ikona dezaktywacji Storage Urządzenia](./media/user-guide/usbx-events/image42.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage dezaktywacji zdarzenia.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-format"></a>Format Storage klasy urządzenia 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**Ikona** ![ Ikona formatu Storage klasy urządzenia](./media/user-guide/usbx-events/image43.png)

**Opis**

To zdarzenie reprezentuje zdarzenie formatu Storage USBX.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-inquiry"></a>Zapytanie dotyczące Storage klas urządzeń 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**Ikona** ![ Ikona zapytania Storage klasa urządzenia](./media/user-guide/usbx-events/image44.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage zdarzenia zapytania.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-mode-select"></a>Wybieranie trybu Storage klasy urządzenia

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**Ikona** ![ Ikona wyboru Storage klasy urządzenia](./media/user-guide/usbx-events/image45.png)

**Opis**

To zdarzenie reprezentuje klasy urządzenia USBX Storage trybie zaznaczania zdarzenia.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-mode-sense"></a>Device Class Storage Mode Sense 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**Ikona** ![ Ikona sense Storage Klasy urządzenia](./media/user-guide/usbx-events/image46.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX dla Storage Sense Mode.

Pola informacji 

- nfo, pole 1: wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-prevent-allow-media-removal"></a>Ustawienia klasy urządzeń Storage zezwalaj na usuwanie multimediów 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**Ikona** ![ Ikona Zezwalaj Storage zezwalaj na usuwanie multimediów przy Storage urządzenia](./media/user-guide/usbx-events/image47.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage zapobiegać zdarzeniu usuwania nośnika.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-read"></a>Odczyt Storage urządzenia 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**Ikona** ![ Ikona odczytu Storage Klasy urządzeń](./media/user-guide/usbx-events/image48.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage odczytu.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacyjne 3: Sektor.
- Pole informacyjne 4: Sektory liczb.

### <a name="device-class-storage-read-capacity"></a>Pojemność odczytu Storage klasy urządzenia 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**Ikona** ![ Ikona pojemności odczytu Storage Urządzenia](./media/user-guide/usbx-events/image49.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage odczytu pojemności.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-read-format-capacity"></a>Pojemność formatu odczytu Storage klasy urządzenia 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**Ikona** ![ Ikona pojemności Storage format odczytu klasy urządzenia](./media/user-guide/usbx-events/image50.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage format odczytu pojemności.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-read-toc"></a>Klasa urządzenia Storage toc odczytu 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**Ikona** ![ Ikona odczytywania Storage urządzenia](./media/user-guide/usbx-events/image51.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage odczytywania toc zdarzenia.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-request-sense"></a>Device Class Storage Request Sense 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**Ikona** ![ Ikona device class Storage request sense](./media/user-guide/usbx-events/image52.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage żądania.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: klucz sense.
- Pole informacji 4: Kod.

### <a name="device-class-storage-start-stop"></a>Uruchamianie/zatrzymywanie Storage klasy urządzeń 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**Ikona** ![ Ikona uruchamiania Storage klasy urządzenia](./media/user-guide/usbx-events/image53.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage start stop.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-test-ready"></a>Gotowość do testowania Storage urządzenia 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**Ikona** ![ Ikona Gotowość Storage urządzenia do testowania](./media/user-guide/usbx-events/image54.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage test gotowe zdarzenie.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-verify"></a>Weryfikacja Storage urządzenia 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**Ikona** ![ Ikona weryfikacji Storage urządzenia](./media/user-guide/usbx-events/image55.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage zdarzenia weryfikacji.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-class-storage-write"></a>Zapis Storage klasy urządzenia 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**Ikona** ![ Ikona Storage zapisu klasy urządzenia](./media/user-guide/usbx-events/image56.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Storage zdarzenia zapisu.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: Lun.
- Pole informacyjne 3: Sektor.
- Pole informacyjne 4: Liczba sektorów.

### <a name="device-stack-alternate-setting-get"></a>Uzyskiwanie alternatywnego ustawienia stosu urządzeń 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**Ikona** ![ Ikona Pobierz ustawienie alternatywne stosu urządzeń](./media/user-guide/usbx-events/image57.png)

**Opis**

To zdarzenie reprezentuje alternatywne ustawienie Pobierz stos urządzeń USBX.

**Pola informacji**

- Pole informacji 1: wartość interfejsu.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-alternate-setting-set"></a>Zestaw alternatywnych ustawień stosu urządzeń 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**Ikona** ![ Ikona zestawu ustawień alternatywnych stosu urządzeń](./media/user-guide/usbx-events/image58.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu ustawień alternatywnych stosu urządzeń USBX.

**Pola informacji**
- Pole informacji 1: wartość interfejsu.
- Pole informacji 2: Wartość ustawienia alternatywnego.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-class-register"></a>Rejestrowanie klas stosu urządzeń 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**Ikona** ![ Ikona Rejestracji klasy stosu urządzeń](./media/user-guide/usbx-events/image59.png)

**Opis**

To zdarzenie reprezentuje zdarzenie rejestrowania klasy stosu urządzeń USBX.

**Pola informacji**

- Pole informacji 1: Nazwa klasy.
- Pole informacyjne 2: Numer interfejsu.
- Pole informacji 3: parametr.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-clear-feature"></a>Funkcja Wyczyść stos urządzeń 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**Ikona** ![ Ikona funkcji Wyczyść stos urządzeń](./media/user-guide/usbx-events/image60.png)

**Opis**

To zdarzenie reprezentuje zdarzenie funkcji wyczyść stos urządzenia USBX.

**Pola informacji**

- Pole informacji 1: Typ żądania.
- Pole informacji 2: wartość żądania. Pole informacyjne 3: indeks żądania.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-configuration-get"></a>Uzyskiwanie konfiguracji stosu urządzeń 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**Ikona** ![ Ikona Pobierz konfigurację stosu urządzeń](./media/user-guide/usbx-events/image61.png)

**Opis**

To zdarzenie reprezentuje konfigurację stosu urządzeń USBX Pobierz zdarzenie.

**Pola informacji** 

- Pole informacji 1: wartość konfiguracji.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-configuration-set"></a>Zestaw konfiguracji stosu urządzeń 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**Ikona** ![ Ikona zestawu konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image62.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu konfiguracji stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wartość konfiguracji.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-connect"></a>Ustawienia stosu Połączenie 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**Ikona** ![ Ikona Połączenie stosu urządzeń](./media/user-guide/usbx-events/image63.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania deskryptora stosu urządzeń USBX.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-descriptor-send"></a>Wysyłanie deskryptora stosu urządzeń 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**Ikona** ![ Ikona wysyłania deskryptora stosu urządzeń](./media/user-guide/usbx-events/image64.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania deskryptora stosu urządzeń USBX.

**Pola informacji**

- Pole informacji 1: typ deskryptora.
- Pole informacyjne 2: indeks żądania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-disconnect"></a>Rozłączanie stosu urządzeń 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**Ikona** ![ Ikona rozłączania stosu urządzeń](./media/user-guide/usbx-events/image65.png)

**Opis**

To zdarzenie reprezentuje zdarzenie rozłączania stosu urządzeń USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-endpoint-stall"></a>Wstrzymanie punktu końcowego stosu urządzeń 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**Ikona** ![ Ikona zatrzymań punktu końcowego stosu urządzeń](./media/user-guide/usbx-events/image66.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wstrzymania punktu końcowego stosu urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: Punkt końcowy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-get-status"></a>Uzyskiwanie stanu stosu urządzeń 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**Ikona** ![ Ikona Pobierz stan stosu urządzeń](./media/user-guide/usbx-events/image67.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get stanu stosu urządzenia USBX.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-host-wakeup"></a>Wznawianie hosta stosu urządzeń 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**Ikona** ![ Ikona wznawiania hosta stosu urządzeń](./media/user-guide/usbx-events/image68.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wznawiania hosta stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-initialize"></a>Inicjowanie stosu urządzeń 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**Ikona** ![ Ikona Inicjowanie stosu urządzeń](./media/user-guide/usbx-events/image69.png)

**Opis**

To zdarzenie reprezentuje zdarzenie inicjowania stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-interface-delete"></a>Usuwanie interfejsu stosu urządzeń 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**Ikona** ![ Ikona usuwania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image70.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usuwania interfejsu stosu urządzeń USBX.

**Pola informacji**

- Pole informacji 1: Interfejs.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-interface-get"></a>Uzyskiwanie interfejsu stosu urządzeń 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**Ikona** ![ Ikona Pobierz interfejs stosu urządzeń](./media/user-guide/usbx-events/image71.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get interfejsu stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wartość interfejsu.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-interface-set"></a>Zestaw interfejsów stosu urządzeń 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**Ikona** ![ Ikona zestawu interfejsów stosu urządzeń](./media/user-guide/usbx-events/image72.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu interfejsów stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wartość żądania. Pole informacji 2: żądanie indeksu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-set-feature"></a>Funkcja zestawu stosów urządzeń 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**Ikona** ![ Ikona funkcji zestawu stosów urządzeń](./media/user-guide/usbx-events/image73.png)

**Opis**

To zdarzenie reprezentuje zdarzenie funkcji zestawu stosów urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wartość żądania. Pole informacji 2: żądanie indeksu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-transfer-abort"></a>Przerwanie transferu stosu urządzeń 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**Ikona** ![ Ikona przerwania transferu stosu urządzeń](./media/user-guide/usbx-events/image74.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania transferu stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: Żądanie przeniesienia.
- Pole informacji 2: Kod ukończenia.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-transfer-all-request-abort"></a>Przenoszenie wszystkich żądań przerwania stosu urządzeń 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**Ikona** ![ Ikona Przekieruj wszystkie żądania w stosie urządzeń](./media/user-guide/usbx-events/image75.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania wszystkich żądań za pomocą stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: Punkt końcowy.
- Pole informacji 2: Kod ukończenia.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="device-stack-transfer-request"></a>Żądanie transferu stosu urządzeń 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**Ikona** ![ Ikona żądania przeniesienia stosu urządzeń](./media/user-guide/usbx-events/image76.png)

**Opis**

To zdarzenie reprezentuje zdarzenie żądania transferu stosu urządzeń USBX.

**Pola informacji**

- Pole informacji 1: Żądanie przeniesienia.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-asix-activate"></a>Aktywowanie asix klasy hosta 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**Ikona** ![ Ikona aktywowania klasy hosta w asix](./media/user-guide/usbx-events/image77.png)

**Opis**

To zdarzenie reprezentuje aktywację Asix klasy hosta USBX.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-asix-deactivate"></a>Dezaktywacja asix klasy hosta 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**Ikona** ![ Ikona dezaktywacji klasy hosta Asix](./media/user-guide/usbx-events/image78.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX Asix.

**Pola informacji** 

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-asix-interrupt-notification"></a>Powiadomienie o przerwaniu asix klasy hosta 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**Ikona** ![ Ikona powiadomienia o przerwaniu asix klasy hosta](./media/user-guide/usbx-events/image79.png)

**Opis**

To zdarzenie reprezentuje zdarzenie powiadomienia o przerwaniu asix klasy hosta USBX.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-asix-read"></a>Host Class Asix Read 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**Ikona** ![ Ikona Read (Asix) klasy hosta](./media/user-guide/usbx-events/image80.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu asix klasy hosta USBX.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-asix-write"></a>Host Class Asix Write 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**Ikona** ![ Ikona zapisu Asix klasy hosta](./media/user-guide/usbx-events/image81.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu Asix klasy hosta USBX.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-audio-activate"></a>Aktywowanie dźwięku klasy hosta 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**Ikona** ![ Ikona aktywowania dźwięku klasy hosta](./media/user-guide/usbx-events/image82.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji audio klasy hosta USBX.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-audio-control-value-get"></a>Pobierz wartość kontrolki audio klasy hosta 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**Ikona** ![ Ikona Pobierz wartość kontrolki audio klasy hosta](./media/user-guide/usbx-events/image83.png)

**Opis**

To zdarzenie reprezentuje wartość kontrolki audio klasy hosta USBX Pobierz zdarzenie.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-audio-control-value-set"></a>Zestaw wartości kontrolki audio klasy hosta 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**Ikona** ![ Ikona zestawu wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image84.png)

**Opis**

To zdarzenie reprezentuje zdarzenia przetwarzania odroczonego wewnętrznego sterownika NetX We/Wy.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: kontrolka dźwięku.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-audio-deactivate"></a>Dezaktywacja dźwięku klasy hosta 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**Ikona** ![ Ikona dezaktywacji dźwięku klasy hosta](./media/user-guide/usbx-events/image85.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji audio klasy hosta USBX.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-audio-read"></a>Odczyt audio klasy hosta 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**Ikona** ![ Ikona odczytu dźwięku klasy hosta](./media/user-guide/usbx-events/image86.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu audio klasy hosta USBX.

- Pola informacji 
- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-audio-streaming-sampling-get"></a>Pobieranie próbkowania audio przesyłania strumieniowego klasy hosta 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**Ikona** ![ Ikona Pobierz próbkowanie audio przesyłania strumieniowego klasy hosta](./media/user-guide/usbx-events/image87.png)

**Opis**

To zdarzenie reprezentuje klasy hosta USBX próbkowanie audio przesyłania strumieniowego Pobierz zdarzenie.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-audio-streaming-sampling-set"></a>Zestaw próbkowania przesyłania strumieniowego audio klasy hosta 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**Ikona** ![ Ikona zestawu próbkowania przesyłania strumieniowego audio klasy hosta](./media/user-guide/usbx-events/image88.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu próbkowania przesyłania strumieniowego audio klasy hosta USBX.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Próbkowanie audio.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-audio-write"></a>Zapis audio klasy hosta 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**Ikona** ![ Ikona zapisu audio klasy hosta](./media/user-guide/usbx-events/image89.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu audio klasy hosta USBX.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-activate"></a>Aktywowanie klasy hosta CDC Acm 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**Ikona** ![ Ikona aktywacji klasy hosta C D C A C M](./media/user-guide/usbx-events/image90.png)

**Opis**

To zdarzenie reprezentuje klasy hosta USBX Cdc Acm Aktywowanie zdarzenia.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-deactivate"></a>Dezaktywacja klasy hosta CDC Acm 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**Ikona** ![ Ikona dezaktywacji klasy hosta C D C A C M](./media/user-guide/usbx-events/image91.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX CDC Acm.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>Klasa hosta Cdc Acm Ioctl Abort in Pipe 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**Ikona** ![ Host Class C D C A C M I O C T L Abort In Pipe icon (Klasa hosta C D C A C M I O C T L Abort In Pipe icon)](./media/user-guide/usbx-events/image92.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Cdc Acm Ioctl Abort In Pipe Event.

Pola informacji 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>Host Class Cdc Acm Ioctl Abort Out Pipe 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**Ikona** ! [ Host Class C D C A C M I O C T L Abort Out Pipe icon (Klasa [hosta C D C A C M I O C T L przerwania potoku wychodzącego)](./media/user-guide/usbx-events/image93.png)

**Opis**

To zdarzenie reprezentuje zdarzenie potoku wychodzącego abort klasy hosta USBX Cdc Acm Ioctl Abort Out Pipe.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>Host Class Cdc Acm Ioctl Get Device Status 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**Ikona** ![ Host Class C D C A C M I O C T L Get Device Status icon (Klasa hosta C D C A C M I O C T L Pobierz stan urządzenia)](./media/user-guide/usbx-events/image94.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Cdc Acm Ioctl Get Device Status Event.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Stan urządzenia.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>Host Class Cdc Acm Ioctl Get Line Coding 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**Ikona** ![ Host Class C D C A C M I O C T L Get Line Coding icon (Klasa hosta C D C A C M I O C T L Pobierz kodowanie liniowe)](./media/user-guide/usbx-events/image95.png)

**Opis**

To zdarzenie reprezentuje zdarzenie kodowania get line klasy hosta USBX Cdc Acm Ioctl.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>Wywołanie zwrotne powiadomień Ioctl klasy hosta CDC Acm

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**Ikona** ![ Host Class C D C A C M I O C T L Notification Callback icon (Klasa hosta C D C A C M I O C T L Ikona wywołania zwrotnego powiadomień)](./media/user-guide/usbx-events/image96.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wywołania zwrotnego powiadomienia Ioctl klasy hosta USBX CDC Acm.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-ioctl-send-break"></a>Podział wysyłania Ioctl klasy hosta Cdc Acm 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**Ikona** ![ Host Class C D C A C M I O C T L Send Break icon (Klasa hosta C D C A C M I O C T L Send Break)](./media/user-guide/usbx-events/image97.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania wysyłania Ioctl klasy hosta USBX Cdc Acm.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>Host Class Cdc Acm Ioctl Set Line Coding 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**Ikona** ![ Ikona kodowania liniowego zestawu hostów Klasa C D C A C M I O C T L zestawu ](./media/user-guide/usbx-events/image97.png) kodu](./media/user-guide/usbx-events/image98.png)

**Opis**

To zdarzenie reprezentuje zdarzenie kodowania liniowego zestawu Ioctl klasy hosta USBX Cdc Acm.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>Host Class Cdc Acm Ioctl Set Line State 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**Ikona** ![ Host Class C D C A C M I O C T L Set Line State icon (Klasa hosta C D C A C M I O C T L Set Line State) ikona](./media/user-guide/usbx-events/image99.png)

**Opis**

To zdarzenie reprezentuje zdarzenie stanu wiersza zestawu Ioctl klasy hosta USBX Cdc Acm.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-read"></a>Klasa hosta Cdc Acm Read 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**Ikona** ![ Host Class C D C A C M Read icon (Klasa hosta C D A C M ikona odczytu)](./media/user-guide/usbx-events/image100.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu Acm klasy hosta USBX Cdc.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-reception-start"></a>Host Class Cdc Acm Reception Start 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**Ikona** ![ Host Class C D C A C M Reception Start icon (Klasa hosta C D C A C M ikona rozpoczęcia odbioru)](./media/user-guide/usbx-events/image101.png)

**Opis**

To zdarzenie reprezentuje zdarzenie rozpoczęcia odbioru klasy hostów USBX Cdc Acm.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-reception-stop"></a>Host Class Cdc Acm Reception Stop 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**Ikona** ![ Host Class C D C A C M Reception Stop icon (Klasa hosta C D C A C M ikona zatrzymania odbioru)](./media/user-guide/usbx-events/image102.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zatrzymania odbioru cdc Acm klasy hosta USBX.

**Pola informacji**

- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-cdc-acm-write"></a>Klasa hosta Cdc Acm Write 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**Ikona** ![ Host Class C D C A C M Write icon (Klasa hosta C D C A C M Ikona zapisu)](./media/user-guide/usbx-events/image103.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu Acm Acm klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-dpump-activate"></a>Aktywowanie dpump klasy hosta 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**Ikona** ![ Ikona aktywacji dpump klasy hosta](./media/user-guide/usbx-events/image104.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji dpump klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-dpump-deactivate"></a>Dezaktywacja dpump klasy hosta 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**Ikona** ![ Ikona dezaktywacji dpump klasy hosta](./media/user-guide/usbx-events/image105.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji dpump klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-dpump-read"></a>Odczyt dpump klasy hosta 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**Ikona** ![ Ikona odczytu dpump klasy hosta](./media/user-guide/usbx-events/image106.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu dpump klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-dpump-write"></a>Host Class Dpump Write 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**Ikona** ![ Ikona zapisu dpump klasy hosta](./media/user-guide/usbx-events/image107.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu dpump klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-activate"></a>Aktywowanie klasy hosta Hid 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**Ikona** ![ Ikona aktywowania klasy hosta](./media/user-guide/usbx-events/image108.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji Hid klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-client-register"></a>Rejestr klienta Hid klasy hosta 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**Ikona** ![ Ikona rejestru klienta Hid klasy hosta](./media/user-guide/usbx-events/image109.png)

**Opis**

To zdarzenie reprezentuje zdarzenie rejestru klienta Hid klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Ukrywanie nazwy klienta.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-deactivate"></a>Dezaktywacja klasy hosta 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**Ikona** ![ Ikona Dezaktywacja klasy hosta](./media/user-guide/usbx-events/image110.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX Hid.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-idle-get"></a>Host Class Hid Idle Get 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**Ikona** ![ Ikona get get klasy hosta Hid Idle](./media/user-guide/usbx-events/image111.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Hid Idle Get klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-idle-set"></a>Zestaw bezczynności Hid klasy hosta 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**Ikona** ![ Ikona zestawu bezczynności Hid klasy hosta](./media/user-guide/usbx-events/image112.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu bezczynności Hid klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-keyboard-activate"></a>Aktywowanie klawiatury Hid klasy hosta 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**Ikona** ![ Ikona aktywowania klawiatury Hid klasy hosta](./media/user-guide/usbx-events/image113.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji klawiatury Hid klasy hosta USBX.

**Pola informacji**
<p>Pole informacji 1: Wystąpienie klasy.
<p>Pole informacji 2: Wystąpienie klienta Hid.
<p>Pole informacji 3: nie jest używane.
<p>Pole informacji 4: nie jest używane.

### <a name="host-class-hid-keyboard-deactivate"></a>Dezaktywacja klawiatury Hid klasy hosta 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**Ikona** ![ Ikona dezaktywacji klawiatury Hid klasy hosta](./media/user-guide/usbx-events/image114.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klawiatury Hid klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Wystąpienie klienta Hid.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-mouse-activate"></a>Aktywowanie myszy Hid klasy hosta 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**Ikona** ![ Ikona aktywowania myszy Hid klasy hosta](./media/user-guide/usbx-events/image115.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji myszy Hid klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Wystąpienie klienta Hid.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-mouse-deactivate"></a>Dezaktywacja myszy Hid klasy hosta 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**Ikona** ![ Ikona dezaktywacji myszy Hid klasy hosta](./media/user-guide/usbx-events/image116.png)

**Opis**

- To zdarzenie reprezentuje zdarzenie dezaktywacji myszy Hid klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Wystąpienie klienta Hid.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-remote-control-activate"></a>Aktywowanie zdalnego sterowania za pomocą klasy hosta 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**Ikona** ![ Ikona aktywowania zdalnego sterowania za pomocą funkcji Host Class Hid](./media/user-guide/usbx-events/image117.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Hid zdarzenia aktywacji zdalnego sterowania.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Wystąpienie klienta Hid.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-remote-control-deactivate"></a>Dezaktywacja zdalnego sterowania przy ukrywaniu klasy hosta 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**Ikona** ![ Ikona dezaktywacji zdalnego sterowania ukrywania klasy hosta](./media/user-guide/usbx-events/image118.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX Hid zdalnego sterowania.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Wystąpienie klienta Hid.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-report-get"></a>Uzyskiwanie raportu Hid klasy hosta 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**Ikona** ![ Ikona Pobierz raport Hid klasy hosta](./media/user-guide/usbx-events/image119.png)

**Opis**

To zdarzenie reprezentuje raport Hid klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Raport klienta.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hid-report-set"></a>Zestaw raportów Hid klasy hosta 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**Ikona** ![ Ikona zestawu raportów Hid klasy hosta](./media/user-guide/usbx-events/image120.png)

**Opis** To zdarzenie reprezentuje zestaw raportów Hid klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Raport klienta.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hub-activate"></a>Aktywowanie centrum klas hosta 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**Ikona** ![ Ikona aktywowania centrum klas hosta](./media/user-guide/usbx-events/image121.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji koncentratora klasy hosta USBX.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hub-change-detect"></a>Wykrywanie zmian centrum klas hosta 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**Ikona** ![ Ikona Wykrywania zmian centrum klas hosta](./media/user-guide/usbx-events/image122.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wykrywania zmiany centrum klas hostów USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hub-deactivate"></a>Dezaktywacja centrum klas hosta 

#### <a name="ux_host_class_hub_deactivate"></a>ux_host_class_hub_deactivate

**Ikona** ![ Ikona dezaktywacji centrum klas hosta](./media/user-guide/usbx-events/image123.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji koncentratora klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hub-port-change-connection-process"></a>Proces zmiany połączenia portu koncentratora klasy hosta 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**Ikona** ![ Ikona Procesu zmiany połączenia portu centrum klasy hosta](./media/user-guide/usbx-events/image124.png)

**Opis**

To zdarzenie reprezentuje zdarzenie procesu zmiany połączenia portu koncentratora klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Port.
- Pole informacyjne 3: Stan portu.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hub-port-change-enable-process"></a>Proces włączania zmiany portu koncentratora klasy hosta 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**Ikona** ![ Ikona Włącz proces zmiany portu centrum klas hosta](./media/user-guide/usbx-events/image125.png)

**Opis**

To zdarzenie reprezentuje zdarzenie procesu włączania portu koncentratora klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Port.
- Pole informacyjne 3: Stan portu.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hub-port-change-over-current-process"></a>Zmiana portu centrum klas hosta w bieżącym procesie 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**Ikona** ![ Ikona Zmiany portu centrum klas hosta w 2018 r.](./media/user-guide/usbx-events/image126.png)

**Opis**

To zdarzenie reprezentuje przydzielenie pakietu za pośrednictwem nx_packet_allocate.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Port.
- Pole informacji 3: Stan portu.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hub-port-change-reset-process"></a>Proces resetowania portu centrum klas hosta 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**Ikona** ![ Ikona procesu resetowania portu centrum klas hosta](./media/user-guide/usbx-events/image127.png)

**Opis**

To zdarzenie reprezentuje zdarzenie procesu resetowania portu centrum klas hostów USBX.

**Pola informacji**

- Pole informacji 1: Centrum. Pole informacji 2: Port.
- Pole informacji 3: Stan portu.
- Pole informacji 4: nie jest używane.

### <a name="host-class-hub-port-change-suspend-process"></a>Proces wstrzymania zmiany portu centrum klas hosta 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**Ikona** ![ Ikona wstrzymywania procesu zmiany portu centrum klas hosta](./media/user-guide/usbx-events/image128.png)

**Opis**

To zdarzenie reprezentuje zdarzenie procesu wstrzymania portu koncentratora klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Port.
- Pole informacji 3: Stan portu.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-activate"></a>Aktywowanie klasy hosta Pima 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**Ikona** ![ Ikona aktywacji Pima klasy hosta](./media/user-guide/usbx-events/image129.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-deactivate"></a>Dezaktywacja Pima klasy hosta 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**Ikona** ![ Ikona dezaktywacji klasy hosta Pima](./media/user-guide/usbx-events/image130.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-device-info-get"></a>Uzyskiwanie informacji o urządzeniu klasy hosta Pima 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**Ikona** ![ Ikona Pobierz informacje o urządzeniu klasy hosta Pima](./media/user-guide/usbx-events/image131.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get informacji o urządzeniu USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: urządzenie Pima.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-device-reset"></a>Resetowanie urządzenia klasy hosta Pima 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**Ikona** ![ Ikona resetowania urządzenia klasy hosta Pima](./media/user-guide/usbx-events/image132.png)

**Opis**

To zdarzenie reprezentuje zdarzenie resetowania urządzenia Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-notification"></a>Powiadomienie Pima klasy hosta 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**Ikona** ![ Ikona powiadomienia Pima klasy hosta](./media/user-guide/usbx-events/image133.png)

**Opis**

To zdarzenie reprezentuje zdarzenie powiadomień Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy. Pole informacji 2: kod zdarzenia.
- Pole informacji 3: identyfikator transakcji.
- Pole informacji 4: Parametr1.

### <a name="host-class-pima-number-objects-get"></a>Host Class Pima Number Objects Get 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**Ikona** ![ Ikona Pobierz obiekty numeru Pima klasy hosta](./media/user-guide/usbx-events/image134.png)

**Opis**

To zdarzenie reprezentuje obiekt numeru Pima hosta USBX Pobierz zdarzenie.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-object-close"></a>Zamknięcie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**Ikona** ![ Ikona zamknięcia obiektu Pima klasy hosta](./media/user-guide/usbx-events/image135.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zamknięcia obiektu Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Obiekt.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-object-copy"></a>Kopiowanie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**Ikona** ![ Ikona kopiowania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image136.png)

**Opis**

To zdarzenie reprezentuje zdarzenie kopiowania obiektu Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-object-delete"></a>Usuwanie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**Ikona** ![ Ikona Usuwania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image137.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia obiektu Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-object-get"></a>Host Class Pima Object Get 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**Ikona** ![ Ikona Pobierz obiekt Pima klasy hosta](./media/user-guide/usbx-events/image138.png)

**Opis**

To zdarzenie reprezentuje pobieranie informacji RARP za pośrednictwem nx_rarp_info_get.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: Obiekt.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-object-info-get"></a>Uzyskiwanie informacji o obiekcie Pima klasy hosta 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**Ikona** ![ Ikona Pobierz informacje o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image139.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get informacji o obiekcie Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: Obiekt.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-object-info-send"></a>Wysyłanie informacji o obiekcie Pima klasy hosta 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**Ikona** ![ Ikona wysyłania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image140.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania informacji o obiekcie Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Obiekt.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-object-move"></a>Przenoszenie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ikona** ![ Ikona przenoszenia obiektu Pima klasy hosta](./media/user-guide/usbx-events/image141.png)

**Opis**

To zdarzenie reprThis reprezentuje zdarzenie przenoszenia obiektu Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: Obiekt.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-object-send"></a>Wysyłanie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ikona** ![ Ikona wysyłania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image142.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania obiektu Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Obiekt.
- Pole informacji 3: Bufor obiektów.
- Pole informacji 4: Długość obiektu.

### <a name="host-class-pima-object-transfer-abort"></a>Przerwanie transferu obiektów Pima klasy hosta 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**Ikona** ![ Ikona przerwania transferu obiektów Pima klasy hosta](./media/user-guide/usbx-events/image143.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania transferu obiektów Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: Obiekt.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-read"></a>Klasa hosta Pima Read 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**Ikona** ![ Ikona odczytu klasy hosta Pima](./media/user-guide/usbx-events/image144.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: Długość danych.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-request-cancel"></a>Anulowanie żądania Pima klasy hosta 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**Ikona** ![ Ikona anulowania żądania Pima klasy hosta](./media/user-guide/usbx-events/image145.png)

**Opis**

To zdarzenie reprezentuje zdarzenie anulowania żądania Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-session-close"></a>Zamknięcie sesji Pima klasy hosta 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**Ikona** ![ Ikona zamknięcia sesji Pima klasy hosta](./media/user-guide/usbx-events/image146.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zamknięcia sesji Pima klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: sesja Pima.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-session-open"></a>Sesja Pima klasy hosta otwarta 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**Ikona** ![ Ikona Otwórz sesję Pima klasy hosta](./media/user-guide/usbx-events/image147.png)

**Opis** To zdarzenie reprezentuje zdarzenie otwartej sesji Pima klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: sesja Pima.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-storage-ids-get"></a>Identyfikatory identyfikatorów Storage Pima klasy hosta Get 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**Ikona** ![ Host Class Pima Storage Ids (Pobierz identyfikatory klasy hosta)](./media/user-guide/usbx-events/image148.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Pima Storage identyfikatory get zdarzenia.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- nfo Pole 2: Storage tablicy identyfikatorów.
- Pole informacji 3: Storage długość identyfikatora.
Pole informacji 4: nie jest używane.

### <a name="host-class-pima-storage-info-get"></a>Uzyskiwanie informacji o Storage Pima klasy hosta 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**Ikona** ![ Ikona pobierz informacje o Storage Pima klasy hosta](./media/user-guide/usbx-events/image149.png)

**Opis**

To zdarzenie reprezentuje klasy hosta USBX Pima Storage informacji o zdarzeniu.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Storage identyfikator.
- Pole informacji 3: Storage.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-thumb-get"></a>Pobierz miniaturę Pima klasy hosta 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ikona** ![ Ikona Pobierz miniaturę Pima klasy hosta](./media/user-guide/usbx-events/image150.png)

**Opis**

To zdarzenie reprezentuje nieakceptowanie połączenia serwera TCP za pośrednictwem nx_tcp_server_socket_unaccept.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: Dojście do obiektu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-pima-write"></a>Klasa hosta Pima Write 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ikona** ![ Ikona zapisu Pima klasy hosta](./media/user-guide/usbx-events/image151.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Pima Write.

**Pola informacji**

- Pole informacyjne 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacyjne 3: Długość danych.
- Pole informacji 4: nie jest używane.

### <a name="host-class-printer-activate"></a>Aktywowanie drukarki klasy hosta 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**Ikona** ![ Ikona aktywowania drukarki klasy hosta](./media/user-guide/usbx-events/image152.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji drukarki klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia adresu IP.
- Info Field 2: Pointer to socket (Pole informacyjne 2: wskaźnik do gniazda).
- Pole informacyjne 3: typ usługi.
- Pole informacyjne 4: rozmiar okna odbioru.

### <a name="host-class-printer-deactivate"></a>Dezaktywacja drukarki klasy hosta 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**Ikona** ![ Ikona dezaktywacji drukarki klasy hosta](./media/user-guide/usbx-events/image153.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji drukarki klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-printer-name-get"></a>Uzyskiwanie nazwy drukarki klasy hosta 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**Ikona** ![ Ikona Pobierz nazwę drukarki klasy hosta](./media/user-guide/usbx-events/image154.png)

**Opis**

To zdarzenie reprezentuje nazwę drukarki klasy hosta USBX Pobierz zdarzenie.

**Pola informacji** 

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-printer-read"></a>Odczyt drukarki klasy hosta 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**Ikona** ![ Ikona odczytu drukarki klasy hosta](./media/user-guide/usbx-events/image155.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu drukarki klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-printer-soft-reset"></a>Resetowanie nie softowe drukarki klasy hosta 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**Ikona** ![ Ikona nie soft resetu drukarki klasy hosta](./media/user-guide/usbx-events/image156.png)

**Opis**

To zdarzenie reprezentuje zdarzenie nie soft resetu drukarki klasy hosta USBX.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-printer-status-get"></a>Uzyskiwanie stanu drukarki klasy hosta 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**Ikona** ![ Ikona Pobierz stan drukarki klasy hosta](./media/user-guide/usbx-events/image157.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get stanu drukarki klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Stan drukarki.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-printer-write"></a>Zapis drukarki klasy hosta 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**Ikona** ![ Ikona zapisu drukarki klasy hosta](./media/user-guide/usbx-events/image158.png)

**Opis**

To zdarzenie reprezentuje zapis drukarki klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-activate"></a>Aktywowanie prolific klasy hosta 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**Ikona** ![ Ikona aktywacji prolific klasy hosta](./media/user-guide/usbx-events/image159.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywacji prolific klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-deactivate"></a>Dezaktywacja klasy hosta 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**Ikona** ![ Ikona dezaktywacji klasy hosta](./media/user-guide/usbx-events/image160.png)

**Opis**

To zdarzenie reprezentuje zdarzenie prolific dezaktywacji klasy hostów USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>Przerwanie prolific Ioctl klasy hosta w potoku 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**Ikona** ![ Ikona przerwania klasy hosta I O O C T L Abort w potoku](./media/user-guide/usbx-events/image161.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX prolific Ioctl Abort In Pipe Event.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>Potok wychodzący od przerwania klasy hosta prolific Ioctl 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**Ikona** ![ Ikona potoku wychodzącego przerwania klasy hosta I O C T L](./media/user-guide/usbx-events/image162.png)

**Opis**

To zdarzenie reprezentuje zdarzenie potoku wychodzącego octl prolific klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-get-device-status"></a>Pobierz stan urządzenia dla prolific Ioctl klasy hosta 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**Ikona** ![ Ikona Pobierz stan urządzenia dla klasy hosta](./media/user-guide/usbx-events/image163.png)

**Opis**

To zdarzenie reprezentuje zdarzenie stanu urządzenia prolific Ioctl klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Stan urządzenia.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-get-line-coding"></a>Prolific Ioctl Klasy hostów Get Line Coding 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**Ikona** ![ Ikona Kodowania liniowego get klasy hosta Prolific I O O C T L](./media/user-guide/usbx-events/image164.png)

**Opis**

To zdarzenie reprezentuje zdarzenie kodowania liniowego w klasie hostów USBX prolific Ioctl.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-purge"></a>Czyszczenie prolific Ioctl klasy hosta 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**Ikona** ![ Ikona oczyszczania prolific Ioctl klasy hosta](./media/user-guide/usbx-events/image165.png)

**Opis**

To zdarzenie reprezentuje zdarzenie prolific Ioctl ioctl klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-report-device"></a>Host Class Prolific Ioctl Report Device 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**Ikona** ![ Ikona urządzenia raportu klasy hostów I O O C T L](./media/user-guide/usbx-events/image166.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany stanu urządzenia raportu o stanie urządzenia klasy hostów USBX.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-send-break"></a>Przerwy wysyłania prolific Ioctl klasy hosta 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**Ikona** ![ Ikona przerwy wysyłania klas hostów](./media/user-guide/usbx-events/image167.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX prolific Ioctl Send Break Event.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-set-line-coding"></a>Prolific Ioctl Ioctl Set Line Coding (Kodowanie liniowe zestawu klas hostów) 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**Ikona** ![ Ikona kodowania liniowego zestawu klas hostów](./media/user-guide/usbx-events/image168.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX prolific Ioctl Set Line Coding Event.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-ioctl-set-line-state"></a>Host Class Prolific Ioctl Set Line State 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**Ikona** ![ Ikona stanu wiersza zestawu klas hostów](./media/user-guide/usbx-events/image169.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX prolific Ioctl ustawić stanu wiersza zdarzenia.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: parametr.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-read"></a>Prolific Read klasy hosta 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**Ikona** ![ Ikona Prolific Read klasy hosta](./media/user-guide/usbx-events/image170.png)

**Opis**

To zdarzenie reprezentuje klasy hosta USBX prolific read zdarzenia.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-reception-start"></a>Uruchamianie fikcyjnego odbioru klasy hosta 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**Ikona** ![ Ikona Uruchamiania fikcyjnego odbioru klasy hosta](./media/user-guide/usbx-events/image171.png)

**Opis**

To zdarzenie reprezentuje klasy hosta USBX prolific zdarzenie rozpoczęcia odbioru.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-reception-stop"></a>Fikcyjny zatrzymywanie odbioru klasy hosta 

#### <a name="ux_host_class_prolific_reception_stop"></a>ux_host_class_prolific_reception_stop

**Ikona** ![ Ikona fikcyjnego zatrzymania odbioru klasy hosta](./media/user-guide/usbx-events/image172.png)

**Opis**

To zdarzenie reprezentuje klasy hosta USBX fikcyjne zdarzenie zatrzymania odbioru.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-prolific-write"></a>Fikcyjny zapis klasy hosta 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**Ikona** ![ Ikona fikcyjnego zapisu klasy hosta](./media/user-guide/usbx-events/image173.png)

**Opis**

To zdarzenie reprezentuje klasy hosta USBX prolific zapisu zdarzenia.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacyjne 2: Wskaźnik danych.
- Pole informacji 3: żądana długość.
- Pole informacji 4: nie jest używane.

### <a name="host-class-storage-activate"></a>Aktywowanie klasy Storage hosta 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**Ikona** ![ Ikona aktywacji Storage klasy hosta](./media/user-guide/usbx-events/image174.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage uaktywnienie zdarzenia.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-storage-deactivate"></a>Dezaktywacja Storage hostów 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**Ikona** ![ Ikona dezaktywacji Storage klasy hosta](./media/user-guide/usbx-events/image175.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage dezaktywacji zdarzenia.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-storage-media-capacity-get"></a>Uzyskiwanie pojemności nośnika Storage klasy hosta 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**Ikona** ![ Ikona Pobierz pojemność Storage klasy hosta](./media/user-guide/usbx-events/image176.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage nośnika Pobierz zdarzenie.

**Pola informacji**

- Info Field 1: Class instance (Pole informacyjne 1: wystąpienie klasy).
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-storage-media-format-capacity-get"></a>Uzyskiwanie pojemności Storage formatu nośnika klasy hosta

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**Ikona** ![ Ikona Pobierz Storage formatu nośnika klasy hosta](./media/user-guide/usbx-events/image177.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage format nośnika Pobierz zdarzenie.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

#### <a name="host-class-storage-media-mount"></a>Host Class Storage Media Mount 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**Ikona** ![ Ikona instalacji nośnika Storage Klasy hosta](./media/user-guide/usbx-events/image178.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage zdarzeń instalacji nośnika.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Sektor.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-storage-media-open"></a>Host Class Storage Media Open 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**Ikona** ![ Ikona Otwórz Storage Klasy hosta](./media/user-guide/usbx-events/image179.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage nośnika otwartego zdarzenia.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: Multimedia.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-storage-media-read"></a>Klasa hosta Storage do odczytu multimediów 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**Ikona** ![ Ikona odczytu Storage klasy hosta](./media/user-guide/usbx-events/image180.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage zdarzeń odczytu multimediów.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Początek sektora.
- Pole informacyjne 3: Liczba sektorów.
- Pole informacyjne 4: Wskaźnik danych.

### <a name="host-class-storage-media-write"></a>Klasa hosta Storage zapisu multimediów 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**Ikona** ![ Ikona zapisu Storage klasy hosta](./media/user-guide/usbx-events/image181.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage zdarzeń zapisu multimediów.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacyjne 2: Początek sektora.
- Pole informacyjne 3: Liczba sektorów.
- Pole informacyjne 4: Wskaźnik danych.

### <a name="host-class-storage-request-sense"></a>Host Class Storage Request Sense 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**Ikona** ![ Ikona usługi Host Class Storage Request Sense](./media/user-guide/usbx-events/image182.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage żądania.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-storage-start-stop"></a>Uruchamianie Storage klasy hosta 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**Ikona** ![ Ikona uruchamiania Storage klasy hosta](./media/user-guide/usbx-events/image183.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage start stop.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: sygnał uruchamiania/zatrzymania.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-class-storage-unit-ready-test"></a>Test gotowości jednostkowej Storage hostów 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**Ikona** ![ Ikona testów gotowości Storage Host Class (Klasa hosta)](./media/user-guide/usbx-events/image184.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX Storage testowe gotowe do użycia jednostki.

**Pola informacji**

- Pole informacji 1: Wystąpienie klasy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-class-instance-create"></a>Tworzenie wystąpienia klasy stosu hosta 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ikona** ![ Ikona tworzenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image185.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia klasy stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Klasa.
- Pole informacji 2: Wystąpienie klasy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-class-instance-destroy"></a>Niszczenie wystąpienia klasy stosu hosta 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ikona** ![ Ikona niszczenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image186.png)

**Opis**

To zdarzenie reprezentuje zdarzenie niszczenia wystąpienia klasy stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Klasa.
- Pole informacji 2: Wystąpienie klasy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-configuration-delete"></a>Usuwanie konfiguracji stosu hosta 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**Ikona** ![ Ikona Usuń konfigurację stosu hosta](./media/user-guide/usbx-events/image187.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usuwania konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Konfiguracja.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-configuration-enumerate"></a>Wyliczanie konfiguracji stosu hosta 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**Ikona** ![ Ikona wyliczenia konfiguracji stosu hosta](./media/user-guide/usbx-events/image188.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wyliczania konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="stack-configuration-instance-create"></a>Tworzenie wystąpienia konfiguracji stosu 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**Ikona** ![ Ikona Tworzenia wystąpienia konfiguracji stosu](./media/user-guide/usbx-events/image189.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Konfiguracja.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-configuration-instance-delete"></a>Usuwanie wystąpienia konfiguracji stosu hosta 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**Ikona** ![ Ikona Usuń wystąpienie konfiguracji stosu hosta](./media/user-guide/usbx-events/image190.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia wystąpienia konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Konfiguracja.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-configuration-set"></a>Zestaw konfiguracji stosu hosta 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**Ikona** ![ Ikona zestawu konfiguracji stosu hosta](./media/user-guide/usbx-events/image191.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Konfiguracja.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-device-address-set"></a>Zestaw adresów urządzeń stosu hosta 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**Ikona** ![ Ikona zestawu adresów urządzeń stosu hosta](./media/user-guide/usbx-events/image192.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu adresów urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: Adres urządzenia.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-device-configuration-get"></a>Uzyskiwanie konfiguracji urządzenia stosu hosta 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**Ikona** ![ Ikona Pobierz konfigurację urządzenia stosu hosta](./media/user-guide/usbx-events/image193.png)

**Opis**

To zdarzenie reprezentuje konfigurację urządzenia stosu hosta USBX Pobierz zdarzenie.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- nfo Pole 2: konfiguracja.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-device-configuration-select"></a>Konfiguracja urządzenia stosu hosta Wybierz 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**Ikona** ![ Konfiguracja urządzenia stosu hosta Ikona wybierz](./media/user-guide/usbx-events/image194.png)

**Opis**

To zdarzenie reprezentuje konfiguracji urządzenia stosu hosta USBX Wybierz zdarzenie.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: Konfiguracja.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-device-descriptor-read"></a>Odczytanie deskryptora urządzenia stosu hosta 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**Ikona** ![ Ikona Odczytuj deskryptor urządzenia stosu hosta](./media/user-guide/usbx-events/image195.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu deskryptora urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-device-get"></a>Pobierz urządzenie stosu hosta 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**Ikona** ![ Ikona Pobierz urządzenie stosu hosta](./media/user-guide/usbx-events/image196.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Indeks urządzeń.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-device-remove"></a>Usuwanie urządzenia stosu hosta 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**Ikona** ![ Ikona Usuń urządzenie stosu hosta](./media/user-guide/usbx-events/image197.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Hcd.
- Pole informacji 2: nadrzędne.
- Pole informacyjne 3: Indeks portów.
- Pole informacji 4: Urządzenie.

### <a name="host-stack-device-resource-free"></a>Stos hosta bez zasobów urządzenia 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**Ikona** ![ Ikona Bezpłatna zasób urządzenia stosu hosta](./media/user-guide/usbx-events/image198.png)

**Opis**

To zdarzenie reprezentuje usbx stosu hosta urządzenia zasób free zdarzenia.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-endpoint-instance-create"></a>Tworzenie wystąpienia punktu końcowego stosu hosta 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**Ikona** ![ Ikona Tworzenia wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image199.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-endpoint-instance-delete"></a>Usuwanie wystąpienia punktu końcowego stosu hosta 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**Ikona** ![ Ikona Usuń wystąpienie punktu końcowego stosu hosta](./media/user-guide/usbx-events/image200.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia wystąpienia punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-endpoint-reset"></a>Resetowanie punktu końcowego stosu hosta 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**Ikona** ![ Ikona resetowania punktu końcowego stosu hosta](./media/user-guide/usbx-events/image201.png)

**Opis**

To zdarzenie reprezentuje zdarzenie resetowania punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-endpoint-transfer-abort"></a>Przerwanie transferu punktu końcowego stosu hosta 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**Ikona** ![ Ikona przerwania transferu punktu końcowego stosu hosta](./media/user-guide/usbx-events/image202.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania transferu punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Punkt końcowy.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-host-controller-register"></a>Rejestrowanie kontrolera hosta stosu hosta 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**Ikona** ![ Ikona rejestracji kontrolera hosta stosu hosta](./media/user-guide/usbx-events/image203.png)

**Opis**

To zdarzenie reprezentuje kontroler hosta stosu hosta USBX rejestru.

**Pola informacji**

- Pole informacyjne 1: Nazwa hcd.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-initialize"></a>Inicjowanie stosu hosta 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**Ikona** ![ Ikona Inicjowanie stosu hosta](./media/user-guide/usbx-events/image204.png)

**Opis**

To zdarzenie reprezentuje zdarzenie inicjowania stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-interface-endpoint-get"></a>Uzyskiwanie punktu końcowego interfejsu stosu hosta 

#### <a name="interface_-tcp-retry-entry"></a>Interface_ wpis ponawiania prób protokołu TCP

**Ikona** ![ Ikona Pobierz punkt końcowy interfejsu stosu hosta](./media/user-guide/usbx-events/image205.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie ponawiania próby protokołu TCP NetX.

**Pola informacji**

- Pole informacji 1: Interfejs.
- Pole informacyjne 2: Indeks punktu końcowego.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-interface-instance-create"></a>Tworzenie wystąpienia interfejsu stosu hosta 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**Ikona** ![ Ikona Utwórz wystąpienie interfejsu stosu hosta](./media/user-guide/usbx-events/image206.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia interfejsu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Interfejs.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-interface-instance-delete"></a>Usuwanie wystąpienia interfejsu stosu hosta 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**Ikona** ![ Ikona Usuwania wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image207.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usuwania wystąpienia interfejsu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Interfejs.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-interface-set"></a>Zestaw interfejsu stosu hosta 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**Ikona** ![ Ikona zestawu interfejsów stosu hosta](./media/user-guide/usbx-events/image208.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu interfejsu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Interfejs.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-interface-setting-select"></a>Wybieranie ustawienia interfejsu stosu hosta 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**Ikona** ![ Ikona Wyboru ustawienia interfejsu stosu hosta](./media/user-guide/usbx-events/image209.png)

**Opis**

To zdarzenie reprezentuje ustawienie interfejsu stosu hosta USBX Wybierz zdarzenie.

**Pola informacji**

- Pole informacji 1: Interfejs.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-new-configuration-create"></a>Tworzenie nowej konfiguracji stosu hosta 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**Ikona** ![ Ikona Tworzenia nowej konfiguracji stosu hosta](./media/user-guide/usbx-events/image210.png)

**Opis**
 
To zdarzenie reprezentuje zdarzenie tworzenia nowej konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: Konfiguracja.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-new-device-create"></a>Tworzenie nowego urządzenia w stosie hosta 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**Ikona** ![ Ikona Tworzenia nowego urządzenia w stosie hosta](./media/user-guide/usbx-events/image211.png)

**Opis**
 
 To zdarzenie reprezentuje zdarzenie tworzenia nowego urządzenia w stosie hosta USBX.

**Pola informacji**

- Pole informacji 1: Hcd.
- Pole informacji 2: Właściciel urządzenia.
- Pole informacji 3: Indeks portów.
- Pole informacji 4: Urządzenie.

### <a name="host-stack-new-endpoint-create"></a>Tworzenie nowego punktu końcowego stosu hosta 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**Ikona** ![ Ikona Tworzenia nowego punktu końcowego stosu hosta](./media/user-guide/usbx-events/image212.png)

**Opis**
 
To zdarzenie reprezentuje zdarzenie tworzenia nowego punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Interfejs.
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-root-hub-change-process"></a>Proces zmiany głównego centrum stosu hosta 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**Ikona** ![ Ikona procesu zmiany głównego centrum stosu hosta](./media/user-guide/usbx-events/image213.png)

**Opis**
 
To zdarzenie reprezentuje proces zmiany głównego koncentratora stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Indeks portów.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-root-hub-device-extraction"></a>Wyodrębnianie urządzenia głównego centrum stosu hosta 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**Ikona** ![ Ikona wyodrębniania urządzenia głównego centrum stosu hosta](./media/user-guide/usbx-events/image214.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wyodrębniania urządzenia głównego koncentratora stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Hcd.
- Pole informacji 2: Indeks portów.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-root-hub-device-insertion"></a>Wstawianie urządzenia głównego koncentratora stosu hosta 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**Ikona** ![ Ikona wstawiania urządzenia głównego centrum stosu hosta](./media/user-guide/usbx-events/image215.png)

**Opis**

To zdarzenie reprezentuje wstawianie urządzenia głównego koncentratora stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Hcd.
- Pole informacji 2: Indeks portów.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-transfer-request"></a>Żądanie transferu stosu hosta 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**Ikona** ![ Ikona żądania przeniesienia stosu hosta](./media/user-guide/usbx-events/image216.png)

**Opis**

To zdarzenie reprezentuje żądanie transferu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: Żądanie przeniesienia.
- Pole informacji 4: nie jest używane.

### <a name="host-stack-transfer-request-abort"></a>Przerwanie żądania transferu stosu hosta 

#### <a name="internal-io-driver-get-status"></a>Uzyskiwanie stanu wewnętrznego sterownika we/wy

**Ikona** ![ Ikona przerwania żądania przeniesienia stosu hosta](./media/user-guide/usbx-events/image217.png)

**Opis**

To zdarzenie reprezentuje przerwanie żądania transferu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Urządzenie.
- Pole informacji 2: Punkt końcowy.
- Pole informacji 3: Żądanie przeniesienia.
- Pole informacji 4: nie jest używane.

### <a name="usbx-error"></a>Błąd USBX 

#### <a name="ux_error"></a>ux_error

**Ikona** ![ Ikona błędu U S B X](./media/user-guide/usbx-events/image218.png)

**Opis**

To zdarzenie reprezentuje zdarzenie błędu USBX.

**Pola informacji**

- Pole informacji 1: błąd USBX.
- Pole informacji 2: Nazwa błędu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.