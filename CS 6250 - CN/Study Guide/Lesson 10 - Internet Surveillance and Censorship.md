# Lesson 10: Internet Surveillance and Censorship

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### What is DNS censorship?

- DNS censorship is a _large scale network traffic filtering strategy_ opted by a network to enforce control and censorship over Internet infrastructure to suppress material which they deem as objectionable. An example of large scale DNS censorship that is implemented by networks located in China use a firewall, and it is popularly known as the **GFW (Great Firewall of China)**. This firewall looks like an opaque system that uses various techniques to censor China’s Internet traffic and block access to various foreign websites.

### What are the properties of GFW (Great Firewall of China)?

1. _Locality of GFW nodes_: there are two differing notions on whether the GFW nodes are present only at the edge ISPs or whether they are also present in non-bordering Chinese ASes. The majority view is that censorship nodes are present at the edge
2. _Centralized management_: since the blocklists obtained from two distinct GFW locations are the same, there is a high possibility of a central management (GFW Manager) entity that orchestrates blocklists
3. _Load balancing_: GFW load balances between processes based on source and destination IP address. The processes are clustered together to collectively send injected DNS responses

### How does DNS injection work?

- **DNS injection** is one of the most common censorship technique employed by the GFW. The GFW uses a _ruleset_ to determine when to inject DNS replies to censor network traffic. To start with, it is important to identify and isolate the networks that use DNS injection for censorship. The authors of the paper titled “Towards a Comprehensive Picture of the Great Firewall’s DNS Censorship” use probing techniques and vantage points to search for injected paths and then evaluate the injection

### What are the three steps involved in DNS injection?

- When tested against probes for restricted and benign domains, the accuracy of DNS open resolvers to accurately pollute the response is recorded over 99.9%. The steps involved in DNS injection are:
  1. _DNS probe_ is sent to the open _DNS resolvers_
  2. The probe is checked against the _blocklist_ of domains and keywords
  3. For domain level blocking, a _fake DNS A record_ response is sent back. There are two levels of blocking domains: the first one is by _directly_ blocking the domain, and the second one is by blocking it based on _keywords_ present in the domain

### List five DNS censorship techniques and briefly describe their working principles

1. **Packet dropping**: all network traffic going to a set of specific IP addresses is discarded. The censor identifies undesirable traffic and chooses to not properly forward any packets it sees associated with the traversing undesirable traffic instead of following a normal routing protocol
2. **DNS poisoning**: when a DNS receives a query for resolving hostname to IP address. If there is no answer returned, an incorrect answer is sent to redirect or mislead the user request
3. **Content inspection**: this censorship technique is more sophisticated, in that it allows for all network traffic to pass through a proxy where the traffic is examined for content, and the proxy rejects requests that serve objectionable content
4. **Blocking with resets**: GFW employs this technique where it sends a TCP reset (RST) to block individual connections that contain requests with objectionable content. We can see this by packet capturing of requests that are normal and requests that contain potentially flaggable keywords
5. **Immediate reset of connections**: censorship systems like GFW have blocking rules in addition to inspecting content, to suspend traffic coming from a source immediately, for a short period of time

### Which DNS censorship technique is susceptible to over-blocking?

- Packet dropping

### What are the strengths and weaknesses of “packet dropping” DNS censorship technique?

- Strengths:
  - Easy to implement
  - Low cost
- Weaknesses:
  - _Maintenance of blocklist_: it is challenging to stay up to date with the list of IP addresses to block
  - _Over-blocking_: if two websites share the same IP address and the intention is to only block one of them, there’s a risk of blocking both

### What are the strengths and weaknesses of “DNS poisoning” DNS censorship technique?

- Strengths:
  - _No over-blocking_: Since there is an extra layer of hostname translation, access to specific host names can be blocked versus blanket IP address blocking
- Weaknesses:
  - Blocks the _entire domain_. It is not possible to allow email contact while blocking the website

### What are the strengths and weaknesses of “content inspection” DNS censorship technique?

- Strengths:
  - _Precise censorship_: a very precise level of censorship can be achieved, down to the level of single web pages or even objects within the web page
  - _Flexible_: works well with hybrid security systems. E.g., with a combination of other censorship techniques like packet dropping and DNS poisoning
- Weaknesses:
  - _Not scalable_: they are expensive to implement on a large scale network as the processing overhead is large

### What are the strengths and weaknesses of “blocking with resets” DNS censorship technique?

- Strengths:
  - _Precise censorship_: precise blocking, since it searches for flagged keywords within content and blocks singular requests
- Weaknesses:
  - _Requires memory_: requires maintaining a blocklist for flagging, any processing overhead for searching for flagged keywords within packets
  - _Additional traffic_: generates additional traffic

### What are the strengths and weaknesses of “immediate reset of connections” DNS censorship technique?

- Strengths:
  - _Easier implementation_: easier to implement than just blocking with resets, blocks a net of requests versus searching individually
- Weaknesses:
  - _Over-blocking_: blocks all connections for a duration versus just blocking connections with flagged keywords

### Our understanding of censorship around the world is relatively limited. Why is it the case? What are the challenges?

1. **Diverse measurements**: such understanding would need a _diverse set of measurements_ spanning different geographic regions, ISPs, countries, and regions within a single country. Since political dynamics can vary so different ISPs can use various filtering techniques and different organizations may implement censorship at multiple layers of the Internet protocol stack and using different techniques. For example, an ISP may be blocking traffic based on IP address, but another ISP may be blocking individual web requests based on keywords. Therefore, we need widespread _longitudinal measurements_ to understand global Internet manipulation and the heterogeneity of DNS manipulation, across countries, resolvers, and domains

2. **Need for scale**: at first, the methods to measure Internet censorship were relying on _volunteers_ who were running measurement software on their own devices. Since this requires them to actually install software and do measurements, we can see that this method is unlikely to reach the scale required. There is a need for methods and tools that are independent of human intervention and participation

3. Identifying the intent to _restrict content access_: while identifying inconsistent or anomalous DNS responses can help to detect a variety of underlying causes such as misconfigurations. Identifying _DNS manipulation is different_ and it requires that we detect the _intent to block access to content_. It poses its own challenges. So we need to rely on identifying _multiple indications_ to infer DNS manipulation.

4. **Ethics and minimizing risks**: obviously, there are risks associated with involving citizens in censorship measurement studies, based on how different countries maybe penalizing access to censored material. Therefore, it is safer to stay away from using DNS resolvers or DNS forwarders in the home networks of individual users. Instead, it is _safer to rely on open DNS resolvers that are hosted in Internet infrastructure_, for example, within Internet service providers or cloud hosting providers.

### What are the limitations of main censorship detection systems?

- Global censorship measurement tools were created by efforts to _measure censorship_ by _running experiments from diverse vantage points_. For example, CensMon used PlanetLab nodes in different countries. However, many such methods are no longer in use. One the most common systems/approaches is the OpenNet Initiative where volunteers perform measurements on their home networks at different times since the past decade. _Relying on volunteer efforts to make continuous and diverse measurements_ is very difficult

### What kind of disruptions does Augur focus on identifying?

- **Augur** is a new system created to perform _longitudinal global measurements using TCP/IP side channels_ (more on Augur soon). However, this system focuses on identifying IP-based disruptions as opposed to DNS-based manipulations

### How does Iris counter the issue of lack of diversity while studying DNS manipulation? What are the steps associated with the proposed process?

- **Iris** uses open DNS resolvers located all over the globe. In order to _avoid using home routers_ (which are usually open due to configuration issues), this dataset is then restricted to a few thousand that are part of the Internet infrastructure. There are two main steps associated with this process:
  1. _Scanning_ the Internet’s IPv4 space for open DNS resolvers
  2. _Identifying_ infrastructure DNS resolvers

### What are the steps involved in the global measurement process using DNS resolvers?

1. _Performing global DNS queries_: Iris _queries thousands of domains_ across _thousands of open DNS resolvers_. To establish a baseline for comparison, the creators included 3 DNS domains which were under their control to help calculate metrics used for evaluation DNS manipulation
2. _Annotating DNS responses with auxiliary information_: to enable the classification, Iris _annotates the IP addresses_ with additional information such as their geo-location, AS, port 80 HTTP responses, etc. This information is available from the Censys dataset
3. _Additional PTR and TLS scanning_: one IP address could host several websites via virtual hosting. So, when Censys retrieves certificates from port 443, it could differ from one retrieved via TLS’s Server Name Indication (SNI) extension. This results in discrepancies that could cause Iris to label virtual hosting as DNS inconsistencies. To avoid this, Iris adds PTR and SNI certificates.

### What metrics does Iris use to identify DNS manipulation once data annotation is complete? Describe the metrics. Under what condition, do we declare the response as being manipulated?

- **Consistency metrics**: _domain access_ should have some consistency, in terms of network properties, infrastructure or content, even when accessed from different global vantage points. Using one of the domains Iris controls gives a set of high-confidence consistency baselines. Some consistency metrics used are _IP address, Autonomous System, HTTP Content, HTTPS Certificate, PTRs for CDN_
- **Independent verifiability metrics**: In addition to the consistency metrics, they also use metrics that could be _externally verified using external data sources_. Some of the independent verifiability metrics used are: HTTPS certificate (whether the IP address presents a valid, browser trusted certificate for the correct domain name when queried without SNI) and HTTPS Certificate with SNI

- Note: if **any** consistency metric or independent verifiability metric is satisfied, the response is correct. Otherwise, the response is classified as manipulated

### How to identify DNS manipulation via machine learning with Iris?

- See above or lecture notes

### How is it possible to achieve connectivity disruption using routing disruption approach?

- **Routing disruption**: a routing mechanism decides which part of the network can be _reachable_. Routers use BGP to communicate updates to other routers in the network. The routers share which destinations it can reach and continuously update its forwarding tables to select the best path for an incoming packet. If this communication is disrupted or disabled on critical routers, it could result in _unreachability_ of the large parts of a network. Using this approach can be _easily detectable_, as it involves withdrawing previously advertised prefixes or re-advertising them with different properties and therefore modifying the global routing state of the network, which is the _control plane_

### How is it possible to achieve connectivity disruption using packet filtering approach?

- **Packet filtering**: typically, packet filtering is used as a _security mechanism in firewalls and switches_. But to disrupt a network’s connectivity, packet filtering can be used to _block packets matching a certain criteria_ disrupting the normal forwarding action. This approach can be _harder to detect_ and might require active probing of the forwarding path or monitoring traffic of the impacted network

### Explain a scenario of connectivity disruption detection in case when no filtering occurs

- The sequence of events is as follows (refer to diagram in lecture notes):
  1. The measurement machine probes the IP ID of the reflector by sending a TCP SYN-ACK packet. It receives a RST response packet with IP ID set to `6` (`IPID (t1)`)
  2. Now, the measurement machine performs perturbation by sending a spoofed TCP SYN to the site
  3. The site sends a TCP SYN-ACK packet to the reflector and receives a RST packet as a response. The IP ID of the reflector is now incremented to `7`
  4. The measurement machine again probes the IP ID of the reflector and receives a response with the IP ID value set to `8` (`IPID (t4)`)
- The measurement machine thus observes that the difference in IP IDs between _steps 1 and 4_ is `2` and infers that _communication has occurred_ between the two hosts

### Explain a scenario of connectivity disruption detection in case of the inbound blocking

- The scenario where filtering occurs on the path _from the site to the reflector_ is termed as **inbound blocking**. In this case, the SYN-ACK packet sent from the site in step 3 does not reach the reflector. Hence, there is no response generated and the IP ID of the reflector does not increase. The returned IP ID in step 4 will be 7 (`IPID (t4)`) as shown in the figure (see lecture). Since the measurement machine observes the increment in IP ID value as `1`, it detects filtering on the path from the site to the reflector

### Explain a scenario of connectivity disruption detection in case of the outbound blocking

- **Outbound blocking** is the filtering imposed on the _outgoing path from the reflector_. Here, the reflector receives the SYN-ACK packet and generates a RST packet. As per our example, in step 3, the IP ID increments to `7`. However, the RST packet does not reach the site. When the site doesn’t receive a RST packet, it continues to resend the SYN-ACK packets at regular intervals depending on the site’s OS and its configuration. This is shown in step 5 of the figure. It results in further increment of the IP ID value of the reflector. In step 6, the probe by the measurement machine reveals the IP ID has again increased by `2`, which shows that retransmission of packets has occurred. In this way, outbound blocking can be detected
