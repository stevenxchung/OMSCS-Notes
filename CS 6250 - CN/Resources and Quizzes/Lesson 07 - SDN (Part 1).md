# Lesson 7: SDN (Part 1)

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

[The Road to SDN: An Intellectual History of Programmable Networks](http://www.sigcomm.org/sites/default/files/ccr/papers/2014/April/0000000-0000012.pdf)

### Book References

Kurose-Ross (7th Edition) Section 4.1.1, Chapter 5.

### Optional Readings

- [SDN Controllers: Benchmarking & Performance Evaluation](https://arxiv.org/pdf/1902.04491.pdf)

- [SDN architecture](https://www.opennetworking.org/wp-content/uploads/2013/02/TR_SDN_ARCH_1.0_06062014.pdf)

### Optional Hands-on

[OpenDaylight Application Developer’s tutorial](http://sdnhub.org/tutorials/opendaylight/)

## Section Quizzes

### Lesson 7: SDN (Part 1) 1 Quiz

1. _The main reason why SDNs were created was because of the increase of internet users_.
   - False
2. _SDNs divide the network in two planes: control plane and data plane, to ease management and speed up innovation_.
   - True

### Lesson 7: SDN (Part 1) 2 Quiz

1. _The Active Networks phase consisted mainly of creating a programming interface that exposed resources/network nodes and supported customization of functionalities for subsets of packets passing through the network_.
   - True
2. _One of the main differences between the Active Networks phase and the separation of the Control and Data plane phase is that the former is focused on network-wide visibility and control and the latter is focused on device-level configurations_.
   - False
3. _An OpenFlow switch has a table of packet-handling rules, and whenever it receives a packet, it determines the highest priority matching rule, performs the action associated with it and increments the respective counter_.
   - True
4. _One of the downfalls of OpenFlow when it was first created was that it was hard to deploy and scale it easily_.
   - False

### Lesson 7: SDN (Part 1) 3 Quiz

1. _SDNs use <...> to control the routers’ behavior (e.g., the path selection process)_.
   - Software
2. _With the separation of the control plane and the data plane, any change to the forwarding functions on a router is independent from the routing functions of the control plane_.
   - True
3. _In the SDN approach, the controller that computes and distributes the forwarding tables to be used by the routers is <...>_.
   - Physically separate from the routers
4. _Software implementations in SDN controllers are increasingly open and publicly available, which <...> innovation in the field_.
   - Speeds up

### Lesson 7: SDN (Part 1) 4 Quiz

1. _The network-control applications use the information about the network devices and elements, provided by the controller, to monitor and control the network devices_.
   - True
2. _In an SDN, the controller is responsible for the <...> of the traffic, and the SDN-controlled network elements such as the switches are responsible for the <...> of the traffic_.
   - Routing, forwarding
3. _Traffic forwarding can be based on any number of header field values in various layers like the transport-layer, network-layer and link-layer_.
   - True
4. _SDN controllers operate on the <...> plane_.
   - Control

### Lesson 7: SDN (Part 1) 5 Quiz

1. _Match the number of the missing components in the following image (provided) with their respective name/example_.
   - Load balancer
   - RESTful API
   - Flow tables
   - OpenFlow
   - SDN controller
2. _The northbound interface is used by the controller and the network-control applications to interact with each other_.
   - True
3. _A REST interface is an example of a southbound API_.
   - False
4. _SDN controllers that are implemented by centralized servers are more likely to achieve fault tolerance, high availability and efficiency_.
   - False
