# Lesson 12: Applications (CDNs and Overlay Networks)

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### What is the drawback to using the traditional approach of having a single, publicly accessible web server?

1. First, with the modern Internet, users are located _all over the globe_. No matter where a single, massive data center is placed, there’s potentially _vast geographic distance between the users and the data center_. That’s a problem because the server-to-client packets will have to traverse lots of communication links between many ISPs, and if just one of those links has a throughput lower than the video playout rate, there will be annoying _interruptions and delays_ for the user
2. Second, what happens when a video goes viral? Think of popular movie trailers, or important breaking news clips. Popular videos result not only in a spike in demand, but many, many requests for the exact same video clip, and thus, the exact same data. It’s wasteful for a single massive data center to repeatedly be sending the exact same data over the same communication link over and over again. Not only does this waste bandwidth, but the Internet video company also loses a lot of money, as _they have to pay their ISP for every byte of data transmitted_
3. The third major drawback to using a single, massive data center is that it is also a _single point of failure_. If there is a natural disaster or a massive power outage in the area, the entire data center could be taken temporarily or permanently offline. Likewise, if the data center’s links to the Internet are disrupted, it will not be able to distribute video content

### What is a CDN?

- **CDNs (Content Distribution Networks)** are networks of multiple, _geographically distributed servers and/or data centers_, with copies of content (videos, but also many other types of Web content), that direct users to a server or server cluster that can best serve the user’s request. CDNs address all of the issues we just discussed (above), but there are new challenges that come with this approach

### What are the six major challenges that Internet applications face?

1. **Peering point congestion**: there’s the business and financial motivation to upgrade the “first mile” (like web hosts) and the “last mile” (end users), but not for the “middle mile” where expensive _peering points_ between networks with no revenue happen. These points end up being bottlenecks causing packet loss and increased latency
2. **Inefficient routing protocols**: BGP has worked really well over the decades and the massive growth of the best-effort Internet, but it was never designed for modern demands. Between the algorithm only using AS hop count and not taking into account other factors (like congestion, latencies, etc.), and BGP’s well-documented vulnerabilities to malicious actions - it’s _not an efficient inter-domain routing protocol_ for the modern Internet
3. **Unreliable networks**: outages happen _all the time_. Some are accidents - like misconfigured routers, power outages in an area, accidental severing of undersea fiber cables. Others are malicious, such as DDoS attacks or BGP hijacking. And others yet are from natural disasters
4. **Inefficient communication protocols**: like BGP, _TCP was not designed for the demands of the modern Internet_. Although it provides reliability and congestion avoidance, there’s a lot of _overhead_. Because it requires an “Ack” for each window of data packets sent, the distance between the server and the end user becomes the overriding bottleneck, and despite all the research into ways to improve TCP, enhancements are slow to actually get implemented across the whole Internet
5. **Scalability**: scaling internet applications are able to respond to current demand by changing resource usage, whether it be a video unexpectedly going viral, or a planned event (like Black Friday shopping traffic peaks). Scaling up infrastructure is expensive and takes time, but it is _hard to forecast what capacity needs will be_
6. **Application limitations and slow rate of change adoption**: as mentioned with TCP, even if there are better protocols developed to meet the needs of the modern Internet, especially with video streaming, historically it can take a _long time for better protocols to get adopted_. For instance, old browsers, like Internet Explorer 6, do not support newer protocols, and so even if the server side is upgraded, there’s no benefit unless the end users also upgrade to client software that also supports the newer protocols

### What are the major shifts that have impacted the evolution of the Internet ecosystem?

- The Internet wasn’t designed for _large scale content delivery_ (it was just a research network originally!), but that’s what it has evolved into. There is an increased demand for online content, especially videos. _Content and video_ accounts for the _largest fraction of today’s Internet traffic_. This demand has spurred the development and growth of CDNs, in place of traditional single, massive data centers
- The second shift is a _“topological flattening”_ - the traditional topology (hierarchical) has _transitioned to more flat_. Originally and traditionally, tier 1 ISPs formed the backbone of the Internet, and connected at relatively few points directly to each other. But if you recall from one of our earlier lectures, _IXPs_ are infrastructures offering interconnections between networks. They have been increasing in number and popularity due to:
  1. The services they offer
  2. They _lower_ network operations costs for the ISPs and interconnection costs. In fact, they’ve grown so large and complex that we need more research in order to update our understanding of _AS-level topology_

### Compare the “enter deep” and “bring home” approach of CDN server placement

- **Enter deep**: the CDNs place _many smaller server clusters “deep” into the access networks around the world_. Akamai is a good example of a third party CDN with the “enter deep” philosophy, as they have clusters in over 1700 locations. With this philosophy, the goal is to make the distance between a user and the closest server cluster as small as possible, which reduces the delay and increases the available throughput for each user. However, the downside to this highly distributed approach is that it is _much more difficult to manage and maintain so many clusters_
- **Bring home**: CDNs place _fewer larger server clusters at key points (typically in IXPs, not in access networks)_, “bringing the ISPs home.” There’s not as many server clusters to manage or maintain, so those tasks are easier, but the downside is that the users will experience _higher delay and lower throughput_

### What is the role of DNS in the way CDN operates?

- By intercepting the requests with DNS, CDNs have the opportunity to choose where to direct users, based on location and/or current conditions (see lecture for more details)

### What are the two main steps in CDN server selection?

1. The first step consists of _mapping the client to a cluster_. Recall that a CDN constitutes of geographically distributed clusters with each cluster containing a set of server
2. In the next step, _a server is selected from the cluster_

### What is the simplest approach to select a cluster? What are the limitations of this approach?

- The simplest strategy is to pick the _geographically closest cluster_ “as the crow flies.” For instance, assume I am watching a video from Georgia Tech campus in Atlanta, and there are three clusters located at Charlotte, Boston, and Los Angeles in the US. Using this strategy, the content will be served from the Charlotte cluster. This simple strategy can work well in a lot of cases. However, it has some limitations:
  - Recall from our example scenario in the previous section - `ExampleCDN` name server system (which is where the server selection happens) didn’t directly interact with the user, but rather with the _user’s Local Domain Name Server (LDNS)_. So, picking the geographically closest cluster is really _“picking the cluster closest to the LDNS”_ and not “closest to the user.” Most of the time, that works ok, but some customers use a remote LDNS. To overcome this, there have been suggestions made to include the client IP in the interaction between the `ExampleCDN` name server system and the LDNS. This allows the `ExampleCDN` name server system to know where the client is located
  - Another very important limitation is that the cluster which is geographically closest may not be the best choice in terms of actual _end-to-end network performance_. This can happen because of multiple reasons. One, due to routing _inefficiencies in routing protocols such as BGP_, the actual network path to the geographically closest server might actually be longer than the path to an alternative cluster. This can lead to a _higher RTT_, even though the server is closest geographically. Another important reason could be that the path to the geographically closest cluster or the cluster itself could be _congested_

### What metrics are could be considered when using measurements to select a cluster?

- One could use _network-layer metrics_ such as _delay_, _available bandwidth_ or both. A better strategy could be to use _application-layer metrics_. For instance, if the content to be delivered is video, metrics such as _re-buffering ratio_ and _average bitrate_ can be used in cluster selection. Similarly, for web-browsing, application-layer performance indicators such as _page load time_ can be used

### How are the metrics for cluster selection obtained?

- **Active measurements**: one way would be to use active measurements. Thus, the LDNS could probe multiple clusters, such as by _sending a ping request_ to multiple clusters for monitoring the RTT and then use the “closest” server. However, most of the LDNS are _not equipped to perform such active measurements_. Furthermore, this would also create _a lot of traffic_
- **Passive measurements**: another strategy could be that the CDN’s name server system uses passive measurements to keep track of the network conditions. The name server system in the CDN could keep a track of the performance metrics based on the current traffic conditions. Note that this information can be kept at an _aggregate level_. For instance, by clubbing IPs from the same subnet together. This is because _IPs under the same subnet_ are most likely to have _similar paths_ to different clusters, thus experiencing similar end-to-end performance. Thus, the best cluster for same subnet can be noted down based on the performance existing sessions are observing. Next time, a new client requests for content, it can be routed to the best performing cluster based on the _existing session information_
  - Limitations: note that this kind of cluster selection strategy requires a _centralized controller_ which has a real-time view of the network conditions between all client-cluster pairs. Given the scale of today’s networks, it can be challenging to design a purely centralized system

### Explain the distributed system that uses a 2-layered system. What are the challenges of this system?

- A _coarse-grained global layer_ operates at larger time scales (timescale of a few _tens of seconds or minutes_). This layer has a _global view of client quality measurements_. It builds a data-driven prediction model of video quality
- A _fine-grained per-client decision layer_ that operates at the _millisecond_ timescale. It makes actual decisions upon a _client request_. This is based on the latest (but possibly stale) pre-computed global model and up-to-date per-client state
  - Limitations: note that this kind of distributed system needs to have data for _different subnet-cluster pairs_. Thus, some of the clients deliberately need to be routed to _sub-optimal clusters_

### What are the strategies for server selection? What are the limitations of these strategies?

- One solution to this can be to do some load-balancing and route a client to the least-loaded server. While this solves the random assignment problem, it is still not optimal
  - Limitations: recall that a CDN server is responsible for distributing content for a variety of content providers. Thus, the same cluster could be serving video content and also web content. Similarly, it could also be serving the same type of content for a variety of content providers. E.g., serve video from different video providers. Thus, not all the servers have all the content at a time. This is because the servers have limited disk space and proactively fetching all the content to the servers is simply not feasible
- A simple solution is then to _map the requests based on the content_. Essentially, requests for the same piece of content can be mapped to the same machine by using some sort of content-based hashing. E.g. Assume a request for `exampleCDN.com/contentFoo`. A hash function calculates hash of `contentFoo` and returns a server. And the client can be mapped to that server. Thus, all the requests for `contentFoo` will be mapped to the same server
  - Limitations: while this idea is fairly simple, it has some challenges. One of the challenge arises from the fact that the _cluster environment is quite dynamic_ and is characterized by frequent machine failures and load changes. Now, when there is a change in the cluster environment such as when a machine fails, the _hash table_ used to map the content to servers _needs to be recomputed_
- One way to handle this is to recompute the hash function for all the objects. However, that is simply expensive and sub-optimal. An ideal solution would be to _only move the objects that were assigned to the server_

### What is consistent hashing? How does it work?

- **Consistent hashing** (distributed hash table) tends to balance load, by assigning roughly the same number of content IDs, and requires relatively little movement of these content IDs when nodes join and leave the system
- The main idea behind consistent hashing is that servers and the content objects are mapped to the same _ID space_
- It can be proved that the solution is _optimal_, which means that least number of keys need to be remapped to maintain load-balance on an average. On a side note, this algorithm was proposed as a part of a popular distributed lookup protocol, known as _Chord_ and was also used for _content lookup in peer-to-peer applications_ such as BitTorrent, Napster.

### Why would a centralized design with a single DNS server not work?

1. First, it introduces a _single point of failure_. If that single server collapses then the entire Internet would not be able to work either!
2. Second, it would be very difficult for a single server to handle all the _volume of the querying traffic_. A single DNS server would have to process a very large number of DNS queries
3. Third, this model is based on a _centralized database which cannot be close to all querying clients_. This model would cause significant delays and slow performance for the clients which are geographically distant and thus they might have to communicate over _slow or congested links_
4. Finally, maintaining this centralized database would be a big problem as we would have to _update a huge database_ with updates _for every single host in the Internet_

### What are the main steps that a host takes to use DNS?

1. The user host runs the client side of the DNS application
2. The browser extracts the hostname (e.g., `www.google.com`) and passes it to client side of the DNS application
3. DNS Client sends a query containing the hostname of DNS
4. DNS Client eventually receives a reply which included IP address for the hostname
5. As soon as the host receives the IP addresses, it can initiate a TCP connection to the HTTP server located at that port at that IP

### What are the services offered by DNS, apart from hostname resolution?

- **Mail server/host aliasing**: email servers have to have simple and mnemonic names. E.g., `@hotmail.com`. However, the canonical hostname can be difficult to remember e.g., `relay2.west-coast.hotmail.com`. DNS is used to get the canonical hostname (and IP address) for an alias hostname. Also, a host can have one or more names. If there are two hostnames then this usually is a combination of canonical and mnemonic hostnames. DNS can be used to find the canonical hostname for a given host and also obtain an IP for that host
- **Load distribution**: busy websites may be replicated over multiple servers. When a client makes a DNS query, the DNS server responds with the entire set of addresses but rotates the address ordering with each reply. This helps in distributing the traffic across servers

### What is the structure of DNS hierarchy? Why does DNS use a hierarchical scheme?

1. **Root DNS servers**: there are 13 servers, each of which is a network of replicated servers mostly located in North America. As of May 2019, the total number of server instances is 984
2. **Top level domain (TLD) servers**: These servers are responsible for the top level domains such as `.com`, `.org`, `.edu`, etc and also all of the country top level domains such as `.uk`, `.fr`, `.jp`
3. **Authoritative servers**: An organization’s authoritative DNS server keeps the DNS records that need to be publicly accessible, such as the domain name - IP mappings for web serves and mail servers of that organization
4. **Local DNS servers**: even though this type of servers is not considered as strictly belonging to the DNS hierarchy, nevertheless it is considered central to the overall DNS architecture. _Each ISP_, such as a university, a company or a small residential ISP, _has one or more local DNS servers_. Hosts that connect to an ISP are provided with the IP addresses of one or more local DNS servers. So, when a host makes a DNS query, the query is sent to the provided local DNS server, which in turn _acts as a proxy_, and it _forwards the query into the DNS hierarchy_

- The DNS uses a hierarchical scheme to solve the scalability problem

### What is the difference between iterative and recursive DNS queries?

- In the **iterative query** process, the querying _host_ is referred to a _different DNS server in the chain_, until it can fully resolve the request
- In the **recursive query**, the querying _host_, and _each DNS server in the chain_ queries the next server and _delegates_ the query to it

### What is DNS caching?

- One way to make the DNS resolution faster, is to cache the responses. This will help in reducing the performance delay and make it more efficient. The idea of **DNS caching** is that, in both iterative and recursive queries, after a server receives the DNS reply of mapping from any host to IP address, it stores this information in the _cache memory_ before sending it to the client

### What is a DNS resource record?

- The DNS servers store the mappings between hostnames and IP addresses as **RRs (resource records)**. These resource records are contained _inside the DNS reply messages_. A DNS resource record has four fields: (_name, value, Type, TTL_). The TTL specifies the time (in sec) a record should remain in the cache. The name and the value depend on the type of the resource record

### What are the most common types of resource records?

1. `TYPE=A`: the name is a _domain name_ and value is the _IP address of the hostname_ (e.g., `abc.com`, `190.191.192.193`, `A`)
2. `TYPE=NS`: the name is the _domain name_, and the value is the _appropriate authoritative DNS server_ that can obtain the IP addresses for hosts in that domain (e.g., `abc.com`, `dns.abc.com`, `NS`)
3. `TYPE=CNAME`: the name is the _alias hostname_, and the value is the _canonical name_ (e.g., `abc.com`, `relay1.dnsserver.abc.com`, `CNAME`)
4. `TYPE=MX`: the name is the alias _hostname of a mail server_, and the value is the _canonical name_ of the email server (e.g., `abc.com`, `mail.dnsserver.abc.com`, `MX`)

### Describe the DNS message format

- The first field is an _ID_ that is an identifier for the query and it allows the client to match queries with responses
- The _flags_ section have _multiple fields_. For example, a field allows to specify if the DNS message is a query or response. Another field specifies if a query is recursive or not
- The _question_ section contains _information about the query that is being made_ for example the hostname that is being queried, the type of the query (A, MX, etc)
- In the _answer_ section, and if the message is a _reply_, we will have the _resource records_ for the hostname that was originally queried.
- In the _authority_ section, we have resource records for more _authoritative servers_
- The _additional_ section contains other helpful records. For example, if the original query was for an MX record, then the answer section will contain the resource record for the canonical hostname of the mail server, and the additional section will contain the IP address for the canonical hostname

### What is IP Anycast?

- The main goal of **IP anycast** is to _route a client to the “closest” server_, as determined by BGP (Border Gateway Protocol), a routing protocol used for inter-AS routing. This is achieved by assigning the _same IP address to multiple servers_ belonging to _different clusters_. Now, each of these servers will use the standard BGP to advertise this IP address. Thus multiple BGP routes for the same IP address corresponding to different cluster locations will propagate in the public Internet. Now when a BGP router receives multiple route advertisements for this IP address, it would treat them as multiple paths to the same locations, although, in reality these routes correspond to different physical locations. In the end, the _shortest path will be stored and used for routing packets_
- Using this strategy can enable CDNs to deliver content using the _“closest” server to a client_

### What is HTTP Redirection?

- **HTTP redirection**: the protocol works at the _HTTP-layer in the network stack_. Essentially, when a client sends a `GET` request to a server, say $A$, it can _redirect_ the client to another server, say $B$, by sending an HTTP response with a code `3xx` and the name of the new server. This essentially means that the client should now fetch the content from this new server. Note that this would incur _at least an additional HTTP request_, which can correspond to one or more RTTs, for the client to fetch the content. While this makes this protocol inefficient, it can be still useful in certain cases
- A recent measurement study reports that YouTube uses this kind of mechanism for _load balancing_. According to the study, YouTube first tries to use HTTP redirection for _sharing the load within a cluster_, and then can also use it to redirect clients to a _different cluster_ if the former is not enough
