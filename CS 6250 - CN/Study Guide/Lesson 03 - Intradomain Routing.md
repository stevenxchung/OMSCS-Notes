# Lesson 3: Intradomain Routing

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### What is the difference between the forwarding and routing?

- **Forwarding**: transferring a packet from an incoming link to an outgoing link _within_ a single router
- **Routing**: refer to how routers work together using routing protocols to determine the good paths (or good routes as we call them) over which the packets travel from the _source_ to the _destination_ node

### What is the main idea behind a link-state routing algorithm?

- The **link-state routing algorithm** is based on Dijkstra's algorithm and assumes the link-state routing protocol; the link costs and the network topology are known to all nodes

### What is an example of a link-state routing algorithm?

- [Dijkstra's algorithm](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm)

### Walk through an example of the link-state routing algorithm

1. Set immediate neighbor path costs
2. Append node $n$ with least cost path to priority queue
3. Update neighbors of $n$ with least cost known path to neighboring nodes
4. Repeat until minimum path is found

### What is the computational complexity of the link-state routing algorithm?

- Since we need to search through all nodes to find the node with minimum path cost (decreases each iteration), we need to search through $\frac{n(n+1)}{2}$ nodes so the runtime complexity is $O(n^2)$

### What is the main idea behind Distance Vector Routing algorithm?

- **DV (Distance Vector) Routing algorithm** is _iterative_ (the algorithm iterates until the neighbors do not have new updates to send to each other), _asynchronous_ (the algorithm does not require the nodes to be synchronized with each other), and _distributed_ (direct nodes send information to one another, and then they resend their results back after performing their own calculations, so the calculations are not happening in a centralized manner)
- The DV algorithm is based on the [Bellman-Ford algorithm](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm). The neighboring nodes exchange their distance vectors to update their own view of the network

### Walk through an example of the Distance Vector algorithm

1. Each node initializes a table to track distance vector of each node on each row (neighboring values set to infinity on first iteration)
2. Nodes exchange their distance vectors and they update their individual views of the network via Bellman-Ford equation
3. Nodes retrieve the distance vectors from the previous iteration (if changed) and repeat the same Bellman-Ford update

### When does count-to-infinity problem occur in the Distance Vector algorithm?

- When a link cost increases by a large amount and a routing loop occurs since a large change takes a long time to propagate among the nodes of a network

### How does poison reverse solve the count-to-infinity problem?

- It removes routing loops by having nodes tell their neighbors that the path to the other neighbors are _infinity_ which essentially removes the path from one neighbor to node to another neighbor
- However, poisoned reverse will **not** solve a general count to infinity problem involving 3 or more nodes that are not directly connected

### What is the Routing Information Protocol (RIP)?

- **RIP (Routing Information Protocol)** is based on the Distance Vector protocol
- The first version, released as a part of the BSD (Berkeley Software Distribution) version of Unix, uses _hop count_ as a metric (i.e. assumes link cost as 1). The metric for choosing a path could be shortest distance, lowest cost or a load-balanced path
- In RIP, routing updates are exchanged between neighbors periodically, using a _RIP response message_, as opposed to distance vectors in the DV Protocols. These messages, called RIP advertisements, contain information about sender’s distances to destination subnets
- If a router does not hear from its neighbor at least once every 180 seconds, that neighbor is considered to be no longer reachable (_broken link_). In this case, the local routing table is modified and changes are propagated. Routers send request and response messages over _UDP_, using port number 520, which is layered on top of _network-layer IP protocol_. RIP is actually implemented as an _application-level_ process
- Some of the challenges with RIP include updating routes, reducing convergence time, and avoiding loops/count-to-infinity problems

### What is the OSPF (Open Shortest Path First) protocol?

- **OSPF (Open Shortest Path First)** is a routing protocol which uses a link-state routing algorithm to find the best path between the source and the destination router. OSPF was introduced as an advancement of the RIP Protocol, operating in upper-tier ISPs (internet service provider)
- It is a _link-state protocol_ that uses _flooding_ of link-state information and a Dijkstra least-cost path algorithm. Advances include authentication of messages exchanged between routers, the option to use multiple same cost paths, and support for hierarchy within a single routing domain
- During operation, a graph (topological map) of the entire AS is constructed. Then, considering itself as the root node, each router computes the shortest-path tree to all subnets, by running _Djikstra’s algorithm_ locally. The link costs have been pre-configured by a network administrator. Given set of link weights, OSFP provides the mechanisms for determining least-cost path routing
- Whenever there is a change in a link’s state, the router broadcasts routing information to _all_ other routers in the AS, not just to its neighboring routers. It also broadcasts a link’s _state_ periodically even if its state hasn’t changed

### How does a router process advertisements?

- Every router within a domain that operates on OSPF uses **LSAs (Link-state Advertisements)** which communicates the router's local routing topology to all other local routers in the same OSPF area
- In practice, LSA is used for building a database (called the _link-state database_) containing all the link-states. LSAs are typically flooded to every router in the domain. This helps form a consistent network topology view. Any change in the topology requires corresponding changes in LSAs
- OSPF typically has a _refresh rate_ for LSAs, which has a default period of 30 minutes. If a link comes alive before this refresh period is reached, they routers connected to that link ensure LSA flooding. Since the process of flooding can happen multiple times, every router receives multiple copies of refreshes or changes - and stores the first received LSA change as new, and the subsequent ones as duplicates

How OSPF messages are processed in the router:

1. Initially, the LS update packets which contain LSAs from a neighboring router reaches the current router’s OSPF (which is the _route processor_). This is the first trigger for the route processor. As the LS Updates reach the router, a consistent view of the topology is being formed and this information is stored in the _link-state database_. Entries of LSAs correspond to the topology which is actually visible from the _current router_
2. Using this information from the _link-state database_, the current router calculates the shortest path using _SPF (Shortest Path First) algorithm_. The result of this step is fed to the _FIB (Forwarding Information Base)_
3. The information in the FIB is used when a data packet arrives at an interface card of the router, where the next hop for the packet is decided and its forwarded to the outgoing interface card

### What is hot potato routing?

- **Hot potato routing** is a technique/practice of choosing a path within the network, by choosing the closest egress point based on intradomain path cost (Interior Gateway Protocol/IGP cost)
- Hot potato routing simplifies computations for the routers as they are already aware of the IGP path costs. It makes sure that the path remains _consistent_, since the next router in the path will also choose to send the packet to the same egress point
- Hot potato routing also effectively reduces the network’s resource consumption by getting the traffic out as soon as possible
