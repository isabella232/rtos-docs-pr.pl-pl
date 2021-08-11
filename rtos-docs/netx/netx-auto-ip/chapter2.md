---
title: Rozdział 2 — Instalowanie i używanie aplikacji Azure RTOS NetX AutoIP
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS NetX AutoIP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9bc5ce189980dbceaf12a2f2e8429d9267e7d37f559c88d10c54e399d01ec259
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796892"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-autoip"></a>Rozdział 2 — Instalowanie i używanie aplikacji Azure RTOS NetX AutoIP

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem Azure RTOS NetX AutoIP.

## <a name="product-distribution"></a>Dystrybucja produktów

Funkcja AutoIP dla NetX jest dostępna na stronie [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) . Pakiet zawiera trzy pliki źródłowe, jeden plik dołączany i plik PDF zawierający ten dokument w następujący sposób:

- **nx_auto_ip.h:** Plik nagłówka dla funkcji NetX AutoIP
- **nx_auto_ip.c:** plik źródłowy języka C dla funkcji NetX AutoIP
- **demo_netx_auto_ip.c:** plik źródłowy języka C dla pokazu funkcji AutoIP netX
- **nx_auto_ip.pdf:** opis PDF funkcji NetX AutoIP

## <a name="autoip-installation"></a>Instalacja funkcji AutoIP

Aby można było korzystać z funkcji NetX AutoIP, cała wymieniona wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano program NetX. Jeśli na przykład netx jest zainstalowany w katalogu *"\threadx\arm7\green",* do tego katalogu powinny zostać skopiowane pliki *nx_auto_ip.h*, *nx_auto_ip.c* i *demo_netx_auto_ip.c.*

## <a name="using-autoip"></a>Korzystanie z funkcji AutoIP

Korzystanie z funkcji NetX AutoIP jest łatwe. Zasadniczo kod aplikacji musi zawierać kod *nx_auto_ip.h* po dojecheniu plików *tx_api.h* i *nx_api.h,* aby można było używać funkcji ThreadX i NetX. Po *nx_auto_ip.h* kod aplikacji może następnie wykonać wywołania funkcji AutoIP określone w dalszej części tego przewodnika. Aplikacja musi również uwzględniać *nx_auto_ip.c* w procesie kompilacji. Te pliki muszą być kompilowane w taki sam sposób jak inne pliki aplikacji, a ich formularz obiektu musi być połączony z plikami aplikacji. To wszystko, co jest wymagane do korzystania z funkcji NetX AutoIP.

> [!NOTE]
> Ponieważ funkcja AutoIP korzysta z usług ARP NetX, należy włączyć funkcję ARP za pomocą *wywołania nx_arp_enable* przed użyciem funkcji AutoIP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład łatwego korzystania z funkcji NetX AutoIP opisano na rysunku 1.1, który znajduje się poniżej. W tym przykładzie plik dołączania autoIP *nx_auto_ip.h* jest w wierszu 002. Następnie wystąpienie funkcji NetX AutoIP jest tworzone w ciągu "*tx_application_define*" w wierszu 090. Zwróć uwagę, że blok sterowania NetX AutoIP "auto_ip_0" został wcześniej zdefiniowany jako zmienna globalna w wierszu 015. Po pomyślnym utworzeniu aplikacja NetX AutoIP zostanie uruchomiona w wierszu 098. Przetwarzanie funkcji wywołania zwrotnego zmiany adresu IP rozpoczyna się w wierszu 105, który jest używany do obsługi kolejnych konfliktów lub możliwego rozpoznawania adresów DHCP.

> [!NOTE]
> W poniższym przykładzie przyjęto założenie, że urządzenie hosta jest urządzeniem z jednym domem. W przypadku urządzenia wieloadresowego aplikacja hosta może używać zestawu nx_auto_ip_interface_ NetX AutoIP w celu określenia pomocniczego interfejsu sieciowego do sondowania adresu IP. Aby uzyskać więcej informacji na temat konfigurowania aplikacji wieloadresowych, zobacz NetX User Guide (Podręcznik użytkownika **netX).** Należy również pamiętać, że aplikacja hosta powinna używać interfejsu API NetX *nx_status_ip_interface_check,* aby sprawdzić, czy usługa AutoIP uzyskała adres IP.

## <a name="example-of-autoip-use-with-netx"></a>Przykład użycia funkcji AutoIP z netx

```c
000 #include "tx_api.h"
001 #include "nx_api.h"
002 #include "nx_auto_ip.h"
003
004 #define         DEMO_STACK_SIZE         4096
005
006 /* Define the ThreadX and NetX object control blocks... */
007
008 TX_THREAD         thread_0;
009 NX_PACKET_POOL    pool_0;
010 NX_IP             ip_0;
011
012
013 /* Define the AUTO IP structures for the IP instance. */
014
015 NX_AUTO_IP         auto_ip_0;
016
017
018 /* Define the counters used in the demo application... */
019
020 ULONG             thread_0_counter;
021 ULONG             address_changes;
022 ULONG             error_counter;
023
024
025 /* Define thread prototypes. */
026
027 void     thread_0_entry(ULONG thread_input);
028 void     ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address);
029 void     _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
030
031
032 /* Define main entry point. */
033
034 int main()
035 {
036
037     /* Enter the ThreadX kernel. */
038     tx_kernel_enter();
039 }
040
041
042 /* Define what the initial system looks like. */
043
044 void     tx_application_define(void *first_unused_memory)
045 {
046
047 CHAR     *pointer;
048 UINT     status;
049
050
051     /* Setup the working pointer. */
052     pointer = (CHAR *) first_unused_memory;
053
054     /* Create the main thread. */
055     tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
056                     pointer, DEMO_STACK_SIZE,
057                     16, 16, 1, TX_AUTO_START);
058
059     pointer = pointer + DEMO_STACK_SIZE;
060
061     /* Initialize the NetX system. */
062     nx_system_initialize();
063
064     /* Create a packet pool. */
065     status = nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 128,
066                                     pointer, 4096);
067                                     pointer = pointer + 4096;
068
069     if (status)
070         error_counter++;
071
072     /* Create an IP instance. */
073     status = nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(0, 0, 0, 0),
074                             0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
075                             pointer, 4096, 1);
076                             pointer = pointer + 4096;
077
078     if (status)
079         error_counter++;
080
081     /* Enable ARP and supply ARP cache memory for IP Instance 0. */
082     status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
083     pointer = pointer + 1024;
084
085     /* Check ARP enable status. */
086     if (status)
087         error_counter++;
088
089     /* Create the AutoIP instance for IP Instance 0. */
090     status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);
091     pointer = pointer + 4096;
092
093     /* Check AutoIP create status. */
094     if (status)
095         error_counter++;
096
097     /* Start AutoIP instances. */
098     status = nx_auto_ip_start(&auto_ip_0, 0 /*IP_ADDRESS(169,254,254,255)*/);
099
100     /* Check AutoIP start status. */
101     if (status)
102         error_counter++;
103
104     /* Register an IP address change function for IP Instance 0. */
105     status = nx_ip_address_change_notify(&ip_0, ip_address_changed,
106                                         (void *) &auto_ip_0);
107
108     /* Check IP address change notify status. */
109     if (status)
110         error_counter++;
111     }
112
113
114     /* Define the test thread. */
115
116     void thread_0_entry(ULONG thread_input)
117     {
118
119     UINT      status;
120     ULONG     actual_status;
121
122
123          /* Wait for IP address to be resolved. */
124         do
125         {
126
127             /* Call IP status check routine. */
128             status = nx_ip_status_check(&ip_0, NX_IP_ADDRESS_RESOLVED,
129                                         &actual_status, 10000);
130
131         } while (status != NX_SUCCESS);
132
133         /* Since the IP address is resolved at this point, the application
134         can now fully utilize NetX! */
135
136         while(1)
137         {
138
139
140
141             /* Increment thread 0's counter. */
142             thread_0_counter++;
143
144             /* Sleep... */
145             tx_thread_sleep(10);
146         }
147     }
148
149
150     void ip_address_changed(NX_IP *ip_ptr, VOID *auto_ip_address)
151     {
152
153     ULONG         ip_address;
154     ULONG         network_mask;
155     NX_AUTO_IP    *auto_ip_ptr;
156
157
158     /* Setup pointer to auto IP instance. */
159     auto_ip_ptr = (NX_AUTO_IP *) auto_ip_address;
160
161     /* Pickup the current IP address. */
162     nx_ip_address_get(ip_ptr, &ip_address, &network_mask);
163
164     /* Determine if the IP address has changed back to zero. If so,
165     make sure the AutoIP instance is started. */
166     if (ip_address == 0)
167     {
168
169         /* Get the last AutoIP address for this node. */
170         nx_auto_ip_get_address(auto_ip_ptr, &ip_address);
171
172         /* Start this AutoIP instance. */
173         nx_auto_ip_start(auto_ip_ptr, ip_address);
174     }
175
176     /* Determine if IP address has transitioned to a non local IP address. */
177     else if ((ip_address & 0xFFFF0000UL) != IP_ADDRESS(169, 254, 0, 0))
178     {
179
180         /* Stop the AutoIP processing. */
181         nx_auto_ip_stop(auto_ip_ptr);
182     }
183
184     /* Increment a counter. */
185     address_changes++;
186 }
```

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji tworzenia funkcji NetX AutoIP. Poniżej znajduje się lista wszystkich opcji, z których każda jest szczegółowo opisana:

- **NX_DISABLE_ERROR_CHECKING:** zdefiniowana, ta opcja usuwa podstawowe sprawdzanie błędów funkcji AutoIP. Jest on zwykle używany po debugowaniu aplikacji.
- **NX_AUTO_IP_PROBE_WAIT:** liczba sekund oczekiwania przed wysłaniem pierwszej sondy. Domyślnie ta wartość jest zdefiniowana jako 1.
- **NX_AUTO_IP_PROBE_NUM:** liczba sond ARP do wysłania. Domyślnie ta wartość jest zdefiniowana jako 3.
- **NX_AUTO_IP_PROBE_MIN:** minimalna liczba sekund oczekiwania między wysyłaniem sond. Domyślnie ta wartość jest zdefiniowana jako 1.
- **NX_AUTO_IP_PROBE_MAX:** maksymalna liczba sekund oczekiwania między wysyłaniem sond. Domyślnie ta wartość jest zdefiniowana jako 2.
- **NX_AUTO_IP_MAX_CONFLICTS:** Liczba konfliktów funkcji AutoIP przed zwiększeniem opóźnień przetwarzania. Domyślnie ta wartość jest zdefiniowana jako 10.
- **NX_AUTO_IP_RATE_LIMIT_INTERVAL:** liczba sekund do rozszerzenia okresu oczekiwania po przekroczeniu całkowitej liczby konfliktów. Domyślnie ta wartość jest zdefiniowana jako 60.
- **NX_AUTO_IP_ANNOUNCE_WAIT:** liczba sekund oczekiwania przed wysłaniem powiadomienia. Domyślnie ta wartość jest zdefiniowana jako 2.
- **NX_AUTO_IP_ANNOUNCE_NUM:** liczba wiadomości ARP do wysłania. Domyślnie ta wartość jest zdefiniowana jako 2.
- **NX_AUTO_IP_ANNOUNCE_INTERVAL:** liczba sekund oczekiwania między wysłaniem głosów. Domyślnie ta wartość jest zdefiniowana jako 2.
- **NX_AUTO_IP_DEFEND_INTERVAL:** liczba sekund oczekiwania między głosami obrony. Domyślnie ta wartość jest zdefiniowana jako 10.