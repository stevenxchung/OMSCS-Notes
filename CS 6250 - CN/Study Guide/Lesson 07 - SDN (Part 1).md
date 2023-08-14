# Lesson 7: SDN (Part 1)

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### What spurred the development of SDN (Software Defined Networking)?

- **SDN (Software Defined Networking)**: arose as part of the process to make computer networks more programmable. Computer networks are very complex and especially difficult to manage for two main reasons:
  - _Diversity of equipment_ on the network
  - _Proprietary technologies_ for the equipment
- SDN offers new ways to redesign networks to make them more manageable! It employs a simple idea - _separation of tasks_. We’ve seen that our code becomes more modular and easy to manage when we divide them into smaller functions with focused tasks. Similarly, SDN divides the network into two planes - _control plane and data plane_. It uses this separation to simplify management and speed up innovation!

### What are the three phases in the history of SDN?

- **Active networks**:
  - This phase took place from the _mid-1990s to the early 2000s_. During this time, the internet takeoff resulted in an increase in the applications and appeal of the internet. Researchers were keen on testing new ideas to improve network services. However, this required standardization of new protocols by the IETF (Internet Engineering Task Force), which was a slow and frustrating process
  - This tediousness led to the growth of active networks, which aimed at opening up network control. Active networking envisioned a programming interface (a network API) that exposed resources/network nodes and supported customization of functionalities for subsets of packets passing through the network nodes. This was the opposite of the popular belief in the internet community - the simplicity of the network core was important to the internet success!
- **Control and data plane separation**: this phase lasted from around _2001 to 2007_. During this time, there was a steady increase in traffic volumes and thus, network reliability, predictability and performance became more important. Network operators were looking for better network-management functions such as control over paths to deliver traffic (traffic engineering). Researchers started exploring short-term approaches that were deployable using existing protocols. They identified the challenge in network management lay in the way existing routers and switches tightly integrated the control and data planes. Once this was identified, efforts to separate the two began
- **OpenFlow API and network operating systems**:
  - This phase took place from around _2007 to 2010_. OpenFlow was born out of the interest in the idea of network experimentation at a scale (by researchers and funding agencies). It was able to balance the vision of fully programmable networks and the practicality of ensuring real world deployment. OpenFlow built on the existing hardware and enabled more functions than earlier route controllers. Although this dependency on hardware limited its flexibility, it enabled immediate deployment
  - The basic working of an OpenFlow switch is as follows. Each switch contains a table of packet-handling rules. Each rule has a pattern, list of actions, set of counters and a priority. When an OpenFlow switch receives a packet, it determines the highest priority matching rule, performs the action associated with it and increments the counter

### Summarize each phase in the history of SDN

- Highlights of _active networks_ include:
  - _Programmable functions_ in the network to lower the barrier to innovation
  - _Network virtualization_, and the ability to demultiplex to software programs based on packet headers
  - The vision of a _unified architecture_ for middlebox orchestration
- Highlights of _control and data plane separation_:
  - Logically _centralized control_ using an open interface to the data plane
  - _Distributed_ state management
- Highlights of _OpenFlow API and network operating systems_:
  - Generalizing network devices and functions
  - The vision of a network operating system
  - Distributed state management techniques

### What is the function of the control and data planes?

- Some functions of the control and data plane include:
  - Selecting between network paths based on the current traffic load
  - Minimizing disruptions during planned routing changes
  - Redirecting/dropping suspected attack traffic
  - Allowing customer networks more control over traffic flow
  - Offering value-added services for virtual private network customers

### Why separate the control from the data plane?

- **Independent evolution and development**: in the traditional approach, routers are responsible for both routing and forwarding functionalities. This meant that a change to either of the functions would require an upgrade of hardware. In this new approach, routers only focus on forwarding. Thus, innovation in this design can proceed independently of other routing considerations. Similarly, improvement in routing algorithms can take place without affecting any of the existing routers. By limiting the interplay between these two functions, we can develop them more easily
- **Control from high-level software program**: in SDN, we use software to compute the forwarding tables. Thus, we can easily use higher-order programs to control the routers’ behavior. The decoupling of functions makes debugging and checking the behavior of the network easier

### Why did the SDN lead to opportunities in various areas such as data centers, routing, enterprise networks, and research network?

- Separation of the control and data planes supports the _independent evolution and development of both_. Thus, the software aspect of the network can evolve independent of the hardware aspect. Since both control and forwarding behavior are separate, this enables us to use higher-level software programs for control. This makes it easier to debug and check the network's behavior
- As a result of separation, opportunities that emerged include:
  - Data centers
  - Routing
  - Enterprise networks
  - Research networks

### What is the relationship between forwarding and routing?

- **Forwarding**: is one of the most common, yet important functions of the network layer. When a router receives a packet at its input link, it must determine which output link that packet should be sent through. This process is called forwarding. It could also entail blocking a packet from exiting the router, if it is suspected to have been sent by a malicious router. It could also duplicate the packet and send it along multiple output links. Since forwarding is a _local function_ for routers, it usually takes place in nanoseconds and is implemented in the hardware itself. Forwarding is a function of the _data plane_
- **Routing**: involves determining the path from the sender to the receiver _across the network_. Routers rely on routing algorithms for this purpose. It is an _end-to-end process for networks_. It usually takes place in seconds and is implemented in the software. Routing is a function of the _control plane_

### What is the difference between a traditional and SDN approach in terms of coupling of control and data plane?

- In the _traditional approach_, the routing algorithms (control plane) and forwarding function (data plane) are closely coupled. The router runs and participates in the routing algorithms. From there it is able to construct the forwarding table which consults it for the forwarding function
- In the _SDN approach_:
  - There is a _remote controller_ that computes and distributes the forwarding tables to be used by every router. This controller is _physically separate_ from the router. It could be located in some remote data center, managed by the ISP or some other third party
  - We have a _separation of the functionalities_. The _routers_ are solely responsible for _forwarding_, and the _remote controllers_ are solely responsible for _computing and distributing the forwarding tables_. The controller is implemented in software, and therefore we say the network is software-defined
  - These software implementations are also increasingly open and publicly available, which speeds up innovation in the field

### What are the main components of SDN network and their responsibilities?

- **SDN-controlled network elements**: the SDN-controlled network elements, sometimes called the _infrastructure layer_, is responsible for the _forwarding_ of traffic in a network based on the rules computed by the SDN control plane
- **SDN controller**: is a _logically centralized entity_ that acts as an interface between the network elements and the network-control applications
- **Network-control applications**: are programs that _manage the underlying network_ by collecting information about the network elements with the help of SDN controller

### What are the four defining features in an SDN architecture?

1. **Flow-based forwarding**: the rules for forwarding packets in the SDN-controlled switches can be computed _based on any number of header field values in various layers_ such as the transport-layer, network-layer and link-layer. This differs from the traditional approach where only the destination IP address determines the forwarding of a packet. For example, OpenFlow allows up to 11 header field values to be considered
2. **Separation of data plane and control plane**: the SDN-controlled switches operate on the _data plane_ and they only execute the rules in the flow tables. Those rules are computed, installed, and managed by software that runs on separate servers
3. **Network control functions**: the SDN control plane, (running on multiple servers for increased performance and availability) consists of two components: _the controller and the network applications_. The controller maintains up-to-date network state information about the network devices and elements (for example, hosts, switches, links) and provides it to the network-control applications. This information, in turn, is used by the applications to monitor and control the network devices
4. **A programmable network**: the network-control applications act as the _“brain” of SDN control plane by managing the network_. Example applications can include network management, traffic engineering, security, automation, analytics, etc. For example, we can have an application that determines the end-to-end path between sources and destinations in the network using Dijkstra’s algorithm

### What are the three layers of SDN controller?

1. **Communication layer**: communicating between the _controller and the network elements_. This layer consists of a _protocol_ through which the SDN controller and the network controlled elements communicate. Using this protocol, the devices send locally observed events to the SDN controller providing the controller with a current view of the network state. For example, these events can be a new device joining the network, heartbeat indicating the device is up, etc. The communication between _SDN controller_ and the _controlled devices_ is known as the _“southbound” interface_. OpenFlow is an example of this protocol, which is broadly used by SDN controllers today
2. **Network-wide state-management layer**: stores information of _network-state_. This layer is about the network-state that is maintained by the controller. The network-state includes any information about the _state of the hosts, links, switches and other controlled elements in the network_. It also includes copies of the flow tables of the switches. Network-state information is _needed by the SDN control plane to configure the flow tables_
3. **Interface to the network-control application layer**: communicating between _controller and applications_. This layer is also known as the controller’s _“northbound” interface_ using which the _SDN controller interacts with network-control applications_. Network-control applications can read/write network state and flow tables in controller’s state-management layer. The SDN controller can notify applications of changes in the network state, based on the event notifications sent by the SDN-controlled devices. The applications can then take appropriate actions based on the event. A REST interface is an example of a northbound API
