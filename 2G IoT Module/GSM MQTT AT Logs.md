# Introduction

Supported modules: M66 RR2.0, M95, MC60, MC90

## Config MQTT Section


### Store cacert,client,user_key into RAM

```
AT+QMTCFG="SSL",0,1,2
OK

/* Store CA file to RAM */
AT+QSECWRITE="RAM:cacert.pem",1467,100
CONNECT

+QSECWRITE: 1392,235a

OK


/* Store client to RAM */
AT+QSECWRITE="RAM:client.pem",1333,100
CONNECT

+QSECWRITE: 1260,5e69

OK

/* Store User Key */
AT+QSECWRITE="RAM:user_key.pem",1674,100
CONNECT

+QSECWRITE: 1588,1a3e

OK
```

Read again content:

```
AT+QSECREAD="RAM:cacert.pem"
+QSECREAD: 1,4c30

OK
AT+QSECREAD="RAM:client.pem"
+QSECREAD: 1,6e5c

OK
AT+QSECREAD="RAM:user_key.pem"
+QSECREAD: 1,321e

OK

```

## Config MQTT to use the certs from RAM

```
AT+QSSLCFG="cacert",2,"RAM:cacert.pem"
OK
AT+QSSLCFG="clientcert",2,"RAM:client.pem"
OK
AT+QSSLCFG="clientkey",2,"RAM:user_key.pem"
OK
AT+QSSLCFG="seclevel",2,2
OK
AT+QSSLCFG="sslversion",2,4
OK
AT+QSSLCFG="ciphersuite",2,"0xFFFF"
OK
AT+QSSLCFG="ignorertctime",1
```

## Open/Close a network

Activate PDP context:

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


To Open the network for MQTT section:

```
AT+QMTOPEN=0,"220.180.239.212","8102"
OK

+QMTOPEN: 0,0
```

To close the connection:

```
AT+QMTCLOSE=0
```

## Manipulate MQTT Connection

```
AT+QMTCONN=0,"M95_0207"
OK

+QMTSTAT: 0,1
```

Subcribe to an topic:

```
AT+QMTSUB=0,1,"$aws/things/M95FAR03A04/shadow/update/accepted",1
```

Note: Need to change the client ID in case of can't connect to the server.

In case, the client is already connected to server, need to disconnect.

```
AT+QMTDISC=0
```