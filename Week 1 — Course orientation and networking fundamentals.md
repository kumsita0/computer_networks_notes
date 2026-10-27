# Week 1 — Computer Networks and the Internet

**Level:** Beginner  
**Chapter:** 1  
**Estimated study time:** 45–60 minutes  
**Status:** Study notes and exam revision

## Learning Objectives

By the end of this lesson, you should be able to:

- Explain what a computer network and the Internet are.
- Identify clients, servers, routers, switches, and protocols.
- Explain how data travels from your computer to a web server.
- Describe the five-layer Internet protocol model.
- Understand the network edge, network core, and access networks.
- Explain packet switching and basic network performance.
- Calculate transmission delay and propagation delay.
- Answer fundamental Computer Networks exam questions.

---

## Part 1 — What Is a Computer Network?

A **computer network** is a group of connected devices that communicate and share information or resources.

Examples include:

- Your laptop connecting to your home Wi-Fi.
- Your phone sending a WhatsApp message.
- A college computer accessing an online assignment.
- A bank server communicating with an ATM.

At home, your laptop and phone connect to a Wi-Fi router. The router connects your devices to your Internet service provider (ISP), which provides access to the wider Internet.

### Important networking vocabulary

| Term | Meaning |
|---|---|
| Client | A device or program requesting a service |
| Server | A computer or program providing a service |
| Network | Connected devices that communicate |
| Router | Forwards packets between networks |
| Switch | Connects devices within a local network |
| ISP | An organization providing Internet access |
| Protocol | Rules that devices follow to communicate |
| Packet | A unit of data sent across a network |
| Host | An end system that sends or receives data |
| IP address | A logical address used to identify a network interface |
| Bandwidth | The capacity of a communication link, often measured in bits per second |
| Throughput | The actual rate of successful data delivery |

**Exam tip:** A protocol is a set of rules defining how communicating devices exchange information. Examples include HTTP, TCP, and IP.

## Part 2 — What Is the Internet?

The Internet is a **global network of interconnected networks**.

It is not one giant computer. It consists of connected devices, routers, servers, communication links, and networks operated by different organizations.

### Major components of the Internet

1. **End systems:** Laptops, smartphones, and servers that run applications.
2. **Communication links:** Fiber-optic cables, copper cables, and wireless connections.
3. **Packet switches:** Devices such as routers that forward packets and switches that forward frames.
4. **ISPs:** Organizations that provide Internet connectivity.
5. **Protocols:** Rules that allow different systems to communicate.

### The Internet versus the World Wide Web

- **Internet:** The underlying global networking infrastructure.
- **World Wide Web (WWW):** A collection of linked resources accessed over the Internet, commonly through HTTP or HTTPS.

Email, online gaming, and other applications also use the Internet, even when they are not Web browsing applications.

## Part 3 — How Data Travels Across the Internet

Let's use a simple example: opening a website.

1. **Your laptop:** You enter a website address in your browser.
2. **DNS:** Your computer obtains the IP address associated with the domain name, if it is not already available from a cache.
3. **Local network:** Your request travels through Wi-Fi or Ethernet.
4. **Router and ISP:** Packets are forwarded toward the destination.
5. **Internet routers:** Routers forward packets between networks.
6. **Web server:** The server receives and processes the request.
7. **Response:** Data returns to your device, and the browser displays the website.

The exact path can vary. A website may also use caches, content delivery networks, proxies, or other intermediary services.

### What is a protocol?

Computers need agreed-upon rules to exchange information.

Think of two people communicating in different languages. They need a shared language or a translation method to understand each other.

Network protocols serve a similar purpose.

| Protocol | Main purpose |
|---|---|
| HTTP | Exchanges Web application messages |
| HTTPS | Protects HTTP communication using TLS |
| TCP | Provides a reliable, ordered byte stream |
| UDP | Sends datagrams without TCP-style delivery guarantees |
| IP | Provides addressing and packet forwarding between networks |
| DNS | Provides domain-name resolution and other naming information |

These protocols perform different jobs and often work together.

## Part 4 — The Five-Layer Internet Model

A key concept in Chapter 1 is the layered architecture of computer networks.

| Layer | Examples | Main responsibility |
|---|---|---|
| Application | HTTP, DNS, SMTP | Supports network applications |
| Transport | TCP, UDP | Communication between application processes |
| Network | IP | Addressing and forwarding packets between networks |
| Link | Ethernet, Wi-Fi | Transfers frames over a local link |
| Physical | Copper, fiber, radio signals | Transmits bits as physical signals |

Remember the layers from top to bottom:

**Application → Transport → Network → Link → Physical**

Each layer provides services to the layer above it and uses services from the layer below it.

### Example: Sending a web request

- The application layer creates an HTTP request.
- The transport layer carries the application data using TCP or another appropriate transport.
- The network layer adds IP information.
- The link layer prepares a frame for the next network hop.
- The physical layer transmits the bits.

At the receiving end, the data is processed through the protocol layers.

### What is encapsulation?

**Encapsulation** occurs when protocol layers add control information to data as it moves down the protocol stack.

A simplified representation is:

```text
Application data
       |
       v
Transport header + application data
       |
       v
IP header + transport data
       |
       v
Link header + IP packet + link trailer
       |
       v
Bits transmitted as physical signals
```

At each router, the link-layer frame is processed. The router forwards the IP packet using an appropriate outgoing link, where a new link-layer frame is created.

**Exam tip:** Know the difference between a transport-layer segment or datagram, an IP packet, and a link-layer frame.

## Part 5 — Network Edge and Network Core

### 5.1 Network edge

The network edge contains end systems, also called hosts, that run applications.

Examples include:
- Your laptop
- Your smartphone
- A university web server
- A cloud application server

A host may act as a client, a server, or both.

### 5.2 Network core

The network core consists of interconnected routers and communication links that carry data between networks.

Its main purpose is to forward packets toward their destinations.

### 5.3 Access networks

An access network connects an end system to its first router or to the wider network.

Common access technologies include:

- **Ethernet:** Wired local-area connectivity.
- **Wi-Fi:** Wireless local-area connectivity.
- **DSL:** Broadband access using telephone-line infrastructure.
- **Cable Internet:** Broadband access using cable infrastructure.
- **Fiber:** High-capacity optical communication.
- **Cellular:** Wireless access through mobile network infrastructure.

### 5.4 Transmission media

**Guided media** carry signals through a physical path.

Examples:
- Twisted-pair copper cable
- Coaxial cable
- Fiber-optic cable

**Unguided media** transmit signals through space.

Examples:
- Wi-Fi radio signals
- Cellular radio signals
- Satellite communication

Fiber supports high data rates over long distances and is relatively resistant to electromagnetic interference. Wireless communication supports mobility but may be affected by interference, obstacles, and signal strength.

## Part 6 — Packet Switching

Packet switching is a fundamental technique used by the Internet.

A message is divided into smaller units called **packets**. Packets are forwarded through communication links and routers toward their destination.

### How packet switching works

1. An application generates data.
2. Protocols divide or encapsulate the data into appropriate units.
3. Packets travel over shared network links.
4. Routers examine packet headers and select outgoing links.
5. The destination receives and processes the data.

Packets belonging to different users can share the same network links. This is called **statistical multiplexing**.

### Store-and-forward transmission

In store-and-forward packet switching, a router generally receives an entire packet before transmitting that packet on the outgoing link.

Transmission delay is the time needed to put all packet bits onto a link.

\[
d_{\text{trans}}=\frac{L}{R}
\]

Where:

- \(L\) = packet length in bits
- \(R\) = link transmission rate in bits per second
- \(d_{\text{trans}}\) = transmission delay in seconds

**Example:**

A 12,000-bit packet is sent over a 6 Mbps link.

\[
d_{\text{trans}}=\frac{12,000}{6,000,000}
=0.002\text{ seconds}
\]

**Answer: 2 milliseconds.**

### Advantages of packet switching

- Many users can share network resources.
- Resources can be used efficiently for bursty traffic.
- Packets can sometimes be rerouted when a path fails.
- A dedicated circuit is not required for ordinary IP communication.

### Limitations

- Congestion can cause queuing delays.
- Packets may be dropped.
- Different packets may experience different delays or paths.
- Applications may need transport protocols to provide additional reliability.

### Packet switching versus circuit switching

| Packet switching | Circuit switching |
|---|---|
| Data is transmitted in packets | A communication circuit is established |
| Network capacity is generally shared dynamically | Resources may be reserved for a session |
| Queuing and packet loss can occur | Performance depends on resource allocation and admission |
| Efficient for bursty traffic | Reserved capacity may be idle during silent periods |
| Example: Internet IP traffic | Example: Traditional circuit-switched telephone systems |

## Part 7 — Network Performance

Network performance is commonly evaluated using delay, packet loss, and throughput.

### 7.1 The four components of nodal delay

\[
d_{\text{nodal}}=
d_{\text{proc}}+
d_{\text{queue}}+
d_{\text{trans}}+
d_{\text{prop}}
\]

**Processing delay:** Time required to examine headers and process a packet.

**Queuing delay:** Time a packet waits in a buffer before transmission.

**Transmission delay:** Time needed to place all packet bits onto the link.

\[
d_{\text{trans}}=\frac{L}{R}
\]

**Propagation delay:** Time required for the signal to travel across the physical link.

\[
d_{\text{prop}}=\frac{d}{s}
\]

Where:
- \(d\) = physical distance
- \(s\) = signal propagation speed

### 7.2 Transmission delay versus propagation delay

These two concepts are frequently tested in exams.

- Transmission delay depends on packet size and link transmission rate.
- Propagation delay depends on distance and signal propagation speed.

**Worked example:**

A packet contains 1,500 bytes. The link rate is 10 Mbps.

Convert bytes to bits:

\[
L=1,500\times8=12,000\text{ bits}
\]

Calculate transmission delay:

\[
d_{\text{trans}}=\frac{12,000}{10,000,000}
=1.2\text{ ms}
\]

If the physical link is 1,000 km long and propagation speed is \(2\times10^8\) m/s:

\[
d_{\text{prop}}=
\frac{1,000,000}{2\times10^8}
=5\text{ ms}
\]

Ignoring processing and queuing delays, the total is:

\[
1.2+5=\boxed{6.2\text{ ms}}
\]

### 7.3 Packet loss

Packet loss occurs when packets fail to reach their intended destination.

One common cause is buffer overflow. When packets arrive faster than a router can forward them, its buffer may become full, causing packets to be discarded.

### 7.4 Throughput

Throughput is the rate at which data is successfully delivered.

\[
\text{Average throughput}=
\frac{\text{Data transferred in bits}}{\text{Time in seconds}}
\]

For example, if 20 million bits are transferred in 4 seconds:

\[
\text{Throughput}=\frac{20,000,000}{4}
=5\text{ Mbps}
\]

**Bandwidth** often refers to a link's capacity, while **throughput** refers to the rate actually achieved.

The slowest link on a path can limit throughput. Congestion, packet loss, protocol overhead, and other factors can also reduce the achieved rate.

## Part 8 — Protocols and Standards

A network protocol specifies rules for communication, including message formats, message order, meaning, and the actions taken when messages are exchanged.

Standards help equipment and software from different manufacturers interoperate.

Important standards organizations include:

- **IETF:** Develops Internet specifications and standards, including RFCs.
- **IEEE:** Develops standards for Ethernet and Wi-Fi technologies.
- **W3C:** Develops standards and guidelines for Web technologies.

Not every RFC is an Internet Standard; RFCs serve several different purposes.

## Part 9 — Introduction to Network Security

Network security protects devices, data, and communication from unauthorized access and disruption.

### Three fundamental security goals

**Confidentiality:** Information is accessible only to authorized parties.

**Integrity:** Information is protected against unauthorized modification.

**Availability:** Systems and services remain accessible when needed.

### Common threats

- Phishing
- Malware
- Denial-of-service attacks
- Eavesdropping on unprotected communication
- Spoofing
- Unauthorized access

### Basic protective measures

- Use strong, unique passwords.
- Enable multifactor authentication.
- Keep software and network equipment updated.
- Use appropriate encryption, such as HTTPS with TLS.
- Apply firewalls and access controls.
- Maintain backups and monitor suspicious activity.

## Part 10 — Important Formulas

| Concept | Formula |
|---|---|
| Transmission delay | \(d_{\text{trans}}=L/R\) |
| Propagation delay | \(d_{\text{prop}}=d/s\) |
| Nodal delay | Processing + queuing + transmission + propagation |
| Average throughput | Data transferred / time |
| Byte conversion | 1 byte = 8 bits |

**Unit conversion reminders:**

- 1 Mbps = \(10^6\) bits per second.
- 1 second = 1,000 milliseconds.
- Convert packet sizes from bytes to bits before calculating transmission delay when the link rate is expressed in bits per second.

## Part 11 — Practice Questions

### Conceptual questions

**1. What is a computer network?**

Answer: A group of interconnected devices that communicate and share information or resources.

**2. What is the difference between the Internet and the World Wide Web?**

Answer: The Internet is the global networking infrastructure. The Web is a collection of linked resources accessed over that infrastructure.

**3. What is the difference between a router and a switch?**

Answer: A router forwards packets between networks. A network switch forwards frames within a local network.

**4. What is a protocol? Give three examples.**

Answer: A protocol defines rules for communication. Examples include HTTP, TCP, and IP.

**5. What is encapsulation?**

Answer: Encapsulation is the process of adding protocol control information as data moves down the network stack.

**6. Why does packet switching work well for Internet traffic?**

Answer: It allows multiple users to share communication links dynamically, which is useful for bursty traffic.

**7. What are the four components of nodal delay?**

Answer: Processing delay, queuing delay, transmission delay, and propagation delay.

### Calculation questions

**8. A 24,000-bit packet travels over a 12 Mbps link. Calculate transmission delay.**

\[
d_{\text{trans}}=
\frac{24,000}{12,000,000}
=0.002\text{ seconds}
\]

Answer: **2 milliseconds.**

**9. A signal travels 600 km at \(2\times10^8\) m/s. Calculate propagation delay.**

\[
d_{\text{prop}}=
\frac{600,000}{2\times10^8}
=0.003\text{ seconds}
\]

Answer: **3 milliseconds.**

**10. A system transfers 40 million bits in 8 seconds. Calculate average throughput.**

\[
\text{Throughput}=
\frac{40,000,000}{8}
=5\text{ Mbps}
\]

Answer: **5 Mbps.**

## Part 12 — Week 1 Revision Summary

Remember these essential points:

1. A computer network connects devices for communication and resource sharing.
2. The Internet is a global network of interconnected networks.
3. Hosts run applications; routers forward packets between networks.
4. Protocols define how devices communicate.
5. The five Internet layers are Application, Transport, Network, Link, and Physical.
6. Encapsulation adds protocol information as data moves down the layers.
7. Packet switching allows multiple users to share communication links.
8. Transmission delay is \(L/R\).
9. Propagation delay is distance divided by propagation speed.
10. Nodal delay includes processing, queuing, transmission, and propagation.
11. Throughput measures the rate of successful data delivery.
12. Network security aims to protect confidentiality, integrity, and availability.

## Further Study

Compare these notes with your instructor's lecture slides and assigned textbook chapter. Add any instructor-specific definitions, diagrams, examples, and required exercises.

**Reference:** Course textbook, Chapter 1 — Computer Networks and the Internet.

Additional introductory reading:
- [Understanding Networking Basics — Medium](https://medium.com/%40k24sw012zahidali/understanding-networking-basics-a-beginner-friendly-guide-d6b7d176a029)
- [Introduction to Computer Networks — SlideShare](https://www.slideshare.net/slideshow/lec01-introduction-computer-networks/267590169)

These external resources are supplementary. Follow your instructor's materials as the primary source for exam preparation.
