# Lesson 2: Transport and Application Layers

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### What does the transport layer provide?

- An end-to-end connection between two applications that are running on different hosts. Of course the transport layer provides this logical connection regardless if the hosts are in the same network

### What is a packet for the transport layer called?

- The transport layer on the sender host receives a message from the application layer and it appends its own header. We refer to this combined message as a **segment**

### What are the two main protocols within the transport layer?

1. UDP (User Datagram Protocol)
2. TCP (Transmission Control Protocol)

### What is multiplexing, and why is it necessary?

- One of the main desired functionalities of the transport layer is the ability for a host to run multiple applications to use the network simultaneously; which we refer to as **multiplexing**
- We need an addressing mechanism to distinguish the many processes sharing the same IP address on the same host. The transport layer solves this problem, by using additional identifiers known as **ports**
- The job of delivering the data that is included in a _transport-layer_ segment to the appropriate _socket_, as defined in the segment fields, is called **demultiplexing** (network -> transport -> socket)
- The sending host will need to gather data from different _sockets_, and encapsulate each data chunk with header information (that will later be used in demultiplexing) to create segments, and then forward the segments to the _network layer_. We refer to this job as _multiplexing_ (socket -> transport -> network)

### Describe the two types of multiplexing/demultiplexing

1. **Connectionless multiplexing/demultiplexing**: (two-tuple: destination IP and port, _mainly UDP_) consider host A sending data to host B; host B identifies the correct socket by looking at the field of the _destination_ port (which matches the _source_ port for host B)
2. **Connection-oriented multiplexing/demultiplexing**: (four-tuple: source and destination IPs and ports, _mainly TCP_) consider a client communicating to a server; the server waits for connection request from client then creates a four-tuple socket (welcoming socket) which establishes the connection

### What are the differences between UDP and TCP?

- _UDP_ properties:
  1. An _unreliable_ protocol as it lacks the mechanisms that TCP has in place
  2. A _connectionless_ protocol that does not require the establishment of a connection (e.g., three-way handshake) before sending packets
  3. However, UDP does offer _less_ delays and better control over sending data since there are no congestion control and connection management overhead
  4. Packet structure includes _source_ and _destination_ ports (note that _identifier socket_ is a two-tuple consisting of a _destination IP and port_), length of UDP segment (header and data), and _checksum_ for error checking (sum and 1 s complement which should result in all 1 s if successful)
- _TCP_ properties:
  1. Uses a **three-way handshake** as discussed in connection-oriented multiplexing/demultiplexing
  2. Using _primitives_ in the transport layer, guarantees an in-order delivery of the application-layer data without any loss or corruption

### When would an application layer protocol choose UDP over TCP?

- See above

### Explain the TCP Three-way Handshake

1. The TCP client sends a special segment, (containing no data) and with `SYN=1`. The client also generates an initial sequence number (`client_isn`) and includes it in this special TCP SYN segment
2. The server upon receiving this packet, allocates the required resources for the connection and sends back the special _connection-granted_ segment which we call **SYNACK**. This packet has `SYN=1`, `ack` field containing (`client_isn+1`) value and a randomly chosen initial sequence number in the sequence number field
3. When the client receives the SYNACK segment, it also allocates buffer and resources for the connection and sends an _acknowledgment_ with `SYN=0`

### Explain the TCP connection tear down

1. When client wants to _end_ the connection, it sends a segment with `FIN=1` to the server
2. Server _acknowledges_ that it has received the connection closing request and is now working on closing the connection
3. The _server_ then sends a segment with `FIN=1`, indicating that connection is closed
4. The _client_ sends an `ACK` for it to the server. It also waits for sometime to resend this acknowledgment in case the first `ACK` segment is lost

### What is Automatic Repeat Request or ARQ?

- Having the receiver send _acknowledgements_ indicating that it has successfully received the specific segment. In case the sender does not receive an acknowledgement within a given period of time, the sender can assume the packet is lost and resend it

### What is Stop and Wait ARQ?

- Sender sends a packet and wait for its acknowledgement from the receiver. In most cases, the _timeout_ value is a function of the _estimated round trip time_ of the connection

### What is Go-back-N?

- When sending multiple packets, for any lost packet $N$, the receiver will discard any subsequent packets and the sender will send all the packets starting from $N$ again

### What is selective ACKing?

- The sender _retransmits_ only those packets that it suspects were received in error. The receiver in this case would acknowledge a correctly received packet even if it is not in order. The out-of-order packets are buffered until any missing packets have been received at which point the batch of the packets can be delivered to the application layer

### What is fast retransmit?

- One example is when a sender receives 3 duplicate ACKs for a packet, it considers the packet to be lost and will retransmit it instead of waiting for the timeout

### What is transmission control and why do we need to control it?

- To determine transfer rates even without knowledge of link capacity and when other users may be using the same link
- To determine transfer rates to the receiver when the receiver is receiving files from many other users
- To understand the proper layer for which transmission control is implemented (transport layer)

### What is flow control and why do we need to control it?

- **Flow control**: controlling the transmission rate to protect the _receiver's buffer_ by matching the sender’s rate against the receiver’s rate of reading the data
- TCP uses a buffer at the receiver end to buffer packets that have not been transmitted to the application. It could happen that the receiver is involved with multiple processes and does not read the data instantly. This can cause accumulation of huge amount of data and overflow the receive buffer

### What is congestion control?

- **Congestion control**: controlling the transmission rate at the sender in order to protect the _network_ from congestion
- Congestion control is a primitive provided in the _transport layer_, whereas routers operate at the _network layer_. Therefore, the feature resides in the end nodes with no support from the network. Note that this is no longer true as certain routers in the modern networks can provide explicit feedback to the end-host by using protocols such as ECN and QCN

### What are the goals of the congestion control?

- **Efficiency**: high throughput and utilization
- **Fairness**: equal network bandwidth
- **Low delay**: minimal network delays
- **Fast convergence**: converge to fair bandwidth allocation quickly

### What is network-assisted congestion control?

- Rely on the network layer to provide explicit feedback to the sender about congestion in the network

### What is end-to-end congestion control?

- The network here does **not** provide any explicit feedback about congestion to the end hosts. Instead, the hosts infer congestion from the network behavior and adapt the transmission rate

### How does a host infer congestion?

1. Packet delay: as the network gets congested, the queues in the router buffers build up. This leads to increased packet delays
2. Packet loss: as the network gets congested, routers start dropping packets

### How does a TCP sender limit the sending rate?

- TCP uses a **congestion window** which is similar to the receive window used for flow control. It represents the maximum number of unacknowledged data that a sending host can have in transit (sent but not yet acknowledged)
- TCP uses a _probe-and-adapt_ approach in adapting the congestion window. Under regular conditions, TCP increases the congestion window trying to achieve the available throughput. Once it detects congestion then the congestion window is decreased

### Explain AIMD (Additive Increase/Multiplicative Decrease) in the context of TCP

- TCP _decreases_ the window when the level of congestion goes _up_, and it _increases_ the window when the level of congestion goes _down_
- The idea behind **additive increase** is to increase the window by one packet every RTT (Round Trip Time). In practice, this increase in AIMD happens incrementally. TCP doesn’t wait for ACKs of all the packets from the previous RTT. Instead, it increases the congestion window size as soon as each `ACK` arrive. In bytes, this increment is a portion of the **MSS (Maximum Segment Size)**
- Once TCP Reno detects congestion, it reduces the rate at which the sender transmits. So, when the TCP sender detects that a timeout occurred, then it sets the congestion window (`cwnd`) to _half_ of its previous value

### What is a slow start in TCP?

- When we have a new connection that starts from cold start, it can take much longer for the sending host to increase the congestion window by using AIMD. Consequently TCP Reno uses slow start phase where the congestion window is increased _exponentially_ instead of linearly as in the case of AIMD
- Slow start is called _slow_ start despite using an exponential increase because in the beginning it sends only _one packet_ and starts doubling it after each RTT. Thus, it is slower than starting with a large window

### Is TCP fair in the case two where connections have the same RTT? Explain

- For connections having _same_ RTT, AIMD leads to fairness in bandwidth sharing

### Is TCP fair in the case where two connections have different RTTs? Explain

- For connections with _different_ RTT, connections with the smaller RTT values would increase their congestion window faster than the ones with longer RTT values

### Explain how TCP CUBIC works

- **TCP CUBIC** uses a CUBIC polynomial as the growth function for congestion control. It follows most of the AIMD principles but _slowly_ increases the congestion window once it gets close to the previous congestion window size where congestion was previously detected
- The key feature of CUBIC is that its _window growth_ depends _only_ on the _time between two consecutive congestion events_. One congestion event is the time when TCP undergoes fast recovery. This feature allows CUBIC flows competing in the same bottleneck to have approximately the same window size independent of their RTTs, achieving good RTT-fairness

### Explain TCP throughput calculation

- The congestion window is increased by `1` packet every RTT, until it reaches the maximum value $W$, at which point a loss is detected and the `cwnd` is cut in half, $\frac{W}{2}$, this allows us to model TCP throughput as $BW < \frac{MSS}{RTT} * \frac{1}{\sqrt{p}}$ where $BW$ is bandwidth, $MSS$ is maximum segment size, and $p$ is probability loss
