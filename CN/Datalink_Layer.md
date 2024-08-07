# Table of contents

| Sl no | Topic                                                               |
| ----- | ------------------------------------------------------------------- |
| 1.    | [Framing](#1-framing)                                               |
| 2.    | [Error Detection and Correction](#2-error-detection-and-correction) |
| 3.    | [Protocols in Data Link Layer](#3-protocols-in-data-link-layer)     |
| 4.    | [Multiple Access Protocols](#4-multiple-access-protocols)           |
| 5.    | [MAC Address](#5-mac-address)                                       |

## Introduction

Datalink layer is the second layer of OSI model. It is responsible for the node to node delivery of the message. It is responsible for the error detection and correction. It is responsible for the flow control and framing. It is responsible for the access control. It is responsible for the media access control

## 1. Framing

Frames are units of digital transmission.
The process of dividing the data into recoverable chunks is called framing. It is done so that it can be easily checked for errors.

### 1.1 Problems with framing

- **Detecting the start of frame**: The receiver must be able to detect the start of the frame. Hence a special sequence of bits is used to indicate the start of the frame.
  This is called SFD (Start Frame Delimiter).
- **Error detection**: The receiver must be able to detect errors in the frame. This is done by adding a checksum to the frame.
  CRC ( Cyclic Redundancy Check ) is used for error detection.

- **Framing overhead**: The extra bits added to the frame for error detection and start of frame detection are called framing overhead.
- **Framing synchronization**: Stations must be synchronized to the frame boundaries and timings.

### 1.2 Types of framing

There are two types of framing:

1. **Fixed size framing**: In this type of framing, the frame size is fixed. The frame size is decided by the network administrator. The frame size is fixed and the data is divided into frames of fixed size.
   - **Drawbacks**: It is not efficient as the frame size is fixed. If the data is less than the frame size, then the remaining space is wasted.
   - **Padding**: If the data is less than the frame size, then padding is done to fill the remaining space.
2. **Variable size framing**: In this type of framing, there is no fixed size but there is a need of frame beginning and frame end. The frame beginning and frame end are indicated by special sequences of bits.
   - **Drawbacks**: It is not efficient as the frame size is not fixed. The receiver must be able to detect the end of the frame.
   - **End of frame detection**: The receiver must be able to detect the end of the frame. This is done by using a special sequence of bits called EOF (End of Frame).
   - What if the data contain **EOF** character? Then we need to use a special escape character to indicate that this is not actually the end of frame.
   - **Bit stuffing**: If the data contains the escape character, then bit stuffing is done to escape the special character.
   - **Byte stuffing**: If the data contains the escape character, then byte stuffing is done to escape the special character.

## 2. Error Detection and Correction

The datalink layer is responsible for error detection and correction. The error detection and correction is done by adding a checksum to the frame. The checksum is calculated by using CRC (Cyclic Redundancy Check).

- **Check Sum**:
  Check sum is a value that is calculated from the data and is sent along with the data. The receiver calculates the checksum from the received data and compares it with the checksum sent by the sender. If the checksums match, then the data is correct. If the checksums do not match, then the data is incorrect.

- **CRC (Cyclic Redundancy Check)**:
  In this method of error detection, the sender and receiver agree on a polynomial. The sender divides the data by the polynomial and sends the remainder along with the data. The receiver divides the received data by the polynomial and checks if the remainder is zero. If the remainder is zero, then the data is correct. If the remainder is not zero, then the data is incorrect.

How error is corrected in CRC?
When a frame is found to have an error, the receiver sends a negative acknowledgment to the sender. The sender then retransmits the frame. The receiver then corrects the error by using the correct frame.

## 3. Protocols in Data Link Layer

There are various protocols in the data link layer. Some of them are:

1. MAC (Media Access Control)
2. Multi-Access Protocols
3. Ethernet

### 3.1 MAC (Media Access Control)

This protocol is used to control the access to the media. It is used to control the access to the media so that only one station can access the media at a time. It is used to control the access to the media so that there is no collision.

### 3.2 Multi-Access Protocols

This protocol is used to control the access to the media so that multiple stations can access the media at the same time. It is used to control the access to the media so that there is no collision.

This works as follows

- **Carrier Sense Multiple Access (CSMA)**: In this protocol, the station listens to the media before sending the data. If the media is free, then the station sends the data. If the media is busy, then the station waits for the media to become free.
- **Carrier Sense Multiple Access with Collision Detection (CSMA/CD)**: In this protocol, the station listens to the media before sending the data. If the media is free, then the station sends the data. If the media is busy, then the station waits for the media to become free. If the station detects a collision, then it sends a jam signal to indicate that there is a collision.
- **Carrier Sense Multiple Access with Collision Avoidance (CSMA/CA)**: In this protocol, the station listens to the media before sending the data. If the media is free, then the station sends the data. If the media is busy, then the station waits for the media to become free. If the station detects a collision, then it waits for a random amount of time before sending the data.

### 3.3 Ethernet

This protocol is used to define the way a data frame should be structured. It has different standard like 802.3, 802.11, 802.15, 802.16 etc.

## 4. Multiple Access Protocols

There are three types of multiple access protocols:

1. **Random Access Protocols**: In this protocol, the station sends the data without checking if the media is free. If there is a collision, then the station waits for a random amount of time before sending the data.
2. **Channelization Protocols**: In this protocol, the media is divided into channels. Each station is assigned a channel. The station can send the data only on its channel.
3. **Controlled Access Protocols**: In this protocol, the station sends the data only when it is allowed to send the data. The station sends the data only when it is allowed to send the data.

### 4.1 Random Access Protocols

In this method there is no fixed timing for sending the data. There is also no fixed sequence of stations sending the data.

1. ALOHA
2. CSMA
3. CSMA/CD
4. CSMA/CA

**Aloha**:
In this protocol, the station sends the data without checking if the media is free. If there is a collision, then the station waits for a random amount of time before sending the data.

- First a station transmits the data and waits a time `T` for the acknowledgment.
- If the acknowledgment is received, then the data is recieved successfully.
- If the acknowledgement is not received in `T` time, then the station retransmits the data.

**CSMA**:
CSMA - Carrier Sense Multiple Access. In this protocol, the station listens to the media before sending the data. If the media is free, then the station sends the data. If the media is busy, then the station waits for the media to become free.

- First a station listens to the media.
- If the media is free, then the station sends the data.
- If the media is busy, then the station waits for the media to become free.

1-Persistent: The node senses the channel, if idle it sends the data, otherwise it continuously keeps on checking the medium for being idle and transmits unconditionally(with 1 probability) as soon as the channel gets idle.

Non-Persistent: The node senses the channel, if idle it sends the data, otherwise it checks the medium after a random amount of time (not continuously) and transmits when found idle.

P-Persistent: The node senses the medium, if idle it sends the data with p probability. If the data is not transmitted ((1-p) probability) then it waits for some time and checks the medium again, now if it is found idle then it send with p probability. This repeat continues until the frame is sent. It is used in Wifi and packet radio systems.

O-Persistent: Superiority of nodes is decided beforehand and transmission occurs in that order. If the medium is idle, node waits for its time slot to send data.

**CSMA/CD**:
CSMA/CD - Carrier Sense Multiple Access with Collision Detection. In this protocol, the station listens to the media before sending the data. If the media is free, then the station sends the data. If the media is busy, then the station waits for the media to become free. If the station detects a collision, then it sends a jam signal to indicate that there is a collision.

This is extensively used in wired networks.

**CSMA/CA**:
CSMA/CA - Carrier Sense Multiple Access with Collision Avoidance. In this protocol, the station listens to the media before sending the data. If the media is free, then the station sends the data. If the media is busy, then the station waits for the media to become free. If the station detects a collision, then it waits for a random amount of time before sending the data.

This is used for wireless networks.

In wireless networks, the station cannot detect the collision. Hence it waits for a random amount of time before sending the data.

### 4.2 Channelization Protocols

**FDMA** :
FDMA - Frequency Division Multiple Access. In this protocol, the media is divided into channels. Each station is assigned a channel. The station can send the data only on its channel.

**TDMA**:
TDMA - Time Division Multiple Access. In this protocol, the media is divided into time slots. Each station is assigned a time slot. The station can send the data only on its time slot.

**CDMA**:
CDMA - Code Division Multiple Access. In this protocol, the media is divided into codes. Each station is assigned a code. The station can send the data only on its code.

### 4.3 Controlled Access Protocols

**Reservation** :
In this protocol, the station sends a reservation signal to the receiver. The receiver sends an acknowledgment to the sender. The sender then sends the data to the receiver.

**Polling** :
In this protocol, the station sends a poll signal to the receiver. The receiver sends an acknowledgment to the sender. The sender then sends the data to the receiver.
Poll signal is sent by the master to the slave. The slave sends the data to the master.

**Token Passing** :
In this protocol, the station sends a token to the receiver. The receiver sends an acknowledgment to the sender. The sender then sends the data to the receiver.
Until the token is received, the station cannot send the data.

## 5. MAC Address

What is MAC Address?
MAC Address is a unique identifier assigned to the network interface for communications on the physical network segment. It is also known as the hardware address or physical address.
This is a 48-bit address. The first 24 bits are the OUI (Organizationally Unique Identifier) and the last 24 bits are the NIC (Network Interface Controller) specific address.

This address is static and is assigned by the manufacturer.
