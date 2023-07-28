## **Overview**

To concreate the discusion, we will discuss the basic transport-layer service in the context of the Internet.

At the destincation host, the transport layer receives segments from the network layer just below. The transport layer has the responsibility of delivering the data in these segments to the appropriate application process running in the host.

### Summary of multiplexing and demultiplexing

- A process (as part of a network application) can have one or more sockets, doors through which data passes from the network to the process and through which data passes from the process to the network.
- Thus, the transport layer in the receiving host does not actually deliver data directly to a process, but instead to an intermediary socket.
- Because at any given time there can be more than one socket in the receiving host, each socket has a unique identifier. The format of the identifier depends on whether the socket is a UDP or a TCP socket.
