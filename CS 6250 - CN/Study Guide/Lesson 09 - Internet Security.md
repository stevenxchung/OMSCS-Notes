# Lesson 9: Internet Security

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### What are the properties of secure communication?

- **Confidentiality**: this is perhaps the first thing that comes to our mind when we think about a secure communication. We want to ensure that the message that is sent from the sender to the receiver is only available to the two parties. An attack scenario is that we have an intruder that can eavesdrop on the communication by sniffing or recording the exchanged messages. One measure to increase the chances that a communication is confidential is to _encrypt the message_ so that even if the communication is intercepted, the message would be meaningless to the attacker
- **Integrity**: in addition to confidentiality, it is important to _ensure the message has not been somehow modified while in transit_ from the sender to the receiver. For example, an intruder could attack by modification, insertion or deletion of part of the messages send. As a countermeasure, we can introduce mechanisms that check for the integrity of the message
- **Authentication**: when two parties are communicating, it is important to _ensure that the two parties are who they say they are_. For example, an intruder may try to steal information by impersonating another entity on the network. As a countermeasure against these attacks we use authentication mechanisms to verify the identity of a user
- **Availability**: a communication is not useful unless the information (or the service that is provided) is indeed _available_. So we will need to ensure that multiple aspects of the communication channel are functioning appropriately and we can cope with possible failures such as power outages, hardware failures, etc. or attacks that aim to render the system unavailable such as denial of service attacks

### How does RRDNS (Round Robin DNS) work?

- _Distributes the load of incoming requests_ to several servers at a single physical location. It responds to a DNS request with a list of DNS A records, which it then cycles through in a round robin manner. The DNS client can then choose a record using different strategies – choose the first record each time, use the closest record in terms of network proximity, etc. Each A record also has a Time to Live (TTL) for this mapping which specifies the number of seconds the response is valid. If the lookup is repeated while the mapping is still active, the DNS client will receive the same set of records, albeit in a different order

### How does DNS-based content delivery work?

- **CDNs (Content Distribution Networks)** also use DNS-based techniques to distribute content but using more complex strategies. For example CDNs _distribute the load amongst multiple servers at a single location_, but also distribute these servers _across the world_. When accessing the name of the service using DNS, the CDN computes the _nearest edge server_ and returns its IP address to the DNS client. It uses sophisticated techniques based on network topology and current link characteristics to determine the nearest server. This results in the content being moved ‘closer’ to the DNS client which increases responsiveness and availability. CDNs can react quickly to changes in link characteristics as their TTL is lower than that in RRDNS

### How do Fast-Flux Service Networks work?

- **FFSN (Fast-Flux Service Networks)** is an extension of the ideas behind RRDNS and CDN. As its name suggests, it is based on a _rapid_ change in DNS answers, with a TTL lower than that of RRDNS and CDN. One key difference between FFSN and the other methods is that _after the TTL expires, it returns a different set of A records from a larger set of compromised machines_. These compromised machines act as proxies between the incoming request and control node/mothership, forming a resilient, robust, one-hop overlay network

### What are the main data sources to identify hosts that likely belong to rogue networks, used by FIRE (FIRE: FInding Rogue nEtworks system)?

1. **Botnet command and control providers**: several botnets still rely on centralized command and control (C&C). So a bot-master would prefer to host their C&C on networks where it is unlikely to be taken down. The two main types of botnets this system considers are IRC-based botnets and HTTP-based botnets
2. **Drive-by-download hosting providers**: drive-by-download is a method of malware installation without interaction with the user. It commonly occurs when the victim visits a web page that contains an exploit for their vulnerable browser
3. **Phish housing providers**: this data source contains URLs of servers that host phishing pages. Phishing pages usually mimic authentic sites to steal login credentials, credit card numbers and other personal information. These pages are hosted on compromised servers and usually are up only for a short period of time

### The design of ASwatch is based on monitoring global BGP routing activity to learn the control plane behavior of a network. Describe 2 phases of this system

1. **Training phase**: system learns control-plane behavior typical of both types of ASes. The system is given a list of known malicious and legitimate ASes. It then tracks the behavior of these ASes over time to track their business relationships with other ASes and their BGP updates/withdrawals patterns. ASwatch then computes statistical features of each AS. There are three main families of features:
   - _Rewiring activity_: based on changes in the AS connecting activity. Frequent changes in customers/providers, connecting with less popular providers, etc. is usually suspicious behavior
   - _IP space fragmentation and churn_: based on the advertised prefixes. Malicious ASes are likely to use small BGP prefixes to partition their IP address space and only advertise a small section of these (to avoid all of them being taken down at one if detected)
   - _BGP routing dynamics_: the BGP announcements and withdrawals for malicious ASes follow different patterns from legitimate ones – such as periodically announcing prefixes for short periods of time
2. **Operational phase** : given an unknown AS, it then calculates the features for this AS. It uses the model to then assign a reputation score to the AS. If the system assigns the AS a low reputation score for several days in a row (indicating consistent suspicious behavior), it identifies it as malicious

### What are 3 classes of features used to determine the likelihood of a security breach within an organization?

1. **Mismanagement symptoms**: if there are misconfigurations in an organization’s network, it indicates that there may not be policies in place to prevent such attacks or may not have the technological capability to detect these failures. This increases the likelihood of a breach. The features used are:
   - _Open recursive resolvers_: misconfigured open DNS resolvers
   - _DNS source port randomization_: many servers still do not implement this
   - _BGP misconfiguration_: short-lived routes can cause unnecessary updates to the global routing table
   - _Untrusted HTTPS certificates_: can detect the validity of a certificate by TLS handshake
   - _Open SMTP mail relays_: servers should filter messages so that only those in the same domain can send mails/messages
2. **Malicious activities**: another factor to consider is the level of malicious activities that are seen to originate from the organization’s network and infrastructure. We can determine this using spam traps, darknet monitors, DNS monitors, etc. We create a reputation blacklist of the IP addresses that are involved in some malicious activities. There are 3 such types of malicious activities:
   1. _Capturing spam activity_, e.g., CBL, SBL, SpamCop
   2. _Capturing phishing and malware activities_, e.g., PhishTank, SURBL
   3. _Capturing scanning activity_, e.g., Dshield, OpenBL
3. **Security incident reports**: data based on actual security incidents gives us the ground truth on which to train our machine learning model on. The system uses 3 collections of such reports to ensure a wider coverage area:
   1. _VERIS community database_: this is a public effort to collect cyber security incidents in a common format. It is maintained by the Verizon RISK team. It contains more than 5000 incident reports
   2. _Hackmageddon_: this is an independently maintained blog that aggregates security incidents on a monthly basis
   3. _The Web Hacking Incidents Database_: this is an actively maintained repository for cyber security incidents

### What is the classification by affected prefix (BGP hijacking)?

- **Classification by affected prefix**: In this class of hijacking attacks, we are primarily concerned with the IP prefixes that are advertised by BGP. There are different ways the prefix can be targeted, such as:
  - **Exact prefix hijacking**: when two different ASes (one is genuine and the other one is counterfeit) announce a path for the same prefix. This disrupts routing in such a way that traffic is routed towards the hijacker wherever the _AS-path route is shortest_, thereby disrupting traffic
  - **Sub-prefix hijacking**: This is an extension of exact prefix hijacking, except that in this case, the hijacking AS works with a sub-prefix of the genuine prefix of the real AS. This exploits the characteristic of BGP to _favor more specific prefixes_, and as a result route large/entire amount of traffic to the hijacking AS
  - **Squatting**: In this type of attack, the hijacking AS _announces a prefix that has not yet been announced_ by the owner AS

### What is the classification by AS-Path announcement (BGP hijacking)?

- **Classification by AS-Path announcement**: in this class of attacks, an illegitimate AS announces the AS-path for a prefix for which it doesn’t have ownership rights. There are different ways this can be achieved:
  - _Type-0 hijacking_: this is simply an AS announcing a prefix not owned by itself
  - _Type-N hijacking_: this is an attack where the counterfeit AS announces an illegitimate path for a prefix that it does not own to create a fake link (path) between different ASes
  - _Type-U hijacking_: in this attack the hijacking AS does not modify the AS-PATH but may change the prefix

### What is the classification by data plane traffic manipulation (BGP hijacking)?

- **Classification by data-plane traffic manipulation**: in this class of attacks, the intention of the attacker is to hijack the network traffic and manipulate the redirected network traffic on its way to the receiving AS. There are three ways the attack can be realized under this classification, i.e. traffic intercepted by the hijacker can be:
  - _Dropped_, so that it never reaches the intended destination. This attack falls under the category of _BH (blackholing) attack_
  - _Eavesdropped or manipulated_ before it reaches the receiving AS, which is also called as _MM (man-in-the-middle attack)_
  - _Impersonated_, e.g. in this case the network traffic of the victim AS is impersonated and the response to this network traffic is sent back to the sender. This attack is called _IM (imposture) attack_

### What are the causes or motivations behind BGP attacks?

- **Human error**: this is an _accidental routing misconfiguration_ due to manual errors. This can lead to large scale exact-prefix hijacking. E.g., China Telecom accidentally leaked a full BGP table that led to large-scale Type-0 hijacking
- **Targeted attack**: in this type of attack, the hijacking AS usually _intercepts network traffic (MM attack)_ while operating in stealth mode to remain under the radar on the control plane (Type-N and Type-U attacks). E.g., Visa and Mastercard’s traffic were hijacked by Russian networks using this method in 2017
- **High impact attack**: here, the attacker is obvious in their intent to cause widespread disruption of services. E.g., Pakistan Telecom in a Type-0 sub-prefix hijacking, essentially blackholing all of YouTube’s services worldwide for nearly 2 hours

### Explain the scenario of prefix hijacking

- The attacker uses a router at AS4 to send _false announcements_ and hijack the prefix 10.10.0.0/16 that belongs to AS1 (refer to class notes):
  1. The attacker uses a router to announce the prefix 10.10.0.0/16 that belongs to AS1, with a new origin AS4, pretending that the prefix belongs to AS4
  2. This new announcement causes a conflict of origin for the ASes that receive it **MOAS (Multiple Origin AS)**
  3. As a result of the new announcement, AS2, AS3 and AS5 receive the false advertisement and they compare it with the previous entries in their RIB
  4. AS2 will not select the route as the best route as it has the same path length with an existing entry
  5. AS3 and AS5 will believe the new advertisement, and they will update their entries (10.10.0.0/16 with path 4,2,1) to (10.10.0.0/16 with path 4). Therefore AS5 and AS3 will send all traffic for prefix 10.10.0.0/16 to AS4 instead of AS1

### Explain the scenario of hijacking a path

- The attacker _manipulates received updates_ before propagating them to neighbors (refer to class notes):
  1. AS1 advertises the prefix 10.10.0.0/16
  2. AS2 and AS3 receive and propagate legitimately the path for the prefix
  3. At AS4, the attacker _compromises the update_ for the path by changing it to 4,1 and propagates it to the neighbors AS3, AS2, and AS5. Therefore it claims that it has direct link to AS1 so that others believe the new false path
  4. AS5 receives the false path (4,1) “believes” the new false path and it adopts it. But the rest of the ASes don't adopt the new path because they either have an shorter path already or an equally long path to AS1 for the same prefix

### What are the key ideas behind ARTEMIS?

- **A configuration file**: where all the prefixes owned by the network are listed here for reference. This configuration file is populated by the network operator
- **A mechanism for receiving BGP updates**: this allows receiving updates from local routers and monitoring services. This is built into the system
- A point of consideration in BGP hijacking detection is the performance of False Positive (FP) and False Negative (FN) rates when we use different detection criteria. We ideally want a system with the least number of FPs and FNs that are inconsequential. The ARTEMIS system also allows the network operator to choose between:
  - _Accuracy and speed_
  - _FN which are inconsequential_ (less impact on control plane) for less FP

### What are the two automated techniques used by ARTEMIS to protect against BGP hijacking?

1. **Prefix deaggregation**: in a BGP attack scenario, the affected network can either contact other networks or it can simply _deaggregate the prefixes_ that were targeted by announcing _more specific prefixes_ of a certain prefix. Remember our prior discussion of YouTube’s services being attacked by Pakistan Telecom. The targeted prefix was 208.65.153.0/24. Within 90 minutes, YouTube started announcing 208.65.153.128/25 and 208.65.153.0/25, thereby counteracting the attack. Although the event required a long term solution, an immediate mitigation was required for services to come back online

2. **MOAS (Mitigation with Multiple Origin AS)**: the idea is to have _third party organizations and service providers_ do BGP announcements for a given network. It is akin to the current model that exists for legitimizing network traffic by third parties that _mitigate DDoS attacks_. When a BGP hijacking event occurs, the following steps occur:
   - The third party receives a notification and immediately announces from their locations the hijacked prefix(es)
   - In this way, network traffic from across the world is attracted to the third party organization, which then scrubs it and tunnels it to the legitimate AS

### What are two findings from ARTEMIS?

1. _Outsource the task of BGP announcement to third parties_: to combat against BGP hijacking attacks, having even just one single external organization to mitigate BGP attacks is highly effective against BGP attacks
2. _Comparison of outsourcing BGP announcements vs prefix filtering_: When compared against prefix filtering, which is the current standard defense mechanism, the research work found that filtering is less optimal when compared against BGP announcements

### Explain the structure of a DDoS attack

- The _master host_, controlled by the attacker, sends control messages to the three _compromised slaves_ directing them to send a _huge amount of traffic to the victim_. The packets sent from the slave contain the source address as a random IP address and the destination as the victim’s IP address. This master slave configuration _amplifies the intensity of the attack_ while also making it difficult to protect against it. The attack traffic sent by the slaves contain spoofed source addresses making it difficult for the victim to track the slaves. Also, since the traffic is sent from multiple sources, it’s harder for the victim to isolate and block the attack traffic

### What is spoofing, and how is related to DDoS attack?

- **IP spoofing** is the act of setting a _false IP address in the source field_ of a packet with the purpose of impersonating a legitimate server. In DDoS attacks, this can happen in two forms:
  1. The _source IP address is spoofed_, resulting in the response of the server sent to some other client instead of the attacker’s machine. This results in wastage of network resources and the client resources while also causing denial of service to legitimate users
  2. The attacker sets the _same IP address_ in both the source and destination IP fields. This results in the server sending the replies to itself, causing it to crash

### Describe a Reflection and Amplification attack

- In a **reflection attack**, the attackers use a set of reflectors to initiate an attack on the victim. A reflector is any server that _sends a response to a request_. For example, any web server or a DNS server would return a SYN ACK in response to a SYN packet as part of TCP handshake. Other examples include query responses sent by a server or `Host Unreachable` responses to a particular IP
- The master commands the slaves to send spoofed requests to the reflectors, which in turn sends traffic to the victim. This is in contrast with the conventional DDoS attack we saw in the previous section, where the slaves directly send traffic to the victim. Note that the victim can easily identify the reflectors from the response packets. However, _the reflector cannot identify the slave sending the spoofed requests_
- If the requests are chosen in such a way that the reflectors send large responses to the victim, it is a reflection and **amplification attack**. Not only would the victim receive traffic from millions of servers, the response sent would be large in size, making it further difficult for the victim to handle it

### What are the defenses against DDoS attacks?

- **Traffic scrubbing services**: a scrubbing service _diverts the incoming traffic to a specialized server_, where the traffic is “scrubbed” into either clean or unwanted traffic. The clean traffic is then sent to its original destination. Although this method offers fine-grained filtering of the packets, there are _monetary costs required_ for an in-time subscription, setup and other recurring costs. The other limitations include _reduced effectiveness_ due to per packet processing and challenges in handling Tbps level attacks. There’s also a possibility of decreased performance as the traffic may be rerouted and becoming susceptible to evasion attacks
- **ACL (Access Control List) filters**: _deployed by ISPs or IXPs_ at their AS border routers to filter out unwanted traffic. These filters, whose implementation depends on the vendor-specific hardware, are effective when the hardware is homogeneous and the deployment of the filters can be automated. The drawbacks of these filters include _limited scalability_ and since the filtering does not occur at the ingress points, it can exhaust the bandwidth to a neighboring AS
- **BGP Flowspec**: an extension to the BGP protocol which allows rules to be created on the _traffic flows_ and take corresponding actions. Helps to mitigate DDoS attacks by supporting the deployment and propagation of _fine-grained filters across AS domain borders_. It can be designed to match a specific flow or be based on packet attributes like _length and fragment_. It can also be based on the drop rate limit. In contrast to ACL filters, FlowSpec _leverages the BGP control plane making it easier to add rules to all the routers simultaneously_. However, drawbacks do exist:
  - Although flowspec has been effective in intra-domain environment, it is not so popular in inter-domain environments as it _depends on trust and cooperation among competitive networks_
  - Also, it might not scale for large attacks where the attack traffic originates from multiple sources as it would multiple rules or combining the sources into one prefix

### Explain provider-based blackholing

- A network that offers blackholing service is known as a **blackholing provider**. It is also responsible for providing the blackholing community that should be used. Network or customer providers act as blackholing providers at the network edge. Internet Service Providers (ISPs) or Internet Exchange Points (IXPs) act as blackholing providers at the Internet core. If the blackholing provider is a peer or an upstream provider, the _AS must announce its associated blackhole community along with the blackhole prefix_

### Explain IXP blackholing

- If the AS is a member of an IXP infrastructure and it is under attack, it _sends the blackholing messages to the IXP route server_ when a member connects to the route server. The route server then announces the message to all the connected IXP member ASes, which then drops the traffic towards the blackholed prefix. The null interface to which the traffic should be sent is specified by the IXP

### What is one of the major drawbacks of BGP blackholing?

- One of the major drawbacks of BGP blackholing is that the _destination under attack becomes unreachable_ since all the traffic including the legitimate traffic is dropped.
