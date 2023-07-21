# Lesson 3: Intradomain Routing

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

[Experience in Black-box OSPF Measurement](http://conferences.sigcomm.org/imc/2001/imw2001-papers/82.pdf)

### Book References

Kurose-Ross (6th Edition) Sections: 4.5.1, 4.5.2, 4.6.1, 4.6.2.

### Optional Readings

- [Hot Potatoes HeatUp BGP Routing](https://www.cs.princeton.edu/~jrex/papers/hotpotato.pdf)

- [Traffic Engineering With Traditional IP Routing Protocols](https://www.cs.princeton.edu/~jrex/teaching/spring2005/reading/fortz02.pdf)

- [Dynamics of Hot-Potato Routing in IP Networks](https://www.cs.princeton.edu/~jrex/papers/sigmetrics04.pdf)

- [OSPF Monitoring: Architecture, Design and Deployment Experience](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.86.8523&rep=rep1&type=pdf)

## Section Quizzes

### Lesson 3: Intradomain Routing 1 Quiz

1. _In this lecture, we discuss intradomain routing, where all the nodes and subnets are owned and managed by the same organization. (In contrast, interdomain routing is about routing between different organizations – such as between two ISPs.) Before we begin talking about intradomain routing algorithms, what could weights on the graph edges represent in these diagrams, when we are seeking the least-cost path between two nodes_?
   - Length of the cable
   - Time delay to traverse the link
   - Monetary cost
   - Link capacity
   - Current load on the link
2. _A packet is <...> when it is moved from a router’s input link to the appropriate link_.
   - Forwarded
3. _Determine which action is network-wide (i.e. involves multiple routers)_. Routing
4. _Intradomain routing must involves multiple administrative domains_.
   - False

### Lesson 3: Intradomain Routing 2 Quiz

1. _In the previous example, node $u$ was the source node, and distances were calculated from $u$ to each other node. Consider the same example, but let $x$ be the source node. Notice that node $x$ has more direct neighbors than $u$ does. Suppose $x$ is executing the link-state algorithm as discussed, and has just finished the initialization step. Which of the following statements are true_?
   - Node $x$ will execute the _same_ number of iterations that node $u$ did, as the number of immediate neighbors has no impact on the number of iterations the algorithm requires
2. _Upon termination of Dijkstra’s algorithm, all nodes in a network are aware of the entire network topology_.
   - True
3. _Consider the following topology. Let b be the source node. Use Dijkstra’s algorithm to determine the cost of the least cost path from node b to all other nodes in the network upon termination of the algorithm_.
   - `b-a`: 3
   - `b-a-c`: 3 + 1 = 4
   - `b-a-c-d`: 3 + 1 + 2 = 6
   - `b-a-c-e`: 3 + 1 + 4 = 8
   - `b-a-c-e-f`: 3 + 1 + 4 + 1 = 9

### Lesson 3: Intradomain Routing 3 Quiz

1. _Select the words that can be used to describe the distance vector algorithm_.
   - Distributed
   - Iterative
   - Asynchronous
2. _Determine which of the following can cause the count-to-infinity problem_.
   - Routing loops

### Lesson 3: Intradomain Routing 4 Quiz

1. _Dijkstra’s algorithm is a <...> routing algorithm, which is also referred to as a <...> algorithm_.
   - Global
   - Link-state
2. _The Bellman Ford equation is used by the <...> algorithm_.
   - Distance vector
3. _Select all statements that correctly complete the sentence. The Routing Information Protocol (RIP) is an example of <...>_.
   - A distance vector algorithm
   - An intradomain routing algorithm

### Lesson 3: Intradomain Routing 5 Quiz

1. _There may be multiple egress points from an administrative domain to an external destination_.
   - True
2. _Hot potato routing always selects the egress point that is geographically closest to the ingress point_.
   - False, hot potato routing is a technique/practice of choosing a path within the network, by choosing the closest _egress_ point based on intradomain path cost (Interior Gateway Protocol/IGP cost)
