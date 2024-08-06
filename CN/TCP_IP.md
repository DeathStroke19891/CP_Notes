# Table of Contents

| Sl No. | Topic                                                                      |
| ------ | -------------------------------------------------------------------------- |
| 1.     | [Definition of TCP/IP Protocol Suite](#definition-of-tcpip-protocol-suite) |
| 2.     | [Functions of TCP/IP Layers](#functions-of-tcpip-layers)                   |
| 3.     | [TCP/IP Model vs OSI Model](#tcpip-model-vs-osi-model)                     |
| 4.     | [Protocols in TCP/IP Suite](#protocols-in-tcpip-suite)                     |

---

# TCP/IP Protocol Suite

TCP/IP is a suite of protocols that is used to interconnect network devices on the internet. It is the most widely used protocol suite in the world. It is named after two of the most important protocols in the suite: the Transmission Control Protocol (TCP) and the Internet Protocol (IP). The TCP/IP protocol suite is also called the Internet Protocol Suite.

There are four layers in the TCP/IP protocol suite:

1. Application Layer
2. Transport Layer
3. Internet Layer
4. Network Interface Layer

## Functions of TCP/IP Layers

| Layer                   | Functions                                                                                               |
| ----------------------- | ------------------------------------------------------------------------------------------------------- |
| Application Layer       | Provides network services directly to the user's applications. Has protocols like HTTP, FTP, SMTP, etc. |
| Transport Layer         | Provides end-to-end communication between the source and destination. Has protocols like TCP, UDP, etc. |
| Internet Layer          | Responsible for routing packets from the source to the destination. Has protocols like IP, ICMP, etc.   |
| Network Interface Layer | Responsible for transmitting data packets over the network. Has protocols like Ethernet, Wi-Fi, etc.    |

## TCP/IP Model vs OSI Model

| OSI Model       | TCP/IP Model |
| --------------- | ------------ |
| Has 7 layers    | Has 4 layers |
| Theoretical     | Practical    |
| Complex         | Simple       |
| Not widely used | Widely used  |

## Protocols in TCP/IP Suite

### 1. Application Layer Protocols

| Protocol                             | Description                                        |
| ------------------------------------ | -------------------------------------------------- |
| HTTP ( HyperText Transfer Protocol)  | Used for transmitting web pages over the internet. |
| FTP (File Transfer Protocol)         | Used for transferring files over the internet.     |
| SMTP (Simple Mail Transfer Protocol) | Used for sending emails over the internet.         |
| POP3 (Post Office Protocol)          | Used for receiving emails over the internet.       |

### 2. Transport Layer Protocols

| Protocol                            | Description                                                                              |
| ----------------------------------- | ---------------------------------------------------------------------------------------- |
| TCP (Transmission Control Protocol) | Provides reliable, connection-oriented communication between the source and destination. |
| UDP (User Datagram Protocol)        | Provides unreliable, connectionless communication between the source and destination.    |

### 3. Internet Layer Protocols

| Protocol                                   | Description                                                         |
| ------------------------------------------ | ------------------------------------------------------------------- |
| IP (Internet Protocol)                     | Responsible for routing packets from the source to the destination. |
| ICMP (Internet Control Message)            | Used for error reporting and diagnostic functions in IP networks.   |
| ARP (Address Resolution Protocol)          | Used for mapping an IP address to a MAC address.                    |
| DHCP (Dynamic Host Configuration Protocol) | Used for dynamically assigning IP addresses to network devices.     |
| RARP (Reverse Address Resolution Protocol) | Used for mapping a MAC address to an IP address.                    |
| IGMP (Internet Group Management Protocol)  | Used for managing IP multicast groups.                              |

### 4. Network Interface Layer Protocols

| Protocol                                | Description                                                            |
| --------------------------------------- | ---------------------------------------------------------------------- |
| Ethernet                                | Used for transmitting data packets over a wired network.               |
| Wi-Fi                                   | Used for transmitting data packets over a wireless network.            |
| PPP (Point-to-Point Protocol)           | Used for establishing a direct connection between two network devices. |
| SLIP (Serial Line Internet Protocol)    | Used for transmitting IP packets over serial lines.                    |
| FDDI (Fiber Distributed Data Interface) | Used for transmitting data packets over a fiber optic network.         |
