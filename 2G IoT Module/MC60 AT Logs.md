# Introduction


Tested on MC60

# Basic information

## Module config

```
/* Start AT SYNC: Send AT every 500ms, if receive OK, SYNC success, if no OK return after sending AT 10 times, SYNC fail */
[2019-01-31 02:58:52:462_S:] AT
[2019-01-31 02:58:52:462_R:] AT
[2019-01-31 02:58:52:462_R:] OK

/* Use ATV1 to set the response format */
[2019-01-31 02:58:52:493_S:] ATV1
[2019-01-31 02:58:52:508_R:] ATV1
[2019-01-31 02:58:52:508_R:] OK

/* Use ATE1 to enable echo mode */
[2019-01-31 02:58:52:524_S:] ATE1
[2019-01-31 02:58:52:540_R:] ATE1
[2019-01-31 02:58:52:540_R:] OK

/* Use AT+CMEE=2 to enable result code and use verbose values */
[2019-01-31 02:58:52:571_S:] AT+CMEE=2
[2019-01-31 02:58:52:587_R:] AT+CMEE=2
[2019-01-31 02:58:52:587_R:] OK

/* Get the baudrate, if the value is 0 (auto baudrate), then it will be set to 115200 (fixed baudrate) to assure reliable communication and avoid any problems caused by undetermined baudrate between DCE and DTE, value of IPR should be saved with AT&W */
[2019-01-31 02:58:52:602_S:] AT+IPR?
[2019-01-31 02:58:52:618_R:] AT+IPR?
[2019-01-31 02:58:52:618_R:] +IPR: 115200

[2019-01-31 02:58:52:618_R:] OK
```
## Module information
```
/* Use ATI to get module information of Manufacturer ID, Device module and Firmware version */
[2019-01-31 02:58:52:633_S:] ATI
[2019-01-31 02:58:52:649_R:] ATI
[2019-01-31 02:58:52:649_R:] Quectel_Ltd
[2019-01-31 02:58:52:649_R:] Quectel_MC60
[2019-01-31 02:58:52:649_R:] Revision: MC60CAR01A10

[2019-01-31 02:58:52:649_R:] OK

/* Use AT+GSN to query the IMEI of module */
[2019-01-31 02:58:52:649_S:] AT+GSN
[2019-01-31 02:58:52:665_R:] AT+GSN
[2019-01-31 02:58:52:665_R:] 861359030299596

[2019-01-31 02:58:52:665_R:] OK
[2019-01-31 02:58:52:680_S:] ATI
[2019-01-31 02:58:52:680_R:] ATI
[2019-01-31 02:58:52:680_R:] Quectel_Ltd
[2019-01-31 02:58:52:680_R:] Quectel_MC60
[2019-01-31 02:58:52:696_R:] Revision: MC60CAR01A10

[2019-01-31 02:58:52:696_R:] OK
```

## SIM card information
```
/* Use AT+CPIN? to query the SIM card status : SIM card inserted or not, locked or unlocked */
[2019-01-31 02:58:52:711_S:] AT+CPIN?
[2019-01-31 02:58:52:727_R:] AT+CPIN?
[2019-01-31 02:58:52:727_R:] +CPIN: READY

[2019-01-31 02:58:52:727_R:] OK

/* Use AT+CIMI to query the IMSI of SIM card */
[2019-01-31 02:58:52:743_S:] AT+CIMI
[2019-01-31 02:58:52:758_R:] AT+CIMI
[2019-01-31 02:58:52:758_R:] 452040038115715

[2019-01-31 02:58:52:758_R:] OK

/* Use AT+QCCID to query ICCID number of SIM card */
[2019-01-31 02:58:52:774_S:] AT+QCCID
[2019-01-31 02:58:52:790_R:] AT+QCCID
[2019-01-31 02:58:52:790_R:] 89840480000381157157

[2019-01-31 02:58:52:790_R:] OK
```
## Registration information
```
/* Use AT+CSQ to query current signal quality */
[2019-01-31 02:58:52:805_S:] AT+CSQ
[2019-01-31 02:58:52:821_R:] AT+CSQ
[2019-01-31 02:58:52:821_R:] +CSQ: 31,0

[2019-01-31 02:58:52:821_R:] OK

/* Use AT+CREG? /AT+CGREG? to query the network registration status. */
[2019-01-31 02:58:52:836_S:] AT+CREG?
[2019-01-31 02:58:52:852_R:] AT+CREG?
[2019-01-31 02:58:52:852_R:] +CREG: 0,1

[2019-01-31 02:58:52:852_R:] OK
[2019-01-31 02:58:52:868_S:] AT+CGREG?
[2019-01-31 02:58:52:883_R:] AT+CGREG?
[2019-01-31 02:58:52:883_R:] +CGREG: 0,1

[2019-01-31 02:58:52:883_R:] OK

/* Use AT+COPS? to query current Network Operator */
[2019-01-31 02:58:52:899_S:] AT+COPS?
[2019-01-31 02:58:52:930_R:] AT+COPS?
[2019-01-31 02:58:52:930_R:] +COPS: 0,0,"Viettel Mobile"

[2019-01-31 02:58:52:930_R:] OK
```

# TCP/UDP

## Server information

Domain: bacnh.duckdns.org  
TCP Port: 2001   
UDP Port: 2000   

Using Ping to get IP --> 203.210.135.30

```
$ ping bacnh.duckdns.org
PING bacnh.duckdns.org (203.210.135.30): 56 data bytes
64 bytes from 203.210.135.30: icmp_seq=0 ttl=64 time=1.431 ms
64 bytes from 203.210.135.30: icmp_seq=1 ttl=64 time=1.679 ms
64 bytes from 203.210.135.30: icmp_seq=2 ttl=64 time=2.504 ms
64 bytes from 203.210.135.30: icmp_seq=3 ttl=64 time=3.857 ms
64 bytes from 203.210.135.30: icmp_seq=4 ttl=64 time=1.405 ms
64 bytes from 203.210.135.30: icmp_seq=5 ttl=64 time=1.631 ms
```

## PDP ACT at non-transparent mode

```
/* Use AT+CPIN?/AT+CREG?/AT+CGREG? to query the SIM status and network registration status */
[2019-01-31 03:12:05:246_S:] AT+CPIN?
[2019-01-31 03:12:05:277_R:] AT+CPIN?
[2019-01-31 03:12:05:277_R:] +CPIN: READY

[2019-01-31 03:12:05:277_R:] OK
[2019-01-31 03:12:05:293_S:] AT+CREG?
[2019-01-31 03:12:05:309_R:] AT+CREG?
[2019-01-31 03:12:05:309_R:] +CREG: 0,1

[2019-01-31 03:12:05:309_R:] OK
[2019-01-31 03:12:05:325_S:] AT+CGREG?
[2019-01-31 03:12:05:340_R:] AT+CGREG?
[2019-01-31 03:12:05:340_R:] +CGREG: 0,1

[2019-01-31 03:12:05:340_R:] OK

/* Use AT+QIMODE command to select TCPIP Stack mode, it is non-transparent mode when AT+QIMODE=0, and AT+QIMODE=1 is transparent (This tool only support non-transparent mode) */
[2019-01-31 03:12:05:357_S:] AT+QIMODE=0
[2019-01-31 03:12:05:372_R:] AT+QIMODE=0
[2019-01-31 03:12:05:372_R:] OK

/* Use AT+QICSGP=1,"V-INTERNET" to set APN as "V-INTERNET" */
[2019-01-31 03:12:05:388_S:] AT+QICSGP=1,"V-INTERNET"
[2019-01-31 03:12:05:402_R:] AT+QICSGP=1,"V-INTERNET"
[2019-01-31 03:12:05:402_R:] OK

/* (4) Start TCPIP task */
[2019-01-31 03:12:05:418_S:] AT+QIREGAPP
[2019-01-31 03:12:05:435_R:] AT+QIREGAPP
[2019-01-31 03:12:05:435_R:] OK

/* Check the current connecting mode(1: GPRS connecting mode - 0: CSD connecting mode) */
[2019-01-31 03:12:05:451_S:] AT+QICSGP?
[2019-01-31 03:12:05:465_R:] AT+QICSGP?
[2019-01-31 03:12:05:465_R:] +QICSGP: 1

[2019-01-31 03:12:05:465_R:] OK

/* The current connecting mode is GPRS connecting mode */

/* Active the GPRS context */
[2019-01-31 03:12:05:481_S:] AT+QIACT
[2019-01-31 03:12:05:496_R:] AT+QIACT
[2019-01-31 03:12:06:045_R:] OK

/* Get the local IP address */
[2019-01-31 03:12:06:075_S:] AT+QILOCIP
[2019-01-31 03:12:06:090_R:] AT+QILOCIP
[2019-01-31 03:12:06:106_R:] 10.137.160.20
```

## TCP/UDP

Setting: AT+QIMUX=0, single TCP/UDP Sessions

### TCP Connect
#### Open IP Socket
```
/* Use ATV1 to set the response format */
[2019-01-31 03:15:15:035_S:] ATV1
[2019-01-31 03:15:15:067_R:] ATV1
[2019-01-31 03:15:15:067_R:] OK

/* Use AT+QIHEAD=1 to add the header information when receive data */
[2019-01-31 03:15:15:098_S:] AT+QIHEAD=1
[2019-01-31 03:15:15:113_R:] AT+QIHEAD=1
[2019-01-31 03:15:15:113_R:] OK

/* Use AT+QIDNSIP=0 to use the IP address to establish TCP/UDP session, while AT+QIDNSIP=1 is use the domain name to establish TCP/UDP session */
[2019-01-31 03:15:15:128_S:] AT+QIDNSIP=0
[2019-01-31 03:15:15:143_R:] AT+QIDNSIP=0
[2019-01-31 03:15:15:143_R:] OK

/* Use AT+QIOPEN="TCP","203.210.135.30","2001" to connect to a TCP server (IP address: 203.210.135.30:2001). If return "CONNECT OK" means successfully connected to the remote server */
[2019-01-31 03:15:15:159_S:] AT+QIOPEN="TCP","203.210.135.30","2001"
[2019-01-31 03:15:15:174_R:] AT+QIOPEN="TCP","203.210.135.30","2001"
[2019-01-31 03:15:15:174_R:] OK

[2019-01-31 03:15:15:800_R:] CONNECT OK
```

#### Open Domain socket
```
/* Use ATV1 to set the response format */
[2019-01-31 03:38:19:148_S:] ATV1
[2019-01-31 03:38:19:148_R:] ATV1
[2019-01-31 03:38:19:148_R:] OK

/* Use AT+QIHEAD=1 to add the header information when receive data */
[2019-01-31 03:38:19:163_S:] AT+QIHEAD=1
[2019-01-31 03:38:19:163_R:] AT+QIHEAD=1
[2019-01-31 03:38:19:163_R:] OK

/* Use AT+QIDNSIP=0 to use the IP address to establish TCP/UDP session, while AT+QIDNSIP=1 is use the domain name to establish TCP/UDP session */
[2019-01-31 03:38:19:179_S:] AT+QIDNSIP=1
[2019-01-31 03:38:19:179_R:] AT+QIDNSIP=1
[2019-01-31 03:38:19:179_R:] OK

/* Use AT+QIOPEN="TCP","bacnh.duckdns.org","2001" to connect to a TCP server (IP address: bacnh.duckdns.org:2001). If return "CONNECT OK" means successfully connected to the remote server */
[2019-01-31 03:38:19:195_S:] AT+QIOPEN="TCP","bacnh.duckdns.org","2001"
[2019-01-31 03:38:19:195_R:] AT+QIOPEN="TCP","bacnh.duckdns.org","2001"
[2019-01-31 03:38:19:195_R:] OK

[2019-01-31 03:38:20:695_R:] CONNECT OK
```
#### Send/Receive data
```
/* AT+QISEND, send data to server, ">" from the UART indicates the following input data is considered as data to be send. After receiving ">", input data (TEST), the maximum length of the data is 1460, the data beyond 1460 will be omitted. Then use <CTRL+Z> to send data. When receive SEND OK means the data has been sent */
[2019-01-31 03:17:01:794_S:] AT+QISEND
[2019-01-31 03:17:01:794_R:] AT+QISEND
[2019-01-31 03:17:01:794_R:] > Hello
/* Use AT+QISACK to query whether all the data has been sent out */

[2019-01-31 03:17:02:046_R:] SEND OK
[2019-01-31 03:17:02:669_R:] IPD5:Hello
[2019-01-31 03:17:03:029_S:] AT+QISACK
[2019-01-31 03:17:03:029_R:] AT+QISACK
[2019-01-31 03:17:03:044_R:] +QISACK: 5, 5, 0

[2019-01-31 03:17:03:044_R:] OK
```
#### Close socket

```
/* Use ATE1 to enable echo mode */
[2019-01-31 03:20:14:280_S:] ATE1
[2019-01-31 03:20:14:297_R:] ATE1
[2019-01-31 03:20:14:297_R:] OK

/* Use AT+QICLOSE to close the connecting of TCP/UDP */
[2019-01-31 03:20:14:313_S:] AT+QICLOSE
[2019-01-31 03:20:14:328_R:] AT+QICLOSE
[2019-01-31 03:20:14:328_R:] CLOSE OK
```

### UDP Connection

#### Open Socket via IP

```
/* Use ATV1 to set the response format */
[2019-01-31 03:21:51:805_S:] ATV1
[2019-01-31 03:21:51:821_R:] ATV1
[2019-01-31 03:21:51:821_R:] OK

/* Use AT+QIHEAD=1 to add the header information when receive data */
[2019-01-31 03:21:51:836_S:] AT+QIHEAD=1
[2019-01-31 03:21:51:836_R:] AT+QIHEAD=1
[2019-01-31 03:21:51:836_R:] OK

/* Use AT+QIDNSIP=0 to use the IP address to establish TCP/UDP session, while AT+QIDNSIP=1 is use the domain name to establish TCP/UDP session */
[2019-01-31 03:21:51:852_S:] AT+QIDNSIP=0
[2019-01-31 03:21:51:852_R:] AT+QIDNSIP=0
[2019-01-31 03:21:51:852_R:] OK

/* Use AT+QIOPEN="TCP","203.210.135.30","2000" to connect to a TCP server (IP address: 203.210.135.30:2000). If return "CONNECT OK" means successfully connected to the remote server */
[2019-01-31 03:21:51:867_S:] AT+QIOPEN="UDP","203.210.135.30","2000"
[2019-01-31 03:21:51:867_R:] AT+QIOPEN="UDP","203.210.135.30","2000"
[2019-01-31 03:21:51:867_R:] OK

[2019-01-31 03:21:51:883_R:] CONNECT OK
```

### Open Socket via Domain

```
/* Use ATV1 to set the response format */
[2019-01-31 03:41:36:092_S:] ATV1
[2019-01-31 03:41:36:122_R:] ATV1
[2019-01-31 03:41:36:122_R:] OK

/* Use AT+QIHEAD=1 to add the header information when receive data */
[2019-01-31 03:41:36:139_S:] AT+QIHEAD=1
[2019-01-31 03:41:36:154_R:] AT+QIHEAD=1
[2019-01-31 03:41:36:154_R:] OK

/* Use AT+QIDNSIP=0 to use the IP address to establish TCP/UDP session, while AT+QIDNSIP=1 is use the domain name to establish TCP/UDP session */
[2019-01-31 03:41:36:184_S:] AT+QIDNSIP=1
[2019-01-31 03:41:36:200_R:] AT+QIDNSIP=1
[2019-01-31 03:41:36:200_R:] OK

/* Use AT+QIOPEN="TCP","bacnh.duckdns.org","2000" to connect to a TCP server (IP address: bacnh.duckdns.org:2000). If return "CONNECT OK" means successfully connected to the remote server */
[2019-01-31 03:41:36:216_S:] AT+QIOPEN="UDP","bacnh.duckdns.org","2000"
[2019-01-31 03:41:36:231_R:] AT+QIOPEN="UDP","bacnh.duckdns.org","2000"
[2019-01-31 03:41:36:231_R:] OK

[2019-01-31 03:41:37:341_R:] CONNECT OK
```

#### Send/Receive data

```
/* AT+QISEND, send data to server, ">" from the UART indicates the following input data is considered as data to be send. After receiving ">", input data (TEST), the maximum length of the data is 1460, the data beyond 1460 will be omitted. Then use <CTRL+Z> to send data. When receive SEND OK means the data has been sent */
[2019-01-31 03:22:49:958_S:] AT+QISEND
[2019-01-31 03:22:49:989_R:] AT+QISEND
[2019-01-31 03:22:49:989_R:] > Hello

/* Use AT+QISACK to query whether all the data has been sent out */
[2019-01-31 03:22:50:239_R:] SEND OK
[2019-01-31 03:22:50:850_R:] IPD5:Hello
```

#### Close Socket

```
/* Use ATE1 to enable echo mode */
[2019-01-31 03:23:10:520_S:] ATE1
[2019-01-31 03:23:10:536_R:] ATE1
[2019-01-31 03:23:10:536_R:] OK

/* Use AT+QICLOSE to close the connecting of TCP/UDP */
[2019-01-31 03:23:10:551_S:] AT+QICLOSE
[2019-01-31 03:23:10:567_R:] AT+QICLOSE
[2019-01-31 03:23:10:567_R:] CLOSE OK
```

## Deactivate GPRS/CSD PDP Context

```
/* Use ATE1 to enable echo mode */
[2019-01-31 03:35:15:033_S:] ATE1
[2019-01-31 03:35:15:033_R:] ATE1
[2019-01-31 03:35:15:048_R:] OK

/* Use AT+QIDEACT to deactivate GPRS context */
[2019-01-31 03:35:15:549_S:] AT+QIDEACT
[2019-01-31 03:35:15:549_R:] AT+QIDEACT
[2019-01-31 03:35:16:001_R:] DEACT OK
```