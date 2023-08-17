## Chapter Goal

- Look into a big picture of Computer Network
- Introduction to terminology

## Overview

- What is the Internet?
- What is a protocol?
- Network edge: hosts, access network, physical media
- Network core: packet/circuit switching, internet structure
- Performance: loss, delay, throughtput
- Protocol layers, service models
- Security
- History

### 1.1.1 A Nuts-and-Bolts Description (물리적 측면)

#### Hosts or Endsystems

- Hosts = Endsystems
- 인터넷 망의 끝단
- 노트북, 스마트폰, 컴퓨터, TV, 게임 콘솔 등

#### Packet Switches

- Packet: 데이터 전송을 위한 가장 작은 단위의 데이터
- When one end system has data to send to another end system, the sending end segments the data and adds header bytes to each segment
- The resulting Packages of information
- Packets are sent through the network to the destination end system, where they arereassembled into the original data
- Packet Switch: 원하는 목적지로 데이터의 묶음을 전달.

  - Packet switch takes a packet arriving on one of its incoming comunication links and forwads that packet on one of its outgoing communication links
  - Routers and Link-layer switches are the most prominent type

#### Communication Links

- 와이파이, ethernet, 구리선, 라디오, coaxial cable(동축 케이블) 등
- transmission rate: bandwidth (네트워크 대역폭). 주로 Mbps, Gbps 단위 사용.

#### Networks

- a collection of devices, routers, linkes
- Typically, managed by organizations

#### Internet

- Network of networks:
- Internet Service Providers (ISPs)
  - KT, SK 브로드밴드 등

#### Protocols

- 인터넷 통신 규약: 이 규약에 맞지 않으면 인터넷 통신 불가능
- End systems, packet switches, and other pieces of the internet run protocols that control the sending, receiving of informations within the Internet
- **TCP/IP** are the most important protocols in th Internet
- HTTPS, streaming video, Skype, TCP/IP,

#### Internet Standards

- IETF(Internet Engineering Task Force): Internet standards are developed by the IETF
- RFC(Request for Comments): The IETF standards documents are called RFCs

![1686889890014](image/what_is_the_internet/1686889890014.png)

### 1.1.2 A Service Description (서비스 측면)

#### Infrastructure

- Provides services to applications
- **Internet applications run on end systems**: they do not run in the packet switches in the network core, Although, packet switches faciliate the exchange of data among end systems, they are not concerned with the application that is the source or sink of data
- Email, web surfing, games, e-commerces, social medias

#### Socket Interface

- Specifies how a program running on one end system asks the Internet infrastructure to deliver data to a specific destination program running on another end system
- This Internet socket interface is *a set of rules* that the sending program must follow so that the Internet can deliver the data to the destination program

### 1.1.3 What is a protocol?

#### A Human Analogy

Example.

 Consider what you do when you want to ask someone for the time of day

1. Offer a greeting (the first 'Hi')
2. Response with 'Hi' in a good manner
   * Implicitly, one then takes a response 'Hi' as an indication that one can proceed and ask for the time of day
   * A different response might indicate an unwillingness or inability to communicate. (Don't bother me or I don't speak English) In this case, the human protocol would be not to ask for the time of day

If people run different protocols, the protocols do not interoperate and no useful work can be accomplished.

![1686896774777](image/what_is_the_internet/1686896774777.png)

#### Network Protocols

A protocol defines the format and the order of messages exchanged between two or more communicating entities, as well as the actions taken on the transmission and/or receipt of a message or other event

- The entities exchanging messages and taking actions are hardware or software components of some devices
- All activity in the Internet that involves two or more communicating remote entities is governed by a protocol

![1686896757418](image/what_is_the_internet/1686896757418.png)
