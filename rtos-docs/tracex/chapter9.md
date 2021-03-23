---
title: Rozdział 9 — zdarzenia śledzenia usługi Azure RTO USBX
description: Ten rozdział zawiera opis zdarzeń usługi Azure RTO USBX wyświetlanych przez usługę TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 98561fe1d131e1d1b0893b7d89eb720881a82ac8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824253"
---
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a>Rozdział 9 — zdarzenia śledzenia usługi Azure RTO USBX

Ten rozdział zawiera opis zdarzeń usługi Azure RTO USBX wyświetlanych przez usługę TraceX. 

## <a name="list-of-events-and-icons"></a>Lista zdarzeń i ikon

Poniżej znajduje się lista zdarzeń USBX wyświetlanych przez TraceX.

| Ikona                             | Znaczenie                               |
| -------------------------------- | ------------------------------------- |
| ![Ikona urządzenia C D C aktywacja](./media/user-guide/usbx-events/image1.png)    | **Aktywowanie przechwytywania klas urządzeń** *(ux_device_class_cdc_activate)* |
| ![Ikona klasy urządzenia C D C](./media/user-guide/usbx-events/image2.png)    | **Dezaktywacja przechwytywania klasy urządzeń** *(ux_device_class_cdc_deactivate)* |
| ![Ikona Odczytaj klasy urządzeń C D C](./media/user-guide/usbx-events/image3.png)    | **Odczytywanie danych przechwytywania z klasy urządzeń** *(ux_device_class_cdc_read)* |
| ![Ikona urządzenia C D C pisanie](./media/user-guide/usbx-events/image4.png)    | **Zapis przechwytywania danych klasy urządzeń** *(ux_device_class_cdc_write)* |
| ![Ikona urządzenia Dpump Activate](./media/user-guide/usbx-events/image5.png)    | **Dpump aktywowania klasy urządzenia** *(ux_device_class_dpump_activate)* |
| ![Ikona dezaktywowania klasy urządzenia Dpump](./media/user-guide/usbx-events/image6.png)    | **Dezaktywacja klasy urządzenia Dpump** *(ux_device_class_dpump_deactivate)* |
| ![Ikona odczytu Dpump klasy urządzeń](./media/user-guide/usbx-events/image7.png)    | **Dpump Odczytaj klasy urządzenia** *(ux_device_class_dpump_read)* |
| ![Ikona zapisu Dpump klasy urządzeń](./media/user-guide/usbx-events/image8.png)    | **Dpump** *(Ux_device_class_dpump_write)* klasy urządzeń |
| ![Ikona klasy urządzenia HID Aktywuj](./media/user-guide/usbx-events/image9.png)    | **Aktywacja klasy urządzenia HID** *(ux_device_class_hid_activate)* |
| ![Ikona dezaktywacji klasy urządzenia](./media/user-guide/usbx-events/image10.png)    | **Dezaktywacja klasy urządzenia HID** *(ux_device_class_hid_deactivate)* |
| ![Ikona wysyłania deskryptora HID klasy urządzeń](./media/user-guide/usbx-events/image11.png)    | **Wysyłanie deskryptora HID klasy urządzeń** *(ux_device_class_hid_descriptor_send)* |
| ![Ikona pobierania zdarzenia HID z klasą urządzeń](./media/user-guide/usbx-events/image12.png)    | **Pobieranie zdarzenia HID** *(Ux_device_class_hid_event_get)* klasy urządzeń |
| ![Ikona zestawu zdarzeń HID klasy urządzeń](./media/user-guide/usbx-events/image13.png)    | **Zestaw zdarzeń HID klasy urządzenia** *(ux_device_class_hid_event_set)* |
| ![Ikona pobierania raportu HID klasy urządzeń](./media/user-guide/usbx-events/image14.png)    | **Pobieranie raportu HID klasy urządzeń** *(ux_device_class_hid_report_get)* |
| ![Ikona zestawu raportów HID klasy urządzeń](./media/user-guide/usbx-events/image15.png)    | **Zestaw raportów HID klasy urządzenia** *(ux_device_class_hid_report_set)* |
| ![Ikona urządzenia Pima Activate](./media/user-guide/usbx-events/image16.png)    | **Pima aktywowania klasy urządzenia** *(ux_device_class_pima_activate)* |
| ![Ikona dezaktywowania klasy urządzenia Pima](./media/user-guide/usbx-events/image17.png)    | **Dezaktywacja klasy urządzenia Pima** *(ux_device_class_pima_deactivate)* |
| ![Ikona wysyłania informacji o urządzeniu Pima klasy urządzeń](./media/user-guide/usbx-events/image18.png)    | **Klasa urządzenia Pima wysyłanie informacji o urządzeniu** *(ux_device_class_pima_device_info_send)* |
| ![Ikona pobierania zdarzenia Pima klasy urządzeń](./media/user-guide/usbx-events/image19.png)    | **Pobieranie zdarzenia Pima klasy urządzenia** *(ux_device_class_pima_event_get)* |
| ![Ikona zestawu zdarzeń Pima klasy urządzeń](./media/user-guide/usbx-events/image20.png)    | **Zestaw zdarzeń Pima klasy urządzeń** *(ux_device_class_pima_event_set)* |
| ![Ikona dodawania obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image21.png)    | **Dodawanie obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_add)* |
| ![Ikona uzyskiwania danych obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image22.png)    | **Pobieranie danych obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_data_get)* |
| ![Ikona wysyłania danych obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image23.png)    | **Wysyłanie danych obiektu Pima klasy urządzeń** *(ux_device_class_pima_object_data_send)* |
| ![Ikona usuwania obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image24.png)    | **Usuwanie obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_delete)* |
| ![Obiekt Pima klasy urządzenia obsługuje ikonę wysyłania](./media/user-guide/usbx-events/image25.png)    | **Obiekt Pima klasy urządzenia obsługuje wysyłanie** *(ux_device_class_pima_object_handles_send)* |
| ![Ikona uzyskiwania informacji o obiekcie Pima klasy urządzeń](./media/user-guide/usbx-events/image26.png)    | **Pobieranie informacji o obiekcie Pima klasy urządzenia** *(ux_device_class_pima_object_info_get)* |
| ![Ikona wysyłania informacji o obiekcie Pima klasy urządzenia](./media/user-guide/usbx-events/image27.png)    | **Wysyłanie informacji o obiekcie Pima klasy urządzenia** *(ux_device_class_pima_object_info_send)* |
| ![Ikona Pima obiektów klasy urządzeń](./media/user-guide/usbx-events/image28.png)    | **Klasa urządzenia Pima liczba obiektów do wysłania** *(ux_device_class_pima_objects_number_send)* |
| ![Ikona Pima części danych obiektu klasy urządzenia](./media/user-guide/usbx-events/image29.png)    | **Klasa urządzenia Pima częściowe dane obiektu Get** *(ux_device_class_pima_partial_object_data_get)* |
| ![Ikona wysyłania odpowiedzi Pima klasy urządzeń](./media/user-guide/usbx-events/image30.png)    | **Odpowiedź klasy urządzenia Pima Send** *(ux_device_class_pima_response_send)*|
| ![Ikona wysyłania I Pima magazynu klasy urządzeń](./media/user-guide/usbx-events/image31.png)    | **Klasa urządzenia Pima — wysyłanie identyfikatora magazynu** *(ux_device_class_pima_storage_id_send)* |
| ![Ikona wysyłania informacji o magazynie Pima klasy urządzeń](./media/user-guide/usbx-events/image32.png)    | **Klasa urządzenia Pima — wysyłanie informacji o magazynie** *(ux_device_class_pima_storage_info_send)* |
| ![Ikona urządzenia R N D I aktywacja](./media/user-guide/usbx-events/image33.png)    | **RNDIS aktywowania klasy urządzenia** *(ux_device_class_rndis_activate)* |
| ![Ikona urządzenia R N D I S Dezaktywuj](./media/user-guide/usbx-events/image34.png)    | **Dezaktywacja klasy urządzenia RNDIS** *(ux_device_class_rndis_deactivate)* |
| ![Klasa urządzenia R N D I S komunikat o zachowaniu Aliveicon](./media/user-guide/usbx-events/image35.png)    | **RNDIS komunikat o klasie urządzenia** *(ux_device_class_rndis_msg_keep_alive)* |
| ![Ikona zapytania R N D I komunikat o błędzie dla klasy urządzenia](./media/user-guide/usbx-events/image36.png)    | **Kwerenda komunikatu RNDIS klasy urządzenia** *(ux_device_class_rndis_msg_query)* |
| ![Klasa urządzenia R N D I S ikona resetowania komunikatu](./media/user-guide/usbx-events/image37.png)    | **Resetowanie komunikatu o klasie urządzeń RNDIS** *(ux_device_class_rndis_msg_reset)* |
| ![Klasa urządzenia R N D I S ikona zestawu komunikatów](./media/user-guide/usbx-events/image38.png)    | **RNDIS klasy urządzeń — zestaw komunikatów** *(ux_device_class_rndis_msg_set)* |
| ![Klasa urządzenia R N D I S — ikona odbierania pakietów](./media/user-guide/usbx-events/image39.png)    | **Odbieranie pakietu RNDIS klasy urządzeń** *(ux_device_class_rndis_packet_receive)* |
| ![Klasa urządzenia R N D I S ikona wysyłania pakietów](./media/user-guide/usbx-events/image40.png)    | **RNDIS przesyłania pakietów klasy urządzeń** *(ux_device_class_rndis_packet_transmit)* |
| ![Ikona aktywacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image41.png)    | **Aktywowanie magazynu klasy urządzeń** *(ux_device_class_storage_activate)* |
| ![Ikona dezaktywacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image42.png)    | **Dezaktywacja magazynu klasy urządzeń** *(ux_device_class_storage_deactivate)* |
| ![Ikona formatu magazynu klasy urządzeń](./media/user-guide/usbx-events/image43.png)    | **Format magazynu klasy urządzeń** *(ux_device_class_storage_format)* |
| ![Ikona zapytania dotyczącego magazynu klasy urządzeń](./media/user-guide/usbx-events/image44.png)    | **Zapytanie dotyczące magazynu klasy urządzeń** *(ux_device_class_storage_inquiry)* |
| ![Ikona wybierania trybu przechowywania klasy urządzeń](./media/user-guide/usbx-events/image45.png)    | **Tryb przechowywania klasy urządzeń** *(ux_device_class_storage_mode_select)* |
| ![Ikona wykrywania trybu przechowywania klasy urządzeń](./media/user-guide/usbx-events/image46.png)    | **Sens trybu przechowywania klasy urządzeń** *(ux_device_class_storage_mode_sense)* |
| ![Nie Zezwalaj na usuwanie nośnika z magazynu klasy urządzeń](./media/user-guide/usbx-events/image47.png)    | **Magazyn klasy urządzeń uniemożliwia usunięcie nośnika** *(ux_device_class_storage_prevent_allow_media_removal)* |
| ![Ikona odczytu magazynu klasy urządzeń](./media/user-guide/usbx-events/image48.png)    | **Odczyt magazynu klasy urządzeń** *(ux_device_class_storage_read)* |
| ![Ikona pojemności Odczytaj magazyn klasy urządzeń](./media/user-guide/usbx-events/image49.png)    | **Pojemność odczytu magazynu klasy urządzeń** *(ux_device_class_storage_read_capacity)* |
| ![Ikona możliwości odczytywania formatu magazynu klasy urządzeń](./media/user-guide/usbx-events/image50.png)    | **Pojemność formatu odczytu magazynu klasy urządzeń** *(ux_device_class_storage_read_format_capacity)* |
| ![Ikona odczytywania SPISu klasy urządzeń](./media/user-guide/usbx-events/image51.png)    | **Magazyn klasy urządzeń odczytywanie spisu treści** *(ux_device_class_storage_read_toc)* |
| ![Ikona wykrywania żądania magazynu klasy urządzeń](./media/user-guide/usbx-events/image52.png)    | **Wykrywanie żądania magazynu klasy urządzeń** *(ux_device_class_storage_request_sense)* |
| ![Ikona zatrzymania uruchamiania magazynu klasy urządzeń](./media/user-guide/usbx-events/image53.png)    | **Zatrzymanie uruchamiania magazynu klasy urządzeń** *(ux_device_class_storage_start_stop)* |
| ![Ikona gotowego testu magazynu klasy urządzeń](./media/user-guide/usbx-events/image54.png)    | **Gotowy Test magazynu klasy urządzeń** *(ux_device_class_storage_test_ready)* |
| ![Ikona weryfikacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image55.png)    | **Weryfikacja magazynu klasy urządzeń** *(ux_device_class_storage_verify)* |
| ![Ikona zapisu magazynu klasy urządzeń](./media/user-guide/usbx-events/image56.png)    | **Zapis magazynu klasy urządzeń** *(ux_device_class_storage_write)* |
| ![Ikona pobierania alternatywnego ustawienia stosu urządzeń](./media/user-guide/usbx-events/image57.png)    | **Pobieranie alternatywnego ustawienia stosu urządzeń** *(ux_device_stack_alternate_setting_get)* |
| ![Ikona zestawu ustawień alternatywnego stosu urządzeń](./media/user-guide/usbx-events/image58.png)    | **Zestaw ustawień alternatywnego stosu urządzeń** *(ux_device_stack_alternate_setting_set)* |
| ![Ikona rejestru klasy stosu urządzeń](./media/user-guide/usbx-events/image59.png)    | **Rejestr klas stosu urządzeń** *(ux_device_stack_class_register)* |
| ![Ikona czyszczenia funkcji dla stosu urządzeń](./media/user-guide/usbx-events/image60.png)    | **Funkcja czyszczenia stosu urządzeń** *(ux_device_stack_clear_feature)* |
| ![Ikona pobierania konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image61.png)    | **Pobieranie konfiguracji stosu urządzeń** *(ux_device_stack_configuration_get)* |
| ![Ikona zestawu konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image62.png)    | **Zestaw konfiguracyjny stosu urządzeń** *(ux_device_stack_configuration_set)* |
| ![Ikona połączenia z stosem urządzeń](./media/user-guide/usbx-events/image63.png)    | **Łączenie stosu urządzeń** *(ux_device_stack_connect)* |
| ![Ikona wysyłania deskryptora stosu urządzeń](./media/user-guide/usbx-events/image64.png)    | **Wysyłanie deskryptora stosu urządzeń** *(ux_device_stack_descriptor_send)* |
| ![Ikona rozłączania stosu urządzeń](./media/user-guide/usbx-events/image65.png)    | **Rozłączenie stosu urządzeń** *(ux_device_stack_disconnect)* |
| ![Ikona miejsca do punktu końcowego stosu urządzeń](./media/user-guide/usbx-events/image66.png)    | **Kabina punktu końcowego stosu urządzeń** *(ux_device_stack_endpoint_stall)* |
| ![Ikona stanu pobierania stosu urządzeń](./media/user-guide/usbx-events/image67.png)    | **Pobieranie stanu stosu urządzeń** *(ux_device_stack_get_status)* |
| ![Ikona wznawiania hosta stosu urządzeń](./media/user-guide/usbx-events/image68.png)    | **Wznawianie hosta stosu urządzeń** *(ux_device_stack_host_wakeup)* |
| ![Ikona inicjowania stosu urządzeń](./media/user-guide/usbx-events/image69.png)    | **Inicjowanie stosu urządzeń** *(ux_device_stack_initialize)* |
| ![Ikona usuwania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image70.png)    | **Usuwanie interfejsu stosu urządzeń** *(ux_device_stack_interface_delete)* |
| ![Ikona pobierania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image71.png)    | **Pobieranie interfejsu stosu urządzeń** *(ux_device_stack_interface_get)* |
| ![Ikona zestawu interfejsów stosu urządzeń](./media/user-guide/usbx-events/image72.png)    | **Zestaw interfejsów stosu urządzeń** *(ux_device_stack_interface_set)* |
| ![Ikona funkcji zestawu stosu urządzeń](./media/user-guide/usbx-events/image73.png)    | **Funkcja zestawu stosu urządzeń** *(ux_device_stack_set_feature)* |
| ![Ikona przerwania transferu stosu urządzeń](./media/user-guide/usbx-events/image74.png)    | **Przerwanie transferu stosu urządzeń** *(ux_device_stack_transfer_abort)* |
| ![* Ikona przetransferowania stosu urządzeń wszystkie żądanie przerwania](./media/user-guide/usbx-events/image75.png)    | **Przerwanie transferu wszystkich żądań przez stos urządzeń** *(ux_device_stack_transfer_all_request_abort)* |
| ![Ikona żądania transferu stosu urządzeń](./media/user-guide/usbx-events/image76.png)    | **Żądanie transferu stosu urządzeń** *(ux_device_stack_transfer_request)* |
| ![Ikona ASIX aktywowania klasy hosta](./media/user-guide/usbx-events/image77.png)    | **ASIX Aktywuj klasy hosta** *(ux_host_class_asix_activate)* |
| ![Ikona dezaktywowania klasy hosta ASIX](./media/user-guide/usbx-events/image78.png)    | **ASIX dezaktywować klasy hosta** *(ux_host_class_asix_deactivate)* |
| ![Ikona powiadomienia o przerwaniu ASIX klasy hosta](./media/user-guide/usbx-events/image79.png)    | **ASIX — powiadomienie o przerwaniu klasy hosta** *(ux_host_class_asix_interrupt_notification)* |
| ![Ikona odczytu ASIX klasy hosta](./media/user-guide/usbx-events/image80.png)    | **ASIX odczytać klasy hosta** *(ux_host_class_asix_read)* |
| ![Ikona zapisu ASIX klasy hosta](./media/user-guide/usbx-events/image81.png)    | **ASIX zapisu klasy hosta** *(ux_host_class_asix_write)* |
| ![Ikona aktywacji dźwięku klasy hosta](./media/user-guide/usbx-events/image82.png)    | **Aktywacja audio klasy hosta** *(ux_host_class_audio_activate)* |
| ![Ikona pobierania wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image83.png)    | **Pobieranie wartości kontrolki audio klasy hosta** *(ux_host_class_audio_control_value_get)* |
| ![Ikona zestawu wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image84.png)    | **Zestaw wartości kontrolki audio klasy hosta** *(ux_host_class_audio_control_value_set)* |
| ![Ikona dezaktywacji audio klasy hosta](./media/user-guide/usbx-events/image85.png)    | **Dezaktywacja audio klasy hosta** *(ux_host_class_audio_deactivate)* |
| ![Ikona odczytu audio klasy hosta](./media/user-guide/usbx-events/image86.png)    | **Odczytaj audio klasy hosta** *(ux_host_class_audio_read)* |
| ![Ikona pobierania próbkowania audio klasy hosta](./media/user-guide/usbx-events/image87.png)    | Pobieranie **próbkowania strumieniowego audio klasy hosta** *(ux_host_class_audio_streaming_sampling_get)* |
| ![Ikona zestawu próbkowania przesyłania strumieniowego audio klasy hosta](./media/user-guide/usbx-events/image88.png)    | **Zestaw próbkowania przesyłania strumieniowego audio klasy hosta** *(ux_host_class_audio_streaming_sampling_set)* |
| ![Ikona zapisu audio klasy hosta](./media/user-guide/usbx-events/image89.png)    | **Zapis audio klasy hosta** *(ux_host_class_audio_write)* |
| ![Klasa hosta C D C A C M ikona aktywacji](./media/user-guide/usbx-events/image90.png)    | **Klasa hosta Przeprowadź aktywację ACM** *(ux_host_class_cdc_acm_activate)* |
| ![Klasa hosta C D C A C M ikona dezaktywowania](./media/user-guide/usbx-events/image91.png)    | **Klasa hosta — dezaktywowanie ACM** *(ux_host_class_cdc_acm_deactivate)* |
| ![Klasa hosta C D C A c M I O C T L na ikonie potoku](./media/user-guide/usbx-events/image92.png)    | **Klasa hosta — przerwanie operacji IOCTL w potoku** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)* |
| ![Klasa hosta C D C A c M I O c T L ikona przerwania](./media/user-guide/usbx-events/image93.png)    | **Klasa hosta Przerzucanie** danych funkcji IOCTL dla operacji przechwytywania *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)* |
| ![Klasa hosta C D C A c M I O C T L Pobierz ikonę stanu urządzenia](./media/user-guide/usbx-events/image94.png)    | **Klasa hosta przechwytywania żądania IOCTL pobieranie stanu urządzenia** *(ux_host_class_cdc_acm_ioctl_get_device_status)* |
| ![Klasa hosta C D C A c M I O C T L ikona Uzyskaj kodowanie wiersza](./media/user-guide/usbx-events/image95.png)    | **Klasa hosta przechwytywania operacji IOCTL Get line kodowania** *(ux_host_class_cdc_acm_ioctl_get_line_coding)* |
| ![Klasa hosta C D C A c M I O c T L ikona wywołania zwrotnego powiadomienia](./media/user-guide/usbx-events/image96.png)    | **Wywołanie zwrotne powiadomień IOCTL klasy hosta** *(ux_host_class_cdc_acm_ioctl_notification_callback)* |
| ![Klasa hosta C D C A c M I O C T L ikona przerwania wysyłania](./media/user-guide/usbx-events/image97.png)    | **Klasa hosta — przerwanie wysyłania żądania IOCTL** *(ux_host_class_cdc_acm_ioctl_send_break)* |
| ![Klasa hosta C D C A c M I O c T L ikona kodowania wierszy](./media/user-guide/usbx-events/image98.png)    | **Klasa hosta — kodowanie liniowe zestawu IOCTL ACM** *(ux_host_class_cdc_acm_ioctl_set_line_coding)* |
| ![Klasa hosta C D C A c M I O C T L ikona stanu wiersza](./media/user-guide/usbx-events/image99.png)    | **Klasa hosta: stan wiersza zestawu IOCTL ACM** *(ux_host_class_cdc_acm_ioctl_set_line_state)* |
| ![Klasa hosta C D C A C M ikona odczytu](./media/user-guide/usbx-events/image100.png)    | **Klasa hosta przechwytywania danych ACM** *(ux_host_class_cdc_acm_read)* |
| ![Klasa hosta C D C A p M — ikona startowa przyjęcia](./media/user-guide/usbx-events/image101.png)    | **Rozpoczęcie odbioru ACM klasy hosta** *(ux_host_class_cdc_acm_reception_start)* |
| ![Klasa hosta C D C, ikona zatrzymania odbierania C M](./media/user-guide/usbx-events/image102.png)    | **Klasa hosta** przełączać do przechwytywania Acm *(ux_host_class_cdc_acm_reception_stop)* |
| ![Klasa hosta C D C A C M ikona zapisu](./media/user-guide/usbx-events/image103.png)    | **Klasa hosta** przeprzechwytywanie do Acm *(ux_host_class_cdc_acm_write)* |
| ![Ikona Dpump aktywowania klasy hosta](./media/user-guide/usbx-events/image104.png)    | **Dpump Aktywuj klasy hosta** *(ux_host_class_dpump_activate)* |
| ![Ikona dezaktywowania klasy hosta Dpump](./media/user-guide/usbx-events/image105.png)    | **Dpump dezaktywować klasy hosta** *(ux_host_class_dpump_deactivate)* |
| ![Ikona odczytu Dpump klasy hosta](./media/user-guide/usbx-events/image106.png)    | **Dpump odczytać klasy hosta** *(ux_host_class_dpump_read)* |
| ![Ikona zapisu Dpump klasy hosta](./media/user-guide/usbx-events/image107.png)    | **Dpump zapisu klasy hosta** *(ux_host_class_dpump_write)* |
| ![Ikona aktywacji klasy hosta HID](./media/user-guide/usbx-events/image108.png)    | **Aktywacja klasy hosta HID** *(ux_host_class_hid_activate)* |
| ![Ikona rejestracji klienta HID klasy hosta](./media/user-guide/usbx-events/image109.png)    | **Rejestr klienta HID klasy hosta** *(ux_host_class_hid_client_register)* |
| ![Ikona dezaktywacji klasy hosta HID](./media/user-guide/usbx-events/image110.png)    | **Dezaktywowanie klasy hosta HID** *(ux_host_class_hid_deactivate)* |
| ![Ikona uzyskiwania bezczynności HID klasy hosta](./media/user-guide/usbx-events/image111.png)    | **Pobieranie z trybu bezczynności HID klasy hosta** *(ux_host_class_hid_idle_get)* |
| ![Ikona zestawu bezczynności HID klasy hosta](./media/user-guide/usbx-events/image112.png)    | **Zestaw bezczynny HID klasy hosta** *(ux_host_class_hid_idle_set)* |
| ![Ikona aktywacji klasy hosta HID](./media/user-guide/usbx-events/image113.png)    | **Aktywuj klasy hosta klawiatury HID** *(ux_host_class_hid_keyboard_activate)* |
| ![Ikona dezaktywacji klawiatury HID klasy hosta](./media/user-guide/usbx-events/image114.png)    | **Dezaktywacja klasy hosta klawiatury HID** *(ux_host_class_hid_keyboard_deactivate)* |
| ![Ikona aktywacji kursora myszy klasy hosta HID](./media/user-guide/usbx-events/image115.png)    | **Aktywacja myszy klasy hosta HID** *(ux_host_class_hid_mouse_activate)* |
| ![Ikona dezaktywacji myszy klasy hosta HID](./media/user-guide/usbx-events/image116.png)    | **Dezaktywacja myszy klasy hosta** *(ux_host_class_hid_mouse_deactivate)* |
| ![Ikona aktywacji zdalnej kontroli HID klasy hosta](./media/user-guide/usbx-events/image117.png)    | **Aktywacja zdalnego sterowania HID klasy hosta** *(ux_host_class_hid_remote_control_activate)* |
| ![Ikona dezaktywowania zdalnego sterowania kontrolką klasy hosta](./media/user-guide/usbx-events/image118.png)    | **Dezaktywacja zdalnego sterowania HID klasy hosta** *(ux_host_class_hid_remote_control_deactivate)* |
| ![Ikona pobierania raportu HID klasy hosta](./media/user-guide/usbx-events/image119.png)    | **Pobieranie raportu HID klasy hosta** *(ux_host_class_hid_report_get)* |
| ![Ikona zestawu raportów HID klasy hosta](./media/user-guide/usbx-events/image120.png)    | **Zestaw raportów HID klasy hosta** *(ux_host_class_hid_report_set)* |
| ![Ikona aktywowania centrum klasy hosta](./media/user-guide/usbx-events/image121.png)    | **Aktywowanie centrum klasy hosta** *(ux_host_class_hub_activate)* |
| ![Ikona wykrywania zmian centrum klasy hosta](./media/user-guide/usbx-events/image122.png)    | **Wykrywanie zmian centrum klasy hosta** *(ux_host_class_hub_change_detect)* |
| ![* Ikona dezaktywacji centrum klasy hosta](./media/user-guide/usbx-events/image123.png)    | **Dezaktywacja centrum klasy hosta** *(ux_host_class_hub_deactivate)* |
| ![Ikona procesu połączenia zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image124.png)    | **Proces połączenia zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_connection_process)* |
| ![Ikona włączenia procesu zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image125.png)    | **Proces włączania zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_enable_process)* |
| ![Ikona hosta zmień port koncentratora na bieżący proces](./media/user-guide/usbx-events/image126.png)    | **Zmiana portu centrum klasy hosta na bieżący proces** *(ux_host_class_hub_port_change_over_current_process)* |
| ![Ikona procesu resetowania zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image127.png)    | **Proces resetowania zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_reset_process)* |
| ![Ikona procesu wstrzymania zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image128.png)    | **Proces wstrzymywania zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_suspend_process)* |
| ![Ikona Pima aktywowania klasy hosta](./media/user-guide/usbx-events/image129.png)    | **Pima Aktywuj klasy hosta** *(ux_host_class_prima_activate)* |
| ![Ikona dezaktywowania klasy hosta Pima](./media/user-guide/usbx-events/image130.png)    | **Pima dezaktywować klasy hosta** *(ux_host_class_pima_deactivate)* |
| ![Ikona uzyskiwania informacji o urządzeniu klasy hosta Pima](./media/user-guide/usbx-events/image131.png)    | **Pobieranie informacji o urządzeniu klasy hosta Pima** *(ux_host_class_pima_device_info_get)* |
| ![Ikona resetowania urządzenia Pima klasy hosta](./media/user-guide/usbx-events/image132.png)    | **Klasa hosta Pima Resetowanie urządzenia** *(ux_host_class_pima_device_reset)* |
| ![Ikona powiadomienia Pima klasy hosta](./media/user-guide/usbx-events/image133.png)    | **Pima — powiadomienie o klasie hosta** *(ux_host_class_pima_notification)* |
| ![Ikona pobierania obiektów Pima klasy hosta](./media/user-guide/usbx-events/image134.png)    | **Pobieranie obiektów Number Pima klasy hosta** *(ux_host_class_pima_num_objects_get)* |
| ![Ikona zamykania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image135.png)    | **Zamknięto obiekt Pima klasy hosta** *(ux_host_class_pima_object_close)* |
| ![Ikona kopiowania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image136.png)    | **Kopia obiektu Pima klasy hosta** *(ux_host_class_pima_object_copy)* |
| ![Ikona usuwania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image137.png)    | **Usuwanie obiektu Pima klasy hosta** *(ux_host_class_pima_object_delete)* |
| ![Ikona pobierania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image138.png)    | **Pobieranie obiektu Pima klasy hosta** *(ux_host_class_pima_object_get)* |
| ![Ikona uzyskiwania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image139.png)    | **Pobieranie informacji o obiekcie Pima klasy hosta** *(ux_host_class_pima_object_info_get)* |
| ![Ikona wysyłania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image140.png)    | **Wysyłanie informacji o obiekcie Pima klasy hosta** *(ux_host_class_pima_object_info_send)* |
| ![Ikona przenoszenia obiektu Pima klasy hosta](./media/user-guide/usbx-events/image141.png)    | **Przeniesienie obiektu Pima klasy hosta** *(ux_host_class_pima_object_move)* |
| ![Ikona wysyłania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image142.png)    | **Wysyłanie obiektu Pima klasy hosta** *(ux_host_class_pima_object_send)* |
| ![Ikona przerwania transferu obiektu klasy hosta Pima](./media/user-guide/usbx-events/image143.png)    | **Przerwanie transferu obiektu Pima klasy hosta** *(ux_host_class_object_transfer_abort)* |
| ![Ikona odczytu Pima klasy hosta](./media/user-guide/usbx-events/image144.png)    | **Pima odczytać klasy hosta** *(ux_host_class_pima_read)* |
| ![Ikona anulowania żądania Pima klasy hosta](./media/user-guide/usbx-events/image145.png)    | **Żądanie anulowania klasy hosta Pima** *(ux_host_class_pima_request_cancel)* |
| ![Ikona zamykania sesji Pima dla klasy hosta](./media/user-guide/usbx-events/image146.png)    | **Zamknięcie sesji Pima** *(Ux_host_class_pima_session_close)* klasy hosta |
| ![Ikona Otwórz sesję Pima sesji hosta](./media/user-guide/usbx-events/image147.png)    | **Pima sesji hosta** *(ux_host_class_pima_session_open)* |
| ![Ikona pobierania identyfikatorów magazynu Pima klasy hosta](./media/user-guide/usbx-events/image148.png)    | **Pobieranie identyfikatorów magazynu Pima klasy hosta** *(ux_host_class_pima_storage_ids_get)* |
| ![Ikona pobierania informacji o magazynie Pima klasy hosta](./media/user-guide/usbx-events/image149.png)    | **Pobieranie informacji o magazynie Pima klasy hosta** *(ux_host_class_pima_storage_info_get)* |
| ![Ikona pobierania Pima klasy hosta](./media/user-guide/usbx-events/image150.png)    | **Pobieranie klasy hosta Pima kciuka** *(ux_host_class_pima_thumb_get)* |
| ![Ikona zapisu Pima klasy hosta](./media/user-guide/usbx-events/image151.png)    | **Pima zapisu klasy hosta** *(ux_host_class_pima_write)* |
| ![Ikona aktywowania drukarki klasy hosta](./media/user-guide/usbx-events/image152.png)    | **Aktywuj drukarkę klasy hosta** *(ux_host_class_printer_activate)* |
| ![Ikona dezaktywacji drukarki klasy hosta](./media/user-guide/usbx-events/image153.png)    | **Dezaktywacja drukarki klasy hosta** *(ux_host_class_printer_deactivate)* |
| ![Ikona pobierania nazwy drukarki klasy hosta](./media/user-guide/usbx-events/image154.png)    | **Pobierz nazwę drukarki klasy hosta** *(ux_host_class_printer_name_get)* |
| ![Ikona odczytu drukarki klasy hosta](./media/user-guide/usbx-events/image155.png)    |  **Odczytaj drukarkę klasy hosta** *(ux_host_class_printer_read)* |
| ![Ikona resetowania nietrwałego drukarki klasy hosta](./media/user-guide/usbx-events/image156.png)    | **Nietrwałe Resetowanie drukarki klasy hosta** *(ux_host_class_printer_soft_reset)* |
| ![Ikona pobierania stanu drukarki klasy hosta](./media/user-guide/usbx-events/image157.png)    | **Pobieranie stanu drukarki klasy hosta** *(ux_host_class_printer_status_get)* |
| ![Ikona zapisu drukarki klasy hosta](./media/user-guide/usbx-events/image158.png)    | **Zapis drukarki klasy hosta** *(ux_host_class_printer_write)* |
| ![Ikona mnóstwo aktywowania klasy hosta](./media/user-guide/usbx-events/image159.png)    | **Mnóstwo Aktywuj klasy hosta** *(ux_host_class_prolific_activate)* |
| ![Ikona dezaktywowania klasy hosta mnóstwo](./media/user-guide/usbx-events/image160.png)    | **Mnóstwo dezaktywować klasy hosta** *(ux_host_class_prolific_deactivate)* |
| ![Ikona potoku mnóstwo I O przerwanie klasy hosta](./media/user-guide/usbx-events/image161.png)    | **Przerwano mnóstwo operacji IOCTL klasy hosta w potoku** *(ux_host_class_prolific_ioctl_abort_in_pipe)* |
| ![Mnóstwo klasy hosta — ikona przerwania rozgałęzienia I O C T L](./media/user-guide/usbx-events/image162.png)    | **Klasa hosta mnóstwo IOCTL przerywanie potoku** *(ux_host_class_prolific_ioctl_abort_out_pipe)* |
| ![Mnóstwo klasy hosta — ikona stanu urządzenia I O C T L](./media/user-guide/usbx-events/image163.png)    | **Klasa hosta mnóstwo IOCTL pobieranie stanu urządzenia** *(ux_host_class_prolific_ioctl_get_device_status)* |
| ![Ikona "Pobierz kodowanie wiersza" klasy hosta mnóstwo I O C T L](./media/user-guide/usbx-events/image164.png)    | **Klasa hosta mnóstwo IOCTL pobieranie kodu** kreskowego *(ux_host_class_prolific_ioctl_get_line_coding)* |
| ![Ikona przeczyszczania klasy hosta mnóstwo I O C T L](./media/user-guide/usbx-events/image165.png)    | **Mnóstwo — przeczyszczanie klasy hosta** *(ux_host_class_prolific_ioctl_purge)* |
| ![Mnóstwo klasy hosta — ikona zmiany stanu urządzenia I O C](./media/user-guide/usbx-events/image166.png)    | **Zmiana stanu urządzenia raportu IOCTL klasy hosta mnóstwo** *(ux_host_class_prolific_ioctl_report_device_status_change)* |
| ![Mnóstwo klasy hosta — ikona przerwania wysyłania I O T L](./media/user-guide/usbx-events/image167.png)    | **Mnóstwo: przerwanie wysyłania elementu IOCTL klasy hosta** *(ux_host_class_prolific_ioctl_send_break)* |
| ![Mnóstwo klasy hosta — ikona kodowania linii I O C T L](./media/user-guide/usbx-events/image168.png)    | **Kodowanie liniowe zestawu poleceń IOCTL klasy hosta mnóstwo** *(ux_host_class_prolific_ioctl_set_line_coding)* |
| ![Mnóstwo klasy hosta — ikona stanu wiersza I O C T L](./media/user-guide/usbx-events/image169.png)    | **Stan wiersza mnóstwo zestawu IOCTL klasy hosta** *(ux_host_class_prolific_ioctl_set_line_state)* |
| ![Ikona odczytu mnóstwo klasy hosta](./media/user-guide/usbx-events/image170.png)    | **Mnóstwo odczytać klasy hosta** *(ux_host_class_prolific_read)* |
| ![Ikona startowa odbioru mnóstwo klasy hosta](./media/user-guide/usbx-events/image171.png)    | **Rozpoczęcie odbioru mnóstwo klasy hosta** *(ux_host_class_prolific_reception_start)* |
| ![Ikona zatrzymania odbierania mnóstwo klasy hosta](./media/user-guide/usbx-events/image172.png)    | **Zatrzymanie odbierania mnóstwo klasy hosta** *(ux_host_class_prolific_reception_stop)* |
| ![Ikona zapisu mnóstwo klasy hosta](./media/user-guide/usbx-events/image173.png)    | **Mnóstwo zapisu klasy hosta** *(ux_host_class_prolific_write)* |
| ![Ikona aktywowania magazynu klasy hosta](./media/user-guide/usbx-events/image174.png)    | **Aktywuj magazyn klas hosta** *(ux_host_class_storage_activate)* |
| ![Ikona dezaktywacji magazynu klasy hosta](./media/user-guide/usbx-events/image175.png)    | **Dezaktywacja magazynu klasy hosta** (*ux_host_class_storage_deactivate)* |
| ![Ikona pobierania pojemności nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image176.png)    | **Pobieranie pojemności nośnika magazynu klasy hosta** *(ux_host_class_storage_media_capacity_get)* |
| ![Ikona pobierania pojemności formatu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image177.png)    | **Pobieranie pojemności formatu nośnika magazynu klasy hosta** *(ux_host_class_storage_media_format_capacity_get)* |
| ![Ikona instalacji nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image178.png)    | **Instalacja nośnika magazynu klasy hosta** (ux_host_class_storage_media_mount) * |
| ![Ikona otwierania nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image179.png)    | **Otwórz nośnik magazynu klasy hosta** *(ux_host_class_storage_media_open)* |
| ![Ikona odczytu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image180.png)    | **Odczyt nośnika magazynu klasy hosta** *(ux_host_class_storage_media_read)* |
| ![Ikona zapisu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image181.png)    | **Zapis nośnika magazynu klasy hosta** *(ux_host_class_storage_media_write)* |
| ![Ikona wykrywania żądań magazynu klasy hosta](./media/user-guide/usbx-events/image182.png)    | **Sens żądania magazynu klasy hosta** *(ux_host_class_storage_request_sense)* |
| ![Ikona zatrzymania uruchamiania magazynu klasy hosta](./media/user-guide/usbx-events/image183.png)    | **Zatrzymanie uruchamiania magazynu klasy hosta** *(ux_host_class_storage_start_stop)* |
| ![Ikona testowania gotowej jednostki magazynu klasy hosta](./media/user-guide/usbx-events/image184.png)    | **Gotowy test jednostki magazynu klasy hosta** *(ux_host_class_storage_activate)* |
| ![Ikona tworzenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image185.png)    | **Tworzenie wystąpienia klasy stosu hosta** *(ux_host_stack_class_instance_create)* |
| ![Ikona niszczenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image186.png)    | **Niszczenie wystąpienia klasy stosu hosta** *(ux_host_stack_class_instance_destroy)* |
| ![Ikona usuwania konfiguracji stosu hosta](./media/user-guide/usbx-events/image187.png)    | **Usuwanie konfiguracji stosu hosta** *(ux_host_stack_configuration_delete)* |
| ![Ikona wyliczenia konfiguracji stosu hosta](./media/user-guide/usbx-events/image188.png)    | **Wyliczenie konfiguracji stosu hosta** *(ux_host_stack_configuration_enumerate)* |
| ![Ikona tworzenia wystąpienia konfiguracji stosu hosta](./media/user-guide/usbx-events/image189.png)    | **Tworzenie wystąpienia konfiguracji stosu hosta** *(ux_host_stack_configuration_instance_create)* |
| ![Ikona usuwania wystąpienia konfiguracji stosu hosta](./media/user-guide/usbx-events/image190.png)    | **Usuwanie wystąpienia konfiguracji stosu hosta** *(ux_host_stack_configuration_instance_delete)* |
| ![Ikona zestawu konfiguracji stosu hosta](./media/user-guide/usbx-events/image191.png)    | **Zestaw konfiguracyjny stosu hosta** *(ux_host_stack_configuration_set)* |
| ![Ikona zestawu adresów urządzeń stosu hosta](./media/user-guide/usbx-events/image192.png)    | **Zestaw adresów urządzeń stosu hosta** *(ux_host_stack_device_set)* |
| ![Ikona pobierania konfiguracji urządzenia stosu hosta](./media/user-guide/usbx-events/image193.png)    | **Pobieranie konfiguracji urządzenia stosu hosta** *(ux_host_stack_device_configuration_get)* |
| ![Ikona wybierania konfiguracji urządzenia stosu hosta](./media/user-guide/usbx-events/image194.png)    | **Wybór konfiguracji urządzenia stosu hosta** *(ux_host_stack_device_configuration_select)* |
| ![Ikona odczytu deskryptora urządzenia stosu hosta](./media/user-guide/usbx-events/image195.png)    | **Odczyt deskryptora urządzenia stosu hosta** *(ux_host_stack_device_descriptor_read)* |
| ![Ikona pobierania urządzenia stosu hosta](./media/user-guide/usbx-events/image196.png)    | **Pobieranie urządzenia stosu hosta** (ux_host_stack_device_get) |
| ![Ikona usuwania urządzenia stosu hosta](./media/user-guide/usbx-events/image197.png)    | **Usuwanie urządzenia stosu hosta** (ux_host_stack_device_get) |
| ![Ikona bezpłatnego zasobu urządzenia stosu hosta](./media/user-guide/usbx-events/image198.png)    | **Bezpłatny zasób urządzenia stosu hosta** (ux_host_stack_device_resource_free) |
| ![Ikona tworzenia wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image199.png)    | **Tworzenie wystąpienia punktu końcowego stosu hosta** (ux_host_stack_endpoint_instance_create) |
| ![Ikona usuwania wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image200.png)    | **Usuwanie wystąpienia punktu końcowego stosu hosta** (ux_host_stack_endpoint_instance_delete) |
| ![Ikona resetowania punktu końcowego stosu hosta](./media/user-guide/usbx-events/image201.png)    | **Resetowanie punktu końcowego stosu hosta** (ux_host_stack_endpoint_reset) |
| ![Ikona przerwania transferu punktu końcowego stosu hosta](./media/user-guide/usbx-events/image202.png)    | **Przerwanie transferu punktu końcowego stosu hosta** (ux_host_stack_endpoint_transfer_abort) |
| ![Ikona rejestru kontrolera hosta stosu hosta](./media/user-guide/usbx-events/image203.png)    | **Rejestr kontrolera hosta stosu hosta** *(ux_host_stack_hcd_register)* |
| ![Ikona inicjowania stosu hosta](./media/user-guide/usbx-events/image204.png)    | **Inicjowanie stosu hosta** *(ux_host_stack_initialize)* |
| ![Ikona pobierania punktu końcowego interfejsu stosu hosta](./media/user-guide/usbx-events/image205.png)    | **Pobieranie punktu końcowego interfejsu stosu hosta** *(ux_host_stack_interface_endpoint_get)* |
| ![Ikona tworzenia wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image206.png)    | **Tworzenie wystąpienia interfejsu stosu hosta** *(ux_host_stack_interface_instance_create)* |
| ![Ikona usuwania wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image207.png)    | **Usuwanie wystąpienia interfejsu stosu hosta** *(ux_host_stack_interface_instance_delete)* |
| ![Ikona zestawu interfejsów stosu hosta](./media/user-guide/usbx-events/image208.png)    | **Zestaw interfejsów stosu hosta** *(ux_host_stack_interface_set)* |
| ![Ikona wybierania ustawienia interfejsu stosu hosta](./media/user-guide/usbx-events/image209.png)    | **Wybór ustawienia interfejsu stosu hosta** *(ux_host_stack_interface_setting_select)* |
| ![Ikona tworzenia nowej konfiguracji stosu hosta](./media/user-guide/usbx-events/image210.png)    | **Tworzenie nowej konfiguracji stosu hosta** *(ux_host_stack_new_configuration_create)* |
| ![Ikona tworzenia nowego urządzenia dla stosu hosta](./media/user-guide/usbx-events/image211.png)    | **Tworzenie nowego urządzenia przez stos hosta** *(ux_host_stack_new_device_create)* |
| ![Ikona tworzenia nowego punktu końcowego stosu hosta](./media/user-guide/usbx-events/image212.png)    | **Utwórz nowy punkt końcowy stosu hosta** *(ux_host_stack_new_endpoint_create)* |
| ![Ikona procesu zmiany głównego centrum w stosie hosta](./media/user-guide/usbx-events/image213.png)    | **Proces zmiany głównego koncentratora stosu hosta** *(ux_host_stack_rh_change_process)* |
| ![Ikona wyodrębniania urządzenia głównego koncentratora stosu hosta](./media/user-guide/usbx-events/image214.png)    | **Wyodrębnianie urządzenia głównego koncentratora stosu hosta** *(ux_host_stack_rh_device_extraction)* |
| ![Ikona wstawienia urządzenia głównego koncentratora stosu hosta](./media/user-guide/usbx-events/image215.png)    | **Wstawianie urządzenia głównego koncentratora stosu hosta** *(ux_host_stack_rh_device_insertion)* |
| ![Ikona żądania transferu stosu hosta](./media/user-guide/usbx-events/image216.png)    | **Żądanie transferu stosu hosta** *(ux_host_stack_transfer_request)* |
| ![Ikona przerwania żądania transferu stosu hosta](./media/user-guide/usbx-events/image217.png)    | **Przerwano żądanie transferu stosu hosta** *(ux_host_stack_transfer_request_abort)* |
| ![Ikona błędu U S B X](./media/user-guide/usbx-events/image218.png)    | **Błąd USBX** *(ux_error)* |

## <a name="event-descriptions"></a>Opisy zdarzeń

Poniższe strony opisują zdarzenia śledzenia USBX.

### <a name="device-class-cdc-activate"></a>Aktywowanie przechwytywania klas urządzeń 

#### <a name="ux_device_class_cdc_activate"></a>ux_device_class_cdc_activate

**Ikona** ![ Ikona urządzenia C D C aktywacja](./media/user-guide/usbx-events/image1.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-cdc-deactivate"></a>Dezaktywacja przechwytywania klasy urządzeń 

#### <a name="ux_device_class_cdc_deactivate"></a>ux_device_class_cdc_deactivate

**Ikona** ![ Ikona klasy urządzenia C D C](./media/user-guide/usbx-events/image2.png)

**Opis**

To zdarzenie przedstawia dezaktywację klasy urządzenia USBX.

Pola informacji 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-cdc-read"></a>Odczyt przechwytywania klasy urządzeń 

#### <a name="ux_device_class_cdc_read"></a>ux_device_class_cdc_read

**Ikona** ![ Ikona Odczytaj klasy urządzeń C D C](./media/user-guide/usbx-events/image3.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="device-class-cdc-write"></a>Zapis przechwytywania danych klasy urządzeń 

#### <a name="ux_device_class_cdc_write"></a>ux_device_class_cdc_write

**Ikona** ![ Ikona urządzenia C D C pisanie](./media/user-guide/usbx-events/image4.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="device-class-dpump-activate"></a>Dpump Aktywuj klasy urządzeń 

#### <a name="ux_device_class_dpump_activate"></a>ux_device_class_dpump_activate

**Ikona** ![ Ikona urządzenia Dpump Activate](./media/user-guide/usbx-events/image5.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX Dpump.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-dpump-deactivate"></a>Dezaktywacja klasy urządzenia Dpump 

#### <a name="ux_device_class_dpump_deactivate"></a>ux_device_class_dpump_deactivate

**Ikona** ![ Ikona dezaktywowania klasy urządzenia Dpump](./media/user-guide/usbx-events/image6.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Dpump.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-dpump-read"></a>Odczyt klasy urządzenia Dpump 

#### <a name="ux_device_class_dpump_read"></a>ux_device_class_dpump_read

**Ikona** ![ Ikona odczytu Dpump klasy urządzeń](./media/user-guide/usbx-events/image7.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu klasy urządzenia USBX Dpump.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: bufor.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="device-class-dpump-write"></a>Dpump zapisu klasy urządzeń 

#### <a name="ux_device_class_dpump_write"></a>ux_device_class_dpump_write

**Ikona** ![ Ikona zapisu Dpump klasy urządzeń](./media/user-guide/usbx-events/image8.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu klasy urządzenia USBX Dpump.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="device-class-hid-activate"></a>Aktywuj klasy urządzenia HID 

#### <a name="ux_device_class_hid_activate"></a>ux_device_class_hid_activate

**Ikona** ![ Ikona klasy urządzenia HID Aktywuj](./media/user-guide/usbx-events/image9.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-hid-deactivate"></a>Dezaktywacja klasy urządzenia HID 

#### <a name="ux_device_class_hid_deactivate"></a>ux_device_class_hid_deactivate

**Ikona** ![ Ikona dezaktywacji klasy urządzenia](./media/user-guide/usbx-events/image10.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-hid-descriptor-send"></a>Wysyłanie deskryptora HID klasy urządzeń 

#### <a name="ux_device_class_hid_descritpor_send"></a>ux_device_class_hid_descritpor_send

**Ikona** ![ Ikona wysyłania deskryptora HID klasy urządzeń](./media/user-guide/usbx-events/image11.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania deskryptora HID klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: typ deskryptora.
- Pole informacji 3: indeks żądania.
- Pole informacji 4: nieużywane.

### <a name="device-class-hid-event-get"></a>Pobieranie zdarzenia HID klasy urządzenia 

#### <a name="ux_device_class_hid_event_get"></a>ux_device_class_hid_event_get

**Ikona** ![ Ikona pobierania zdarzenia HID z klasą urządzeń](./media/user-guide/usbx-events/image12.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania zdarzenia HID klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-hid-event-set"></a>Zestaw zdarzeń HID klasy urządzeń 

#### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

**Ikona** ![ Ikona zestawu zdarzeń HID klasy urządzeń](./media/user-guide/usbx-events/image13.png)

**Opis**

To zdarzenie reprezentuje zestaw zdarzeń HID klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-hid-report-get"></a>Pobieranie raportu HID klasy urządzeń 

#### <a name="ux_device_class_hid_report_get"></a>ux_device_class_hid_report_get

**Ikona** ![ Ikona pobierania raportu HID klasy urządzeń](./media/user-guide/usbx-events/image14.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get raportu HID klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: typ deskryptora.
- Pole informacji 3: indeks żądania.
- Pole informacji 4: nieużywane.

### <a name="device-class-hid-report-set"></a>Zestaw raportów HID klasy urządzeń 

#### <a name="ux_device_class_hid_report_set"></a>ux_device_class_hid_report_set

**Ikona** ![ Ikona zestawu raportów HID klasy urządzeń](./media/user-guide/usbx-events/image15.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu raportów HID klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: typ deskryptora.
- Pole informacji 3: indeks żądania.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-activate"></a>Pima Aktywuj klasy urządzeń

#### <a name="ux_device_class_pima_activate"></a>ux_device_class_pima_activate

**Ikona** ![ Ikona urządzenia Pima Activate](./media/user-guide/usbx-events/image16.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-deactivate"></a>Dezaktywacja klasy urządzenia Pima 

#### <a name="ux_device_class_pima_deactivate"></a>ux_device_class_pima_deactivate

**Ikona** ![ Ikona dezaktywowania klasy urządzenia Pima](./media/user-guide/usbx-events/image17.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-device-info-send"></a>Klasa urządzenia Pima wysyłanie informacji o urządzeniu 

#### <a name="ux_device_class_pima_device_info_send"></a>ux_device_class_pima_device_info_send

**Ikona** ![ Ikona wysyłania informacji o urządzeniu Pima klasy urządzeń](./media/user-guide/usbx-events/image18.png)

**Opis**

To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania informacji o urządzeniu.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.

### <a name="device-class-pima-event-get"></a>Pobieranie zdarzenia Pima klasy urządzeń 

#### <a name="ux_device_class_pima_event_get"></a>ux_device_class_pima_event_get

**Ikona** ![ Ikona pobierania zdarzenia Pima klasy urządzeń](./media/user-guide/usbx-events/image19.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania zdarzenia USBX klasy urządzenia.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: zdarzenie Pima.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-event-set"></a>Zestaw zdarzeń Pima klasy urządzeń 

#### <a name="ux_device_class_pima_event_set"></a>ux_device_class_pima_event_set

**Ikona** ![ Ikona zestawu zdarzeń Pima klasy urządzeń](./media/user-guide/usbx-events/image20.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: zdarzenie Pima.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-object-add"></a>Dodawanie obiektu Pima klasy urządzeń 

#### <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

**Ikona** ![ Ikona dodawania obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image21.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-object-data-get"></a>Pobieranie danych obiektu Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

**Ikona** ![ Ikona uzyskiwania danych obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image22.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-object-data-send"></a>Wysyłanie danych obiektu Pima klasy urządzeń 

#### <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

**Ikona** ![ Ikona wysyłania danych obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image23.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-object-delete"></a>Usuwanie obiektu Pima klasy urządzeń 

#### <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

**Ikona** ![ Ikona usuwania obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image24.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-object-handles-send"></a>Obiekt Pima klasy urządzenia obsługuje wysyłanie 

#### <a name="ux_device_class_pima_object_handles_send"></a>ux_device_class_pima_object_handles_send

**Ikona** ![ Obiekt Pima klasy urządzenia obsługuje ikonę wysyłania](./media/user-guide/usbx-events/image25.png)

**Opis**

To zdarzenie reprezentuje klasę urządzenia USBX Pima obsługuje zdarzenie wysyłania.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: Identyfikator magazynu.
- Pole informacji 3: kod formatu obiektu.
- Pole informacji 4: skojarzenie obiektu.

### <a name="device-class-pima-object-info-get"></a>Pobieranie informacji o obiekcie Pima klasy urządzenia 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ikona** ![ Ikona uzyskiwania informacji o obiekcie Pima klasy urządzeń](./media/user-guide/usbx-events/image26.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get USBX klasy urządzenia Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-object-info-send"></a>Wysyłanie informacji o obiekcie Pima klasy urządzeń 

#### <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

**Ikona** ![ Ikona wysyłania informacji o obiekcie Pima klasy urządzenia](./media/user-guide/usbx-events/image27.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania informacji o obiekcie USBX klasy urządzenia Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-objects-number-send"></a>Klasa urządzenia Pima liczba obiektów do wysłania 

#### <a name="ux_device_class_pima_object_number_send"></a>ux_device_class_pima_object_number_send

**Ikona** ![ Ikona Pima obiektów klasy urządzeń](./media/user-guide/usbx-events/image28.png)

**Opis**

To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania numeru obiektu.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: Identyfikator magazynu.
- Pole informacji 3: kod formatu obiektu.
- Pole informacji 4: obiekt skojarzony.

### <a name="device-class-pima-partial-object-data-get"></a>Klasa urządzenia Pima częściowe dane obiektu Get

#### <a name="ux_device_class_pima_partial_object_data_get"></a>ux_device_class_pima_partial_object_data_get

**Ikona** ![ Ikona Pima części danych obiektu klasy urządzenia](./media/user-guide/usbx-events/image29.png)

**Opis**

To zdarzenie reprezentuje USBX klasy urządzenia Pima częściowe zdarzenie Get Data.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: zażądano przesunięcia.
- Pole informacji 4: Żądana długość.

### <a name="device-class-pima-response-send"></a>Wysyłanie odpowiedzi przez Pima klasy urządzeń 

#### <a name="ux_device_class_pima_response_send"></a>ux_device_class_pima_response_send

**Ikona** ![ Ikona wysyłania odpowiedzi Pima klasy urządzeń](./media/user-guide/usbx-events/image30.png)

**Opis**

To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania odpowiedzi.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: kod odpowiedzi.
- Pole informacji 3: parametr liczby.
- Pole informacji 4: Pima parametr 1.

### <a name="device-class-pima-storage-id-send"></a>Klasa urządzenia Pima — wysyłanie identyfikatora magazynu 

#### <a name="ux_device_class_pima_storage_id_send"></a>ux_device_class_pima_storage_id_send

**Ikona** ![ Ikona wysyłania identyfikatora magazynu Pima klasy urządzeń](./media/user-guide/usbx-events/image31.png)

**Opis**

To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania identyfikatora magazynu.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-pima-storage-info-send"></a>Pima urządzenia — wysyłanie informacji o magazynie 

#### <a name="ux_device_class_pima_storage_info_send"></a>ux_device_class_pima_storage_info_send

**Ikona** ![ Ikona wysyłania informacji o magazynie Pima klasy urządzeń](./media/user-guide/usbx-events/image32.png)

**Opis**

To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania informacji o magazynie.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-rndis-activate"></a>RNDIS Aktywuj klasy urządzeń 

#### <a name="ux_device_class_rndis_activate"></a>ux_device_class_rndis_activate

**Ikona** ![ Ikona urządzenia RNDIS Activate](./media/user-guide/usbx-events/image33.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX RNDIS.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-rndis-deactivate"></a>Dezaktywacja klasy urządzenia RNDIS 

#### <a name="ux_device_class_rndis_deactivate"></a>ux_device_class_rndis_deactivate

**Ikona** ![ Ikona dezaktywowania klasy urządzenia RNDIS](./media/user-guide/usbx-events/image34.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia RNDIS.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-rndis-message-keep-alive"></a>RNDIS aktywność komunikatu o klasie urządzeń 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a>ux_device_class_rndis_msg_keep_alive

**Ikona** ![ Ikona utrzymywania aktywności komunikatu RNDIS na urządzeniu](./media/user-guide/usbx-events/image35.png)

**Opis**

To zdarzenie reprezentuje USBX klasy urządzenia RNDIS zdarzenie Keep Alive.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-rndis-message-query"></a>Zapytanie o komunikat RNDIS klasy urządzeń 

#### <a name="ux_device_class_rndis_msg_keep_query"></a>ux_device_class_rndis_msg_keep_query

**Ikona** ![ Ikona zapytania komunikatu RNDIS klasy urządzeń](./media/user-guide/usbx-events/image36.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia RNDIS.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: RNDIS identyfikatora OID.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-rndis-message-reset"></a>Resetowanie komunikatu klasy urządzenia RNDIS 

#### <a name="ux_device_class_rndis_msg_reset"></a>ux_device_class_rndis_msg_reset

**Ikona** ![ Ikona resetowania komunikatu RNDIS klasy urządzeń](./media/user-guide/usbx-events/image37.png)

**Opis**

To zdarzenie reprezentuje zdarzenie resetowania komunikatu klasy urządzenia USBX RNDIS.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.

### <a name="device-class-rndis-message-set"></a>RNDIS klasy urządzeń — zestaw komunikatów 

#### <a name="ux_device_class_rndis_msg_set"></a>ux_device_class_rndis_msg_set

**Ikona** ![ Ikona zestawu komunikatów RNDIS klasy urządzeń](./media/user-guide/usbx-events/image38.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia RNDIS.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: RNDIS identyfikatora OID.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-rndis-packet-receive"></a>Odbieranie pakietu RNDIS klasy urządzeń 

#### <a name="ux_device_class_rndis_packet_receive"></a>ux_device_class_rndis_packet_receive

**Ikona** ![ Ikona odbierania pakietu RNDIS klasy urządzeń](./media/user-guide/usbx-events/image39.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia RNDIS.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-rndis-packet-transmit"></a>Transmisja pakietów RNDIS klasy urządzeń 

#### <a name="ux_device_class_rndis_packet_transmit"></a>ux_device_class_rndis_packet_transmit

**Ikona** ![ Ikona wysyłania pakietów RNDIS klasy urządzeń](./media/user-guide/usbx-events/image40.png)

**Opis**

To zdarzenie reprezentuje zdarzenie transmisji pakietu USBX klasy urządzenia RNDIS.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-activate"></a>Aktywowanie magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_activate"></a>ux_device_class_storage_activate

**Ikona** ![ Ikona aktywacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image41.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania magazynu klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-deactivate"></a>Dezaktywacja magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_deactivate"></a>ux_device_class_storage_deactivate

**Ikona** ![ Ikona dezaktywacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image42.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji magazynu klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-format"></a>Format magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_format"></a>ux_device_class_storage_format

**Ikona** ![ Ikona formatu magazynu klasy urządzeń](./media/user-guide/usbx-events/image43.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX w formacie magazynu klasy urządzeń.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-inquiry"></a>Zapytanie dotyczące magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_inquiry"></a>ux_device_class_storage_inquiry

**Ikona** ![ Ikona zapytania dotyczącego magazynu klasy urządzeń](./media/user-guide/usbx-events/image44.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapytania dotyczącego magazynu klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-mode-select"></a>Wybór trybu przechowywania klasy urządzeń

#### <a name="ux_device_class_storage_mode_select"></a>ux_device_class_storage_mode_select

**Ikona** ![ Ikona wybierania trybu przechowywania klasy urządzeń](./media/user-guide/usbx-events/image45.png)

**Opis**

To zdarzenie reprezentuje tryb przechowywania klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-mode-sense"></a>Wykrywanie trybu przechowywania klasy urządzeń 

#### <a name="ux_device_class_storage_mode_sense"></a>ux_device_class_storage_mode_sense

**Ikona** ![ Ikona wykrywania trybu przechowywania klasy urządzeń](./media/user-guide/usbx-events/image46.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wykrywania klasy urządzenia USBX.

Pola informacji 

- NFO pole 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-prevent-allow-media-removal"></a>Magazyn klasy urządzeń uniemożliwia usunięcie nośnika 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a>ux_device_class_storage_prevent_allow_media_removal

**Ikona** ![ Nie Zezwalaj na usuwanie nośnika z magazynu klasy urządzeń](./media/user-guide/usbx-events/image47.png)

**Opis**

To zdarzenie reprezentuje magazyn klasy urządzeń USBX zapobieganie zdarzeniu usuwania multimediów.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-read"></a>Odczyt magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_read"></a>ux_device_class_storage_read

**Ikona** ![ Ikona odczytu magazynu klasy urządzeń](./media/user-guide/usbx-events/image48.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu magazynu klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: sektor.
- Pole informacji 4: liczba sektorów.

### <a name="device-class-storage-read-capacity"></a>Pojemność odczytu magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_read_capacity"></a>ux_device_class_storage_read_capacity

**Ikona** ![ Ikona pojemności Odczytaj magazyn klasy urządzeń](./media/user-guide/usbx-events/image49.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pojemności odczytu magazynu klasy urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-read-format-capacity"></a>Pojemność formatu odczytu magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_read_format_capacity"></a>ux_device_class_storage_read_format_capacity

**Ikona** ![ Ikona możliwości odczytywania formatu magazynu klasy urządzeń](./media/user-guide/usbx-events/image50.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pojemności Odczytaj USBX magazynu klasy urządzeń.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-read-toc"></a>Magazyn klasy urządzeń odczytywanie spisu treści 

#### <a name="ux_device_class_storage_read_toc"></a>ux_device_class_storage_read_toc

**Ikona** ![ Ikona odczytywania SPISu klasy urządzeń](./media/user-guide/usbx-events/image51.png)

**Opis**

To zdarzenie reprezentuje zdarzenie TOC Read USBX Storage klasy urządzeń.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-request-sense"></a>Wykrywanie żądania magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_request_sense"></a>ux_device_class_storage_request_sense

**Ikona** ![ Ikona wykrywania żądania magazynu klasy urządzeń](./media/user-guide/usbx-events/image52.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wykrywania żądania magazynu klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: klucz wykrywania.
- Pole informacji 4: kod.

### <a name="device-class-storage-start-stop"></a>Zatrzymanie uruchomienia magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_start_stop"></a>ux_device_class_storage_start_stop

**Ikona** ![ Ikona zatrzymania uruchamiania magazynu klasy urządzeń](./media/user-guide/usbx-events/image53.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zatrzymania uruchomienia magazynu klasy urządzenia USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-test-ready"></a>Gotowy Test magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_test_ready"></a>ux_device_class_storage_test_ready

**Ikona** ![ Ikona gotowego testu magazynu klasy urządzeń](./media/user-guide/usbx-events/image54.png)

**Opis**

To zdarzenie reprezentuje zdarzenie gotowe do testowania magazynu klasy urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-verify"></a>Weryfikacja magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_verify"></a>ux_device_class_storage_verify

**Ikona** ![ Ikona weryfikacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image55.png)

**Opis**

To zdarzenie reprezentuje zdarzenie weryfikacji magazynu klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-class-storage-write"></a>Zapis magazynu klasy urządzeń 

#### <a name="ux_device_class_storage_write"></a>ux_device_class_storage_write

**Ikona** ![ Ikona zapisu magazynu klasy urządzeń](./media/user-guide/usbx-events/image56.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu magazynu klasy urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: numer LUN.
- Pole informacji 3: sektor.
- Pole informacji 4: liczba sektorów.

### <a name="device-stack-alternate-setting-get"></a>Pobieranie alternatywnego ustawienia stosu urządzeń 

#### <a name="ux_device_class_alternate_setting_get"></a>ux_device_class_alternate_setting_get

**Ikona** ![ Ikona pobierania alternatywnego ustawienia stosu urządzeń](./media/user-guide/usbx-events/image57.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania ustawienia alternatywnego stosu urządzeń USBX.

**Pola informacji**

- Pole informacji 1: wartość interfejsu.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-alternate-setting-set"></a>Zestaw ustawień alternatywnego stosu urządzeń 

#### <a name="ux_device_class_alternate_setting_set"></a>ux_device_class_alternate_setting_set

**Ikona** ![ Ikona zestawu ustawień alternatywnego stosu urządzeń](./media/user-guide/usbx-events/image58.png)

**Opis**

To zdarzenie reprezentuje zdarzenie ustawienia alternatywnego ustawienia stosu urządzeń USBX.

**Pola informacji**
- Pole informacji 1: wartość interfejsu.
- Pole informacji 2: wartość ustawienia alternatywnego.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-class-register"></a>Rejestr klas stosu urządzeń 

#### <a name="ux_device_stack_class_register"></a>ux_device_stack_class_register

**Ikona** ![ Ikona rejestru klasy stosu urządzeń](./media/user-guide/usbx-events/image59.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Register klasy stosu urządzeń USBX.

**Pola informacji**

- Pole informacji 1: Nazwa klasy.
- Pole informacji 2: numer interfejsu.
- Pole informacji 3: parametr.
- Pole informacji 4: nieużywane.

### <a name="device-stack-clear-feature"></a>Funkcja czyszczenia stosu urządzeń 

#### <a name="ux_device_stack_clear_feature"></a>ux_device_stack_clear_feature

**Ikona** ![ Ikona czyszczenia funkcji dla stosu urządzeń](./media/user-guide/usbx-events/image60.png)

**Opis**

To zdarzenie reprezentuje zdarzenie funkcji Clear USBX stosu urządzeń.

**Pola informacji**

- Pole informacji 1: typ żądania.
- Pole informacji 2: wartość żądania. Pole informacji 3: indeks żądania.
- Pole informacji 4: nieużywane.

### <a name="device-stack-configuration-get"></a>Pobieranie konfiguracji stosu urządzeń 

#### <a name="ux_device_stack_configuration_get-t"></a>ux_device_stack_configuration_get t

**Ikona** ![ Ikona pobierania konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image61.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania konfiguracji stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wartość konfiguracji.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-configuration-set"></a>Zestaw konfiguracji stosu urządzeń 

#### <a name="ux_device_stack_configuration_set"></a>ux_device_stack_configuration_set

**Ikona** ![ Ikona zestawu konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image62.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu konfiguracji stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wartość konfiguracji.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-connect"></a>Łączenie stosu urządzeń 

#### <a name="ux_device_stack_connect"></a>ux_device_stack_connect

**Ikona** ![ Ikona połączenia z stosem urządzeń](./media/user-guide/usbx-events/image63.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania deskryptora stosu urządzenia USBX.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-descriptor-send"></a>Wysyłanie deskryptora stosu urządzeń 

#### <a name="ux_device_stack_descriptor_send"></a>ux_device_stack_descriptor_send

**Ikona** ![ Ikona wysyłania deskryptora stosu urządzeń](./media/user-guide/usbx-events/image64.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania deskryptora stosu urządzenia USBX.

**Pola informacji**

- Pole informacji 1: typ deskryptora.
- Pole informacji 2: indeks żądania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-disconnect"></a>Rozłączanie stosu urządzeń 

#### <a name="ux_device_stack_disconnect"></a>ux_device_stack_disconnect

**Ikona** ![ Ikona rozłączania stosu urządzeń](./media/user-guide/usbx-events/image65.png)

**Opis**

To zdarzenie reprezentuje zdarzenie rozłączenia stosu urządzenia USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-endpoint-stall"></a>Kabina punktu końcowego stosu urządzeń 

#### <a name="ux_device_stack_endpoint_stall"></a>ux_device_stack_endpoint_stall

**Ikona** ![ Ikona miejsca do punktu końcowego stosu urządzeń](./media/user-guide/usbx-events/image66.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX punktu końcowego stosu urządzeń.

**Pola informacji** 

- Pole informacji 1: punkt końcowy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-get-status"></a>Pobieranie stanu stosu urządzeń 

#### <a name="ux_device_stack_get_status"></a>ux_device_stack_get_status

**Ikona** ![ Ikona stanu pobierania stosu urządzeń](./media/user-guide/usbx-events/image67.png)

**Opis**

To zdarzenie reprezentuje zdarzenie stanu Get USBX stosu urządzeń.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-host-wakeup"></a>Wznawianie hosta stosu urządzeń 

#### <a name="ux_device_stack_host_wakeup"></a>ux_device_stack_host_wakeup

**Ikona** ![ Ikona wznawiania hosta stosu urządzeń](./media/user-guide/usbx-events/image68.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wznowienia hosta stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-initialize"></a>Inicjowanie stosu urządzeń 

#### <a name="ux_device_stack_initialize"></a>ux_device_stack_initialize

**Ikona** ![ Ikona inicjowania stosu urządzeń](./media/user-guide/usbx-events/image69.png)

**Opis**

To zdarzenie reprezentuje zdarzenie inicjowania stosu urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-interface-delete"></a>Usuwanie interfejsu stosu urządzeń 

#### <a name="ux_device_stack_interface_delete"></a>ux_device_stack_interface_delete

**Ikona** ![ Ikona usuwania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image70.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia interfejsu stosu urządzenia USBX.

**Pola informacji**

- Pole informacji 1: interfejs.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-interface-get"></a>Pobieranie interfejsu stosu urządzeń 

#### <a name="ux_device_stack_interface_get"></a>ux_device_stack_interface_get

**Ikona** ![ Ikona pobierania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image71.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get interfejsu stosu urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wartość interfejsu.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-interface-set"></a>Zestaw interfejsów stosu urządzeń 

#### <a name="ux_device_stack_interface_set"></a>ux_device_stack_interface_set

**Ikona** ![ Ikona zestawu interfejsów stosu urządzeń](./media/user-guide/usbx-events/image72.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu interfejsu stosu urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: wartość żądania. Pole informacji 2: indeks żądania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-set-feature"></a>Funkcja zestawu stosu urządzeń 

#### <a name="ux_device_stack_set_feature"></a>ux_device_stack_set_feature

**Ikona** ![ Ikona funkcji zestawu stosu urządzeń](./media/user-guide/usbx-events/image73.png)

**Opis**

To zdarzenie reprezentuje zdarzenie funkcji zestawu stosu urządzeń USBX.

**Pola informacji** 

- Pole informacji 1: wartość żądania. Pole informacji 2: indeks żądania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-transfer-abort"></a>Przerwanie transferu stosu urządzeń 

#### <a name="ux_device_stack_transfer_abort"></a>ux_device_stack_transfer_abort

**Ikona** ![ Ikona przerwania transferu stosu urządzeń](./media/user-guide/usbx-events/image74.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania transferu stosu urządzenia USBX.

**Pola informacji** 

- Pole informacji 1: żądanie transferu.
- Pole informacji 2: kod zakończenia.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-transfer-all-request-abort"></a>Przerwanie transferu wszystkich żądań przez stos urządzeń 

#### <a name="ux_device_stack_transfer_all_request_abort"></a>ux_device_stack_transfer_all_request_abort

**Ikona** ![ Ikona przerwania transferu wszystkich żądań w stosie urządzeń](./media/user-guide/usbx-events/image75.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania transferu wszystkich żądań USBX.

**Pola informacji** 

- Pole informacji 1: punkt końcowy.
- Pole informacji 2: kod zakończenia.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="device-stack-transfer-request"></a>Żądanie transferu stosu urządzeń 

#### <a name="ux_device_stack_transfer_request"></a>ux_device_stack_transfer_request

**Ikona** ![ Ikona żądania transferu stosu urządzeń](./media/user-guide/usbx-events/image76.png)

**Opis**

To zdarzenie reprezentuje zdarzenie żądania transferu stosu urządzenia USBX.

**Pola informacji**

- Pole informacji 1: żądanie transferu.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-asix-activate"></a>ASIX Aktywuj klasy hosta 

#### <a name="ux_host_class_asix_activate"></a>ux_host_class_asix_activate

**Ikona** ![ Ikona ASIX aktywowania klasy hosta](./media/user-guide/usbx-events/image77.png)

**Opis**

To zdarzenie reprezentuje USBX klasy hosta ASIX Aktywuj.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-asix-deactivate"></a>ASIX Dezaktywuj klasy hosta 

#### <a name="ux_host_class_asix_deactivate"></a>ux_host_class_asix_deactivate

**Ikona** ![ Ikona dezaktywowania klasy hosta ASIX](./media/user-guide/usbx-events/image78.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX ASIX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-asix-interrupt-notification"></a>Powiadomienie o przerwaniu ASIX klasy hosta 

#### <a name="ux_host_class_asix_interrupt_notification"></a>ux_host_class_asix_interrupt_notification

**Ikona** ![ Ikona powiadomienia o przerwaniu ASIX klasy hosta](./media/user-guide/usbx-events/image79.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBXa przerwania klasy hosta ASIX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-asix-read"></a>Odczytaj ASIX klasy hosta 

#### <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

**Ikona** ![ Ikona odczytu ASIX klasy hosta](./media/user-guide/usbx-events/image80.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu USBX klasy hosta ASIX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-asix-write"></a>ASIX zapisu klasy hosta 

#### <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

**Ikona** ![ Ikona zapisu ASIX klasy hosta](./media/user-guide/usbx-events/image81.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu USBX klasy hosta ASIX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-audio-activate"></a>Aktywuj klasy hosta audio 

#### <a name="ux_host_class_audio_activate"></a>ux_host_class_audio_activate

**Ikona** ![ Ikona aktywacji dźwięku klasy hosta](./media/user-guide/usbx-events/image82.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania audio klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-audio-control-value-get"></a>Pobieranie wartości kontrolki audio klasy hosta 

#### <a name="ux_host_class_audio_control_value_get"></a>ux_host_class_audio_control_value_get

**Ikona** ![ Ikona pobierania wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image83.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania wartości kontrolki audio klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-audio-control-value-set"></a>Zestaw wartości kontrolki audio klasy hosta 

#### <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

**Ikona** ![ Ikona zestawu wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image84.png)

**Opis**

To zdarzenie przedstawia wewnętrzne zdarzenie przetwarzania odroczonego sterownika we/wy NetX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: formant audio.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-audio-deactivate"></a>Dezaktywacja audio klasy hosta 

#### <a name="ux_host_class_audio_deactivate"></a>ux_host_class_audio_deactivate

**Ikona** ![ Ikona dezaktywacji audio klasy hosta](./media/user-guide/usbx-events/image85.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji audio klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-audio-read"></a>Odczyt klasy hosta audio 

#### <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

**Ikona** ![ Ikona odczytu audio klasy hosta](./media/user-guide/usbx-events/image86.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu audio klasy hosta USBX.

- Pola informacji 
- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-audio-streaming-sampling-get"></a>Pobieranie próbkowania audio klasy hosta 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

**Ikona** ![ Ikona pobierania próbkowania audio klasy hosta](./media/user-guide/usbx-events/image87.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania próbkowania audio klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-audio-streaming-sampling-set"></a>Zestaw próbkowania przesyłania strumieniowego audio klasy hosta 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

**Ikona** ![ Ikona zestawu próbkowania przesyłania strumieniowego audio klasy hosta](./media/user-guide/usbx-events/image88.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu próbkowania audio klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: próbkowanie audio.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-audio-write"></a>Zapis audio klasy hosta 

#### <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

**Ikona** ![ Ikona zapisu audio klasy hosta](./media/user-guide/usbx-events/image89.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu audio klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-activate"></a>Aktywacja ACM klasy hosta 

#### <a name="ux_host_class_cdc_acm_activate"></a>ux_host_class_cdc_acm_activate

**Ikona** ![ Klasa hosta C D C A C M ikona aktywacji](./media/user-guide/usbx-events/image90.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Activate (USBX) klasy hosta przechwytywania.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-deactivate"></a>Klasa hosta przechwytywania danych ACM 

#### <a name="ux_host_class_cdc_acm_deactivate"></a>ux_host_class_cdc_acm_deactivate

**Ikona** ![ Klasa hosta C D C A C M ikona dezaktywowania](./media/user-guide/usbx-events/image91.png)

**Opis**

To zdarzenie reprezentuje USBXą klasę hosta przechwytywania zdarzeń.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a>Klasa hosta — przerywanie operacji IOCTL w potoku 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a>ux_host_class_cdc_acm_ioctl_abort_in_pipe

**Ikona** ![ Klasa hosta C D C A c M I O s T L przerwa w potoku](./media/user-guide/usbx-events/image92.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX przechwytywanie zdarzeń IOCTL w zdarzeniu potoku.

Pola informacji 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a>Klasa hosta Przerzucanie polecenia IOCTL w usłudze ACM przerywanie potoku 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a>ux_host_class_cdc_acm_ioct_abort_out_pipe

**Ikona** ! [[Klasa hosta c D c A c M I o c T L ikona przerwania w potoku](./media/user-guide/usbx-events/image93.png)

**Opis**

To zdarzenie reprezentuje USBX klasy hosta przechwytywania zdarzeń IOCTL przerywanie potoku.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a>Klasa hosta przechwytywania żądania IOCTL pobieranie stanu urządzenia 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a>ux_host_class_cdc_acm_ioctl_get_device_status

**Ikona** ![ Klasa hosta C D C A c M I O C T L Pobierz ikonę stanu urządzenia](./media/user-guide/usbx-events/image94.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX, która umożliwia pobieranie zdarzenia stanu urządzenia.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: stan urządzenia.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a>Klasa hosta przechwytywania operacji IOCTL pobieranie kodowania wierszy 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a>ux_host_class_cdc_acm_ioctl_get_line_coding

**Ikona** ![ Klasa hosta C D C A c M I O C T L ikona Uzyskaj kodowanie wiersza](./media/user-guide/usbx-events/image95.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX przechwytywanie zdarzeń IOCTL pobieranie wiersza zdarzenia.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a>Wywołanie zwrotne powiadomień IOCTL klasy hosta

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a>ux_host_class_cdc_acm_ioctl_notification_callback

**Ikona** ![ Klasa hosta C D C A c M I O c T L ikona wywołania zwrotnego powiadomienia](./media/user-guide/usbx-events/image96.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX zdarzenia wywołania zwrotnego powiadomienia dla operacji IOCTL.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-ioctl-send-break"></a>Klasa hosta przechwytywania przerwania operacji IOCTL 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a>ux_host_class_cdc_acm_ioctl_send_break

**Ikona** ![ Klasa hosta C D C A c M I O C T L ikona przerwania wysyłania](./media/user-guide/usbx-events/image97.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX zdarzenia przerwania wysyłania IOCTL.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a>Klasa hosta przechwytywania operacji IOCTL ustawienia kodowania linii 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a>ux_host_class_cdc_acm_ioctl_set_line_coding

**Ikona** ![ Klasa hosta C D C A c M I O C T L ustawienia ikona kodowania linii ](./media/user-guide/usbx-events/image97.png) ] (./media/user-guide/usbx-events/image98.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX. zdarzenie IOCTL ustawiania kodowania wiersza.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a>Klasa hosta Przekreśl stan wiersza zestawu IOCTL ACM 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a>ux_host_class_cdc_acm_ioctl_set_line_state

**Ikona** ![ Klasa hosta C D C A c M I O C T L ikona stanu wiersza](./media/user-guide/usbx-events/image99.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX zdarzenia IOCTL ustawiania stanu wiersza.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-read"></a>Klasa hosta — odczyt przechwytywania ACM 

#### <a name="ux_host_class_cdc_acm_read"></a>ux_host_class_cdc_acm_read

**Ikona** ![ Klasa hosta C D C A C M ikona odczytu](./media/user-guide/usbx-events/image100.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu klasy USBX przechwytywania.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-reception-start"></a>Rozpoczęcie odbierania ACM klasy hosta 

#### <a name="ux_host_class_cdc_acm_reception_start"></a>ux_host_class_cdc_acm_reception_start

**Ikona** ![ Klasa hosta C D C A p M — ikona startowa przyjęcia](./media/user-guide/usbx-events/image101.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX zdarzenia rozpoczęcia odbioru ACM.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-reception-stop"></a>Klasa hosta przełączać do przechwytywania ACM 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a>ux_host_class_cdc_acm_reception_stop

**Ikona** ![ Klasa hosta C D C, ikona zatrzymania odbierania C M](./media/user-guide/usbx-events/image102.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX przełączać zdarzenie zatrzymania odbioru ACM.

**Pola informacji**

- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-cdc-acm-write"></a>Klasa hosta przechwytywania ACM 

#### <a name="ux_host_class_acm_write"></a>ux_host_class_acm_write

**Ikona** ![ Klasa hosta C D C A C M ikona zapisu](./media/user-guide/usbx-events/image103.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu klasy USBX przechwytywania ACM.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-dpump-activate"></a>Dpump Aktywuj klasy hosta 

#### <a name="ux_host_class_dpump_activate"></a>ux_host_class_dpump_activate

**Ikona** ![ Ikona Dpump aktywowania klasy hosta](./media/user-guide/usbx-events/image104.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Activate USBX klasy hosta Dpump.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-dpump-deactivate"></a>Dpump Dezaktywuj klasy hosta 

#### <a name="ux_host_class_dpump_deactivate"></a>ux_host_class_dpump_deactivate

**Ikona** ![ Ikona dezaktywowania klasy hosta Dpump](./media/user-guide/usbx-events/image105.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX Dpump.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-dpump-read"></a>Odczytaj Dpump klasy hosta 

#### <a name="ux_host_class_dpump_read"></a>ux_host_class_dpump_read

**Ikona** ![ Ikona odczytu Dpump klasy hosta](./media/user-guide/usbx-events/image106.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu USBX klasy hosta Dpump.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-dpump-write"></a>Dpump zapisu klasy hosta 

#### <a name="ux_host_class_dpump_write"></a>ux_host_class_dpump_write

**Ikona** ![ Ikona zapisu Dpump klasy hosta](./media/user-guide/usbx-events/image107.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu USBX klasy hosta Dpump.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-activate"></a>Aktywacja klasy hosta HID 

#### <a name="ux_host_class_hid_activate"></a>ux_host_class_hid_activate

**Ikona** ![ Ikona aktywacji klasy hosta HID](./media/user-guide/usbx-events/image108.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania klasy hosta HID USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-client-register"></a>Rejestr klienta HID klasy hosta 

#### <a name="ux_host_class_hid_client_register"></a>ux_host_class_hid_client_register

**Ikona** ![ Ikona rejestracji klienta HID klasy hosta](./media/user-guide/usbx-events/image109.png)

**Opis**

To zdarzenie reprezentuje zdarzenie rejestracji klienta klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: Nazwa klienta HID.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-deactivate"></a>Dezaktywowanie klasy hosta HID 

#### <a name="ux_host_class_hid_deactivate"></a>ux_host_class_hid_deactivate

**Ikona** ![ Ikona dezaktywacji klasy hosta HID](./media/user-guide/usbx-events/image110.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-idle-get"></a>Pobieranie z trybu bezczynności HID klasy hosta 

#### <a name="ux_host_class_hid_idle_get"></a>ux_host_class_hid_idle_get

**Ikona** ![ Ikona uzyskiwania bezczynności HID klasy hosta](./media/user-guide/usbx-events/image111.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania bezczynnej klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-idle-set"></a>Zestaw bezczynny HID klasy hosta 

#### <a name="ux_host_class_hid_idle_set"></a>ux_host_class_hid_idle_set

**Ikona** ![ Ikona zestawu bezczynności HID klasy hosta](./media/user-guide/usbx-events/image112.png)

**Opis**

To zdarzenie reprezentuje zdarzenie bezczynnego ustawiania klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-keyboard-activate"></a>Aktywuj klasy hosta klawiatury HID 

#### <a name="ux_host_class_hid_keyboard_activate"></a>ux_host_class_hid_keyboard_activate

**Ikona** ![ Ikona aktywacji klasy hosta HID](./media/user-guide/usbx-events/image113.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania klawiatury HID USBX klasy hosta.

**Pola informacji**
<p>Pole informacji 1: wystąpienie klasy.
<p>Pole informacji 2: wystąpienie klienta HID.
<p>Pole informacji 3: nie zostało użyte.
<p>Pole informacji 4: nieużywane.

### <a name="host-class-hid-keyboard-deactivate"></a>Dezaktywacja klasy hosta klawiatury HID 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a>ux_host_class_hid_keyboard_deactivate

**Ikona** ![ Ikona dezaktywacji klawiatury HID klasy hosta](./media/user-guide/usbx-events/image114.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klawiatury HID USBX klasy hosta.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wystąpienie klienta HID.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-mouse-activate"></a>Aktywacja myszy klasy hosta HID 

#### <a name="ux_host_class_hid_mouse_activate"></a>ux_host_class_hid_mouse_activate

**Ikona** ![ Ikona aktywacji kursora myszy klasy hosta HID](./media/user-guide/usbx-events/image115.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania myszy USBX klasy hosta HID.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wystąpienie klienta HID.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-mouse-deactivate"></a>Dezaktywacja myszy klasy hosta HID 

#### <a name="ux_host_class_hid_mouse_deactivate"></a>ux_host_class_hid_mouse_deactivate

**Ikona** ![ Ikona dezaktywacji myszy klasy hosta HID](./media/user-guide/usbx-events/image116.png)

**Opis**

- To zdarzenie reprezentuje zdarzenie dezaktywacji myszy klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wystąpienie klienta HID.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-remote-control-activate"></a>Aktywacja zdalnego sterowania HID klasy hosta 

#### <a name="ux_host_class_hid_remote_control_activate"></a>ux_host_class_hid_remote_control_activate

**Ikona** ![ Ikona aktywacji zdalnej kontroli HID klasy hosta](./media/user-guide/usbx-events/image117.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania zdalnego sterowania HID klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wystąpienie klienta HID.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-remote-control-deactivate"></a>Dezaktywacja zdalnego sterowania HID klasy hosta 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a>ux_host_class_hid_remote_control_deactivate

**Ikona** ![ Ikona dezaktywowania zdalnego sterowania kontrolką klasy hosta](./media/user-guide/usbx-events/image118.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji zdalnego sterowania HID klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wystąpienie klienta HID.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-report-get"></a>Pobieranie raportu HID klasy hosta 

#### <a name="ux_host_class_hid_report_get"></a>ux_host_class_hid_report_get

**Ikona** ![ Ikona pobierania raportu HID klasy hosta](./media/user-guide/usbx-events/image119.png)

**Opis**

To zdarzenie reprezentuje raport USBX klasy hosta HID get.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: Raport klienta.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hid-report-set"></a>Zestaw raportów HID klasy hosta 

#### <a name="ux_host_class_hid_report_set"></a>ux_host_class_hid_report_set

**Ikona** ![ Ikona zestawu raportów HID klasy hosta](./media/user-guide/usbx-events/image120.png)

**Opis** To zdarzenie reprezentuje zestaw raportów HID klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: Raport klienta.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hub-activate"></a>Aktywuj koncentrator klasy hosta 

#### <a name="ux_host_class_hub_activate"></a>ux_host_class_hub_activate

**Ikona** ![ Ikona aktywowania centrum klasy hosta](./media/user-guide/usbx-events/image121.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania centrum klas hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hub-change-detect"></a>Wykrywanie zmian centrum klasy hosta 

#### <a name="ux_host_class_hub_change_detect"></a>ux_host_class_hub_change_detect

**Ikona** ![ Ikona wykrywania zmian centrum klasy hosta](./media/user-guide/usbx-events/image122.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wykrywania zmiany centrum klas hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hub-deactivate"></a>Dezaktywacja centrum klasy hosta 

#### <a name="ux_host_class_hub_deactivate"></a>ux_host_class_hub_deactivate

**Ikona** ![ Ikona dezaktywacji centrum klasy hosta](./media/user-guide/usbx-events/image123.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji centrum klas hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-hub-port-change-connection-process"></a>Proces połączenia zmiany portu centrum klasy hosta 

#### <a name="ux_host_class_hub_change_connection_process"></a>ux_host_class_hub_change_connection_process

**Ikona** ![ Ikona procesu połączenia zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image124.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przetworzenia połączenia zmiany portu centrum klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: port.
- Pole informacji 3: stan portu.
- Pole informacji 4: nieużywane.

### <a name="host-class-hub-port-change-enable-process"></a>Proces włączania zmiany portu centrum klasy hosta 

#### <a name="ux_host_class_hub_port_change_enable_process"></a>ux_host_class_hub_port_change_enable_process

**Ikona** ![ Ikona włączenia procesu zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image125.png)

**Opis**

To zdarzenie reprezentuje zdarzenie włączenia procesu zmiany portu centrum klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: port.
- Pole informacji 3: stan portu.
- Pole informacji 4: nieużywane.

### <a name="host-class-hub-port-change-over-current-process"></a>Zmiana portu koncentratora klasy hosta na bieżący proces 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a>ux_host_class_hub_port_change_over_current_process

**Ikona** ![ Ikona hosta zmień port koncentratora na bieżący proces](./media/user-guide/usbx-events/image126.png)

**Opis**

To zdarzenie reprezentuje przydzielenie pakietu za pośrednictwem nx_packet_allocate.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: port.
- Pole informacji 3: stan portu.
- Pole informacji 4: nieużywane.

### <a name="host-class-hub-port-change-reset-process"></a>Proces resetowania zmiany portu centrum klasy hosta 

#### <a name="ux_host_class_hub_port_change_reset_process"></a>ux_host_class_hub_port_change_reset_process

**Ikona** ![ Ikona procesu resetowania zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image127.png)

**Opis**

To zdarzenie reprezentuje zdarzenie procesu resetowania portu centrum klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: centrum. Pole informacji 2: port.
- Pole informacji 3: stan portu.
- Pole informacji 4: nieużywane.

### <a name="host-class-hub-port-change-suspend-process"></a>Proces wstrzymania zmiany portu centrum klasy hosta 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a>ux_host_class_hub_port_change_suspend_process

**Ikona** ![ Ikona procesu wstrzymania zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image128.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wstrzymania zmiany portu centrum klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: port.
- Pole informacji 3: stan portu.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-activate"></a>Pima Aktywuj klasy hosta 

#### <a name="ux_host_class_pima_activate"></a>ux_host_class_pima_activate

**Ikona** ![ Ikona Pima aktywowania klasy hosta](./media/user-guide/usbx-events/image129.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Activate USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-deactivate"></a>Pima Dezaktywuj klasy hosta 

#### <a name="ux_host_class_pima_deactivate"></a>ux_host_class_pima_deactivate

**Ikona** ![ Ikona dezaktywowania klasy hosta Pima](./media/user-guide/usbx-events/image130.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-device-info-get"></a>Pobieranie informacji o urządzeniu klasy hosta Pima 

#### <a name="ux_host_class_pima_device_info_get"></a>ux_host_class_pima_device_info_get

**Ikona** ![ Ikona uzyskiwania informacji o urządzeniu klasy hosta Pima](./media/user-guide/usbx-events/image131.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: urządzenie Pima.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-device-reset"></a>Resetowanie urządzenia Pima klasy hosta 

#### <a name="ux_host_class_pima_device_reset"></a>ux_host_class_pima_device_reset

**Ikona** ![ Ikona resetowania urządzenia Pima klasy hosta](./media/user-guide/usbx-events/image132.png)

**Opis**

To zdarzenie reprezentuje USBX klasy hosta Pima zdarzenie resetowania urządzenia.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-notification"></a>Powiadomienie Pima klasy hosta 

#### <a name="ux_host_class_pima_notification"></a>ux_host_class_pima_notification

**Ikona** ![ Ikona powiadomienia Pima klasy hosta](./media/user-guide/usbx-events/image133.png)

**Opis**

To zdarzenie reprezentuje zdarzenie powiadomienia USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy. Pole informacji 2: kod zdarzenia.
- Pole informacji 3: Identyfikator transakcji.
- Pole informacji 4: parametr1.

### <a name="host-class-pima-number-objects-get"></a>Pobieranie obiektów typu Pima klasy hosta 

#### <a name="ux_host_class_pima_number_objects_get"></a>ux_host_class_pima_number_objects_get

**Ikona** ![ Ikona pobierania obiektów Pima klasy hosta](./media/user-guide/usbx-events/image134.png)

**Opis**

To zdarzenie reprezentuje klasę USBX hosta Pima obiektów Number zdarzenia.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-object-close"></a>Zamknięto obiekt Pima klasy hosta 

#### <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

**Ikona** ![ Ikona zamykania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image135.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zamknięcia obiektu USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: obiekt.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-object-copy"></a>Kopia obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_copy"></a>ux_host_class_pima_object_copy

**Ikona** ![ Ikona kopiowania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image136.png)

**Opis**

To zdarzenie reprezentuje zdarzenie USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-object-delete"></a>Usuwanie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

**Ikona** ![ Ikona usuwania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image137.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia obiektu USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-object-get"></a>Pobieranie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

**Ikona** ![ Ikona pobierania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image138.png)

**Opis**

To zdarzenie reprezentuje informacje o pobieraniu RARP za pośrednictwem nx_rarp_info_get.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: obiekt.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-object-info-get"></a>Pobieranie informacji o obiekcie Pima klasy hosta 

#### <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

**Ikona** ![ Ikona uzyskiwania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image139.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: obiekt.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-object-info-send"></a>Wysyłanie informacji o obiekcie Pima klasy hosta 

#### <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

**Ikona** ![ Ikona wysyłania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image140.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania informacji o obiekcie USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: obiekt.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-object-move"></a>Przeniesienie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ikona** ![ Ikona przenoszenia obiektu Pima klasy hosta](./media/user-guide/usbx-events/image141.png)

**Opis**

To zdarzenie reprThis zdarzenia reprezentuje zdarzenie przenoszenia obiektu klasy hosta USBX Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: obiekt.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-object-send"></a>Wysyłanie obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_move"></a>ux_host_class_pima_object_move

**Ikona** ![ Ikona wysyłania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image142.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wysyłania obiektu USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: obiekt.
- Pole informacji 3: bufor obiektów.
- Pole informacji 4: Długość obiektu.

### <a name="host-class-pima-object-transfer-abort"></a>Przerwanie transferu obiektu Pima klasy hosta 

#### <a name="ux_host_class_pima_object_transfer_abort"></a>ux_host_class_pima_object_transfer_abort

**Ikona** ![ Ikona przerwania transferu obiektu klasy hosta Pima](./media/user-guide/usbx-events/image143.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania transferu obiektu klasy USBX Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: obiekt.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-read"></a>Odczytaj Pima klasy hosta 

#### <a name="ux_host_class_pima_read"></a>ux_host_class_pima_read

**Ikona** ![ Ikona odczytu Pima klasy hosta](./media/user-guide/usbx-events/image144.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: długość danych.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-request-cancel"></a>Żądanie anulowania klasy hosta Pima 

#### <a name="ux_host_class_pima_request_cancel"></a>ux_host_class_pima_request_cancel

**Ikona** ![ Ikona anulowania żądania Pima klasy hosta](./media/user-guide/usbx-events/image145.png)

**Opis**

To zdarzenie reprezentuje zdarzenie anulowania żądania USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-session-close"></a>Zamknięcie sesji Pima klasy hosta 

#### <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

**Ikona** ![ Ikona zamykania sesji Pima dla klasy hosta](./media/user-guide/usbx-events/image146.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zamknięcia sesji USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: sesja Pima.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-session-open"></a>Otwarta sesja Pima sesji hosta 

#### <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

**Ikona** ![ Ikona Otwórz sesję Pima sesji hosta](./media/user-guide/usbx-events/image147.png)

**Opis** To zdarzenie reprezentuje USBX klasy hosta zdarzenia Pima sesji.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: sesja Pima.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-storage-ids-get"></a>Pobieranie identyfikatorów magazynu Pima klasy hosta 

#### <a name="ux_host_class_pima_session_ids_get"></a>ux_host_class_pima_session_ids_get

**Ikona** ![ Ikona pobierania identyfikatorów magazynu Pima klasy hosta](./media/user-guide/usbx-events/image148.png)

**Opis**

To zdarzenie reprezentuje USBX klasy hosta Pima zdarzenia get.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- NFO pole 2: tablica identyfikatorów magazynu.
- Pole informacji 3: Długość identyfikatora magazynu.
Pole informacji 4: nieużywane.

### <a name="host-class-pima-storage-info-get"></a>Pobieranie informacji o magazynie Pima klasy hosta 

#### <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

**Ikona** ![ Ikona pobierania informacji o magazynie Pima klasy hosta](./media/user-guide/usbx-events/image149.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania informacji o magazynie USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: Identyfikator magazynu.
- Pole informacji 3: Magazyn.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-thumb-get"></a>Pobieranie klasy hosta Pima kciuka 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ikona** ![ Ikona pobierania Pima klasy hosta](./media/user-guide/usbx-events/image150.png)

**Opis**

To zdarzenie reprezentuje nieakceptowanie połączenia z serwerem TCP za pośrednictwem nx_tcp_server_socket_unaccept.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: uchwyt obiektu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-pima-write"></a>Pima zapisu klasy hosta 

#### <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

**Ikona** ![ Ikona zapisu Pima klasy hosta](./media/user-guide/usbx-events/image151.png)

**Opis**

To zdarzenie reprezentuje USBX klasy hosta Pima.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: długość danych.
- Pole informacji 4: nieużywane.

### <a name="host-class-printer-activate"></a>Aktywuj drukarkę klasy hosta 

#### <a name="ux_host_class_printer_activate"></a>ux_host_class_printer_activate

**Ikona** ![ Ikona aktywowania drukarki klasy hosta](./media/user-guide/usbx-events/image152.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania drukarki klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wskaźnik do wystąpienia IP.
- Pole informacji 2: wskaźnik do gniazda.
- Pole informacji 3: typ usługi.
- Pole informacji 4: rozmiar okna odbierania.

### <a name="host-class-printer-deactivate"></a>Dezaktywacja drukarki klasy hosta 

#### <a name="ux_host_class_printer_deactivate"></a>ux_host_class_printer_deactivate

**Ikona** ![ Ikona dezaktywacji drukarki klasy hosta](./media/user-guide/usbx-events/image153.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji drukarki klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-printer-name-get"></a>Pobieranie nazwy drukarki klasy hosta 

#### <a name="ux_host_class_printer_name_get"></a>ux_host_class_printer_name_get

**Ikona** ![ Ikona pobierania nazwy drukarki klasy hosta](./media/user-guide/usbx-events/image154.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get nazwy drukarki klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-printer-read"></a>Odczytaj drukarkę klasy hosta 

#### <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

**Ikona** ![ Ikona odczytu drukarki klasy hosta](./media/user-guide/usbx-events/image155.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu drukarki klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-printer-soft-reset"></a>Resetowanie nietrwałe drukarki klasy hosta 

#### <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

**Ikona** ![ Ikona resetowania nietrwałego drukarki klasy hosta](./media/user-guide/usbx-events/image156.png)

**Opis**

To zdarzenie reprezentuje zdarzenie nietrwałego resetowania drukarki klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-printer-status-get"></a>Pobieranie stanu drukarki klasy hosta 

#### <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

**Ikona** ![ Ikona pobierania stanu drukarki klasy hosta](./media/user-guide/usbx-events/image157.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get stanu drukarki klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: stan drukarki.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-printer-write"></a>Zapis drukarki klasy hosta 

#### <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

**Ikona** ![ Ikona zapisu drukarki klasy hosta](./media/user-guide/usbx-events/image158.png)

**Opis**

To zdarzenie przedstawia zapis drukarki klasy hosta USBX.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-activate"></a>Mnóstwo Aktywuj klasy hosta 

#### <a name="ux_host_class_prolific_activate"></a>ux_host_class_prolific_activate 

**Ikona** ![ Ikona mnóstwo aktywowania klasy hosta](./media/user-guide/usbx-events/image159.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Activate USBX klasy hosta mnóstwo.

**Pola informacji** 

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-deactivate"></a>Mnóstwo Dezaktywuj klasy hosta 

#### <a name="ux_host_class_prolific_deactivate"></a>ux_host_class_prolific_deactivate 

**Ikona** ![ Ikona dezaktywowania klasy hosta mnóstwo](./media/user-guide/usbx-events/image160.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX mnóstwo.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a>Przerwanie mnóstwo operacji IOCTL klasy hosta w potoku 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a>ux_host_class_prolific_ioctl_abort_in_pipe

**Ikona** ![ Ikona potoku mnóstwo I O przerwanie klasy hosta](./media/user-guide/usbx-events/image161.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX mnóstwo przerwania w zdarzeniu potoku.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a>Przerwano potok operacji IOCTL klasy hosta mnóstwo 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a>ux_host_class_prolific_ioctl_abort_out_pipe

**Ikona** ![ Mnóstwo klasy hosta — ikona przerwania rozgałęzienia I O C T L](./media/user-guide/usbx-events/image162.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX mnóstwo przerywanie zdarzenia potoku.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-get-device-status"></a>Klasa hosta mnóstwo IOCTL pobieranie stanu urządzenia 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a>ux_host_class_prolific_ioctl_get_device_status

**Ikona** ![ Mnóstwo klasy hosta — ikona stanu urządzenia I O C T L](./media/user-guide/usbx-events/image163.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX mnóstwo IOCTL pobieranie zdarzenia stanu urządzenia.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: stan urządzenia.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-get-line-coding"></a>Klasa hosta mnóstwo IOCTL Pobierz kodowanie wiersza 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a>ux_host_class_prolific_ioctl_get_line_coding

**Ikona** ![ Ikona "Pobierz kodowanie wiersza" klasy hosta mnóstwo I O C T L](./media/user-guide/usbx-events/image164.png)

**Opis**

To zdarzenie reprezentuje klasę hosta USBX mnóstwo polecenie IOCTL pobieranie wiersza zdarzenia.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-purge"></a>Mnóstwo — przeczyszczanie klasy hosta 

#### <a name="ux_host_class_prolific_ioctl_purge"></a>ux_host_class_prolific_ioctl_purge

**Ikona** ![ Ikona przeczyszczania elementu IOCTL klasy hosta mnóstwo](./media/user-guide/usbx-events/image165.png)

**Opis**

To zdarzenie reprezentuje USBX klasy hosta mnóstwo zdarzenia przeczyszczania IOCTL.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-report-device"></a>Urządzenie raportu IOCTL klasy hosta mnóstwo 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a>ux_host_class_prolific_ioctl_report_device

**Ikona** ![ Ikona urządzenia z raportem klasy hosta mnóstwo I O C T L](./media/user-guide/usbx-events/image166.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany stanu urządzenia USBX klasy hosta mnóstwo.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-send-break"></a>Przerwanie wysyłania polecenia IOCTL klasy hosta mnóstwo 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a>ux_host_class_prolific_ioctl_send_break

**Ikona** ![ Mnóstwo klasy hosta — ikona przerwania wysyłania I O T L](./media/user-guide/usbx-events/image167.png)

**Opis**

To zdarzenie reprezentuje USBXą klasę hosta mnóstwo zdarzenie przerwania.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-set-line-coding"></a>Kodowanie liniowe zestawu poleceń IOCTL klasy hosta mnóstwo 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a>ux_host_class_prolific_ioctl_set_line_coding

**Ikona** ![ Mnóstwo klasy hosta — ikona kodowania linii I O C T L](./media/user-guide/usbx-events/image168.png)

**Opis**

To zdarzenie reprezentuje USBX klasy hosta mnóstwo zdarzenie kodowania wiersza.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-ioctl-set-line-state"></a>Stan wiersza ustawiania elementu IOCTL klasy hosta mnóstwo 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a>ux_host_class_prolific_ioctl_set_line_state

**Ikona** ![ Mnóstwo klasy hosta — ikona stanu wiersza I O C T L](./media/user-guide/usbx-events/image169.png)

**Opis**

To zdarzenie reprezentuje USBX klasy hosta mnóstwo zdarzenie stanu wiersza.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: parametr.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-read"></a>Odczytaj mnóstwo klasy hosta 

#### <a name="ux_host_class_prolific_read"></a>ux_host_class_prolific_read

**Ikona** ![ Ikona odczytu mnóstwo klasy hosta](./media/user-guide/usbx-events/image170.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu USBX klasy hosta mnóstwo.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-reception-start"></a>Rozpoczęcie odbierania mnóstwo klasy hosta 

#### <a name="ux_host_class_prolific_reception_start"></a>ux_host_class_prolific_reception_start

**Ikona** ![ Ikona startowa odbioru mnóstwo klasy hosta](./media/user-guide/usbx-events/image171.png)

**Opis**

To zdarzenie reprezentuje zdarzenie rozpoczęcia odbioru USBX klasy hosta mnóstwo.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-reception-stop"></a>Zatrzymanie odbierania mnóstwo klasy hosta 

#### <a name="ux_host_class_prolific_reception_stop"></a>ux_host_class_prolific_reception_stop

**Ikona** ![ Ikona zatrzymania odbierania mnóstwo klasy hosta](./media/user-guide/usbx-events/image172.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zatrzymania odbioru USBX klasy hosta mnóstwo.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-prolific-write"></a>Mnóstwo zapisu klasy hosta 

#### <a name="ux_host_class_prolific_write"></a>ux_host_class_prolific_write

**Ikona** ![ Ikona zapisu mnóstwo klasy hosta](./media/user-guide/usbx-events/image173.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu USBX klasy hosta mnóstwo.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: wskaźnik danych.
- Pole informacji 3: Żądana długość.
- Pole informacji 4: nieużywane.

### <a name="host-class-storage-activate"></a>Aktywuj magazyn klas hosta 

#### <a name="ux_host_class_storage_activate"></a>ux_host_class_storage_activate

**Ikona** ![ Ikona aktywowania magazynu klasy hosta](./media/user-guide/usbx-events/image174.png)

**Opis**

To zdarzenie reprezentuje zdarzenie aktywowania magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-storage-deactivate"></a>Dezaktywowanie magazynu klasy hosta 

#### <a name="ux_host_class_storage_deactivate"></a>ux_host_class_storage_deactivate

**Ikona** ![ Ikona dezaktywacji magazynu klasy hosta](./media/user-guide/usbx-events/image175.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dezaktywacji magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-storage-media-capacity-get"></a>Pobieranie pojemności nośnika magazynu klasy hosta 

#### <a name="ux_host_class_storage_media_capacity_get"></a>ux_host_class_storage_media_capacity_get

**Ikona** ![ Ikona pobierania pojemności nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image176.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania pojemności nośnika magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-storage-media-format-capacity-get"></a>Pobieranie pojemności formatu nośnika magazynu klasy hosta

#### <a name="ux_host_class_storage_media_format_capacity_get"></a>ux_host_class_storage_media_format_capacity_get

**Ikona** ![ Ikona pobierania pojemności formatu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image177.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania pojemności formatu nośnika magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

#### <a name="host-class-storage-media-mount"></a>Instalacja nośnika magazynu klasy hosta 

#### <a name="ux_host_class_storage_media_mount"></a>ux_host_class_storage_media_mount

**Ikona** ![ Ikona instalacji nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image178.png)

**Opis**

To zdarzenie reprezentuje zdarzenie instalacji nośnika magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: sektor.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-storage-media-open"></a>Otwarty nośnik magazynu klasy hosta 

#### <a name="ux_host_class_storage_media_open"></a>ux_host_class_storage_media_open

**Ikona** ![ Ikona otwierania nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image179.png)

**Opis**

To zdarzenie reprezentuje zdarzenie otwarcia nośnika magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: Multimedia.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-storage-media-read"></a>Odczyt nośnika magazynu klasy hosta 

#### <a name="ux_host_class_storage_media_read"></a>ux_host_class_storage_media_read

**Ikona** ![ Ikona odczytu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image180.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu nośnika magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: początek sektora.
- Pole informacji 3: liczba sektorów.
- Pole informacji 4: wskaźnik danych.

### <a name="host-class-storage-media-write"></a>Zapis nośnika magazynu klasy hosta 

#### <a name="ux_host_class_storage_media_write"></a>ux_host_class_storage_media_write

**Ikona** ![ Ikona zapisu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image181.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu nośnika magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: początek sektora.
- Pole informacji 3: liczba sektorów.
- Pole informacji 4: wskaźnik danych.

### <a name="host-class-storage-request-sense"></a>Wykrywanie żądania magazynu klasy hosta 

#### <a name="ux_host_class_storage_request_sense"></a>ux_host_class_storage_request_sense

**Ikona** ![ Ikona wykrywania żądań magazynu klasy hosta](./media/user-guide/usbx-events/image182.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wykrywania żądania magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-storage-start-stop"></a>Zatrzymanie uruchomienia magazynu klasy hosta 

#### <a name="ux_host_class_storage_start_stop"></a>ux_host_class_storage_start_stop

**Ikona** ![ Ikona zatrzymania uruchamiania magazynu klasy hosta](./media/user-guide/usbx-events/image183.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zatrzymania uruchamiania magazynu klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: Uruchom sygnał zatrzymania.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-class-storage-unit-ready-test"></a>Gotowy test jednostki magazynu klasy hosta 

#### <a name="ux_host_class_storage_unit_ready_test"></a>ux_host_class_storage_unit_ready_test

**Ikona** ![ Ikona testowania gotowej jednostki magazynu klasy hosta](./media/user-guide/usbx-events/image184.png)

**Opis**

To zdarzenie reprezentuje zdarzenie testowania gotowej jednostki magazynowej klasy hosta USBX.

**Pola informacji**

- Pole informacji 1: wystąpienie klasy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-class-instance-create"></a>Tworzenie wystąpienia klasy stosu hosta 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ikona** ![ Ikona tworzenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image185.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia klasy stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Klasa.
- Pole informacji 2: wystąpienie klasy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-class-instance-destroy"></a>Niszczenie wystąpienia klasy stosu hosta 

#### <a name="ux_host_class_instance_create"></a>ux_host_class_instance_create

**Ikona** ![ Ikona niszczenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image186.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zniszczenia wystąpienia klasy stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Klasa.
- Pole informacji 2: wystąpienie klasy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-configuration-delete"></a>Usuwanie konfiguracji stosu hosta 

#### <a name="ux_host_class_configuration_delete"></a>ux_host_class_configuration_delete

**Ikona** ![ Ikona usuwania konfiguracji stosu hosta](./media/user-guide/usbx-events/image187.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: konfiguracja.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-configuration-enumerate"></a>Wyliczenie konfiguracji stosu hosta 

#### <a name="ux_host_stack_configuration_enumerate"></a>ux_host_stack_configuration_enumerate

**Ikona** ![ Ikona wyliczenia konfiguracji stosu hosta](./media/user-guide/usbx-events/image188.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wyliczania konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="stack-configuration-instance-create"></a>Tworzenie wystąpienia konfiguracji stosu 

#### <a name="ux_host_stack_configuration_instance_create"></a>ux_host_stack_configuration_instance_create

**Ikona** ![ Ikona tworzenia wystąpienia konfiguracji stosu](./media/user-guide/usbx-events/image189.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: konfiguracja.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-configuration-instance-delete"></a>Usuwanie wystąpienia konfiguracji stosu hosta 

#### <a name="ux_host_stack_configuration_instance_delete"></a>ux_host_stack_configuration_instance_delete

**Ikona** ![ Ikona usuwania wystąpienia konfiguracji stosu hosta](./media/user-guide/usbx-events/image190.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia wystąpienia konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: konfiguracja.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-configuration-set"></a>Zestaw konfiguracyjny stosu hosta 

#### <a name="ux_host_stack_configuration_set"></a>ux_host_stack_configuration_set

**Ikona** ![ Ikona zestawu konfiguracji stosu hosta](./media/user-guide/usbx-events/image191.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu konfiguracji stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: konfiguracja.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-device-address-set"></a>Zestaw adresów urządzeń stosu hosta 

#### <a name="ux_host_stack_device_address_set"></a>ux_host_stack_device_address_set

**Ikona** ![ Ikona zestawu adresów urządzeń stosu hosta](./media/user-guide/usbx-events/image192.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu adresów urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: adres urządzenia.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-device-configuration-get"></a>Pobieranie konfiguracji urządzenia stosu hosta 

#### <a name="ux_host_stack_device_configuration_get"></a>ux_host_stack_device_configuration_get

**Ikona** ![ Ikona pobierania konfiguracji urządzenia stosu hosta](./media/user-guide/usbx-events/image193.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania konfiguracji urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- NFO pole 2: konfiguracja.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-device-configuration-select"></a>Wybór konfiguracji urządzenia stosu hosta 

#### <a name="ux_host_stack_device_configuration_select"></a>ux_host_stack_device_configuration_select

**Ikona** ![ Ikona wybierania konfiguracji urządzenia stosu hosta](./media/user-guide/usbx-events/image194.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wybierania konfiguracji urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: konfiguracja.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-device-descriptor-read"></a>Odczyt deskryptora urządzenia stosu hosta 

#### <a name="ux_host_stack_device_descriptor_read"></a>ux_host_stack_device_descriptor_read

**Ikona** ![ Ikona odczytu deskryptora urządzenia stosu hosta](./media/user-guide/usbx-events/image195.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu deskryptora urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-device-get"></a>Pobieranie urządzenia stosu hosta 

#### <a name="ux_host_stack_device_get"></a>ux_host_stack_device_get

**Ikona** ![ Ikona pobierania urządzenia stosu hosta](./media/user-guide/usbx-events/image196.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: indeks urządzenia.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-device-remove"></a>Usuwanie urządzenia stosu hosta 

#### <a name="ux_host_stack_device_remove"></a>ux_host_stack_device_remove

**Ikona** ![ Ikona usuwania urządzenia stosu hosta](./media/user-guide/usbx-events/image197.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: HCD.
- Pole informacji 2: element nadrzędny.
- Pole informacji 3: indeks portu.
- Pole informacji 4: urządzenie.

### <a name="host-stack-device-resource-free"></a>Zasób urządzenia stosu hosta bezpłatnie 

#### <a name="ux_host_stack_device_resource_free"></a>ux_host_stack_device_resource_free

**Ikona** ![ Ikona bezpłatnego zasobu urządzenia stosu hosta](./media/user-guide/usbx-events/image198.png)

**Opis**

To zdarzenie reprezentuje zdarzenie bezpłatne zasobów urządzenia stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-endpoint-instance-create"></a>Tworzenie wystąpienia punktu końcowego stosu hosta 

#### <a name="ux_host_stack_endpoint_instance_create"></a>ux_host_stack_endpoint_instance_create

**Ikona** ![ Ikona tworzenia wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image199.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-endpoint-instance-delete"></a>Usuwanie wystąpienia punktu końcowego stosu hosta 

#### <a name="ux_host_stack_endpoint_instance_delete"></a>ux_host_stack_endpoint_instance_delete

**Ikona** ![ Ikona usuwania wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image200.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usuwania wystąpienia punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 2: punkt końcowy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-endpoint-reset"></a>Resetowanie punktu końcowego stosu hosta 

#### <a name="ux_host_stack_endpoint_reset"></a>ux_host_stack_endpoint_reset

**Ikona** ![ Ikona resetowania punktu końcowego stosu hosta](./media/user-guide/usbx-events/image201.png)

**Opis**

To zdarzenie reprezentuje zdarzenie resetowania punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-endpoint-transfer-abort"></a>Przerwanie transferu punktu końcowego stosu hosta 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a>ux_host_stack_endpoint_transfer_abort

**Ikona** ![ Ikona przerwania transferu punktu końcowego stosu hosta](./media/user-guide/usbx-events/image202.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania transferu punktu końcowego stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: punkt końcowy.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-host-controller-register"></a>Rejestr kontrolera hosta stosu hosta 

#### <a name="ux_host_stack_hcd_register"></a>ux_host_stack_hcd_register

**Ikona** ![ Ikona rejestru kontrolera hosta stosu hosta](./media/user-guide/usbx-events/image203.png)

**Opis**

To zdarzenie reprezentuje rejestr kontrolera hosta stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: Nazwa HCD.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-initialize"></a>Inicjowanie stosu hosta 

#### <a name="ux_host_stack_initialize"></a>ux_host_stack_initialize

**Ikona** ![ Ikona inicjowania stosu hosta](./media/user-guide/usbx-events/image204.png)

**Opis**

To zdarzenie reprezentuje zdarzenie inicjowania stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-interface-endpoint-get"></a>Pobieranie punktu końcowego interfejsu stosu hosta 

#### <a name="interface_-tcp-retry-entry"></a>Interface_ wpis ponownych prób protokołu TCP

**Ikona** ![ Ikona pobierania punktu końcowego interfejsu stosu hosta](./media/user-guide/usbx-events/image205.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne zdarzenie ponowienia protokołu TCP NetX.

**Pola informacji**

- Pole informacji 1: interfejs.
- Pole informacji 2: Indeks punktu końcowego.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-interface-instance-create"></a>Tworzenie wystąpienia interfejsu stosu hosta 

#### <a name="ux_host_stack_interface_instance_create"></a>ux_host_stack_interface_instance_create

**Ikona** ![ Ikona tworzenia wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image206.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia interfejsu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: interfejs.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-interface-instance-delete"></a>Usuwanie wystąpienia interfejsu stosu hosta 

#### <a name="ux_host_stack_interface_instance_delete"></a>ux_host_stack_interface_instance_delete

**Ikona** ![ Ikona usuwania wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image207.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia wystąpienia interfejsu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: interfejs.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-interface-set"></a>Zestaw interfejsów stosu hosta 

#### <a name="ux_host_stack_interface_set"></a>ux_host_stack_interface_set

**Ikona** ![ Ikona zestawu interfejsów stosu hosta](./media/user-guide/usbx-events/image208.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu interfejsu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: interfejs.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-interface-setting-select"></a>Wybieranie ustawienia interfejsu stosu hosta 

#### <a name="ux_host_stack_interface_setting_select"></a>ux_host_stack_interface_setting_select

**Ikona** ![ Ikona wybierania ustawienia interfejsu stosu hosta](./media/user-guide/usbx-events/image209.png)

**Opis**

To zdarzenie przedstawia zdarzenie select dla ustawienia interfejsu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: interfejs.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-new-configuration-create"></a>Tworzenie nowej konfiguracji stosu hosta 

#### <a name="ux_host_stack_new_configuration_create"></a>ux_host_stack_new_configuration_create

**Ikona** ![ Ikona tworzenia nowej konfiguracji stosu hosta](./media/user-guide/usbx-events/image210.png)

**Opis**
 
To zdarzenie reprezentuje zdarzenie tworzenia nowej konfiguracji w stosie hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: konfiguracja.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-new-device-create"></a>Tworzenie nowego urządzenia przez stos hosta 

#### <a name="ux_host_stack_new_device_create"></a>ux_host_stack_new_device_create

**Ikona** ![ Ikona tworzenia nowego urządzenia dla stosu hosta](./media/user-guide/usbx-events/image211.png)

**Opis**
 
 To zdarzenie reprezentuje zdarzenie tworzenia nowego urządzenia przez stos hosta USBX.

**Pola informacji**

- Pole informacji 1: HCD.
- Pole informacji 2: właściciel urządzenia.
- Pole informacji 3: indeks portu.
- Pole informacji 4: urządzenie.

### <a name="host-stack-new-endpoint-create"></a>Tworzenie nowego punktu końcowego stosu hosta 

#### <a name="ux_host_stack_new_endpoint_create"></a>ux_host_stack_new_endpoint_create

**Ikona** ![ Ikona tworzenia nowego punktu końcowego stosu hosta](./media/user-guide/usbx-events/image212.png)

**Opis**
 
To zdarzenie reprezentuje zdarzenie tworzenia nowego punktu końcowego przez stos hosta USBX.

**Pola informacji**

- Pole informacji 1: interfejs.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-root-hub-change-process"></a>Proces zmiany głównego koncentratora stosu hosta 

#### <a name="ux_host_stack_rh_change_process"></a>ux_host_stack_rh_change_process

**Ikona** ![ Ikona procesu zmiany głównego centrum w stosie hosta](./media/user-guide/usbx-events/image213.png)

**Opis**
 
To zdarzenie reprezentuje proces zmiany głównego centrum USBX stosu hosta.

**Pola informacji**

- Pole informacji 1: indeks portu.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-root-hub-device-extraction"></a>Wyodrębnianie urządzenia głównego koncentratora stosu hosta 

#### <a name="ux_host_stack_rh_device_extraction"></a>ux_host_stack_rh_device_extraction

**Ikona** ![ Ikona wyodrębniania urządzenia głównego koncentratora stosu hosta](./media/user-guide/usbx-events/image214.png)

**Opis**

To zdarzenie przedstawia zdarzenie wyodrębniania głównego urządzenia piasty stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: HCD.
- Pole informacji 2: indeks portu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-root-hub-device-insertion"></a>Wstawianie urządzenia głównego koncentratora stosu hosta 

#### <a name="ux_host_stack_rh_device_insertion"></a>ux_host_stack_rh_device_insertion

**Ikona** ![ Ikona wstawienia urządzenia głównego koncentratora stosu hosta](./media/user-guide/usbx-events/image215.png)

**Opis**

To zdarzenie reprezentuje włożenie urządzenia głównego koncentratora USBX stosu.

**Pola informacji**

- Pole informacji 1: HCD.
- Pole informacji 2: indeks portu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="host-stack-transfer-request"></a>Żądanie transferu stosu hosta 

#### <a name="ux_host_stack_transfer_request"></a>ux_host_stack_transfer_request

**Ikona** ![ Ikona żądania transferu stosu hosta](./media/user-guide/usbx-events/image216.png)

**Opis**

To zdarzenie reprezentuje żądanie przetransferowania stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: żądanie transferu.
- Pole informacji 4: nieużywane.

### <a name="host-stack-transfer-request-abort"></a>Przerwano żądanie transferu stosu hosta 

#### <a name="internal-io-driver-get-status"></a>Stan wewnętrznego pobierania sterownika we/wy

**Ikona** ![ Ikona przerwania żądania transferu stosu hosta](./media/user-guide/usbx-events/image217.png)

**Opis**

To zdarzenie przedstawia przerwanie żądania transferu stosu hosta USBX.

**Pola informacji**

- Pole informacji 1: urządzenie.
- Pole informacji 2: punkt końcowy.
- Pole informacji 3: żądanie transferu.
- Pole informacji 4: nieużywane.

### <a name="usbx-error"></a>Błąd USBX 

#### <a name="ux_error"></a>ux_error

**Ikona** ![ Ikona błędu U S B X](./media/user-guide/usbx-events/image218.png)

**Opis**

To zdarzenie reprezentuje zdarzenie błędu USBX.

**Pola informacji**

- Pole informacji 1: błąd USBX.
- Pole informacji 2: Nazwa błędu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.