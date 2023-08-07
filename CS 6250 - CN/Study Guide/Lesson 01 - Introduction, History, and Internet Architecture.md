# Lesson 1: Introduction, History, and Internet Architecture

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### What are advantages and disadvantages of a layered architecture?

- **Advantages** include: **scalability, modularity, and flexibility**. Some of the advantages of having a layered network stack include scalability, modularity and the flexibility to add or delete components which makes it easier overall for cost-effective implementations
- **Disadvantages** include:
  1. Some layers functionality depends on the information from other layers, which can violate the goal of layer separation
  2. One layer may _duplicate_ lower layer functionalities. For example, the functionality of error recovery can occur in lower layers, but also on upper layers as well
  3. Some additional _overhead_ that is caused by the abstraction between layers

### What are the differences and similarities of the OSI model and five-layered Internet model?

- OSI has seven layers: application, presentation, session, transport, network, data link, and physical. The internet model only has five layers: application, transport, network, data link, and physical (the application, presentation, and session layers are _combined_ into a single layer, and this combined layer is called the application layer)

### What are sockets?

- The interface between the application layer and the transport layer are the **sockets** (5-layer Internet model)

### Describe each layer of the OSI model

- The International Organization for Standardization (ISO) proposed the **seven-layered OSI (Open Systems Interconnection) model**:
  1. **Application**: packet of information is referred to as a **message**. Includes multiple protocols, some of the most popular ones include:
     - HTTP (web)
     - SMTP (email)
     - FTP (file transfer)
     - DNS (domain names to IP)
  2. **Presentation**: plays the intermediate role of formatting the information that it receives from the layer below and delivering it to the application layer
  3. **Session**: responsible for the mechanism that manages the different transport streams that belong to the same session between end-user application processes
  4. **Transport**: responsible for the end-to-end communication between end hosts. In this layer, there are two transport protocols, namely TCP and UDP. Generally, TCP offers more options, control, and reliability compared to UDP. Packet of information on this layer is referred to as a **segment**
  5. **Network**: responsible for moving **datagrams** (packet of information on the network layer) from one Internet host to another. Protocols in this layer include:
     - IP: defines the fields in the datagram and how the source/destination hosts and the intermediate routers use these fields
     - Routing: determines routes for datagrams between source and destination
  6. **Data link**: responsible to move the frames from one node (host or router) to the next node. Packets of information are referred to as **frames**. Protocols include:
     - Ethernet
     - PPP
     - WiFi
  7. **Physical**: facilitates the interaction with the actual hardware and is responsible to transfer bits within a frame between two nodes that are connected through a physical link

### Provide examples of popular protocols at each layer of the five-layered Internet model

- Application: HTTP, SMTP, FTP, and DNS
- Transport: TCP and UDP
- Network: IP and Routing
- Data link: Ethernet, PPP, and WiFi
- Physical: link dependent

### What is encapsulation, and how is it used in a layered model?

- **Encapsulation** is the process of taking data from one protocol and translating it into data that are used by another protocol, so that the data can continue across a network
- Suppose a message is to be sent from a source to a destination. At each layer the message is a combination of two parts:
  1. The _payload_ which is the message from the layer above
  2. The new appended _header_ information

### What is the e2e (end-to-end) principle?

- > The network core should be simple and minimal, while the end systems should carry the intelligence

### What are the examples of a violation of e2e principle?

- **Firewalls/traffic filters**: intermediate devices that are operated between two end hosts and they can drop the end hosts communication
- **NAT (Network Address Translation) boxes**: NAT boxes help us as a band-aid measure to deal with the shortage of Internet addresses. If we have a host behind a NAT and a host in the public Internet, then by default they cannot communicate without the intervention of a NAT box (there are workarounds to this however)

### What is the EvoArch model?

- EvoArch is a _discrete-time_ model that is executed over rounds and can help to study layered architectures and their evolution in a _quantitative_ manner. Through this model researchers were able to explain how the hierarchical structure of the layer architecture eventually lead to the _hourglass shape_

### Explain a round in the EvoArch model

1. **Introduce** new nodes, and we place them randomly at layers
2. **Examine** all layers, from the top to the bottom, and perform the following:
   - Connect the new nodes that we may have just introduced to that layer, by choosing _substrates_ based on the generality probabilities of the layer below $s(l−1)$, and by choosing products for them based on the generality probability of the current layer $s(l)$
   - Update the value of each node at each layer $l$, given that we may have new nodes added to the same layer $l$
   - Examine all nodes, in order of decreasing value in that layer, and remove the nodes that should die
3. **Stop** the execution of the model when the network reaches a given number of nodes

### What are the ramifications of the hourglass shape of the internet?

- In terms of future and entirely new Internet architectures, the EvoArch model predicts that even if these brand new architectures do **not** have the shape of an hourglass initially, they will probably do so as they evolve, which will lead to new _ossified_ protocols. The model suggests that one way to proactively avoid these ossification effects, that we now experience with TCP/IP, a network architect should try to design the functionality of each layer so that the waist is wider, consisting of several protocols that offer largely _non-overlapping_ but general services, so that they do not compete with each other

### Repeaters, hubs, bridges, routers operate on which layers?

- **Repeaters and hubs**: physical layer (L1)
- **Bridges and layer 2-switches**: data link layer (L2)
- **Routers and layer 3-switches**: network (L3)

### What is a bridge, and how does it “learn”?

- A **bridge** is a device with multiple inputs/outputs. A bridge transfers frames from an input to one (or multiple) outputs
- A **learning bridge** learns, populates and maintains, a forwarding table. The bridge consults that table so that it only forwards frames on specific ports, rather than over all ports. When the bridge receives any frame this is a _learning opportunity_ to know which hosts are reachable through which ports. This is because the bridge can view the _port_ over which a frame arrives and the _source host_

### What is a distributed algorithm?

- An algorithm that represents a network as a graph, bridges as nodes, and links between bridges as edges

### Explain the Spanning Tree Algorithm

- **STP (Spanning Tree Algorithm)** runs in rounds and selects configuration based on:
  1. Root of the configuration having a smaller ID
  2. Root of the configuration has equal IDs but one is closer to the root
  3. Both roots have the same ID and distance so select based on smaller _sending_ ID
- A node stops sending configuration messages over a link (port) when the node receives a configuration message that indicates that it is not the root

### What is the purpose of the Spanning Tree Algorithm?

- STP is a _distributed_ algorithm that _excludes links that lead to loops_ by having bridges select which links (ports) to use for forwarding and eliminating loops
