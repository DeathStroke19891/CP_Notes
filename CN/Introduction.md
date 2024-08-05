# Table of contents

| Sl No. | Topic                                                                     |
| ------ | ------------------------------------------------------------------------- |
| 1      | [Introduction to Computer Networks](#1-introduction-to-computer-networks) |
| 2      | [OSI Model](#2-osi-model)                                                 |

---

## Formulae

| Sl No. | Formula Name  | Formula                    |
| ------ | ------------- | -------------------------- |
| 1      | Star Topology | Number of links = n - 1    |
| 2      | Bus Topology  | Number of links = n - 1    |
| 3      | Ring Topology | Number of links = n        |
| 4      | Mesh Topology | Number of links = n(n-1)/2 |

# 1. Introduction to Computer Networks

What is a network ?
A network is a collection of computers, servers, mainframes, network devices, and other devices connected to one another to allow the sharing of data. An excellent example of a network is the Internet, which connects millions of people all over the world.

## 1.1 Types of Networks

There are different types of networks, depending upon the geographical area they cover. The most common types of networks are:

| Sl No. | Network Type | Description                                                                                                                                     |
| ------ | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 1      | LAN          | Local Area Network (LAN) is a network which is used for a small geographical area. It is used for connecting the devices over a short distance. |
| 2      | WAN          | Wide Area Network (WAN) is a network which is used for a large geographical area. It is used for connecting the devices over a large distance.  |
| 3      | MAN          | Metropolitan Area Network (MAN) is a network which spans entire city. It is used for connecting the devices over a city.                        |
| 4      | WLAN         | Wireless Local Area Network (WLAN) is a type of LAN which uses wireless technology for communication.                                           |
| 5      | SAN          | Storage Area Network (SAN) is a type of network which provides high-speed network for storage devices.                                          |
| 6      | CAN          | Campus Area Network (CAN) is a network of multiple interconnected LANs in a limited geographical area.                                          |
| 7      | PAN          | Personal Area Network (PAN) is a network of devices used for communication among the devices close to one person.                               |

## 1.2 Network Topologies

Network topology is the arrangement of the various elements (links,nodes etc) of a network.
Physical Topologies: These are the physical layout of the network.
Logical Topologies: These are the logical layout of the network regarding how data is transferred in the network.

1. Star Topology
   Star topology is a network topology where each individual piece of a network is attached to a central node, often a hub or switch. The central node is the brain of the network and acts as a mediator to all the connected devices.
   If there is a failure of central node, the whole network goes down.

   - **Advantages**:
     - Easy to install and wire.
     - Easy to detect faults and to remove parts.
     - Easy to upgrade.
   - **Disadvantages**:
     - If the central node fails, the whole network goes down.
     - Performance is based on the central node.
     - Expensive to install.

![Star topology](https://media.geeksforgeeks.org/wp-content/uploads/20201023231032/14064-300x226.png)

2. Bus Topology
   Bus topology is a network type in which every computer and network device is connected to a single cable. When it has exactly two endpoints, then it is called Linear Bus topology.
   The central cable is the backbone of the network and is known as Bus.

   - **Advantages**:
     - Easy to connect a computer or peripheral to a linear bus.
     - Requires less cable length than a star topology.
     - Easy to detect faults.
   - **Disadvantages**:
     - Entire network shuts down if there is a break in the main cable.
     - Terminators are required at both ends of the backbone cable.
     - Difficult to identify the problem if the entire network shuts down.

![bus topology](https://media.geeksforgeeks.org/wp-content/uploads/20240221113117/3-55.png)

3. Ring Topology
   In a ring network, every device has exactly two neighbors for communication purposes. All messages travel through a ring in the same direction (either "clockwise" or "counterclockwise").

   - **Advantages**:
     - Easy to install and reconfigure.
     - Easy to detect faults.
     - No network traffic jams.
   - **Disadvantages**:
     - If one device fails, the whole network goes down.
     - Expensive to install.
     - Performance is based on the central node.

![Ring topology](https://upload.wikimedia.org/wikipedia/commons/d/db/NetworkTopology-Ring.png)

4. Mesh Topology
   Mesh topology is a type of networking where all nodes cooperate to distribute data amongst each other. This topology is used in wireless networks, WANs, and the internet.

   - **Advantages**:
     - Data can be transmitted from different devices simultaneously.
     - Fault detection is easy.
     - Privacy and security.
   - **Disadvantages**:
     - Installation and configuration are difficult.
     - Expensive to install.
     - Cabling cost is high.

![Mesh topology](https://www.computerhope.com/jargon/m/mesh.png)

5. Tree Topology
   Tree topology is a combination of the bus and star network topology. It is a hierarchical topology that is divided into different levels.

   - **Advantages**:
     - Easy to extend.
     - Easy to detect faults.
     - Easy to manage.
   - **Disadvantages**:
     - If the backbone fails, the whole network goes down.
     - Expensive to install.
     - Performance is based on the central node.

6. Hybrid Topology
   Hybrid topology is a combination of two or more different types of network topologies. It is used in large networks where different types of network topologies are interconnected.

   - **Advantages**:
     - Scalable.
     - Reliable.
     - Secure.
   - **Disadvantages**:
     - Complex to design and implement.
     - Expensive to install.
     - Difficult to manage.

> Formulas for calculating the number of links in a network:

1. **Star Topology**:

   - Number of links = n - 1

2. **Bus Topology**:

   - Number of links = n - 1

3. **Ring Topology**:

   - Number of links = n

4. **Mesh Topology**:
   - Number of links = n(n-1)/2

Where `n` is the number of devices in the network.

## 1.3 Network Devices

| Sl No. | Device Type | Description                                                                                                                                                                                          |
| ------ | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.     | Hub         | Hub is a device that connects multiple Ethernet devices on a single network. When a packet arrives at one port, it is copied to the other ports so that all segments of the LAN can see all packets. |
| 2.     | Switch      | A switch forwards data only to the device for which it is intended. It learns the MAC address of the device connected to it and then sends the data to the correct port.                             |
| 3.     | Router      | A router is a device that forwards data packets between computer networks. Routers perform the traffic directing functions on the Internet.                                                          |

---

# 2. OSI Model

Open Systems Interconnection (OSI) model is a conceptual framework that standardizes the functions of a telecommunication or computing system into seven abstraction layers.

| Sl No. | Layer Name   | Description                                                                                                                                                                                                |
| ------ | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1.     | Application  | The application layer is the top-most layer of the OSI model. It provides the interface between the applications we use to communicate and the underlying network over which our messages are transmitted. |
| 2.     | Presentation | The presentation layer is responsible for the delivery and formatting of information to the application layer for further processing or display.                                                           |
| 3.     | Session      | The session layer is responsible for establishing, maintaining, and terminating connections between applications.                                                                                          |
| 4.     | Transport    | The transport layer is responsible for error-checking and data recovery. It ensures complete data transfer.                                                                                                |
| 5.     | Network      | The network layer is responsible for routing packets to the correct destination.                                                                                                                           |
| 6.     | Data Link    | The data link layer is responsible for the node-to-node delivery of the message.                                                                                                                           |
| 7.     | Physical     | The physical layer is responsible for the transmission and reception of unstructured raw data between a device and a physical transmission medium.                                                         |

This is a theoretical model and is not implemented in the real world. The TCP/IP model is used in the real world.
In the TCP/IP Model , certain layers of the OSI model are combined.

```
OSI MODEL         TCP/IP MODEL

Application
Presentation
Session             Application

Transport           Transport

Network             Network

Data Link
Physical            Physical
```

OSI model serves as a guideline for understanding and designing a network architecture that is flexible, robust, and interoperable.
It is a conceptual framework used to understand the working of the network.
It is validated by the International Standards Organization (ISO).
