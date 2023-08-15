# Lesson 8: SDN (Part 2)

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### Describe the three perspectives of the SDN landscape

1. **Data plane**: functions and processes that forward data in the form of packets or frames
2. **Control plane**: functions and processes that determine which path to use by using protocols to populate forwarding tables of data plane elements
3. **Management plane**: services that are used to monitor and configure the control functionality, e.g., SNMP-based tools

- If a network policy is _defined_ in the management plane, the control plane _enforces_ the policy and the data plane _executes_ the policy by forwarding the data accordingly

### Describe the responsibility of each layer in the SDN layer perspective

- Management plane:

  - **Network applications**: functionalities that implement the _control plane logic_ and _translate_ to commands in the _data plane_. SDNs can be deployed on traditional networks, and can find itself in home area networks, data centers, IXPs etc. Due to this, there is a wide variety of network applications such as _routing, load balancing, security enforcement, end-to-end QoS enforcement, power consumption reduction, network virtualization, mobility management, etc._ Some well known solutions are Hedera, Aster\*x, OSP, OpenQoS, Pronto, Plug-N-Serve, SIMPLE, FAMS, FlowSense, OpenTCP, NetGraph, FortNOX, FlowNAC, VAVE, etc.
  - **Programming languages**: low-level or high-level programming languages. Using low-level languages, it is difficult to write modular code, reuse it and it generally leads to more error-prone development. _High level programming languages_ in SDNs provide _abstractions_, make development more _modular_, code more _reusable_ in control plane, do away with device specific and low-level configurations, and generally allow _faster_ development. Some examples of network programming languages in SDNs are Pyretic, Frenetic, Merlin, Nettle, Procera, FML, etc.
  - **Language-based virtualization**: ability to express _modularity_ and allowing different levels of _abstraction_. For example, using virtualization we can view a single physical device in different ways. This takes away the complexity away from application developers without compromising on security which is inherently guaranteed. Some popular examples of programming languages that support virtualization are Pyretic, libNetVirt, AutoSlice, RadioVisor, OpenVirteX, etc.

- Control plane:

  - **Northbound interface**: two core abstractions of an SDN ecosystem are the Southbound and Northbound interfaces. We have already seen Southbound interfaces, and that it already has a widely acceptable norm (OpenFlow). Compared to that, a standard for _Northbound interface is still an open problem_, as are its use cases. What is relatively clear is that Northbound interfaces are supposed to be a mostly software ecosystem, as opposed to the Southbound interfaces. Another key requirement is the _abstraction_ that guarantees _programming language and controller independence_. Some popular examples are Floodlight, Trema, NOX, Onix and SFNet
  - **Network operating system**: _logically centralized controller_ by way of a NOS (network operating system). The value of a NOS is in providing _abstractions_, essential services and common APIs to developers. For example, while programming a network policy, if a developer doesn’t need to worry about low-level details about data distribution among routing elements, that is an abstraction. Such systems propel more innovation by reducing inherent complexity of creating new network protocols and network applications. Some popular NOSs are OpenDayLight, OpenContrail, Onix, Beacon and HP VAN SDN
  - **Network hypervisor**: provide support for _arbitrary network topologies_ and _addressing schemes_, similar to the computing layer. Existing virtualization constructs such as VLAN, NAT and MLPS are able to provide full network virtualization, however these technologies are connected by a box-by-box basis configuration and there is no unifying abstraction that can be leveraged to configure these in a global manner, thereby making current network provisioning tasks as long as months and years. New advancements in SDN network virtualization such as VxLAN, NVGRE, FlowVisor, FlowN, NVP are promising

- Data plane:

  - **Southbound interface**: act as _connecting bridges_ between _control_ and _forwarding_ elements, and since they sit in between control and data plane, they play a crucial role in separating control and data plane functionality. These APIs are tightly coupled with the forwarding elements of the underlying physical or virtual infrastructure. The most popular implementation of Southbound APIs for SDNs is OpenFlow, however there are other APIs proposed such as ForCES, OVSDB, POF, OpFlex, OpenState, etc. For more reading and hands on for OVSDB: http://docs.openvswitch.org/en/latest/ref/ovsdb.7/
  - **Network infrastructure**: consists of _networking equipment (routers, switches and other middlebox hardware)_. What is now different is that these physical networking equipment are merely forwarding elements that do a simple forwarding task, and any logic to operate them is directed from the centralized control system. Popular examples of such infrastructure equipment include OpenFlow (software) switches such as SwitchLight, Open vSwitch, Pica8, etc.

### Describe a pipeline of flow tables in OpenFlow

- In the SDN architecture, a _data plane device_ is a hardware or software entity that _forwards packets_, while a _controller_ is a _software stack_ running on commodity hardware. A model derived from OpenFlow is currently the most widely accepted design of SDN data plane devices. It is based on a pipeline of flow tables where each entry of a flow table has three parts:
  1. A matching rule
  2. Actions to be executed on matching packets
  3. Counters that keep statistics of matching packets
- Possible actions for match or misses (when no rule is found for that packet) include:
  1. Forward the packet to outgoing port
  2. Encapsulate the packet and forward it to controller
  3. Drop the packet
  4. Send the packet to normal processing pipeline
  5. Send the packet to next flow table

### What’s the main purpose of southbound interfaces?

- Southbound interfaces or APIs are the _separating medium_ between the _control plane_ and _data plane_ functionality
- **OpenFlow** is the most widely accepted southbound standard for SDNs. It provides specification to implement OpenFlow-enabled forwarding devices, and for the communication channel between data and control plane devices

### What are three information sources provided by OpenFlow protocol?

1. _Event-based messages_ that are sent by forwarding devices to controller when there is a link or port change
2. _Flow statistics_ are generated by forwarding devices and collected by controller
3. _Packet messages_ are sent by forwarding devices to controller when they do not know what to do with a new incoming flow

### What are the core functions of an SDN controller?

- Functions such as _topology_, _statistics_, _notifications_, _device management_, along with _shortest path forwarding_ and _security mechanisms_ are essentials network control functionalities that network applications may use in building its logic. For example, security mechanisms are critical components to provide basic isolation and security enforcements between services and applications. For instance, high priority services’ rules should always take precedence over rules created by applications with low priority

### What are the differences between centralized and distributed architectures of SDN controllers?

- **Centralized controllers**: we typically see a _single entity that manages all forwarding devices in the network_, which is a single point of failure and may have scaling issues. Also, a single controller may not be enough to handle a large number of data plane elements. Some enterprise class networks and data centers use such architectures, such as Maestro, Beacon, NOX-MT. They use multi-threaded designs to explore parallelism of multi-core computer architectures. For example, Beacon can deal with more than 12 million flows per second by using large sized computing nodes of cloud providers. Other single controller architectures such as Trema, Ryu NOS, etc. target specific environments such as data centers, cloud infrastructures. Controllers such as Rosemary offer specific functionality and guarantees security and isolation of applications by using a container based architecture called micro-NOS
- **Distributed controllers**: Unlike single controller architectures that cannot scale in practice, _a distributed network operating system (controller) can be scaled to meet the requirements of potentially any environment - small or large networks_. Distribution can occur in two ways: it can be a centralized cluster of nodes or physically distributed set of elements. Typically, a cloud provider that runs across multiple data centers interconnected by a WAN may require a hybrid approach to distribution - clusters of controllers inside each data center and distributed controller nodes in different sites. Properties of distributed controllers:
  - Weak consistency semantics
  - Fault tolerance

### When would a distributed controller be preferred to a centralized controller?

- As mentioned above, when scaling and distribution is desired

### Describe the purpose of each component of ONOS (Open Networking Operating System) is a distributed SDN control platform

- **ONOS (Open Networking Operating System)** is a distributed SDN control platform. It aims to provide a global view of the network to the applications, scale-out performance and fault tolerance
- Components:
  - **Network view**: The management and sharing of the network state across these instances is achieved by maintaining a global network view. This view is built by using the network topology and state information (port, link and host information, etc) that is discovered by each instance
    - **Titan**, a _graph database_ and a _distributed key value store_ **Cassandra** is used to implement the view. The applications interact with the network view using the Blueprints graph API
  - **OpenFlow managers**: receive the changes the applications make to the view, and the appropriate switches are programmed

### How does ONOS achieve fault tolerance?

- To achieve fault tolerance, _ONOS redistributes the work of a failed instance to other remaining instances_. Each switch in the network connects to multiple ONOS instances with only one instance acting as its master. Each ONOS instance acts as a master for a subset of switches. Upon failure of an ONOS instance, an election is held on a consensus basis to choose a master for each of the switches that were controlled by the failed instance. For each switch, a master is selected among the remaining instances with which the switch had established connection. At the end of election for all switches, each switch would have at most one new master instance

### What is P4?

- **P4 (Programming Protocol-independent Packet Processors)** is a high-level programming language to _configure switches_ which works in conjunction with SDN control protocols. The popular vendor-agnostic OpenFlow interface, which enables the control plane to manage devices from different vendors, started with a simple rule table to match packets based on a dozen header fields. However, this specification has grown over the years to include multiple stages of the rule tables with increasing number of header fields to allow better exposure of a switch’s functionalities to the controller

### What are the primary goals of P4?

- **Reconfigurability**: the way parsing and processing of packets takes place in the switches should be modifiable by the _controller_
- **Protocol independence**: to enable the switches to be _independent_ of any particular protocol, the controller defines a packet parser and a set of tables mapping matches and their actions. The packet parser extracts the header fields which are then passed on to the `match+action` tables to be processed
- **Target independence**: the packet processing programs should be _programmed independent_ of the underlying target devices. These generalized programs written in P4 should be converted into target-dependent programs by a compiler which are then used to configure the switch

### What are the two main operations of P4 forwarding model?

1. **Configure**: these sets of operations are used to program the parser. They specify the header fields to be processed in each match+action stage and also define the order of these stages
2. **Populate**: the entries in the `match+action tables` specified during configuration may be altered using the populate operations. It allows addition and deletion of the entries in the tables

- In short, _configuration_ determines the packet processing and the supported protocols in a _switch_ whereas _population_ decides the policies to be applied to the _packets_

### What are the applications of SDN? Provide examples of each application

- **Traffic engineering**: This is one of the major areas of interest for SDN applications with main focus on optimizing the traffic flow so as to minimize power consumption, judiciously use network resources, perform load balancing, etc. With the help of optimization algorithms and monitoring the data plane load via southbound interfaces, the power consumption can be reduced drastically while still maintaining the desired goals of performance. ElasticTree is one such application which identifies and shut downs specific links and devices depending on the traffic load. Load balancing applications such as Plug-n-Serve and Aster\*x achieve scalability by creating rules based on wildcard patterns which enables handling of large numbers of requests from a particular group. Another use case of SDN applications is to automate the management of router configuration to reduce the growth in routing tables due to duplication of data. Large scale service providers also use SDN for traffic optimization to scale dynamically, e.g. ALTO VPN enables dynamic provisioning of VPNs in cloud infrastructure
- **Mobility and wireless**: The existing wireless networks face various challenges in its control plane including management of the limited spectrum, allocation of radio resources and load-balancing. The deployment and management of various wireless networks (WLANS, cellular networks) is made easier using SDN. SDN-based wireless networks offer a variety of features including on-demand virtual access points (VAPs), usage of spectrum dynamically, sharing of wireless infrastructure, etc. OpenRadio, which is considered as the OpenFlow for wireless, enables decoupling of the wireless protocols from the underlying hardware by providing an abstraction layer. Light virtual access points (LVAPs) offer an improved way of managing wireless networks by using a one-to-one mapping between LVAPs and clients. The Odin framework leverages LVAPs and the applications built on it provide features such as mobility management, channel selection algorithms, etc. In contrast to traditional wireless networks, a user can move between APs without any visible lag as the mobility manager can automatically move the client LVAP to a different AP
- **Measurement and monitoring**: The first class of applications in this domain aims to add features to other networking services. For example, new functions can be added easily to measurement systems such as BISmark in an SDN-based broadband connection, which enables the system to respond to change in network conditions. A second class of these applications aim to improve the existing features of SDNs using OpenFlow such as reducing the load on the control plane arising from collection of data plane statistics using various sampling and estimation techniques. OpenSketch is a southbound API that offers flexibility for network measurements. OpenSample and PayLess are examples of monitoring frameworks
- **Security and dependability**: The applications in this area focus majorly on improving the security of networks. One approach of using SDN to enhance security is to impose security policies on the entry point to the network. Another approach is to use programmable devices to enforce security policies on a wider network. DDoS detection, an SDN application identifies and mitigates DDoS flooding attacks by leveraging the timely information collected from the network. Furthermore, SDN has also been used to detect any anomalies in the traffic, to randomly mutate the IP addresses of hosts to fake dynamic IPs to the attackers (OF-RHM) , and monitoring the cloud infrastructures (CloudWatcher)
- **Data center networking**: Data Center networking can be revolutionized by the use of SDN which aims to offer services such as live migration of networks, troubleshooting, real-time monitoring of networks among various other features. SDN applications can also help detect anomalous behavior in data centers by defining different models and building application signatures from observing the information collected from network devices in the data center. Any deviation from the signature history can be identified and appropriate measures can be taken. SDN also helps in performing dynamic reconfigurations of virtual networks involved in a live virtual network migration, which is an important feature of virtual networks in cloud. LIME is one such SDN application which aims to provide live migration and FlowDiff is an application which detects abnormalities

### Which BGP limitations can be addressed by using SDN?

- _Routing only on destination IP prefix_: the routing is decided based on the destination prefix IP of the incoming packet. There’s no flexibility to customize rules for example based on the traffic application or the source/destination network.
- _Networks have little control over end-to-end paths_: networks can only select paths advertised by direct neighbors. Networks cannot directly control preferred paths but instead have to rely on indirect mechanisms such as “AS Path prepending”

### What’s the purpose of SDX?

- **SDX** was proposed to implement multiple applications including:
  - **Application specific peering**: custom peering rules can be installed for certain applications, such as high-bandwidth video applications like Netflix or YouTube which constitute a significant amount of traffic volume
  - **Traffic engineering**: controlling the inbound traffic based on source IP or port numbers by setting forwarding rules
  - **Traffic load balancing**: the destination IP address can be rewritten based on any field in the packet header to balance the load
  - **Traffic redirection through middleboxes**: targeted subsets of traffic can be redirected to middleboxes

### Describe the SDX architecture

- In the SDX architecture, each AS is the illusion of its own _virtual SDN switch_ that connects its border router to every other participant AS. For example, AS $A$ has a virtual switch connecting to the virtual switches of ASes $B$ and $C$.
- Each AS can define _forwarding policies_ as if it is the only participant at the SDX, without influencing how other participants forward packets on their own virtual switches. Each AS can have its own _SDN applications_ for dropping, modifying, or forwarding their traffic. The policies can also be different based on the direction of the traffic (inbound or outbound). An inbound policy is applied on the traffic coming from other SDX participant on a virtual switch. An outbound policy is applied to traffic from the participant’s virtual switch port towards other participants. The SDX is responsible to combine the policies from multiple participants into a single policy for the physical switch

### What are the applications of SDX in the domain of wide area traffic delivery?

- **Application specific peering**: ISPs prefer dedicated ASes to handle the high volume of traffic flowing from high bandwidth applications such as YouTube, Netflix. This can be achieved by identifying a particular application’s traffic using packet classifiers and directing the traffic in a different path. However this involves configuring additional and appropriate rules in the edge routers of the ISP. This overhead can be eliminated by configuring custom rules for flows matching a certain criteria at the SDX
- **Inbound traffic engineering**: an SDN enabled switch can be installed with forwarding rules based on the source IP address and source port of the packets, thereby enabling an AS to control how the traffic enters its network. This is in contrast with BGP which performs routing based solely on the destination address of a packet. Although there are workarounds such as using AS path prepending and selective advertisements to control the inbound traffic using BGP, they come with certain limitations. An AS’s local preference takes a higher priority for the outgoing traffic and the selective advertisements can lead to pollution of the global routing tables
- **Wide-area server load balancing**: the existing approach of load balancing across multiple servers of a service involves a client’s local DNS server issuing a request to the service’s DNS server. As a response, the service DNS returns the IP address of a server such that it balances the load in its system. This involves DNS caching which can lead to slower responses in case of a failure. A more efficient approach to load balancing can be achieved with the help of SDX, as it supports modification of the packet headers. A single anycast IP can be assigned to a service, and the destination IP addresses of packets can be modified at the exchange point to the desired backend server based on the request load
- **Redirection through middle boxes**: SDX can be used to address the challenges in existing approaches to using middleboxes (firewalls, load balancers, etc). The placement of middleboxes are usually targeted at important junctions, such as the boundary of the enterprise networks with their upstream ISPs. To avoid the high expenses involved in placing middleboxes at every location in case of geographically large ISPs, the traffic is directed through a fixed set of middleboxes by the ISPs. This is done by manipulating routing protocols such as internal BGP to essentially hijack a subset of traffic and sending it to a middlebox. This approach could result in unnecessary additional traffic being redirected, and is also limited by the fixed set of middleboxes. To overcome these issues, an SDX can identify and redirect the desired traffic through a sequence of middleboxes
