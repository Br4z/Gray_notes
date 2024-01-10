---
id: 44vqmdxs6zo7jln0syjxas4
title: 1-Conceptos básicos
desc: ''
updated: 1704854772071
created: 1704299320395
---

## 1 - Direcciones IP (IPV4 e IPV6)

### IP

IP is short for Internet Protocol, which is a protocol for the communication of data across a network. An IP address is a number that uniquely identifies a device connected to a network that uses IP. An IP address has two main functions: host or network interface identification and location addressing.

#### IPv4

uses 32-bit (four octets of $8$ bits) addresses, which are written as four numbers separated by periods, such as `172.16.254.1`. Each number can range from $0$ to $255$ ($2^4$), which means there are $4.294.967.296$ ($2^{ 32 }$) possible IPv4 addresses.

#### IPv6

uses 128-bit (which consists of eight groups of four hexadecimal digits) addresses, which are written as eigth numbers separated by colons, such as `3001:0da8:75a3:0000:0000:8a2e:0370:7334`. Each number can range from $0$ to $65535$ (`FFFF`), which means there are $40.282. 366.920.938.463.463.374.607.431.768.211.456$ ($2^{ 128 }$) possible IPv6 addresses.

> The ratio between a hexadecimal digit and a binary digit is $4$, so we can represent $2^{ 128 }$ ($2^{ 4 * 4 * 8 }$) addresses in IPv6, which is equal to $2^{ 96 } = \frac{ 2^{ 128 } }{ 2^{ 32 } }$ times IPv4.

## 2 - Direcciones MAC (OUI y NIC)

A MAC address, which stands for Media Access Control Address, is a unique $48$-bit ($12$ hexadecimal numbers) hardware number of a computer that is embedded into a network card (known as a Network Interface Card) during manufacturing. The MAC Address is also known as the Physical Address of a network device.

The First 6 digits of the MAC Address identify the manufacturer, called the OUI (Organizational Unique Identifier). The rightmost six digits represent the Network Interface Controller, which is assigned by the manufacturer.

> The IEEE Registration Authority Committee assigns these MAC prefixes to its registered vendors.

The MAC address is represented by Colon-Hexadecimal (`XX:XX:XX:XX:XX:XX`) notation. But this is just a conversion, not mandatory.

> With the `macchanger` package, we can print known vendors with the `-l` (`macchanger -l`) option.

## 3 - Protocolos comunes (TCP, UDP) y el famoso Three-Way Handshake

Both protocols let two hosts connect and exchange data streams.

### TCP (Transmission Control Protocol)

It guarantees the delivery of data and packets in the same order as they were sent.

TCP's role is to ensure the packets are reliably delivered and error-free. TCP implements congestion control, which means the initial requests start small and increase in size according to the levels of bandwidth the computers, servers, and network can support.

#### Three-Way Handshake

The three messages transmitted by TCP to negotiate and start a TCP session are nicknamed **SYN**, **SYN-ACK**, and **ACK** for SYNchronize, SYNchronize-ACKnowledgement, and ACKnowledge respectively. The three-message mechanism is designed so that two computers that want to pass information back and forth to each other can negotiate the parameters of the connection before transmitting data.

### UDP (User Datagram Protocol)

It is used together with IP for sending data when transmission speed and efficiency matter more than security and reliability.

UDP uses a simple connectionless communication model with a minimum of protocol mechanisms. UDP provides checksums for data integrity and port numbers for addressing different functions at the source and destination of the datagram. It has no handshaking dialogues and thus exposes the user's program to any unreliability of the underlying network; There is no guarantee of delivery, ordering, or duplicate protection.

## 4 - El modelo OSI – ¿En qué consiste y cómo se estructura la actividad de red en capas?

The OSI (Open Systems Interconnection) model, created in 1984 by the ISO (International Organization for Standardization), is a reference framework that explains the process of transmitting data between computers. It is divided into seven layers that work together to carry out specialized network functions, **allowing for a more systematic approach to networking**.

1. Physical Layer: is responsible for the actual physical connection between the devices. The physical layer contains information in the form of bits. It is responsible for transmitting individual bits from one node to the next. When receiving data, this layer will get the signal received, convert it into 0s and 1s and send them to the Data Link layer, which will put the frame back together.

2. Data Link Layer: is responsible for the node-to-node delivery of the message. The main function of this layer is to make sure data transfer is error-free from one node to another over the physical layer.

3. Network Layer: works for the transmission of data from one host to another located in different networks. It also takes care of packet routing, i.e. selection of the shortest path to transmit the packet from the number of routes available.

4. Transport Layer: provides services to the application layer and takes services from the network layer. The data in the transport layer is referred to as Segments. It is responsible for the End to End Delivery of the complete message. The transport layer also provides acknowledgment of successful data transmission and re-transmits the data if an error is found.

5. Session Layer: is responsible for the establishment of connections, maintenance of sessions, and authentication, and also ensures security.

6. Presentation Layer: is also called the **Translation layer**. The data from the application layer is extracted here and manipulated as per the required format to transmit over the network. .

7. Application Layer: is implemented by the network applications. These applications produce the data, which has to be transferred over the network. This layer also serves as a window for the application services to access the network and for displaying the received information to the user.

| Layer No |     Layer Name     |                                            Responsibility                                             | Information form (data unit) |      Device or Protocol      |
|:--------:|:------------------:|:-----------------------------------------------------------------------------------------------------:|:----------------------------:|:----------------------------:|
|    7     | Application Layer  |                   Helps in identifying the client and synchronizing communication.                    |           Message            |             SMTP             |
|    6     | Presentation Layer | Data from the Application Layer is extracted and manipulated in the required format for transmission. |           Message            |       JPEG, MPEG, GIF        |
|    5     |   Session Layer    |          Establishes connection, maintenance, ensures authentication, and ensures security.           |           Message            |           Gateway            |
|    4     |  Transport Layer   |               Take service from Network Layer and provide it to the Application Layer.                |           Segment            |           Firewall           |
|    3     |   Network Layer    |             Transmission of data from one host to another, located in different networks.             |            Packet            |            Router            |
|    2     |  Data Link Layer   |                                  Node to node delivery of messages.                                   |            Frame             |        Switch, Bridge        |
|    1     |   Physical Layer   |                          Establishing physical connections between devices.                           |             Bits             | Hub, repeater, modem, cables |

## 5 - Subnetting – ¿Qué es y cómo se interpreta una máscara de red?

### Subnetting

Dividing a large block of addresses into several contiguous sub-blocks and assigning these sub-blocks to different smaller networks is called subnetting. It is a practice that is widely used when classless addressing is done.

A subnet or subnetwork is a network inside a network. Subnets make networks more efficient. Through subnetting, network traffic can travel a shorter distance without passing through unnecessary routers to reach its destination.

### Classful Addressing

The 32-bit IP address is divided into five subclasses.

1. Class A.

2. Class B.

3. Class C.

4. Class D.

5. Class E.

> Classes D and E are reserved for multicast and experimental purposes respectively.

---

The IPv4 address is divided into two parts:

1. Network ID.

2. Host ID.

> While finding the total number of host IP addresses, 2 IP addresses are not counted and are therefore, decreased from the total count because the first IP address of any network is the network number and whereas the last IP address is reserved for broadcast IP.

#### Class A

IP addresses belonging to class A are assigned to networks that contain numerous hosts. The higher-order bit of the first octet in class A is always set to `0`.

- Network ID is 8 bits (1 byte) long ($2^7 = 128$).

- Host ID is 24 bits (3 bytes) long ($2^{ 24 } – 2 = 16.777.214$).

The default subnet mask for Class A is `255.X.X.X`. IP addresses belonging to class A ranges from `1.0.0.0` – `126.255.255.255` (`00000001.0.0.0` - `01111110.255.255.255`).

##### Exceptions (Class A)

- `127.X.X.X` is reserved for loopback.

- `0.X.X.X` is reserved for the default network.

#### Class B

IP addresses belonging to class B are assigned to networks that range from medium-sized to large-sized networks. The higher-order bits of the first octet of IP addresses of class B are always set to `10`.

- Network ID is 16 bits long ($2^{ 14 } = 16.384$).

- Host ID is 16 bits long ($2^{ 16 } – 2 = 65.534$).

The default subnet mask for class C is `255.255.X.X`. IP addresses belonging to class B ranges from `128.0.0.0` – `191.255.255.255` (`10000000.0.0.0` - `10111111.255.255.255`).

#### Class C

IP addresses belonging to class C are assigned to small-sized networks. The higher-order bits of the first octet of IP addresses of class C are always set to `110`.

- Network ID is 24 bits long ($2^{ 22 } = 2.097.152$).

- Host ID is 8 bits long ($2^{ 8 } – 2 = 254$).

The default subnet mask for class C is `255.255.255.X`. IP addresses belonging to class C range from `192.0.0.0` – `223.255.255.255` (`11000000.0.0.0` - `11011111.255.255.255`).

#### Class D

IP addresses belonging to class D are reserved for multi-casting. The higher-order bits of the first octet of IP addresses belonging to class D are always set to `1110`.

Class D does not possess any subnet mask. IP addresses belonging to class D range from `224.0.0.0` – `239.255.255.255` (`1110.0.0.0` - `11101111.255.255.255`).

#### Class E

IP addresses belonging to class E are reserved for experimental and research purposes. The higher-order bits of the first octet of class E are always set to `1111`. IP addresses of class E range from `240.0.0.0` – `255.255.255.254` (`11110000.0.0.0` - `11111111.255.255.254`). This class does not have any subnet mask.

#### Problems with Classful Addressing

The problem with this classful addressing method is that millions of class A and class B addresses are wasted, whereas the number of addresses available in class C is so small that it cannot cater to the needs of organizations. Class D addresses are used for multicast routing and are therefore available as a single block only. Class E addresses are reserved.

Since there are these problems, Classful networking was replaced by Classless Inter-Domain Routing (CIDR) in 1993.

## 6 - Problems with Classful Addressing

### Classless Addressing

To reduce the waste of IP addresses in a block, we use sub-netting. What we do is use host id bits as net id bits of a classful IP address. We give the IP address and define the number of bits for the mask along with it (usually followed by a `/`).

- Number of subnets : $2^{ \text{ given bits for mask } – \text{ No. of bits in default mask } }$.

- Subnet address: AND result of subnet mask and the given IP address.

- Broadcast address: by putting the host bits as 1 and retaining the network bits as in the IP address (the network address used to send packets to all hosts on the subnet).

- Number of hosts per subnet: $2^{ 32 – \text{ given bits for mask } } – 2$.

- First Host ID : $\text{ subnet address } + 1$ (adding one to the binary representation of the subnet address).

- Last Host ID : $\text{ subnet address } + \text{ number of hosts }$.

> Also know as CIDR (Classless Inter Domain Routing)

#### Rules (Classless Addressing)

- All IP addresses must be contiguous.

- Block size must be the power of 2 ($2^n$).

## 7 - Subnetting – Máscaras de subred, tipos de clase e interpretación de prefijos de red

### No class and subnet mask `X.0.0.0`

| CIDR |     Hosts     |
|:----:|:-------------:|
| `/1` | 2.147.483.648 |
| `/2` | 1.073.741.824 |
| `/3` |  536.870.912  |
| `/4` |  268.435.456  |
| `/5` |  134.217.728  |
| `/6` |  67.108.864   |
| `/7` |  33.554.432   |
| `/8` |  16.777.216   |

### Class A and subnet mask `255.X.0.0`

| CIDR  |   Hosts   |
|:-----:|:---------:|
| `/9`  | 8.388.608 |
| `/10` | 4.194.304 |
| `/11` | 2.097.152 |
| `/12` | 1.048.576 |
| `/13` |  524.288  |
| `/14` |  262.144  |
| `/15` |  131.072  |
| `/16` |  65.536   |

### Class B and subnet mask `255.255.X.0`

| CIDR  | Hosts  |
|:-----:|:------:|
| `/17` | 32.768 |
| `/18` | 16.384 |
| `/19` | 8.192  |
| `/20` | 4.096  |
| `/21` | 2.048  |
| `/22` | 1.024  |
| `/23` |  512   |
| `/24` |  256   |

### Class C and subnet mask `255.255.255.X`

| CIDR  | Hosts |
|:-----:|:-----:|
| `/25` |  128  |
| `/26` |  64   |
| `/27` |  32   |
| `/28` |  16   |
| `/29` |   8   |
| `/30` |   4   |
| `/31` |   2   |
| `/32` |   1   |

---

|            CIDR            |  X  |
|:--------------------------:|:---:|
| `/1`, `/9`, `/17` y `/25`  | 128 |
| `/2`, `/10`, `/18` y `/26` | 192 |
| `/3`, `/11`, `/19` y `/27` | 224 |
| `/4`, `/12`, `/20` y `/28` | 240 |
| `/5`, `/13`, `/21` y `/29` | 248 |
| `/6`, `/14`, `/22` y `/30` | 252 |
| `/7`, `/15`, `/23` y `/31` | 254 |
| `/8`, `/19`, `/24` y `/32` | 255 |

## 9 - Subnetting – Redes extrañas y casos particulares

Exercises

- `13.13.13.13/13`.

	- Subnet address.

		$$
		\begin{array}{lllll}
				&13.  &00001101. &13. &13 \\
				&255. &11111000. &0.  &0 \\
			=   &13.  &00001000. &0.  &0 = 13.8.0.0
		\end{array}
		$$

	- Broadcast address: $13.00001111.255.255 = 13.15.255.255$.

	- Number of hosts per subnet: $524.288$.

	- First Host ID: $13.8.0.1$.

	- Last Host ID: $13.15.255.254$.

- `10.10.0.12/15`.

	- Subnet address.

		$$
		\begin{array}{lllll}
				&10.  &00001010. &0. &12 \\
				&255. &11111110. &0. &0 \\
			=   &10.  &00001010. &0. &0 = 10.10.0.0
		\end{array}
		$$

	- Broadcast address: $10.00001011.255.255 = 10.11.255.255$.

	- Number of hosts per subnet: $131.072$.

	- First Host ID: $10.10.0.1$.

	- Last Host ID: $10.11.255.254$.

- `192.168.1.45/29`.

	- Subnet address.

		$$
		\begin{array}{lllll}
				&192. &168.  &1.   &00101101 \\
				&255. &255.  &255. &11111000 \\
			=   &192. &168.  &255. &00101000 = 192.168.1.40
		\end{array}
		$$

	- Broadcast address: $192.168.1.00101111 = 192.168.1.47$.

	- Number of hosts per subnet: $8$.

	- First Host ID: $192.168.1.41$.

	- Last Host ID: $192.168.1.47$.
