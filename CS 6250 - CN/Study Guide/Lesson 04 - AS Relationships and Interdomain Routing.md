# Lesson 4: AS Relationships and Interdomain Routing

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### Describe the relationships between ISPs, IXPs, and CDNs

- **ISPs (Internet Service Providers)** can be categorized into three tiers or types: _access_ ISPs (or Tier-3), _regional_ ISPs (or Tier-2) and _large global scale_ ISPs (or Tier-1). There is a dozen of large scale Tier-1 ISPs that operate at a global scale, and essentially they form the “backbone” network over which smaller networks can connect. Some example Tier-1 ISPs include AT&T, NTT, Level-3, and Sprint. In turn regional ISPs connect to Tier-1 ISPs, and smaller access ISPs connect to regional ISPs

- **IXPs (Internet Exchange Points)** are interconnection infrastructures, which provide the _physical infrastructure_, where multiple networks (e.g., ISPs and CDNs) can interconnect and exchange traffic locally. As of 2019, there are approximately 500 IXPs around the world

- **CDNs (Content Delivery Networks)** are _networks_ that are created by content providers with the goal of having greater control of how the content is delivered to the end-users, and also to reduce connectivity costs. Some example CDNs include Google and Netflix. These networks have multiple data centers - and each one of them may be housing hundreds of servers – that are distributed across the world

### What is an AS?

- Each of the types of networks (e.g., ISPs and CDNs) may operate as an **AS (Autonomous System)**. An AS is a _group of routers_ (including the links among them) that operate under the _same_ administrative authority. An ISP, for example, may operate as a single AS or it may operate through multiple ASes. Each AS implements its own set of policies, makes its own traffic engineering decisions and interconnection strategies, and also determines how the traffic leaves and enters the network
- The _border routers_ of the ASes use the _BGP (Border Gateway Protocol)_ to exchange routing information with one another. In contrast, the _IGPs (Internal Gateway Protocols)_, operate within an AS and they are focused on “optimizing a path metric” within that network. Example IGPs include OSPF (Open Shortest Paths First), IS-IS (Intermediate System - Intermediate System), RIP (Routing Information Protocol), E-IGRP

### What kind of relationship does AS have with other parties?

1. **Provider-customer relationship**: based on a _financial settlement_ which determines how much the customer will pay the provider, so the provider forwards the customer’s traffic to destinations found in the provider’s routing table (including the opposite direction of the traffic as well)
2. **Peering relationship**:
   - Two ASes _share access_ to a subset of each other’s routing tables.
   - The routes that are _shared_ between two peers are often _restricted_ to the respective customers of each one. The agreement holds provided that the traffic exchanged between the two peers is **not** highly asymmetric.
   - Peering relationships are formed between _Tier-1 ISPs_ but also between _smaller ISPs_. In the case of Tier-1 ISPs, the two peers need to be of similar size and handle similar amounts of traffic. Otherwise, the larger ISP would lack the incentive to enter a peering relationship with a smaller size ISP.
   - In the case of peering between _two smaller size ISPs_, the incentive they both have is to save the money they would pay their providers by directly forwarding to each other their traffic, provided that there is a significant amount of traffic that is destined for each other (or each other’s customers)

### What is BGP?

- **BGP (Border Routing Protocol)**:

  > is a standardized exterior gateway protocol designed to exchange routing and reachability information among autonomous systems (AS) on the Internet. BGP is classified as a path-vector routing protocol, and it makes routing decisions based on paths, network policies, or rule-sets configured by a network administrator. -Wiki

### How does an AS determine what rules to import/export?

- Deciding which routes to export is an important decision with business and financial implications. This is the case because, _advertising_ a route for a destination to a neighboring AS, means that this route may be selected by that AS and traffic will start to flow through. Deciding which routes to advertise is a _policy decision_ and it is implemented through route filters
- **Route filters**: rules that determine which routes an AS will allow to advertise to other neighboring ASes
- Deciding routes to _export_ ($X$ is an AS):
  1. **Routes learned from customers**: routes that $X$ receives as _advertisements_ from its _customers_. Since provider $X$ is getting paid to provide reachability to a customer AS, it makes sense that $X$ wants to advertise these customer routes to as many other neighboring ASes as possible. This will likely cause more traffic towards the customer (through $X$) and hence more revenue to $X$
  2. **Routes learned from providers**: routes that $X$ receives as _advertisements_ from its _providers_. Advertising these routes doesn’t make sense, since $X$ does not have the financial incentive to carry traffic for its provider’s routes. These routes are withheld from $X$’s peers and other $X$’s providers, but they are advertised to $X$’s customers
  3. **Routes learned from peers**: routes that $X$ receives as _advertisements_ from its _peers_. As we saw earlier, it doesn’t make sense for $X$ to advertise to a provider A the routes that it receives from another provider B. Because in that case, these providers A and B are going to use $X$ to reach the advertised destinations without $X$ making revenue. The same is true for the routes that $X$ learns from peers
- When an AS receives multiple route advertisements towards the _same destination_, from _multiple ASes_, then it needs to _rank_ the routes before selecting which one to _import_. The routes that are preferred in order: (1) customer routes, (2) peer routes, and (3) provider routes. The reasoning behind this ranking is that an AS:
  1. Wants to ensure that routes towards its customers do **not** traverse other ASes unnecessarily generating costs
  2. Uses routes _learned from peers_ since these are usually “free” (under the peering agreement)
  3. Resorts to _import_ routes _learned from providers_ as these will add to costs

### What were original the design goals of BGP? What was considered later?

1. Scalability
2. Express routing policies
3. Allow cooperation among ASes
4. Security (not included in the original design goals for BGP)

### What are the basics of BGP?

- A pair of routers, known as **BGP peers**, exchange routing information over a semi-permanent TCP port connection called a **BGP session**
- After a session is established between BGP peers, the peers can exchange **BGP messages** to provide reachability information and enforce routing policies. We have two types of BGP messages:
  1. `UPDATE`: messages advertise new routes and updates to existing routes (_announcements_) or messages are sent when a previously announced route is removed (_withdrawals_)
  2. `KEEPALIVE`: messages are exchanged to keep a current session going
- **BGP prefix reachability**: destinations are represented by **IP Prefixes**. Each prefix represents a subnet or a collection of subnets that an AS can reach
- **Path attributes and BGP routes**: in addition to the reachable IP prefix field, advertised **BGP routes** consist of a number of **BGP attributes**. Two notable attributes are `AS-PATH` and `NEXT-HOP`:
  1. `AS-PATH`: each AS, as identified by the AS’s **ASN (Autonomous System Number)**, that the route passes through is included in the `AS-PATH`. This attribute is used to _prevent loops_ and to choose between multiple routes to the same destination, the route with the shortest path
  2. `NEXT-HOP`: refers to the IP address (interface) of the _next-hop router_ along the path towards the destination. Internal routers use the field to store the IP address of the border router

### What is the difference between iBGP and eBGP?

- A BGP session between a pair of routers in _two different ASes_ is called **eBGP (external BGP)** session, and a BGP session between routers that belong to the _same_ AS is called **iBGP (internal BGP)** session
- The eBGP speaking routers _learn routes to external prefixes_ and they disseminate them to all routers within the AS. This dissemination is happening within iBGP sessions
- Dissemination of routes within the AS is done by establishing a _full mesh of iBGP sessions_ between the _internal routers_. Each eBGP speaking router has an iBGP session with every other BGP router in the AS, so that it can send updates about the routes it learns (over eBGP)

### What is the difference between iBGP and IGP-like protocols (RIP or OSPF)?

- iBGP is **not** another IGP-like protocol (e.g., RIP or OSPF). IGP-like protocols are used to _establish paths between the internal routers_ of an AS based on specific costs within the AS. In contrast, iBGP is _only_ used to disseminate _external routes_ within the AS

### How does a router use the BGP decision process to choose which routes to import?

- A router compares routes, by going through the _list of attributes_ in the _route advertisements_. In the simplest scenario, where there is no policy in place (meaning it doesn’t matter which route will be imported), the router uses the attribute of the _path length_ to select the route with the fewest number of hops. But in practice, this simple scenario is rarely the case
- Influencing the route decision using the **LocalPref**: used to prefer routes learned through a _specific AS_ over other ASes. For example, suppose AS $B$ learns of a route to the same destination $x$ via $A$ and $C$. If $B$ prefers to route its traffic through $A$, due to peering or business, it can assign a _higher_ LocalPref value to routes it learns from $A$. And therefore, by using LocalPref, AS $B$ can _control_ where the traffic _exits_ the AS. In other words, it will influence which routers will be selected as _exit points_ for the traffic that leaves the AS (_outbound traffic_)
- Influencing the route decision using the **MED (Mutli-Exit Discriminator)** attribute: used by ASes _connected by multiple links_ to designate which of those links are preferred for _inbound traffic_. For example, the network operator of AS $B$ will assign different MED values to its routes advertised to AS $A$ through $R1$ and different MED values to its routes advertised through $R2$. As a result of different MED values for the same routes, AS $A$ will be influenced to choose $R1$ to forward traffic to AS $B$, if $R1$ has _lower_ MED value, and if all other attributes are equal
- _How are the attributes controlled_?
  1. Locally by the AS (e.g., LocalPref)
  2. By the neighboring AS (e.g., MED)
  3. They are set by the protocol (e.g., if a route is learned through eBGP or iBGP)

### What are 2 main challenges with BGP? Why?

- _Misconfigurations and faults_ which results in an excessively large number of updates which in turn can result in route instability, router processor and memory overloading, outages, and router failures
- Misconfigurations and faults can be reduced by limiting the _routing table_ size and also by limiting the number of _route changes_

### What is an IXP?

- IXPs are _physical infrastructures_ that provide the means for ASes to interconnect and directly exchange traffic with one another
- The ASes that interconnect at an IXP are called **participant ASes**. The physical infrastructure of an IXP is usually a network of switches that are located either in the same physical location, or they can be distributed over a region or even at a global scale

### What are four reasons for IXPs increased popularity?

1. IXPs are interconnection hubs handling large traffic volumes
2. Important role in mitigating DDoS attacks
3. Real-world infrastructures with a plethora of research opportunities
4. IXPs are active marketplaces and technology innovation hubs

### Which services do IXPs provide?

1. **Public peering**: most well-known use of IXPs is public peering service - in which two networks use the IXP’s network infrastructure to establish a connection to exchange traffic based on their bilateral relations and traffic requirements
2. **Private peering**: most operational IXPs also provide a private peering service (Private Interconnects - PIs) that allow _direct_ traffic exchange between two parties of a PI and don’t use the IXP’s public peering infrastructure
3. **Route servers and SLAs (Service Level Agreements)**: allows participants to arrange instant peering with a large number of _co-located participant networks_ using essentially a single agreement/BGP session
4. **Remote peering through resellers**: allows third-parties to _resell_ IXP ports wherever they have infrastructure connected to the IXP. These third-parties are allowed to offer the IXP’s service remotely, which allows networks that have little traffic to also use the IXP. This also enables **remote peering** - networks in distant geographic areas can use the IXP
5. **Mobile peering**: a scalable solution for interconnection of mobile GPRS/3G networks
6. **DDoS black-holing**: customer-triggered black-holing, which allows users to alleviate the effects of DDoS attacks against their network
7. **Free value-added services**: a few IXPs such as Scandinavian IXP Netnod offer free value-added services like Internet Routing Registry (IRR), consumer broadband speed tests9, DNS root name servers, country-code top-level domain (ccTLD) nameservers, as well as distribution of the official local time through NTP

### How does a route server work?

- **RS (Route Server)**:
  - _Collects and shares_ routing information from its peers or participants that connects with (i.e. IXP members that connect to the RS)
  - Executes it’s _own_ BGP decision process and also _re-advertise_ the resulting information (i.e. best route selection) to _all RS’s peer routers_
- A typical routing daemon maintains a **RIB (Routing Information Base)** which contains all BGP paths that it receives from its peers - the **Master RIB**. The RS also maintains _AS-specific RIBs_ to keep track of the individual BGP sessions they maintain with each participant AS
- A RS maintains multi-lateral peering sessions through:
  1. **Import filters**: ensure that each member AS only advertises routes that it should advertise
  2. **Export filters**: triggered by the IXP members themselves to restrict the set of other IXP member ASes that receive their routes
