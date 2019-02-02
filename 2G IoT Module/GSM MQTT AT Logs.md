# Introduction

Supported modules: M66 RR2.0, M95, MC60, MC90

## Config MQTT Section


### Step 1: Install certificate and key to file system

Install certificate and key to the file system by `AT+QSECWRITE`, in case the file system is existed, use `AT+QSECDEL` to delete the respective file.


Delete old cer file if have:
```
AT+QSECDEL="RAM:cacert.pem"
AT+QSECDEL="RAM:client.pem"
AT+QSECDEL="RAM:user_key.pem"
```

Write CA certs, client certs and client private keys into RAM. Due to EOL (CRLF) issue: please use Notepad++ to open files to calculate actual size of CA, CC and CK files.

```
AT+QMTCFG="SSL",0,1,2
OK

/* Store CA file to RAM */
AT+QSECWRITE="RAM:cacert.pem",1492,100
CONNECT

+QSECWRITE: 1492,2554

OK

/* Store client to RAM */
AT+QSECWRITE="RAM:client.pem",1356,100
CONNECT

+QSECWRITE: 1356,1629

OK

/* Store User Key */
AT+QSECWRITE="RAM:user_key.pem",1702,100
CONNECT

+QSECWRITE: 1702,446f

OK
```

`AT+QSECREAD` to check the checksum of certificate and key:

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

## Step 2: Configure SSL

Quectel GSM module supports 6 SSL contexts. Let's say, SSL context = `2`.

```
/* Set location of cacert, clientcert, clientkey */
AT+QSSLCFG="cacert",2,"RAM:cacert.pem"
OK
AT+QSSLCFG="clientcert",2,"RAM:client.pem"
OK
AT+QSSLCFG="clientkey",2,"RAM:user_key.pem"
OK

/* Security level = 2, manage server and client authentication if requested by the remote server */
AT+QSSLCFG="seclevel",2,2
OK

/* SSL Version = 4 --> Support all SSL versions: (0) - SSL3.0, (1) - TLS1.0, (2) - TLS1.1, (3) - TLS1.2 */
AT+QSSLCFG="sslversion",2,4
OK

/* Support all SSL ciper suites */
AT+QSSLCFG="ciphersuite",2,"0xFFFF"
OK


AT+QSSLCFG="ignorertctime",1
```

## Step 3: Config APN and activate network

Configure network parameters: APN, ...: 

```
/* Use AT+CPIN?/AT+CREG?/AT+CGREG? to query the SIM status and network registration status */
AT+CPIN?
+CPIN: READY

OK
AT+CREG?
+CREG: 0,1

OK
AT+CGREG?
+CGREG: 0,1

OK

/* Use AT+QIMODE command to select TCPIP Stack mode, it is non-transparent mode when AT+QIMODE=0 */
AT+QIMODE=0
OK

/* Use AT+QICSGP=1,"V-INTERNET" to set APN as "V-INTERNET" */
AT+QICSGP=1,"V-INTERNET"
OK
```
Start the TCP/IP Stack and active GPRS context:

```
/* Start TCPIP task */
AT+QIREGAPP
OK

/* Check the current connecting mode(1: GPRS connecting mode - 0: CSD connecting mode) */
AT+QICSGP?
+QICSGP: 1

OK

/* Active the GPRS context */
AT+QIACT
OK
```

Query the local IP addrerss by `AT+QILOCIP`:

```
/* Get the local IP address */
AT+QILOCIP
10.137.160.20
```


To Open the network for MQTT section:

```
AT+QMTOPEN=0,"220.180.239.212","8102"
OK

+QMTOPEN: 0,0
```

To close the MQTT section:

```
AT+QMTCLOSE=0
OK
```

## Manipulate MQTT Connection

Open MQTT Connection

```
AT+QMTCONN=0,"M95_0207"
OK

+QMTSTAT: 0,1
```

Subcribe to an topic, using `AT+QMTSUB`

```
AT+QMTSUB=0,1,"test",1


OK

+QMTSUB: 0,1,0,1
```

Public to an toic, using `AT+QMTPUB`:

```
AT+QMTPUB=0,1,1,0,"test"


> M95 Hello World


OK


+QMTPUB: 0,1,0


+QMTRECV: 0,1,test,M95 Hello World
```


Note: Need to change the client ID in case of can't connect to the server.

In case, the client is already connected to server, need to disconnect.

```
AT+QMTDISC=0
OK
```