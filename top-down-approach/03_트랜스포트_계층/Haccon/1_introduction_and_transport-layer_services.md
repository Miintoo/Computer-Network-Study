## Overview

A trnsport-layer protocol provides for **logical communication** between application process running on different hosts.

By *logical communication*, we mean that from an application's perspective, it is as if the hosts running the processes were directly connected; in reality, the hosts may be on opposite sides of the planet, connected via numerous routers and a wide range of link types.

Application processes use the logical communication provided by the transport layer to send messages to each other, free from the worry of the details of the physical infrastructure used to carry these messages.

- Whereas transport-layer protocols are implemented in the end systems but not in network routers.
- The transport layer converts the application-layer messages it receives from a sending application process into transport-layer packets, known as **segments** in Internet terminology.

  - This is done by breaking the application messages into smaller chunks and *adding a transport-layer header* to each chunk to create the transport-layer segment.
  - Transport layer then passes the segment to the network layer at the sending end system, where the segment is encapsulated within a network-layer packet (a datagram) and sent to the destination.
  - On the receiving side, the network layer extracts the transport-layer segment from the datagram and passes the segment up to the transport layer.
  - The transport layer then processes the received segment, making the data in the segment available to the receivng application.

![1688054233788](image/1_introduction_and_transport-layer_services/1688054233788.png)

### 3.1.1 Relationship Between Transport and Network Layers

Whereas a trasnport-layer protocol provides logical communication between **processes** running on different hosts, a network-layer protocol provides logical communication between **hosts**.

Certain services can be offered by a transport protocol even when the underlying network protocol doesn't offer the corresponding service at the network layer, such as network protocol loses, garbles, or duplicates packets.

Why transport-layer is logical?

Network layers does not care the quality of message, they just sent out as is. However, transport-layer

정확히 어떤 데이터에 바인딩을 해줘야하는가 등 데이터의 퀄리티에 신경을 쓰기 때문에 logical communication 이라고 부른다.

### 3.1.2 Overview of the Transport Layer in the Internet

Recall that the Internet makes two distinct transport-layer protocols available to the application layer.

- UDP (User Datagram Protocol) provides an unreliable, connectionless service to the invoking application.
- TCP (Transmission Control Protocol) provides a reliable, connection-oriented service to the invoiking application.
- When desigining a network application, developers must specify one of these two transport protocols and this will be selected when creating sockets.
- The terminoloy for transport-layer packet is extremly chaos; In this book we refer both TCP and UDP packets as *segments*, and reserve the tern *datagram* for the network-layer packet.

#### Network-layer protocol

In order to have a breif introduction of UDP and TCP, we have to say a few words about network layer.

Every host has at least one network layer called **IP address (Internet Protocol)**. IP address provides logical communication between hosts.

- The IP addres
- The most fundamental responsibility of UDP and TCP is to extend IP's delivery service between two end systems to a delivery to process-to-process delivery, is called transport-layer **multiplexing** and **demultiplexing**.
- Also, it provides integrity checking by including error-detectno fields in their segments' headers (Error Checking)

#### Introduction of TCP

- **Reliable data transfer**
  - TCP ensures that data is delivered from sending process to receiving process, correctly and in order. TCP thus converts IP's unreliable service between end systems into a reliable data transport service between processes.
  - Flow control, squence numbers, acknowledgements, and timers
- **Congestion control**
  - It prevents any one TCP connection from swamping the links and routers between communicating hosts with an excessive amount of traffic.
  - TCP strives to gve each connection traversing a congested link an equal share of the link bandwidth.
