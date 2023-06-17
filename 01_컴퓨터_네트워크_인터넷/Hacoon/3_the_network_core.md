## The Network Core

Mesh of packet switches(routers) and links that interconnects the Internet's end systems.

Router는 작은 스페셜한 컴퓨터라고 생각하면 된다. 그래서 CPU, 메모리 등을 탑재하고 있다.

![1686898337610](image/3_the_network_core/1686898337610.png)

### 1.3.1 Packet Switching

In a network application, end systems exchange messages with each other. Messages can contain any types of data, including email message, image, and audio files.

To send a message from a source end system to a destination end system, the source breaks long messages into smaller chunks of data known as **packets**.

Between source and destination, each packet travels through communication links and packet swithes.

#### Two Key Network-Core Functions

- Forwarding (or Switching)
  - **Local** Action: move arriving packets from router's imput link to appropriate router output link
  - Micro concepts
- Routing
  - **Global** Action: determine source-destination paths taken by packets (전체 path를 확인하여 최적의 경로를 탐색)
  - Routing Algorithms

Packet switch는 다음과 같이 작동 된다.

1. packet 헤더의 destination address를 확인 한다.
2. routing algorithm으로 해당 destination address와 동일한 communication link를 확인한다.
   * Routing Algorithm은 packet이 정해진 address로 갈 수 있는 최단 거리를 계산한다.
3. 해당 communication link로 packet을 내보낸다.

![1686898462819](https://file+.vscode-resource.vscode-cdn.net/Users/minha/Documents/5-study/Computer-Network-Study/Chapter_1/Hacoon/image/3_the_network_core/1686898462819.png)

#### Store-and-Forward Transmission

Store-and-Forward Transmission means that the packet switch **must receive the entire packet before** it can begin to transmit the first bit of the packet onto the outbound link.

Most packet switches use store-and-forward transmission at the inputs to the links.

![1686898269457](https://file+.vscode-resource.vscode-cdn.net/Users/minha/Documents/5-study/Computer-Network-Study/Chapter_1/Hacoon/image/3_the_network_core/1686898269457.png)

#### Queuing Delays and Packet Loss

Queuing occurs when work arrives faster than it can be serviced.

Each packet switch has multiple links attached to it. For each attached link, the packet switch has an **output buffer** (or output queue), which stores packets that the router is about to send into that link.

The output buffers play a key role in packet switching. If an arriving packet needs to be transmitted onto a link but finds the link busy with the transmission of another packet, the arriving packet must wait in the output buffer.

Thus, in addition to the store-and-forward delays, packets suffer output buffer **queuing delays**.

Since the amount of buffer space is finite, an arriving packet may find that the buffer is completely full with other packets waiting for transmission. In this case, **packet loss** will occur - either the arriving packet or one of the already-queued packets will be dropped.

![1686901585907](image/3_the_network_core/1686901585907.png)

#### Forwarding Tables and Routing Protocols

How does the router determine which link it should forward the packet onto? Packet forwarding is actually done in different ways in different types of computre networks.

In the Internet, every end system has an address called an **IP address**. When a source end system wants to send a packet to a destination end system, the source includes the destinatoin's **IP address in the packet's header.**

As with postal addresses, this address has a *hierarchical structure*. When a packet arrives at a router in the network, the router examines a portion of the packet's destination address and forwards the packet to an adjacent router.

More specifically, each router has a **forwarding table** that maps destinatoin address, to find the apprppriate outboud link. The router then directs the packet to this outbound link.

### 1.3.2 Circuit Switching

Alternative to packet switching. Commonly used in traditional telephone networks.

전화기만 있던 시절에 사용하던 switching 방법. 현재 보편적으로는 packit switching이 사용되고 있다.

There are two fundamental approaches to moving data through a network of links and switches: **circuit switching** and **packet switching**.

In circuit-switched networks, the resources needed along a path to provide for communication between the end systems **are reserved** for the duration of the communication session between the end systems.

One person wants to send information to another over a telephone network. Before the sender can send the information, the network must establish a connection between the sender and the receiver. This is a bona fide connection for which the switches on the path between the sender and receiver *maintain connection state for that connection*.

In the jargon of telephony, this connection is called a **circuit**. When the network establishes the circuit, it also reserves a constant transmission rate in the network's links for the duration of the connection. Therefore, the sender can transfer the data to the receiver at the *guaranteed constant rate*.

- The hosts (PCs and workstations) are each directly connected to one of the switches.
- When two hosts want to communicate, the network establishes a dedicated **end-to-end connection** between the two hosts.
- The host must reserve one circuit on each of two links

![1686903264242](image/3_the_network_core/1686903264242.png)

#### Multiplexing in Circuit-Switched Networks

##### Frequency Division Multiplexing (FDM)

주파수 대역을 나누어 동시에 통신 가능. ex) 라디오 방송

**The frequency** spectrum of a link is divided up among the connections established accross the link. Specifically, the link dedicates a frequency band to each connectino for the duration of the connection. Each call allocted its own band.

##### Time-Division Multiplexing (TDM)

시간대별로 나누어 통신

**Time** is divided into frams of fixed duration, and each fram is divided into a fixed number of time slots.

When the network establishes a connection across a link, the network dedicates one time slot in every frame to this connection . These slots are dedicated for the sole use of that connection, with one time slot available for use to transmit the connection's data.

![1686904265159](image/3_the_network_core/1686904265159.png)

#### Packet Switching vs Circuit Switching

Critics of packetswitching have often argued that Packet switching is not suitable due to variable and unpredictable queuing delays. However, propponents of packet switching argue the below:

- It offers better sharing of transmission capacity than citcuit switching
- More efficient, and less costly to implement than circuit switching

Why is packet switching more efficient?

Example) how many users can use this network under circuit-switching nd packet switching?

Suppose users share a 1 Mbps link. Also suppose that each user alternates between periods of activity, when a user generates data at a constant rate of 100 kbps, and periods of inactivity, when a user generates no data. Suppose further
that a user is active only 10 percent of the time.

- Circuit-switching: 10 users with TDM
  - 100 kbps must be reserved for each user at all times.
- Packet-switching: with 35 users
  - the probability that there are 11 or more simultaneously active users is approximately 0.0004.

They also highlight the crucial difference between the two forms of sharing **a link’s transmission rate among multiple data streams**. 

Circuit switching *pre-allocates* use of the transmission link regardless of demand, with allocated but unneeded link time going unused.

Packet switching on the other hand allocates link use *on demand*. Link transmission capacity will be shared on a packet-by-packet basis only among those users who have packets that need to be transmitted over the link.

### 1.3.3 A Network of Networks


|  |  |  |
| - | - | - |
