# ExᴘʀᴇssPQDᴇʟɪᴠᴇʀʏ based on WolfSSL 4.7.0 with Post-Quantum Algorithms for PC (Server)

## Description
This is a library that implements ExᴘʀᴇssPQDᴇʟɪᴠᴇʀʏ based on WolfSSL, designed to run on Nucleo Boards F439ZI. The version we are using is [WolfSSL 4.7.0](https://github.com/wolfSSL/wolfssl/releases/tag/v4.7.0-stable) and the postquantum algorithms are from [PQClean](https://github.com/PQClean/PQClean). The postquantum algorithms that are supported are:

### Key Encapsualtion Mechanisms (KEMs)

- [x] CRYSTALS-Kyber


### Digital Signature Algorithms

- [x] CRYSTALS-Dilithium

- [x] Falcon

For networking, the [LwIP](https://savannah.nongnu.org/projects/lwip/) TCP/IP stack (version 2.1.2) is used and the [FreeRTOS](https://www.freertos.org/), as a real time operating system.

## Target Boards

This version is developed and is mainly targeting the [STM32 Nucleo F439ZI](https://www.st.com/en/evaluation-tools/nucleo-f439zi.html) board.


## Installation


### STM32 Cube IDE

1. Download this repository as a ziped file:

2. Using STM32 Cube IDE, go to `File > Import > Projects from Folder or Archive`, select the `Archive...` button and select the file `pq-wolfssl-for-embedded-main.zip`.

3. Click `Finish` and the project is ready to be built.

## Configuring
