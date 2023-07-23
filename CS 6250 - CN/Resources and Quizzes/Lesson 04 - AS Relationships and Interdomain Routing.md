# Lesson 4: AS Relationships And Interdomain Routing

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

- [Interdomain Internet Routing](http://web.mit.edu/6.829/www/currentsemester/papers/AS-bgp-notes.pdf)

- [BGP routing policies in ISP networks](https://www.cs.princeton.edu/~jrex/papers/policies.pdf)

- [On the importance of Internet eXchange Points for today’s Internet ecosystem](https://cryptome.wikileaks.org/2013/07/ixp-importance.pdf)

- [Peering at Peerings: On the Role of IXP Route Servers](https://people.csail.mit.edu/richterp/imc238-richterA.pdf)

### Book References

Kurose-Ross (6th Edition) Sections: 1.3.3, 4.6.3.

### Optional Readings

- [Investigating Interdomain Routing Policies in the Wild](https://people.cs.umass.edu/~phillipa/papers/AnwarIMC15.pdf)

- [BGP Communities: Even more Worms in the Routing Can](https://people.mpi-inf.mpg.de/~fstreibelt/preprint/communities-imc2018.pdf)

- [On the scalability of BGP: the roles of topology growth and update rate-limiting](https://www.cc.gatech.edu/home/dovrolis/Papers/bgp-scale-conext08.pdf)

- [O Peer, Where Art Thou? Uncovering Remote Peering Interconnections at IXPs](https://www.inspire.edu.gr/wp-content/pdfs/uncovering_remote_peering_interconnections_v1.pdf)

- [Detecting BGP Configuration Faults with Static Analysis](https://www.usenix.org/legacy/events/nsdi05/tech/feamster/feamster.pdf)

## Section Quizzes

### Lesson 4: AS Relationships And Interdomain Routing 1 Quiz

1. _The internet topology has been evolving from a <...> structure into a <...> structure_.
   - Hierarchical, flat
2. _An Autonomous System is a group of routers that operate under <...> administrative <...>_.
   - The same, authority
3. _Autonomous Systems implement their own set of policies, make their own traffic engineering decisions and interconnection strategies, and determine how traffic leaves and enters the network_.
   - True
4. _The BGP protocol is used within an AS and focuses on optimizing a path metric within the network. Examples of BGP protocols are OSPF (Open Shortest Paths First) and Routing Information Protocol_.
   - False

### Lesson 4: AS Relationships And Interdomain Routing 2 Quiz

1. _In a peering relationship, the traffic exchanged between the two peers must be highly asymmetric so that there is enough incentive for both parties to peer with each other_.
   - False
2. _A customer-provider relationship between ASes is based on a financial settlement, which determines how much the customer will pay the provider. The provider takes care of connecting the customer network with destinations found in the provider's routing table. The customer pays regardless of the direction of the traffic_.
   - True
3. _There is no incentive for smaller ISPs to peer with each other_.
   - False
4. _Provider ASes have a financial incentive to forward as much of their customers’ traffic as possible_.
   - True
5. _Select the correct order for an AS to import its routes based on their incentive_.
   1. Routes learned from customers
   2. Routes learned from peers
   3. Routes learned from providers

### Lesson 4: AS Relationships And Interdomain Routing 3 Quiz

1. _What is the difference between iBGP and eBGP_?
   - Both flavors (iBGP and eBGP) take care of disseminating _external_ routes. An eBGP session is established between two border routers that belong to different ASes. An iBGP session is established between routers that belong to the same AS. Once a router hears about a route that is learned through eBGP, then it disseminates that route to other internal routers in the same AS, using iBGP
2. _What is the difference between iBGP and IGP_?
   - IGP-like protocols are used to establish paths between the internal routers of an AS based on specific costs within the AS. In contrast, iBGP is only used to disseminate external routes within the AS

### Lesson 4: AS Relationships And Interdomain Routing 4 Quiz

1. _A router within an AS decides which route to export by first applying import policies to exclude routes entirely from further consideration_.
   - True
2. _The LocalPref attribute is used to prefer routes learned through a specific AS over other ASes for <...> traffic_.
   - Outbound
3. _Assume that AS X learns of a route to the same destination a via AS Y and AS Z. If X prefers to route its traffic through Z due to peering or business, it can assign a <...> LocalPref value to routes it learns from Z, and thus using LocalPref, AS X can control where traffic exits the AS_.
   - Higher
4. _The MED (Multi-Exit Discriminator) value is used by ASes connected by multiple links to designate which of those links are preferred for <...> traffic_.
   - Inbound
5. _Assume that AS X prefers routes advertised to AS Y to go through R1 as opposed to R2. For AS Y to be influenced to choose R1 to forward traffic to AS X, R1 must have a <...> MED value, assuming that all other attributes are equal_.
   - Lower

### Lesson 4: AS Relationships And Interdomain Routing 5 Quiz

1. _One of the services offered by IXPs is protection against <...> attacks_.
   - DDoS
2. _Participation of an AS in an IXP is free_.
   - False
3. _IXPs handle large volumes of traffic_.
   - True
4. _One of the reasons why networks choose to peer at IXPs is because critical players in today’s Internet ecosystem often “incentivize” other networks to connect at IXPs_.
   - True
5. _Private peering PIs do not use the IXP’s public peering infrastructure_.
   - True
6. _IXPs users may use route servers for an additional cost_.
   - False

### Lesson 4: AS Relationships And Interdomain Routing 6 Quiz

1. _Route Servers keep track of the BGP sessions they maintain with each participant AS through RIBs_.
   - True
2. _<...> filters are applied to ensure that each member AS only advertises routes that it should advertise_.
   - Import
