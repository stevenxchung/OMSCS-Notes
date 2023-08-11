# Lesson 5: Router Design and Algorithms (Part 1)

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### What are the basic components of a router?

- The main job of a router is to implement the _forwarding plane_ functions and the _control plane_ functions
- **Forwarding (or switching) function**: a.k.a. data plane function, is typically implemented in _hardware_, forwarding is the router’s action to transfer a packet from an input link interface to the appropriate output link interface
- **Input ports**: serve several purposes which include terminating incoming links, data link processing, and lookup (including forwarding and queuing)
- **Switching fabric**: moves the packets from input to output ports. There are three types of switching fabrics: _memory_, _bus_, and _crossbar_
- **Output ports**: receives and queues the packets which come from the _switching fabric_ and then sends them over to the _outgoing link_
- **Control plane functions**: implement the routing protocols, maintain the routing tables, compute the forwarding table. All these functions are implemented in _software_ in the _routing processor_

### Explain the forwarding (or switching) function of a router

- See above

### The switching fabric moves the packets from input to output ports. What are the functionalities performed by the input and output ports?

- Input/output ports operate as _I/O devices_ in an operating system, and they are controlled by the _routing processor_. See above for functionalities

### What is the purpose of the router’s control plane?

- See above

### What tasks occur in a router?

Several tasks occur in a router:

- **Lookup**: when a packet arrives at the input link, the router looks at the destination IP address and determines the output link by looking at the forwarding table (or Forwarding Information Base or FIB). The **FIB** provides a mapping between destination prefixes and output links
- **Switching**: after _lookup_, the switching system takes over to transfer the packet from the input link to the output link. Modern fast routers use crossbar switches for this task. Though scheduling the switch (matching available inputs with outputs) is a difficult task because multiple inputs may want to send packets to the same output
- **Queuing**: after the packet has been _switched_ to a specific output, it will need to be _queued_ (if the link is congested). The queue maybe as simple as First-In-First-Out (FIFO) or it may be more complex (e.g. weighted fair queuing) to provide delay guarantees or fair bandwidth allocation
- **Header validation and checksum**: the router checks the packet's version number, it decrements the time-to-live (TTL) field, and also it recalculates the header checksum
- **Route processing**: the routers build their _forwarding tables_ using routing protocols such as RIP, OSPF, and BGP. These protocols are implemented in the routing processors
- **Protocol processing**: in order to implement their functions, need to implement the following protocols:
  - The _SNMP (simple network management protocol)_ that provides a set of counters for remote inspection
  - TCP and UDP for remote communication with the router,
  - _ICMP (internet control message protocol)_, for sending error messages, e.g., when time to live time is exceeded

### List and briefly describe each type of switching. Which, if any, can send multiple packets across the fabric in parallel?

- There are three types of switching:
  1. **Switching via memory**: when an input port receives a packet, it sends an interrupt to the routing processor and the packet is copied to the processor’s memory. Then the processor extracts the destination address and looks into the forward table to find the output port, and finally the packet is copied into that output’s port buffer
  2. **Switching via bus**: when an input port receives a new packet, it puts an internal header that designates the output port, and it sends the packet to the shared bus. Then all the output ports will receive the packet, but _only the designated one will keep it_. When the packet arrives at the designated output port, then the internal header is removed from the packet. _Only one packet can cross the bus at a given time_, and so the speed of the bus limits the speed of the router
  3. **Switching via interconnection network**: a **crossbar switch** is an interconnection network that connects $N$ input ports to $N$ output ports using $2N$ buses. Horizontal buses meet the vertical buses at cross-points which are controlled by the switching fabric. For example, let's suppose that a packet arrives at port A that will need to be forwarded to output port Y, the switching fabric closes the cross-point where the two buses intersect, so that port A can send the packets onto the bus and then the packet can only be picked up by output port Y. Crossbar network can carry _multiple packets at the same time_, as long as they are using _different input and output ports_

### What are two fundamental problems involving routers, and what causes these problems?

- The two fundamental problems that a router faces revolve around:
  1. **Bandwidth and internet population scaling**: These scaling issues are caused by:
     - An increasing number of devices that connect to the internet
     - Increasing volumes of network traffic due to new applications
     - New technologies such as optical links that can accommodate higher volumes of traffic
  2. **Services at high speeds**: new applications require services such as protection against delays in presence of congestion, and protection during attacks or failures. But offering these services at very high speeds is a challenge for routers

### What are the bottlenecks that routers face, and why do they occur?

- A list of bottlenecks and causes include:
  - **Exact lookups**: caused by link speed scaling
  - **Prefix lookups**: caused by link speed and prefix database size scaling
  - **Packet classification**: caused by service differentiation and link spend and size scaling
  - **Switching**: caused by optical-electronic speed gap and head-of-line blocking
  - **Fair queueing**: caused by service differentiation and link speed and memory scaling
  - **Internal bandwidth**: caused by scaling of internal bus speeds
  - **Measurement**: caused by link speed scaling
  - **Security**: caused by scaling in number and intensity of attacks

### Convert between different prefix notations (dot-decimal, slash, and masking)

- **Dot decimal**: an example 16-b prefix `132.234` can be converted to:
  - Binary, first octet: `10000100`
  - Binary, second octet: `11101010`
  - Binary, prefix: `1000010011101010*` where `*` indicates the remaining bits do not matter
- **Slash notation**: standard notation: $A/L$ (where $A=Address$, $L=Length$), e.g., `132.238.0.0/16` where `16` denotes that only the first 16 bits are relevant for prefixing
- **Masking**: we can use a mask instead of the prefix length (e.g., the prefix `123.234.0.0/16` is written as `123.234.0.0` with a mask `255.255.0.0`). The mask `255.255.0.0` denotes that only the first 16 bits are important

### What is CIDR, and why was it introduced?

- Due to the rapid exhaustion of IP addresses, in 1993, the **CIDR (Classless Internet Domain Routing)** came into effect. CIDR essentially assigns IP addresses using _arbitrary-length prefixes_. CIDR has helped to decrease the router table size but at the same time it introduced us to a new problem: _longest-matching-prefix lookup_

### Name 4 takeaway observations around network traffic characteristics. Explain their consequences

- The four takeaway observations are:
  1. Measurement studies on network traffic had shown a large number (in the order of hundred thousands, 250,000 according to a measurement study in the earlier days of the Internet) of _concurrent flows of short duration_. This already large number has only been increasing. This has a consequence that a caching solution would **not** work efficiently
  2. The important element while performing any lookup operation is how fast it is done (lookup speed). A large part of the _cost of computation for lookup is accessing memory_
  3. An _unstable routing protocol_ may adversely impact the update time in the table: add, delete or replace a prefix. Inefficient routing protocols increase this value up to additional milliseconds
  4. An important trade-off is _memory usage_. We have the option to use expensive fast memory (cache in software, SRAM in hardware) or cheaper but slower memory (e.g., DRAM, SDRAM)

### Why do we need multi-bit tries?

- While a **uni-bit trie** is very efficient and also offers advantages such as fast lookup and easier updates, its biggest problem is the _number of memory accesses_ that it requires to perform a lookup. For 32 bit addresses, we can see that looking up the address in a uni-bit trie might require 32 memory accesses, in the worst case. Assuming a 60 nano-sec latency, the worst case search time is 1.92 microseconds. This could be _very inefficient in high speed links_
- Instead, we can implement lookups using a stride. By **stride** we refer to the _number of bits_ that we check at each step. A **multi-bit trie** is a trie where each node has $2^k$ children, where $k$ is the stride. Next we will see that we can have two flavors of multi-bit tries: _fixed length_ stride tries and _variable length_ stride tries

### What is prefix expansion, and why is it needed?

- Consider a prefix such as `101*` (length 3) and a stride length of 2 bits. If we search in 2 bit lengths, we will miss out on prefixes like `101*`. To combat this, we use a strategy called **controlled prefix expansion**, where we expand a given prefix to more prefixes
- We ensure that the expanded prefix is a _multiple_ of the chosen stride length. At the same time we _remove_ all lengths that are not multiples of the chosen stride length. We end up with a new database of prefixes, which may be larger (in terms of actual number of prefixes) but with fewer lengths. So, the expansion gives us more speed with an increased cost of the database size. For example, we substitute (expand) `P3 = 11001*` with `110010*` and `110011*`

### Perform a prefix lookup given a list of pointers for uni-bit tries, fixed-length multi-bit ties, and variable-length multi-bit tries

- Performed in lesson quiz

### Perform a prefix expansion. How many prefix lengths do old prefixes have? What about new prefixes?

- Performed in lesson quiz

### What are the benefits of variable-stride versus fixed-stride multi-bit tries?

- **Fixed-stride**:
  1. Every element in a trie represents two pieces of information: a _pointer_ and a _prefix value_
  2. The prefix search moves ahead with the preset length in n-bits (3 in this case)
  3. When the path is traced by a pointer, we remember the last matched prefix (if any)
  4. Our search ends when an _empty pointer_ is met. At that time, we return the _last matched prefix_ as our final prefix match
- **Variable-stride**:
  1. Every node can have a _different number of bits_ to be explored
  2. The optimizations to the stride length for each node are all done in pursuit of _saving trie memory_ and the _least memory access_
  3. An optimum variable stride is selected by using _dynamic programming_
