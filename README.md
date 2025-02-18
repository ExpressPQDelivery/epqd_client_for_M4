# ExᴘʀᴇssPQDᴇʟɪᴠᴇʀʏ based on WolfSSL 4.7.0 with Post-Quantum Algorithms for Nucleo-F439ZI (Client)

## Description
This is a library that implements ExᴘʀᴇssPQDᴇʟɪᴠᴇʀʏ client based on WolfSSL, designed to run on Nucleo Boards F439ZI. The version we are using is [WolfSSL 4.7.0](https://github.com/wolfSSL/wolfssl/releases/tag/v4.7.0-stable) and the postquantum algorithms are from [PQClean](https://github.com/PQClean/PQClean). The postquantum algorithms that are supported are:

### Key Encapsualtion Mechanisms (KEMs)

- [x] CRYSTALS-Kyber


### Digital Signature Algorithms

- [x] CRYSTALS-Dilithium

- [x] Falcon

## Target Board and Settings

- This version is developed and is mainly targeting the [STM32 Nucleo F439ZI](https://www.st.com/en/evaluation-tools/nucleo-f439zi.html) board.
- For networking, the [LwIP](https://savannah.nongnu.org/projects/lwip/) TCP/IP stack (version 2.1.2) is used and the [FreeRTOS](https://www.freertos.org/), as a real time operating system.

## Installation


### STM32 Cube IDE
0. Connect the LAN and power to the board to enable communication via LwIP.

1. Download this repository.

2. Using STM32 Cube IDE, go to `File > Import > Projects from Folder or Archive`, select the `Archive...` button and select the file `epqd_client_for_nucleof439zi.zip`.

3. Click `Finish` and the project is ready to be built.

## Configuring

### 1. Enable ExᴘʀᴇssPQDᴇʟɪᴠᴇʀʏ and PQ algorithms
in line 141 of `Core/Inc/user_setting.h` we can enable `#define HAVE_PQDELIVARY` to use ExᴘʀᴇssPQDᴇʟɪᴠᴇʀʏ; if we comment it out, we can run the original PQC-TLS.

in line 133-134, We can choose which signature algorithms (Falcon or Dilithum) will be enabled.

Note that we use only Kyber as the KEM.

**   **From now on we define *"Middlewares/Third_Party/wolfSSL_wolfSSL_wolfSSL/wolfssl"* as "/"** 	**

### 2. Choose the security strength of PQ algorithms


edit the following files: 

*"/wolfcrypt/postquantum/kyber/kyber_security.h"*

*"/wolfcrypt/postquantum/dilithium/dilithium_security.h"*

*"/wolfcrypt/postquantum/falcon/falcon_security.h"*


namely we have the following equivelences:

**SECURITY_LEVEL 1** --> Kyber512, Dilithium2, Falcon512

**SECURITY_LEVEL 3** --> Kyber768, Dilithium3

**SECURITY_LEVEL 5** --> Kyber1024, Falcon1024

### 3. Set the DNS IP address and the server Port number
in line 115 of `Core/Src/main.c` we can set the domain name of the server.

in line 1577 of `Core/Src/main.c` we can set the DNS IP address.

## Usage

To use this project to establish a TLS connection to a remote PC (Server) (i.e a server running [this](https://github.com/ExpressPQDelivery/epqd_server_lib_forM4) project) you should do:

0. Set up a DNS (see [here](https://github.com/ExpressPQDelivery/DNS_records_for_epqd)) and a server before running a client.
1. Set up a client to run on the board by "downloading" the code to the board.
2. Edit the external DNS IP and the server port number, then run a client.

## Serial terminal

We use [CoolTerm](https://coolterm.macupdate.com/) as a serial terminal.
