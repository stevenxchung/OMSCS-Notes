# Lesson 6: Router Design and Algorithms (Part 2)

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### Why is packet classification needed?

- As the internet becomes increasingly complex, networks require _quality of service guarantees_ and _security guarantees_ for their traffic. Packet forwarding based on the longest prefix matching of destination IP addresses is **not** enough and we need to handle packets based on multiple criteria (TCP flags, source addresses) - we refer to this finer packet handling as **packet classification**

### What are three established variants of packet classification?

1. **Firewalls**: routers implement firewalls at the entry and exit points of the network to filter out unwanted traffic, or to enforce other security policies
2. **Resource reservation protocols**: e.g., **DiffServ (differentiated services)** has been used to reserve bandwidth between a source and a destination
3. **Routing based on traffic type**: routing based on the specific type of traffic helps avoid delays for time-sensitive applications

### What are the simple solutions to the packet classification problem?

- **Linear search**: _firewall implementations_ perform a linear search of the rules database and keep track of the best-match rule. This solution can be reasonable for a few rules but the time to search through a large database that may have thousands of rules can be prohibitive
- **Caching**: another approach is to cache the results so that future searches can run faster. This has two problems:
  1. The cache-hit rate can be high (eg 80-90%), but still we will need to perform _searches for missed hits_
  2. Even with a high 90% hit rate cache, a _slow linear search_ of the rule space will result in _poor performance_. For example, suppose that a search of the cache costs 100 nano-sec (one memory access) and that a linear search of 10,000 rules costs 1,000,000 nano-sec = 1 msec (one memory access per rule). Then the average search time with a cache hit rate of 90% is still 0.1 msec, which is rather slow
- **Passing labels**: the **MPLS (Multiprotocol Label Switching)** and _DiffServ_ use this technology. MPLS is useful for _traffic engineering_. A label-switched path is set up between the two sites A and B. Before traffic leaves site A, a router does packet classification and maps the web traffic into an _MPLS header_. Then the intermediate routers between A and B apply the label without having to redo packet classification. DiffServ follows a similar approach, applying _packet classification_ at the _edges_ to mark packets for special quality of service

### How does fast searching using set-pruning tries work?

- Start with a _two-dimensional rule_ (e.g., we want to classify packets using both the source and the destination IP addresses)
- Build a trie on the _destination prefixes_ in the database, and then _for every leaf-node_ at the destination trie to “hang” source tries
- By $S1$ we denote the source prefix of rule $R1$, $S2$ of rule $R2$, etc. Thus for every destination prefix $D$ in the destination trie we _prune_ the set of rules to those that are compatible with $D$
- We first match the destination IP address in a packet in the destination trie. Then we traverse the corresponding source trie to find the longest prefix match for the source IP. The algorithm keeps track of the _lowest-cost matching rule_. The algorithm concludes with the _least-cost rule_

### What’s the main problem with the set pruning tries?

- Referring to the lecture, the problem is _which source prefixes to store at the sources tries_? For example, let's consider the destination $D = 00∗$. Both rules $R4$ and $R5$ have $D$ as the destination prefix. So the source tries for $D$ will need to include the source prefixes $1∗$ and $11∗$
- The problem with the set pruning tries is _memory explosion_. Because a source prefix can occur in _multiple destination tries_

### What is the difference between the pruning approach and backtracking approach for packet classification with a trie?

- The set pruning approach has _high cost in memory_ to _reduce time_. The opposite approach (**backtracking**) is to _pay in time_ to _reduce memory_
- The algorithm goes through the destination trie and finds the longest destination prefix $D$ matching the header. Then it works its way back up the destination trie and search the source trie associated with every ancestor prefix of $D$ that points to a nonempty source trie
- Since each rule now is stored exactly _once_, the _memory requirements_ are _lower_ than the previous scheme. But, the _lookup cost_ for backtracking is _worse_ than for _set-pruning tries_

### What’s the benefit of grid of tries approach?

- With the **grid of tries** approach, we can reduce the wasted time in the backtracking search by using _pre-computation_. When there is a failure point in a source trie, we pre-compute a switch pointer. Switch pointers take us directly to the next possible source trie that can contain a matching rule

### Describe the “Take the Ticket” algorithm

- A simple scheduling algorithm is the **take the ticket algorithm**. Each output line maintains a _distributed queue_ for all input lines that want to send packets to it. When an input line wants to send a packet to a specific output line, it requests a ticket. The input line waits for the ticket to be served. At that point, the input line connects to the output line, the cross-point is turned on, and the input line sends the packet

### What is head-of-line problem?

- Referring to lecture, in the first iteration while $A$ sends its packet, the entire queue for $B$ and $C$ are waiting. We refer to this problem as **HOL (head-of-line)** blocking because the entire queue is _blocked_ by the progress of the _head of the queue_

### How to avoid head-of-line problem using knockout scheme?

- Avoiding head-of-line blocking via **output queuing**: a practical implementation of this approach is the **Knockout scheme**. It relies on breaking up packets into _fixed size (cell)_. We suppose that in practice the same output rarely receives $N$ cells and the expected number is $k$ (smaller than $N$). Then we can have the fabric running $k$ times as fast as an input link, instead of $N$. We may still have scenarios where the expected case is violated
- To accommodate these scenarios, we have one or more of a primitive switching element that randomly picks the chosen output:
  - _Two contenders, one winner_: $k = 1$ and $N = 2$. _Randomly_ pick the output that is chosen. The switching element in this case is called a **concentrator**
  - _Many contenders, one winner_: $k = 1$ and $N > 2$. One output is chosen out of $N$ possible outputs. In this case, we can use the same strategy of _multiple_ 2-by-2 concentrators
  - _Many contenders, more than one winner_: $k$ needs to be chosen out of $N$ possible cells, with $k$ and $N$ _arbitrary values_. We create $k$ knockout trees to calculate the first $k$ winners
- The drawback with this approach is that is it is complex to implement

### How to avoid head-of-line problem using parallel iterative matching?

- Avoiding head-of-line blocking by using **parallel iterative matching**: allow queueing for the input lines, but in such a way so we avoid the head of line blocking. With this approach, we _schedule both the head of the queue_ but also _more packets_, so that the queue makes progress in the case that the head is blocked
- The algorithm runs in three rounds:
  1. The scheme works by having all inputs send requests in _parallel_ to all outputs they want to connect with. This is the _request phase_ of the algorithm
  2. In the _grant phase_, the outputs that receive multiple requests pick a _random input_, so the output link 1 randomly chooses $B$. Similarly, the output link 2 randomly chooses $A$ (between $A$ and $B$)
  3. Finally, in the _accept phase_, inputs that receive multiple grants _randomly_ pick an output to send to
- Note: in the _second round_, the algorithm repeats by having each input send to _two outputs_. And finally the third row repeats by having each input send to one output. Thus in four cell times (of which the fourth cell time is sparsely used and could have been used to send more traffic) _all_ the traffic is sent. This is clearly _more efficient_ than the take-a-ticket

### Describe FIFO with tail drop

- **FIFO with tail drop**: packets enter a router on input links. They are then looked up using the _address lookup component_ – which gives the router an output link number. The switching system within the router then places the packet in the corresponding output port. This port is a _FIFO (first in, first out) queue_. If the output link _buffer is completely full_, incoming packets to the _tail of the queue are dropped_. This results in _fast_ scheduling decisions, but potential _loss_ in important data packets

### What are the reasons to make scheduling decisions more complex than FIFO?

- Finding time-efficient scheduling algorithms that provide guarantees for _bandwidth_ and _delay_ are important!
- The reasons to make scheduling decisions _more complex_ than FIFO with tail drop are:
  1. **Router support for congestion**: congestion in the internet is increasingly possible as the usage has increased faster than the link speeds. While most traffic is based on TCP (which has its own ways to handle congestion), additional router support can improve the _throughput of sources_ by helping handle congestion
  2. **Fair sharing of links among competing flows**: during _periods of backup_, these packets tend to _flood the buffers_ at an output link. If we use FIFO with tail drop, this blocks other flows, resulting in important connections on the clients’ end freezing. This provides a sub-optimal experience to the user, indicating a change is necessary!
  3. **Providing QoS guarantees to flows**: one way to enable fair sharing is to _guarantee_ certain amounts of _bandwidths_ to a flow. Another way is to _guarantee_ the _delay_ through a router for a flow. This is noticeably important for video flows – without a bound on delays, live video streaming will not work well

### Describe BBRR (Bit-by-bit Round Robin) scheduling

- **BBRR (bit-by-bit round robin)**: imagine a system where in a single round, one bit from each active flow is transmitted in a round robin manner. This would ensure fairness in bandwidth allocation. However, since it’s not possible in the real world to split up the packets, we consider an _imaginary bit-by-bit system_ to calculate the _packet-finishing time_ and send a packet as a whole

### Bit-by-bit Round Robin provides fairness, what’s the problem with this method?

- We will need to keep track of the _finishing time_ at which the _head packet of each queue would depart_ and choose the earliest one. This requires a _priority queue_ implementation, which has time complexity which is _logarithmic_ in the number of flows! Additionally, if a new queue becomes active, _all_ timestamps may have to change – which is an operation with time complexity _linear_ in the number of flows. Thus, the _time complexity_ of this method makes it _hard to implement at gigabit speeds_

### Describe DRR (Deficit Round Robin)

- **DRR (Deficit Round Robin)**: simple _constant-time_ round robin algorithm with a modification to ensure _fairness_. For each flow, we assign a _quantum size_, $Q_i$, and a _deficit counter_, $D_i$. The **quantum size** determines the share of bandwidth allocated to that flow. For each turn of round robin, the algorithm will serve as many packets in the flow $i$ with size less than $(Q_i + D_i)$. If there are packets remaining in the queue, it will store the remaining bandwidth in $D_i$ for the next run. However, if all packets in the queue are serviced in that turn, it will clear $D_i$ to 0 for the next turn

### What is a token bucket shaping?

- **Token bucket shaping**: can limit the burst rate of a flow by:
  1. Limiting the _average rate_ (e.g., 100 kbps)
  2. Limiting the _maximum burst size_ (e.g., the flow can send a burst of 4KB at a rate of its choice)
- In practice, the bucket shaping idea is implemented using a _counter_ (can’t go more than max value $B$, and gets decremented when a bit arrives) and a _timer_ (to increment the counter at a rate $R$). The problem with this technique is that we have _one queue per flow_. This is because a flow may have a full token bucket, whereas other flows may have an empty token bucket and therefore will need to wait
- **Bucket policing**: to maintain _one single queue_, we use a modified version of token bucket shaper, called token bucket policing. When a packet arrives, it will need to have tokens at the bucket already there. If the bucket is empty the packet is dropped

### In traffic scheduling, what is the difference between policing and shaping?

- **Traffic policing** and **traffic shaping** are mechanisms to _limit_ the _output rate of a link_. The output rate is controlled by _identifying traffic descriptor violations_ and then responding to them in two different ways:
  - **Policer**: when traffic rate reaches the maximum configured rate, excess traffic is either _dropped_, or the setting or _marking_ of a packet is changed. The output rate appears as a _saw-toothed wave_
  - **Shaper**: _retains excess packets_ in a queue or a buffer and this excess is _scheduled for later transmission_. The result is that excess traffic is _delayed_ instead of dropped. Thus, when the data rate is _higher_ than the configured rate, the flow is _shaped or smoothed_. Traffic shaping and policing can work in tandem

### How is a leaky bucket used for traffic policing and shaping?

- **Leaky bucket algorithm**: analogous to water flowing into a leaky bucket with the water leaking at a _constant rate_. The bucket, say with _capacity_ $b$, represents a _buffer_ that holds packets and the water corresponds to the incoming packets. The _leak rate_, $r$, is the rate at which the packets are allowed to enter the network, which is constant irrespective of the rate at which packets arrive
- If an arriving packet does **not** cause an _overflow_ when added to the bucket, it is said to be _conforming_. Otherwise, it is said to be _non-conforming_. Packets classified as conforming are added to the bucket while non-conforming packets are discarded. So if the bucket is _full_, the new packet that arrives to the bucket is _dropped_
- Irrespective of the input rate of packets, the _output rate is constant_ which leads to _uniform distribution_ of packets send to the network. This algorithm can be implemented as a _single server queue_
