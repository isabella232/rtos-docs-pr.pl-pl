---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX BSD
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika usługi Azure RTO NetX BSD.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7539565ccd4956c5354be45000efab8318dc606c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822747"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-bsd"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO NetX BSD

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem składnika usługi Azure RTO NetX BSD.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO NetX BSD można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji [https://github.com/azure-rtos/netx/](https://github.com/azure-rtos/netx/) . Pakiet zawiera dwa pliki źródłowe i plik PDF, który zawiera ten dokument, w następujący sposób:

- **nx_bsd. h**: plik nagłówkowy dla NetX BSD
- plik źródłowy **nx_bsd. c**: c dla NetX BSD
- **nx_bsd.pdf**: Podręcznik użytkownika dotyczący NetX BSD

Pliki demonstracyjne:
- **bsd_demo_tcp. c**
- **bsd_demo_udp. c**

## <a name="netx-bsd-installation"></a>NetX instalacji BSD

Aby można było korzystać z NetX BSD, cała wspomniana wcześniej dystrybucja powinna zostać skopiowana do tego samego katalogu, w którym zainstalowano NetX. Na przykład jeśli NetX jest zainstalowana w katalogu "*\threadx\arm7\green*", wówczas pliki *nx_bsd. h* i *nx_bsd. c* powinny zostać skopiowane do tego katalogu.

## <a name="building-the-threadx-and-netx-components-of-a-bsd-application"></a>Kompilowanie składników ThreadX i NetX aplikacji BSD

### <a name="threadx"></a>ThreadX

Biblioteka ThreadX musi definiować *bsd_errno* w lokalnym magazynie wątków. Zalecamy wykonanie następującej procedury:

1. W *tx_port. h* Ustaw jeden z TX_THREAD_EXTENSION makr w następujący sposób:

  ```c
  #define TX_THREAD_EXTENSION_3     int bsd_errno
  ```

2. Skompiluj ponownie bibliotekę ThreadX.

> [!NOTE]
> Jeśli TX_THREAD_EXTENSION_3 jest już używany, użytkownik może korzystać z jednego z innych TX_THREAD_EXTENSION makr.

### <a name="netx"></a>NetX

Przed rozpoczęciem korzystania z usług NetX BSD należy utworzyć bibliotekę NetX z definicją NX_ENABLE_EXTENDED_NOTIFY_SUPPORT (np. w *nx_user. h*). Domyślnie nie jest on zdefiniowany.

## <a name="using-netx-bsd"></a>Korzystanie z NetX BSD

Korzystanie z narzędzia BSD for NetX jest łatwe. W zasadzie kod aplikacji musi zawierać *nx_bsd. h* po zawiera *tx_api. h* i *nx_api. h*, aby użyć odpowiednio ThreadX i NetX. Po dołączeniu *nx_bsd. h* kod aplikacji może korzystać z usług BSD określonych w dalszej części tego przewodnika. Aplikacja musi również zawierać *nx_bsd. c* w procesie kompilacji. Ten plik musi być skompilowany w taki sam sposób, jak inne pliki aplikacji i jego formularz obiektu muszą być połączone wraz z plikami aplikacji. To wszystko, co jest wymagane do korzystania z NetX BSD.

Aby korzystać z usług NetX BSD, aplikacja musi utworzyć wystąpienie IP, pulę pakietów i zainicjować usługi BSD przez wywołanie *bsd_initialize.* Jest to zademonstrowane w sekcji "mały przykład" w dalszej części tego przewodnika. Poniżej przedstawiono prototyp:

```c
INT bsd_initialize(NX_IP *default_ip, NX_PACKET_POOL *default_pool,
                  CHAR *free_memory_ptr, ULONG bsd_thread_stack_size,
                  UINT bsd_thread_priority);
```

Ostatnie trzy parametry są używane do tworzenia wątku do wykonywania zadań okresowych, takich jak sprawdzanie zdarzeń TCP i Definiowanie przestrzeni stosu wątków.

> [!NOTE]
> W przeciwieństwie do gniazd BSD, które działają w kolejności bye w sieci, NetX działa w kolejności bajtów hosta procesora hosta. Ze względu na zgodność ze źródłami makra htons (), ntohs (), htonl (), ntohl () zostały zdefiniowane, ale nie modyfikują podanego argumentu.

## <a name="netx-bsd-limitations"></a>Ograniczenia NetX BSD

Ze względu na problemy z wydajnością i architekturą NetX BSD nie obsługuje wszystkich funkcji gniazda BSD 4,3:

Flagi INT nie są obsługiwane dla wywołań *send, recv, SendTo* i *recvfrom* .

## <a name="netx-bsd-with-dns-support"></a>NetX BSD z obsługą systemu DNS

Jeśli NX_BSD_ENABLE_DNS jest zdefiniowany, NetX BSD może wysyłać zapytania DNS w celu uzyskania informacji o nazwie hosta lub adresie IP hosta. Ta funkcja wymaga, aby klient NetX DNS był wcześniej tworzony przy użyciu usługi *nx_dns_create* . Co najmniej jeden znany adres IP serwera DNS musi być zarejestrowany w wystąpieniu usługi DNS przy użyciu *nx_dns_server_add* do dodawania adresów serwerów.

Usługi systemu DNS i alokacja pamięci są używane przez usługi *Getaddrinfo* i *getnameinfo* :

```c
INT getaddrinfo(const CHAR *node, const CHAR *service,
              const struct addrinfo *hints, struct addrinfo **res)

INT getnameinfo(const struct sockaddr *sa, socklen_t salen,
              char *host, size_t hostlen, char *serv, size_t servlen, int flags)
```

Gdy aplikacja BSD wywołuje *Getaddrinfo* z nazwą hosta, NetX BSD wywoła następujące usługi, aby uzyskać adres IP:

- nx_dns_ipv4_address_by_name_get
- nx_dns_cname_get

W przypadku *nx_dns_ipv4_address_by_name_get* NetX BSD używa obszarów pamięci ipv4_addr_buffer. Rozmiar tych buforów jest definiowany przez ( `NX_BSD_IPV4_ADDR_PER_HOST * 4` ).

W przypadku zwracania informacji o adresie z *Getaddrinfo*, NetX BSD używa tabeli pamięci blokowej ThreadX *nx_bsd_addrinfo_pool_memory*, której obszar pamięci jest zdefiniowany przez inny zestaw konfigurowalnych opcji, *NX_BSD_IPV4_ADDR_MAX_NUM*.

Zobacz **Opcje konfiguracji** , aby uzyskać szczegółowe informacje na temat powyższych opcji konfiguracji.

Ponadto jeśli NX_DNS_ENABLE_EXTENDED_RR_TYPES jest zdefiniowana, a dane wejściowe hosta są nazwą kanoniczną, NetX BSD przydzieli pamięć dynamicznie z wcześniej utworzonej puli bloków *_nx_bsd_cname_block_pool*

> [!NOTE]
> Po wywołaniu *Getaddrinfo* aplikacja BSD jest odpowiedzialna za zwolnienie pamięci wskazywanej przez argument res z powrotem do tabeli blokowej przy użyciu usługi *freeaddrinfo* .

## <a name="configuration-options"></a>Opcje konfiguracji

Opcje konfigurowalne przez użytkownika w *nx_bsd. h* pozwalają aplikacji dostroić NetX BSD do określonych wymagań. Poniżej znajduje się lista tych parametrów:

- **NX_BSD_TCP_WINDOW**: używany w wywołaniach tworzenia gniazda TCP. 65535 to typowy rozmiar okna dla 100 MB sieci Ethernet. Wartość domyślna to 65535.
- **NX_BSD_SOCKFD_START** Jest to logiczny indeks wartości początkowej deskryptora pliku gniazda BSD. Domyślnie ta opcja to 32.
- **NX_BSD_MAX_SOCKETS** Określa maksymalną liczbę gniazd dostępnych w warstwie BSD i musi być wielokrotnością 32. wartość domyślna to 32.
- **NX_BSD_SOCKET_QUEUE_MAX** Określa maksymalną liczbę pakietów UDP przechowywanych w kolejce odbierania. Wartość jest domyślnie równa 5.
- **NX_BSD_MAX_LISTEN_BACKLOG** Określa rozmiar kolejki nasłuchu ("zaległości") dla gniazd TCP BSD. Wartość domyślna to 5.
- **NX_MICROSECOND_PER_CPU_TICK** Określa liczbę mikrosekund na przerwanie czasomierza
- **NX_BSD_TIMEOUT** Określa limit czasu w taktach czasomierza na wywołaniach wewnętrznych NetX wymaganych przez BSD. Wartość domyślna to 20 * NX_IP_PERIODIC_RATE.
- **NX_BSD_TCP_SOCKET_DISCONNECT_TIMEOUT**: określa limit czasu w taktach czasomierza w wywołaniu NetX Disconnect. Wartość domyślna to 1.
- **NX_BSD_PRINT_ERRORS** Jeśli ta wartość jest ustawiona, zwracany stan błędu funkcji BSD zwraca numer wiersza i typ błędu, np. NX_SOC_ERROR gdzie wystąpi błąd. Wymaga to od deweloperów aplikacji zdefiniowania danych wyjściowych debugowania. Ustawienie domyślne jest wyłączone i nie określono danych wyjściowych debugowania w *nx_bsd. h*
- **NX_BSD_TIMER_RATE** Interwał, po którym uruchamiane jest zadanie okresowego czasomierza BSD. Wartość domyślna to 1 sekunda (1 * NX_IP_PERIODIC_RATE).
- **NX_BSD_TIMEOUT_PROCESS_IN_TIMER** W przypadku ustawienia ta opcja umożliwia wykonanie procesu limitu czasu BSD w kontekście czasomierza systemu. Zachowanie domyślne jest wyłączone. Ta funkcja została szczegółowo opisana w rozdziale 2 "Instalacja i korzystanie z NetX BSD".
- **NX_BSD_ENABLE_DNS** Jeśli ta funkcja jest włączona, NetX BSD wyśle zapytanie DNS dla nazwy hosta lub adresu IP hosta. Wymaga wcześniejszego utworzenia i uruchomienia wystąpienia klienta DNS. Domyślnie nie jest włączona.
- **NX_BSD_IPV4_ADDR_MAX_NUM** Maksymalna liczba adresów IPv4 zwróconych przez *Getaddrinfo*. Dzięki NX_BSD_IPV4_ADDR_MAX_NUM definiuje rozmiar puli bloku NetX BSD nx_bsd_addrinfo_block_pool do dynamicznego przydzielania pamięci do przechowywania informacji w *Getaddrinfo*. Wartość domyślna to 5.
- **NX_BSD_IPV4_ADDR_PER_HOST**: określa maksymalną liczbę adresów IPv4 przechowywanych dla kwerendy DNS. Wartość domyślna to 5.

## <a name="bsd-socket-options"></a>Opcje gniazda BSD

Poniższa lista opcji NetX w gnieździe BSD można włączyć (lub wyłączyć) w czasie wykonywania dla poszczególnych gniazd przy użyciu usługi *SetSockOpt* :

```c
INT setsockopt(INT sockID, INT option_level, INT option_name, const
                void *option_value, INT option_length);
```

Istnieją dwa różne ustawienia dla *option_level*.

Pierwszy typ opcji gniazda czasu wykonywania jest SOL_SOCKET dla opcji poziomu gniazda. Aby włączyć opcję poziomu gniazda, należy wywołać *setsockopt* option_level z ustawionym na SOL_SOCKET, a option_name ustawić dla konkretnej opcji, np. SO_BROADCAST. Aby pobrać ustawienie opcji, wywołaj *getsockopt* dla option_name z option_level ponownie ustawiona na SOL_SOCKET.

Zostanie wyświetlona lista opcji poziomu gniazda w czasie wykonywania poniżej.

- **SO_BROADCAST**: ustawienie umożliwia wysyłanie i otrzymywanie pakietów emisji z gniazd NetX. Jest to domyślne zachowanie dla NetX. Wszystkie gniazda mają tę możliwość.
- **SO_ERROR**: służy do uzyskiwania stanu gniazda dla operacji poprzedniej gniazda określonego gniazda przy użyciu usługi *getsockopt* . Wszystkie gniazda mają tę możliwość.
- **SO_KEEPALIVE**: ustawienie powoduje włączenie funkcji utrzymywania aktywności protokołu TCP. Wymaga to, aby Biblioteka NetX była skompilowana przy użyciu NX_TCP_ENABLE_KEEPALIVE zdefiniowanej w *nx_user. h*. Domyślnie ta funkcja jest wyłączona.
- **SO_RCVTIMEO**: to ustawienie opcji oczekiwania (w sekundach) dla pakietów odbieranych w NetX BSD. Wartość domyślna to NX_WAIT_FOREVER (0xFFFFFFFF) lub, jeśli jest włączony bez blokowania, NX_NO_WAIT (0x0).
- **SO_RCVBUF**: Określa rozmiar okna gniazda TCP. Wartość domyślna NX_BSD_TCP_WINDOW jest ustawiona na 64 KB w przypadku pakietów BSD TCP Sockets. Aby ustawić rozmiar ponad 65535, należy utworzyć bibliotekę NetX z zdefiniowanym NX_TCP_ENABLE_WINDOW_SCALING.
- **SO_REUSEADDR**: ustawienie umożliwia zmapowanie wielu gniazd na jeden port. Typowy sposób użycia dotyczy gniazda serwera TCP. Jest to domyślne zachowanie NetX Sockets.

Drugim typem opcji gniazda czasu wykonywania jest poziom opcji IP. Aby włączyć opcję poziomu IP, należy wywołać *setsockopt* option_level z ustawionym na IP_PROTO, a option_name ustawić opcję na np. IP_MULTICAST_TTL. Aby pobrać ustawienie opcji, wywołaj *getsockopt* dla option_name z option_level ponownie ustawiona na IP_PROTO.

Zostanie wyświetlona lista opcji poziomu adresu IP czasu wykonywania poniżej.

- **IP_MULTICAST_TTL**: służy do ustawiania czasu wygaśnięcia dla gniazd UDP. Wartość domyślna to NX_IP_TIME_TO_LIVE (0x80) podczas tworzenia gniazda. Tę wartość można zastąpić, wywołując *SetSockOpt* z tą opcją gniazda.
- **IP_ADD_MEMBERSHIP**: Jeśli ta opcja jest ustawiona, w celu przyłączenia do określonej grupy IGMP gniazdo BSD (dotyczy tylko gniazd UDP).
- **IP_DROP_MEMBERSHIP**: w przypadku ustawienia, ta opcja włącza gniazdo BSD (dotyczy tylko gniazd UDP), aby opuścić określoną grupę IGMP.

## <a name="small-example-system"></a>Mały przykładowy system

Przykład użycia NetX BSD przedstawiono na rysunku 1,0 poniżej. W tym przykładzie plik dołączany *nx_bsd. h* jest wprowadzany w wierszu 7. Następnie *bsd_pool* *bsd_ip* wystąpienia adresu IP i puli pakietów są tworzone jako zmienne globalne w wierszu 20 i 21. Należy zauważyć, że w tej wersji demonstracyjnej jest stosowany sterownik sieciowy pamięci RAM (linia 41). Klient i serwer będą współużytkować ten sam adres IP na pojedynczym wystąpieniu IP w tym przykładzie.

Wątki klienta i serwera są tworzone w wierszach 303 i 309 w *tx_application_define* , które konfigurują aplikację i są zdefiniowane w wierszach 293-361. Po pomyślnym utworzeniu wystąpienia adresu IP w wierszu 327 wystąpienie protokołu IP jest włączone dla usług TCP w wierszu 350. Ostatnim wymaganiem przed użyciem usług BSD jest wywołanie *bsd_initialize* w wierszu 360 w celu skonfigurowania wszystkich struktur danych i NetX oraz zasobów ThreadX wymaganych przez BSD.

W funkcji wprowadzania wątku serwera *thread_1_entry,* która jest zdefiniowana w wierszach 381-397, aplikacja oczekuje na zainicjowanie przez sterownik NetX z parametrami sieci. Gdy to zrobisz, wywoła *tcpServer* zdefiniowane w wierszach 146-253, aby obsłużyć szczegółowe informacje dotyczące konfigurowania gniazda serwera TCP.

*tcpServer* tworzy gniazdo główne przez wywołanie usługi *socket* w wierszu 159 i wiąże ją z gniazdem nasłuchiwania przy użyciu wywołania *bind* w wierszu 176. Następnie jest skonfigurowany do nasłuchiwania żądań połączeń w wierszu 191. Należy zauważyć, że gniazdo główne nie akceptuje żądania połączenia. Działa w pętli ciągłej, *która wywołuje się* za każdym razem, aby wykryć żądania połączenia. Dodatkowe gniazdo BSD wybrane z tablicy usługi BSD Sockets jest przypisane do żądania połączenia po wywołaniu usługi *Accept* w wierszu 218.

Po stronie klienta funkcja wprowadzania wątku klienta *thread_0_entry* zdefiniowana w wierszach 366-377 powinna również oczekiwać na zainicjowanie NetX przez sterownik. W tym miejscu po prostu poczekamy na wykonanie tej czynności po stronie serwera. Następnie wywołuje *tcpClient* zdefiniowane w wierszu 54-142, aby obsłużyć szczegółowe informacje dotyczące konfigurowania gniazda klienta TCP i żądania połączenia TCP.

Gniazdo klienta TCP jest tworzone w wierszu 68. Gniazdo jest powiązane z określonym adresem IP i próbuje połączyć się z serwerem TCP przez wywołanie metody *Connect* on line 84. Teraz można zacząć wysyłać i odbierać pakiety.

```c
1 /*  This is a small demo of BSD Wrapper for the high-performance NetX TCP/IP stack.
2     This demo demonstrate TCP connection, disconnection, sending, and receiving using
3     ARP and a simulated Ethernet driver. */
4
5 #include     "tx_api.h"
6 #include     "nx_api.h"
7 #include     "nx_bsd.h"
8 #include     <string.h>
9 #include     <stdlib.h>
10
11 #define         DEMO_STACK_SIZE         (16*1024)
12
13
14 /* Define the ThreadX and NetX object control blocks... */
15
16 TX_THREAD       thread_0;
17 TX_THREAD       thread_1;
18
19
20 NX_PACKET_POOL  bsd_pool;
21 NX_IP           bsd_ip;
22
23
24 /* Define the counters used in the demo application... */
25
26 ULONG           error_counter;
27
28 /* Define fd_set for select call */
29 fd_set          master_list,read_ready,read_ready1;
30
31
32 /* Define thread prototypes. */
33
34 VOID            thread_0_entry(ULONG thread_input);
35 VOID            thread_1_entry(ULONG thread_input);
36
37 VOID            tcpClient(CHAR *msg0);
38 VOID            tcpServer(VOID);
39 INT             HandleClient(INT sock);
40
41 VOID            _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
42
43
44 /* Define main entry point. */
45
46 int main()
47 {
48
49     /* Enter the ThreadX kernel. */
50     tx_kernel_enter();
51 }
52
53
54 VOID tcpClient(CHAR *msg0)
55 {
56
57 INT     status,status1,send_counter;
58 INT     sock_tcp_1,length,length1;
59 struct  sockaddr_in echoServAddr;       /* Echo server address */
60 struct  sockaddr_in localAddr;          /* Local address */
61 struct  sockaddr_in remoteAddr;         /* Remote address */
62
63 UINT    echoServPort; /* Echo Server Port */
64 CHAR    rcvBuffer1[32]
65
66
67     /* Create BSD TCP Socket */
68     sock_tcp_1 = **socket**( PF_INET, SOCK_STREAM, IPPROTO_TCP);
69     if (sock_tcp_1 == -1)
70     {
71         printf("\nError: BSD TCP Client socket create \n");
72         return;
73     }
74
75     printf("\nBSD TCP Client socket created %lu \n", sock_tcp_1);
76     /* Fill destination port and IP address */
77     echoServPort = 12;
78     memset(&echoServAddr, 0, sizeof(echoServAddr));
79     echoServAddr.sin_family = PF_INET;
80     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
81     echoServAddr.sin_port = echoServPort;
82
83     /* Now connect this client the server */
84     status1 = connect(sock_tcp_1, (struct sockaddr *)&echoServAddr, sizeof(echoServAddr));
85     /* Check for error. */
86     if (status1 != OK)
87     {
88         printf("\nError: BSD TCP Client socket Connect, %d \n",sock_tcp_1);
89         status = soc_close(sock_tcp_1);
90         if (status != ERROR)
91             printf("\nConnect ERROR so BSD Client Socket Closed: %d\n",sock_tcp_1);
92         else
93             printf("\nError: BSD Client Socket close %d\n",sock_tcp_1);
94         return;
95     }
96     /* Get and print source and destination information */
97     printf("\nBSD TCP Client socket: %d connected \n", sock_tcp_1);
98
99     status = getsockname(sock_tcp_1, (struct sockaddr *)&localAddr, &length);
100    printf("Client port = %lu , Client = %lu,", 
            localAddr.sin_port, localAddr.sin_addr.s_addr);
101    status = getpeername( sock_tcp_1, (struct sockaddr *) &remoteAddr, &length1);
102    printf("Remote port = %lu, Remote IP = %lu \n", 
            remoteAddr.sin_port remoteAddr.sin_addr.s_addr);
103
104    send_counter = 1;
105
106    /* Now receive the echoed packet from the server */
107    while(1)
108    {
109        tx_thread_sleep(2);
110
111        printf("\nClient sock: %d Sending packet No: %d to
                server\n",sock_tcp_1,send_counter);
112        status = send(sock_tcp_1,msg0, sizeof(msg0), 0);
113        if (status == ERROR)
114            printf("Error: BSD Client Socket send %d\n",sock_tcp_1);
115        else
116        {
117            printf("\nMessage sent: %s\n",msg0);
118            send_counter++;
119        }
120
121        status = recv(sock_tcp_1, (VOID *)rcvBuffer1, 31,0);
122        if (status == 0)
123            break;
124
125        rcvBuffer1[status] = 0;
126
127        if (status != ERROR)
128            printf("\nBSD Client Socket: %d received %lu bytes: %s ", 
                        sock_tcp_1,(ULONG)status,rcvBuffer1);
129        else
130            printf("\nError: BSD Client Socket receive %d \n",sock_tcp_1);
131
132    }
133
134    /* close this client socket */
135    status = soc_close(sock_tcp_1);
136    if (status != ERROR)
137        printf("\nBSD Client Socket Closed %d\n",sock_tcp_1);
138    else
139        printf("\nError: BSD Client Socket close %d \n",sock_tcp_1);
140
141    /* End */
142 }
143
144
145
146 void tcpServer(void)
147 {
148
149 INT         status,status1,sock,sock_tcp_2,i;
150 struct      sockaddr_in echoServAddr; /* Echo server address */
151 struct      sockaddr_in ClientAddr;
152
153 INT         Clientlen;
154 UINT        echoServPort; /* Echo Server Port */
155
156 INT         maxfd;
157
158 /* Create BSD TCP Server Socket */
159     sock_tcp_2 = socket( PF_INET, SOCK_STREAM, IPPROTO_TCP);
160     if (sock_tcp_2 == -1)
161     {
162         printf("Error: BSD TCP Server socket create\n");
163         return;
164     }
165     else
166         printf("BSD TCP Server socket created \n");
167
168     /* Now fill server side information */
169     echoServPort = 12;
170     memset(&echoServAddr, 0, sizeof(echoServAddr));
171     echoServAddr.sin_family = PF_INET;
172     echoServAddr.sin_addr.s_addr = htonl(0x01020304);
173     echoServAddr.sin_port = echoServPort;
174
175     /* Bind this server socket */
176         status = bind(sock_tcp_2, (struct sockaddr *) &echoServAddr, sizeof(echoServAddr));
177     if (status < 0)
178     {
179         printf("Error: BSD TCP Server Socket Bind \n");
180         return;
181     }
182     else
183         printf("BSD TCP Server Socket bound \n");
184
185     FD_ZERO(&master_list);
186     FD_ZERO(&read_ready);
187     FD_SET(sock_tcp_2,&master_list);
188     maxfd = sock_tcp_2;
189
190     /* Now listen for any client connections for this server socket */
191     status = listen(sock_tcp_2,5);
192     if (status < 0)
193     {
194         printf("Error: BSD TCP Server Socket Listen\n");
195         return;
196     }
197     else
198         printf("BSD TCP Server Socket Listen complete, ");
199
200     /* All set to accept client connections */
201     printf("Now accepting client connections\n");
202
203     /* Loop to create and establish server connections. */
204     while(1)
205     {
206
207         read_ready = master_list;
208         tx_thread_sleep(2); /* Allow some time to other threads too */
209         status = select(maxfd+1,&read_ready,0,0,0);
210         if (status == ERROR)
211         {
212             continue;
213         }
214
215         status = FD_ISSET(sock_tcp_2,&read_ready);
216         if(status)
217         {
218             sock = accept(sock_tcp_2,(struct sockaddr*)&ClientAddr, &Clientlen);
219
220             /* Add this new connection to our master list */
221             FD_SET(sock,&master_list);
222             if ( sock \maxfd)
223             {
224                 maxfd = sock;
225             }
226
227             continue;
228         }
229         for (i = 0; i < (maxfd+1); i++)
230         {
231             if (( i != sock_tcp_2) && (FD_ISSET(i,&master_list)) && 
                    (FD_ISSET(i,&read_ready)))
232             {
233                 status1 = HandleClient(i);
234                 if (status1 == 0)
235                 {
236                     status1 = soc_close(i);
237                     if (status1 == OK)
238                     {
239                         FD_CLR(i,&master_list);
240                         printf("\nBSD Server Socket:%d closed\n",i);
241                     }
242                     else
243                         printf("\nError:BSD Server Socket:%d close\n",i);
244                 }
245
246             }
247         }
248
249         /* Loop back to check any next client connection */
250
251     } /* While(1) ends */
252
253 }
254
255 CHAR     rcvBuffer[128];
256
257 INT     HandleClient(INT sock)
258 {
259
260 INT     status;
261
262
263     status = recv(sock, (VOID *)rcvBuffer, 128,0);
264     if (status == ERROR )
265     {
266         printf("\n BSD Server Socket:%d receive \n",sock);
267         return(ERROR);
268     }
269
270     /* a zero return from a recv() call indicates client is terminated! */
271     if (status == 0)
272     {
273         /* Done with this client , close this secondary server socket */
274         return(status);
275     }
276
277     /* print data received from the client */
278     printf("\nBSD Server Socket:%d received %lu bytes: %s \n", sock, (ULONG)status,rcvBuffer);
279
280     /* And echo the same data to the client */
281     status = send(sock,rcvBuffer, status + 1, 0);
282     if (status == ERROR )
283     {
284         printf("\nError: BSD Server Socket:%d send \n",sock);
285         return(ERROR);
286     }
287     return(status);
288 }
289
290
291 /* Define what the initial system looks like. */
292
293 void     tx_application_define(void *first_unused_memory)
294 {
295
296 CHAR     *pointer;
297 UINT     status;
298
299     /* Setup the working pointer. */
300     pointer = (CHAR *) first_unused_memory;
301
302     /* Create a client thread. */
303     tx_thread_create(&thread_0, "Client1", thread_0_entry, 0,
304         pointer, DEMO_STACK_SIZE, 2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
305
306     pointer = pointer + DEMO_STACK_SIZE;
307
308     /* Create a server thread. */
309     tx_thread_create(&thread_1, "Server", thread_1_entry, 0,
310         pointer, DEMO_STACK_SIZE,1,1, TX_NO_TIME_SLICE, TX_AUTO_START);
311
312     pointer = pointer + DEMO_STACK_SIZE;
313
314     /* Initialize the NetX system. */
315     nx_system_initialize();
316
317     /* Create a BSD packet pool. */
318     status = nx_packet_pool_create(&bsd_pool,"NetX BSD Packet Pool", 128
                                        pointer, 16384);
319     pointer = pointer + 16384;
320     if (status)
321     {
322         error_counter++;
323         printf("Error in creating BSD packet pool\n!");
324     }
325
326     /* Create an IP instance for BSD. */
327     status = nx_ip_create(&bsd_ip, "NetX IP Instance 2", IP_ADDRESS(1, 2, 3, 4),
                              0xFFFFFF00UL, &bsd_pool, _nx_ram_network_driver,
                              pointer, 2048, 1);
328
329     pointer = pointer + 2048;
330
331     if (status)
332     {
333         error_counter++;
334         printf("Error creating BSD IP instance\n!");
335     }
336
337     /* Enable ARP and supply ARP cache memory for BSD IP Instance */
338     status = nx_arp_enable(&bsd_ip, (void *) pointer, 1024);
339     pointer = pointer + 1024;
340
341     /* Check ARP enable status. */
342     if (status)
343     {
344         error_counter++;
345         printf("Error in Enable ARP and supply ARP cache memory to BSD IP instance\n");
346     }
347
348     /* Enable TCP processing for BSD IP instances. */
349
350     status = nx_tcp_enable(&bsd_ip);
351
352     /* Check TCP enable status. */
353     if (status)
354     {
355         error_counter++;
356         printf("Error in Enable TCP \n");
357     }
358
359     /* Now initialize BSD Scoket Wrapper */
360     status = bsd_initialize(&bsd_ip, &bsd_pool,pointer, 2048, 1);
361 }
362
363
364 /* Define the test threads. */
365
366 void     thread_0_entry)ULONG thread_input)
367 {
368
369 CHAR     *msg0 = "Client 1:
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>ABCDEFGHIJKLMNOPQRSTUVWXYZ<> \
                     "ABCDEFGHIJKLMNOPQRSTUVWXYZ<>END";
370
371     /* Wait till Server side is all set */
372     tx_thread_sleep(2);
373     while (1)
374     {
375         tcpClient(msg0);
376         tx_thread_sleep(1);
377     }
378 }
379
380 /* Define the server thread entry function. */
381 void     thread_1_entry(ULONG thread_input)
382 {
383
384 UINT     status;
385 ULONG    actual_status;
386
387 /* Ensure the IP instance has been initialized. */
388 status = nx_ip_status_check(&bsd_ip, NX_IP_INITIALIZE_DONE, &actual_status, 100);
389
390 /* Check status... */
391 if (status != NX_SUCCESS)
392 {
393     error_counter++;
394     return;
395 }
396 /* Start a TCP Server */
397 tcpServer();
398 }
399
```
