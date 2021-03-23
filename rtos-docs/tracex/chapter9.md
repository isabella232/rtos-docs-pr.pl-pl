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
# <a name="chapter-9---azure-rtos-usbx-trace-events"></a><span data-ttu-id="949aa-103">Rozdział 9 — zdarzenia śledzenia usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="949aa-103">Chapter 9 - Azure RTOS USBX trace events</span></span>

<span data-ttu-id="949aa-104">Ten rozdział zawiera opis zdarzeń usługi Azure RTO USBX wyświetlanych przez usługę TraceX.</span><span class="sxs-lookup"><span data-stu-id="949aa-104">This chapter contains a description of the Azure RTOS USBX events displayed by TraceX.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="949aa-105">Lista zdarzeń i ikon</span><span class="sxs-lookup"><span data-stu-id="949aa-105">List of Events and Icons</span></span>

<span data-ttu-id="949aa-106">Poniżej znajduje się lista zdarzeń USBX wyświetlanych przez TraceX.</span><span class="sxs-lookup"><span data-stu-id="949aa-106">The following is a list of USBX events displayed by TraceX.</span></span>

| <span data-ttu-id="949aa-107">Ikona</span><span class="sxs-lookup"><span data-stu-id="949aa-107">Icon</span></span>                             | <span data-ttu-id="949aa-108">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="949aa-108">Meaning</span></span>                               |
| -------------------------------- | ------------------------------------- |
| ![Ikona urządzenia C D C aktywacja](./media/user-guide/usbx-events/image1.png)    | <span data-ttu-id="949aa-110">**Aktywowanie przechwytywania klas urządzeń** *(ux_device_class_cdc_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-110">**Device Class Cdc Activate** *(ux_device_class_cdc_activate)*</span></span> |
| ![Ikona klasy urządzenia C D C](./media/user-guide/usbx-events/image2.png)    | <span data-ttu-id="949aa-112">**Dezaktywacja przechwytywania klasy urządzeń** *(ux_device_class_cdc_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-112">**Device Class Cdc Deactivate** *(ux_device_class_cdc_deactivate)*</span></span> |
| ![Ikona Odczytaj klasy urządzeń C D C](./media/user-guide/usbx-events/image3.png)    | <span data-ttu-id="949aa-114">**Odczytywanie danych przechwytywania z klasy urządzeń** *(ux_device_class_cdc_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-114">**Device Class Cdc Read** *(ux_device_class_cdc_read)*</span></span> |
| ![Ikona urządzenia C D C pisanie](./media/user-guide/usbx-events/image4.png)    | <span data-ttu-id="949aa-116">**Zapis przechwytywania danych klasy urządzeń** *(ux_device_class_cdc_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-116">**Device Class Cdc Write** *(ux_device_class_cdc_write)*</span></span> |
| ![Ikona urządzenia Dpump Activate](./media/user-guide/usbx-events/image5.png)    | <span data-ttu-id="949aa-118">**Dpump aktywowania klasy urządzenia** *(ux_device_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-118">**Device Class Dpump Activate** *(ux_device_class_dpump_activate)*</span></span> |
| ![Ikona dezaktywowania klasy urządzenia Dpump](./media/user-guide/usbx-events/image6.png)    | <span data-ttu-id="949aa-120">**Dezaktywacja klasy urządzenia Dpump** *(ux_device_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-120">**Device Class Dpump Deactivate** *(ux_device_class_dpump_deactivate)*</span></span> |
| ![Ikona odczytu Dpump klasy urządzeń](./media/user-guide/usbx-events/image7.png)    | <span data-ttu-id="949aa-122">**Dpump Odczytaj klasy urządzenia** *(ux_device_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-122">**Device Class Dpump Read** *(ux_device_class_dpump_read)*</span></span> |
| ![Ikona zapisu Dpump klasy urządzeń](./media/user-guide/usbx-events/image8.png)    | <span data-ttu-id="949aa-124">**Dpump** *(Ux_device_class_dpump_write)* klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-124">**Device Class Dpump Write** *(ux_device_class_dpump_write)*</span></span> |
| ![Ikona klasy urządzenia HID Aktywuj](./media/user-guide/usbx-events/image9.png)    | <span data-ttu-id="949aa-126">**Aktywacja klasy urządzenia HID** *(ux_device_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-126">**Device Class Hid Activate** *(ux_device_class_hid_activate)*</span></span> |
| ![Ikona dezaktywacji klasy urządzenia](./media/user-guide/usbx-events/image10.png)    | <span data-ttu-id="949aa-128">**Dezaktywacja klasy urządzenia HID** *(ux_device_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-128">**Device Class Hid Deactivate** *(ux_device_class_hid_deactivate)*</span></span> |
| ![Ikona wysyłania deskryptora HID klasy urządzeń](./media/user-guide/usbx-events/image11.png)    | <span data-ttu-id="949aa-130">**Wysyłanie deskryptora HID klasy urządzeń** *(ux_device_class_hid_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-130">**Device Class Hid Descriptor Send** *(ux_device_class_hid_descriptor_send)*</span></span> |
| ![Ikona pobierania zdarzenia HID z klasą urządzeń](./media/user-guide/usbx-events/image12.png)    | <span data-ttu-id="949aa-132">**Pobieranie zdarzenia HID** *(Ux_device_class_hid_event_get)* klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-132">**Device Class Hid Event Get** *(ux_device_class_hid_event_get)*</span></span> |
| ![Ikona zestawu zdarzeń HID klasy urządzeń](./media/user-guide/usbx-events/image13.png)    | <span data-ttu-id="949aa-134">**Zestaw zdarzeń HID klasy urządzenia** *(ux_device_class_hid_event_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-134">**Device Class Hid Event Set** *(ux_device_class_hid_event_set)*</span></span> |
| ![Ikona pobierania raportu HID klasy urządzeń](./media/user-guide/usbx-events/image14.png)    | <span data-ttu-id="949aa-136">**Pobieranie raportu HID klasy urządzeń** *(ux_device_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-136">**Device Class Hid Report Get** *(ux_device_class_hid_report_get)*</span></span> |
| ![Ikona zestawu raportów HID klasy urządzeń](./media/user-guide/usbx-events/image15.png)    | <span data-ttu-id="949aa-138">**Zestaw raportów HID klasy urządzenia** *(ux_device_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-138">**Device Class Hid Report Set** *(ux_device_class_hid_report_set)*</span></span> |
| ![Ikona urządzenia Pima Activate](./media/user-guide/usbx-events/image16.png)    | <span data-ttu-id="949aa-140">**Pima aktywowania klasy urządzenia** *(ux_device_class_pima_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-140">**Device Class Pima Activate** *(ux_device_class_pima_activate)*</span></span> |
| ![Ikona dezaktywowania klasy urządzenia Pima](./media/user-guide/usbx-events/image17.png)    | <span data-ttu-id="949aa-142">**Dezaktywacja klasy urządzenia Pima** *(ux_device_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-142">**Device Class Pima Deactivate** *(ux_device_class_pima_deactivate)*</span></span> |
| ![Ikona wysyłania informacji o urządzeniu Pima klasy urządzeń](./media/user-guide/usbx-events/image18.png)    | <span data-ttu-id="949aa-144">**Klasa urządzenia Pima wysyłanie informacji o urządzeniu** *(ux_device_class_pima_device_info_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-144">**Device Class Pima Device Info Send** *(ux_device_class_pima_device_info_send)*</span></span> |
| ![Ikona pobierania zdarzenia Pima klasy urządzeń](./media/user-guide/usbx-events/image19.png)    | <span data-ttu-id="949aa-146">**Pobieranie zdarzenia Pima klasy urządzenia** *(ux_device_class_pima_event_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-146">**Device Class Pima Event Get** *(ux_device_class_pima_event_get)*</span></span> |
| ![Ikona zestawu zdarzeń Pima klasy urządzeń](./media/user-guide/usbx-events/image20.png)    | <span data-ttu-id="949aa-148">**Zestaw zdarzeń Pima klasy urządzeń** *(ux_device_class_pima_event_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-148">**Device Class Pima Event Set** *(ux_device_class_pima_event_set)*</span></span> |
| ![Ikona dodawania obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image21.png)    | <span data-ttu-id="949aa-150">**Dodawanie obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_add)*</span><span class="sxs-lookup"><span data-stu-id="949aa-150">**Device Class Pima Object Add** *(ux_device_class_pima_object_add)*</span></span> |
| ![Ikona uzyskiwania danych obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image22.png)    | <span data-ttu-id="949aa-152">**Pobieranie danych obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-152">**Device Class Pima Object Data Get** *(ux_device_class_pima_object_data_get)*</span></span> |
| ![Ikona wysyłania danych obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image23.png)    | <span data-ttu-id="949aa-154">**Wysyłanie danych obiektu Pima klasy urządzeń** *(ux_device_class_pima_object_data_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-154">**Device Class Pima Object Data Send** *(ux_device_class_pima_object_data_send)*</span></span> |
| ![Ikona usuwania obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image24.png)    | <span data-ttu-id="949aa-156">**Usuwanie obiektu Pima klasy urządzenia** *(ux_device_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="949aa-156">**Device Class Pima Object Delete** *(ux_device_class_pima_object_delete)*</span></span> |
| ![Obiekt Pima klasy urządzenia obsługuje ikonę wysyłania](./media/user-guide/usbx-events/image25.png)    | <span data-ttu-id="949aa-158">**Obiekt Pima klasy urządzenia obsługuje wysyłanie** *(ux_device_class_pima_object_handles_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-158">**Device Class Pima Object Handles Send** *(ux_device_class_pima_object_handles_send)*</span></span> |
| ![Ikona uzyskiwania informacji o obiekcie Pima klasy urządzeń](./media/user-guide/usbx-events/image26.png)    | <span data-ttu-id="949aa-160">**Pobieranie informacji o obiekcie Pima klasy urządzenia** *(ux_device_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-160">**Device Class Pima Object Info Get** *(ux_device_class_pima_object_info_get)*</span></span> |
| ![Ikona wysyłania informacji o obiekcie Pima klasy urządzenia](./media/user-guide/usbx-events/image27.png)    | <span data-ttu-id="949aa-162">**Wysyłanie informacji o obiekcie Pima klasy urządzenia** *(ux_device_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-162">**Device Class Pima Object Info Send** *(ux_device_class_pima_object_info_send)*</span></span> |
| ![Ikona Pima obiektów klasy urządzeń](./media/user-guide/usbx-events/image28.png)    | <span data-ttu-id="949aa-164">**Klasa urządzenia Pima liczba obiektów do wysłania** *(ux_device_class_pima_objects_number_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-164">**Device Class Pima Objects Number Send** *(ux_device_class_pima_objects_number_send)*</span></span> |
| ![Ikona Pima części danych obiektu klasy urządzenia](./media/user-guide/usbx-events/image29.png)    | <span data-ttu-id="949aa-166">**Klasa urządzenia Pima częściowe dane obiektu Get** *(ux_device_class_pima_partial_object_data_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-166">**Device Class Pima Partial Object Data Get** *(ux_device_class_pima_partial_object_data_get)*</span></span> |
| ![Ikona wysyłania odpowiedzi Pima klasy urządzeń](./media/user-guide/usbx-events/image30.png)    | <span data-ttu-id="949aa-168">**Odpowiedź klasy urządzenia Pima Send** *(ux_device_class_pima_response_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-168">**Device Class Pima Response Send** *(ux_device_class_pima_response_send)*</span></span>|
| ![Ikona wysyłania I Pima magazynu klasy urządzeń](./media/user-guide/usbx-events/image31.png)    | <span data-ttu-id="949aa-170">**Klasa urządzenia Pima — wysyłanie identyfikatora magazynu** *(ux_device_class_pima_storage_id_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-170">**Device Class Pima Storage Id Send** *(ux_device_class_pima_storage_id_send)*</span></span> |
| ![Ikona wysyłania informacji o magazynie Pima klasy urządzeń](./media/user-guide/usbx-events/image32.png)    | <span data-ttu-id="949aa-172">**Klasa urządzenia Pima — wysyłanie informacji o magazynie** *(ux_device_class_pima_storage_info_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-172">**Device Class Pima Storage Info Send** *(ux_device_class_pima_storage_info_send)*</span></span> |
| ![Ikona urządzenia R N D I aktywacja](./media/user-guide/usbx-events/image33.png)    | <span data-ttu-id="949aa-174">**RNDIS aktywowania klasy urządzenia** *(ux_device_class_rndis_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-174">**Device Class Rndis Activate** *(ux_device_class_rndis_activate)*</span></span> |
| ![Ikona urządzenia R N D I S Dezaktywuj](./media/user-guide/usbx-events/image34.png)    | <span data-ttu-id="949aa-176">**Dezaktywacja klasy urządzenia RNDIS** *(ux_device_class_rndis_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-176">**Device Class Rndis Deactivate** *(ux_device_class_rndis_deactivate)*</span></span> |
| ![Klasa urządzenia R N D I S komunikat o zachowaniu Aliveicon](./media/user-guide/usbx-events/image35.png)    | <span data-ttu-id="949aa-178">**RNDIS komunikat o klasie urządzenia** *(ux_device_class_rndis_msg_keep_alive)*</span><span class="sxs-lookup"><span data-stu-id="949aa-178">**Device Class Rndis Message Keep Alive** *(ux_device_class_rndis_msg_keep_alive)*</span></span> |
| ![Ikona zapytania R N D I komunikat o błędzie dla klasy urządzenia](./media/user-guide/usbx-events/image36.png)    | <span data-ttu-id="949aa-180">**Kwerenda komunikatu RNDIS klasy urządzenia** *(ux_device_class_rndis_msg_query)*</span><span class="sxs-lookup"><span data-stu-id="949aa-180">**Device Class Rndis Message Query** *(ux_device_class_rndis_msg_query)*</span></span> |
| ![Klasa urządzenia R N D I S ikona resetowania komunikatu](./media/user-guide/usbx-events/image37.png)    | <span data-ttu-id="949aa-182">**Resetowanie komunikatu o klasie urządzeń RNDIS** *(ux_device_class_rndis_msg_reset)*</span><span class="sxs-lookup"><span data-stu-id="949aa-182">**Device Class Rndis Message Reset** *(ux_device_class_rndis_msg_reset)*</span></span> |
| ![Klasa urządzenia R N D I S ikona zestawu komunikatów](./media/user-guide/usbx-events/image38.png)    | <span data-ttu-id="949aa-184">**RNDIS klasy urządzeń — zestaw komunikatów** *(ux_device_class_rndis_msg_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-184">**Device Class Rndis Message Set** *(ux_device_class_rndis_msg_set)*</span></span> |
| ![Klasa urządzenia R N D I S — ikona odbierania pakietów](./media/user-guide/usbx-events/image39.png)    | <span data-ttu-id="949aa-186">**Odbieranie pakietu RNDIS klasy urządzeń** *(ux_device_class_rndis_packet_receive)*</span><span class="sxs-lookup"><span data-stu-id="949aa-186">**Device Class Rndis Packet Receive** *(ux_device_class_rndis_packet_receive)*</span></span> |
| ![Klasa urządzenia R N D I S ikona wysyłania pakietów](./media/user-guide/usbx-events/image40.png)    | <span data-ttu-id="949aa-188">**RNDIS przesyłania pakietów klasy urządzeń** *(ux_device_class_rndis_packet_transmit)*</span><span class="sxs-lookup"><span data-stu-id="949aa-188">**Device Class Rndis Packet Transmit** *(ux_device_class_rndis_packet_transmit)*</span></span> |
| ![Ikona aktywacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image41.png)    | <span data-ttu-id="949aa-190">**Aktywowanie magazynu klasy urządzeń** *(ux_device_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-190">**Device Class Storage Activate** *(ux_device_class_storage_activate)*</span></span> |
| ![Ikona dezaktywacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image42.png)    | <span data-ttu-id="949aa-192">**Dezaktywacja magazynu klasy urządzeń** *(ux_device_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-192">**Device Class Storage Deactivate** *(ux_device_class_storage_deactivate)*</span></span> |
| ![Ikona formatu magazynu klasy urządzeń](./media/user-guide/usbx-events/image43.png)    | <span data-ttu-id="949aa-194">**Format magazynu klasy urządzeń** *(ux_device_class_storage_format)*</span><span class="sxs-lookup"><span data-stu-id="949aa-194">**Device Class Storage Format** *(ux_device_class_storage_format)*</span></span> |
| ![Ikona zapytania dotyczącego magazynu klasy urządzeń](./media/user-guide/usbx-events/image44.png)    | <span data-ttu-id="949aa-196">**Zapytanie dotyczące magazynu klasy urządzeń** *(ux_device_class_storage_inquiry)*</span><span class="sxs-lookup"><span data-stu-id="949aa-196">**Device Class Storage Inquiry** *(ux_device_class_storage_inquiry)*</span></span> |
| ![Ikona wybierania trybu przechowywania klasy urządzeń](./media/user-guide/usbx-events/image45.png)    | <span data-ttu-id="949aa-198">**Tryb przechowywania klasy urządzeń** *(ux_device_class_storage_mode_select)*</span><span class="sxs-lookup"><span data-stu-id="949aa-198">**Device Class Storage Mode Select** *(ux_device_class_storage_mode_select)*</span></span> |
| ![Ikona wykrywania trybu przechowywania klasy urządzeń](./media/user-guide/usbx-events/image46.png)    | <span data-ttu-id="949aa-200">**Sens trybu przechowywania klasy urządzeń** *(ux_device_class_storage_mode_sense)*</span><span class="sxs-lookup"><span data-stu-id="949aa-200">**Device Class Storage Mode Sense** *(ux_device_class_storage_mode_sense)*</span></span> |
| ![Nie Zezwalaj na usuwanie nośnika z magazynu klasy urządzeń](./media/user-guide/usbx-events/image47.png)    | <span data-ttu-id="949aa-202">**Magazyn klasy urządzeń uniemożliwia usunięcie nośnika** *(ux_device_class_storage_prevent_allow_media_removal)*</span><span class="sxs-lookup"><span data-stu-id="949aa-202">**Device Class Storage Prevent Allow Media Removal** *(ux_device_class_storage_prevent_allow_media_removal)*</span></span> |
| ![Ikona odczytu magazynu klasy urządzeń](./media/user-guide/usbx-events/image48.png)    | <span data-ttu-id="949aa-204">**Odczyt magazynu klasy urządzeń** *(ux_device_class_storage_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-204">**Device Class Storage Read** *(ux_device_class_storage_read)*</span></span> |
| ![Ikona pojemności Odczytaj magazyn klasy urządzeń](./media/user-guide/usbx-events/image49.png)    | <span data-ttu-id="949aa-206">**Pojemność odczytu magazynu klasy urządzeń** *(ux_device_class_storage_read_capacity)*</span><span class="sxs-lookup"><span data-stu-id="949aa-206">**Device Class Storage Read Capacity** *(ux_device_class_storage_read_capacity)*</span></span> |
| ![Ikona możliwości odczytywania formatu magazynu klasy urządzeń](./media/user-guide/usbx-events/image50.png)    | <span data-ttu-id="949aa-208">**Pojemność formatu odczytu magazynu klasy urządzeń** *(ux_device_class_storage_read_format_capacity)*</span><span class="sxs-lookup"><span data-stu-id="949aa-208">**Device Class Storage Read Format Capacity** *(ux_device_class_storage_read_format_capacity)*</span></span> |
| ![Ikona odczytywania SPISu klasy urządzeń](./media/user-guide/usbx-events/image51.png)    | <span data-ttu-id="949aa-210">**Magazyn klasy urządzeń odczytywanie spisu treści** *(ux_device_class_storage_read_toc)*</span><span class="sxs-lookup"><span data-stu-id="949aa-210">**Device Class Storage Read TOC** *(ux_device_class_storage_read_toc)*</span></span> |
| ![Ikona wykrywania żądania magazynu klasy urządzeń](./media/user-guide/usbx-events/image52.png)    | <span data-ttu-id="949aa-212">**Wykrywanie żądania magazynu klasy urządzeń** *(ux_device_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="949aa-212">**Device Class Storage Request Sense** *(ux_device_class_storage_request_sense)*</span></span> |
| ![Ikona zatrzymania uruchamiania magazynu klasy urządzeń](./media/user-guide/usbx-events/image53.png)    | <span data-ttu-id="949aa-214">**Zatrzymanie uruchamiania magazynu klasy urządzeń** *(ux_device_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="949aa-214">**Device Class Storage Start Stop** *(ux_device_class_storage_start_stop)*</span></span> |
| ![Ikona gotowego testu magazynu klasy urządzeń](./media/user-guide/usbx-events/image54.png)    | <span data-ttu-id="949aa-216">**Gotowy Test magazynu klasy urządzeń** *(ux_device_class_storage_test_ready)*</span><span class="sxs-lookup"><span data-stu-id="949aa-216">**Device Class Storage Test Ready** *(ux_device_class_storage_test_ready)*</span></span> |
| ![Ikona weryfikacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image55.png)    | <span data-ttu-id="949aa-218">**Weryfikacja magazynu klasy urządzeń** *(ux_device_class_storage_verify)*</span><span class="sxs-lookup"><span data-stu-id="949aa-218">**Device Class Storage Verify** *(ux_device_class_storage_verify)*</span></span> |
| ![Ikona zapisu magazynu klasy urządzeń](./media/user-guide/usbx-events/image56.png)    | <span data-ttu-id="949aa-220">**Zapis magazynu klasy urządzeń** *(ux_device_class_storage_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-220">**Device Class Storage Write** *(ux_device_class_storage_write)*</span></span> |
| ![Ikona pobierania alternatywnego ustawienia stosu urządzeń](./media/user-guide/usbx-events/image57.png)    | <span data-ttu-id="949aa-222">**Pobieranie alternatywnego ustawienia stosu urządzeń** *(ux_device_stack_alternate_setting_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-222">**Device Stack Alternate Setting Get** *(ux_device_stack_alternate_setting_get)*</span></span> |
| ![Ikona zestawu ustawień alternatywnego stosu urządzeń](./media/user-guide/usbx-events/image58.png)    | <span data-ttu-id="949aa-224">**Zestaw ustawień alternatywnego stosu urządzeń** *(ux_device_stack_alternate_setting_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-224">**Device Stack Alternate Setting Set** *(ux_device_stack_alternate_setting_set)*</span></span> |
| ![Ikona rejestru klasy stosu urządzeń](./media/user-guide/usbx-events/image59.png)    | <span data-ttu-id="949aa-226">**Rejestr klas stosu urządzeń** *(ux_device_stack_class_register)*</span><span class="sxs-lookup"><span data-stu-id="949aa-226">**Device Stack Class Register** *(ux_device_stack_class_register)*</span></span> |
| ![Ikona czyszczenia funkcji dla stosu urządzeń](./media/user-guide/usbx-events/image60.png)    | <span data-ttu-id="949aa-228">**Funkcja czyszczenia stosu urządzeń** *(ux_device_stack_clear_feature)*</span><span class="sxs-lookup"><span data-stu-id="949aa-228">**Device Stack Clear Feature** *(ux_device_stack_clear_feature)*</span></span> |
| ![Ikona pobierania konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image61.png)    | <span data-ttu-id="949aa-230">**Pobieranie konfiguracji stosu urządzeń** *(ux_device_stack_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-230">**Device Stack Configuration Get** *(ux_device_stack_configuration_get)*</span></span> |
| ![Ikona zestawu konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image62.png)    | <span data-ttu-id="949aa-232">**Zestaw konfiguracyjny stosu urządzeń** *(ux_device_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-232">**Device Stack Configuration Set** *(ux_device_stack_configuration_set)*</span></span> |
| ![Ikona połączenia z stosem urządzeń](./media/user-guide/usbx-events/image63.png)    | <span data-ttu-id="949aa-234">**Łączenie stosu urządzeń** *(ux_device_stack_connect)*</span><span class="sxs-lookup"><span data-stu-id="949aa-234">**Device Stack Connect** *(ux_device_stack_connect)*</span></span> |
| ![Ikona wysyłania deskryptora stosu urządzeń](./media/user-guide/usbx-events/image64.png)    | <span data-ttu-id="949aa-236">**Wysyłanie deskryptora stosu urządzeń** *(ux_device_stack_descriptor_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-236">**Device Stack Descriptor Send** *(ux_device_stack_descriptor_send)*</span></span> |
| ![Ikona rozłączania stosu urządzeń](./media/user-guide/usbx-events/image65.png)    | <span data-ttu-id="949aa-238">**Rozłączenie stosu urządzeń** *(ux_device_stack_disconnect)*</span><span class="sxs-lookup"><span data-stu-id="949aa-238">**Device Stack Disconnect** *(ux_device_stack_disconnect)*</span></span> |
| ![Ikona miejsca do punktu końcowego stosu urządzeń](./media/user-guide/usbx-events/image66.png)    | <span data-ttu-id="949aa-240">**Kabina punktu końcowego stosu urządzeń** *(ux_device_stack_endpoint_stall)*</span><span class="sxs-lookup"><span data-stu-id="949aa-240">**Device Stack Endpoint Stall** *(ux_device_stack_endpoint_stall)*</span></span> |
| ![Ikona stanu pobierania stosu urządzeń](./media/user-guide/usbx-events/image67.png)    | <span data-ttu-id="949aa-242">**Pobieranie stanu stosu urządzeń** *(ux_device_stack_get_status)*</span><span class="sxs-lookup"><span data-stu-id="949aa-242">**Device Stack Get Status** *(ux_device_stack_get_status)*</span></span> |
| ![Ikona wznawiania hosta stosu urządzeń](./media/user-guide/usbx-events/image68.png)    | <span data-ttu-id="949aa-244">**Wznawianie hosta stosu urządzeń** *(ux_device_stack_host_wakeup)*</span><span class="sxs-lookup"><span data-stu-id="949aa-244">**Device Stack Host Wakeup** *(ux_device_stack_host_wakeup)*</span></span> |
| ![Ikona inicjowania stosu urządzeń](./media/user-guide/usbx-events/image69.png)    | <span data-ttu-id="949aa-246">**Inicjowanie stosu urządzeń** *(ux_device_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="949aa-246">**Device Stack Initialize** *(ux_device_stack_initialize)*</span></span> |
| ![Ikona usuwania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image70.png)    | <span data-ttu-id="949aa-248">**Usuwanie interfejsu stosu urządzeń** *(ux_device_stack_interface_delete)*</span><span class="sxs-lookup"><span data-stu-id="949aa-248">**Device Stack Interface Delete** *(ux_device_stack_interface_delete)*</span></span> |
| ![Ikona pobierania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image71.png)    | <span data-ttu-id="949aa-250">**Pobieranie interfejsu stosu urządzeń** *(ux_device_stack_interface_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-250">**Device Stack Interface Get** *(ux_device_stack_interface_get)*</span></span> |
| ![Ikona zestawu interfejsów stosu urządzeń](./media/user-guide/usbx-events/image72.png)    | <span data-ttu-id="949aa-252">**Zestaw interfejsów stosu urządzeń** *(ux_device_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-252">**Device Stack Interface Set** *(ux_device_stack_interface_set)*</span></span> |
| ![Ikona funkcji zestawu stosu urządzeń](./media/user-guide/usbx-events/image73.png)    | <span data-ttu-id="949aa-254">**Funkcja zestawu stosu urządzeń** *(ux_device_stack_set_feature)*</span><span class="sxs-lookup"><span data-stu-id="949aa-254">**Device Stack Set Feature** *(ux_device_stack_set_feature)*</span></span> |
| ![Ikona przerwania transferu stosu urządzeń](./media/user-guide/usbx-events/image74.png)    | <span data-ttu-id="949aa-256">**Przerwanie transferu stosu urządzeń** *(ux_device_stack_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="949aa-256">**Device Stack Transfer Abort** *(ux_device_stack_transfer_abort)*</span></span> |
| ![\* Ikona przetransferowania stosu urządzeń wszystkie żądanie przerwania](./media/user-guide/usbx-events/image75.png)    | <span data-ttu-id="949aa-258">**Przerwanie transferu wszystkich żądań przez stos urządzeń** *(ux_device_stack_transfer_all_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="949aa-258">**Device Stack Transfer All Request Abort** *(ux_device_stack_transfer_all_request_abort)*</span></span> |
| ![Ikona żądania transferu stosu urządzeń](./media/user-guide/usbx-events/image76.png)    | <span data-ttu-id="949aa-260">**Żądanie transferu stosu urządzeń** *(ux_device_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="949aa-260">**Device Stack Transfer Request** *(ux_device_stack_transfer_request)*</span></span> |
| ![Ikona ASIX aktywowania klasy hosta](./media/user-guide/usbx-events/image77.png)    | <span data-ttu-id="949aa-262">**ASIX Aktywuj klasy hosta** *(ux_host_class_asix_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-262">**Host Class Asix Activate** *(ux_host_class_asix_activate)*</span></span> |
| ![Ikona dezaktywowania klasy hosta ASIX](./media/user-guide/usbx-events/image78.png)    | <span data-ttu-id="949aa-264">**ASIX dezaktywować klasy hosta** *(ux_host_class_asix_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-264">**Host Class Asix Deactivate** *(ux_host_class_asix_deactivate)*</span></span> |
| ![Ikona powiadomienia o przerwaniu ASIX klasy hosta](./media/user-guide/usbx-events/image79.png)    | <span data-ttu-id="949aa-266">**ASIX — powiadomienie o przerwaniu klasy hosta** *(ux_host_class_asix_interrupt_notification)*</span><span class="sxs-lookup"><span data-stu-id="949aa-266">**Host Class Asix Interrupt Notification** *(ux_host_class_asix_interrupt_notification)*</span></span> |
| ![Ikona odczytu ASIX klasy hosta](./media/user-guide/usbx-events/image80.png)    | <span data-ttu-id="949aa-268">**ASIX odczytać klasy hosta** *(ux_host_class_asix_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-268">**Host Class Asix Read** *(ux_host_class_asix_read)*</span></span> |
| ![Ikona zapisu ASIX klasy hosta](./media/user-guide/usbx-events/image81.png)    | <span data-ttu-id="949aa-270">**ASIX zapisu klasy hosta** *(ux_host_class_asix_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-270">**Host Class Asix Write** *(ux_host_class_asix_write)*</span></span> |
| ![Ikona aktywacji dźwięku klasy hosta](./media/user-guide/usbx-events/image82.png)    | <span data-ttu-id="949aa-272">**Aktywacja audio klasy hosta** *(ux_host_class_audio_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-272">**Host Class Audio Activate** *(ux_host_class_audio_activate)*</span></span> |
| ![Ikona pobierania wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image83.png)    | <span data-ttu-id="949aa-274">**Pobieranie wartości kontrolki audio klasy hosta** *(ux_host_class_audio_control_value_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-274">**Host Class Audio Control Value Get** *(ux_host_class_audio_control_value_get)*</span></span> |
| ![Ikona zestawu wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image84.png)    | <span data-ttu-id="949aa-276">**Zestaw wartości kontrolki audio klasy hosta** *(ux_host_class_audio_control_value_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-276">**Host Class Audio Control Value Set** *(ux_host_class_audio_control_value_set)*</span></span> |
| ![Ikona dezaktywacji audio klasy hosta](./media/user-guide/usbx-events/image85.png)    | <span data-ttu-id="949aa-278">**Dezaktywacja audio klasy hosta** *(ux_host_class_audio_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-278">**Host Class Audio Deactivate** *(ux_host_class_audio_deactivate)*</span></span> |
| ![Ikona odczytu audio klasy hosta](./media/user-guide/usbx-events/image86.png)    | <span data-ttu-id="949aa-280">**Odczytaj audio klasy hosta** *(ux_host_class_audio_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-280">**Host Class Audio Read** *(ux_host_class_audio_read)*</span></span> |
| ![Ikona pobierania próbkowania audio klasy hosta](./media/user-guide/usbx-events/image87.png)    | <span data-ttu-id="949aa-282">Pobieranie **próbkowania strumieniowego audio klasy hosta** *(ux_host_class_audio_streaming_sampling_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-282">**Host Class Audio Streaming Sampling Get** *(ux_host_class_audio_streaming_sampling_get)*</span></span> |
| ![Ikona zestawu próbkowania przesyłania strumieniowego audio klasy hosta](./media/user-guide/usbx-events/image88.png)    | <span data-ttu-id="949aa-284">**Zestaw próbkowania przesyłania strumieniowego audio klasy hosta** *(ux_host_class_audio_streaming_sampling_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-284">**Host Class Audio Streaming Sampling Set** *(ux_host_class_audio_streaming_sampling_set)*</span></span> |
| ![Ikona zapisu audio klasy hosta](./media/user-guide/usbx-events/image89.png)    | <span data-ttu-id="949aa-286">**Zapis audio klasy hosta** *(ux_host_class_audio_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-286">**Host Class Audio Write** *(ux_host_class_audio_write)*</span></span> |
| ![Klasa hosta C D C A C M ikona aktywacji](./media/user-guide/usbx-events/image90.png)    | <span data-ttu-id="949aa-288">**Klasa hosta Przeprowadź aktywację ACM** *(ux_host_class_cdc_acm_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-288">**Host Class Cdc Acm Activate** *(ux_host_class_cdc_acm_activate)*</span></span> |
| ![Klasa hosta C D C A C M ikona dezaktywowania](./media/user-guide/usbx-events/image91.png)    | <span data-ttu-id="949aa-290">**Klasa hosta — dezaktywowanie ACM** *(ux_host_class_cdc_acm_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-290">**Host Class Cdc Acm Deactivate** *(ux_host_class_cdc_acm_deactivate)*</span></span> |
| ![Klasa hosta C D C A c M I O C T L na ikonie potoku](./media/user-guide/usbx-events/image92.png)    | <span data-ttu-id="949aa-292">**Klasa hosta — przerwanie operacji IOCTL w potoku** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="949aa-292">**Host Class Cdc Acm Ioctl Abort In Pipe** *(ux_host_class_cdc_acm_ioctl_abort_in_pipe)*</span></span> |
| ![Klasa hosta C D C A c M I O c T L ikona przerwania](./media/user-guide/usbx-events/image93.png)    | <span data-ttu-id="949aa-294">**Klasa hosta Przerzucanie** danych funkcji IOCTL dla operacji przechwytywania *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="949aa-294">**Host Class Cdc Acm Ioctl Abort Out Pipe** *(ux_host_class_cdc_acm_ioctl_abort_out_pipe)*</span></span> |
| ![Klasa hosta C D C A c M I O C T L Pobierz ikonę stanu urządzenia](./media/user-guide/usbx-events/image94.png)    | <span data-ttu-id="949aa-296">**Klasa hosta przechwytywania żądania IOCTL pobieranie stanu urządzenia** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="949aa-296">**Host Class Cdc Acm Ioctl Get Device Status** *(ux_host_class_cdc_acm_ioctl_get_device_status)*</span></span> |
| ![Klasa hosta C D C A c M I O C T L ikona Uzyskaj kodowanie wiersza](./media/user-guide/usbx-events/image95.png)    | <span data-ttu-id="949aa-298">**Klasa hosta przechwytywania operacji IOCTL Get line kodowania** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="949aa-298">**Host Class Cdc Acm Ioctl Get Line Coding** *(ux_host_class_cdc_acm_ioctl_get_line_coding)*</span></span> |
| ![Klasa hosta C D C A c M I O c T L ikona wywołania zwrotnego powiadomienia](./media/user-guide/usbx-events/image96.png)    | <span data-ttu-id="949aa-300">**Wywołanie zwrotne powiadomień IOCTL klasy hosta** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span><span class="sxs-lookup"><span data-stu-id="949aa-300">**Host Class Cdc Acm Ioctl Notification Callback** *(ux_host_class_cdc_acm_ioctl_notification_callback)*</span></span> |
| ![Klasa hosta C D C A c M I O C T L ikona przerwania wysyłania](./media/user-guide/usbx-events/image97.png)    | <span data-ttu-id="949aa-302">**Klasa hosta — przerwanie wysyłania żądania IOCTL** *(ux_host_class_cdc_acm_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="949aa-302">**Host Class Cdc Acm Ioctl Send Break** *(ux_host_class_cdc_acm_ioctl_send_break)*</span></span> |
| ![Klasa hosta C D C A c M I O c T L ikona kodowania wierszy](./media/user-guide/usbx-events/image98.png)    | <span data-ttu-id="949aa-304">**Klasa hosta — kodowanie liniowe zestawu IOCTL ACM** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="949aa-304">**Host Class Cdc Acm Ioctl Set Line Coding** *(ux_host_class_cdc_acm_ioctl_set_line_coding)*</span></span> |
| ![Klasa hosta C D C A c M I O C T L ikona stanu wiersza](./media/user-guide/usbx-events/image99.png)    | <span data-ttu-id="949aa-306">**Klasa hosta: stan wiersza zestawu IOCTL ACM** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="949aa-306">**Host Class Cdc Acm Ioctl Set Line State** *(ux_host_class_cdc_acm_ioctl_set_line_state)*</span></span> |
| ![Klasa hosta C D C A C M ikona odczytu](./media/user-guide/usbx-events/image100.png)    | <span data-ttu-id="949aa-308">**Klasa hosta przechwytywania danych ACM** *(ux_host_class_cdc_acm_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-308">**Host Class Cdc Acm Read** *(ux_host_class_cdc_acm_read)*</span></span> |
| ![Klasa hosta C D C A p M — ikona startowa przyjęcia](./media/user-guide/usbx-events/image101.png)    | <span data-ttu-id="949aa-310">**Rozpoczęcie odbioru ACM klasy hosta** *(ux_host_class_cdc_acm_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="949aa-310">**Host Class Cdc Acm Reception Start** *(ux_host_class_cdc_acm_reception_start)*</span></span> |
| ![Klasa hosta C D C, ikona zatrzymania odbierania C M](./media/user-guide/usbx-events/image102.png)    | <span data-ttu-id="949aa-312">**Klasa hosta** przełączać do przechwytywania Acm *(ux_host_class_cdc_acm_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="949aa-312">**Host Class Cdc Acm Reception Stop** *(ux_host_class_cdc_acm_reception_stop)*</span></span> |
| ![Klasa hosta C D C A C M ikona zapisu](./media/user-guide/usbx-events/image103.png)    | <span data-ttu-id="949aa-314">**Klasa hosta** przeprzechwytywanie do Acm *(ux_host_class_cdc_acm_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-314">**Host Class Cdc Acm Write** *(ux_host_class_cdc_acm_write)*</span></span> |
| ![Ikona Dpump aktywowania klasy hosta](./media/user-guide/usbx-events/image104.png)    | <span data-ttu-id="949aa-316">**Dpump Aktywuj klasy hosta** *(ux_host_class_dpump_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-316">**Host Class Dpump Activate** *(ux_host_class_dpump_activate)*</span></span> |
| ![Ikona dezaktywowania klasy hosta Dpump](./media/user-guide/usbx-events/image105.png)    | <span data-ttu-id="949aa-318">**Dpump dezaktywować klasy hosta** *(ux_host_class_dpump_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-318">**Host Class Dpump Deactivate** *(ux_host_class_dpump_deactivate)*</span></span> |
| ![Ikona odczytu Dpump klasy hosta](./media/user-guide/usbx-events/image106.png)    | <span data-ttu-id="949aa-320">**Dpump odczytać klasy hosta** *(ux_host_class_dpump_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-320">**Host Class Dpump Read** *(ux_host_class_dpump_read)*</span></span> |
| ![Ikona zapisu Dpump klasy hosta](./media/user-guide/usbx-events/image107.png)    | <span data-ttu-id="949aa-322">**Dpump zapisu klasy hosta** *(ux_host_class_dpump_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-322">**Host Class Dpump Write** *(ux_host_class_dpump_write)*</span></span> |
| ![Ikona aktywacji klasy hosta HID](./media/user-guide/usbx-events/image108.png)    | <span data-ttu-id="949aa-324">**Aktywacja klasy hosta HID** *(ux_host_class_hid_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-324">**Host Class Hid Activate** *(ux_host_class_hid_activate)*</span></span> |
| ![Ikona rejestracji klienta HID klasy hosta](./media/user-guide/usbx-events/image109.png)    | <span data-ttu-id="949aa-326">**Rejestr klienta HID klasy hosta** *(ux_host_class_hid_client_register)*</span><span class="sxs-lookup"><span data-stu-id="949aa-326">**Host Class Hid Client Register** *(ux_host_class_hid_client_register)*</span></span> |
| ![Ikona dezaktywacji klasy hosta HID](./media/user-guide/usbx-events/image110.png)    | <span data-ttu-id="949aa-328">**Dezaktywowanie klasy hosta HID** *(ux_host_class_hid_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-328">**Host Class Hid Deactivate** *(ux_host_class_hid_deactivate)*</span></span> |
| ![Ikona uzyskiwania bezczynności HID klasy hosta](./media/user-guide/usbx-events/image111.png)    | <span data-ttu-id="949aa-330">**Pobieranie z trybu bezczynności HID klasy hosta** *(ux_host_class_hid_idle_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-330">**Host Class Hid Idle Get** *(ux_host_class_hid_idle_get)*</span></span> |
| ![Ikona zestawu bezczynności HID klasy hosta](./media/user-guide/usbx-events/image112.png)    | <span data-ttu-id="949aa-332">**Zestaw bezczynny HID klasy hosta** *(ux_host_class_hid_idle_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-332">**Host Class Hid Idle Set** *(ux_host_class_hid_idle_set)*</span></span> |
| ![Ikona aktywacji klasy hosta HID](./media/user-guide/usbx-events/image113.png)    | <span data-ttu-id="949aa-334">**Aktywuj klasy hosta klawiatury HID** *(ux_host_class_hid_keyboard_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-334">**Host Class Hid Keyboard Activate** *(ux_host_class_hid_keyboard_activate)*</span></span> |
| ![Ikona dezaktywacji klawiatury HID klasy hosta](./media/user-guide/usbx-events/image114.png)    | <span data-ttu-id="949aa-336">**Dezaktywacja klasy hosta klawiatury HID** *(ux_host_class_hid_keyboard_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-336">**Host Class Hid Keyboard Deactivate** *(ux_host_class_hid_keyboard_deactivate)*</span></span> |
| ![Ikona aktywacji kursora myszy klasy hosta HID](./media/user-guide/usbx-events/image115.png)    | <span data-ttu-id="949aa-338">**Aktywacja myszy klasy hosta HID** *(ux_host_class_hid_mouse_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-338">**Host Class Hid Mouse Activate** *(ux_host_class_hid_mouse_activate)*</span></span> |
| ![Ikona dezaktywacji myszy klasy hosta HID](./media/user-guide/usbx-events/image116.png)    | <span data-ttu-id="949aa-340">**Dezaktywacja myszy klasy hosta** *(ux_host_class_hid_mouse_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-340">**Host Class Hid Mouse Deactivate** *(ux_host_class_hid_mouse_deactivate)*</span></span> |
| ![Ikona aktywacji zdalnej kontroli HID klasy hosta](./media/user-guide/usbx-events/image117.png)    | <span data-ttu-id="949aa-342">**Aktywacja zdalnego sterowania HID klasy hosta** *(ux_host_class_hid_remote_control_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-342">**Host Class Hid Remote Control Activate** *(ux_host_class_hid_remote_control_activate)*</span></span> |
| ![Ikona dezaktywowania zdalnego sterowania kontrolką klasy hosta](./media/user-guide/usbx-events/image118.png)    | <span data-ttu-id="949aa-344">**Dezaktywacja zdalnego sterowania HID klasy hosta** *(ux_host_class_hid_remote_control_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-344">**Host Class Hid Remote Control Deactivate** *(ux_host_class_hid_remote_control_deactivate)*</span></span> |
| ![Ikona pobierania raportu HID klasy hosta](./media/user-guide/usbx-events/image119.png)    | <span data-ttu-id="949aa-346">**Pobieranie raportu HID klasy hosta** *(ux_host_class_hid_report_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-346">**Host Class Hid Report Get** *(ux_host_class_hid_report_get)*</span></span> |
| ![Ikona zestawu raportów HID klasy hosta](./media/user-guide/usbx-events/image120.png)    | <span data-ttu-id="949aa-348">**Zestaw raportów HID klasy hosta** *(ux_host_class_hid_report_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-348">**Host Class Hid Report Set** *(ux_host_class_hid_report_set)*</span></span> |
| ![Ikona aktywowania centrum klasy hosta](./media/user-guide/usbx-events/image121.png)    | <span data-ttu-id="949aa-350">**Aktywowanie centrum klasy hosta** *(ux_host_class_hub_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-350">**Host Class Hub Activate** *(ux_host_class_hub_activate)*</span></span> |
| ![Ikona wykrywania zmian centrum klasy hosta](./media/user-guide/usbx-events/image122.png)    | <span data-ttu-id="949aa-352">**Wykrywanie zmian centrum klasy hosta** *(ux_host_class_hub_change_detect)*</span><span class="sxs-lookup"><span data-stu-id="949aa-352">**Host Class Hub Change Detect** *(ux_host_class_hub_change_detect)*</span></span> |
| ![\* Ikona dezaktywacji centrum klasy hosta](./media/user-guide/usbx-events/image123.png)    | <span data-ttu-id="949aa-354">**Dezaktywacja centrum klasy hosta** *(ux_host_class_hub_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-354">**Host Class Hub Deactivate** *(ux_host_class_hub_deactivate)*</span></span> |
| ![Ikona procesu połączenia zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image124.png)    | <span data-ttu-id="949aa-356">**Proces połączenia zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_connection_process)*</span><span class="sxs-lookup"><span data-stu-id="949aa-356">**Host Class Hub Port Change Connection Process** *(ux_host_class_hub_port_change_connection_process)*</span></span> |
| ![Ikona włączenia procesu zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image125.png)    | <span data-ttu-id="949aa-358">**Proces włączania zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_enable_process)*</span><span class="sxs-lookup"><span data-stu-id="949aa-358">**Host Class Hub Port Change Enable Process** *(ux_host_class_hub_port_change_enable_process)*</span></span> |
| ![Ikona hosta zmień port koncentratora na bieżący proces](./media/user-guide/usbx-events/image126.png)    | <span data-ttu-id="949aa-360">**Zmiana portu centrum klasy hosta na bieżący proces** *(ux_host_class_hub_port_change_over_current_process)*</span><span class="sxs-lookup"><span data-stu-id="949aa-360">**Host Class Hub Port Change Over Current Process** *(ux_host_class_hub_port_change_over_current_process)*</span></span> |
| ![Ikona procesu resetowania zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image127.png)    | <span data-ttu-id="949aa-362">**Proces resetowania zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_reset_process)*</span><span class="sxs-lookup"><span data-stu-id="949aa-362">**Host Class Hub Port Change Reset Process** *(ux_host_class_hub_port_change_reset_process)*</span></span> |
| ![Ikona procesu wstrzymania zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image128.png)    | <span data-ttu-id="949aa-364">**Proces wstrzymywania zmiany portu centrum klasy hosta** *(ux_host_class_hub_port_change_suspend_process)*</span><span class="sxs-lookup"><span data-stu-id="949aa-364">**Host Class Hub Port Change Suspend Process** *(ux_host_class_hub_port_change_suspend_process)*</span></span> |
| ![Ikona Pima aktywowania klasy hosta](./media/user-guide/usbx-events/image129.png)    | <span data-ttu-id="949aa-366">**Pima Aktywuj klasy hosta** *(ux_host_class_prima_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-366">**Host Class Pima Activate** *(ux_host_class_prima_activate)*</span></span> |
| ![Ikona dezaktywowania klasy hosta Pima](./media/user-guide/usbx-events/image130.png)    | <span data-ttu-id="949aa-368">**Pima dezaktywować klasy hosta** *(ux_host_class_pima_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-368">**Host Class Pima Deactivate** *(ux_host_class_pima_deactivate)*</span></span> |
| ![Ikona uzyskiwania informacji o urządzeniu klasy hosta Pima](./media/user-guide/usbx-events/image131.png)    | <span data-ttu-id="949aa-370">**Pobieranie informacji o urządzeniu klasy hosta Pima** *(ux_host_class_pima_device_info_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-370">**Host Class Pima Device Info Get** *(ux_host_class_pima_device_info_get)*</span></span> |
| ![Ikona resetowania urządzenia Pima klasy hosta](./media/user-guide/usbx-events/image132.png)    | <span data-ttu-id="949aa-372">**Klasa hosta Pima Resetowanie urządzenia** *(ux_host_class_pima_device_reset)*</span><span class="sxs-lookup"><span data-stu-id="949aa-372">**Host Class Pima Device Reset** *(ux_host_class_pima_device_reset)*</span></span> |
| ![Ikona powiadomienia Pima klasy hosta](./media/user-guide/usbx-events/image133.png)    | <span data-ttu-id="949aa-374">**Pima — powiadomienie o klasie hosta** *(ux_host_class_pima_notification)*</span><span class="sxs-lookup"><span data-stu-id="949aa-374">**Host Class Pima Notification** *(ux_host_class_pima_notification)*</span></span> |
| ![Ikona pobierania obiektów Pima klasy hosta](./media/user-guide/usbx-events/image134.png)    | <span data-ttu-id="949aa-376">**Pobieranie obiektów Number Pima klasy hosta** *(ux_host_class_pima_num_objects_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-376">**Host Class Pima Number Objects Get** *(ux_host_class_pima_num_objects_get)*</span></span> |
| ![Ikona zamykania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image135.png)    | <span data-ttu-id="949aa-378">**Zamknięto obiekt Pima klasy hosta** *(ux_host_class_pima_object_close)*</span><span class="sxs-lookup"><span data-stu-id="949aa-378">**Host Class Pima Object Close** *(ux_host_class_pima_object_close)*</span></span> |
| ![Ikona kopiowania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image136.png)    | <span data-ttu-id="949aa-380">**Kopia obiektu Pima klasy hosta** *(ux_host_class_pima_object_copy)*</span><span class="sxs-lookup"><span data-stu-id="949aa-380">**Host Class Pima Object Copy** *(ux_host_class_pima_object_copy)*</span></span> |
| ![Ikona usuwania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image137.png)    | <span data-ttu-id="949aa-382">**Usuwanie obiektu Pima klasy hosta** *(ux_host_class_pima_object_delete)*</span><span class="sxs-lookup"><span data-stu-id="949aa-382">**Host Class Pima Object Delete** *(ux_host_class_pima_object_delete)*</span></span> |
| ![Ikona pobierania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image138.png)    | <span data-ttu-id="949aa-384">**Pobieranie obiektu Pima klasy hosta** *(ux_host_class_pima_object_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-384">**Host Class Pima Object Get** *(ux_host_class_pima_object_get)*</span></span> |
| ![Ikona uzyskiwania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image139.png)    | <span data-ttu-id="949aa-386">**Pobieranie informacji o obiekcie Pima klasy hosta** *(ux_host_class_pima_object_info_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-386">**Host Class Pima Object Info Get** *(ux_host_class_pima_object_info_get)*</span></span> |
| ![Ikona wysyłania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image140.png)    | <span data-ttu-id="949aa-388">**Wysyłanie informacji o obiekcie Pima klasy hosta** *(ux_host_class_pima_object_info_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-388">**Host Class Pima Object Info Send** *(ux_host_class_pima_object_info_send)*</span></span> |
| ![Ikona przenoszenia obiektu Pima klasy hosta](./media/user-guide/usbx-events/image141.png)    | <span data-ttu-id="949aa-390">**Przeniesienie obiektu Pima klasy hosta** *(ux_host_class_pima_object_move)*</span><span class="sxs-lookup"><span data-stu-id="949aa-390">**Host Class Pima Object Move** *(ux_host_class_pima_object_move)*</span></span> |
| ![Ikona wysyłania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image142.png)    | <span data-ttu-id="949aa-392">**Wysyłanie obiektu Pima klasy hosta** *(ux_host_class_pima_object_send)*</span><span class="sxs-lookup"><span data-stu-id="949aa-392">**Host Class Pima Object Send** *(ux_host_class_pima_object_send)*</span></span> |
| ![Ikona przerwania transferu obiektu klasy hosta Pima](./media/user-guide/usbx-events/image143.png)    | <span data-ttu-id="949aa-394">**Przerwanie transferu obiektu Pima klasy hosta** *(ux_host_class_object_transfer_abort)*</span><span class="sxs-lookup"><span data-stu-id="949aa-394">**Host Class Pima Object Transfer Abort** *(ux_host_class_object_transfer_abort)*</span></span> |
| ![Ikona odczytu Pima klasy hosta](./media/user-guide/usbx-events/image144.png)    | <span data-ttu-id="949aa-396">**Pima odczytać klasy hosta** *(ux_host_class_pima_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-396">**Host Class Pima Read** *(ux_host_class_pima_read)*</span></span> |
| ![Ikona anulowania żądania Pima klasy hosta](./media/user-guide/usbx-events/image145.png)    | <span data-ttu-id="949aa-398">**Żądanie anulowania klasy hosta Pima** *(ux_host_class_pima_request_cancel)*</span><span class="sxs-lookup"><span data-stu-id="949aa-398">**Host Class Pima Request Cancel** *(ux_host_class_pima_request_cancel)*</span></span> |
| ![Ikona zamykania sesji Pima dla klasy hosta](./media/user-guide/usbx-events/image146.png)    | <span data-ttu-id="949aa-400">**Zamknięcie sesji Pima** *(Ux_host_class_pima_session_close)* klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-400">**Host Class Pima Session Close** *(ux_host_class_pima_session_close)*</span></span> |
| ![Ikona Otwórz sesję Pima sesji hosta](./media/user-guide/usbx-events/image147.png)    | <span data-ttu-id="949aa-402">**Pima sesji hosta** *(ux_host_class_pima_session_open)*</span><span class="sxs-lookup"><span data-stu-id="949aa-402">**Host Class Pima Session Open** *(ux_host_class_pima_session_open)*</span></span> |
| ![Ikona pobierania identyfikatorów magazynu Pima klasy hosta](./media/user-guide/usbx-events/image148.png)    | <span data-ttu-id="949aa-404">**Pobieranie identyfikatorów magazynu Pima klasy hosta** *(ux_host_class_pima_storage_ids_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-404">**Host Class Pima Storage Ids Get** *(ux_host_class_pima_storage_ids_get)*</span></span> |
| ![Ikona pobierania informacji o magazynie Pima klasy hosta](./media/user-guide/usbx-events/image149.png)    | <span data-ttu-id="949aa-406">**Pobieranie informacji o magazynie Pima klasy hosta** *(ux_host_class_pima_storage_info_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-406">**Host Class Pima Storage Info Get** *(ux_host_class_pima_storage_info_get)*</span></span> |
| ![Ikona pobierania Pima klasy hosta](./media/user-guide/usbx-events/image150.png)    | <span data-ttu-id="949aa-408">**Pobieranie klasy hosta Pima kciuka** *(ux_host_class_pima_thumb_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-408">**Host Class Pima Thumb Get** *(ux_host_class_pima_thumb_get)*</span></span> |
| ![Ikona zapisu Pima klasy hosta](./media/user-guide/usbx-events/image151.png)    | <span data-ttu-id="949aa-410">**Pima zapisu klasy hosta** *(ux_host_class_pima_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-410">**Host Class Pima Write** *(ux_host_class_pima_write)*</span></span> |
| ![Ikona aktywowania drukarki klasy hosta](./media/user-guide/usbx-events/image152.png)    | <span data-ttu-id="949aa-412">**Aktywuj drukarkę klasy hosta** *(ux_host_class_printer_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-412">**Host Class Printer Activate** *(ux_host_class_printer_activate)*</span></span> |
| ![Ikona dezaktywacji drukarki klasy hosta](./media/user-guide/usbx-events/image153.png)    | <span data-ttu-id="949aa-414">**Dezaktywacja drukarki klasy hosta** *(ux_host_class_printer_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-414">**Host Class Printer Deactivate** *(ux_host_class_printer_deactivate)*</span></span> |
| ![Ikona pobierania nazwy drukarki klasy hosta](./media/user-guide/usbx-events/image154.png)    | <span data-ttu-id="949aa-416">**Pobierz nazwę drukarki klasy hosta** *(ux_host_class_printer_name_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-416">**Host Class Printer Name Get** *(ux_host_class_printer_name_get)*</span></span> |
| ![Ikona odczytu drukarki klasy hosta](./media/user-guide/usbx-events/image155.png)    |  <span data-ttu-id="949aa-418">**Odczytaj drukarkę klasy hosta** *(ux_host_class_printer_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-418">**Host Class Printer Read** *(ux_host_class_printer_read)*</span></span> |
| ![Ikona resetowania nietrwałego drukarki klasy hosta](./media/user-guide/usbx-events/image156.png)    | <span data-ttu-id="949aa-420">**Nietrwałe Resetowanie drukarki klasy hosta** *(ux_host_class_printer_soft_reset)*</span><span class="sxs-lookup"><span data-stu-id="949aa-420">**Host Class Printer Soft Reset** *(ux_host_class_printer_soft_reset)*</span></span> |
| ![Ikona pobierania stanu drukarki klasy hosta](./media/user-guide/usbx-events/image157.png)    | <span data-ttu-id="949aa-422">**Pobieranie stanu drukarki klasy hosta** *(ux_host_class_printer_status_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-422">**Host Class Printer Status Get** *(ux_host_class_printer_status_get)*</span></span> |
| ![Ikona zapisu drukarki klasy hosta](./media/user-guide/usbx-events/image158.png)    | <span data-ttu-id="949aa-424">**Zapis drukarki klasy hosta** *(ux_host_class_printer_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-424">**Host Class Printer Write** *(ux_host_class_printer_write)*</span></span> |
| ![Ikona mnóstwo aktywowania klasy hosta](./media/user-guide/usbx-events/image159.png)    | <span data-ttu-id="949aa-426">**Mnóstwo Aktywuj klasy hosta** *(ux_host_class_prolific_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-426">**Host Class Prolific Activate** *(ux_host_class_prolific_activate)*</span></span> |
| ![Ikona dezaktywowania klasy hosta mnóstwo](./media/user-guide/usbx-events/image160.png)    | <span data-ttu-id="949aa-428">**Mnóstwo dezaktywować klasy hosta** *(ux_host_class_prolific_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-428">**Host Class Prolific Deactivate** *(ux_host_class_prolific_deactivate)*</span></span> |
| ![Ikona potoku mnóstwo I O przerwanie klasy hosta](./media/user-guide/usbx-events/image161.png)    | <span data-ttu-id="949aa-430">**Przerwano mnóstwo operacji IOCTL klasy hosta w potoku** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span><span class="sxs-lookup"><span data-stu-id="949aa-430">**Host Class Prolific Ioctl Abort In Pipe** *(ux_host_class_prolific_ioctl_abort_in_pipe)*</span></span> |
| ![Mnóstwo klasy hosta — ikona przerwania rozgałęzienia I O C T L](./media/user-guide/usbx-events/image162.png)    | <span data-ttu-id="949aa-432">**Klasa hosta mnóstwo IOCTL przerywanie potoku** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span><span class="sxs-lookup"><span data-stu-id="949aa-432">**Host Class Prolific Ioctl Abort Out Pipe** *(ux_host_class_prolific_ioctl_abort_out_pipe)*</span></span> |
| ![Mnóstwo klasy hosta — ikona stanu urządzenia I O C T L](./media/user-guide/usbx-events/image163.png)    | <span data-ttu-id="949aa-434">**Klasa hosta mnóstwo IOCTL pobieranie stanu urządzenia** *(ux_host_class_prolific_ioctl_get_device_status)*</span><span class="sxs-lookup"><span data-stu-id="949aa-434">**Host Class Prolific Ioctl Get Device Status** *(ux_host_class_prolific_ioctl_get_device_status)*</span></span> |
| ![Ikona "Pobierz kodowanie wiersza" klasy hosta mnóstwo I O C T L](./media/user-guide/usbx-events/image164.png)    | <span data-ttu-id="949aa-436">**Klasa hosta mnóstwo IOCTL pobieranie kodu** kreskowego *(ux_host_class_prolific_ioctl_get_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="949aa-436">**Host Class Prolific Ioctl Get Line Coding** *(ux_host_class_prolific_ioctl_get_line_coding)*</span></span> |
| ![Ikona przeczyszczania klasy hosta mnóstwo I O C T L](./media/user-guide/usbx-events/image165.png)    | <span data-ttu-id="949aa-438">**Mnóstwo — przeczyszczanie klasy hosta** *(ux_host_class_prolific_ioctl_purge)*</span><span class="sxs-lookup"><span data-stu-id="949aa-438">**Host Class Prolific Ioctl Purge** *(ux_host_class_prolific_ioctl_purge)*</span></span> |
| ![Mnóstwo klasy hosta — ikona zmiany stanu urządzenia I O C](./media/user-guide/usbx-events/image166.png)    | <span data-ttu-id="949aa-440">**Zmiana stanu urządzenia raportu IOCTL klasy hosta mnóstwo** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span><span class="sxs-lookup"><span data-stu-id="949aa-440">**Host Class Prolific Ioctl Report Device Status Change** *(ux_host_class_prolific_ioctl_report_device_status_change)*</span></span> |
| ![Mnóstwo klasy hosta — ikona przerwania wysyłania I O T L](./media/user-guide/usbx-events/image167.png)    | <span data-ttu-id="949aa-442">**Mnóstwo: przerwanie wysyłania elementu IOCTL klasy hosta** *(ux_host_class_prolific_ioctl_send_break)*</span><span class="sxs-lookup"><span data-stu-id="949aa-442">**Host Class Prolific Ioctl Send Break** *(ux_host_class_prolific_ioctl_send_break)*</span></span> |
| ![Mnóstwo klasy hosta — ikona kodowania linii I O C T L](./media/user-guide/usbx-events/image168.png)    | <span data-ttu-id="949aa-444">**Kodowanie liniowe zestawu poleceń IOCTL klasy hosta mnóstwo** *(ux_host_class_prolific_ioctl_set_line_coding)*</span><span class="sxs-lookup"><span data-stu-id="949aa-444">**Host Class Prolific Ioctl Set Line Coding** *(ux_host_class_prolific_ioctl_set_line_coding)*</span></span> |
| ![Mnóstwo klasy hosta — ikona stanu wiersza I O C T L](./media/user-guide/usbx-events/image169.png)    | <span data-ttu-id="949aa-446">**Stan wiersza mnóstwo zestawu IOCTL klasy hosta** *(ux_host_class_prolific_ioctl_set_line_state)*</span><span class="sxs-lookup"><span data-stu-id="949aa-446">**Host Class Prolific Ioctl Set Line State** *(ux_host_class_prolific_ioctl_set_line_state)*</span></span> |
| ![Ikona odczytu mnóstwo klasy hosta](./media/user-guide/usbx-events/image170.png)    | <span data-ttu-id="949aa-448">**Mnóstwo odczytać klasy hosta** *(ux_host_class_prolific_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-448">**Host Class Prolific Read** *(ux_host_class_prolific_read)*</span></span> |
| ![Ikona startowa odbioru mnóstwo klasy hosta](./media/user-guide/usbx-events/image171.png)    | <span data-ttu-id="949aa-450">**Rozpoczęcie odbioru mnóstwo klasy hosta** *(ux_host_class_prolific_reception_start)*</span><span class="sxs-lookup"><span data-stu-id="949aa-450">**Host Class Prolific Reception Start** *(ux_host_class_prolific_reception_start)*</span></span> |
| ![Ikona zatrzymania odbierania mnóstwo klasy hosta](./media/user-guide/usbx-events/image172.png)    | <span data-ttu-id="949aa-452">**Zatrzymanie odbierania mnóstwo klasy hosta** *(ux_host_class_prolific_reception_stop)*</span><span class="sxs-lookup"><span data-stu-id="949aa-452">**Host Class Prolific Reception Stop** *(ux_host_class_prolific_reception_stop)*</span></span> |
| ![Ikona zapisu mnóstwo klasy hosta](./media/user-guide/usbx-events/image173.png)    | <span data-ttu-id="949aa-454">**Mnóstwo zapisu klasy hosta** *(ux_host_class_prolific_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-454">**Host Class Prolific Write** *(ux_host_class_prolific_write)*</span></span> |
| ![Ikona aktywowania magazynu klasy hosta](./media/user-guide/usbx-events/image174.png)    | <span data-ttu-id="949aa-456">**Aktywuj magazyn klas hosta** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-456">**Host Class Storage Activate** *(ux_host_class_storage_activate)*</span></span> |
| ![Ikona dezaktywacji magazynu klasy hosta](./media/user-guide/usbx-events/image175.png)    | <span data-ttu-id="949aa-458">**Dezaktywacja magazynu klasy hosta** (*ux_host_class_storage_deactivate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-458">**Host Class Storage Deactivate** (*ux_host_class_storage_deactivate)*</span></span> |
| ![Ikona pobierania pojemności nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image176.png)    | <span data-ttu-id="949aa-460">**Pobieranie pojemności nośnika magazynu klasy hosta** *(ux_host_class_storage_media_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-460">**Host Class Storage Media Capacity Get** *(ux_host_class_storage_media_capacity_get)*</span></span> |
| ![Ikona pobierania pojemności formatu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image177.png)    | <span data-ttu-id="949aa-462">**Pobieranie pojemności formatu nośnika magazynu klasy hosta** *(ux_host_class_storage_media_format_capacity_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-462">**Host Class Storage Media Format Capacity Get** *(ux_host_class_storage_media_format_capacity_get)*</span></span> |
| ![Ikona instalacji nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image178.png)    | <span data-ttu-id="949aa-464">**Instalacja nośnika magazynu klasy hosta** (ux_host_class_storage_media_mount) \*</span><span class="sxs-lookup"><span data-stu-id="949aa-464">**Host Class Storage Media Mount** (ux_host_class_storage_media_mount)\*</span></span> |
| ![Ikona otwierania nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image179.png)    | <span data-ttu-id="949aa-466">**Otwórz nośnik magazynu klasy hosta** *(ux_host_class_storage_media_open)*</span><span class="sxs-lookup"><span data-stu-id="949aa-466">**Host Class Storage Media Open** *(ux_host_class_storage_media_open)*</span></span> |
| ![Ikona odczytu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image180.png)    | <span data-ttu-id="949aa-468">**Odczyt nośnika magazynu klasy hosta** *(ux_host_class_storage_media_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-468">**Host Class Storage Media Read** *(ux_host_class_storage_media_read)*</span></span> |
| ![Ikona zapisu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image181.png)    | <span data-ttu-id="949aa-470">**Zapis nośnika magazynu klasy hosta** *(ux_host_class_storage_media_write)*</span><span class="sxs-lookup"><span data-stu-id="949aa-470">**Host Class Storage Media Write** *(ux_host_class_storage_media_write)*</span></span> |
| ![Ikona wykrywania żądań magazynu klasy hosta](./media/user-guide/usbx-events/image182.png)    | <span data-ttu-id="949aa-472">**Sens żądania magazynu klasy hosta** *(ux_host_class_storage_request_sense)*</span><span class="sxs-lookup"><span data-stu-id="949aa-472">**Host Class Storage Request Sense** *(ux_host_class_storage_request_sense)*</span></span> |
| ![Ikona zatrzymania uruchamiania magazynu klasy hosta](./media/user-guide/usbx-events/image183.png)    | <span data-ttu-id="949aa-474">**Zatrzymanie uruchamiania magazynu klasy hosta** *(ux_host_class_storage_start_stop)*</span><span class="sxs-lookup"><span data-stu-id="949aa-474">**Host Class Storage Start Stop** *(ux_host_class_storage_start_stop)*</span></span> |
| ![Ikona testowania gotowej jednostki magazynu klasy hosta](./media/user-guide/usbx-events/image184.png)    | <span data-ttu-id="949aa-476">**Gotowy test jednostki magazynu klasy hosta** *(ux_host_class_storage_activate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-476">**Host Class Storage Unit Ready Test** *(ux_host_class_storage_activate)*</span></span> |
| ![Ikona tworzenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image185.png)    | <span data-ttu-id="949aa-478">**Tworzenie wystąpienia klasy stosu hosta** *(ux_host_stack_class_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="949aa-478">**Host Stack Class Instance Create** *(ux_host_stack_class_instance_create)*</span></span> |
| ![Ikona niszczenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image186.png)    | <span data-ttu-id="949aa-480">**Niszczenie wystąpienia klasy stosu hosta** *(ux_host_stack_class_instance_destroy)*</span><span class="sxs-lookup"><span data-stu-id="949aa-480">**Host Stack Class Instance Destroy** *(ux_host_stack_class_instance_destroy)*</span></span> |
| ![Ikona usuwania konfiguracji stosu hosta](./media/user-guide/usbx-events/image187.png)    | <span data-ttu-id="949aa-482">**Usuwanie konfiguracji stosu hosta** *(ux_host_stack_configuration_delete)*</span><span class="sxs-lookup"><span data-stu-id="949aa-482">**Host Stack Configuration Delete** *(ux_host_stack_configuration_delete)*</span></span> |
| ![Ikona wyliczenia konfiguracji stosu hosta](./media/user-guide/usbx-events/image188.png)    | <span data-ttu-id="949aa-484">**Wyliczenie konfiguracji stosu hosta** *(ux_host_stack_configuration_enumerate)*</span><span class="sxs-lookup"><span data-stu-id="949aa-484">**Host Stack Configuration Enumerate** *(ux_host_stack_configuration_enumerate)*</span></span> |
| ![Ikona tworzenia wystąpienia konfiguracji stosu hosta](./media/user-guide/usbx-events/image189.png)    | <span data-ttu-id="949aa-486">**Tworzenie wystąpienia konfiguracji stosu hosta** *(ux_host_stack_configuration_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="949aa-486">**Host Stack Configuration Instance Create** *(ux_host_stack_configuration_instance_create)*</span></span> |
| ![Ikona usuwania wystąpienia konfiguracji stosu hosta](./media/user-guide/usbx-events/image190.png)    | <span data-ttu-id="949aa-488">**Usuwanie wystąpienia konfiguracji stosu hosta** *(ux_host_stack_configuration_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="949aa-488">**Host Stack Configuration Instance Delete** *(ux_host_stack_configuration_instance_delete)*</span></span> |
| ![Ikona zestawu konfiguracji stosu hosta](./media/user-guide/usbx-events/image191.png)    | <span data-ttu-id="949aa-490">**Zestaw konfiguracyjny stosu hosta** *(ux_host_stack_configuration_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-490">**Host Stack Configuration Set** *(ux_host_stack_configuration_set)*</span></span> |
| ![Ikona zestawu adresów urządzeń stosu hosta](./media/user-guide/usbx-events/image192.png)    | <span data-ttu-id="949aa-492">**Zestaw adresów urządzeń stosu hosta** *(ux_host_stack_device_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-492">**Host Stack Device Address Set** *(ux_host_stack_device_set)*</span></span> |
| ![Ikona pobierania konfiguracji urządzenia stosu hosta](./media/user-guide/usbx-events/image193.png)    | <span data-ttu-id="949aa-494">**Pobieranie konfiguracji urządzenia stosu hosta** *(ux_host_stack_device_configuration_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-494">**Host Stack Device Configuration Get** *(ux_host_stack_device_configuration_get)*</span></span> |
| ![Ikona wybierania konfiguracji urządzenia stosu hosta](./media/user-guide/usbx-events/image194.png)    | <span data-ttu-id="949aa-496">**Wybór konfiguracji urządzenia stosu hosta** *(ux_host_stack_device_configuration_select)*</span><span class="sxs-lookup"><span data-stu-id="949aa-496">**Host Stack Device Configuration Select** *(ux_host_stack_device_configuration_select)*</span></span> |
| ![Ikona odczytu deskryptora urządzenia stosu hosta](./media/user-guide/usbx-events/image195.png)    | <span data-ttu-id="949aa-498">**Odczyt deskryptora urządzenia stosu hosta** *(ux_host_stack_device_descriptor_read)*</span><span class="sxs-lookup"><span data-stu-id="949aa-498">**Host Stack Device Descriptor Read** *(ux_host_stack_device_descriptor_read)*</span></span> |
| ![Ikona pobierania urządzenia stosu hosta](./media/user-guide/usbx-events/image196.png)    | <span data-ttu-id="949aa-500">**Pobieranie urządzenia stosu hosta** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="949aa-500">**Host Stack Device Get** (ux_host_stack_device_get)</span></span> |
| ![Ikona usuwania urządzenia stosu hosta](./media/user-guide/usbx-events/image197.png)    | <span data-ttu-id="949aa-502">**Usuwanie urządzenia stosu hosta** (ux_host_stack_device_get)</span><span class="sxs-lookup"><span data-stu-id="949aa-502">**Host Stack Device Remove** (ux_host_stack_device_get)</span></span> |
| ![Ikona bezpłatnego zasobu urządzenia stosu hosta](./media/user-guide/usbx-events/image198.png)    | <span data-ttu-id="949aa-504">**Bezpłatny zasób urządzenia stosu hosta** (ux_host_stack_device_resource_free)</span><span class="sxs-lookup"><span data-stu-id="949aa-504">**Host Stack Device Resource Free** (ux_host_stack_device_resource_free)</span></span> |
| ![Ikona tworzenia wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image199.png)    | <span data-ttu-id="949aa-506">**Tworzenie wystąpienia punktu końcowego stosu hosta** (ux_host_stack_endpoint_instance_create)</span><span class="sxs-lookup"><span data-stu-id="949aa-506">**Host Stack Endpoint Instance Create** (ux_host_stack_endpoint_instance_create)</span></span> |
| ![Ikona usuwania wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image200.png)    | <span data-ttu-id="949aa-508">**Usuwanie wystąpienia punktu końcowego stosu hosta** (ux_host_stack_endpoint_instance_delete)</span><span class="sxs-lookup"><span data-stu-id="949aa-508">**Host Stack Endpoint Instance Delete** (ux_host_stack_endpoint_instance_delete)</span></span> |
| ![Ikona resetowania punktu końcowego stosu hosta](./media/user-guide/usbx-events/image201.png)    | <span data-ttu-id="949aa-510">**Resetowanie punktu końcowego stosu hosta** (ux_host_stack_endpoint_reset)</span><span class="sxs-lookup"><span data-stu-id="949aa-510">**Host Stack Endpoint Reset** (ux_host_stack_endpoint_reset)</span></span> |
| ![Ikona przerwania transferu punktu końcowego stosu hosta](./media/user-guide/usbx-events/image202.png)    | <span data-ttu-id="949aa-512">**Przerwanie transferu punktu końcowego stosu hosta** (ux_host_stack_endpoint_transfer_abort)</span><span class="sxs-lookup"><span data-stu-id="949aa-512">**Host Stack Endpoint Transfer Abort** (ux_host_stack_endpoint_transfer_abort)</span></span> |
| ![Ikona rejestru kontrolera hosta stosu hosta](./media/user-guide/usbx-events/image203.png)    | <span data-ttu-id="949aa-514">**Rejestr kontrolera hosta stosu hosta** *(ux_host_stack_hcd_register)*</span><span class="sxs-lookup"><span data-stu-id="949aa-514">**Host Stack Host Controller Register** *(ux_host_stack_hcd_register)*</span></span> |
| ![Ikona inicjowania stosu hosta](./media/user-guide/usbx-events/image204.png)    | <span data-ttu-id="949aa-516">**Inicjowanie stosu hosta** *(ux_host_stack_initialize)*</span><span class="sxs-lookup"><span data-stu-id="949aa-516">**Host Stack Initialize** *(ux_host_stack_initialize)*</span></span> |
| ![Ikona pobierania punktu końcowego interfejsu stosu hosta](./media/user-guide/usbx-events/image205.png)    | <span data-ttu-id="949aa-518">**Pobieranie punktu końcowego interfejsu stosu hosta** *(ux_host_stack_interface_endpoint_get)*</span><span class="sxs-lookup"><span data-stu-id="949aa-518">**Host Stack Interface Endpoint Get** *(ux_host_stack_interface_endpoint_get)*</span></span> |
| ![Ikona tworzenia wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image206.png)    | <span data-ttu-id="949aa-520">**Tworzenie wystąpienia interfejsu stosu hosta** *(ux_host_stack_interface_instance_create)*</span><span class="sxs-lookup"><span data-stu-id="949aa-520">**Host Stack Interface Instance Create** *(ux_host_stack_interface_instance_create)*</span></span> |
| ![Ikona usuwania wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image207.png)    | <span data-ttu-id="949aa-522">**Usuwanie wystąpienia interfejsu stosu hosta** *(ux_host_stack_interface_instance_delete)*</span><span class="sxs-lookup"><span data-stu-id="949aa-522">**Host Stack Interface Instance Delete** *(ux_host_stack_interface_instance_delete)*</span></span> |
| ![Ikona zestawu interfejsów stosu hosta](./media/user-guide/usbx-events/image208.png)    | <span data-ttu-id="949aa-524">**Zestaw interfejsów stosu hosta** *(ux_host_stack_interface_set)*</span><span class="sxs-lookup"><span data-stu-id="949aa-524">**Host Stack Interface Set** *(ux_host_stack_interface_set)*</span></span> |
| ![Ikona wybierania ustawienia interfejsu stosu hosta](./media/user-guide/usbx-events/image209.png)    | <span data-ttu-id="949aa-526">**Wybór ustawienia interfejsu stosu hosta** *(ux_host_stack_interface_setting_select)*</span><span class="sxs-lookup"><span data-stu-id="949aa-526">**Host Stack Interface Setting Select** *(ux_host_stack_interface_setting_select)*</span></span> |
| ![Ikona tworzenia nowej konfiguracji stosu hosta](./media/user-guide/usbx-events/image210.png)    | <span data-ttu-id="949aa-528">**Tworzenie nowej konfiguracji stosu hosta** *(ux_host_stack_new_configuration_create)*</span><span class="sxs-lookup"><span data-stu-id="949aa-528">**Host Stack New Configuration Create** *(ux_host_stack_new_configuration_create)*</span></span> |
| ![Ikona tworzenia nowego urządzenia dla stosu hosta](./media/user-guide/usbx-events/image211.png)    | <span data-ttu-id="949aa-530">**Tworzenie nowego urządzenia przez stos hosta** *(ux_host_stack_new_device_create)*</span><span class="sxs-lookup"><span data-stu-id="949aa-530">**Host Stack New Device Create** *(ux_host_stack_new_device_create)*</span></span> |
| ![Ikona tworzenia nowego punktu końcowego stosu hosta](./media/user-guide/usbx-events/image212.png)    | <span data-ttu-id="949aa-532">**Utwórz nowy punkt końcowy stosu hosta** *(ux_host_stack_new_endpoint_create)*</span><span class="sxs-lookup"><span data-stu-id="949aa-532">**Host Stack New Endpoint Create** *(ux_host_stack_new_endpoint_create)*</span></span> |
| ![Ikona procesu zmiany głównego centrum w stosie hosta](./media/user-guide/usbx-events/image213.png)    | <span data-ttu-id="949aa-534">**Proces zmiany głównego koncentratora stosu hosta** *(ux_host_stack_rh_change_process)*</span><span class="sxs-lookup"><span data-stu-id="949aa-534">**Host Stack Root Hub Change Process** *(ux_host_stack_rh_change_process)*</span></span> |
| ![Ikona wyodrębniania urządzenia głównego koncentratora stosu hosta](./media/user-guide/usbx-events/image214.png)    | <span data-ttu-id="949aa-536">**Wyodrębnianie urządzenia głównego koncentratora stosu hosta** *(ux_host_stack_rh_device_extraction)*</span><span class="sxs-lookup"><span data-stu-id="949aa-536">**Host Stack Root Hub Device Extraction** *(ux_host_stack_rh_device_extraction)*</span></span> |
| ![Ikona wstawienia urządzenia głównego koncentratora stosu hosta](./media/user-guide/usbx-events/image215.png)    | <span data-ttu-id="949aa-538">**Wstawianie urządzenia głównego koncentratora stosu hosta** *(ux_host_stack_rh_device_insertion)*</span><span class="sxs-lookup"><span data-stu-id="949aa-538">**Host Stack Root Hub Device Insertion** *(ux_host_stack_rh_device_insertion)*</span></span> |
| ![Ikona żądania transferu stosu hosta](./media/user-guide/usbx-events/image216.png)    | <span data-ttu-id="949aa-540">**Żądanie transferu stosu hosta** *(ux_host_stack_transfer_request)*</span><span class="sxs-lookup"><span data-stu-id="949aa-540">**Host Stack Transfer Request** *(ux_host_stack_transfer_request)*</span></span> |
| ![Ikona przerwania żądania transferu stosu hosta](./media/user-guide/usbx-events/image217.png)    | <span data-ttu-id="949aa-542">**Przerwano żądanie transferu stosu hosta** *(ux_host_stack_transfer_request_abort)*</span><span class="sxs-lookup"><span data-stu-id="949aa-542">**Host Stack Transfer Request Abort** *(ux_host_stack_transfer_request_abort)*</span></span> |
| ![Ikona błędu U S B X](./media/user-guide/usbx-events/image218.png)    | <span data-ttu-id="949aa-544">**Błąd USBX** *(ux_error)*</span><span class="sxs-lookup"><span data-stu-id="949aa-544">**USBX Error** *(ux_error)*</span></span> |

## <a name="event-descriptions"></a><span data-ttu-id="949aa-545">Opisy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-545">Event Descriptions</span></span>

<span data-ttu-id="949aa-546">Poniższe strony opisują zdarzenia śledzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-546">The following pages describe the USBX Trace Events.</span></span>

### <a name="device-class-cdc-activate"></a><span data-ttu-id="949aa-547">Aktywowanie przechwytywania klas urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-547">Device Class Cdc Activate</span></span> 

#### <a name="ux_device_class_cdc_activate"></a><span data-ttu-id="949aa-548">ux_device_class_cdc_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-548">ux_device_class_cdc_activate</span></span>

<span data-ttu-id="949aa-549">**Ikona** ![ Ikona urządzenia C D C aktywacja](./media/user-guide/usbx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-549">**Icon** ![Device Class C D C Activate icon](./media/user-guide/usbx-events/image1.png)</span></span>

<span data-ttu-id="949aa-550">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-550">**Description**</span></span>

<span data-ttu-id="949aa-551">To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-551">This event represents a USBX Device Class Cdc Activate Event.</span></span>

<span data-ttu-id="949aa-552">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-552">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-553">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-553">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-554">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-554">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-555">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-555">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-556">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-556">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-deactivate"></a><span data-ttu-id="949aa-557">Dezaktywacja przechwytywania klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-557">Device Class Cdc Deactivate</span></span> 

#### <a name="ux_device_class_cdc_deactivate"></a><span data-ttu-id="949aa-558">ux_device_class_cdc_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-558">ux_device_class_cdc_deactivate</span></span>

<span data-ttu-id="949aa-559">**Ikona** ![ Ikona klasy urządzenia C D C](./media/user-guide/usbx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-559">**Icon** ![Device Class C D C Deactivate icon](./media/user-guide/usbx-events/image2.png)</span></span>

<span data-ttu-id="949aa-560">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-560">**Description**</span></span>

<span data-ttu-id="949aa-561">To zdarzenie przedstawia dezaktywację klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-561">This event represents a USBX Device Class Cdc Deactivate.</span></span>

<span data-ttu-id="949aa-562">Pola informacji</span><span class="sxs-lookup"><span data-stu-id="949aa-562">Information Fields</span></span> 

- <span data-ttu-id="949aa-563">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-563">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-564">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-564">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-565">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-565">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-566">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-566">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-read"></a><span data-ttu-id="949aa-567">Odczyt przechwytywania klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-567">Device Class Cdc Read</span></span> 

#### <a name="ux_device_class_cdc_read"></a><span data-ttu-id="949aa-568">ux_device_class_cdc_read</span><span class="sxs-lookup"><span data-stu-id="949aa-568">ux_device_class_cdc_read</span></span>

<span data-ttu-id="949aa-569">**Ikona** ![ Ikona Odczytaj klasy urządzeń C D C](./media/user-guide/usbx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-569">**Icon** ![Device Class C D C Read icon](./media/user-guide/usbx-events/image3.png)</span></span>

<span data-ttu-id="949aa-570">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-570">**Description**</span></span>

<span data-ttu-id="949aa-571">To zdarzenie reprezentuje zdarzenie odczytu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-571">This event represents a USBX Device Class Cdc Read Event.</span></span>

<span data-ttu-id="949aa-572">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-572">**Information Fields**</span></span>

- <span data-ttu-id="949aa-573">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-573">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-574">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-574">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-575">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-575">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-576">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-576">Info Field 4: Not used.</span></span>

### <a name="device-class-cdc-write"></a><span data-ttu-id="949aa-577">Zapis przechwytywania danych klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-577">Device Class Cdc Write</span></span> 

#### <a name="ux_device_class_cdc_write"></a><span data-ttu-id="949aa-578">ux_device_class_cdc_write</span><span class="sxs-lookup"><span data-stu-id="949aa-578">ux_device_class_cdc_write</span></span>

<span data-ttu-id="949aa-579">**Ikona** ![ Ikona urządzenia C D C pisanie](./media/user-guide/usbx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-579">**Icon** ![Device Class C D C Write icon](./media/user-guide/usbx-events/image4.png)</span></span>

<span data-ttu-id="949aa-580">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-580">**Description**</span></span>

<span data-ttu-id="949aa-581">To zdarzenie reprezentuje zdarzenie zapisu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-581">This event represents a USBX Device Class Cdc Write Event.</span></span>

<span data-ttu-id="949aa-582">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-582">**Information Fields**</span></span>

- <span data-ttu-id="949aa-583">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-583">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-584">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-584">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-585">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-585">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-586">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-586">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-activate"></a><span data-ttu-id="949aa-587">Dpump Aktywuj klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-587">Device Class Dpump Activate</span></span> 

#### <a name="ux_device_class_dpump_activate"></a><span data-ttu-id="949aa-588">ux_device_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-588">ux_device_class_dpump_activate</span></span>

<span data-ttu-id="949aa-589">**Ikona** ![ Ikona urządzenia Dpump Activate](./media/user-guide/usbx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-589">**Icon** ![Device Class Dpump Activate icon](./media/user-guide/usbx-events/image5.png)</span></span>

<span data-ttu-id="949aa-590">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-590">**Description**</span></span>

<span data-ttu-id="949aa-591">To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX Dpump.</span><span class="sxs-lookup"><span data-stu-id="949aa-591">This event represents a USBX Device Class Dpump Activate Event.</span></span>

<span data-ttu-id="949aa-592">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-592">**Information Fields**</span></span>

- <span data-ttu-id="949aa-593">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-593">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-594">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-594">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-595">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-595">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-596">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-596">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-deactivate"></a><span data-ttu-id="949aa-597">Dezaktywacja klasy urządzenia Dpump</span><span class="sxs-lookup"><span data-stu-id="949aa-597">Device Class Dpump Deactivate</span></span> 

#### <a name="ux_device_class_dpump_deactivate"></a><span data-ttu-id="949aa-598">ux_device_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-598">ux_device_class_dpump_deactivate</span></span>

<span data-ttu-id="949aa-599">**Ikona** ![ Ikona dezaktywowania klasy urządzenia Dpump](./media/user-guide/usbx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-599">**Icon** ![Device Class Dpump Deactivate icon](./media/user-guide/usbx-events/image6.png)</span></span>

<span data-ttu-id="949aa-600">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-600">**Description**</span></span>

<span data-ttu-id="949aa-601">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Dpump.</span><span class="sxs-lookup"><span data-stu-id="949aa-601">This event represents a USBX Device Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="949aa-602">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-602">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-603">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-603">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-604">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-604">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-605">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-605">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-606">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-606">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-read"></a><span data-ttu-id="949aa-607">Odczyt klasy urządzenia Dpump</span><span class="sxs-lookup"><span data-stu-id="949aa-607">Device Class Dpump Read</span></span> 

#### <a name="ux_device_class_dpump_read"></a><span data-ttu-id="949aa-608">ux_device_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="949aa-608">ux_device_class_dpump_read</span></span>

<span data-ttu-id="949aa-609">**Ikona** ![ Ikona odczytu Dpump klasy urządzeń](./media/user-guide/usbx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-609">**Icon** ![Device Class Dpump Read icon](./media/user-guide/usbx-events/image7.png)</span></span>

<span data-ttu-id="949aa-610">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-610">**Description**</span></span>

<span data-ttu-id="949aa-611">To zdarzenie reprezentuje zdarzenie odczytu klasy urządzenia USBX Dpump.</span><span class="sxs-lookup"><span data-stu-id="949aa-611">This event represents a USBX Device Class Dpump Read Event.</span></span>

<span data-ttu-id="949aa-612">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-612">**Information Fields**</span></span>

- <span data-ttu-id="949aa-613">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-613">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-614">Pole informacji 2: bufor.</span><span class="sxs-lookup"><span data-stu-id="949aa-614">Info Field 2: Buffer.</span></span>
- <span data-ttu-id="949aa-615">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-615">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-616">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-616">Info Field 4: Not used.</span></span>

### <a name="device-class-dpump-write"></a><span data-ttu-id="949aa-617">Dpump zapisu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-617">Device Class Dpump Write</span></span> 

#### <a name="ux_device_class_dpump_write"></a><span data-ttu-id="949aa-618">ux_device_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="949aa-618">ux_device_class_dpump_write</span></span>

<span data-ttu-id="949aa-619">**Ikona** ![ Ikona zapisu Dpump klasy urządzeń](./media/user-guide/usbx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-619">**Icon** ![Device Class Dpump Write icon](./media/user-guide/usbx-events/image8.png)</span></span>

<span data-ttu-id="949aa-620">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-620">**Description**</span></span>

<span data-ttu-id="949aa-621">To zdarzenie reprezentuje zdarzenie zapisu klasy urządzenia USBX Dpump.</span><span class="sxs-lookup"><span data-stu-id="949aa-621">This event represents a USBX Device Class Dpump Write Event.</span></span>

<span data-ttu-id="949aa-622">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-622">**Information Fields**</span></span>

- <span data-ttu-id="949aa-623">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-623">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-624">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-624">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-625">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-625">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-626">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-626">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-activate"></a><span data-ttu-id="949aa-627">Aktywuj klasy urządzenia HID</span><span class="sxs-lookup"><span data-stu-id="949aa-627">Device Class Hid Activate</span></span> 

#### <a name="ux_device_class_hid_activate"></a><span data-ttu-id="949aa-628">ux_device_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-628">ux_device_class_hid_activate</span></span>

<span data-ttu-id="949aa-629">**Ikona** ![ Ikona klasy urządzenia HID Aktywuj](./media/user-guide/usbx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-629">**Icon** ![Device Class Hid Activate icon](./media/user-guide/usbx-events/image9.png)</span></span>

<span data-ttu-id="949aa-630">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-630">**Description**</span></span>

<span data-ttu-id="949aa-631">To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-631">This event represents a USBX Device Class Hid Activate Event.</span></span>

<span data-ttu-id="949aa-632">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-632">**Information Fields**</span></span>

- <span data-ttu-id="949aa-633">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-633">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-634">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-634">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-635">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-635">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-636">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-636">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-deactivate"></a><span data-ttu-id="949aa-637">Dezaktywacja klasy urządzenia HID</span><span class="sxs-lookup"><span data-stu-id="949aa-637">Device Class Hid Deactivate</span></span> 

#### <a name="ux_device_class_hid_deactivate"></a><span data-ttu-id="949aa-638">ux_device_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-638">ux_device_class_hid_deactivate</span></span>

<span data-ttu-id="949aa-639">**Ikona** ![ Ikona dezaktywacji klasy urządzenia](./media/user-guide/usbx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-639">**Icon** ![Device Class Hid Deactivate icon](./media/user-guide/usbx-events/image10.png)</span></span>

<span data-ttu-id="949aa-640">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-640">**Description**</span></span>

<span data-ttu-id="949aa-641">To zdarzenie reprezentuje zdarzenie dezaktywacji klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-641">This event represents a USBX Device Class Hid Deactivate Event.</span></span>

<span data-ttu-id="949aa-642">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-642">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-643">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-643">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-644">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-644">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-645">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-645">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-646">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-646">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-descriptor-send"></a><span data-ttu-id="949aa-647">Wysyłanie deskryptora HID klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-647">Device Class Hid Descriptor Send</span></span> 

#### <a name="ux_device_class_hid_descritpor_send"></a><span data-ttu-id="949aa-648">ux_device_class_hid_descritpor_send</span><span class="sxs-lookup"><span data-stu-id="949aa-648">ux_device_class_hid_descritpor_send</span></span>

<span data-ttu-id="949aa-649">**Ikona** ![ Ikona wysyłania deskryptora HID klasy urządzeń](./media/user-guide/usbx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-649">**Icon** ![Device Class Hid Descriptor Send icon](./media/user-guide/usbx-events/image11.png)</span></span>

<span data-ttu-id="949aa-650">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-650">**Description**</span></span>

<span data-ttu-id="949aa-651">To zdarzenie reprezentuje zdarzenie wysyłania deskryptora HID klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-651">This event represents a USBX Device Class Hid Descriptor Send Event.</span></span>

<span data-ttu-id="949aa-652">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-652">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-653">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-653">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-654">Pole informacji 2: typ deskryptora.</span><span class="sxs-lookup"><span data-stu-id="949aa-654">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="949aa-655">Pole informacji 3: indeks żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-655">Info Field 3: Request index.</span></span>
- <span data-ttu-id="949aa-656">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-656">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-get"></a><span data-ttu-id="949aa-657">Pobieranie zdarzenia HID klasy urządzenia</span><span class="sxs-lookup"><span data-stu-id="949aa-657">Device Class Hid Event Get</span></span> 

#### <a name="ux_device_class_hid_event_get"></a><span data-ttu-id="949aa-658">ux_device_class_hid_event_get</span><span class="sxs-lookup"><span data-stu-id="949aa-658">ux_device_class_hid_event_get</span></span>

<span data-ttu-id="949aa-659">**Ikona** ![ Ikona pobierania zdarzenia HID z klasą urządzeń](./media/user-guide/usbx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-659">**Icon** ![Device Class Hid Event Get icon](./media/user-guide/usbx-events/image12.png)</span></span>

<span data-ttu-id="949aa-660">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-660">**Description**</span></span>

<span data-ttu-id="949aa-661">To zdarzenie reprezentuje zdarzenie pobrania zdarzenia HID klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-661">This event represents a USBX Device Class Hid Event Get Event.</span></span>

<span data-ttu-id="949aa-662">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-662">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-663">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-663">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-664">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-664">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-665">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-665">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-666">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-666">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-event-set"></a><span data-ttu-id="949aa-667">Zestaw zdarzeń HID klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-667">Device Class Hid Event Set</span></span> 

#### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="949aa-668">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="949aa-668">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="949aa-669">**Ikona** ![ Ikona zestawu zdarzeń HID klasy urządzeń](./media/user-guide/usbx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-669">**Icon** ![Device Class Hid Event Set icon](./media/user-guide/usbx-events/image13.png)</span></span>

<span data-ttu-id="949aa-670">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-670">**Description**</span></span>

<span data-ttu-id="949aa-671">To zdarzenie reprezentuje zestaw zdarzeń HID klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-671">This event represents a USBX Device Class Hid Event Set.</span></span>

<span data-ttu-id="949aa-672">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-672">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-673">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-673">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-674">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-674">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-675">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-675">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-676">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-676">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-get"></a><span data-ttu-id="949aa-677">Pobieranie raportu HID klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-677">Device Class Hid Report Get</span></span> 

#### <a name="ux_device_class_hid_report_get"></a><span data-ttu-id="949aa-678">ux_device_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="949aa-678">ux_device_class_hid_report_get</span></span>

<span data-ttu-id="949aa-679">**Ikona** ![ Ikona pobierania raportu HID klasy urządzeń](./media/user-guide/usbx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-679">**Icon** ![Device Class Hid Report Get icon](./media/user-guide/usbx-events/image14.png)</span></span>

<span data-ttu-id="949aa-680">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-680">**Description**</span></span>

<span data-ttu-id="949aa-681">To zdarzenie reprezentuje zdarzenie Get raportu HID klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-681">This event represents a USBX Device Class Hid Report Get Event.</span></span>

<span data-ttu-id="949aa-682">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-682">**Information Fields**</span></span>

- <span data-ttu-id="949aa-683">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-683">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-684">Pole informacji 2: typ deskryptora.</span><span class="sxs-lookup"><span data-stu-id="949aa-684">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="949aa-685">Pole informacji 3: indeks żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-685">Info Field 3: Request index.</span></span>
- <span data-ttu-id="949aa-686">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-686">Info Field 4: Not used.</span></span>

### <a name="device-class-hid-report-set"></a><span data-ttu-id="949aa-687">Zestaw raportów HID klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-687">Device Class Hid Report Set</span></span> 

#### <a name="ux_device_class_hid_report_set"></a><span data-ttu-id="949aa-688">ux_device_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="949aa-688">ux_device_class_hid_report_set</span></span>

<span data-ttu-id="949aa-689">**Ikona** ![ Ikona zestawu raportów HID klasy urządzeń](./media/user-guide/usbx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-689">**Icon** ![Device Class Hid Report Set icon](./media/user-guide/usbx-events/image15.png)</span></span>

<span data-ttu-id="949aa-690">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-690">**Description**</span></span>

<span data-ttu-id="949aa-691">To zdarzenie reprezentuje zdarzenie zestawu raportów HID klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-691">This event represents a USBX Device Class Hid Report Set Event.</span></span>

<span data-ttu-id="949aa-692">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-692">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-693">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-693">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-694">Pole informacji 2: typ deskryptora.</span><span class="sxs-lookup"><span data-stu-id="949aa-694">Info Field 2: Descriptor type.</span></span>
- <span data-ttu-id="949aa-695">Pole informacji 3: indeks żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-695">Info Field 3: Request index.</span></span>
- <span data-ttu-id="949aa-696">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-696">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-activate"></a><span data-ttu-id="949aa-697">Pima Aktywuj klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-697">Device Class Pima Activate</span></span>

#### <a name="ux_device_class_pima_activate"></a><span data-ttu-id="949aa-698">ux_device_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-698">ux_device_class_pima_activate</span></span>

<span data-ttu-id="949aa-699">**Ikona** ![ Ikona urządzenia Pima Activate](./media/user-guide/usbx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-699">**Icon** ![Device Class Pima Activate icon](./media/user-guide/usbx-events/image16.png)</span></span>

<span data-ttu-id="949aa-700">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-700">**Description**</span></span>

<span data-ttu-id="949aa-701">To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-701">This event represents a USBX Device Class Pima Activate Event.</span></span>

<span data-ttu-id="949aa-702">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-702">**Information Fields**</span></span>

- <span data-ttu-id="949aa-703">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-703">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-704">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-704">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-705">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-705">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-706">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-706">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-deactivate"></a><span data-ttu-id="949aa-707">Dezaktywacja klasy urządzenia Pima</span><span class="sxs-lookup"><span data-stu-id="949aa-707">Device Class Pima Deactivate</span></span> 

#### <a name="ux_device_class_pima_deactivate"></a><span data-ttu-id="949aa-708">ux_device_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-708">ux_device_class_pima_deactivate</span></span>

<span data-ttu-id="949aa-709">**Ikona** ![ Ikona dezaktywowania klasy urządzenia Pima](./media/user-guide/usbx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-709">**Icon** ![Device Class Pima Deactivate icon](./media/user-guide/usbx-events/image17.png)</span></span>

<span data-ttu-id="949aa-710">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-710">**Description**</span></span>

<span data-ttu-id="949aa-711">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-711">This event represents a USBX Device Class Pima Deactivate Event.</span></span>

<span data-ttu-id="949aa-712">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-712">**Information Fields**</span></span>

- <span data-ttu-id="949aa-713">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-713">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-714">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-714">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-715">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-715">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-716">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-716">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-device-info-send"></a><span data-ttu-id="949aa-717">Klasa urządzenia Pima wysyłanie informacji o urządzeniu</span><span class="sxs-lookup"><span data-stu-id="949aa-717">Device Class Pima Device Info Send</span></span> 

#### <a name="ux_device_class_pima_device_info_send"></a><span data-ttu-id="949aa-718">ux_device_class_pima_device_info_send</span><span class="sxs-lookup"><span data-stu-id="949aa-718">ux_device_class_pima_device_info_send</span></span>

<span data-ttu-id="949aa-719">**Ikona** ![ Ikona wysyłania informacji o urządzeniu Pima klasy urządzeń](./media/user-guide/usbx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-719">**Icon** ![Device Class Pima Device Info Send icon](./media/user-guide/usbx-events/image18.png)</span></span>

<span data-ttu-id="949aa-720">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-720">**Description**</span></span>

<span data-ttu-id="949aa-721">To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania informacji o urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="949aa-721">This event represents a USBX Device Class Pima Device Info Send Event.</span></span>

<span data-ttu-id="949aa-722">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-722">**Information Fields**</span></span>

- <span data-ttu-id="949aa-723">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-723">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-724">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-724">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-725">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-725">Info Field 3: Not used.</span></span>

### <a name="device-class-pima-event-get"></a><span data-ttu-id="949aa-726">Pobieranie zdarzenia Pima klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-726">Device Class Pima Event Get</span></span> 

#### <a name="ux_device_class_pima_event_get"></a><span data-ttu-id="949aa-727">ux_device_class_pima_event_get</span><span class="sxs-lookup"><span data-stu-id="949aa-727">ux_device_class_pima_event_get</span></span>

<span data-ttu-id="949aa-728">**Ikona** ![ Ikona pobierania zdarzenia Pima klasy urządzeń](./media/user-guide/usbx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-728">**Icon** ![Device Class Pima Event Get icon](./media/user-guide/usbx-events/image19.png)</span></span>

<span data-ttu-id="949aa-729">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-729">**Description**</span></span>

<span data-ttu-id="949aa-730">To zdarzenie reprezentuje zdarzenie pobrania zdarzenia USBX klasy urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-730">This event represents a USBX Device Class Pima Event Get Event.</span></span>

<span data-ttu-id="949aa-731">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-731">**Information Fields**</span></span>

- <span data-ttu-id="949aa-732">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-732">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-733">Pole informacji 2: zdarzenie Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-733">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="949aa-734">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-734">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-735">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-735">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-event-set"></a><span data-ttu-id="949aa-736">Zestaw zdarzeń Pima klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-736">Device Class Pima Event Set</span></span> 

#### <a name="ux_device_class_pima_event_set"></a><span data-ttu-id="949aa-737">ux_device_class_pima_event_set</span><span class="sxs-lookup"><span data-stu-id="949aa-737">ux_device_class_pima_event_set</span></span>

<span data-ttu-id="949aa-738">**Ikona** ![ Ikona zestawu zdarzeń Pima klasy urządzeń](./media/user-guide/usbx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-738">**Icon** ![Device Class Pima Event Set icon](./media/user-guide/usbx-events/image20.png)</span></span>

<span data-ttu-id="949aa-739">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-739">**Description**</span></span>

<span data-ttu-id="949aa-740">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-740">This event represents a USBX Device Class Pima Event Set Event.</span></span>

<span data-ttu-id="949aa-741">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-741">**Information Fields**</span></span>

- <span data-ttu-id="949aa-742">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-742">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-743">Pole informacji 2: zdarzenie Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-743">Info Field 2: Pima event.</span></span>
- <span data-ttu-id="949aa-744">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-744">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-745">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-745">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-add"></a><span data-ttu-id="949aa-746">Dodawanie obiektu Pima klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-746">Device Class Pima Object Add</span></span> 

#### <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="949aa-747">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="949aa-747">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="949aa-748">**Ikona** ![ Ikona dodawania obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-748">**Icon** ![Device Class Pima Object Add icon](./media/user-guide/usbx-events/image21.png)</span></span>

<span data-ttu-id="949aa-749">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-749">**Description**</span></span>

<span data-ttu-id="949aa-750">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-750">This event represents a USBX Device Class Pima Object Add Event.</span></span>

<span data-ttu-id="949aa-751">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-751">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-752">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-752">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-753">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-753">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-754">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-754">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-755">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-755">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-get"></a><span data-ttu-id="949aa-756">Pobieranie danych obiektu Pima klasy urządzenia</span><span class="sxs-lookup"><span data-stu-id="949aa-756">Device Class Pima Object Data Get</span></span> 

#### <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="949aa-757">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="949aa-757">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="949aa-758">**Ikona** ![ Ikona uzyskiwania danych obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-758">**Icon** ![Device Class Pima Object Data Get icon](./media/user-guide/usbx-events/image22.png)</span></span>

<span data-ttu-id="949aa-759">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-759">**Description**</span></span>

<span data-ttu-id="949aa-760">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-760">This event represents a USBX Device Class Pima Object Data Get Event.</span></span>

<span data-ttu-id="949aa-761">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-761">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-762">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-762">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-763">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-763">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-764">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-764">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-765">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-765">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-data-send"></a><span data-ttu-id="949aa-766">Wysyłanie danych obiektu Pima klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-766">Device Class Pima Object Data Send</span></span> 

#### <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="949aa-767">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="949aa-767">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="949aa-768">**Ikona** ![ Ikona wysyłania danych obiektu Pima klasy urządzeń](./media/user-guide/usbx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-768">**Icon** ![Device Class Pima Object Data Send icon](./media/user-guide/usbx-events/image23.png)</span></span>

<span data-ttu-id="949aa-769">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-769">**Description**</span></span>

<span data-ttu-id="949aa-770">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-770">This event represents a USBX Device Class Pima Object Data Send Event.</span></span>

<span data-ttu-id="949aa-771">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-771">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-772">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-772">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-773">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-773">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-774">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-774">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-775">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-775">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-delete"></a><span data-ttu-id="949aa-776">Usuwanie obiektu Pima klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-776">Device Class Pima Object Delete</span></span> 

#### <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="949aa-777">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="949aa-777">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="949aa-778">**Ikona** ![ Ikona usuwania obiektu Pima klasy urządzenia](./media/user-guide/usbx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-778">**Icon** ![Device Class Pima Object Delete icon](./media/user-guide/usbx-events/image24.png)</span></span>

<span data-ttu-id="949aa-779">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-779">**Description**</span></span>

<span data-ttu-id="949aa-780">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-780">This event represents a USBX Device Class Pima Object Delete Event.</span></span>

<span data-ttu-id="949aa-781">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-781">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-782">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-782">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-783">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-783">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-784">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-784">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-785">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-785">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-handles-send"></a><span data-ttu-id="949aa-786">Obiekt Pima klasy urządzenia obsługuje wysyłanie</span><span class="sxs-lookup"><span data-stu-id="949aa-786">Device Class Pima Object Handles Send</span></span> 

#### <a name="ux_device_class_pima_object_handles_send"></a><span data-ttu-id="949aa-787">ux_device_class_pima_object_handles_send</span><span class="sxs-lookup"><span data-stu-id="949aa-787">ux_device_class_pima_object_handles_send</span></span>

<span data-ttu-id="949aa-788">**Ikona** ![ Obiekt Pima klasy urządzenia obsługuje ikonę wysyłania](./media/user-guide/usbx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-788">**Icon** ![Device Class Pima Object Handles Send icon](./media/user-guide/usbx-events/image25.png)</span></span>

<span data-ttu-id="949aa-789">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-789">**Description**</span></span>

<span data-ttu-id="949aa-790">To zdarzenie reprezentuje klasę urządzenia USBX Pima obsługuje zdarzenie wysyłania.</span><span class="sxs-lookup"><span data-stu-id="949aa-790">This event represents a USBX Device Class Pima Object Handles Send Event.</span></span>

<span data-ttu-id="949aa-791">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-791">**Information Fields**</span></span>

- <span data-ttu-id="949aa-792">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-792">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-793">Pole informacji 2: Identyfikator magazynu.</span><span class="sxs-lookup"><span data-stu-id="949aa-793">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="949aa-794">Pole informacji 3: kod formatu obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-794">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="949aa-795">Pole informacji 4: skojarzenie obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-795">Info Field 4: Object association.</span></span>

### <a name="device-class-pima-object-info-get"></a><span data-ttu-id="949aa-796">Pobieranie informacji o obiekcie Pima klasy urządzenia</span><span class="sxs-lookup"><span data-stu-id="949aa-796">Device Class Pima Object Info Get</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="949aa-797">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="949aa-797">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="949aa-798">**Ikona** ![ Ikona uzyskiwania informacji o obiekcie Pima klasy urządzeń](./media/user-guide/usbx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-798">**Icon** ![Device Class Pima Object Info Get icon](./media/user-guide/usbx-events/image26.png)</span></span>

<span data-ttu-id="949aa-799">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-799">**Description**</span></span>

<span data-ttu-id="949aa-800">To zdarzenie reprezentuje zdarzenie Get USBX klasy urządzenia Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-800">This event represents a USBX Device Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="949aa-801">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-801">**Information Fields**</span></span>

- <span data-ttu-id="949aa-802">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-802">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-803">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-803">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-804">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-804">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-805">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-805">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-object-info-send"></a><span data-ttu-id="949aa-806">Wysyłanie informacji o obiekcie Pima klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-806">Device Class Pima Object Info Send</span></span> 

#### <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="949aa-807">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="949aa-807">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="949aa-808">**Ikona** ![ Ikona wysyłania informacji o obiekcie Pima klasy urządzenia](./media/user-guide/usbx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-808">**Icon** ![Device Class Pima Object Info Send icon](./media/user-guide/usbx-events/image27.png)</span></span>

<span data-ttu-id="949aa-809">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-809">**Description**</span></span>

<span data-ttu-id="949aa-810">To zdarzenie reprezentuje zdarzenie wysyłania informacji o obiekcie USBX klasy urządzenia Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-810">This event represents a USBX Device Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="949aa-811">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-811">**Information Fields**</span></span>

- <span data-ttu-id="949aa-812">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-812">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-813">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-813">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-814">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-814">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-815">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-815">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-objects-number-send"></a><span data-ttu-id="949aa-816">Klasa urządzenia Pima liczba obiektów do wysłania</span><span class="sxs-lookup"><span data-stu-id="949aa-816">Device Class Pima Objects Number Send</span></span> 

#### <a name="ux_device_class_pima_object_number_send"></a><span data-ttu-id="949aa-817">ux_device_class_pima_object_number_send</span><span class="sxs-lookup"><span data-stu-id="949aa-817">ux_device_class_pima_object_number_send</span></span>

<span data-ttu-id="949aa-818">**Ikona** ![ Ikona Pima obiektów klasy urządzeń](./media/user-guide/usbx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-818">**Icon** ![Device Class Pima Objects Number Send icon](./media/user-guide/usbx-events/image28.png)</span></span>

<span data-ttu-id="949aa-819">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-819">**Description**</span></span>

<span data-ttu-id="949aa-820">To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania numeru obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-820">This event represents a USBX Device Class Pima Object Number Send event.</span></span>

<span data-ttu-id="949aa-821">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-821">**Information Fields**</span></span>

- <span data-ttu-id="949aa-822">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-822">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-823">Pole informacji 2: Identyfikator magazynu.</span><span class="sxs-lookup"><span data-stu-id="949aa-823">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="949aa-824">Pole informacji 3: kod formatu obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-824">Info Field 3: Object format code.</span></span>
- <span data-ttu-id="949aa-825">Pole informacji 4: obiekt skojarzony.</span><span class="sxs-lookup"><span data-stu-id="949aa-825">Info Field 4: Object associate.</span></span>

### <a name="device-class-pima-partial-object-data-get"></a><span data-ttu-id="949aa-826">Klasa urządzenia Pima częściowe dane obiektu Get</span><span class="sxs-lookup"><span data-stu-id="949aa-826">Device Class Pima Partial Object Data Get</span></span>

#### <a name="ux_device_class_pima_partial_object_data_get"></a><span data-ttu-id="949aa-827">ux_device_class_pima_partial_object_data_get</span><span class="sxs-lookup"><span data-stu-id="949aa-827">ux_device_class_pima_partial_object_data_get</span></span>

<span data-ttu-id="949aa-828">**Ikona** ![ Ikona Pima części danych obiektu klasy urządzenia](./media/user-guide/usbx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-828">**Icon** ![Device Class Pima Partial Object Data Get icon](./media/user-guide/usbx-events/image29.png)</span></span>

<span data-ttu-id="949aa-829">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-829">**Description**</span></span>

<span data-ttu-id="949aa-830">To zdarzenie reprezentuje USBX klasy urządzenia Pima częściowe zdarzenie Get Data.</span><span class="sxs-lookup"><span data-stu-id="949aa-830">This event represents a USBX Device Class Pima Partial Object Data Get Event.</span></span>

<span data-ttu-id="949aa-831">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-831">**Information Fields**</span></span>

- <span data-ttu-id="949aa-832">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-832">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-833">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-833">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-834">Pole informacji 3: zażądano przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="949aa-834">Info Field 3: Offset requested.</span></span>
- <span data-ttu-id="949aa-835">Pole informacji 4: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-835">Info Field 4: Length requested.</span></span>

### <a name="device-class-pima-response-send"></a><span data-ttu-id="949aa-836">Wysyłanie odpowiedzi przez Pima klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-836">Device Class Pima Response Send</span></span> 

#### <a name="ux_device_class_pima_response_send"></a><span data-ttu-id="949aa-837">ux_device_class_pima_response_send</span><span class="sxs-lookup"><span data-stu-id="949aa-837">ux_device_class_pima_response_send</span></span>

<span data-ttu-id="949aa-838">**Ikona** ![ Ikona wysyłania odpowiedzi Pima klasy urządzeń](./media/user-guide/usbx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-838">**Icon** ![Device Class Pima Response Send icon](./media/user-guide/usbx-events/image30.png)</span></span>

<span data-ttu-id="949aa-839">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-839">**Description**</span></span>

<span data-ttu-id="949aa-840">To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="949aa-840">This event represents a USBX Device Class Pima Response Send Event.</span></span>

<span data-ttu-id="949aa-841">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-841">**Information Fields**</span></span>

- <span data-ttu-id="949aa-842">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-842">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-843">Pole informacji 2: kod odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="949aa-843">Info Field 2: Response code.</span></span>
- <span data-ttu-id="949aa-844">Pole informacji 3: parametr liczby.</span><span class="sxs-lookup"><span data-stu-id="949aa-844">Info Field 3: Number parameter.</span></span>
- <span data-ttu-id="949aa-845">Pole informacji 4: Pima parametr 1.</span><span class="sxs-lookup"><span data-stu-id="949aa-845">Info Field 4: Pima parameter 1.</span></span>

### <a name="device-class-pima-storage-id-send"></a><span data-ttu-id="949aa-846">Klasa urządzenia Pima — wysyłanie identyfikatora magazynu</span><span class="sxs-lookup"><span data-stu-id="949aa-846">Device Class Pima Storage Id Send</span></span> 

#### <a name="ux_device_class_pima_storage_id_send"></a><span data-ttu-id="949aa-847">ux_device_class_pima_storage_id_send</span><span class="sxs-lookup"><span data-stu-id="949aa-847">ux_device_class_pima_storage_id_send</span></span>

<span data-ttu-id="949aa-848">**Ikona** ![ Ikona wysyłania identyfikatora magazynu Pima klasy urządzeń](./media/user-guide/usbx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-848">**Icon** ![Device Class Pima Storage Id Send icon](./media/user-guide/usbx-events/image31.png)</span></span>

<span data-ttu-id="949aa-849">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-849">**Description**</span></span>

<span data-ttu-id="949aa-850">To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania identyfikatora magazynu.</span><span class="sxs-lookup"><span data-stu-id="949aa-850">This event represents a USBX Device Class Pima Storage Id Send Event.</span></span>

<span data-ttu-id="949aa-851">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-851">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-852">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-852">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-853">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-853">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-854">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-854">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-855">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-855">Info Field 4: Not used.</span></span>

### <a name="device-class-pima-storage-info-send"></a><span data-ttu-id="949aa-856">Pima urządzenia — wysyłanie informacji o magazynie</span><span class="sxs-lookup"><span data-stu-id="949aa-856">Device Class Pima Storage Info Send</span></span> 

#### <a name="ux_device_class_pima_storage_info_send"></a><span data-ttu-id="949aa-857">ux_device_class_pima_storage_info_send</span><span class="sxs-lookup"><span data-stu-id="949aa-857">ux_device_class_pima_storage_info_send</span></span>

<span data-ttu-id="949aa-858">**Ikona** ![ Ikona wysyłania informacji o magazynie Pima klasy urządzeń](./media/user-guide/usbx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-858">**Icon** ![Device Class Pima Storage Info Send icon](./media/user-guide/usbx-events/image32.png)</span></span>

<span data-ttu-id="949aa-859">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-859">**Description**</span></span>

<span data-ttu-id="949aa-860">To zdarzenie reprezentuje USBX klasy urządzenia Pima zdarzenie wysyłania informacji o magazynie.</span><span class="sxs-lookup"><span data-stu-id="949aa-860">This event represents a USBX Device Class Pima Storage Info Send Event.</span></span>

<span data-ttu-id="949aa-861">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-861">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-862">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-862">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-863">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-863">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-864">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-864">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-865">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-865">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-activate"></a><span data-ttu-id="949aa-866">RNDIS Aktywuj klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-866">Device Class Rndis Activate</span></span> 

#### <a name="ux_device_class_rndis_activate"></a><span data-ttu-id="949aa-867">ux_device_class_rndis_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-867">ux_device_class_rndis_activate</span></span>

<span data-ttu-id="949aa-868">**Ikona** ![ Ikona urządzenia RNDIS Activate](./media/user-guide/usbx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-868">**Icon** ![Device Class Rndis Activate icon](./media/user-guide/usbx-events/image33.png)</span></span>

<span data-ttu-id="949aa-869">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-869">**Description**</span></span>

<span data-ttu-id="949aa-870">To zdarzenie reprezentuje zdarzenie aktywowania klasy urządzenia USBX RNDIS.</span><span class="sxs-lookup"><span data-stu-id="949aa-870">This event represents a USBX Device Class Rndis Activate Event.</span></span>

<span data-ttu-id="949aa-871">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-871">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-872">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-872">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-873">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-873">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-874">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-874">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-875">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-875">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-deactivate"></a><span data-ttu-id="949aa-876">Dezaktywacja klasy urządzenia RNDIS</span><span class="sxs-lookup"><span data-stu-id="949aa-876">Device Class Rndis Deactivate</span></span> 

#### <a name="ux_device_class_rndis_deactivate"></a><span data-ttu-id="949aa-877">ux_device_class_rndis_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-877">ux_device_class_rndis_deactivate</span></span>

<span data-ttu-id="949aa-878">**Ikona** ![ Ikona dezaktywowania klasy urządzenia RNDIS](./media/user-guide/usbx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-878">**Icon** ![Device Class Rndis Deactivate icon](./media/user-guide/usbx-events/image34.png)</span></span>

<span data-ttu-id="949aa-879">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-879">**Description**</span></span>

<span data-ttu-id="949aa-880">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia RNDIS.</span><span class="sxs-lookup"><span data-stu-id="949aa-880">This event represents a USBX Device Class Rndis Deactivate Event.</span></span>

<span data-ttu-id="949aa-881">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-881">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-882">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-882">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-883">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-883">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-884">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-884">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-885">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-885">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-keep-alive"></a><span data-ttu-id="949aa-886">RNDIS aktywność komunikatu o klasie urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-886">Device Class Rndis Message Keep Alive</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_alive"></a><span data-ttu-id="949aa-887">ux_device_class_rndis_msg_keep_alive</span><span class="sxs-lookup"><span data-stu-id="949aa-887">ux_device_class_rndis_msg_keep_alive</span></span>

<span data-ttu-id="949aa-888">**Ikona** ![ Ikona utrzymywania aktywności komunikatu RNDIS na urządzeniu](./media/user-guide/usbx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-888">**Icon** ![Device Class Rndis Message Keep Alive icon](./media/user-guide/usbx-events/image35.png)</span></span>

<span data-ttu-id="949aa-889">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-889">**Description**</span></span>

<span data-ttu-id="949aa-890">To zdarzenie reprezentuje USBX klasy urządzenia RNDIS zdarzenie Keep Alive.</span><span class="sxs-lookup"><span data-stu-id="949aa-890">This event represents a USBX Device Class Rndis Message Keep Alive Event.</span></span>

<span data-ttu-id="949aa-891">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-891">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-892">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-892">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-893">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-893">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-894">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-894">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-895">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-895">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-query"></a><span data-ttu-id="949aa-896">Zapytanie o komunikat RNDIS klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-896">Device Class Rndis Message Query</span></span> 

#### <a name="ux_device_class_rndis_msg_keep_query"></a><span data-ttu-id="949aa-897">ux_device_class_rndis_msg_keep_query</span><span class="sxs-lookup"><span data-stu-id="949aa-897">ux_device_class_rndis_msg_keep_query</span></span>

<span data-ttu-id="949aa-898">**Ikona** ![ Ikona zapytania komunikatu RNDIS klasy urządzeń](./media/user-guide/usbx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-898">**Icon** ![Device Class Rndis Message Query icon](./media/user-guide/usbx-events/image36.png)</span></span>

<span data-ttu-id="949aa-899">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-899">**Description**</span></span>

<span data-ttu-id="949aa-900">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia RNDIS.</span><span class="sxs-lookup"><span data-stu-id="949aa-900">This event represents a USBX Device Class Rndis Message Query Event.</span></span>

<span data-ttu-id="949aa-901">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-901">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-902">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-902">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-903">Pole informacji 2: RNDIS identyfikatora OID.</span><span class="sxs-lookup"><span data-stu-id="949aa-903">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="949aa-904">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-904">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-905">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-905">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-message-reset"></a><span data-ttu-id="949aa-906">Resetowanie komunikatu klasy urządzenia RNDIS</span><span class="sxs-lookup"><span data-stu-id="949aa-906">Device Class Rndis Message Reset</span></span> 

#### <a name="ux_device_class_rndis_msg_reset"></a><span data-ttu-id="949aa-907">ux_device_class_rndis_msg_reset</span><span class="sxs-lookup"><span data-stu-id="949aa-907">ux_device_class_rndis_msg_reset</span></span>

<span data-ttu-id="949aa-908">**Ikona** ![ Ikona resetowania komunikatu RNDIS klasy urządzeń](./media/user-guide/usbx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-908">**Icon** ![Device Class Rndis Message Reset icon](./media/user-guide/usbx-events/image37.png)</span></span>

<span data-ttu-id="949aa-909">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-909">**Description**</span></span>

<span data-ttu-id="949aa-910">To zdarzenie reprezentuje zdarzenie resetowania komunikatu klasy urządzenia USBX RNDIS.</span><span class="sxs-lookup"><span data-stu-id="949aa-910">This event represents a USBX Device Class Rndis Message Reset Event.</span></span>

<span data-ttu-id="949aa-911">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-911">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-912">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-912">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-913">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-913">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-914">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-914">Info Field 3: Not used.</span></span>

### <a name="device-class-rndis-message-set"></a><span data-ttu-id="949aa-915">RNDIS klasy urządzeń — zestaw komunikatów</span><span class="sxs-lookup"><span data-stu-id="949aa-915">Device Class Rndis Message Set</span></span> 

#### <a name="ux_device_class_rndis_msg_set"></a><span data-ttu-id="949aa-916">ux_device_class_rndis_msg_set</span><span class="sxs-lookup"><span data-stu-id="949aa-916">ux_device_class_rndis_msg_set</span></span>

<span data-ttu-id="949aa-917">**Ikona** ![ Ikona zestawu komunikatów RNDIS klasy urządzeń](./media/user-guide/usbx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-917">**Icon** ![Device Class Rndis Message Set icon](./media/user-guide/usbx-events/image38.png)</span></span>

<span data-ttu-id="949aa-918">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-918">**Description**</span></span>

<span data-ttu-id="949aa-919">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia RNDIS.</span><span class="sxs-lookup"><span data-stu-id="949aa-919">This event represents a USBX Device Class Rndis Message Set Event.</span></span>

<span data-ttu-id="949aa-920">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-920">**Information Fields**</span></span>

- <span data-ttu-id="949aa-921">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-921">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-922">Pole informacji 2: RNDIS identyfikatora OID.</span><span class="sxs-lookup"><span data-stu-id="949aa-922">Info Field 2: Rndis OID.</span></span>
- <span data-ttu-id="949aa-923">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-923">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-924">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-924">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-receive"></a><span data-ttu-id="949aa-925">Odbieranie pakietu RNDIS klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-925">Device Class Rndis Packet Receive</span></span> 

#### <a name="ux_device_class_rndis_packet_receive"></a><span data-ttu-id="949aa-926">ux_device_class_rndis_packet_receive</span><span class="sxs-lookup"><span data-stu-id="949aa-926">ux_device_class_rndis_packet_receive</span></span>

<span data-ttu-id="949aa-927">**Ikona** ![ Ikona odbierania pakietu RNDIS klasy urządzeń](./media/user-guide/usbx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-927">**Icon** ![Device Class Rndis Packet Receive icon](./media/user-guide/usbx-events/image39.png)</span></span>

<span data-ttu-id="949aa-928">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-928">**Description**</span></span>

<span data-ttu-id="949aa-929">To zdarzenie reprezentuje zdarzenie USBX klasy urządzenia RNDIS.</span><span class="sxs-lookup"><span data-stu-id="949aa-929">This event represents a USBX Device Class Rndis Packet Receive Event.</span></span>

<span data-ttu-id="949aa-930">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-930">**Information Fields**</span></span>

- <span data-ttu-id="949aa-931">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-931">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-932">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-932">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-933">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-933">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-934">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-934">Info Field 4: Not used.</span></span>

### <a name="device-class-rndis-packet-transmit"></a><span data-ttu-id="949aa-935">Transmisja pakietów RNDIS klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-935">Device Class Rndis Packet Transmit</span></span> 

#### <a name="ux_device_class_rndis_packet_transmit"></a><span data-ttu-id="949aa-936">ux_device_class_rndis_packet_transmit</span><span class="sxs-lookup"><span data-stu-id="949aa-936">ux_device_class_rndis_packet_transmit</span></span>

<span data-ttu-id="949aa-937">**Ikona** ![ Ikona wysyłania pakietów RNDIS klasy urządzeń](./media/user-guide/usbx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-937">**Icon** ![Device Class Rndis Packet Transmit icon](./media/user-guide/usbx-events/image40.png)</span></span>

<span data-ttu-id="949aa-938">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-938">**Description**</span></span>

<span data-ttu-id="949aa-939">To zdarzenie reprezentuje zdarzenie transmisji pakietu USBX klasy urządzenia RNDIS.</span><span class="sxs-lookup"><span data-stu-id="949aa-939">This event represents a USBX Device Class Rndis Packet Transmit Event.</span></span>

<span data-ttu-id="949aa-940">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-940">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-941">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-941">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-942">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-942">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-943">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-943">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-944">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-944">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-activate"></a><span data-ttu-id="949aa-945">Aktywowanie magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-945">Device Class Storage Activate</span></span> 

#### <a name="ux_device_class_storage_activate"></a><span data-ttu-id="949aa-946">ux_device_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-946">ux_device_class_storage_activate</span></span>

<span data-ttu-id="949aa-947">**Ikona** ![ Ikona aktywacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-947">**Icon** ![Device Class Storage Activate icon](./media/user-guide/usbx-events/image41.png)</span></span>

<span data-ttu-id="949aa-948">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-948">**Description**</span></span>

<span data-ttu-id="949aa-949">To zdarzenie reprezentuje zdarzenie aktywowania magazynu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-949">This event represents a USBX Device Class Storage Activate Event.</span></span>

<span data-ttu-id="949aa-950">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-950">**Information Fields**</span></span>

- <span data-ttu-id="949aa-951">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-951">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-952">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-952">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-953">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-953">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-954">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-954">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-deactivate"></a><span data-ttu-id="949aa-955">Dezaktywacja magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-955">Device Class Storage Deactivate</span></span> 

#### <a name="ux_device_class_storage_deactivate"></a><span data-ttu-id="949aa-956">ux_device_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-956">ux_device_class_storage_deactivate</span></span>

<span data-ttu-id="949aa-957">**Ikona** ![ Ikona dezaktywacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-957">**Icon** ![Device Class Storage Deactivate icon](./media/user-guide/usbx-events/image42.png)</span></span>

<span data-ttu-id="949aa-958">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-958">**Description**</span></span>

<span data-ttu-id="949aa-959">To zdarzenie reprezentuje zdarzenie dezaktywacji magazynu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-959">This event represents a USBX Device Class Storage Deactivate Event.</span></span>

<span data-ttu-id="949aa-960">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-960">**Information Fields**</span></span>

- <span data-ttu-id="949aa-961">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-961">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-962">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-962">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-963">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-963">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-964">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-964">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-format"></a><span data-ttu-id="949aa-965">Format magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-965">Device Class Storage Format</span></span> 

#### <a name="ux_device_class_storage_format"></a><span data-ttu-id="949aa-966">ux_device_class_storage_format</span><span class="sxs-lookup"><span data-stu-id="949aa-966">ux_device_class_storage_format</span></span>

<span data-ttu-id="949aa-967">**Ikona** ![ Ikona formatu magazynu klasy urządzeń](./media/user-guide/usbx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-967">**Icon** ![Device Class Storage Format icon](./media/user-guide/usbx-events/image43.png)</span></span>

<span data-ttu-id="949aa-968">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-968">**Description**</span></span>

<span data-ttu-id="949aa-969">To zdarzenie reprezentuje zdarzenie USBX w formacie magazynu klasy urządzeń.</span><span class="sxs-lookup"><span data-stu-id="949aa-969">This event represents a USBX Device Class Storage Format Event.</span></span>

<span data-ttu-id="949aa-970">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-970">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-971">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-971">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-972">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-972">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-973">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-973">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-974">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-974">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-inquiry"></a><span data-ttu-id="949aa-975">Zapytanie dotyczące magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-975">Device Class Storage Inquiry</span></span> 

#### <a name="ux_device_class_storage_inquiry"></a><span data-ttu-id="949aa-976">ux_device_class_storage_inquiry</span><span class="sxs-lookup"><span data-stu-id="949aa-976">ux_device_class_storage_inquiry</span></span>

<span data-ttu-id="949aa-977">**Ikona** ![ Ikona zapytania dotyczącego magazynu klasy urządzeń](./media/user-guide/usbx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-977">**Icon** ![Device Class Storage Inquiry icon](./media/user-guide/usbx-events/image44.png)</span></span>

<span data-ttu-id="949aa-978">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-978">**Description**</span></span>

<span data-ttu-id="949aa-979">To zdarzenie reprezentuje zdarzenie zapytania dotyczącego magazynu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-979">This event represents a USBX Device Class Storage Inquiry Event.</span></span>

<span data-ttu-id="949aa-980">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-980">**Information Fields**</span></span>

- <span data-ttu-id="949aa-981">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-981">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-982">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-982">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-983">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-983">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-984">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-984">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-select"></a><span data-ttu-id="949aa-985">Wybór trybu przechowywania klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-985">Device Class Storage Mode Select</span></span>

#### <a name="ux_device_class_storage_mode_select"></a><span data-ttu-id="949aa-986">ux_device_class_storage_mode_select</span><span class="sxs-lookup"><span data-stu-id="949aa-986">ux_device_class_storage_mode_select</span></span>

<span data-ttu-id="949aa-987">**Ikona** ![ Ikona wybierania trybu przechowywania klasy urządzeń](./media/user-guide/usbx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-987">**Icon** ![Device Class Storage Mode Select icon](./media/user-guide/usbx-events/image45.png)</span></span>

<span data-ttu-id="949aa-988">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-988">**Description**</span></span>

<span data-ttu-id="949aa-989">To zdarzenie reprezentuje tryb przechowywania klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-989">This event represents a USBX Device Class Storage Mode Select Event.</span></span>

<span data-ttu-id="949aa-990">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-990">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-991">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-991">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-992">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-992">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-993">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-993">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-994">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-994">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-mode-sense"></a><span data-ttu-id="949aa-995">Wykrywanie trybu przechowywania klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-995">Device Class Storage Mode Sense</span></span> 

#### <a name="ux_device_class_storage_mode_sense"></a><span data-ttu-id="949aa-996">ux_device_class_storage_mode_sense</span><span class="sxs-lookup"><span data-stu-id="949aa-996">ux_device_class_storage_mode_sense</span></span>

<span data-ttu-id="949aa-997">**Ikona** ![ Ikona wykrywania trybu przechowywania klasy urządzeń](./media/user-guide/usbx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-997">**Icon** ![Device Class Storage Mode Sense icon](./media/user-guide/usbx-events/image46.png)</span></span>

<span data-ttu-id="949aa-998">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-998">**Description**</span></span>

<span data-ttu-id="949aa-999">To zdarzenie reprezentuje zdarzenie wykrywania klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-999">This event represents a USBX Device Class Storage Mode Sense Event.</span></span>

<span data-ttu-id="949aa-1000">Pola informacji</span><span class="sxs-lookup"><span data-stu-id="949aa-1000">Information Fields</span></span> 

- <span data-ttu-id="949aa-1001">NFO pole 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1001">nfo Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1002">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1002">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1003">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1003">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1004">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1004">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-prevent-allow-media-removal"></a><span data-ttu-id="949aa-1005">Magazyn klasy urządzeń uniemożliwia usunięcie nośnika</span><span class="sxs-lookup"><span data-stu-id="949aa-1005">Device Class Storage Prevent Allow Media Removal</span></span> 

#### <a name="ux_device_class_storage_prevent_allow_media_removal"></a><span data-ttu-id="949aa-1006">ux_device_class_storage_prevent_allow_media_removal</span><span class="sxs-lookup"><span data-stu-id="949aa-1006">ux_device_class_storage_prevent_allow_media_removal</span></span>

<span data-ttu-id="949aa-1007">**Ikona** ![ Nie Zezwalaj na usuwanie nośnika z magazynu klasy urządzeń](./media/user-guide/usbx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1007">**Icon** ![Device Class Storage Prevent Allow Media Removal icon](./media/user-guide/usbx-events/image47.png)</span></span>

<span data-ttu-id="949aa-1008">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1008">**Description**</span></span>

<span data-ttu-id="949aa-1009">To zdarzenie reprezentuje magazyn klasy urządzeń USBX zapobieganie zdarzeniu usuwania multimediów.</span><span class="sxs-lookup"><span data-stu-id="949aa-1009">This event represents a USBX Device Class Storage Prevent Allow Media Removal Event.</span></span>

<span data-ttu-id="949aa-1010">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1010">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1011">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1011">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1012">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1012">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1013">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1013">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1014">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1014">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read"></a><span data-ttu-id="949aa-1015">Odczyt magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1015">Device Class Storage Read</span></span> 

#### <a name="ux_device_class_storage_read"></a><span data-ttu-id="949aa-1016">ux_device_class_storage_read</span><span class="sxs-lookup"><span data-stu-id="949aa-1016">ux_device_class_storage_read</span></span>

<span data-ttu-id="949aa-1017">**Ikona** ![ Ikona odczytu magazynu klasy urządzeń](./media/user-guide/usbx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1017">**Icon** ![Device Class Storage Read icon](./media/user-guide/usbx-events/image48.png)</span></span>

<span data-ttu-id="949aa-1018">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1018">**Description**</span></span>

<span data-ttu-id="949aa-1019">To zdarzenie reprezentuje zdarzenie odczytu magazynu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1019">This event represents a USBX Device Class Storage Read Event.</span></span>

<span data-ttu-id="949aa-1020">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1020">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1021">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1021">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1022">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1022">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1023">Pole informacji 3: sektor.</span><span class="sxs-lookup"><span data-stu-id="949aa-1023">Info Field 3: Sector.</span></span>
- <span data-ttu-id="949aa-1024">Pole informacji 4: liczba sektorów.</span><span class="sxs-lookup"><span data-stu-id="949aa-1024">Info Field 4: Number sectors.</span></span>

### <a name="device-class-storage-read-capacity"></a><span data-ttu-id="949aa-1025">Pojemność odczytu magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1025">Device Class Storage Read Capacity</span></span> 

#### <a name="ux_device_class_storage_read_capacity"></a><span data-ttu-id="949aa-1026">ux_device_class_storage_read_capacity</span><span class="sxs-lookup"><span data-stu-id="949aa-1026">ux_device_class_storage_read_capacity</span></span>

<span data-ttu-id="949aa-1027">**Ikona** ![ Ikona pojemności Odczytaj magazyn klasy urządzeń](./media/user-guide/usbx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1027">**Icon** ![Device Class Storage Read Capacity icon](./media/user-guide/usbx-events/image49.png)</span></span>

<span data-ttu-id="949aa-1028">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1028">**Description**</span></span>

<span data-ttu-id="949aa-1029">To zdarzenie reprezentuje zdarzenie pojemności odczytu magazynu klasy urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1029">This event represents a USBX Device Class Storage Read Capacity Event.</span></span>

<span data-ttu-id="949aa-1030">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1030">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1031">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1031">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1032">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1032">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1033">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1033">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1034">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1034">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-format-capacity"></a><span data-ttu-id="949aa-1035">Pojemność formatu odczytu magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1035">Device Class Storage Read Format Capacity</span></span> 

#### <a name="ux_device_class_storage_read_format_capacity"></a><span data-ttu-id="949aa-1036">ux_device_class_storage_read_format_capacity</span><span class="sxs-lookup"><span data-stu-id="949aa-1036">ux_device_class_storage_read_format_capacity</span></span>

<span data-ttu-id="949aa-1037">**Ikona** ![ Ikona możliwości odczytywania formatu magazynu klasy urządzeń](./media/user-guide/usbx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1037">**Icon** ![Device Class Storage Read Format Capacity icon](./media/user-guide/usbx-events/image50.png)</span></span>

<span data-ttu-id="949aa-1038">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1038">**Description**</span></span>

<span data-ttu-id="949aa-1039">To zdarzenie reprezentuje zdarzenie pojemności Odczytaj USBX magazynu klasy urządzeń.</span><span class="sxs-lookup"><span data-stu-id="949aa-1039">This event represents a USBX Device Class Storage Read Format Capacity Event.</span></span>

<span data-ttu-id="949aa-1040">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1040">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1041">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1041">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1042">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1042">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1043">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1043">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1044">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1044">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-read-toc"></a><span data-ttu-id="949aa-1045">Magazyn klasy urządzeń odczytywanie spisu treści</span><span class="sxs-lookup"><span data-stu-id="949aa-1045">Device Class Storage Read TOC</span></span> 

#### <a name="ux_device_class_storage_read_toc"></a><span data-ttu-id="949aa-1046">ux_device_class_storage_read_toc</span><span class="sxs-lookup"><span data-stu-id="949aa-1046">ux_device_class_storage_read_toc</span></span>

<span data-ttu-id="949aa-1047">**Ikona** ![ Ikona odczytywania SPISu klasy urządzeń](./media/user-guide/usbx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1047">**Icon** ![Device Class Storage Read TOC icon](./media/user-guide/usbx-events/image51.png)</span></span>

<span data-ttu-id="949aa-1048">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1048">**Description**</span></span>

<span data-ttu-id="949aa-1049">To zdarzenie reprezentuje zdarzenie TOC Read USBX Storage klasy urządzeń.</span><span class="sxs-lookup"><span data-stu-id="949aa-1049">This event represents a USBX Device Class Storage Read TOC Event.</span></span>

<span data-ttu-id="949aa-1050">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1050">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1051">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1051">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1052">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1052">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1053">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1053">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1054">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1054">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-request-sense"></a><span data-ttu-id="949aa-1055">Wykrywanie żądania magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1055">Device Class Storage Request Sense</span></span> 

#### <a name="ux_device_class_storage_request_sense"></a><span data-ttu-id="949aa-1056">ux_device_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="949aa-1056">ux_device_class_storage_request_sense</span></span>

<span data-ttu-id="949aa-1057">**Ikona** ![ Ikona wykrywania żądania magazynu klasy urządzeń](./media/user-guide/usbx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1057">**Icon** ![Device Class Storage Request Sense icon](./media/user-guide/usbx-events/image52.png)</span></span>

<span data-ttu-id="949aa-1058">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1058">**Description**</span></span>

<span data-ttu-id="949aa-1059">To zdarzenie reprezentuje zdarzenie wykrywania żądania magazynu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1059">This event represents a USBX Device Class Storage Request Sense Event.</span></span>

<span data-ttu-id="949aa-1060">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1060">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1061">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1061">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1062">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1062">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1063">Pole informacji 3: klucz wykrywania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1063">Info Field 3: Sense key.</span></span>
- <span data-ttu-id="949aa-1064">Pole informacji 4: kod.</span><span class="sxs-lookup"><span data-stu-id="949aa-1064">Info Field 4: Code.</span></span>

### <a name="device-class-storage-start-stop"></a><span data-ttu-id="949aa-1065">Zatrzymanie uruchomienia magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1065">Device Class Storage Start Stop</span></span> 

#### <a name="ux_device_class_storage_start_stop"></a><span data-ttu-id="949aa-1066">ux_device_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="949aa-1066">ux_device_class_storage_start_stop</span></span>

<span data-ttu-id="949aa-1067">**Ikona** ![ Ikona zatrzymania uruchamiania magazynu klasy urządzeń](./media/user-guide/usbx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1067">**Icon** ![Device Class Storage Start Stop icon](./media/user-guide/usbx-events/image53.png)</span></span>

<span data-ttu-id="949aa-1068">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1068">**Description**</span></span>

<span data-ttu-id="949aa-1069">To zdarzenie reprezentuje zdarzenie zatrzymania uruchomienia magazynu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1069">This event represents a USBX Device Class Storage Start Stop Event.</span></span>

<span data-ttu-id="949aa-1070">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1070">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1071">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1071">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1072">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1072">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1073">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1073">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1074">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1074">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-test-ready"></a><span data-ttu-id="949aa-1075">Gotowy Test magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1075">Device Class Storage Test Ready</span></span> 

#### <a name="ux_device_class_storage_test_ready"></a><span data-ttu-id="949aa-1076">ux_device_class_storage_test_ready</span><span class="sxs-lookup"><span data-stu-id="949aa-1076">ux_device_class_storage_test_ready</span></span>

<span data-ttu-id="949aa-1077">**Ikona** ![ Ikona gotowego testu magazynu klasy urządzeń](./media/user-guide/usbx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1077">**Icon** ![Device Class Storage Test Ready icon](./media/user-guide/usbx-events/image54.png)</span></span>

<span data-ttu-id="949aa-1078">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1078">**Description**</span></span>

<span data-ttu-id="949aa-1079">To zdarzenie reprezentuje zdarzenie gotowe do testowania magazynu klasy urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1079">This event represents a USBX Device Class Storage Test Ready Event.</span></span>

<span data-ttu-id="949aa-1080">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1080">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1081">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1081">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1082">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1082">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1083">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1083">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1084">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1084">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-verify"></a><span data-ttu-id="949aa-1085">Weryfikacja magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1085">Device Class Storage Verify</span></span> 

#### <a name="ux_device_class_storage_verify"></a><span data-ttu-id="949aa-1086">ux_device_class_storage_verify</span><span class="sxs-lookup"><span data-stu-id="949aa-1086">ux_device_class_storage_verify</span></span>

<span data-ttu-id="949aa-1087">**Ikona** ![ Ikona weryfikacji magazynu klasy urządzeń](./media/user-guide/usbx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1087">**Icon** ![Device Class Storage Verify icon](./media/user-guide/usbx-events/image55.png)</span></span>

<span data-ttu-id="949aa-1088">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1088">**Description**</span></span>

<span data-ttu-id="949aa-1089">To zdarzenie reprezentuje zdarzenie weryfikacji magazynu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1089">This event represents a USBX Device Class Storage Verify Event.</span></span>

<span data-ttu-id="949aa-1090">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1090">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1091">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1091">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1092">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1092">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1093">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1093">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1094">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1094">Info Field 4: Not used.</span></span>

### <a name="device-class-storage-write"></a><span data-ttu-id="949aa-1095">Zapis magazynu klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1095">Device Class Storage Write</span></span> 

#### <a name="ux_device_class_storage_write"></a><span data-ttu-id="949aa-1096">ux_device_class_storage_write</span><span class="sxs-lookup"><span data-stu-id="949aa-1096">ux_device_class_storage_write</span></span>

<span data-ttu-id="949aa-1097">**Ikona** ![ Ikona zapisu magazynu klasy urządzeń](./media/user-guide/usbx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1097">**Icon** ![Device Class Storage Write icon](./media/user-guide/usbx-events/image56.png)</span></span>

<span data-ttu-id="949aa-1098">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1098">**Description**</span></span>

<span data-ttu-id="949aa-1099">To zdarzenie reprezentuje zdarzenie zapisu magazynu klasy urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1099">This event represents a USBX Device Class Storage Write Event.</span></span>

<span data-ttu-id="949aa-1100">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1100">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1101">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1101">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1102">Pole informacji 2: numer LUN.</span><span class="sxs-lookup"><span data-stu-id="949aa-1102">Info Field 2: Lun.</span></span>
- <span data-ttu-id="949aa-1103">Pole informacji 3: sektor.</span><span class="sxs-lookup"><span data-stu-id="949aa-1103">Info Field 3: Sector.</span></span>
- <span data-ttu-id="949aa-1104">Pole informacji 4: liczba sektorów.</span><span class="sxs-lookup"><span data-stu-id="949aa-1104">Info Field 4: Number sectors.</span></span>

### <a name="device-stack-alternate-setting-get"></a><span data-ttu-id="949aa-1105">Pobieranie alternatywnego ustawienia stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1105">Device Stack Alternate Setting Get</span></span> 

#### <a name="ux_device_class_alternate_setting_get"></a><span data-ttu-id="949aa-1106">ux_device_class_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1106">ux_device_class_alternate_setting_get</span></span>

<span data-ttu-id="949aa-1107">**Ikona** ![ Ikona pobierania alternatywnego ustawienia stosu urządzeń](./media/user-guide/usbx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1107">**Icon** ![Device Stack Alternate Setting Get icon](./media/user-guide/usbx-events/image57.png)</span></span>

<span data-ttu-id="949aa-1108">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1108">**Description**</span></span>

<span data-ttu-id="949aa-1109">To zdarzenie reprezentuje zdarzenie pobrania ustawienia alternatywnego stosu urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1109">This event represents a USBX Device Stack Alternate Setting Get Event.</span></span>

<span data-ttu-id="949aa-1110">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1110">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1111">Pole informacji 1: wartość interfejsu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1111">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="949aa-1112">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1112">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1113">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1113">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1114">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1114">Info Field 4: Not used.</span></span>

### <a name="device-stack-alternate-setting-set"></a><span data-ttu-id="949aa-1115">Zestaw ustawień alternatywnego stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1115">Device Stack Alternate Setting Set</span></span> 

#### <a name="ux_device_class_alternate_setting_set"></a><span data-ttu-id="949aa-1116">ux_device_class_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="949aa-1116">ux_device_class_alternate_setting_set</span></span>

<span data-ttu-id="949aa-1117">**Ikona** ![ Ikona zestawu ustawień alternatywnego stosu urządzeń](./media/user-guide/usbx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1117">**Icon** ![Device Stack Alternate Setting Set icon](./media/user-guide/usbx-events/image58.png)</span></span>

<span data-ttu-id="949aa-1118">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1118">**Description**</span></span>

<span data-ttu-id="949aa-1119">To zdarzenie reprezentuje zdarzenie ustawienia alternatywnego ustawienia stosu urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1119">This event represents a USBX Device Stack Alternate Setting Set Event.</span></span>

<span data-ttu-id="949aa-1120">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1120">**Information Fields**</span></span>
- <span data-ttu-id="949aa-1121">Pole informacji 1: wartość interfejsu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1121">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="949aa-1122">Pole informacji 2: wartość ustawienia alternatywnego.</span><span class="sxs-lookup"><span data-stu-id="949aa-1122">Info Field 2: Alternate setting value.</span></span>
- <span data-ttu-id="949aa-1123">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1123">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1124">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1124">Info Field 4: Not used.</span></span>

### <a name="device-stack-class-register"></a><span data-ttu-id="949aa-1125">Rejestr klas stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1125">Device Stack Class Register</span></span> 

#### <a name="ux_device_stack_class_register"></a><span data-ttu-id="949aa-1126">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="949aa-1126">ux_device_stack_class_register</span></span>

<span data-ttu-id="949aa-1127">**Ikona** ![ Ikona rejestru klasy stosu urządzeń](./media/user-guide/usbx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1127">**Icon** ![Device Stack Class Register icon](./media/user-guide/usbx-events/image59.png)</span></span>

<span data-ttu-id="949aa-1128">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1128">**Description**</span></span>

<span data-ttu-id="949aa-1129">To zdarzenie reprezentuje zdarzenie Register klasy stosu urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1129">This event represents a USBX Device Stack Class Register Event.</span></span>

<span data-ttu-id="949aa-1130">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1130">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1131">Pole informacji 1: Nazwa klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1131">Info Field 1: Class name.</span></span>
- <span data-ttu-id="949aa-1132">Pole informacji 2: numer interfejsu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1132">Info Field 2: Interface number.</span></span>
- <span data-ttu-id="949aa-1133">Pole informacji 3: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-1133">Info Field 3: Parameter.</span></span>
- <span data-ttu-id="949aa-1134">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1134">Info Field 4: Not used.</span></span>

### <a name="device-stack-clear-feature"></a><span data-ttu-id="949aa-1135">Funkcja czyszczenia stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1135">Device Stack Clear Feature</span></span> 

#### <a name="ux_device_stack_clear_feature"></a><span data-ttu-id="949aa-1136">ux_device_stack_clear_feature</span><span class="sxs-lookup"><span data-stu-id="949aa-1136">ux_device_stack_clear_feature</span></span>

<span data-ttu-id="949aa-1137">**Ikona** ![ Ikona czyszczenia funkcji dla stosu urządzeń](./media/user-guide/usbx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1137">**Icon** ![Device Stack Clear Feature icon](./media/user-guide/usbx-events/image60.png)</span></span>

<span data-ttu-id="949aa-1138">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1138">**Description**</span></span>

<span data-ttu-id="949aa-1139">To zdarzenie reprezentuje zdarzenie funkcji Clear USBX stosu urządzeń.</span><span class="sxs-lookup"><span data-stu-id="949aa-1139">This event represents a USBX Device Stack Clear Feature Event.</span></span>

<span data-ttu-id="949aa-1140">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1140">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1141">Pole informacji 1: typ żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1141">Info Field 1: Request type.</span></span>
- <span data-ttu-id="949aa-1142">Pole informacji 2: wartość żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1142">Info Field 2: Request value.</span></span> <span data-ttu-id="949aa-1143">Pole informacji 3: indeks żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1143">Info Field 3: Request index.</span></span>
- <span data-ttu-id="949aa-1144">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1144">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-get"></a><span data-ttu-id="949aa-1145">Pobieranie konfiguracji stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1145">Device Stack Configuration Get</span></span> 

#### <a name="ux_device_stack_configuration_get-t"></a><span data-ttu-id="949aa-1146">ux_device_stack_configuration_get t</span><span class="sxs-lookup"><span data-stu-id="949aa-1146">ux_device_stack_configuration_get t</span></span>

<span data-ttu-id="949aa-1147">**Ikona** ![ Ikona pobierania konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1147">**Icon** ![Device Stack Configuration Get icon](./media/user-guide/usbx-events/image61.png)</span></span>

<span data-ttu-id="949aa-1148">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1148">**Description**</span></span>

<span data-ttu-id="949aa-1149">To zdarzenie reprezentuje zdarzenie pobrania konfiguracji stosu urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1149">This event represents a USBX Device Stack Configuration Get Event.</span></span>

<span data-ttu-id="949aa-1150">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1150">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1151">Pole informacji 1: wartość konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="949aa-1151">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="949aa-1152">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1152">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1153">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1153">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1154">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1154">Info Field 4: Not used.</span></span>

### <a name="device-stack-configuration-set"></a><span data-ttu-id="949aa-1155">Zestaw konfiguracji stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1155">Device Stack Configuration Set</span></span> 

#### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="949aa-1156">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="949aa-1156">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="949aa-1157">**Ikona** ![ Ikona zestawu konfiguracji stosu urządzeń](./media/user-guide/usbx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1157">**Icon** ![Device Stack Configuration Set icon](./media/user-guide/usbx-events/image62.png)</span></span>

<span data-ttu-id="949aa-1158">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1158">**Description**</span></span>

<span data-ttu-id="949aa-1159">To zdarzenie reprezentuje zdarzenie zestawu konfiguracji stosu urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1159">This event represents a USBX Device Stack Configuration Set Event.</span></span>

<span data-ttu-id="949aa-1160">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1160">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1161">Pole informacji 1: wartość konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="949aa-1161">Info Field 1: Configuration value.</span></span>
- <span data-ttu-id="949aa-1162">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1162">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1163">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1163">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1164">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1164">Info Field 4: Not used.</span></span>

### <a name="device-stack-connect"></a><span data-ttu-id="949aa-1165">Łączenie stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1165">Device Stack Connect</span></span> 

#### <a name="ux_device_stack_connect"></a><span data-ttu-id="949aa-1166">ux_device_stack_connect</span><span class="sxs-lookup"><span data-stu-id="949aa-1166">ux_device_stack_connect</span></span>

<span data-ttu-id="949aa-1167">**Ikona** ![ Ikona połączenia z stosem urządzeń](./media/user-guide/usbx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1167">**Icon** ![Device Stack Connect icon](./media/user-guide/usbx-events/image63.png)</span></span>

<span data-ttu-id="949aa-1168">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1168">**Description**</span></span>

<span data-ttu-id="949aa-1169">To zdarzenie reprezentuje zdarzenie wysyłania deskryptora stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1169">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="949aa-1170">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1170">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1171">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1171">Info Field 1: Not used.</span></span>
- <span data-ttu-id="949aa-1172">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1172">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1173">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1173">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1174">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1174">Info Field 4: Not used.</span></span>

### <a name="device-stack-descriptor-send"></a><span data-ttu-id="949aa-1175">Wysyłanie deskryptora stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1175">Device Stack Descriptor Send</span></span> 

#### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="949aa-1176">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="949aa-1176">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="949aa-1177">**Ikona** ![ Ikona wysyłania deskryptora stosu urządzeń](./media/user-guide/usbx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1177">**Icon** ![Device Stack Descriptor Send icon](./media/user-guide/usbx-events/image64.png)</span></span>

<span data-ttu-id="949aa-1178">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1178">**Description**</span></span>

<span data-ttu-id="949aa-1179">To zdarzenie reprezentuje zdarzenie wysyłania deskryptora stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1179">This event represents a USBX Device Stack Descriptor Send Event.</span></span>

<span data-ttu-id="949aa-1180">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1180">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1181">Pole informacji 1: typ deskryptora.</span><span class="sxs-lookup"><span data-stu-id="949aa-1181">Info Field 1: Descriptor type.</span></span>
- <span data-ttu-id="949aa-1182">Pole informacji 2: indeks żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1182">Info Field 2: Request index.</span></span>
- <span data-ttu-id="949aa-1183">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1183">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1184">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1184">Info Field 4: Not used.</span></span>

### <a name="device-stack-disconnect"></a><span data-ttu-id="949aa-1185">Rozłączanie stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1185">Device Stack Disconnect</span></span> 

#### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="949aa-1186">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="949aa-1186">ux_device_stack_disconnect</span></span>

<span data-ttu-id="949aa-1187">**Ikona** ![ Ikona rozłączania stosu urządzeń](./media/user-guide/usbx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1187">**Icon** ![Device Stack Disconnect icon](./media/user-guide/usbx-events/image65.png)</span></span>

<span data-ttu-id="949aa-1188">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1188">**Description**</span></span>

<span data-ttu-id="949aa-1189">To zdarzenie reprezentuje zdarzenie rozłączenia stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1189">This event represents a USBX Device Stack Disconnect Event.</span></span>

<span data-ttu-id="949aa-1190">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1190">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1191">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-1191">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-1192">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1192">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1193">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1193">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1194">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1194">Info Field 4: Not used.</span></span>

### <a name="device-stack-endpoint-stall"></a><span data-ttu-id="949aa-1195">Kabina punktu końcowego stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1195">Device Stack Endpoint Stall</span></span> 

#### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="949aa-1196">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="949aa-1196">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="949aa-1197">**Ikona** ![ Ikona miejsca do punktu końcowego stosu urządzeń](./media/user-guide/usbx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1197">**Icon** ![Device Stack Endpoint Stall icon](./media/user-guide/usbx-events/image66.png)</span></span>

<span data-ttu-id="949aa-1198">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1198">**Description**</span></span>

<span data-ttu-id="949aa-1199">To zdarzenie reprezentuje zdarzenie USBX punktu końcowego stosu urządzeń.</span><span class="sxs-lookup"><span data-stu-id="949aa-1199">This event represents a USBX Device Stack Endpoint Stall Event.</span></span>

<span data-ttu-id="949aa-1200">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1200">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1201">Pole informacji 1: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1201">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="949aa-1202">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1202">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1203">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1203">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1204">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1204">Info Field 4: Not used.</span></span>

### <a name="device-stack-get-status"></a><span data-ttu-id="949aa-1205">Pobieranie stanu stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1205">Device Stack Get Status</span></span> 

#### <a name="ux_device_stack_get_status"></a><span data-ttu-id="949aa-1206">ux_device_stack_get_status</span><span class="sxs-lookup"><span data-stu-id="949aa-1206">ux_device_stack_get_status</span></span>

<span data-ttu-id="949aa-1207">**Ikona** ![ Ikona stanu pobierania stosu urządzeń](./media/user-guide/usbx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1207">**Icon** ![Device Stack Get Status icon](./media/user-guide/usbx-events/image67.png)</span></span>

<span data-ttu-id="949aa-1208">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1208">**Description**</span></span>

<span data-ttu-id="949aa-1209">To zdarzenie reprezentuje zdarzenie stanu Get USBX stosu urządzeń.</span><span class="sxs-lookup"><span data-stu-id="949aa-1209">This event represents a USBX Device Stack Get Status Event.</span></span>

<span data-ttu-id="949aa-1210">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1210">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1211">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1211">Info Field 1: Not used.</span></span>
- <span data-ttu-id="949aa-1212">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1212">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1213">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1213">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1214">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1214">Info Field 4: Not used.</span></span>

### <a name="device-stack-host-wakeup"></a><span data-ttu-id="949aa-1215">Wznawianie hosta stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1215">Device Stack Host Wakeup</span></span> 

#### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="949aa-1216">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="949aa-1216">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="949aa-1217">**Ikona** ![ Ikona wznawiania hosta stosu urządzeń](./media/user-guide/usbx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1217">**Icon** ![Device Stack Host Wakeup icon](./media/user-guide/usbx-events/image68.png)</span></span>

<span data-ttu-id="949aa-1218">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1218">**Description**</span></span>

<span data-ttu-id="949aa-1219">To zdarzenie reprezentuje zdarzenie wznowienia hosta stosu urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1219">This event represents a USBX Device Stack Host Wakeup Event.</span></span>

<span data-ttu-id="949aa-1220">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1220">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1221">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1221">Info Field 1: Not used.</span></span>
- <span data-ttu-id="949aa-1222">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1222">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1223">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1223">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1224">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1224">Info Field 4: Not used.</span></span>

### <a name="device-stack-initialize"></a><span data-ttu-id="949aa-1225">Inicjowanie stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1225">Device Stack Initialize</span></span> 

#### <a name="ux_device_stack_initialize"></a><span data-ttu-id="949aa-1226">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="949aa-1226">ux_device_stack_initialize</span></span>

<span data-ttu-id="949aa-1227">**Ikona** ![ Ikona inicjowania stosu urządzeń](./media/user-guide/usbx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1227">**Icon** ![Device Stack Initialize icon](./media/user-guide/usbx-events/image69.png)</span></span>

<span data-ttu-id="949aa-1228">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1228">**Description**</span></span>

<span data-ttu-id="949aa-1229">To zdarzenie reprezentuje zdarzenie inicjowania stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1229">This event represents a USBX Device Stack Initialize Event.</span></span>

<span data-ttu-id="949aa-1230">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1230">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1231">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1231">Info Field 1: Not used.</span></span>
- <span data-ttu-id="949aa-1232">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1232">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1233">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1233">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1234">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1234">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-delete"></a><span data-ttu-id="949aa-1235">Usuwanie interfejsu stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1235">Device Stack Interface Delete</span></span> 

#### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="949aa-1236">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="949aa-1236">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="949aa-1237">**Ikona** ![ Ikona usuwania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1237">**Icon** ![Device Stack Interface Delete icon](./media/user-guide/usbx-events/image70.png)</span></span>

<span data-ttu-id="949aa-1238">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1238">**Description**</span></span>

<span data-ttu-id="949aa-1239">To zdarzenie reprezentuje zdarzenie usunięcia interfejsu stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1239">This event represents a USBX Device Stack Interface Delete Event.</span></span>

<span data-ttu-id="949aa-1240">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1240">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1241">Pole informacji 1: interfejs.</span><span class="sxs-lookup"><span data-stu-id="949aa-1241">Info Field 1: Interface.</span></span>
- <span data-ttu-id="949aa-1242">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1242">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1243">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1243">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1244">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1244">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-get"></a><span data-ttu-id="949aa-1245">Pobieranie interfejsu stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1245">Device Stack Interface Get</span></span> 

#### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="949aa-1246">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1246">ux_device_stack_interface_get</span></span>

<span data-ttu-id="949aa-1247">**Ikona** ![ Ikona pobierania interfejsu stosu urządzeń](./media/user-guide/usbx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1247">**Icon** ![Device Stack Interface Get icon](./media/user-guide/usbx-events/image71.png)</span></span>

<span data-ttu-id="949aa-1248">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1248">**Description**</span></span>

<span data-ttu-id="949aa-1249">To zdarzenie reprezentuje zdarzenie Get interfejsu stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1249">This event represents a USBX Device Stack Interface Get Event.</span></span>

<span data-ttu-id="949aa-1250">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1250">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1251">Pole informacji 1: wartość interfejsu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1251">Info Field 1: Interface value.</span></span>
- <span data-ttu-id="949aa-1252">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1252">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1253">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1253">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1254">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1254">Info Field 4: Not used.</span></span>

### <a name="device-stack-interface-set"></a><span data-ttu-id="949aa-1255">Zestaw interfejsów stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1255">Device Stack Interface Set</span></span> 

#### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="949aa-1256">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="949aa-1256">ux_device_stack_interface_set</span></span>

<span data-ttu-id="949aa-1257">**Ikona** ![ Ikona zestawu interfejsów stosu urządzeń](./media/user-guide/usbx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1257">**Icon** ![Device Stack Interface Set icon](./media/user-guide/usbx-events/image72.png)</span></span>

<span data-ttu-id="949aa-1258">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1258">**Description**</span></span>

<span data-ttu-id="949aa-1259">To zdarzenie reprezentuje zdarzenie zestawu interfejsu stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1259">This event represents a USBX Device Stack Interface Set Event.</span></span>

<span data-ttu-id="949aa-1260">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1260">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1261">Pole informacji 1: wartość żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1261">Info Field 1: Request value.</span></span> <span data-ttu-id="949aa-1262">Pole informacji 2: indeks żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1262">Info Field 2: Request index.</span></span>
- <span data-ttu-id="949aa-1263">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1263">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1264">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1264">Info Field 4: Not used.</span></span>

### <a name="device-stack-set-feature"></a><span data-ttu-id="949aa-1265">Funkcja zestawu stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1265">Device Stack Set Feature</span></span> 

#### <a name="ux_device_stack_set_feature"></a><span data-ttu-id="949aa-1266">ux_device_stack_set_feature</span><span class="sxs-lookup"><span data-stu-id="949aa-1266">ux_device_stack_set_feature</span></span>

<span data-ttu-id="949aa-1267">**Ikona** ![ Ikona funkcji zestawu stosu urządzeń](./media/user-guide/usbx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1267">**Icon** ![Device Stack Set Feature icon](./media/user-guide/usbx-events/image73.png)</span></span>

<span data-ttu-id="949aa-1268">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1268">**Description**</span></span>

<span data-ttu-id="949aa-1269">To zdarzenie reprezentuje zdarzenie funkcji zestawu stosu urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1269">This event represents a USBX Device Stack Set Feature Event.</span></span>

<span data-ttu-id="949aa-1270">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1270">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1271">Pole informacji 1: wartość żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1271">Info Field 1: Request value.</span></span> <span data-ttu-id="949aa-1272">Pole informacji 2: indeks żądania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1272">Info Field 2: Request index.</span></span>
- <span data-ttu-id="949aa-1273">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1273">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1274">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1274">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-abort"></a><span data-ttu-id="949aa-1275">Przerwanie transferu stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1275">Device Stack Transfer Abort</span></span> 

#### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="949aa-1276">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="949aa-1276">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="949aa-1277">**Ikona** ![ Ikona przerwania transferu stosu urządzeń](./media/user-guide/usbx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1277">**Icon** ![Device Stack Transfer Abort icon](./media/user-guide/usbx-events/image74.png)</span></span>

<span data-ttu-id="949aa-1278">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1278">**Description**</span></span>

<span data-ttu-id="949aa-1279">To zdarzenie reprezentuje zdarzenie przerwania transferu stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1279">This event represents a USBX Device Stack Transfer Abort Event.</span></span>

<span data-ttu-id="949aa-1280">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1280">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1281">Pole informacji 1: żądanie transferu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1281">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="949aa-1282">Pole informacji 2: kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-1282">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="949aa-1283">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1283">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1284">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1284">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-all-request-abort"></a><span data-ttu-id="949aa-1285">Przerwanie transferu wszystkich żądań przez stos urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1285">Device Stack Transfer All Request Abort</span></span> 

#### <a name="ux_device_stack_transfer_all_request_abort"></a><span data-ttu-id="949aa-1286">ux_device_stack_transfer_all_request_abort</span><span class="sxs-lookup"><span data-stu-id="949aa-1286">ux_device_stack_transfer_all_request_abort</span></span>

<span data-ttu-id="949aa-1287">**Ikona** ![ Ikona przerwania transferu wszystkich żądań w stosie urządzeń](./media/user-guide/usbx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1287">**Icon** ![Device Stack Transfer All Request Abort icon](./media/user-guide/usbx-events/image75.png)</span></span>

<span data-ttu-id="949aa-1288">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1288">**Description**</span></span>

<span data-ttu-id="949aa-1289">To zdarzenie reprezentuje zdarzenie przerwania transferu wszystkich żądań USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1289">This event represents a USBX Device Stack Transfer All Request Abort Event.</span></span>

<span data-ttu-id="949aa-1290">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1290">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1291">Pole informacji 1: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1291">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="949aa-1292">Pole informacji 2: kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-1292">Info Field 2: Completion code.</span></span>
- <span data-ttu-id="949aa-1293">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1293">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1294">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1294">Info Field 4: Not used.</span></span>

### <a name="device-stack-transfer-request"></a><span data-ttu-id="949aa-1295">Żądanie transferu stosu urządzeń</span><span class="sxs-lookup"><span data-stu-id="949aa-1295">Device Stack Transfer Request</span></span> 

#### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="949aa-1296">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="949aa-1296">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="949aa-1297">**Ikona** ![ Ikona żądania transferu stosu urządzeń](./media/user-guide/usbx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1297">**Icon** ![Device Stack Transfer Request icon](./media/user-guide/usbx-events/image76.png)</span></span>

<span data-ttu-id="949aa-1298">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1298">**Description**</span></span>

<span data-ttu-id="949aa-1299">To zdarzenie reprezentuje zdarzenie żądania transferu stosu urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1299">This event represents a USBX Device Stack Transfer Request Event.</span></span>

<span data-ttu-id="949aa-1300">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1300">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1301">Pole informacji 1: żądanie transferu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1301">Info Field 1: Transfer request.</span></span>
- <span data-ttu-id="949aa-1302">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1302">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1303">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1303">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1304">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1304">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-activate"></a><span data-ttu-id="949aa-1305">ASIX Aktywuj klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1305">Host Class Asix Activate</span></span> 

#### <a name="ux_host_class_asix_activate"></a><span data-ttu-id="949aa-1306">ux_host_class_asix_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1306">ux_host_class_asix_activate</span></span>

<span data-ttu-id="949aa-1307">**Ikona** ![ Ikona ASIX aktywowania klasy hosta](./media/user-guide/usbx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1307">**Icon** ![Host Class Asix Activate icon](./media/user-guide/usbx-events/image77.png)</span></span>

<span data-ttu-id="949aa-1308">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1308">**Description**</span></span>

<span data-ttu-id="949aa-1309">To zdarzenie reprezentuje USBX klasy hosta ASIX Aktywuj.</span><span class="sxs-lookup"><span data-stu-id="949aa-1309">This event represents a USBX Host Class Asix Activate.</span></span>

<span data-ttu-id="949aa-1310">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1310">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1311">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1311">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1312">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1312">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1313">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1313">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1314">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1314">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-deactivate"></a><span data-ttu-id="949aa-1315">ASIX Dezaktywuj klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1315">Host Class Asix Deactivate</span></span> 

#### <a name="ux_host_class_asix_deactivate"></a><span data-ttu-id="949aa-1316">ux_host_class_asix_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1316">ux_host_class_asix_deactivate</span></span>

<span data-ttu-id="949aa-1317">**Ikona** ![ Ikona dezaktywowania klasy hosta ASIX](./media/user-guide/usbx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1317">**Icon** ![Host Class Asix Deactivate icon](./media/user-guide/usbx-events/image78.png)</span></span>

<span data-ttu-id="949aa-1318">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1318">**Description**</span></span>

<span data-ttu-id="949aa-1319">To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX ASIX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1319">This event represents a USBX Host Class Asix Deactivate Event.</span></span>

<span data-ttu-id="949aa-1320">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1320">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1321">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1321">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1322">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1322">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1323">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1323">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1324">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1324">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-interrupt-notification"></a><span data-ttu-id="949aa-1325">Powiadomienie o przerwaniu ASIX klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1325">Host Class Asix Interrupt Notification</span></span> 

#### <a name="ux_host_class_asix_interrupt_notification"></a><span data-ttu-id="949aa-1326">ux_host_class_asix_interrupt_notification</span><span class="sxs-lookup"><span data-stu-id="949aa-1326">ux_host_class_asix_interrupt_notification</span></span>

<span data-ttu-id="949aa-1327">**Ikona** ![ Ikona powiadomienia o przerwaniu ASIX klasy hosta](./media/user-guide/usbx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1327">**Icon** ![Host Class Asix Interrupt Notification icon](./media/user-guide/usbx-events/image79.png)</span></span>

<span data-ttu-id="949aa-1328">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1328">**Description**</span></span>

<span data-ttu-id="949aa-1329">To zdarzenie reprezentuje zdarzenie USBXa przerwania klasy hosta ASIX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1329">This event represents a USBX Host Class Asix Interrupt Notification Event.</span></span>

<span data-ttu-id="949aa-1330">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1330">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1331">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1331">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-1332">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1332">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1333">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1333">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1334">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1334">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-read"></a><span data-ttu-id="949aa-1335">Odczytaj ASIX klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1335">Host Class Asix Read</span></span> 

#### <a name="ux_host_class_asix_read"></a><span data-ttu-id="949aa-1336">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="949aa-1336">ux_host_class_asix_read</span></span>

<span data-ttu-id="949aa-1337">**Ikona** ![ Ikona odczytu ASIX klasy hosta](./media/user-guide/usbx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1337">**Icon** ![Host Class Asix Read icon](./media/user-guide/usbx-events/image80.png)</span></span>

<span data-ttu-id="949aa-1338">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1338">**Description**</span></span>

<span data-ttu-id="949aa-1339">To zdarzenie reprezentuje zdarzenie odczytu USBX klasy hosta ASIX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1339">This event represents a USBX Host Class Asix Read Event.</span></span>

<span data-ttu-id="949aa-1340">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1340">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1341">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1341">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1342">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1342">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1343">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-1343">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-1344">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1344">Info Field 4: Not used.</span></span>

### <a name="host-class-asix-write"></a><span data-ttu-id="949aa-1345">ASIX zapisu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1345">Host Class Asix Write</span></span> 

#### <a name="ux_host_class_asix_write"></a><span data-ttu-id="949aa-1346">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="949aa-1346">ux_host_class_asix_write</span></span>

<span data-ttu-id="949aa-1347">**Ikona** ![ Ikona zapisu ASIX klasy hosta](./media/user-guide/usbx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1347">**Icon** ![Host Class Asix Write icon](./media/user-guide/usbx-events/image81.png)</span></span>

<span data-ttu-id="949aa-1348">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1348">**Description**</span></span>

<span data-ttu-id="949aa-1349">To zdarzenie reprezentuje zdarzenie zapisu USBX klasy hosta ASIX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1349">This event represents a USBX Host Class Asix Write Event.</span></span>

<span data-ttu-id="949aa-1350">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1350">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1351">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1351">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1352">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1352">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1353">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-1353">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-1354">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1354">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-activate"></a><span data-ttu-id="949aa-1355">Aktywuj klasy hosta audio</span><span class="sxs-lookup"><span data-stu-id="949aa-1355">Host Class Audio Activate</span></span> 

#### <a name="ux_host_class_audio_activate"></a><span data-ttu-id="949aa-1356">ux_host_class_audio_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1356">ux_host_class_audio_activate</span></span>

<span data-ttu-id="949aa-1357">**Ikona** ![ Ikona aktywacji dźwięku klasy hosta](./media/user-guide/usbx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1357">**Icon** ![Host Class Audio Activate icon](./media/user-guide/usbx-events/image82.png)</span></span>

<span data-ttu-id="949aa-1358">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1358">**Description**</span></span>

<span data-ttu-id="949aa-1359">To zdarzenie reprezentuje zdarzenie aktywowania audio klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1359">This event represents a USBX Host Class Audio Activate Event.</span></span>

<span data-ttu-id="949aa-1360">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1360">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1361">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1361">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1362">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1362">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1363">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1363">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1364">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1364">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-get"></a><span data-ttu-id="949aa-1365">Pobieranie wartości kontrolki audio klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1365">Host Class Audio Control Value Get</span></span> 

#### <a name="ux_host_class_audio_control_value_get"></a><span data-ttu-id="949aa-1366">ux_host_class_audio_control_value_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1366">ux_host_class_audio_control_value_get</span></span>

<span data-ttu-id="949aa-1367">**Ikona** ![ Ikona pobierania wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1367">**Icon** ![Host Class Audio Control Value Get icon](./media/user-guide/usbx-events/image83.png)</span></span>

<span data-ttu-id="949aa-1368">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1368">**Description**</span></span>

<span data-ttu-id="949aa-1369">To zdarzenie reprezentuje zdarzenie pobrania wartości kontrolki audio klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1369">This event represents a USBX Host Class Audio Control Value Get Event.</span></span>

<span data-ttu-id="949aa-1370">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1370">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1371">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1371">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1372">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1372">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1373">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1373">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1374">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1374">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-control-value-set"></a><span data-ttu-id="949aa-1375">Zestaw wartości kontrolki audio klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1375">Host Class Audio Control Value Set</span></span> 

#### <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="949aa-1376">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="949aa-1376">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="949aa-1377">**Ikona** ![ Ikona zestawu wartości kontrolki audio klasy hosta](./media/user-guide/usbx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1377">**Icon** ![Host Class Audio Control Value Set icon](./media/user-guide/usbx-events/image84.png)</span></span>

<span data-ttu-id="949aa-1378">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1378">**Description**</span></span>

<span data-ttu-id="949aa-1379">To zdarzenie przedstawia wewnętrzne zdarzenie przetwarzania odroczonego sterownika we/wy NetX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1379">This event represents an internal NetX I/O driver deferred processing event.</span></span>

<span data-ttu-id="949aa-1380">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1380">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1381">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1381">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1382">Pole informacji 2: formant audio.</span><span class="sxs-lookup"><span data-stu-id="949aa-1382">Info Field 2: Audio control.</span></span>
- <span data-ttu-id="949aa-1383">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1383">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1384">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1384">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-deactivate"></a><span data-ttu-id="949aa-1385">Dezaktywacja audio klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1385">Host Class Audio Deactivate</span></span> 

#### <a name="ux_host_class_audio_deactivate"></a><span data-ttu-id="949aa-1386">ux_host_class_audio_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1386">ux_host_class_audio_deactivate</span></span>

<span data-ttu-id="949aa-1387">**Ikona** ![ Ikona dezaktywacji audio klasy hosta](./media/user-guide/usbx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1387">**Icon** ![Host Class Audio Deactivate icon](./media/user-guide/usbx-events/image85.png)</span></span>

<span data-ttu-id="949aa-1388">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1388">**Description**</span></span>

<span data-ttu-id="949aa-1389">To zdarzenie reprezentuje zdarzenie dezaktywacji audio klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1389">This event represents a USBX Host Class Audio Deactivate Event.</span></span>

<span data-ttu-id="949aa-1390">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1390">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1391">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1391">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1392">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1392">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1393">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1393">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1394">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1394">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-read"></a><span data-ttu-id="949aa-1395">Odczyt klasy hosta audio</span><span class="sxs-lookup"><span data-stu-id="949aa-1395">Host Class Audio Read</span></span> 

#### <a name="ux_host_class_audio_read"></a><span data-ttu-id="949aa-1396">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="949aa-1396">ux_host_class_audio_read</span></span>

<span data-ttu-id="949aa-1397">**Ikona** ![ Ikona odczytu audio klasy hosta](./media/user-guide/usbx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1397">**Icon** ![Host Class Audio Read icon](./media/user-guide/usbx-events/image86.png)</span></span>

<span data-ttu-id="949aa-1398">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1398">**Description**</span></span>

<span data-ttu-id="949aa-1399">To zdarzenie reprezentuje zdarzenie odczytu audio klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1399">This event represents a USBX Host Class Audio Read Event.</span></span>

- <span data-ttu-id="949aa-1400">Pola informacji</span><span class="sxs-lookup"><span data-stu-id="949aa-1400">Information Fields</span></span> 
- <span data-ttu-id="949aa-1401">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1401">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1402">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1402">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1403">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-1403">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-1404">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1404">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-get"></a><span data-ttu-id="949aa-1405">Pobieranie próbkowania audio klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1405">Host Class Audio Streaming Sampling Get</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="949aa-1406">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1406">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="949aa-1407">**Ikona** ![ Ikona pobierania próbkowania audio klasy hosta](./media/user-guide/usbx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1407">**Icon** ![Host Class Audio Streaming Sampling Get icon](./media/user-guide/usbx-events/image87.png)</span></span>

<span data-ttu-id="949aa-1408">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1408">**Description**</span></span>

<span data-ttu-id="949aa-1409">To zdarzenie reprezentuje zdarzenie pobrania próbkowania audio klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1409">This event represents a USBX Host Class Audio Streaming Sampling Get Event.</span></span>

<span data-ttu-id="949aa-1410">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1410">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1411">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1411">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1412">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1412">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1413">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1413">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1414">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1414">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-streaming-sampling-set"></a><span data-ttu-id="949aa-1415">Zestaw próbkowania przesyłania strumieniowego audio klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1415">Host Class Audio Streaming Sampling Set</span></span> 

#### <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="949aa-1416">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="949aa-1416">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="949aa-1417">**Ikona** ![ Ikona zestawu próbkowania przesyłania strumieniowego audio klasy hosta](./media/user-guide/usbx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1417">**Icon** ![Host Class Audio Streaming Sampling Set icon](./media/user-guide/usbx-events/image88.png)</span></span>

<span data-ttu-id="949aa-1418">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1418">**Description**</span></span>

<span data-ttu-id="949aa-1419">To zdarzenie reprezentuje zdarzenie zestawu próbkowania audio klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1419">This event represents a USBX Host Class Audio Streaming Sampling Set Event.</span></span>

<span data-ttu-id="949aa-1420">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1420">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1421">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1421">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1422">Pole informacji 2: próbkowanie audio.</span><span class="sxs-lookup"><span data-stu-id="949aa-1422">Info Field 2: Audio Sampling.</span></span>
- <span data-ttu-id="949aa-1423">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1423">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1424">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1424">Info Field 4: Not used.</span></span>

### <a name="host-class-audio-write"></a><span data-ttu-id="949aa-1425">Zapis audio klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1425">Host Class Audio Write</span></span> 

#### <a name="ux_host_class_audio_write"></a><span data-ttu-id="949aa-1426">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="949aa-1426">ux_host_class_audio_write</span></span>

<span data-ttu-id="949aa-1427">**Ikona** ![ Ikona zapisu audio klasy hosta](./media/user-guide/usbx-events/image89.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1427">**Icon** ![Host Class Audio Write icon](./media/user-guide/usbx-events/image89.png)</span></span>

<span data-ttu-id="949aa-1428">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1428">**Description**</span></span>

<span data-ttu-id="949aa-1429">To zdarzenie reprezentuje zdarzenie zapisu audio klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1429">This event represents a USBX Host Class Audio Write Event.</span></span>

<span data-ttu-id="949aa-1430">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1430">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1431">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1431">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1432">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1432">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1433">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-1433">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-1434">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1434">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-activate"></a><span data-ttu-id="949aa-1435">Aktywacja ACM klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1435">Host Class Cdc Acm Activate</span></span> 

#### <a name="ux_host_class_cdc_acm_activate"></a><span data-ttu-id="949aa-1436">ux_host_class_cdc_acm_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1436">ux_host_class_cdc_acm_activate</span></span>

<span data-ttu-id="949aa-1437">**Ikona** ![ Klasa hosta C D C A C M ikona aktywacji](./media/user-guide/usbx-events/image90.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1437">**Icon** ![Host Class C D C A C M Activate icon](./media/user-guide/usbx-events/image90.png)</span></span>

<span data-ttu-id="949aa-1438">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1438">**Description**</span></span>

<span data-ttu-id="949aa-1439">To zdarzenie reprezentuje zdarzenie Activate (USBX) klasy hosta przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1439">This event represents a USBX Host Class Cdc Acm Activate Event.</span></span>

<span data-ttu-id="949aa-1440">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1440">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1441">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1441">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1442">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1442">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1443">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1443">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1444">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1444">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-deactivate"></a><span data-ttu-id="949aa-1445">Klasa hosta przechwytywania danych ACM</span><span class="sxs-lookup"><span data-stu-id="949aa-1445">Host Class Cdc Acm Deactivate</span></span> 

#### <a name="ux_host_class_cdc_acm_deactivate"></a><span data-ttu-id="949aa-1446">ux_host_class_cdc_acm_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1446">ux_host_class_cdc_acm_deactivate</span></span>

<span data-ttu-id="949aa-1447">**Ikona** ![ Klasa hosta C D C A C M ikona dezaktywowania](./media/user-guide/usbx-events/image91.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1447">**Icon** ![Host Class C D C A C M Deactivate icon](./media/user-guide/usbx-events/image91.png)</span></span>

<span data-ttu-id="949aa-1448">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1448">**Description**</span></span>

<span data-ttu-id="949aa-1449">To zdarzenie reprezentuje USBXą klasę hosta przechwytywania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="949aa-1449">This event represents a USBX Host Class Cdc Acm Deactivate Event.</span></span>

<span data-ttu-id="949aa-1450">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1450">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1451">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1451">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1452">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1452">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1453">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1453">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1454">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1454">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-in-pipe"></a><span data-ttu-id="949aa-1455">Klasa hosta — przerywanie operacji IOCTL w potoku</span><span class="sxs-lookup"><span data-stu-id="949aa-1455">Host Class Cdc Acm Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_abort_in_pipe"></a><span data-ttu-id="949aa-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="949aa-1456">ux_host_class_cdc_acm_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="949aa-1457">**Ikona** ![ Klasa hosta C D C A c M I O s T L przerwa w potoku](./media/user-guide/usbx-events/image92.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1457">**Icon** ![Host Class C D C A C M I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image92.png)</span></span>

<span data-ttu-id="949aa-1458">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1458">**Description**</span></span>

<span data-ttu-id="949aa-1459">To zdarzenie reprezentuje klasę hosta USBX przechwytywanie zdarzeń IOCTL w zdarzeniu potoku.</span><span class="sxs-lookup"><span data-stu-id="949aa-1459">This event represents a USBX Host Class Cdc Acm Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="949aa-1460">Pola informacji</span><span class="sxs-lookup"><span data-stu-id="949aa-1460">Information Fields</span></span> 

- <span data-ttu-id="949aa-1461">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1461">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1462">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1462">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-1463">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1463">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1464">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1464">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-abort-out-pipe"></a><span data-ttu-id="949aa-1465">Klasa hosta Przerzucanie polecenia IOCTL w usłudze ACM przerywanie potoku</span><span class="sxs-lookup"><span data-stu-id="949aa-1465">Host Class Cdc Acm Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_cdc_acm_ioct_abort_out_pipe"></a><span data-ttu-id="949aa-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="949aa-1466">ux_host_class_cdc_acm_ioct_abort_out_pipe</span></span>

<span data-ttu-id="949aa-1467">**Ikona** ! [[Klasa hosta c D c A c M I o c T L ikona przerwania w potoku](./media/user-guide/usbx-events/image93.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1467">**Icon** ![[Host Class C D C A C M I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image93.png)</span></span>

<span data-ttu-id="949aa-1468">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1468">**Description**</span></span>

<span data-ttu-id="949aa-1469">To zdarzenie reprezentuje USBX klasy hosta przechwytywania zdarzeń IOCTL przerywanie potoku.</span><span class="sxs-lookup"><span data-stu-id="949aa-1469">This event represents a USBX Host Class Cdc Acm Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="949aa-1470">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1470">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1471">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1471">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1472">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1472">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-1473">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1473">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1474">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1474">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-device-status"></a><span data-ttu-id="949aa-1475">Klasa hosta przechwytywania żądania IOCTL pobieranie stanu urządzenia</span><span class="sxs-lookup"><span data-stu-id="949aa-1475">Host Class Cdc Acm Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_device_status"></a><span data-ttu-id="949aa-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="949aa-1476">ux_host_class_cdc_acm_ioctl_get_device_status</span></span>

<span data-ttu-id="949aa-1477">**Ikona** ![ Klasa hosta C D C A c M I O C T L Pobierz ikonę stanu urządzenia](./media/user-guide/usbx-events/image94.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1477">**Icon** ![Host Class C D C A C M I O C T L Get Device Status icon](./media/user-guide/usbx-events/image94.png)</span></span>

<span data-ttu-id="949aa-1478">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1478">**Description**</span></span>

<span data-ttu-id="949aa-1479">To zdarzenie reprezentuje klasę hosta USBX, która umożliwia pobieranie zdarzenia stanu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-1479">This event represents a USBX Host Class Cdc Acm Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="949aa-1480">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1480">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1481">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1481">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1482">Pole informacji 2: stan urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-1482">Info Field 2: Device status.</span></span>
- <span data-ttu-id="949aa-1483">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1483">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1484">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1484">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-get-line-coding"></a><span data-ttu-id="949aa-1485">Klasa hosta przechwytywania operacji IOCTL pobieranie kodowania wierszy</span><span class="sxs-lookup"><span data-stu-id="949aa-1485">Host Class Cdc Acm Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="949aa-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="949aa-1486">ux_host_class_cdc_acm_ioctl_get_line_coding</span></span>

<span data-ttu-id="949aa-1487">**Ikona** ![ Klasa hosta C D C A c M I O C T L ikona Uzyskaj kodowanie wiersza](./media/user-guide/usbx-events/image95.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1487">**Icon** ![Host Class C D C A C M I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image95.png)</span></span>

<span data-ttu-id="949aa-1488">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1488">**Description**</span></span>

<span data-ttu-id="949aa-1489">To zdarzenie reprezentuje klasę hosta USBX przechwytywanie zdarzeń IOCTL pobieranie wiersza zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-1489">This event represents a USBX Host Class Cdc Acm Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="949aa-1490">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1490">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1491">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1491">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1492">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-1492">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-1493">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1493">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1494">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1494">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-notification-callback"></a><span data-ttu-id="949aa-1495">Wywołanie zwrotne powiadomień IOCTL klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1495">Host Class Cdc Acm Ioctl Notification Callback</span></span>

#### <a name="ux_host_class_cdc_acm_ioctl_notification_callback"></a><span data-ttu-id="949aa-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span><span class="sxs-lookup"><span data-stu-id="949aa-1496">ux_host_class_cdc_acm_ioctl_notification_callback</span></span>

<span data-ttu-id="949aa-1497">**Ikona** ![ Klasa hosta C D C A c M I O c T L ikona wywołania zwrotnego powiadomienia](./media/user-guide/usbx-events/image96.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1497">**Icon** ![Host Class C D C A C M I O C T L Notification Callback icon](./media/user-guide/usbx-events/image96.png)</span></span>

<span data-ttu-id="949aa-1498">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1498">**Description**</span></span>

<span data-ttu-id="949aa-1499">To zdarzenie reprezentuje klasę hosta USBX zdarzenia wywołania zwrotnego powiadomienia dla operacji IOCTL.</span><span class="sxs-lookup"><span data-stu-id="949aa-1499">This event represents a USBX Host Class Cdc Acm Ioctl Notification Callback Event.</span></span>

<span data-ttu-id="949aa-1500">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1500">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1501">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1501">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1502">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-1502">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-1503">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1503">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1504">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1504">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-send-break"></a><span data-ttu-id="949aa-1505">Klasa hosta przechwytywania przerwania operacji IOCTL</span><span class="sxs-lookup"><span data-stu-id="949aa-1505">Host Class Cdc Acm Ioctl Send Break</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_send_break"></a><span data-ttu-id="949aa-1506">ux_host_class_cdc_acm_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="949aa-1506">ux_host_class_cdc_acm_ioctl_send_break</span></span>

<span data-ttu-id="949aa-1507">**Ikona** ![ Klasa hosta C D C A c M I O C T L ikona przerwania wysyłania](./media/user-guide/usbx-events/image97.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1507">**Icon** ![Host Class C D C A C M I O C T L Send Break icon](./media/user-guide/usbx-events/image97.png)</span></span>

<span data-ttu-id="949aa-1508">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1508">**Description**</span></span>

<span data-ttu-id="949aa-1509">To zdarzenie reprezentuje klasę hosta USBX zdarzenia przerwania wysyłania IOCTL.</span><span class="sxs-lookup"><span data-stu-id="949aa-1509">This event represents a USBX Host Class Cdc Acm Ioctl Send Break Event.</span></span>

<span data-ttu-id="949aa-1510">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1510">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1511">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1511">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1512">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-1512">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-1513">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1513">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1514">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1514">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-coding"></a><span data-ttu-id="949aa-1515">Klasa hosta przechwytywania operacji IOCTL ustawienia kodowania linii</span><span class="sxs-lookup"><span data-stu-id="949aa-1515">Host Class Cdc Acm Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="949aa-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="949aa-1516">ux_host_class_cdc_acm_ioctl_set_line_coding</span></span>

<span data-ttu-id="949aa-1517">**Ikona** ![ Klasa hosta C D C A c M I O C T L ustawienia ikona kodowania linii ](./media/user-guide/usbx-events/image97.png) ] (./media/user-guide/usbx-events/image98.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1517">**Icon** ![The Host Class C D C A C M I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image97.png) icon](./media/user-guide/usbx-events/image98.png)</span></span>

<span data-ttu-id="949aa-1518">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1518">**Description**</span></span>

<span data-ttu-id="949aa-1519">To zdarzenie reprezentuje klasę hosta USBX. zdarzenie IOCTL ustawiania kodowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="949aa-1519">This event represents a USBX Host Class Cdc Acm Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="949aa-1520">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1520">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1521">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1521">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1522">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-1522">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-1523">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1523">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1524">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1524">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-ioctl-set-line-state"></a><span data-ttu-id="949aa-1525">Klasa hosta Przekreśl stan wiersza zestawu IOCTL ACM</span><span class="sxs-lookup"><span data-stu-id="949aa-1525">Host Class Cdc Acm Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="949aa-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="949aa-1526">ux_host_class_cdc_acm_ioctl_set_line_state</span></span>

<span data-ttu-id="949aa-1527">**Ikona** ![ Klasa hosta C D C A c M I O C T L ikona stanu wiersza](./media/user-guide/usbx-events/image99.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1527">**Icon** ![Host Class C D C A C M I O C T L Set Line State icon](./media/user-guide/usbx-events/image99.png)</span></span>

<span data-ttu-id="949aa-1528">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1528">**Description**</span></span>

<span data-ttu-id="949aa-1529">To zdarzenie reprezentuje klasę hosta USBX zdarzenia IOCTL ustawiania stanu wiersza.</span><span class="sxs-lookup"><span data-stu-id="949aa-1529">This event represents a USBX Host Class Cdc Acm Ioctl Set Line State Event.</span></span>

<span data-ttu-id="949aa-1530">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1530">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1531">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1531">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1532">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-1532">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-1533">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1533">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1534">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1534">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-read"></a><span data-ttu-id="949aa-1535">Klasa hosta — odczyt przechwytywania ACM</span><span class="sxs-lookup"><span data-stu-id="949aa-1535">Host Class Cdc Acm Read</span></span> 

#### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="949aa-1536">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="949aa-1536">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="949aa-1537">**Ikona** ![ Klasa hosta C D C A C M ikona odczytu](./media/user-guide/usbx-events/image100.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1537">**Icon** ![Host Class C D C A C M Read icon](./media/user-guide/usbx-events/image100.png)</span></span>

<span data-ttu-id="949aa-1538">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1538">**Description**</span></span>

<span data-ttu-id="949aa-1539">To zdarzenie reprezentuje zdarzenie odczytu klasy USBX przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="949aa-1539">This event represents a USBX Host Class Cdc Acm Read Event.</span></span>

<span data-ttu-id="949aa-1540">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1540">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1541">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1541">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1542">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1542">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1543">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-1543">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="949aa-1544">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1544">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-start"></a><span data-ttu-id="949aa-1545">Rozpoczęcie odbierania ACM klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1545">Host Class Cdc Acm Reception Start</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="949aa-1546">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="949aa-1546">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="949aa-1547">**Ikona** ![ Klasa hosta C D C A p M — ikona startowa przyjęcia](./media/user-guide/usbx-events/image101.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1547">**Icon** ![Host Class C D C A C M Reception Start icon](./media/user-guide/usbx-events/image101.png)</span></span>

<span data-ttu-id="949aa-1548">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1548">**Description**</span></span>

<span data-ttu-id="949aa-1549">To zdarzenie reprezentuje klasę hosta USBX zdarzenia rozpoczęcia odbioru ACM.</span><span class="sxs-lookup"><span data-stu-id="949aa-1549">This event represents a USBX Host Class Cdc Acm Reception Start Event.</span></span>

<span data-ttu-id="949aa-1550">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1550">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1551">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1551">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1552">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1552">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1553">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1553">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1554">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1554">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-reception-stop"></a><span data-ttu-id="949aa-1555">Klasa hosta przełączać do przechwytywania ACM</span><span class="sxs-lookup"><span data-stu-id="949aa-1555">Host Class Cdc Acm Reception Stop</span></span> 

#### <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="949aa-1556">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="949aa-1556">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="949aa-1557">**Ikona** ![ Klasa hosta C D C, ikona zatrzymania odbierania C M](./media/user-guide/usbx-events/image102.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1557">**Icon** ![Host Class C D C A C M Reception Stop icon](./media/user-guide/usbx-events/image102.png)</span></span>

<span data-ttu-id="949aa-1558">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1558">**Description**</span></span>

<span data-ttu-id="949aa-1559">To zdarzenie reprezentuje klasę hosta USBX przełączać zdarzenie zatrzymania odbioru ACM.</span><span class="sxs-lookup"><span data-stu-id="949aa-1559">This event represents a USBX Host Class Cdc Acm Reception Stop Event.</span></span>

<span data-ttu-id="949aa-1560">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1560">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1561">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1561">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1562">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1562">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1563">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1563">Info Field 4: Not used.</span></span>

### <a name="host-class-cdc-acm-write"></a><span data-ttu-id="949aa-1564">Klasa hosta przechwytywania ACM</span><span class="sxs-lookup"><span data-stu-id="949aa-1564">Host Class Cdc Acm Write</span></span> 

#### <a name="ux_host_class_acm_write"></a><span data-ttu-id="949aa-1565">ux_host_class_acm_write</span><span class="sxs-lookup"><span data-stu-id="949aa-1565">ux_host_class_acm_write</span></span>

<span data-ttu-id="949aa-1566">**Ikona** ![ Klasa hosta C D C A C M ikona zapisu](./media/user-guide/usbx-events/image103.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1566">**Icon** ![Host Class C D C A C M Write icon](./media/user-guide/usbx-events/image103.png)</span></span>

<span data-ttu-id="949aa-1567">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1567">**Description**</span></span>

<span data-ttu-id="949aa-1568">To zdarzenie reprezentuje zdarzenie zapisu klasy USBX przechwytywania ACM.</span><span class="sxs-lookup"><span data-stu-id="949aa-1568">This event represents a USBX Host Class Cdc Acm Write Event.</span></span>

<span data-ttu-id="949aa-1569">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1569">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1570">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1570">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1571">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1571">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1572">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-1572">Info Field 3: Requested Length.</span></span>
- <span data-ttu-id="949aa-1573">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1573">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-activate"></a><span data-ttu-id="949aa-1574">Dpump Aktywuj klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1574">Host Class Dpump Activate</span></span> 

#### <a name="ux_host_class_dpump_activate"></a><span data-ttu-id="949aa-1575">ux_host_class_dpump_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1575">ux_host_class_dpump_activate</span></span>

<span data-ttu-id="949aa-1576">**Ikona** ![ Ikona Dpump aktywowania klasy hosta](./media/user-guide/usbx-events/image104.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1576">**Icon** ![Host Class Dpump Activate icon](./media/user-guide/usbx-events/image104.png)</span></span>

<span data-ttu-id="949aa-1577">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1577">**Description**</span></span>

<span data-ttu-id="949aa-1578">To zdarzenie reprezentuje zdarzenie Activate USBX klasy hosta Dpump.</span><span class="sxs-lookup"><span data-stu-id="949aa-1578">This event represents a USBX Host Class Dpump Activate Event.</span></span>

<span data-ttu-id="949aa-1579">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1579">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1580">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1580">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1581">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1581">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1582">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1582">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1583">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1583">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-deactivate"></a><span data-ttu-id="949aa-1584">Dpump Dezaktywuj klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1584">Host Class Dpump Deactivate</span></span> 

#### <a name="ux_host_class_dpump_deactivate"></a><span data-ttu-id="949aa-1585">ux_host_class_dpump_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1585">ux_host_class_dpump_deactivate</span></span>

<span data-ttu-id="949aa-1586">**Ikona** ![ Ikona dezaktywowania klasy hosta Dpump](./media/user-guide/usbx-events/image105.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1586">**Icon** ![Host Class Dpump Deactivate icon](./media/user-guide/usbx-events/image105.png)</span></span>

<span data-ttu-id="949aa-1587">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1587">**Description**</span></span>

<span data-ttu-id="949aa-1588">To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX Dpump.</span><span class="sxs-lookup"><span data-stu-id="949aa-1588">This event represents a USBX Host Class Dpump Deactivate Event.</span></span>

<span data-ttu-id="949aa-1589">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1589">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1590">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1590">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1591">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1591">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1592">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1592">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1593">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1593">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-read"></a><span data-ttu-id="949aa-1594">Odczytaj Dpump klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1594">Host Class Dpump Read</span></span> 

#### <a name="ux_host_class_dpump_read"></a><span data-ttu-id="949aa-1595">ux_host_class_dpump_read</span><span class="sxs-lookup"><span data-stu-id="949aa-1595">ux_host_class_dpump_read</span></span>

<span data-ttu-id="949aa-1596">**Ikona** ![ Ikona odczytu Dpump klasy hosta](./media/user-guide/usbx-events/image106.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1596">**Icon** ![Host Class Dpump Read icon](./media/user-guide/usbx-events/image106.png)</span></span>

<span data-ttu-id="949aa-1597">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1597">**Description**</span></span>

<span data-ttu-id="949aa-1598">To zdarzenie reprezentuje zdarzenie odczytu USBX klasy hosta Dpump.</span><span class="sxs-lookup"><span data-stu-id="949aa-1598">This event represents a USBX Host Class Dpump Read Event.</span></span>

<span data-ttu-id="949aa-1599">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1599">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1600">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1600">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1601">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1601">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1602">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-1602">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-1603">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1603">Info Field 4: Not used.</span></span>

### <a name="host-class-dpump-write"></a><span data-ttu-id="949aa-1604">Dpump zapisu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1604">Host Class Dpump Write</span></span> 

#### <a name="ux_host_class_dpump_write"></a><span data-ttu-id="949aa-1605">ux_host_class_dpump_write</span><span class="sxs-lookup"><span data-stu-id="949aa-1605">ux_host_class_dpump_write</span></span>

<span data-ttu-id="949aa-1606">**Ikona** ![ Ikona zapisu Dpump klasy hosta](./media/user-guide/usbx-events/image107.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1606">**Icon** ![Host Class Dpump Write icon](./media/user-guide/usbx-events/image107.png)</span></span>

<span data-ttu-id="949aa-1607">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1607">**Description**</span></span>

<span data-ttu-id="949aa-1608">To zdarzenie reprezentuje zdarzenie zapisu USBX klasy hosta Dpump.</span><span class="sxs-lookup"><span data-stu-id="949aa-1608">This event represents a USBX Host Class Dpump Write Event.</span></span>

<span data-ttu-id="949aa-1609">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1609">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1610">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1610">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1611">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1611">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1612">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-1612">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-1613">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1613">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-activate"></a><span data-ttu-id="949aa-1614">Aktywacja klasy hosta HID</span><span class="sxs-lookup"><span data-stu-id="949aa-1614">Host Class Hid Activate</span></span> 

#### <a name="ux_host_class_hid_activate"></a><span data-ttu-id="949aa-1615">ux_host_class_hid_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1615">ux_host_class_hid_activate</span></span>

<span data-ttu-id="949aa-1616">**Ikona** ![ Ikona aktywacji klasy hosta HID](./media/user-guide/usbx-events/image108.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1616">**Icon** ![Host Class Hid Activate icon](./media/user-guide/usbx-events/image108.png)</span></span>

<span data-ttu-id="949aa-1617">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1617">**Description**</span></span>

<span data-ttu-id="949aa-1618">To zdarzenie reprezentuje zdarzenie aktywowania klasy hosta HID USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1618">This event represents a USBX Host Class Hid Activate Event.</span></span>

<span data-ttu-id="949aa-1619">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1619">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1620">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1620">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1621">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1621">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1622">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1622">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1623">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1623">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-client-register"></a><span data-ttu-id="949aa-1624">Rejestr klienta HID klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1624">Host Class Hid Client Register</span></span> 

#### <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="949aa-1625">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="949aa-1625">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="949aa-1626">**Ikona** ![ Ikona rejestracji klienta HID klasy hosta](./media/user-guide/usbx-events/image109.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1626">**Icon** ![Host Class Hid Client Register icon](./media/user-guide/usbx-events/image109.png)</span></span>

<span data-ttu-id="949aa-1627">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1627">**Description**</span></span>

<span data-ttu-id="949aa-1628">To zdarzenie reprezentuje zdarzenie rejestracji klienta klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1628">This event represents a USBX Host Class Hid Client Register Event.</span></span>

<span data-ttu-id="949aa-1629">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1629">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1630">Pole informacji 1: Nazwa klienta HID.</span><span class="sxs-lookup"><span data-stu-id="949aa-1630">Info Field 1: Hid client name.</span></span>
- <span data-ttu-id="949aa-1631">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1631">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1632">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1632">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1633">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1633">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-deactivate"></a><span data-ttu-id="949aa-1634">Dezaktywowanie klasy hosta HID</span><span class="sxs-lookup"><span data-stu-id="949aa-1634">Host Class Hid Deactivate</span></span> 

#### <a name="ux_host_class_hid_deactivate"></a><span data-ttu-id="949aa-1635">ux_host_class_hid_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1635">ux_host_class_hid_deactivate</span></span>

<span data-ttu-id="949aa-1636">**Ikona** ![ Ikona dezaktywacji klasy hosta HID](./media/user-guide/usbx-events/image110.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1636">**Icon** ![Host Class Hid Deactivate icon](./media/user-guide/usbx-events/image110.png)</span></span>

<span data-ttu-id="949aa-1637">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1637">**Description**</span></span>

<span data-ttu-id="949aa-1638">To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1638">This event represents a USBX Host Class Hid Deactivate Event.</span></span>

<span data-ttu-id="949aa-1639">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1639">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1640">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1640">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1641">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1641">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1642">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1642">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1643">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1643">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-get"></a><span data-ttu-id="949aa-1644">Pobieranie z trybu bezczynności HID klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1644">Host Class Hid Idle Get</span></span> 

#### <a name="ux_host_class_hid_idle_get"></a><span data-ttu-id="949aa-1645">ux_host_class_hid_idle_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1645">ux_host_class_hid_idle_get</span></span>

<span data-ttu-id="949aa-1646">**Ikona** ![ Ikona uzyskiwania bezczynności HID klasy hosta](./media/user-guide/usbx-events/image111.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1646">**Icon** ![Host Class Hid Idle Get icon](./media/user-guide/usbx-events/image111.png)</span></span>

<span data-ttu-id="949aa-1647">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1647">**Description**</span></span>

<span data-ttu-id="949aa-1648">To zdarzenie reprezentuje zdarzenie pobrania bezczynnej klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1648">This event represents a USBX Host Class Hid Idle Get Event.</span></span>

<span data-ttu-id="949aa-1649">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1649">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1650">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1650">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1651">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1651">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1652">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1652">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1653">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1653">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-idle-set"></a><span data-ttu-id="949aa-1654">Zestaw bezczynny HID klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1654">Host Class Hid Idle Set</span></span> 

#### <a name="ux_host_class_hid_idle_set"></a><span data-ttu-id="949aa-1655">ux_host_class_hid_idle_set</span><span class="sxs-lookup"><span data-stu-id="949aa-1655">ux_host_class_hid_idle_set</span></span>

<span data-ttu-id="949aa-1656">**Ikona** ![ Ikona zestawu bezczynności HID klasy hosta](./media/user-guide/usbx-events/image112.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1656">**Icon** ![Host Class Hid Idle Set icon](./media/user-guide/usbx-events/image112.png)</span></span>

<span data-ttu-id="949aa-1657">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1657">**Description**</span></span>

<span data-ttu-id="949aa-1658">To zdarzenie reprezentuje zdarzenie bezczynnego ustawiania klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1658">This event represents a USBX Host Class Hid Idle Set Event.</span></span>

<span data-ttu-id="949aa-1659">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1659">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1660">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1660">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1661">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1661">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1662">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1662">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1663">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1663">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-activate"></a><span data-ttu-id="949aa-1664">Aktywuj klasy hosta klawiatury HID</span><span class="sxs-lookup"><span data-stu-id="949aa-1664">Host Class Hid Keyboard Activate</span></span> 

#### <a name="ux_host_class_hid_keyboard_activate"></a><span data-ttu-id="949aa-1665">ux_host_class_hid_keyboard_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1665">ux_host_class_hid_keyboard_activate</span></span>

<span data-ttu-id="949aa-1666">**Ikona** ![ Ikona aktywacji klasy hosta HID](./media/user-guide/usbx-events/image113.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1666">**Icon** ![Host Class Hid Keyboard Activate icon](./media/user-guide/usbx-events/image113.png)</span></span>

<span data-ttu-id="949aa-1667">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1667">**Description**</span></span>

<span data-ttu-id="949aa-1668">To zdarzenie reprezentuje zdarzenie aktywowania klawiatury HID USBX klasy hosta.</span><span class="sxs-lookup"><span data-stu-id="949aa-1668">This event represents a USBX Host Class Hid Keyboard Activate Event.</span></span>

<span data-ttu-id="949aa-1669">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1669">**Information Fields**</span></span>
<p><span data-ttu-id="949aa-1670">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1670">Info Field 1: Class instance.</span></span>
<p><span data-ttu-id="949aa-1671">Pole informacji 2: wystąpienie klienta HID.</span><span class="sxs-lookup"><span data-stu-id="949aa-1671">Info Field 2: Hid client instance.</span></span>
<p><span data-ttu-id="949aa-1672">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1672">Info Field 3: Not used.</span></span>
<p><span data-ttu-id="949aa-1673">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1673">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-keyboard-deactivate"></a><span data-ttu-id="949aa-1674">Dezaktywacja klasy hosta klawiatury HID</span><span class="sxs-lookup"><span data-stu-id="949aa-1674">Host Class Hid Keyboard Deactivate</span></span> 

#### <a name="ux_host_class_hid_keyboard_deactivate"></a><span data-ttu-id="949aa-1675">ux_host_class_hid_keyboard_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1675">ux_host_class_hid_keyboard_deactivate</span></span>

<span data-ttu-id="949aa-1676">**Ikona** ![ Ikona dezaktywacji klawiatury HID klasy hosta](./media/user-guide/usbx-events/image114.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1676">**Icon** ![Host Class Hid Keyboard Deactivate icon](./media/user-guide/usbx-events/image114.png)</span></span>

<span data-ttu-id="949aa-1677">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1677">**Description**</span></span>

<span data-ttu-id="949aa-1678">To zdarzenie reprezentuje zdarzenie dezaktywacji klawiatury HID USBX klasy hosta.</span><span class="sxs-lookup"><span data-stu-id="949aa-1678">This event represents a USBX Host Class Hid Keyboard Deactivate Event.</span></span>

<span data-ttu-id="949aa-1679">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1679">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1680">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1680">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1681">Pole informacji 2: wystąpienie klienta HID.</span><span class="sxs-lookup"><span data-stu-id="949aa-1681">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="949aa-1682">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1682">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1683">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1683">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-activate"></a><span data-ttu-id="949aa-1684">Aktywacja myszy klasy hosta HID</span><span class="sxs-lookup"><span data-stu-id="949aa-1684">Host Class Hid Mouse Activate</span></span> 

#### <a name="ux_host_class_hid_mouse_activate"></a><span data-ttu-id="949aa-1685">ux_host_class_hid_mouse_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1685">ux_host_class_hid_mouse_activate</span></span>

<span data-ttu-id="949aa-1686">**Ikona** ![ Ikona aktywacji kursora myszy klasy hosta HID](./media/user-guide/usbx-events/image115.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1686">**Icon** ![Host Class Hid Mouse Activate icon](./media/user-guide/usbx-events/image115.png)</span></span>

<span data-ttu-id="949aa-1687">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1687">**Description**</span></span>

<span data-ttu-id="949aa-1688">To zdarzenie reprezentuje zdarzenie aktywowania myszy USBX klasy hosta HID.</span><span class="sxs-lookup"><span data-stu-id="949aa-1688">This event represents a USBX Host Class Hid Mouse Activate Event.</span></span>

<span data-ttu-id="949aa-1689">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1689">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1690">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1690">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1691">Pole informacji 2: wystąpienie klienta HID.</span><span class="sxs-lookup"><span data-stu-id="949aa-1691">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="949aa-1692">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1692">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1693">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1693">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-mouse-deactivate"></a><span data-ttu-id="949aa-1694">Dezaktywacja myszy klasy hosta HID</span><span class="sxs-lookup"><span data-stu-id="949aa-1694">Host Class Hid Mouse Deactivate</span></span> 

#### <a name="ux_host_class_hid_mouse_deactivate"></a><span data-ttu-id="949aa-1695">ux_host_class_hid_mouse_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1695">ux_host_class_hid_mouse_deactivate</span></span>

<span data-ttu-id="949aa-1696">**Ikona** ![ Ikona dezaktywacji myszy klasy hosta HID](./media/user-guide/usbx-events/image116.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1696">**Icon** ![Host Class Hid Mouse Deactivate icon](./media/user-guide/usbx-events/image116.png)</span></span>

<span data-ttu-id="949aa-1697">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1697">**Description**</span></span>

- <span data-ttu-id="949aa-1698">To zdarzenie reprezentuje zdarzenie dezaktywacji myszy klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1698">This event represents a USBX Host Class Hid Mouse Deactivate Event.</span></span>

<span data-ttu-id="949aa-1699">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1699">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1700">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1700">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1701">Pole informacji 2: wystąpienie klienta HID.</span><span class="sxs-lookup"><span data-stu-id="949aa-1701">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="949aa-1702">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1702">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1703">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1703">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-activate"></a><span data-ttu-id="949aa-1704">Aktywacja zdalnego sterowania HID klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1704">Host Class Hid Remote Control Activate</span></span> 

#### <a name="ux_host_class_hid_remote_control_activate"></a><span data-ttu-id="949aa-1705">ux_host_class_hid_remote_control_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1705">ux_host_class_hid_remote_control_activate</span></span>

<span data-ttu-id="949aa-1706">**Ikona** ![ Ikona aktywacji zdalnej kontroli HID klasy hosta](./media/user-guide/usbx-events/image117.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1706">**Icon** ![Host Class Hid Remote Control Activate icon](./media/user-guide/usbx-events/image117.png)</span></span>

<span data-ttu-id="949aa-1707">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1707">**Description**</span></span>

<span data-ttu-id="949aa-1708">To zdarzenie reprezentuje zdarzenie aktywowania zdalnego sterowania HID klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1708">This event represents a USBX Host Class Hid Remote Control Activate Event.</span></span>

<span data-ttu-id="949aa-1709">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1709">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1710">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1710">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1711">Pole informacji 2: wystąpienie klienta HID.</span><span class="sxs-lookup"><span data-stu-id="949aa-1711">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="949aa-1712">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1712">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1713">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1713">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-remote-control-deactivate"></a><span data-ttu-id="949aa-1714">Dezaktywacja zdalnego sterowania HID klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1714">Host Class Hid Remote Control Deactivate</span></span> 

#### <a name="ux_host_class_hid_remote_control_deactivate"></a><span data-ttu-id="949aa-1715">ux_host_class_hid_remote_control_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1715">ux_host_class_hid_remote_control_deactivate</span></span>

<span data-ttu-id="949aa-1716">**Ikona** ![ Ikona dezaktywowania zdalnego sterowania kontrolką klasy hosta](./media/user-guide/usbx-events/image118.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1716">**Icon** ![Host Class Hid Remote Control Deactivate icon](./media/user-guide/usbx-events/image118.png)</span></span>

<span data-ttu-id="949aa-1717">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1717">**Description**</span></span>

<span data-ttu-id="949aa-1718">To zdarzenie reprezentuje zdarzenie dezaktywacji zdalnego sterowania HID klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1718">This event represents a USBX Host Class Hid Remote Control Deactivate Event.</span></span>

<span data-ttu-id="949aa-1719">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1719">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1720">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1720">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1721">Pole informacji 2: wystąpienie klienta HID.</span><span class="sxs-lookup"><span data-stu-id="949aa-1721">Info Field 2: Hid client instance.</span></span>
- <span data-ttu-id="949aa-1722">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1722">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1723">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1723">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-get"></a><span data-ttu-id="949aa-1724">Pobieranie raportu HID klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1724">Host Class Hid Report Get</span></span> 

#### <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="949aa-1725">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1725">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="949aa-1726">**Ikona** ![ Ikona pobierania raportu HID klasy hosta](./media/user-guide/usbx-events/image119.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1726">**Icon** ![Host Class Hid Report Get icon](./media/user-guide/usbx-events/image119.png)</span></span>

<span data-ttu-id="949aa-1727">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1727">**Description**</span></span>

<span data-ttu-id="949aa-1728">To zdarzenie reprezentuje raport USBX klasy hosta HID get.</span><span class="sxs-lookup"><span data-stu-id="949aa-1728">This event represents a USBX Host Class Hid Report Get.</span></span>

<span data-ttu-id="949aa-1729">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1729">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1730">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1730">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1731">Pole informacji 2: Raport klienta.</span><span class="sxs-lookup"><span data-stu-id="949aa-1731">Info Field 2: Client report.</span></span>
- <span data-ttu-id="949aa-1732">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1732">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1733">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1733">Info Field 4: Not used.</span></span>

### <a name="host-class-hid-report-set"></a><span data-ttu-id="949aa-1734">Zestaw raportów HID klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1734">Host Class Hid Report Set</span></span> 

#### <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="949aa-1735">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="949aa-1735">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="949aa-1736">**Ikona** ![ Ikona zestawu raportów HID klasy hosta](./media/user-guide/usbx-events/image120.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1736">**Icon** ![Host Class Hid Report Set icon](./media/user-guide/usbx-events/image120.png)</span></span>

<span data-ttu-id="949aa-1737">**Opis** To zdarzenie reprezentuje zestaw raportów HID klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1737">**Description** This event represents a USBX Host Class Hid Report Set.</span></span>

<span data-ttu-id="949aa-1738">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1738">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1739">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1739">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1740">Pole informacji 2: Raport klienta.</span><span class="sxs-lookup"><span data-stu-id="949aa-1740">Info Field 2: Client report.</span></span>
- <span data-ttu-id="949aa-1741">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1741">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1742">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1742">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-activate"></a><span data-ttu-id="949aa-1743">Aktywuj koncentrator klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1743">Host Class Hub Activate</span></span> 

#### <a name="ux_host_class_hub_activate"></a><span data-ttu-id="949aa-1744">ux_host_class_hub_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1744">ux_host_class_hub_activate</span></span>

<span data-ttu-id="949aa-1745">**Ikona** ![ Ikona aktywowania centrum klasy hosta](./media/user-guide/usbx-events/image121.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1745">**Icon** ![Host Class Hub Activate icon](./media/user-guide/usbx-events/image121.png)</span></span>

<span data-ttu-id="949aa-1746">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1746">**Description**</span></span>

<span data-ttu-id="949aa-1747">To zdarzenie reprezentuje zdarzenie aktywowania centrum klas hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1747">This event represents a USBX Host Class Hub Activate Event.</span></span>

<span data-ttu-id="949aa-1748">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1748">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-1749">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1749">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1750">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1750">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1751">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1751">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1752">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1752">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-change-detect"></a><span data-ttu-id="949aa-1753">Wykrywanie zmian centrum klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1753">Host Class Hub Change Detect</span></span> 

#### <a name="ux_host_class_hub_change_detect"></a><span data-ttu-id="949aa-1754">ux_host_class_hub_change_detect</span><span class="sxs-lookup"><span data-stu-id="949aa-1754">ux_host_class_hub_change_detect</span></span>

<span data-ttu-id="949aa-1755">**Ikona** ![ Ikona wykrywania zmian centrum klasy hosta](./media/user-guide/usbx-events/image122.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1755">**Icon** ![Host Class Hub Change Detect icon](./media/user-guide/usbx-events/image122.png)</span></span>

<span data-ttu-id="949aa-1756">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1756">**Description**</span></span>

<span data-ttu-id="949aa-1757">To zdarzenie reprezentuje zdarzenie wykrywania zmiany centrum klas hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1757">This event represents a USBX Host Class Hub Change Detect Event.</span></span>

<span data-ttu-id="949aa-1758">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1758">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1759">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1759">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1760">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1760">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1761">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1761">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1762">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1762">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-deactivate"></a><span data-ttu-id="949aa-1763">Dezaktywacja centrum klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1763">Host Class Hub Deactivate</span></span> 

#### <a name="ux_host_class_hub_deactivate"></a><span data-ttu-id="949aa-1764">ux_host_class_hub_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1764">ux_host_class_hub_deactivate</span></span>

<span data-ttu-id="949aa-1765">**Ikona** ![ Ikona dezaktywacji centrum klasy hosta](./media/user-guide/usbx-events/image123.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1765">**Icon** ![Host Class Hub Deactivate icon](./media/user-guide/usbx-events/image123.png)</span></span>

<span data-ttu-id="949aa-1766">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1766">**Description**</span></span>

<span data-ttu-id="949aa-1767">To zdarzenie reprezentuje zdarzenie dezaktywacji centrum klas hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1767">This event represents a USBX Host Class Hub Deactivate Event.</span></span>

<span data-ttu-id="949aa-1768">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1768">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1769">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1769">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1770">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1770">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1771">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1771">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1772">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1772">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-connection-process"></a><span data-ttu-id="949aa-1773">Proces połączenia zmiany portu centrum klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1773">Host Class Hub Port Change Connection Process</span></span> 

#### <a name="ux_host_class_hub_change_connection_process"></a><span data-ttu-id="949aa-1774">ux_host_class_hub_change_connection_process</span><span class="sxs-lookup"><span data-stu-id="949aa-1774">ux_host_class_hub_change_connection_process</span></span>

<span data-ttu-id="949aa-1775">**Ikona** ![ Ikona procesu połączenia zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image124.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1775">**Icon** ![Host Class Hub Port Change Connection Process icon](./media/user-guide/usbx-events/image124.png)</span></span>

<span data-ttu-id="949aa-1776">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1776">**Description**</span></span>

<span data-ttu-id="949aa-1777">To zdarzenie reprezentuje zdarzenie przetworzenia połączenia zmiany portu centrum klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1777">This event represents a USBX Host Class Hub Port Change Connection Process Event.</span></span>

<span data-ttu-id="949aa-1778">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1778">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1779">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1779">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1780">Pole informacji 2: port.</span><span class="sxs-lookup"><span data-stu-id="949aa-1780">Info Field 2: Port.</span></span>
- <span data-ttu-id="949aa-1781">Pole informacji 3: stan portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1781">Info Field 3: Port status.</span></span>
- <span data-ttu-id="949aa-1782">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1782">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-enable-process"></a><span data-ttu-id="949aa-1783">Proces włączania zmiany portu centrum klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1783">Host Class Hub Port Change Enable Process</span></span> 

#### <a name="ux_host_class_hub_port_change_enable_process"></a><span data-ttu-id="949aa-1784">ux_host_class_hub_port_change_enable_process</span><span class="sxs-lookup"><span data-stu-id="949aa-1784">ux_host_class_hub_port_change_enable_process</span></span>

<span data-ttu-id="949aa-1785">**Ikona** ![ Ikona włączenia procesu zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image125.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1785">**Icon** ![Host Class Hub Port Change Enable Process icon](./media/user-guide/usbx-events/image125.png)</span></span>

<span data-ttu-id="949aa-1786">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1786">**Description**</span></span>

<span data-ttu-id="949aa-1787">To zdarzenie reprezentuje zdarzenie włączenia procesu zmiany portu centrum klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1787">This event represents a USBX Host Class Hub Port Change Enable Process Event.</span></span>

<span data-ttu-id="949aa-1788">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1788">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1789">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1789">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1790">Pole informacji 2: port.</span><span class="sxs-lookup"><span data-stu-id="949aa-1790">Info Field 2: Port.</span></span>
- <span data-ttu-id="949aa-1791">Pole informacji 3: stan portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1791">Info Field 3: Port status.</span></span>
- <span data-ttu-id="949aa-1792">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1792">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-over-current-process"></a><span data-ttu-id="949aa-1793">Zmiana portu koncentratora klasy hosta na bieżący proces</span><span class="sxs-lookup"><span data-stu-id="949aa-1793">Host Class Hub Port Change Over Current Process</span></span> 

#### <a name="ux_host_class_hub_port_change_over_current_process"></a><span data-ttu-id="949aa-1794">ux_host_class_hub_port_change_over_current_process</span><span class="sxs-lookup"><span data-stu-id="949aa-1794">ux_host_class_hub_port_change_over_current_process</span></span>

<span data-ttu-id="949aa-1795">**Ikona** ![ Ikona hosta zmień port koncentratora na bieżący proces](./media/user-guide/usbx-events/image126.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1795">**Icon** ![Host Class Hub Port Change Over Current Process icon](./media/user-guide/usbx-events/image126.png)</span></span>

<span data-ttu-id="949aa-1796">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1796">**Description**</span></span>

<span data-ttu-id="949aa-1797">To zdarzenie reprezentuje przydzielenie pakietu za pośrednictwem nx_packet_allocate.</span><span class="sxs-lookup"><span data-stu-id="949aa-1797">This event represents allocating a packet via nx_packet_allocate.</span></span>

<span data-ttu-id="949aa-1798">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1798">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1799">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1799">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1800">Pole informacji 2: port.</span><span class="sxs-lookup"><span data-stu-id="949aa-1800">Info Field 2: Port.</span></span>
- <span data-ttu-id="949aa-1801">Pole informacji 3: stan portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1801">Info Field 3: Port status.</span></span>
- <span data-ttu-id="949aa-1802">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1802">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-reset-process"></a><span data-ttu-id="949aa-1803">Proces resetowania zmiany portu centrum klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1803">Host Class Hub Port Change Reset Process</span></span> 

#### <a name="ux_host_class_hub_port_change_reset_process"></a><span data-ttu-id="949aa-1804">ux_host_class_hub_port_change_reset_process</span><span class="sxs-lookup"><span data-stu-id="949aa-1804">ux_host_class_hub_port_change_reset_process</span></span>

<span data-ttu-id="949aa-1805">**Ikona** ![ Ikona procesu resetowania zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image127.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1805">**Icon** ![Host Class Hub Port Change Reset Process icon](./media/user-guide/usbx-events/image127.png)</span></span>

<span data-ttu-id="949aa-1806">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1806">**Description**</span></span>

<span data-ttu-id="949aa-1807">To zdarzenie reprezentuje zdarzenie procesu resetowania portu centrum klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1807">This event represents a USBX Host Class Hub Port Change Reset Process Event.</span></span>

<span data-ttu-id="949aa-1808">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1808">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1809">Pole informacji 1: centrum.</span><span class="sxs-lookup"><span data-stu-id="949aa-1809">Info Field 1: Hub.</span></span> <span data-ttu-id="949aa-1810">Pole informacji 2: port.</span><span class="sxs-lookup"><span data-stu-id="949aa-1810">Info Field 2: Port.</span></span>
- <span data-ttu-id="949aa-1811">Pole informacji 3: stan portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1811">Info Field 3: Port status.</span></span>
- <span data-ttu-id="949aa-1812">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1812">Info Field 4: Not used.</span></span>

### <a name="host-class-hub-port-change-suspend-process"></a><span data-ttu-id="949aa-1813">Proces wstrzymania zmiany portu centrum klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1813">Host Class Hub Port Change Suspend Process</span></span> 

#### <a name="ux_host_class_hub_port_change_suspend_process"></a><span data-ttu-id="949aa-1814">ux_host_class_hub_port_change_suspend_process</span><span class="sxs-lookup"><span data-stu-id="949aa-1814">ux_host_class_hub_port_change_suspend_process</span></span>

<span data-ttu-id="949aa-1815">**Ikona** ![ Ikona procesu wstrzymania zmiany portu centrum klasy hosta](./media/user-guide/usbx-events/image128.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1815">**Icon** ![Host Class Hub Port Change Suspend Process icon](./media/user-guide/usbx-events/image128.png)</span></span>

<span data-ttu-id="949aa-1816">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1816">**Description**</span></span>

<span data-ttu-id="949aa-1817">To zdarzenie reprezentuje zdarzenie wstrzymania zmiany portu centrum klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-1817">This event represents a USBX Host Class Hub Port Change Suspend Process Event.</span></span>

<span data-ttu-id="949aa-1818">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1818">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1819">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1819">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1820">Pole informacji 2: port.</span><span class="sxs-lookup"><span data-stu-id="949aa-1820">Info Field 2: Port.</span></span>
- <span data-ttu-id="949aa-1821">Pole informacji 3: stan portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1821">Info Field 3: Port status.</span></span>
- <span data-ttu-id="949aa-1822">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1822">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-activate"></a><span data-ttu-id="949aa-1823">Pima Aktywuj klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1823">Host Class Pima Activate</span></span> 

#### <a name="ux_host_class_pima_activate"></a><span data-ttu-id="949aa-1824">ux_host_class_pima_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-1824">ux_host_class_pima_activate</span></span>

<span data-ttu-id="949aa-1825">**Ikona** ![ Ikona Pima aktywowania klasy hosta](./media/user-guide/usbx-events/image129.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1825">**Icon** ![Host Class Pima Activate icon](./media/user-guide/usbx-events/image129.png)</span></span>

<span data-ttu-id="949aa-1826">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1826">**Description**</span></span>

<span data-ttu-id="949aa-1827">To zdarzenie reprezentuje zdarzenie Activate USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1827">This event represents a USBX Host Class Pima Activate Event.</span></span>

<span data-ttu-id="949aa-1828">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1828">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1829">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1829">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1830">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1830">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1831">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1831">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1832">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1832">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-deactivate"></a><span data-ttu-id="949aa-1833">Pima Dezaktywuj klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1833">Host Class Pima Deactivate</span></span> 

#### <a name="ux_host_class_pima_deactivate"></a><span data-ttu-id="949aa-1834">ux_host_class_pima_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-1834">ux_host_class_pima_deactivate</span></span>

<span data-ttu-id="949aa-1835">**Ikona** ![ Ikona dezaktywowania klasy hosta Pima](./media/user-guide/usbx-events/image130.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1835">**Icon** ![Host Class Pima Deactivate icon](./media/user-guide/usbx-events/image130.png)</span></span>

<span data-ttu-id="949aa-1836">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1836">**Description**</span></span>

<span data-ttu-id="949aa-1837">To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1837">This event represents a USBX Host Class Pima Deactivate Event.</span></span>

<span data-ttu-id="949aa-1838">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1838">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1839">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1839">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1840">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1840">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1841">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1841">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1842">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1842">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-info-get"></a><span data-ttu-id="949aa-1843">Pobieranie informacji o urządzeniu klasy hosta Pima</span><span class="sxs-lookup"><span data-stu-id="949aa-1843">Host Class Pima Device Info Get</span></span> 

#### <a name="ux_host_class_pima_device_info_get"></a><span data-ttu-id="949aa-1844">ux_host_class_pima_device_info_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1844">ux_host_class_pima_device_info_get</span></span>

<span data-ttu-id="949aa-1845">**Ikona** ![ Ikona uzyskiwania informacji o urządzeniu klasy hosta Pima](./media/user-guide/usbx-events/image131.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1845">**Icon** ![Host Class Pima Device Info Get icon](./media/user-guide/usbx-events/image131.png)</span></span>

<span data-ttu-id="949aa-1846">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1846">**Description**</span></span>

<span data-ttu-id="949aa-1847">To zdarzenie reprezentuje zdarzenie Get USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1847">This event represents a USBX Host Class Pima Device Info Get Event.</span></span>

<span data-ttu-id="949aa-1848">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1848">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1849">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1849">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1850">Pole informacji 2: urządzenie Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1850">Info Field 2: Pima device.</span></span>
- <span data-ttu-id="949aa-1851">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1851">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1852">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1852">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-device-reset"></a><span data-ttu-id="949aa-1853">Resetowanie urządzenia Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1853">Host Class Pima Device Reset</span></span> 

#### <a name="ux_host_class_pima_device_reset"></a><span data-ttu-id="949aa-1854">ux_host_class_pima_device_reset</span><span class="sxs-lookup"><span data-stu-id="949aa-1854">ux_host_class_pima_device_reset</span></span>

<span data-ttu-id="949aa-1855">**Ikona** ![ Ikona resetowania urządzenia Pima klasy hosta](./media/user-guide/usbx-events/image132.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1855">**Icon** ![Host Class Pima Device Reset icon](./media/user-guide/usbx-events/image132.png)</span></span>

<span data-ttu-id="949aa-1856">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1856">**Description**</span></span>

<span data-ttu-id="949aa-1857">To zdarzenie reprezentuje USBX klasy hosta Pima zdarzenie resetowania urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-1857">This event represents a USBX Host Class Pima Device Reset Event.</span></span>

<span data-ttu-id="949aa-1858">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1858">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1859">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1859">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1860">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1860">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1861">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1861">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1862">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1862">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-notification"></a><span data-ttu-id="949aa-1863">Powiadomienie Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1863">Host Class Pima Notification</span></span> 

#### <a name="ux_host_class_pima_notification"></a><span data-ttu-id="949aa-1864">ux_host_class_pima_notification</span><span class="sxs-lookup"><span data-stu-id="949aa-1864">ux_host_class_pima_notification</span></span>

<span data-ttu-id="949aa-1865">**Ikona** ![ Ikona powiadomienia Pima klasy hosta](./media/user-guide/usbx-events/image133.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1865">**Icon** ![Host Class Pima Notification icon](./media/user-guide/usbx-events/image133.png)</span></span>

<span data-ttu-id="949aa-1866">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1866">**Description**</span></span>

<span data-ttu-id="949aa-1867">To zdarzenie reprezentuje zdarzenie powiadomienia USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1867">This event represents a USBX Host Class Pima Notification Event.</span></span>

<span data-ttu-id="949aa-1868">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1868">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1869">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1869">Info Field 1: Class instance.</span></span> <span data-ttu-id="949aa-1870">Pole informacji 2: kod zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-1870">Info Field 2: Event code.</span></span>
- <span data-ttu-id="949aa-1871">Pole informacji 3: Identyfikator transakcji.</span><span class="sxs-lookup"><span data-stu-id="949aa-1871">Info Field 3: Transaction ID.</span></span>
- <span data-ttu-id="949aa-1872">Pole informacji 4: parametr1.</span><span class="sxs-lookup"><span data-stu-id="949aa-1872">Info Field 4: Parameter1.</span></span>

### <a name="host-class-pima-number-objects-get"></a><span data-ttu-id="949aa-1873">Pobieranie obiektów typu Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1873">Host Class Pima Number Objects Get</span></span> 

#### <a name="ux_host_class_pima_number_objects_get"></a><span data-ttu-id="949aa-1874">ux_host_class_pima_number_objects_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1874">ux_host_class_pima_number_objects_get</span></span>

<span data-ttu-id="949aa-1875">**Ikona** ![ Ikona pobierania obiektów Pima klasy hosta](./media/user-guide/usbx-events/image134.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1875">**Icon** ![Host Class Pima Number Objects Get icon](./media/user-guide/usbx-events/image134.png)</span></span>

<span data-ttu-id="949aa-1876">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1876">**Description**</span></span>

<span data-ttu-id="949aa-1877">To zdarzenie reprezentuje klasę USBX hosta Pima obiektów Number zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-1877">This event represents a USBX Host Class Pima Number Objects Get Event.</span></span>

<span data-ttu-id="949aa-1878">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1878">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1879">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1879">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1880">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1880">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1881">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1881">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1882">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1882">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-close"></a><span data-ttu-id="949aa-1883">Zamknięto obiekt Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1883">Host Class Pima Object Close</span></span> 

#### <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="949aa-1884">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="949aa-1884">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="949aa-1885">**Ikona** ![ Ikona zamykania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image135.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1885">**Icon** ![Host Class Pima Object Close icon](./media/user-guide/usbx-events/image135.png)</span></span>

<span data-ttu-id="949aa-1886">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1886">**Description**</span></span>

<span data-ttu-id="949aa-1887">To zdarzenie reprezentuje zdarzenie zamknięcia obiektu USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1887">This event represents a USBX Host Class Pima Object Close Event.</span></span>

<span data-ttu-id="949aa-1888">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1888">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1889">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1889">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1890">Pole informacji 2: obiekt.</span><span class="sxs-lookup"><span data-stu-id="949aa-1890">Info Field 2: Object.</span></span>
- <span data-ttu-id="949aa-1891">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1891">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1892">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1892">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-copy"></a><span data-ttu-id="949aa-1893">Kopia obiektu Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1893">Host Class Pima Object Copy</span></span> 

#### <a name="ux_host_class_pima_object_copy"></a><span data-ttu-id="949aa-1894">ux_host_class_pima_object_copy</span><span class="sxs-lookup"><span data-stu-id="949aa-1894">ux_host_class_pima_object_copy</span></span>

<span data-ttu-id="949aa-1895">**Ikona** ![ Ikona kopiowania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image136.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1895">**Icon** ![Host Class Pima Object Copy icon](./media/user-guide/usbx-events/image136.png)</span></span>

<span data-ttu-id="949aa-1896">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1896">**Description**</span></span>

<span data-ttu-id="949aa-1897">To zdarzenie reprezentuje zdarzenie USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1897">This event represents a USBX Host Class Pima Object Copy Event.</span></span>

<span data-ttu-id="949aa-1898">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1898">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1899">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1899">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1900">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1900">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-1901">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1901">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1902">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1902">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-delete"></a><span data-ttu-id="949aa-1903">Usuwanie obiektu Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1903">Host Class Pima Object Delete</span></span> 

#### <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="949aa-1904">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="949aa-1904">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="949aa-1905">**Ikona** ![ Ikona usuwania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image137.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1905">**Icon** ![Host Class Pima Object Delete icon](./media/user-guide/usbx-events/image137.png)</span></span>

<span data-ttu-id="949aa-1906">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1906">**Description**</span></span>

<span data-ttu-id="949aa-1907">To zdarzenie reprezentuje zdarzenie usunięcia obiektu USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1907">This event represents a USBX Host Class Pima Object Delete Event.</span></span>

<span data-ttu-id="949aa-1908">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1908">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1909">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1909">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1910">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1910">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-1911">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1911">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1912">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1912">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-get"></a><span data-ttu-id="949aa-1913">Pobieranie obiektu Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1913">Host Class Pima Object Get</span></span> 

#### <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="949aa-1914">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1914">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="949aa-1915">**Ikona** ![ Ikona pobierania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image138.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1915">**Icon** ![Host Class Pima Object Get icon](./media/user-guide/usbx-events/image138.png)</span></span>

<span data-ttu-id="949aa-1916">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1916">**Description**</span></span>

<span data-ttu-id="949aa-1917">To zdarzenie reprezentuje informacje o pobieraniu RARP za pośrednictwem nx_rarp_info_get.</span><span class="sxs-lookup"><span data-stu-id="949aa-1917">This event represents getting RARP information via nx_rarp_info_get.</span></span>

<span data-ttu-id="949aa-1918">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1918">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1919">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1919">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1920">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1920">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-1921">Pole informacji 3: obiekt.</span><span class="sxs-lookup"><span data-stu-id="949aa-1921">Info Field 3: Object.</span></span>
- <span data-ttu-id="949aa-1922">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1922">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-get"></a><span data-ttu-id="949aa-1923">Pobieranie informacji o obiekcie Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1923">Host Class Pima Object Info Get</span></span> 

#### <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="949aa-1924">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="949aa-1924">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="949aa-1925">**Ikona** ![ Ikona uzyskiwania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image139.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1925">**Icon** ![Host Class Pima Object Info Get icon](./media/user-guide/usbx-events/image139.png)</span></span>

<span data-ttu-id="949aa-1926">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1926">**Description**</span></span>

<span data-ttu-id="949aa-1927">To zdarzenie reprezentuje zdarzenie Get USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1927">This event represents a USBX Host Class Pima Object Info Get Event.</span></span>

<span data-ttu-id="949aa-1928">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1928">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1929">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1929">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1930">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1930">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-1931">Pole informacji 3: obiekt.</span><span class="sxs-lookup"><span data-stu-id="949aa-1931">Info Field 3: Object.</span></span>
- <span data-ttu-id="949aa-1932">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1932">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-info-send"></a><span data-ttu-id="949aa-1933">Wysyłanie informacji o obiekcie Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1933">Host Class Pima Object Info Send</span></span> 

#### <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="949aa-1934">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="949aa-1934">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="949aa-1935">**Ikona** ![ Ikona wysyłania informacji o obiekcie Pima klasy hosta](./media/user-guide/usbx-events/image140.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1935">**Icon** ![Host Class Pima Object Info Send icon](./media/user-guide/usbx-events/image140.png)</span></span>

<span data-ttu-id="949aa-1936">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1936">**Description**</span></span>

<span data-ttu-id="949aa-1937">To zdarzenie reprezentuje zdarzenie wysyłania informacji o obiekcie USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1937">This event represents a USBX Host Class Pima Object Info Send Event.</span></span>

<span data-ttu-id="949aa-1938">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1938">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1939">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1939">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1940">Pole informacji 2: obiekt.</span><span class="sxs-lookup"><span data-stu-id="949aa-1940">Info Field 2: Object.</span></span>
- <span data-ttu-id="949aa-1941">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1941">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1942">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1942">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-move"></a><span data-ttu-id="949aa-1943">Przeniesienie obiektu Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1943">Host Class Pima Object Move</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="949aa-1944">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="949aa-1944">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="949aa-1945">**Ikona** ![ Ikona przenoszenia obiektu Pima klasy hosta](./media/user-guide/usbx-events/image141.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1945">**Icon** ![Host Class Pima Object Move icon](./media/user-guide/usbx-events/image141.png)</span></span>

<span data-ttu-id="949aa-1946">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1946">**Description**</span></span>

<span data-ttu-id="949aa-1947">To zdarzenie reprThis zdarzenia reprezentuje zdarzenie przenoszenia obiektu klasy hosta USBX Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1947">This event reprThis event represents a USBX Host Class Pima Object Move Event.</span></span>

<span data-ttu-id="949aa-1948">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1948">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1949">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1949">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1950">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1950">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-1951">Pole informacji 3: obiekt.</span><span class="sxs-lookup"><span data-stu-id="949aa-1951">Info Field 3: Object.</span></span>
- <span data-ttu-id="949aa-1952">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1952">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-object-send"></a><span data-ttu-id="949aa-1953">Wysyłanie obiektu Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1953">Host Class Pima Object Send</span></span> 

#### <a name="ux_host_class_pima_object_move"></a><span data-ttu-id="949aa-1954">ux_host_class_pima_object_move</span><span class="sxs-lookup"><span data-stu-id="949aa-1954">ux_host_class_pima_object_move</span></span>

<span data-ttu-id="949aa-1955">**Ikona** ![ Ikona wysyłania obiektu Pima klasy hosta](./media/user-guide/usbx-events/image142.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1955">**Icon** ![Host Class Pima Object Send icon](./media/user-guide/usbx-events/image142.png)</span></span>

<span data-ttu-id="949aa-1956">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1956">**Description**</span></span>

<span data-ttu-id="949aa-1957">To zdarzenie reprezentuje zdarzenie wysyłania obiektu USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1957">This event represents a USBX Host Class Pima Object Send Event.</span></span>

<span data-ttu-id="949aa-1958">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1958">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1959">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1959">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1960">Pole informacji 2: obiekt.</span><span class="sxs-lookup"><span data-stu-id="949aa-1960">Info Field 2: Object.</span></span>
- <span data-ttu-id="949aa-1961">Pole informacji 3: bufor obiektów.</span><span class="sxs-lookup"><span data-stu-id="949aa-1961">Info Field 3: Object buffer.</span></span>
- <span data-ttu-id="949aa-1962">Pole informacji 4: Długość obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1962">Info Field 4: Object length.</span></span>

### <a name="host-class-pima-object-transfer-abort"></a><span data-ttu-id="949aa-1963">Przerwanie transferu obiektu Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1963">Host Class Pima Object Transfer Abort</span></span> 

#### <a name="ux_host_class_pima_object_transfer_abort"></a><span data-ttu-id="949aa-1964">ux_host_class_pima_object_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="949aa-1964">ux_host_class_pima_object_transfer_abort</span></span>

<span data-ttu-id="949aa-1965">**Ikona** ![ Ikona przerwania transferu obiektu klasy hosta Pima](./media/user-guide/usbx-events/image143.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1965">**Icon** ![Host Class Pima Object Transfer Abort icon](./media/user-guide/usbx-events/image143.png)</span></span>

<span data-ttu-id="949aa-1966">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1966">**Description**</span></span>

<span data-ttu-id="949aa-1967">To zdarzenie reprezentuje zdarzenie przerwania transferu obiektu klasy USBX Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1967">This event represents a USBX Host Class Pima Object Transfer Abort Event.</span></span>

<span data-ttu-id="949aa-1968">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1968">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1969">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1969">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1970">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-1970">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-1971">Pole informacji 3: obiekt.</span><span class="sxs-lookup"><span data-stu-id="949aa-1971">Info Field 3: Object.</span></span>
- <span data-ttu-id="949aa-1972">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1972">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-read"></a><span data-ttu-id="949aa-1973">Odczytaj Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1973">Host Class Pima Read</span></span> 

#### <a name="ux_host_class_pima_read"></a><span data-ttu-id="949aa-1974">ux_host_class_pima_read</span><span class="sxs-lookup"><span data-stu-id="949aa-1974">ux_host_class_pima_read</span></span>

<span data-ttu-id="949aa-1975">**Ikona** ![ Ikona odczytu Pima klasy hosta](./media/user-guide/usbx-events/image144.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1975">**Icon** ![Host Class Pima Read icon](./media/user-guide/usbx-events/image144.png)</span></span>

<span data-ttu-id="949aa-1976">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1976">**Description**</span></span>

<span data-ttu-id="949aa-1977">To zdarzenie reprezentuje zdarzenie odczytu USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1977">This event represents a USBX Host Class Pima Read Event.</span></span>

<span data-ttu-id="949aa-1978">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1978">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1979">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1979">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1980">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1980">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-1981">Pole informacji 3: długość danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-1981">Info Field 3: Data length.</span></span>
- <span data-ttu-id="949aa-1982">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1982">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-request-cancel"></a><span data-ttu-id="949aa-1983">Żądanie anulowania klasy hosta Pima</span><span class="sxs-lookup"><span data-stu-id="949aa-1983">Host Class Pima Request Cancel</span></span> 

#### <a name="ux_host_class_pima_request_cancel"></a><span data-ttu-id="949aa-1984">ux_host_class_pima_request_cancel</span><span class="sxs-lookup"><span data-stu-id="949aa-1984">ux_host_class_pima_request_cancel</span></span>

<span data-ttu-id="949aa-1985">**Ikona** ![ Ikona anulowania żądania Pima klasy hosta](./media/user-guide/usbx-events/image145.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1985">**Icon** ![Host Class Pima Request Cancel icon](./media/user-guide/usbx-events/image145.png)</span></span>

<span data-ttu-id="949aa-1986">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1986">**Description**</span></span>

<span data-ttu-id="949aa-1987">To zdarzenie reprezentuje zdarzenie anulowania żądania USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1987">This event represents a USBX Host Class Pima Request Cancel Event.</span></span>

<span data-ttu-id="949aa-1988">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1988">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1989">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1989">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-1990">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1990">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-1991">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-1991">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-1992">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-1992">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-close"></a><span data-ttu-id="949aa-1993">Zamknięcie sesji Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-1993">Host Class Pima Session Close</span></span> 

#### <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="949aa-1994">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="949aa-1994">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="949aa-1995">**Ikona** ![ Ikona zamykania sesji Pima dla klasy hosta](./media/user-guide/usbx-events/image146.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-1995">**Icon** ![Host Class Pima Session Close icon](./media/user-guide/usbx-events/image146.png)</span></span>

<span data-ttu-id="949aa-1996">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-1996">**Description**</span></span>

<span data-ttu-id="949aa-1997">To zdarzenie reprezentuje zdarzenie zamknięcia sesji USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-1997">This event represents a USBX Host Class Pima Session Close Event.</span></span>

<span data-ttu-id="949aa-1998">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-1998">**Information Fields**</span></span>

- <span data-ttu-id="949aa-1999">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-1999">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2000">Pole informacji 2: sesja Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-2000">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="949aa-2001">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2001">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2002">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2002">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-session-open"></a><span data-ttu-id="949aa-2003">Otwarta sesja Pima sesji hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2003">Host Class Pima Session Open</span></span> 

#### <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="949aa-2004">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="949aa-2004">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="949aa-2005">**Ikona** ![ Ikona Otwórz sesję Pima sesji hosta](./media/user-guide/usbx-events/image147.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2005">**Icon** ![Host Class Pima Session Open icon](./media/user-guide/usbx-events/image147.png)</span></span>

<span data-ttu-id="949aa-2006">**Opis** To zdarzenie reprezentuje USBX klasy hosta zdarzenia Pima sesji.</span><span class="sxs-lookup"><span data-stu-id="949aa-2006">**Description** This event represents a USBX Host Class Pima Session Open Event.</span></span>

<span data-ttu-id="949aa-2007">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2007">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2008">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2008">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2009">Pole informacji 2: sesja Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-2009">Info Field 2: Pima session.</span></span>
- <span data-ttu-id="949aa-2010">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2010">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2011">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2011">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-ids-get"></a><span data-ttu-id="949aa-2012">Pobieranie identyfikatorów magazynu Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2012">Host Class Pima Storage Ids Get</span></span> 

#### <a name="ux_host_class_pima_session_ids_get"></a><span data-ttu-id="949aa-2013">ux_host_class_pima_session_ids_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2013">ux_host_class_pima_session_ids_get</span></span>

<span data-ttu-id="949aa-2014">**Ikona** ![ Ikona pobierania identyfikatorów magazynu Pima klasy hosta](./media/user-guide/usbx-events/image148.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2014">**Icon** ![Host Class Pima Storage Ids Get icon](./media/user-guide/usbx-events/image148.png)</span></span>

<span data-ttu-id="949aa-2015">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2015">**Description**</span></span>

<span data-ttu-id="949aa-2016">To zdarzenie reprezentuje USBX klasy hosta Pima zdarzenia get.</span><span class="sxs-lookup"><span data-stu-id="949aa-2016">This event represents a USBX Host Class Pima Storage Ids Get Event.</span></span>

<span data-ttu-id="949aa-2017">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2017">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2018">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2018">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2019">NFO pole 2: tablica identyfikatorów magazynu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2019">nfo Field 2: Storage ID array.</span></span>
- <span data-ttu-id="949aa-2020">Pole informacji 3: Długość identyfikatora magazynu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2020">Info Field 3: Storage ID length.</span></span>
<span data-ttu-id="949aa-2021">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2021">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-storage-info-get"></a><span data-ttu-id="949aa-2022">Pobieranie informacji o magazynie Pima klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2022">Host Class Pima Storage Info Get</span></span> 

#### <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="949aa-2023">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2023">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="949aa-2024">**Ikona** ![ Ikona pobierania informacji o magazynie Pima klasy hosta](./media/user-guide/usbx-events/image149.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2024">**Icon** ![Host Class Pima Storage Info Get icon](./media/user-guide/usbx-events/image149.png)</span></span>

<span data-ttu-id="949aa-2025">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2025">**Description**</span></span>

<span data-ttu-id="949aa-2026">To zdarzenie reprezentuje zdarzenie pobrania informacji o magazynie USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-2026">This event represents a USBX Host Class Pima Storage Info Get Event.</span></span>

<span data-ttu-id="949aa-2027">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2027">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2028">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2028">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2029">Pole informacji 2: Identyfikator magazynu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2029">Info Field 2: Storage ID.</span></span>
- <span data-ttu-id="949aa-2030">Pole informacji 3: Magazyn.</span><span class="sxs-lookup"><span data-stu-id="949aa-2030">Info Field 3: Storage.</span></span>
- <span data-ttu-id="949aa-2031">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2031">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-thumb-get"></a><span data-ttu-id="949aa-2032">Pobieranie klasy hosta Pima kciuka</span><span class="sxs-lookup"><span data-stu-id="949aa-2032">Host Class Pima Thumb Get</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="949aa-2033">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2033">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="949aa-2034">**Ikona** ![ Ikona pobierania Pima klasy hosta](./media/user-guide/usbx-events/image150.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2034">**Icon** ![Host Class Pima Thumb Get icon](./media/user-guide/usbx-events/image150.png)</span></span>

<span data-ttu-id="949aa-2035">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2035">**Description**</span></span>

<span data-ttu-id="949aa-2036">To zdarzenie reprezentuje nieakceptowanie połączenia z serwerem TCP za pośrednictwem nx_tcp_server_socket_unaccept.</span><span class="sxs-lookup"><span data-stu-id="949aa-2036">This event represents unaccepting a TCP server connection via nx_tcp_server_socket_unaccept.</span></span>

<span data-ttu-id="949aa-2037">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2037">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-2038">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2038">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2039">Pole informacji 2: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2039">Info Field 2: Object handle.</span></span>
- <span data-ttu-id="949aa-2040">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2040">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2041">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2041">Info Field 4: Not used.</span></span>

### <a name="host-class-pima-write"></a><span data-ttu-id="949aa-2042">Pima zapisu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2042">Host Class Pima Write</span></span> 

#### <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="949aa-2043">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2043">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="949aa-2044">**Ikona** ![ Ikona zapisu Pima klasy hosta](./media/user-guide/usbx-events/image151.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2044">**Icon** ![Host Class Pima Write icon](./media/user-guide/usbx-events/image151.png)</span></span>

<span data-ttu-id="949aa-2045">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2045">**Description**</span></span>

<span data-ttu-id="949aa-2046">To zdarzenie reprezentuje USBX klasy hosta Pima.</span><span class="sxs-lookup"><span data-stu-id="949aa-2046">This event represents a USBX Host Class Pima Write.</span></span>

<span data-ttu-id="949aa-2047">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2047">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2048">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2048">Info Field 1: Class Instance.</span></span>
- <span data-ttu-id="949aa-2049">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-2049">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-2050">Pole informacji 3: długość danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-2050">Info Field 3: Data length.</span></span>
- <span data-ttu-id="949aa-2051">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2051">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-activate"></a><span data-ttu-id="949aa-2052">Aktywuj drukarkę klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2052">Host Class Printer Activate</span></span> 

#### <a name="ux_host_class_printer_activate"></a><span data-ttu-id="949aa-2053">ux_host_class_printer_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-2053">ux_host_class_printer_activate</span></span>

<span data-ttu-id="949aa-2054">**Ikona** ![ Ikona aktywowania drukarki klasy hosta](./media/user-guide/usbx-events/image152.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2054">**Icon** ![Host Class Printer Activate icon](./media/user-guide/usbx-events/image152.png)</span></span>

<span data-ttu-id="949aa-2055">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2055">**Description**</span></span>

<span data-ttu-id="949aa-2056">To zdarzenie reprezentuje zdarzenie aktywowania drukarki klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2056">This event represents a USBX Host Class Printer Activate Event.</span></span>

<span data-ttu-id="949aa-2057">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2057">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2058">Pole informacji 1: wskaźnik do wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="949aa-2058">Info Field 1: Pointer to IP instance.</span></span>
- <span data-ttu-id="949aa-2059">Pole informacji 2: wskaźnik do gniazda.</span><span class="sxs-lookup"><span data-stu-id="949aa-2059">Info Field 2: Pointer to socket.</span></span>
- <span data-ttu-id="949aa-2060">Pole informacji 3: typ usługi.</span><span class="sxs-lookup"><span data-stu-id="949aa-2060">Info Field 3: Type of service.</span></span>
- <span data-ttu-id="949aa-2061">Pole informacji 4: rozmiar okna odbierania.</span><span class="sxs-lookup"><span data-stu-id="949aa-2061">Info Field 4: Receive window size.</span></span>

### <a name="host-class-printer-deactivate"></a><span data-ttu-id="949aa-2062">Dezaktywacja drukarki klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2062">Host Class Printer Deactivate</span></span> 

#### <a name="ux_host_class_printer_deactivate"></a><span data-ttu-id="949aa-2063">ux_host_class_printer_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-2063">ux_host_class_printer_deactivate</span></span>

<span data-ttu-id="949aa-2064">**Ikona** ![ Ikona dezaktywacji drukarki klasy hosta](./media/user-guide/usbx-events/image153.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2064">**Icon** ![Host Class Printer Deactivate icon](./media/user-guide/usbx-events/image153.png)</span></span>

<span data-ttu-id="949aa-2065">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2065">**Description**</span></span>

<span data-ttu-id="949aa-2066">To zdarzenie reprezentuje zdarzenie dezaktywacji drukarki klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2066">This event represents a USBX Host Class Printer Deactivate Event.</span></span>

<span data-ttu-id="949aa-2067">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2067">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2068">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2068">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2069">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2069">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2070">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2070">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2071">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2071">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-name-get"></a><span data-ttu-id="949aa-2072">Pobieranie nazwy drukarki klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2072">Host Class Printer Name Get</span></span> 

#### <a name="ux_host_class_printer_name_get"></a><span data-ttu-id="949aa-2073">ux_host_class_printer_name_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2073">ux_host_class_printer_name_get</span></span>

<span data-ttu-id="949aa-2074">**Ikona** ![ Ikona pobierania nazwy drukarki klasy hosta](./media/user-guide/usbx-events/image154.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2074">**Icon** ![Host Class Printer Name Get icon](./media/user-guide/usbx-events/image154.png)</span></span>

<span data-ttu-id="949aa-2075">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2075">**Description**</span></span>

<span data-ttu-id="949aa-2076">To zdarzenie reprezentuje zdarzenie Get nazwy drukarki klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2076">This event represents a USBX Host Class Printer Name Get Event.</span></span>

<span data-ttu-id="949aa-2077">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2077">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-2078">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2078">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2079">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2079">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2080">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2080">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2081">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2081">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-read"></a><span data-ttu-id="949aa-2082">Odczytaj drukarkę klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2082">Host Class Printer Read</span></span> 

#### <a name="ux_host_class_printer_read"></a><span data-ttu-id="949aa-2083">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="949aa-2083">ux_host_class_printer_read</span></span>

<span data-ttu-id="949aa-2084">**Ikona** ![ Ikona odczytu drukarki klasy hosta](./media/user-guide/usbx-events/image155.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2084">**Icon** ![Host Class Printer Read icon](./media/user-guide/usbx-events/image155.png)</span></span>

<span data-ttu-id="949aa-2085">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2085">**Description**</span></span>

<span data-ttu-id="949aa-2086">To zdarzenie reprezentuje zdarzenie odczytu drukarki klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2086">This event represents a USBX Host Class Printer Read Event.</span></span>

<span data-ttu-id="949aa-2087">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2087">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2088">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2088">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2089">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-2089">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-2090">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-2090">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-2091">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2091">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-soft-reset"></a><span data-ttu-id="949aa-2092">Resetowanie nietrwałe drukarki klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2092">Host Class Printer Soft Reset</span></span> 

#### <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="949aa-2093">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="949aa-2093">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="949aa-2094">**Ikona** ![ Ikona resetowania nietrwałego drukarki klasy hosta](./media/user-guide/usbx-events/image156.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2094">**Icon** ![Host Class Printer Soft Reset icon](./media/user-guide/usbx-events/image156.png)</span></span>

<span data-ttu-id="949aa-2095">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2095">**Description**</span></span>

<span data-ttu-id="949aa-2096">To zdarzenie reprezentuje zdarzenie nietrwałego resetowania drukarki klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2096">This event represents a USBX Host Class Printer Soft Reset Event.</span></span>

<span data-ttu-id="949aa-2097">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2097">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2098">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2098">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2099">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2099">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2100">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2100">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2101">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2101">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-status-get"></a><span data-ttu-id="949aa-2102">Pobieranie stanu drukarki klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2102">Host Class Printer Status Get</span></span> 

#### <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="949aa-2103">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2103">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="949aa-2104">**Ikona** ![ Ikona pobierania stanu drukarki klasy hosta](./media/user-guide/usbx-events/image157.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2104">**Icon** ![Host Class Printer Status Get icon](./media/user-guide/usbx-events/image157.png)</span></span>

<span data-ttu-id="949aa-2105">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2105">**Description**</span></span>

<span data-ttu-id="949aa-2106">To zdarzenie reprezentuje zdarzenie Get stanu drukarki klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2106">This event represents a USBX Host Class Printer Status Get Event.</span></span>

<span data-ttu-id="949aa-2107">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2107">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2108">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2108">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2109">Pole informacji 2: stan drukarki.</span><span class="sxs-lookup"><span data-stu-id="949aa-2109">Info Field 2: Printer status.</span></span>
- <span data-ttu-id="949aa-2110">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2110">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2111">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2111">Info Field 4: Not used.</span></span>

### <a name="host-class-printer-write"></a><span data-ttu-id="949aa-2112">Zapis drukarki klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2112">Host Class Printer Write</span></span> 

#### <a name="ux_host_class_printer_write"></a><span data-ttu-id="949aa-2113">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="949aa-2113">ux_host_class_printer_write</span></span>

<span data-ttu-id="949aa-2114">**Ikona** ![ Ikona zapisu drukarki klasy hosta](./media/user-guide/usbx-events/image158.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2114">**Icon** ![Host Class Printer Write icon](./media/user-guide/usbx-events/image158.png)</span></span>

<span data-ttu-id="949aa-2115">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2115">**Description**</span></span>

<span data-ttu-id="949aa-2116">To zdarzenie przedstawia zapis drukarki klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2116">This event represents a USBX Host Class Printer Write.</span></span>

<span data-ttu-id="949aa-2117">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2117">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-2118">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2118">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2119">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-2119">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-2120">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-2120">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-2121">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2121">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-activate"></a><span data-ttu-id="949aa-2122">Mnóstwo Aktywuj klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2122">Host Class Prolific Activate</span></span> 

#### <a name="ux_host_class_prolific_activate"></a><span data-ttu-id="949aa-2123">ux_host_class_prolific_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-2123">ux_host_class_prolific_activate</span></span> 

<span data-ttu-id="949aa-2124">**Ikona** ![ Ikona mnóstwo aktywowania klasy hosta](./media/user-guide/usbx-events/image159.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2124">**Icon** ![Host Class Prolific Activate icon](./media/user-guide/usbx-events/image159.png)</span></span>

<span data-ttu-id="949aa-2125">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2125">**Description**</span></span>

<span data-ttu-id="949aa-2126">To zdarzenie reprezentuje zdarzenie Activate USBX klasy hosta mnóstwo.</span><span class="sxs-lookup"><span data-stu-id="949aa-2126">This event represents a USBX Host Class Prolific Activate Event.</span></span>

<span data-ttu-id="949aa-2127">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2127">**Information Fields**</span></span> 

- <span data-ttu-id="949aa-2128">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2128">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2129">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2129">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2130">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2130">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2131">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2131">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-deactivate"></a><span data-ttu-id="949aa-2132">Mnóstwo Dezaktywuj klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2132">Host Class Prolific Deactivate</span></span> 

#### <a name="ux_host_class_prolific_deactivate"></a><span data-ttu-id="949aa-2133">ux_host_class_prolific_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-2133">ux_host_class_prolific_deactivate</span></span> 

<span data-ttu-id="949aa-2134">**Ikona** ![ Ikona dezaktywowania klasy hosta mnóstwo](./media/user-guide/usbx-events/image160.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2134">**Icon** ![Host Class Prolific Deactivate icon](./media/user-guide/usbx-events/image160.png)</span></span>

<span data-ttu-id="949aa-2135">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2135">**Description**</span></span>

<span data-ttu-id="949aa-2136">To zdarzenie reprezentuje zdarzenie dezaktywacji klasy hosta USBX mnóstwo.</span><span class="sxs-lookup"><span data-stu-id="949aa-2136">This event represents a USBX Host Class Prolific Deactivate Event.</span></span>

<span data-ttu-id="949aa-2137">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2137">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2138">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2138">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2139">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2139">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2140">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2140">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2141">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2141">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-in-pipe"></a><span data-ttu-id="949aa-2142">Przerwanie mnóstwo operacji IOCTL klasy hosta w potoku</span><span class="sxs-lookup"><span data-stu-id="949aa-2142">Host Class Prolific Ioctl Abort In Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_in_pipe"></a><span data-ttu-id="949aa-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span><span class="sxs-lookup"><span data-stu-id="949aa-2143">ux_host_class_prolific_ioctl_abort_in_pipe</span></span>

<span data-ttu-id="949aa-2144">**Ikona** ![ Ikona potoku mnóstwo I O przerwanie klasy hosta](./media/user-guide/usbx-events/image161.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2144">**Icon** ![Host Class Prolific I O C T L Abort In Pipe icon](./media/user-guide/usbx-events/image161.png)</span></span>

<span data-ttu-id="949aa-2145">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2145">**Description**</span></span>

<span data-ttu-id="949aa-2146">To zdarzenie reprezentuje klasę hosta USBX mnóstwo przerwania w zdarzeniu potoku.</span><span class="sxs-lookup"><span data-stu-id="949aa-2146">This event represents a USBX Host Class Prolific Ioctl Abort In Pipe Event.</span></span>

<span data-ttu-id="949aa-2147">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2147">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2148">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2148">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2149">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2149">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-2150">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2150">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2151">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2151">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-abort-out-pipe"></a><span data-ttu-id="949aa-2152">Przerwano potok operacji IOCTL klasy hosta mnóstwo</span><span class="sxs-lookup"><span data-stu-id="949aa-2152">Host Class Prolific Ioctl Abort Out Pipe</span></span> 

#### <a name="ux_host_class_prolific_ioctl_abort_out_pipe"></a><span data-ttu-id="949aa-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span><span class="sxs-lookup"><span data-stu-id="949aa-2153">ux_host_class_prolific_ioctl_abort_out_pipe</span></span>

<span data-ttu-id="949aa-2154">**Ikona** ![ Mnóstwo klasy hosta — ikona przerwania rozgałęzienia I O C T L](./media/user-guide/usbx-events/image162.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2154">**Icon** ![Host Class Prolific I O C T L Abort Out Pipe icon](./media/user-guide/usbx-events/image162.png)</span></span>

<span data-ttu-id="949aa-2155">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2155">**Description**</span></span>

<span data-ttu-id="949aa-2156">To zdarzenie reprezentuje klasę hosta USBX mnóstwo przerywanie zdarzenia potoku.</span><span class="sxs-lookup"><span data-stu-id="949aa-2156">This event represents a USBX Host Class Prolific Ioctl Abort Out Pipe Event.</span></span>

<span data-ttu-id="949aa-2157">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2157">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2158">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2158">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2159">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2159">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-2160">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2160">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2161">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2161">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-device-status"></a><span data-ttu-id="949aa-2162">Klasa hosta mnóstwo IOCTL pobieranie stanu urządzenia</span><span class="sxs-lookup"><span data-stu-id="949aa-2162">Host Class Prolific Ioctl Get Device Status</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_device_status"></a><span data-ttu-id="949aa-2163">ux_host_class_prolific_ioctl_get_device_status</span><span class="sxs-lookup"><span data-stu-id="949aa-2163">ux_host_class_prolific_ioctl_get_device_status</span></span>

<span data-ttu-id="949aa-2164">**Ikona** ![ Mnóstwo klasy hosta — ikona stanu urządzenia I O C T L](./media/user-guide/usbx-events/image163.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2164">**Icon** ![Host Class Prolific I O C T L Get Device Status icon](./media/user-guide/usbx-events/image163.png)</span></span>

<span data-ttu-id="949aa-2165">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2165">**Description**</span></span>

<span data-ttu-id="949aa-2166">To zdarzenie reprezentuje klasę hosta USBX mnóstwo IOCTL pobieranie zdarzenia stanu urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-2166">This event represents a USBX Host Class Prolific Ioctl Get Device Status Event.</span></span>

<span data-ttu-id="949aa-2167">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2167">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2168">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2168">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2169">Pole informacji 2: stan urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-2169">Info Field 2: Device status.</span></span>
- <span data-ttu-id="949aa-2170">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2170">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2171">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2171">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-get-line-coding"></a><span data-ttu-id="949aa-2172">Klasa hosta mnóstwo IOCTL Pobierz kodowanie wiersza</span><span class="sxs-lookup"><span data-stu-id="949aa-2172">Host Class Prolific Ioctl Get Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_get_line_coding"></a><span data-ttu-id="949aa-2173">ux_host_class_prolific_ioctl_get_line_coding</span><span class="sxs-lookup"><span data-stu-id="949aa-2173">ux_host_class_prolific_ioctl_get_line_coding</span></span>

<span data-ttu-id="949aa-2174">**Ikona** ![ Ikona "Pobierz kodowanie wiersza" klasy hosta mnóstwo I O C T L](./media/user-guide/usbx-events/image164.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2174">**Icon** ![Host Class Prolific I O C T L Get Line Coding icon](./media/user-guide/usbx-events/image164.png)</span></span>

<span data-ttu-id="949aa-2175">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2175">**Description**</span></span>

<span data-ttu-id="949aa-2176">To zdarzenie reprezentuje klasę hosta USBX mnóstwo polecenie IOCTL pobieranie wiersza zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-2176">This event represents a USBX Host Class Prolific Ioctl Get Line Coding Event.</span></span>

<span data-ttu-id="949aa-2177">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2177">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2178">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2178">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2179">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-2179">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-2180">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2180">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2181">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2181">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-purge"></a><span data-ttu-id="949aa-2182">Mnóstwo — przeczyszczanie klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2182">Host Class Prolific Ioctl Purge</span></span> 

#### <a name="ux_host_class_prolific_ioctl_purge"></a><span data-ttu-id="949aa-2183">ux_host_class_prolific_ioctl_purge</span><span class="sxs-lookup"><span data-stu-id="949aa-2183">ux_host_class_prolific_ioctl_purge</span></span>

<span data-ttu-id="949aa-2184">**Ikona** ![ Ikona przeczyszczania elementu IOCTL klasy hosta mnóstwo](./media/user-guide/usbx-events/image165.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2184">**Icon** ![Host Class Prolific Ioctl Purge icon](./media/user-guide/usbx-events/image165.png)</span></span>

<span data-ttu-id="949aa-2185">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2185">**Description**</span></span>

<span data-ttu-id="949aa-2186">To zdarzenie reprezentuje USBX klasy hosta mnóstwo zdarzenia przeczyszczania IOCTL.</span><span class="sxs-lookup"><span data-stu-id="949aa-2186">This event represents a USBX Host Class Prolific Ioctl Purge Event.</span></span>

<span data-ttu-id="949aa-2187">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2187">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2188">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2188">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2189">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-2189">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-2190">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2190">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2191">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2191">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-report-device"></a><span data-ttu-id="949aa-2192">Urządzenie raportu IOCTL klasy hosta mnóstwo</span><span class="sxs-lookup"><span data-stu-id="949aa-2192">Host Class Prolific Ioctl Report Device</span></span> 

#### <a name="ux_host_class_prolific_ioctl_report_device"></a><span data-ttu-id="949aa-2193">ux_host_class_prolific_ioctl_report_device</span><span class="sxs-lookup"><span data-stu-id="949aa-2193">ux_host_class_prolific_ioctl_report_device</span></span>

<span data-ttu-id="949aa-2194">**Ikona** ![ Ikona urządzenia z raportem klasy hosta mnóstwo I O C T L](./media/user-guide/usbx-events/image166.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2194">**Icon** ![Host Class Prolific I O C T L Report Device icon](./media/user-guide/usbx-events/image166.png)</span></span>

<span data-ttu-id="949aa-2195">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2195">**Description**</span></span>

<span data-ttu-id="949aa-2196">To zdarzenie reprezentuje zdarzenie zmiany stanu urządzenia USBX klasy hosta mnóstwo.</span><span class="sxs-lookup"><span data-stu-id="949aa-2196">This event represents a USBX Host Class Prolific Ioctl Report Device Status Change Event.</span></span>

<span data-ttu-id="949aa-2197">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2197">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2198">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2198">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2199">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-2199">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-2200">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2200">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2201">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2201">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-send-break"></a><span data-ttu-id="949aa-2202">Przerwanie wysyłania polecenia IOCTL klasy hosta mnóstwo</span><span class="sxs-lookup"><span data-stu-id="949aa-2202">Host Class Prolific Ioctl Send Break</span></span> 

#### <a name="ux_host_class_prolific_ioctl_send_break"></a><span data-ttu-id="949aa-2203">ux_host_class_prolific_ioctl_send_break</span><span class="sxs-lookup"><span data-stu-id="949aa-2203">ux_host_class_prolific_ioctl_send_break</span></span>

<span data-ttu-id="949aa-2204">**Ikona** ![ Mnóstwo klasy hosta — ikona przerwania wysyłania I O T L](./media/user-guide/usbx-events/image167.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2204">**Icon** ![Host Class Prolific I O C T L Send Break icon](./media/user-guide/usbx-events/image167.png)</span></span>

<span data-ttu-id="949aa-2205">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2205">**Description**</span></span>

<span data-ttu-id="949aa-2206">To zdarzenie reprezentuje USBXą klasę hosta mnóstwo zdarzenie przerwania.</span><span class="sxs-lookup"><span data-stu-id="949aa-2206">This event represents a USBX Host Class Prolific Ioctl Send Break Event.</span></span>

<span data-ttu-id="949aa-2207">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2207">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2208">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2208">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2209">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2209">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2210">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2210">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2211">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2211">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-coding"></a><span data-ttu-id="949aa-2212">Kodowanie liniowe zestawu poleceń IOCTL klasy hosta mnóstwo</span><span class="sxs-lookup"><span data-stu-id="949aa-2212">Host Class Prolific Ioctl Set Line Coding</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_coding"></a><span data-ttu-id="949aa-2213">ux_host_class_prolific_ioctl_set_line_coding</span><span class="sxs-lookup"><span data-stu-id="949aa-2213">ux_host_class_prolific_ioctl_set_line_coding</span></span>

<span data-ttu-id="949aa-2214">**Ikona** ![ Mnóstwo klasy hosta — ikona kodowania linii I O C T L](./media/user-guide/usbx-events/image168.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2214">**Icon** ![Host Class Prolific I O C T L Set Line Coding icon](./media/user-guide/usbx-events/image168.png)</span></span>

<span data-ttu-id="949aa-2215">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2215">**Description**</span></span>

<span data-ttu-id="949aa-2216">To zdarzenie reprezentuje USBX klasy hosta mnóstwo zdarzenie kodowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="949aa-2216">This event represents a USBX Host Class Prolific Ioctl Set Line Coding Event.</span></span>

<span data-ttu-id="949aa-2217">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2217">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2218">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2218">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2219">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-2219">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-2220">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2220">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2221">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2221">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-ioctl-set-line-state"></a><span data-ttu-id="949aa-2222">Stan wiersza ustawiania elementu IOCTL klasy hosta mnóstwo</span><span class="sxs-lookup"><span data-stu-id="949aa-2222">Host Class Prolific Ioctl Set Line State</span></span> 

#### <a name="ux_host_class_prolific_ioctl_set_line_state"></a><span data-ttu-id="949aa-2223">ux_host_class_prolific_ioctl_set_line_state</span><span class="sxs-lookup"><span data-stu-id="949aa-2223">ux_host_class_prolific_ioctl_set_line_state</span></span>

<span data-ttu-id="949aa-2224">**Ikona** ![ Mnóstwo klasy hosta — ikona stanu wiersza I O C T L](./media/user-guide/usbx-events/image169.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2224">**Icon** ![Host Class Prolific I O C T L Set Line State icon](./media/user-guide/usbx-events/image169.png)</span></span>

<span data-ttu-id="949aa-2225">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2225">**Description**</span></span>

<span data-ttu-id="949aa-2226">To zdarzenie reprezentuje USBX klasy hosta mnóstwo zdarzenie stanu wiersza.</span><span class="sxs-lookup"><span data-stu-id="949aa-2226">This event represents a USBX Host Class Prolific Ioctl Set Line State Event.</span></span>

<span data-ttu-id="949aa-2227">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2227">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2228">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2228">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2229">Pole informacji 2: parametr.</span><span class="sxs-lookup"><span data-stu-id="949aa-2229">Info Field 2: Parameter.</span></span>
- <span data-ttu-id="949aa-2230">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2230">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2231">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2231">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-read"></a><span data-ttu-id="949aa-2232">Odczytaj mnóstwo klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2232">Host Class Prolific Read</span></span> 

#### <a name="ux_host_class_prolific_read"></a><span data-ttu-id="949aa-2233">ux_host_class_prolific_read</span><span class="sxs-lookup"><span data-stu-id="949aa-2233">ux_host_class_prolific_read</span></span>

<span data-ttu-id="949aa-2234">**Ikona** ![ Ikona odczytu mnóstwo klasy hosta](./media/user-guide/usbx-events/image170.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2234">**Icon** ![Host Class Prolific Read icon](./media/user-guide/usbx-events/image170.png)</span></span>

<span data-ttu-id="949aa-2235">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2235">**Description**</span></span>

<span data-ttu-id="949aa-2236">To zdarzenie reprezentuje zdarzenie odczytu USBX klasy hosta mnóstwo.</span><span class="sxs-lookup"><span data-stu-id="949aa-2236">This event represents a USBX Host Class Prolific Read Event.</span></span>

<span data-ttu-id="949aa-2237">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2237">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2238">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2238">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2239">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-2239">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-2240">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-2240">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-2241">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2241">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-start"></a><span data-ttu-id="949aa-2242">Rozpoczęcie odbierania mnóstwo klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2242">Host Class Prolific Reception Start</span></span> 

#### <a name="ux_host_class_prolific_reception_start"></a><span data-ttu-id="949aa-2243">ux_host_class_prolific_reception_start</span><span class="sxs-lookup"><span data-stu-id="949aa-2243">ux_host_class_prolific_reception_start</span></span>

<span data-ttu-id="949aa-2244">**Ikona** ![ Ikona startowa odbioru mnóstwo klasy hosta](./media/user-guide/usbx-events/image171.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2244">**Icon** ![Host Class Prolific Reception Start icon](./media/user-guide/usbx-events/image171.png)</span></span>

<span data-ttu-id="949aa-2245">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2245">**Description**</span></span>

<span data-ttu-id="949aa-2246">To zdarzenie reprezentuje zdarzenie rozpoczęcia odbioru USBX klasy hosta mnóstwo.</span><span class="sxs-lookup"><span data-stu-id="949aa-2246">This event represents a USBX Host Class Prolific Reception Start Event.</span></span>

<span data-ttu-id="949aa-2247">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2247">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2248">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2248">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2249">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2249">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2250">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2250">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2251">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2251">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-reception-stop"></a><span data-ttu-id="949aa-2252">Zatrzymanie odbierania mnóstwo klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2252">Host Class Prolific Reception Stop</span></span> 

#### <a name="ux_host_class_prolific_reception_stop"></a><span data-ttu-id="949aa-2253">ux_host_class_prolific_reception_stop</span><span class="sxs-lookup"><span data-stu-id="949aa-2253">ux_host_class_prolific_reception_stop</span></span>

<span data-ttu-id="949aa-2254">**Ikona** ![ Ikona zatrzymania odbierania mnóstwo klasy hosta](./media/user-guide/usbx-events/image172.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2254">**Icon** ![Host Class Prolific Reception Stop icon](./media/user-guide/usbx-events/image172.png)</span></span>

<span data-ttu-id="949aa-2255">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2255">**Description**</span></span>

<span data-ttu-id="949aa-2256">To zdarzenie reprezentuje zdarzenie zatrzymania odbioru USBX klasy hosta mnóstwo.</span><span class="sxs-lookup"><span data-stu-id="949aa-2256">This event represents a USBX Host Class Prolific Reception Stop Event.</span></span>

<span data-ttu-id="949aa-2257">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2257">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2258">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2258">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2259">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2259">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2260">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2260">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2261">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2261">Info Field 4: Not used.</span></span>

### <a name="host-class-prolific-write"></a><span data-ttu-id="949aa-2262">Mnóstwo zapisu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2262">Host Class Prolific Write</span></span> 

#### <a name="ux_host_class_prolific_write"></a><span data-ttu-id="949aa-2263">ux_host_class_prolific_write</span><span class="sxs-lookup"><span data-stu-id="949aa-2263">ux_host_class_prolific_write</span></span>

<span data-ttu-id="949aa-2264">**Ikona** ![ Ikona zapisu mnóstwo klasy hosta](./media/user-guide/usbx-events/image173.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2264">**Icon** ![Host Class Prolific Write icon](./media/user-guide/usbx-events/image173.png)</span></span>

<span data-ttu-id="949aa-2265">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2265">**Description**</span></span>

<span data-ttu-id="949aa-2266">To zdarzenie reprezentuje zdarzenie zapisu USBX klasy hosta mnóstwo.</span><span class="sxs-lookup"><span data-stu-id="949aa-2266">This event represents a USBX Host Class Prolific Write Event.</span></span>

<span data-ttu-id="949aa-2267">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2267">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2268">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2268">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2269">Pole informacji 2: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-2269">Info Field 2: Data pointer.</span></span>
- <span data-ttu-id="949aa-2270">Pole informacji 3: Żądana długość.</span><span class="sxs-lookup"><span data-stu-id="949aa-2270">Info Field 3: Requested length.</span></span>
- <span data-ttu-id="949aa-2271">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2271">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-activate"></a><span data-ttu-id="949aa-2272">Aktywuj magazyn klas hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2272">Host Class Storage Activate</span></span> 

#### <a name="ux_host_class_storage_activate"></a><span data-ttu-id="949aa-2273">ux_host_class_storage_activate</span><span class="sxs-lookup"><span data-stu-id="949aa-2273">ux_host_class_storage_activate</span></span>

<span data-ttu-id="949aa-2274">**Ikona** ![ Ikona aktywowania magazynu klasy hosta](./media/user-guide/usbx-events/image174.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2274">**Icon** ![Host Class Storage Activate icon](./media/user-guide/usbx-events/image174.png)</span></span>

<span data-ttu-id="949aa-2275">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2275">**Description**</span></span>

<span data-ttu-id="949aa-2276">To zdarzenie reprezentuje zdarzenie aktywowania magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2276">This event represents a USBX Host Class Storage Activate Event.</span></span>

<span data-ttu-id="949aa-2277">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2277">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2278">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2278">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2279">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2279">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2280">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2280">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2281">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2281">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-deactivate"></a><span data-ttu-id="949aa-2282">Dezaktywowanie magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2282">Host Class Storage Deactivate</span></span> 

#### <a name="ux_host_class_storage_deactivate"></a><span data-ttu-id="949aa-2283">ux_host_class_storage_deactivate</span><span class="sxs-lookup"><span data-stu-id="949aa-2283">ux_host_class_storage_deactivate</span></span>

<span data-ttu-id="949aa-2284">**Ikona** ![ Ikona dezaktywacji magazynu klasy hosta](./media/user-guide/usbx-events/image175.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2284">**Icon** ![Host Class Storage Deactivate icon](./media/user-guide/usbx-events/image175.png)</span></span>

<span data-ttu-id="949aa-2285">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2285">**Description**</span></span>

<span data-ttu-id="949aa-2286">To zdarzenie reprezentuje zdarzenie dezaktywacji magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2286">This event represents a USBX Host Class Storage Deactivate Event.</span></span>

<span data-ttu-id="949aa-2287">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2287">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2288">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2288">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2289">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2289">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2290">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2290">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2291">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2291">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-capacity-get"></a><span data-ttu-id="949aa-2292">Pobieranie pojemności nośnika magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2292">Host Class Storage Media Capacity Get</span></span> 

#### <a name="ux_host_class_storage_media_capacity_get"></a><span data-ttu-id="949aa-2293">ux_host_class_storage_media_capacity_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2293">ux_host_class_storage_media_capacity_get</span></span>

<span data-ttu-id="949aa-2294">**Ikona** ![ Ikona pobierania pojemności nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image176.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2294">**Icon** ![Host Class Storage Media Capacity Get icon](./media/user-guide/usbx-events/image176.png)</span></span>

<span data-ttu-id="949aa-2295">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2295">**Description**</span></span>

<span data-ttu-id="949aa-2296">To zdarzenie reprezentuje zdarzenie pobrania pojemności nośnika magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2296">This event represents a USBX Host Class Storage Media Capacity Get Event.</span></span>

<span data-ttu-id="949aa-2297">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2297">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2298">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2298">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2299">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2299">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2300">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2300">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2301">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2301">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-format-capacity-get"></a><span data-ttu-id="949aa-2302">Pobieranie pojemności formatu nośnika magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2302">Host Class Storage Media Format Capacity Get</span></span>

#### <a name="ux_host_class_storage_media_format_capacity_get"></a><span data-ttu-id="949aa-2303">ux_host_class_storage_media_format_capacity_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2303">ux_host_class_storage_media_format_capacity_get</span></span>

<span data-ttu-id="949aa-2304">**Ikona** ![ Ikona pobierania pojemności formatu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image177.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2304">**Icon** ![Host Class Storage Media Format Capacity Get icon](./media/user-guide/usbx-events/image177.png)</span></span>

<span data-ttu-id="949aa-2305">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2305">**Description**</span></span>

<span data-ttu-id="949aa-2306">To zdarzenie reprezentuje zdarzenie pobrania pojemności formatu nośnika magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2306">This event represents a USBX Host Class Storage Media Format Capacity Get Event.</span></span>

<span data-ttu-id="949aa-2307">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2307">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2308">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2308">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2309">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2309">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2310">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2310">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2311">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2311">Info Field 4: Not used.</span></span>

#### <a name="host-class-storage-media-mount"></a><span data-ttu-id="949aa-2312">Instalacja nośnika magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2312">Host Class Storage Media Mount</span></span> 

#### <a name="ux_host_class_storage_media_mount"></a><span data-ttu-id="949aa-2313">ux_host_class_storage_media_mount</span><span class="sxs-lookup"><span data-stu-id="949aa-2313">ux_host_class_storage_media_mount</span></span>

<span data-ttu-id="949aa-2314">**Ikona** ![ Ikona instalacji nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image178.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2314">**Icon** ![Host Class Storage Media Mount icon](./media/user-guide/usbx-events/image178.png)</span></span>

<span data-ttu-id="949aa-2315">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2315">**Description**</span></span>

<span data-ttu-id="949aa-2316">To zdarzenie reprezentuje zdarzenie instalacji nośnika magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2316">This event represents a USBX Host Class Storage Media Mount Event.</span></span>

<span data-ttu-id="949aa-2317">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2317">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2318">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2318">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2319">Pole informacji 2: sektor.</span><span class="sxs-lookup"><span data-stu-id="949aa-2319">Info Field 2: Sector.</span></span>
- <span data-ttu-id="949aa-2320">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2320">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2321">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2321">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-open"></a><span data-ttu-id="949aa-2322">Otwarty nośnik magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2322">Host Class Storage Media Open</span></span> 

#### <a name="ux_host_class_storage_media_open"></a><span data-ttu-id="949aa-2323">ux_host_class_storage_media_open</span><span class="sxs-lookup"><span data-stu-id="949aa-2323">ux_host_class_storage_media_open</span></span>

<span data-ttu-id="949aa-2324">**Ikona** ![ Ikona otwierania nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image179.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2324">**Icon** ![Host Class Storage Media Open icon](./media/user-guide/usbx-events/image179.png)</span></span>

<span data-ttu-id="949aa-2325">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2325">**Description**</span></span>

<span data-ttu-id="949aa-2326">To zdarzenie reprezentuje zdarzenie otwarcia nośnika magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2326">This event represents a USBX Host Class Storage Media Open Event.</span></span>

<span data-ttu-id="949aa-2327">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2327">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2328">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2328">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2329">Pole informacji 2: Multimedia.</span><span class="sxs-lookup"><span data-stu-id="949aa-2329">Info Field 2: Media.</span></span>
- <span data-ttu-id="949aa-2330">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2330">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2331">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2331">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-media-read"></a><span data-ttu-id="949aa-2332">Odczyt nośnika magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2332">Host Class Storage Media Read</span></span> 

#### <a name="ux_host_class_storage_media_read"></a><span data-ttu-id="949aa-2333">ux_host_class_storage_media_read</span><span class="sxs-lookup"><span data-stu-id="949aa-2333">ux_host_class_storage_media_read</span></span>

<span data-ttu-id="949aa-2334">**Ikona** ![ Ikona odczytu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image180.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2334">**Icon** ![Host Class Storage Media Read icon](./media/user-guide/usbx-events/image180.png)</span></span>

<span data-ttu-id="949aa-2335">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2335">**Description**</span></span>

<span data-ttu-id="949aa-2336">To zdarzenie reprezentuje zdarzenie odczytu nośnika magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2336">This event represents a USBX Host Class Storage Media Read Event.</span></span>

<span data-ttu-id="949aa-2337">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2337">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2338">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2338">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2339">Pole informacji 2: początek sektora.</span><span class="sxs-lookup"><span data-stu-id="949aa-2339">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="949aa-2340">Pole informacji 3: liczba sektorów.</span><span class="sxs-lookup"><span data-stu-id="949aa-2340">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="949aa-2341">Pole informacji 4: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-2341">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-media-write"></a><span data-ttu-id="949aa-2342">Zapis nośnika magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2342">Host Class Storage Media Write</span></span> 

#### <a name="ux_host_class_storage_media_write"></a><span data-ttu-id="949aa-2343">ux_host_class_storage_media_write</span><span class="sxs-lookup"><span data-stu-id="949aa-2343">ux_host_class_storage_media_write</span></span>

<span data-ttu-id="949aa-2344">**Ikona** ![ Ikona zapisu nośnika magazynu klasy hosta](./media/user-guide/usbx-events/image181.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2344">**Icon** ![Host Class Storage Media Write icon](./media/user-guide/usbx-events/image181.png)</span></span>

<span data-ttu-id="949aa-2345">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2345">**Description**</span></span>

<span data-ttu-id="949aa-2346">To zdarzenie reprezentuje zdarzenie zapisu nośnika magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2346">This event represents a USBX Host Class Storage Media Write Event.</span></span>

<span data-ttu-id="949aa-2347">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2347">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2348">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2348">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2349">Pole informacji 2: początek sektora.</span><span class="sxs-lookup"><span data-stu-id="949aa-2349">Info Field 2: Sector start.</span></span>
- <span data-ttu-id="949aa-2350">Pole informacji 3: liczba sektorów.</span><span class="sxs-lookup"><span data-stu-id="949aa-2350">Info Field 3: Sector count.</span></span>
- <span data-ttu-id="949aa-2351">Pole informacji 4: wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="949aa-2351">Info Field 4: Data pointer.</span></span>

### <a name="host-class-storage-request-sense"></a><span data-ttu-id="949aa-2352">Wykrywanie żądania magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2352">Host Class Storage Request Sense</span></span> 

#### <a name="ux_host_class_storage_request_sense"></a><span data-ttu-id="949aa-2353">ux_host_class_storage_request_sense</span><span class="sxs-lookup"><span data-stu-id="949aa-2353">ux_host_class_storage_request_sense</span></span>

<span data-ttu-id="949aa-2354">**Ikona** ![ Ikona wykrywania żądań magazynu klasy hosta](./media/user-guide/usbx-events/image182.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2354">**Icon** ![Host Class Storage Request Sense icon](./media/user-guide/usbx-events/image182.png)</span></span>

<span data-ttu-id="949aa-2355">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2355">**Description**</span></span>

<span data-ttu-id="949aa-2356">To zdarzenie reprezentuje zdarzenie wykrywania żądania magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2356">This event represents a USBX Host Class Storage Request Sense Event.</span></span>

<span data-ttu-id="949aa-2357">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2357">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2358">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2358">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2359">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2359">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2360">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2360">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2361">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2361">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-start-stop"></a><span data-ttu-id="949aa-2362">Zatrzymanie uruchomienia magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2362">Host Class Storage Start Stop</span></span> 

#### <a name="ux_host_class_storage_start_stop"></a><span data-ttu-id="949aa-2363">ux_host_class_storage_start_stop</span><span class="sxs-lookup"><span data-stu-id="949aa-2363">ux_host_class_storage_start_stop</span></span>

<span data-ttu-id="949aa-2364">**Ikona** ![ Ikona zatrzymania uruchamiania magazynu klasy hosta](./media/user-guide/usbx-events/image183.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2364">**Icon** ![Host Class Storage Start Stop icon](./media/user-guide/usbx-events/image183.png)</span></span>

<span data-ttu-id="949aa-2365">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2365">**Description**</span></span>

<span data-ttu-id="949aa-2366">To zdarzenie reprezentuje zdarzenie zatrzymania uruchamiania magazynu klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2366">This event represents a USBX Host Class Storage Start Stop Event.</span></span>

<span data-ttu-id="949aa-2367">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2367">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2368">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2368">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2369">Pole informacji 2: Uruchom sygnał zatrzymania.</span><span class="sxs-lookup"><span data-stu-id="949aa-2369">Info Field 2: Start stop signal.</span></span>
- <span data-ttu-id="949aa-2370">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2370">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2371">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2371">Info Field 4: Not used.</span></span>

### <a name="host-class-storage-unit-ready-test"></a><span data-ttu-id="949aa-2372">Gotowy test jednostki magazynu klasy hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2372">Host Class Storage Unit Ready Test</span></span> 

#### <a name="ux_host_class_storage_unit_ready_test"></a><span data-ttu-id="949aa-2373">ux_host_class_storage_unit_ready_test</span><span class="sxs-lookup"><span data-stu-id="949aa-2373">ux_host_class_storage_unit_ready_test</span></span>

<span data-ttu-id="949aa-2374">**Ikona** ![ Ikona testowania gotowej jednostki magazynu klasy hosta](./media/user-guide/usbx-events/image184.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2374">**Icon** ![Host Class Storage Unit Ready Test icon](./media/user-guide/usbx-events/image184.png)</span></span>

<span data-ttu-id="949aa-2375">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2375">**Description**</span></span>

<span data-ttu-id="949aa-2376">To zdarzenie reprezentuje zdarzenie testowania gotowej jednostki magazynowej klasy hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2376">This event represents a USBX Host Class Storage Unit Ready Test Event.</span></span>

<span data-ttu-id="949aa-2377">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2377">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2378">Pole informacji 1: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2378">Info Field 1: Class instance.</span></span>
- <span data-ttu-id="949aa-2379">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2379">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2380">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2380">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2381">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2381">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-create"></a><span data-ttu-id="949aa-2382">Tworzenie wystąpienia klasy stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2382">Host Stack Class Instance Create</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="949aa-2383">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="949aa-2383">ux_host_class_instance_create</span></span>

<span data-ttu-id="949aa-2384">**Ikona** ![ Ikona tworzenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image185.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2384">**Icon** ![Host Stack Class Instance Create icon](./media/user-guide/usbx-events/image185.png)</span></span>

<span data-ttu-id="949aa-2385">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2385">**Description**</span></span>

<span data-ttu-id="949aa-2386">To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia klasy stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2386">This event represents a USBX Host Stack Class Instance Create Event.</span></span>

<span data-ttu-id="949aa-2387">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2387">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2388">Pole informacji 1: Klasa.</span><span class="sxs-lookup"><span data-stu-id="949aa-2388">Info Field 1: Class.</span></span>
- <span data-ttu-id="949aa-2389">Pole informacji 2: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2389">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="949aa-2390">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2390">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2391">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2391">Info Field 4: Not used.</span></span>

### <a name="host-stack-class-instance-destroy"></a><span data-ttu-id="949aa-2392">Niszczenie wystąpienia klasy stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2392">Host Stack Class Instance Destroy</span></span> 

#### <a name="ux_host_class_instance_create"></a><span data-ttu-id="949aa-2393">ux_host_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="949aa-2393">ux_host_class_instance_create</span></span>

<span data-ttu-id="949aa-2394">**Ikona** ![ Ikona niszczenia wystąpienia klasy stosu hosta](./media/user-guide/usbx-events/image186.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2394">**Icon** ![Host Stack Class Instance Destroy icon](./media/user-guide/usbx-events/image186.png)</span></span>

<span data-ttu-id="949aa-2395">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2395">**Description**</span></span>

<span data-ttu-id="949aa-2396">To zdarzenie reprezentuje zdarzenie zniszczenia wystąpienia klasy stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2396">This event represents a USBX Host Stack Class Instance Destroy Event.</span></span>

<span data-ttu-id="949aa-2397">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2397">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2398">Pole informacji 1: Klasa.</span><span class="sxs-lookup"><span data-stu-id="949aa-2398">Info Field 1: Class.</span></span>
- <span data-ttu-id="949aa-2399">Pole informacji 2: wystąpienie klasy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2399">Info Field 2: Class Instance.</span></span>
- <span data-ttu-id="949aa-2400">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2400">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2401">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2401">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-delete"></a><span data-ttu-id="949aa-2402">Usuwanie konfiguracji stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2402">Host Stack Configuration Delete</span></span> 

#### <a name="ux_host_class_configuration_delete"></a><span data-ttu-id="949aa-2403">ux_host_class_configuration_delete</span><span class="sxs-lookup"><span data-stu-id="949aa-2403">ux_host_class_configuration_delete</span></span>

<span data-ttu-id="949aa-2404">**Ikona** ![ Ikona usuwania konfiguracji stosu hosta](./media/user-guide/usbx-events/image187.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2404">**Icon** ![Host Stack Configuration Delete icon](./media/user-guide/usbx-events/image187.png)</span></span>

<span data-ttu-id="949aa-2405">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2405">**Description**</span></span>

<span data-ttu-id="949aa-2406">To zdarzenie reprezentuje zdarzenie usunięcia konfiguracji stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2406">This event represents a USBX Host Stack Configuration Delete Event.</span></span>

<span data-ttu-id="949aa-2407">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2407">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2408">Pole informacji 1: konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="949aa-2408">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="949aa-2409">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2409">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2410">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2410">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2411">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2411">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-enumerate"></a><span data-ttu-id="949aa-2412">Wyliczenie konfiguracji stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2412">Host Stack Configuration Enumerate</span></span> 

#### <a name="ux_host_stack_configuration_enumerate"></a><span data-ttu-id="949aa-2413">ux_host_stack_configuration_enumerate</span><span class="sxs-lookup"><span data-stu-id="949aa-2413">ux_host_stack_configuration_enumerate</span></span>

<span data-ttu-id="949aa-2414">**Ikona** ![ Ikona wyliczenia konfiguracji stosu hosta](./media/user-guide/usbx-events/image188.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2414">**Icon** ![Host Stack Configuration Enumerate icon](./media/user-guide/usbx-events/image188.png)</span></span>

<span data-ttu-id="949aa-2415">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2415">**Description**</span></span>

<span data-ttu-id="949aa-2416">To zdarzenie reprezentuje zdarzenie wyliczania konfiguracji stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2416">This event represents a USBX Host Stack Configuration Enumerate Event.</span></span>

<span data-ttu-id="949aa-2417">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2417">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2418">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2418">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2419">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2419">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2420">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2420">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2421">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2421">Info Field 4: Not used.</span></span>

### <a name="stack-configuration-instance-create"></a><span data-ttu-id="949aa-2422">Tworzenie wystąpienia konfiguracji stosu</span><span class="sxs-lookup"><span data-stu-id="949aa-2422">Stack Configuration Instance Create</span></span> 

#### <a name="ux_host_stack_configuration_instance_create"></a><span data-ttu-id="949aa-2423">ux_host_stack_configuration_instance_create</span><span class="sxs-lookup"><span data-stu-id="949aa-2423">ux_host_stack_configuration_instance_create</span></span>

<span data-ttu-id="949aa-2424">**Ikona** ![ Ikona tworzenia wystąpienia konfiguracji stosu](./media/user-guide/usbx-events/image189.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2424">**Icon** ![Stack Configuration Instance Create icon](./media/user-guide/usbx-events/image189.png)</span></span>

<span data-ttu-id="949aa-2425">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2425">**Description**</span></span>

<span data-ttu-id="949aa-2426">To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia konfiguracji stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2426">This event represents a USBX Host Stack Configuration Instance Create Event.</span></span>

<span data-ttu-id="949aa-2427">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2427">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2428">Pole informacji 1: konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="949aa-2428">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="949aa-2429">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2429">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2430">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2430">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2431">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2431">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-instance-delete"></a><span data-ttu-id="949aa-2432">Usuwanie wystąpienia konfiguracji stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2432">Host Stack Configuration Instance Delete</span></span> 

#### <a name="ux_host_stack_configuration_instance_delete"></a><span data-ttu-id="949aa-2433">ux_host_stack_configuration_instance_delete</span><span class="sxs-lookup"><span data-stu-id="949aa-2433">ux_host_stack_configuration_instance_delete</span></span>

<span data-ttu-id="949aa-2434">**Ikona** ![ Ikona usuwania wystąpienia konfiguracji stosu hosta](./media/user-guide/usbx-events/image190.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2434">**Icon** ![Host Stack Configuration Instance Delete icon](./media/user-guide/usbx-events/image190.png)</span></span>

<span data-ttu-id="949aa-2435">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2435">**Description**</span></span>

<span data-ttu-id="949aa-2436">To zdarzenie reprezentuje zdarzenie usunięcia wystąpienia konfiguracji stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2436">This event represents a USBX Host Stack Configuration Instance Delete Event.</span></span>

<span data-ttu-id="949aa-2437">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2437">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2438">Pole informacji 1: konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="949aa-2438">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="949aa-2439">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2439">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2440">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2440">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2441">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2441">Info Field 4: Not used.</span></span>

### <a name="host-stack-configuration-set"></a><span data-ttu-id="949aa-2442">Zestaw konfiguracyjny stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2442">Host Stack Configuration Set</span></span> 

#### <a name="ux_host_stack_configuration_set"></a><span data-ttu-id="949aa-2443">ux_host_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="949aa-2443">ux_host_stack_configuration_set</span></span>

<span data-ttu-id="949aa-2444">**Ikona** ![ Ikona zestawu konfiguracji stosu hosta](./media/user-guide/usbx-events/image191.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2444">**Icon** ![Host Stack Configuration Set icon](./media/user-guide/usbx-events/image191.png)</span></span>

<span data-ttu-id="949aa-2445">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2445">**Description**</span></span>

<span data-ttu-id="949aa-2446">To zdarzenie reprezentuje zdarzenie zestawu konfiguracji stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2446">This event represents a USBX Host Stack Configuration Set Event.</span></span>

<span data-ttu-id="949aa-2447">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2447">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2448">Pole informacji 1: konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="949aa-2448">Info Field 1: Configuration.</span></span>
- <span data-ttu-id="949aa-2449">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2449">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2450">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2450">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2451">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2451">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-address-set"></a><span data-ttu-id="949aa-2452">Zestaw adresów urządzeń stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2452">Host Stack Device Address Set</span></span> 

#### <a name="ux_host_stack_device_address_set"></a><span data-ttu-id="949aa-2453">ux_host_stack_device_address_set</span><span class="sxs-lookup"><span data-stu-id="949aa-2453">ux_host_stack_device_address_set</span></span>

<span data-ttu-id="949aa-2454">**Ikona** ![ Ikona zestawu adresów urządzeń stosu hosta](./media/user-guide/usbx-events/image192.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2454">**Icon** ![Host Stack Device Address Set icon](./media/user-guide/usbx-events/image192.png)</span></span>

<span data-ttu-id="949aa-2455">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2455">**Description**</span></span>

<span data-ttu-id="949aa-2456">To zdarzenie reprezentuje zdarzenie zestawu adresów urządzenia stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2456">This event represents a USBX Host Stack Device Address Set Event.</span></span>

<span data-ttu-id="949aa-2457">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2457">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2458">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2458">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2459">Pole informacji 2: adres urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-2459">Info Field 2: Device Address.</span></span>
- <span data-ttu-id="949aa-2460">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2460">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2461">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2461">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-get"></a><span data-ttu-id="949aa-2462">Pobieranie konfiguracji urządzenia stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2462">Host Stack Device Configuration Get</span></span> 

#### <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="949aa-2463">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2463">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="949aa-2464">**Ikona** ![ Ikona pobierania konfiguracji urządzenia stosu hosta](./media/user-guide/usbx-events/image193.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2464">**Icon** ![Host Stack Device Configuration Get icon](./media/user-guide/usbx-events/image193.png)</span></span>

<span data-ttu-id="949aa-2465">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2465">**Description**</span></span>

<span data-ttu-id="949aa-2466">To zdarzenie reprezentuje zdarzenie pobrania konfiguracji urządzenia stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2466">This event represents a USBX Host Stack Device Configuration Get Event.</span></span>

<span data-ttu-id="949aa-2467">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2467">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2468">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2468">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2469">NFO pole 2: konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="949aa-2469">nfo Field 2: Configuration.</span></span>
- <span data-ttu-id="949aa-2470">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2470">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2471">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2471">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-configuration-select"></a><span data-ttu-id="949aa-2472">Wybór konfiguracji urządzenia stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2472">Host Stack Device Configuration Select</span></span> 

#### <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="949aa-2473">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="949aa-2473">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="949aa-2474">**Ikona** ![ Ikona wybierania konfiguracji urządzenia stosu hosta](./media/user-guide/usbx-events/image194.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2474">**Icon** ![Host Stack Device Configuration Select icon](./media/user-guide/usbx-events/image194.png)</span></span>

<span data-ttu-id="949aa-2475">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2475">**Description**</span></span>

<span data-ttu-id="949aa-2476">To zdarzenie reprezentuje zdarzenie wybierania konfiguracji urządzenia stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2476">This event represents a USBX Host Stack Device Configuration Select Event.</span></span>

<span data-ttu-id="949aa-2477">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2477">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2478">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2478">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2479">Pole informacji 2: konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="949aa-2479">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="949aa-2480">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2480">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2481">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2481">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-descriptor-read"></a><span data-ttu-id="949aa-2482">Odczyt deskryptora urządzenia stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2482">Host Stack Device Descriptor Read</span></span> 

#### <a name="ux_host_stack_device_descriptor_read"></a><span data-ttu-id="949aa-2483">ux_host_stack_device_descriptor_read</span><span class="sxs-lookup"><span data-stu-id="949aa-2483">ux_host_stack_device_descriptor_read</span></span>

<span data-ttu-id="949aa-2484">**Ikona** ![ Ikona odczytu deskryptora urządzenia stosu hosta](./media/user-guide/usbx-events/image195.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2484">**Icon** ![Host Stack Device Descriptor Read icon](./media/user-guide/usbx-events/image195.png)</span></span>

<span data-ttu-id="949aa-2485">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2485">**Description**</span></span>

<span data-ttu-id="949aa-2486">To zdarzenie reprezentuje zdarzenie odczytu deskryptora urządzenia stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2486">This event represents a USBX Host Stack Device Descriptor Read Event.</span></span>

<span data-ttu-id="949aa-2487">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2487">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2488">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2488">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2489">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2489">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2490">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2490">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2491">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2491">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-get"></a><span data-ttu-id="949aa-2492">Pobieranie urządzenia stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2492">Host Stack Device Get</span></span> 

#### <a name="ux_host_stack_device_get"></a><span data-ttu-id="949aa-2493">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="949aa-2493">ux_host_stack_device_get</span></span>

<span data-ttu-id="949aa-2494">**Ikona** ![ Ikona pobierania urządzenia stosu hosta](./media/user-guide/usbx-events/image196.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2494">**Icon** ![Host Stack Device Get icon](./media/user-guide/usbx-events/image196.png)</span></span>

<span data-ttu-id="949aa-2495">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2495">**Description**</span></span>

<span data-ttu-id="949aa-2496">To zdarzenie reprezentuje zdarzenie pobrania urządzenia stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2496">This event represents a USBX Host Stack Device Get Event.</span></span>

<span data-ttu-id="949aa-2497">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2497">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2498">Pole informacji 1: indeks urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-2498">Info Field 1: Device index.</span></span>
- <span data-ttu-id="949aa-2499">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2499">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2500">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2500">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2501">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2501">Info Field 4: Not used.</span></span>

### <a name="host-stack-device-remove"></a><span data-ttu-id="949aa-2502">Usuwanie urządzenia stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2502">Host Stack Device Remove</span></span> 

#### <a name="ux_host_stack_device_remove"></a><span data-ttu-id="949aa-2503">ux_host_stack_device_remove</span><span class="sxs-lookup"><span data-stu-id="949aa-2503">ux_host_stack_device_remove</span></span>

<span data-ttu-id="949aa-2504">**Ikona** ![ Ikona usuwania urządzenia stosu hosta](./media/user-guide/usbx-events/image197.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2504">**Icon** ![Host Stack Device Remove icon](./media/user-guide/usbx-events/image197.png)</span></span>

<span data-ttu-id="949aa-2505">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2505">**Description**</span></span>

<span data-ttu-id="949aa-2506">To zdarzenie reprezentuje zdarzenie usunięcia urządzenia stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2506">This event represents a USBX Host Stack Device Remove Event.</span></span>

<span data-ttu-id="949aa-2507">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2507">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2508">Pole informacji 1: HCD.</span><span class="sxs-lookup"><span data-stu-id="949aa-2508">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="949aa-2509">Pole informacji 2: element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="949aa-2509">Info Field 2: Parent.</span></span>
- <span data-ttu-id="949aa-2510">Pole informacji 3: indeks portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2510">Info Field 3: Port Index.</span></span>
- <span data-ttu-id="949aa-2511">Pole informacji 4: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2511">Info Field 4: Device.</span></span>

### <a name="host-stack-device-resource-free"></a><span data-ttu-id="949aa-2512">Zasób urządzenia stosu hosta bezpłatnie</span><span class="sxs-lookup"><span data-stu-id="949aa-2512">Host Stack Device Resource Free</span></span> 

#### <a name="ux_host_stack_device_resource_free"></a><span data-ttu-id="949aa-2513">ux_host_stack_device_resource_free</span><span class="sxs-lookup"><span data-stu-id="949aa-2513">ux_host_stack_device_resource_free</span></span>

<span data-ttu-id="949aa-2514">**Ikona** ![ Ikona bezpłatnego zasobu urządzenia stosu hosta](./media/user-guide/usbx-events/image198.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2514">**Icon** ![Host Stack Device Resource Free icon](./media/user-guide/usbx-events/image198.png)</span></span>

<span data-ttu-id="949aa-2515">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2515">**Description**</span></span>

<span data-ttu-id="949aa-2516">To zdarzenie reprezentuje zdarzenie bezpłatne zasobów urządzenia stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2516">This event represents a USBX Host Stack Device Resource Free Event.</span></span>

<span data-ttu-id="949aa-2517">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2517">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2518">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2518">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2519">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2519">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2520">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2520">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2521">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2521">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-create"></a><span data-ttu-id="949aa-2522">Tworzenie wystąpienia punktu końcowego stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2522">Host Stack Endpoint Instance Create</span></span> 

#### <a name="ux_host_stack_endpoint_instance_create"></a><span data-ttu-id="949aa-2523">ux_host_stack_endpoint_instance_create</span><span class="sxs-lookup"><span data-stu-id="949aa-2523">ux_host_stack_endpoint_instance_create</span></span>

<span data-ttu-id="949aa-2524">**Ikona** ![ Ikona tworzenia wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image199.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2524">**Icon** ![Host Stack Endpoint Instance Create icon](./media/user-guide/usbx-events/image199.png)</span></span>

<span data-ttu-id="949aa-2525">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2525">**Description**</span></span>

<span data-ttu-id="949aa-2526">To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia punktu końcowego stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2526">This event represents a USBX Host Stack Endpoint Instance Create Event.</span></span>

<span data-ttu-id="949aa-2527">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2527">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2528">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2528">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2529">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2529">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-2530">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2530">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2531">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2531">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-instance-delete"></a><span data-ttu-id="949aa-2532">Usuwanie wystąpienia punktu końcowego stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2532">Host Stack Endpoint Instance Delete</span></span> 

#### <a name="ux_host_stack_endpoint_instance_delete"></a><span data-ttu-id="949aa-2533">ux_host_stack_endpoint_instance_delete</span><span class="sxs-lookup"><span data-stu-id="949aa-2533">ux_host_stack_endpoint_instance_delete</span></span>

<span data-ttu-id="949aa-2534">**Ikona** ![ Ikona usuwania wystąpienia punktu końcowego stosu hosta](./media/user-guide/usbx-events/image200.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2534">**Icon** ![Host Stack Endpoint Instance Delete icon](./media/user-guide/usbx-events/image200.png)</span></span>

<span data-ttu-id="949aa-2535">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2535">**Description**</span></span>

<span data-ttu-id="949aa-2536">To zdarzenie reprezentuje zdarzenie usuwania wystąpienia punktu końcowego stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2536">This event represents a USBX Host Stack Endpoint Instance Delete Event.</span></span>

<span data-ttu-id="949aa-2537">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2537">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2538">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2538">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-2539">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2539">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2540">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2540">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-reset"></a><span data-ttu-id="949aa-2541">Resetowanie punktu końcowego stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2541">Host Stack Endpoint Reset</span></span> 

#### <a name="ux_host_stack_endpoint_reset"></a><span data-ttu-id="949aa-2542">ux_host_stack_endpoint_reset</span><span class="sxs-lookup"><span data-stu-id="949aa-2542">ux_host_stack_endpoint_reset</span></span>

<span data-ttu-id="949aa-2543">**Ikona** ![ Ikona resetowania punktu końcowego stosu hosta](./media/user-guide/usbx-events/image201.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2543">**Icon** ![Host Stack Endpoint Reset icon](./media/user-guide/usbx-events/image201.png)</span></span>

<span data-ttu-id="949aa-2544">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2544">**Description**</span></span>

<span data-ttu-id="949aa-2545">To zdarzenie reprezentuje zdarzenie resetowania punktu końcowego stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2545">This event represents a USBX Host Stack Endpoint Reset Event.</span></span>

<span data-ttu-id="949aa-2546">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2546">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2547">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2547">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2548">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2548">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-2549">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2549">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2550">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2550">Info Field 4: Not used.</span></span>

### <a name="host-stack-endpoint-transfer-abort"></a><span data-ttu-id="949aa-2551">Przerwanie transferu punktu końcowego stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2551">Host Stack Endpoint Transfer Abort</span></span> 

#### <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="949aa-2552">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="949aa-2552">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="949aa-2553">**Ikona** ![ Ikona przerwania transferu punktu końcowego stosu hosta](./media/user-guide/usbx-events/image202.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2553">**Icon** ![Host Stack Endpoint Transfer Abort icon](./media/user-guide/usbx-events/image202.png)</span></span>

<span data-ttu-id="949aa-2554">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2554">**Description**</span></span>

<span data-ttu-id="949aa-2555">To zdarzenie reprezentuje zdarzenie przerwania transferu punktu końcowego stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2555">This event represents a USBX Host Stack Endpoint Transfer Abort Event.</span></span>

<span data-ttu-id="949aa-2556">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2556">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2557">Pole informacji 1: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2557">Info Field 1: Endpoint.</span></span>
- <span data-ttu-id="949aa-2558">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2558">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2559">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2559">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2560">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2560">Info Field 4: Not used.</span></span>

### <a name="host-stack-host-controller-register"></a><span data-ttu-id="949aa-2561">Rejestr kontrolera hosta stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2561">Host Stack Host Controller Register</span></span> 

#### <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="949aa-2562">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="949aa-2562">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="949aa-2563">**Ikona** ![ Ikona rejestru kontrolera hosta stosu hosta](./media/user-guide/usbx-events/image203.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2563">**Icon** ![Host Stack Host Controller Register icon](./media/user-guide/usbx-events/image203.png)</span></span>

<span data-ttu-id="949aa-2564">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2564">**Description**</span></span>

<span data-ttu-id="949aa-2565">To zdarzenie reprezentuje rejestr kontrolera hosta stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2565">This event represents a USBX Host Stack Host Controller Register.</span></span>

<span data-ttu-id="949aa-2566">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2566">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2567">Pole informacji 1: Nazwa HCD.</span><span class="sxs-lookup"><span data-stu-id="949aa-2567">Info Field 1: Hcd Name.</span></span>
- <span data-ttu-id="949aa-2568">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2568">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2569">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2569">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2570">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2570">Info Field 4: Not used.</span></span>

### <a name="host-stack-initialize"></a><span data-ttu-id="949aa-2571">Inicjowanie stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2571">Host Stack Initialize</span></span> 

#### <a name="ux_host_stack_initialize"></a><span data-ttu-id="949aa-2572">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="949aa-2572">ux_host_stack_initialize</span></span>

<span data-ttu-id="949aa-2573">**Ikona** ![ Ikona inicjowania stosu hosta](./media/user-guide/usbx-events/image204.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2573">**Icon** ![Host Stack Initialize icon](./media/user-guide/usbx-events/image204.png)</span></span>

<span data-ttu-id="949aa-2574">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2574">**Description**</span></span>

<span data-ttu-id="949aa-2575">To zdarzenie reprezentuje zdarzenie inicjowania stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2575">This event represents a USBX Host Stack Initialize Event.</span></span>

<span data-ttu-id="949aa-2576">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2576">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2577">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2577">Info Field 1: Not used.</span></span>
- <span data-ttu-id="949aa-2578">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2578">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2579">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2579">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2580">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2580">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-endpoint-get"></a><span data-ttu-id="949aa-2581">Pobieranie punktu końcowego interfejsu stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2581">Host Stack Interface Endpoint Get</span></span> 

#### <a name="interface_-tcp-retry-entry"></a><span data-ttu-id="949aa-2582">Interface_ wpis ponownych prób protokołu TCP</span><span class="sxs-lookup"><span data-stu-id="949aa-2582">Interface_ TCP retry entry</span></span>

<span data-ttu-id="949aa-2583">**Ikona** ![ Ikona pobierania punktu końcowego interfejsu stosu hosta](./media/user-guide/usbx-events/image205.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2583">**Icon** ![Host Stack Interface Endpoint Get icon](./media/user-guide/usbx-events/image205.png)</span></span>

<span data-ttu-id="949aa-2584">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2584">**Description**</span></span>

<span data-ttu-id="949aa-2585">To zdarzenie reprezentuje wewnętrzne zdarzenie ponowienia protokołu TCP NetX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2585">This event represents an internal NetX TCP retry event.</span></span>

<span data-ttu-id="949aa-2586">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2586">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2587">Pole informacji 1: interfejs.</span><span class="sxs-lookup"><span data-stu-id="949aa-2587">Info Field 1: Interface.</span></span>
- <span data-ttu-id="949aa-2588">Pole informacji 2: Indeks punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="949aa-2588">Info Field 2: Endpoint index.</span></span>
- <span data-ttu-id="949aa-2589">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2589">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2590">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2590">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-create"></a><span data-ttu-id="949aa-2591">Tworzenie wystąpienia interfejsu stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2591">Host Stack Interface Instance Create</span></span> 

#### <a name="ux_host_stack_interface_instance_create"></a><span data-ttu-id="949aa-2592">ux_host_stack_interface_instance_create</span><span class="sxs-lookup"><span data-stu-id="949aa-2592">ux_host_stack_interface_instance_create</span></span>

<span data-ttu-id="949aa-2593">**Ikona** ![ Ikona tworzenia wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image206.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2593">**Icon** ![Host Stack Interface Instance Create icon](./media/user-guide/usbx-events/image206.png)</span></span>

<span data-ttu-id="949aa-2594">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2594">**Description**</span></span>

<span data-ttu-id="949aa-2595">To zdarzenie reprezentuje zdarzenie tworzenia wystąpienia interfejsu stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2595">This event represents a USBX Host Stack Interface Instance Create Event.</span></span>

<span data-ttu-id="949aa-2596">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2596">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2597">Pole informacji 1: interfejs.</span><span class="sxs-lookup"><span data-stu-id="949aa-2597">Info Field 1: Interface.</span></span>
- <span data-ttu-id="949aa-2598">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2598">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2599">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2599">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2600">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2600">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-instance-delete"></a><span data-ttu-id="949aa-2601">Usuwanie wystąpienia interfejsu stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2601">Host Stack Interface Instance Delete</span></span> 

#### <a name="ux_host_stack_interface_instance_delete"></a><span data-ttu-id="949aa-2602">ux_host_stack_interface_instance_delete</span><span class="sxs-lookup"><span data-stu-id="949aa-2602">ux_host_stack_interface_instance_delete</span></span>

<span data-ttu-id="949aa-2603">**Ikona** ![ Ikona usuwania wystąpienia interfejsu stosu hosta](./media/user-guide/usbx-events/image207.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2603">**Icon** ![Host Stack Interface Instance Delete icon](./media/user-guide/usbx-events/image207.png)</span></span>

<span data-ttu-id="949aa-2604">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2604">**Description**</span></span>

<span data-ttu-id="949aa-2605">To zdarzenie reprezentuje zdarzenie usunięcia wystąpienia interfejsu stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2605">This event represents a USBX Host Stack Interface Instance Delete Event.</span></span>

<span data-ttu-id="949aa-2606">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2606">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2607">Pole informacji 1: interfejs.</span><span class="sxs-lookup"><span data-stu-id="949aa-2607">Info Field 1: Interface.</span></span>
- <span data-ttu-id="949aa-2608">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2608">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2609">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2609">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2610">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2610">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-set"></a><span data-ttu-id="949aa-2611">Zestaw interfejsów stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2611">Host Stack Interface Set</span></span> 

#### <a name="ux_host_stack_interface_set"></a><span data-ttu-id="949aa-2612">ux_host_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="949aa-2612">ux_host_stack_interface_set</span></span>

<span data-ttu-id="949aa-2613">**Ikona** ![ Ikona zestawu interfejsów stosu hosta](./media/user-guide/usbx-events/image208.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2613">**Icon** ![Host Stack Interface Set icon](./media/user-guide/usbx-events/image208.png)</span></span>

<span data-ttu-id="949aa-2614">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2614">**Description**</span></span>

<span data-ttu-id="949aa-2615">To zdarzenie reprezentuje zdarzenie zestawu interfejsu stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2615">This event represents a USBX Host Stack Interface Set Event.</span></span>

<span data-ttu-id="949aa-2616">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2616">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2617">Pole informacji 1: interfejs.</span><span class="sxs-lookup"><span data-stu-id="949aa-2617">Info Field 1: Interface.</span></span>
- <span data-ttu-id="949aa-2618">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2618">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2619">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2619">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2620">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2620">Info Field 4: Not used.</span></span>

### <a name="host-stack-interface-setting-select"></a><span data-ttu-id="949aa-2621">Wybieranie ustawienia interfejsu stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2621">Host Stack Interface Setting Select</span></span> 

#### <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="949aa-2622">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="949aa-2622">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="949aa-2623">**Ikona** ![ Ikona wybierania ustawienia interfejsu stosu hosta](./media/user-guide/usbx-events/image209.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2623">**Icon** ![Host Stack Interface Setting Select icon](./media/user-guide/usbx-events/image209.png)</span></span>

<span data-ttu-id="949aa-2624">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2624">**Description**</span></span>

<span data-ttu-id="949aa-2625">To zdarzenie przedstawia zdarzenie select dla ustawienia interfejsu stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2625">This event represents a USBX Host Stack Interface Setting Select Event.</span></span>

<span data-ttu-id="949aa-2626">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2626">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2627">Pole informacji 1: interfejs.</span><span class="sxs-lookup"><span data-stu-id="949aa-2627">Info Field 1: Interface.</span></span>
- <span data-ttu-id="949aa-2628">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2628">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2629">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2629">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2630">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2630">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-configuration-create"></a><span data-ttu-id="949aa-2631">Tworzenie nowej konfiguracji stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2631">Host Stack New Configuration Create</span></span> 

#### <a name="ux_host_stack_new_configuration_create"></a><span data-ttu-id="949aa-2632">ux_host_stack_new_configuration_create</span><span class="sxs-lookup"><span data-stu-id="949aa-2632">ux_host_stack_new_configuration_create</span></span>

<span data-ttu-id="949aa-2633">**Ikona** ![ Ikona tworzenia nowej konfiguracji stosu hosta](./media/user-guide/usbx-events/image210.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2633">**Icon** ![Host Stack New Configuration Create icon](./media/user-guide/usbx-events/image210.png)</span></span>

<span data-ttu-id="949aa-2634">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2634">**Description**</span></span>
 
<span data-ttu-id="949aa-2635">To zdarzenie reprezentuje zdarzenie tworzenia nowej konfiguracji w stosie hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2635">This event represents a USBX Host Stack New Configuration Create Event.</span></span>

<span data-ttu-id="949aa-2636">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2636">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2637">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2637">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2638">Pole informacji 2: konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="949aa-2638">Info Field 2: Configuration.</span></span>
- <span data-ttu-id="949aa-2639">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2639">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2640">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2640">Info Field 4: Not used.</span></span>

### <a name="host-stack-new-device-create"></a><span data-ttu-id="949aa-2641">Tworzenie nowego urządzenia przez stos hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2641">Host Stack New Device Create</span></span> 

#### <a name="ux_host_stack_new_device_create"></a><span data-ttu-id="949aa-2642">ux_host_stack_new_device_create</span><span class="sxs-lookup"><span data-stu-id="949aa-2642">ux_host_stack_new_device_create</span></span>

<span data-ttu-id="949aa-2643">**Ikona** ![ Ikona tworzenia nowego urządzenia dla stosu hosta](./media/user-guide/usbx-events/image211.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2643">**Icon** ![Host Stack New Device Create icon](./media/user-guide/usbx-events/image211.png)</span></span>

<span data-ttu-id="949aa-2644">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2644">**Description**</span></span>
 
 <span data-ttu-id="949aa-2645">To zdarzenie reprezentuje zdarzenie tworzenia nowego urządzenia przez stos hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2645">This event represents a USBX Host Stack New Device Create Event.</span></span>

<span data-ttu-id="949aa-2646">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2646">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2647">Pole informacji 1: HCD.</span><span class="sxs-lookup"><span data-stu-id="949aa-2647">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="949aa-2648">Pole informacji 2: właściciel urządzenia.</span><span class="sxs-lookup"><span data-stu-id="949aa-2648">Info Field 2: Device owner.</span></span>
- <span data-ttu-id="949aa-2649">Pole informacji 3: indeks portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2649">Info Field 3: Port index.</span></span>
- <span data-ttu-id="949aa-2650">Pole informacji 4: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2650">Info Field 4: Device.</span></span>

### <a name="host-stack-new-endpoint-create"></a><span data-ttu-id="949aa-2651">Tworzenie nowego punktu końcowego stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2651">Host Stack New Endpoint Create</span></span> 

#### <a name="ux_host_stack_new_endpoint_create"></a><span data-ttu-id="949aa-2652">ux_host_stack_new_endpoint_create</span><span class="sxs-lookup"><span data-stu-id="949aa-2652">ux_host_stack_new_endpoint_create</span></span>

<span data-ttu-id="949aa-2653">**Ikona** ![ Ikona tworzenia nowego punktu końcowego stosu hosta](./media/user-guide/usbx-events/image212.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2653">**Icon** ![Host Stack New Endpoint Create icon](./media/user-guide/usbx-events/image212.png)</span></span>

<span data-ttu-id="949aa-2654">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2654">**Description**</span></span>
 
<span data-ttu-id="949aa-2655">To zdarzenie reprezentuje zdarzenie tworzenia nowego punktu końcowego przez stos hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2655">This event represents a USBX Host Stack New Endpoint Create Event.</span></span>

<span data-ttu-id="949aa-2656">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2656">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2657">Pole informacji 1: interfejs.</span><span class="sxs-lookup"><span data-stu-id="949aa-2657">Info Field 1: Interface.</span></span>
- <span data-ttu-id="949aa-2658">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2658">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-2659">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2659">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2660">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2660">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-change-process"></a><span data-ttu-id="949aa-2661">Proces zmiany głównego koncentratora stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2661">Host Stack Root Hub Change Process</span></span> 

#### <a name="ux_host_stack_rh_change_process"></a><span data-ttu-id="949aa-2662">ux_host_stack_rh_change_process</span><span class="sxs-lookup"><span data-stu-id="949aa-2662">ux_host_stack_rh_change_process</span></span>

<span data-ttu-id="949aa-2663">**Ikona** ![ Ikona procesu zmiany głównego centrum w stosie hosta](./media/user-guide/usbx-events/image213.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2663">**Icon** ![Host Stack Root Hub Change Process icon](./media/user-guide/usbx-events/image213.png)</span></span>

<span data-ttu-id="949aa-2664">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2664">**Description**</span></span>
 
<span data-ttu-id="949aa-2665">To zdarzenie reprezentuje proces zmiany głównego centrum USBX stosu hosta.</span><span class="sxs-lookup"><span data-stu-id="949aa-2665">This event represents a USBX Host Stack Root Hub Change Process.</span></span>

<span data-ttu-id="949aa-2666">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2666">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2667">Pole informacji 1: indeks portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2667">Info Field 1: Port index.</span></span>
- <span data-ttu-id="949aa-2668">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2668">Info Field 2: Not used.</span></span>
- <span data-ttu-id="949aa-2669">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2669">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2670">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2670">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-extraction"></a><span data-ttu-id="949aa-2671">Wyodrębnianie urządzenia głównego koncentratora stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2671">Host Stack Root Hub Device Extraction</span></span> 

#### <a name="ux_host_stack_rh_device_extraction"></a><span data-ttu-id="949aa-2672">ux_host_stack_rh_device_extraction</span><span class="sxs-lookup"><span data-stu-id="949aa-2672">ux_host_stack_rh_device_extraction</span></span>

<span data-ttu-id="949aa-2673">**Ikona** ![ Ikona wyodrębniania urządzenia głównego koncentratora stosu hosta](./media/user-guide/usbx-events/image214.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2673">**Icon** ![Host Stack Root Hub Device Extraction icon](./media/user-guide/usbx-events/image214.png)</span></span>

<span data-ttu-id="949aa-2674">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2674">**Description**</span></span>

<span data-ttu-id="949aa-2675">To zdarzenie przedstawia zdarzenie wyodrębniania głównego urządzenia piasty stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2675">This event represents a USBX Host Stack Root Hub Device Extraction Event.</span></span>

<span data-ttu-id="949aa-2676">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2676">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2677">Pole informacji 1: HCD.</span><span class="sxs-lookup"><span data-stu-id="949aa-2677">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="949aa-2678">Pole informacji 2: indeks portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2678">Info Field 2: Port index.</span></span>
- <span data-ttu-id="949aa-2679">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2679">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2680">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2680">Info Field 4: Not used.</span></span>

### <a name="host-stack-root-hub-device-insertion"></a><span data-ttu-id="949aa-2681">Wstawianie urządzenia głównego koncentratora stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2681">Host Stack Root Hub Device Insertion</span></span> 

#### <a name="ux_host_stack_rh_device_insertion"></a><span data-ttu-id="949aa-2682">ux_host_stack_rh_device_insertion</span><span class="sxs-lookup"><span data-stu-id="949aa-2682">ux_host_stack_rh_device_insertion</span></span>

<span data-ttu-id="949aa-2683">**Ikona** ![ Ikona wstawienia urządzenia głównego koncentratora stosu hosta](./media/user-guide/usbx-events/image215.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2683">**Icon** ![Host Stack Root Hub Device Insertion icon](./media/user-guide/usbx-events/image215.png)</span></span>

<span data-ttu-id="949aa-2684">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2684">**Description**</span></span>

<span data-ttu-id="949aa-2685">To zdarzenie reprezentuje włożenie urządzenia głównego koncentratora USBX stosu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2685">This event represents a USBX Host Stack Root Hub Device Insertion.</span></span>

<span data-ttu-id="949aa-2686">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2686">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2687">Pole informacji 1: HCD.</span><span class="sxs-lookup"><span data-stu-id="949aa-2687">Info Field 1: Hcd.</span></span>
- <span data-ttu-id="949aa-2688">Pole informacji 2: indeks portu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2688">Info Field 2: Port index.</span></span>
- <span data-ttu-id="949aa-2689">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2689">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2690">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2690">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request"></a><span data-ttu-id="949aa-2691">Żądanie transferu stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2691">Host Stack Transfer Request</span></span> 

#### <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="949aa-2692">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="949aa-2692">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="949aa-2693">**Ikona** ![ Ikona żądania transferu stosu hosta](./media/user-guide/usbx-events/image216.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2693">**Icon** ![Host Stack Transfer Request icon](./media/user-guide/usbx-events/image216.png)</span></span>

<span data-ttu-id="949aa-2694">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2694">**Description**</span></span>

<span data-ttu-id="949aa-2695">To zdarzenie reprezentuje żądanie przetransferowania stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2695">This event represents a USBX Host Stack Transfer Request.</span></span>

<span data-ttu-id="949aa-2696">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2696">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2697">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2697">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2698">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2698">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-2699">Pole informacji 3: żądanie transferu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2699">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="949aa-2700">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2700">Info Field 4: Not used.</span></span>

### <a name="host-stack-transfer-request-abort"></a><span data-ttu-id="949aa-2701">Przerwano żądanie transferu stosu hosta</span><span class="sxs-lookup"><span data-stu-id="949aa-2701">Host Stack Transfer Request Abort</span></span> 

#### <a name="internal-io-driver-get-status"></a><span data-ttu-id="949aa-2702">Stan wewnętrznego pobierania sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="949aa-2702">Internal I/O driver get status</span></span>

<span data-ttu-id="949aa-2703">**Ikona** ![ Ikona przerwania żądania transferu stosu hosta](./media/user-guide/usbx-events/image217.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2703">**Icon** ![Host Stack Transfer Request Abort icon](./media/user-guide/usbx-events/image217.png)</span></span>

<span data-ttu-id="949aa-2704">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2704">**Description**</span></span>

<span data-ttu-id="949aa-2705">To zdarzenie przedstawia przerwanie żądania transferu stosu hosta USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2705">This event represents a USBX Host Stack Transfer Request Abort.</span></span>

<span data-ttu-id="949aa-2706">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2706">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2707">Pole informacji 1: urządzenie.</span><span class="sxs-lookup"><span data-stu-id="949aa-2707">Info Field 1: Device.</span></span>
- <span data-ttu-id="949aa-2708">Pole informacji 2: punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="949aa-2708">Info Field 2: Endpoint.</span></span>
- <span data-ttu-id="949aa-2709">Pole informacji 3: żądanie transferu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2709">Info Field 3: Transfer request.</span></span>
- <span data-ttu-id="949aa-2710">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2710">Info Field 4: Not used.</span></span>

### <a name="usbx-error"></a><span data-ttu-id="949aa-2711">Błąd USBX</span><span class="sxs-lookup"><span data-stu-id="949aa-2711">USBX Error</span></span> 

#### <a name="ux_error"></a><span data-ttu-id="949aa-2712">ux_error</span><span class="sxs-lookup"><span data-stu-id="949aa-2712">ux_error</span></span>

<span data-ttu-id="949aa-2713">**Ikona** ![ Ikona błędu U S B X](./media/user-guide/usbx-events/image218.png)</span><span class="sxs-lookup"><span data-stu-id="949aa-2713">**Icon** ![U S B X Error icon](./media/user-guide/usbx-events/image218.png)</span></span>

<span data-ttu-id="949aa-2714">**Opis**</span><span class="sxs-lookup"><span data-stu-id="949aa-2714">**Description**</span></span>

<span data-ttu-id="949aa-2715">To zdarzenie reprezentuje zdarzenie błędu USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2715">This event represents a USBX Error Event.</span></span>

<span data-ttu-id="949aa-2716">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="949aa-2716">**Information Fields**</span></span>

- <span data-ttu-id="949aa-2717">Pole informacji 1: błąd USBX.</span><span class="sxs-lookup"><span data-stu-id="949aa-2717">Info Field 1: USBX error.</span></span>
- <span data-ttu-id="949aa-2718">Pole informacji 2: Nazwa błędu.</span><span class="sxs-lookup"><span data-stu-id="949aa-2718">Info Field 2: Error Name.</span></span>
- <span data-ttu-id="949aa-2719">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="949aa-2719">Info Field 3: Not used.</span></span>
- <span data-ttu-id="949aa-2720">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="949aa-2720">Info Field 4: Not used.</span></span>