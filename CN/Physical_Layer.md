# Table of contents

| Sl No. | Topic                                       |
| ------ | ------------------------------------------- |
| 1.     | [Introduction](#physical-layer)             |
| 2.     | [Data transmission](#1-data-transmission)   |
| 3.     | [Bandwidth](#2-bandwidth)                   |
| 4.     | [Transmission media](#3-transmission-media) |

# Physical Layer

This is the first layer of the OSI model. It is responsible for the transmission and reception of unstructured raw data between a device and a physical transmission medium.
It converts the digital bits into electrical, radio, or optical signals and transmits them over a physical medium.

This layer deals with the bit-level transmission between different devices and supports the following functions:

1. Bit synchronization
2. Bit rate control
3. Physical topology
4. Transmission mode
5. Line configuration
6. Multiplexing

## 1. Data transmission

Data transmission is the process of sending digital or analog data over a communication medium. It involves the transmission of data from one device to another.

Data transmission can be classified into two types:

1. Serial transmission
2. Parallel transmission

### 1.1 Serial transmission

Serial transmission is the process of sending data one bit at a time over a communication channel. It is slower than parallel transmission but requires fewer wires.
Most of the communication between devices is done using serial transmission.

### 1.2 Parallel transmission

Parallel transmission is the process of sending multiple bits simultaneously over multiple communication channels. It is faster than serial transmission but requires more wires.

### 1.2 Bit synchronization

Bit synchronization is the process of ensuring that the sender and receiver are synchronized in terms of the timing of the bits being transmitted. It is essential for accurate data transmission.
Bit synchronization is achieved using clock signals that are sent along with the data.

Example:
A bit is said to be transmitted at the rising edge of the clock signal.
then the receiver will sample the bit at the rising edge of the clock signal to ensure proper synchronization.

### 1.3 Bit rate control

Bit rate control is necessary to ensure that the sender and receiver are transmitting and receiving data at the same rate. It involves controlling the speed at which data is transmitted over the communication channel.

Different communication channels have different data transmission rates, and bit rate control ensures that the data is transmitted at the correct speed.

### 1.4 Physical topology

Physical topology refers to the arrangement of devices on a network. It defines how devices are connected to each other and how data is transmitted between them.
This layer is responsible for defining the physical topology of the network, such as bus, ring, star, mesh, etc.

### 1.5 Transmission mode

Transmission mode refers to the direction of data flow between devices.
There are two types of transmission modes:

1. Simplex mode
2. Duplex mode

#### 1.5.1 Simplex mode

In this mode the data flows in only one direction, from the sender to the receiver. The receiver cannot send data back to the sender.

Example:
Television, radio, etc.

#### 1.5.2 Duplex mode

In this mode, data can flow in both directions, from the sender to the receiver and vice versa. It allows for bidirectional communication between devices.

Example:
Telephone, computer, etc.

### 1.6 Line configuration

Line configuration refers to the way devices are connected to a communication channel. It defines how data is transmitted between devices and how they are connected to the network.

There are two types of line configurations:

1. Point-to-point
2. Multipoint

#### 1.6.1 Point-to-point

In this configuration, two devices are connected directly to each other using a communication channel. It allows for communication between two devices only.

Example:
Telephone, bluetooth etc.

#### 1.6.2 Multipoint

In this configuration, multiple devices are connected to a single communication channel. It allows for communication between multiple devices on the same network.

Example:
Bus network, ring network, etc.

### 1.7 Multiplexing

Multiplexing refers to the process of combining multiple data streams into a single data stream for transmission over a communication channel. It allows for the efficient use of the communication channel by sharing it among multiple devices.

There are three types of multiplexing:

1. Frequency division multiplexing (FDM)
2. Time division multiplexing (TDM)
3. Code division multiplexing (CDM)

#### 1.7.1 Frequency division multiplexing (FDM)

In this technique, the available bandwidth is divided into multiple frequency bands, and each data stream is assigned a different frequency band for transmission.
Each data stream is transmitted over its allocated frequency band, and the receiver separates the data streams based on the frequency bands.

Example:
Radio broadcasting, cable television, etc.

#### 1.7.2 Time division multiplexing (TDM)

In this technique, the available bandwidth is divided into multiple time slots, and each data stream is assigned a different time slot for transmission.
Each data stream is transmitted over its allocated time slot, and the receiver separates the data streams based on the time slots.

Example:
Telephone networks, digital communication, etc.

#### 1.7.3 Code division multiplexing (CDM)

In this technique, each data stream is assigned a unique code, and all data streams are transmitted simultaneously over the same frequency band.
The receiver uses the unique code to separate the data streams and reconstruct the original data streams.

Example:
CDMA (Code Division Multiple Access) in mobile communication, etc.

## 2. Bandwidth

Bandwidth refers to the maximum data transfer rate of a network or communication channel. It is the amount of data that can be transmitted in a fixed amount of time.
Bandwidth is measured in bits per second (bps), kilobits per second (Kbps), megabits per second (Mbps), etc.

There are two types of bandwidth:

1. Analog bandwidth
2. Digital bandwidth

### 2.1 Analog bandwidth

This refers to the range of frequencies that can be transmitted over an analog communication channel. It is measured in hertz (Hz) and is used in analog communication systems.

Example:
Telephone lines, radio broadcasting, etc.

### 2.2 Digital bandwidth

This refers to the data transfer rate of a digital communication channel. It is measured in bits per second (bps) and is used in digital communication systems.

Example:
Computer networks, internet, etc.

Bandwidth is an essential factor in determining the speed and efficiency of data transmission over a network. Higher bandwidth allows for faster data transmission and better network performance.

| Base Band      | Broad Band        |
| -------------- | ----------------- |
| Single channel | Multiple channels |
| Digital signal | Analog signal     |
| Ethernet       | Cable TV          |

### 2.3 Base Band

Base band is a type of communication channel that carries a single channel of data. It uses digital signaling and is commonly used in computer networks.

### 2.4 Broad Band

Broad band is a type of communication channel that carries multiple channels of data. It uses analog signaling and is commonly used in cable television networks.

## 3. Transmission media

Transmission media refers to the physical medium used to transmit data between devices. It can be classified into two types:

1. Guided media
2. Unguided media

### 3.1 Guided media

Guided media refers to the physical medium that guides the data signals along a specific path. It provides a physical connection between devices and supports data transmission over a communication channel.
Mainly used in wired communication systems.
Examples of guided media include:

- Twisted pair cable
- Coaxial cable
- Fiber optic cable
- Ethernet cable

### 3.2 Unguided media

Unguided media refers to the physical medium that does not guide the data signals along a specific path. It allows data signals to travel freely through the air or space.
Mainly used in wireless communication systems.
Examples of unguided media include:

- Radio waves
- Microwaves
- Infrared waves
