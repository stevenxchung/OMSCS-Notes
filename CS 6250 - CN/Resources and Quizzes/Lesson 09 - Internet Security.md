# Lesson 9: Internet Security

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

- [Measuring and Detecting Fast-Flux Service Networks](https://user.informatik.uni-goettingen.de/~krieck/docs/2008-ndss.pdf)

- [FIRE: FInding Rogue nEtworks](https://sites.cs.ucsb.edu/~chris/research/doc/acsac09_fire.pdf)

- [ASwatch: An AS Reputation System to ExposeBulletproof Hosting ASes](https://conferences.sigcomm.org/sigcomm/2015/pdf/papers/p625.pdf)

- [Cloudy with a Chance of Breach: Forecasting Cyber Security Incident](https://www.usenix.org/system/files/conference/usenixsecurity15/sec15-paper-liu.pdf)

- [ARTEMIS: Neutralizing BGP HijackingWithin a Minute](https://www.inspire.edu.gr/wp-content/pdfs/artemis_TON2018.pdf)

- [BGP Anomaly Detection Techniques: A Survey](https://www.researchgate.net/profile/Bahaa_Musawi/publication/309519246_BGP_Anomaly_Detection_Techniques_A_Survey/links/5a63db73aca272a1581bf3ea/BGP-Anomaly-Detection-Techniques-A-Survey.pdf)

- [A Forensic Case Study on AS Hijacking:The Attacker’s Perspective](http://www.sigcomm.org/sites/default/files/ccr/papers/2013/April/2479957-2479959.pdf)

- [An Analysis of Using Reflectors for Distributed Denial-of-Service Attacks](https://www.icir.org/vern/papers/reflectors.CCR.01.pdf)

- [Stellar: Network Attack Mitigation using Advanced Blackholing](https://www.de-cix.net/Files/2731074c857497be3827ac9537b6e486f27aa57c/Research-paper-Stellar-Network-Attack-Mitigation-using-Advanced-Blackholing.pdf)

- [Inferring BGP Blackholing Activity in the Internet](https://www.de-cix.net/Files/3dc6302479dc77225a799f83532945dbcb6ea236/Inferring-BGP-Blackholing-Activity.pdf)

- [Next Gen Blackholing to Counter DDoS](https://ripe78.ripe.net/presentations/9-RIPE_Presentation_MW.pdf)

### Book References

Kurose-Ross (6th Edition) Section 8.1.

## Section Quizzes

### Lesson 9: Internet Security 1 Quiz

1. _Which property of secure communication ensures that people are who they say they are when communicating over the internet_?
   - Authentication
2. _Which property of secure communication ensures that a message is not modified before it reaches the receiver_?
   - Integrity
3. _Which property of secure communication is protected by encrypting the messages exchanged_?
   - Confidentiality

### Lesson 9: Internet Security 2 Quiz

1. _Attackers tend to keep the uptime of domains used for malicious purposes as short as possible in order to avoid being detected_.
   - False
2. _Round Robin DNS is a mechanism used by large websites to distribute the load of incoming requests to several servers at a single physical location_.
   - True
3. _DNS-based content delivery aims to distribute the load amongst multiple servers at a single location, but also distribute these servers across the world_.
   - True
4. _DNS-based content delivery determines the nearest server, which results in increased responsiveness and availability_.
   - True

### Lesson 9: Internet Security 3 Quiz

1. _Legitimate networks may let malicious content be up for weeks to more than a year_.
   - False
2. _How does FIRE identify the most malicious networks_?
   - Analyzing the information given by data sources and searching for ASes with a large percentage of malicious IP addresses
3. _ASwatch uses information exclusively from the data plane to infer network reputation_.
   - False
4. _ASwatch relies on the premise that “bulletproof” ASes have <...> interconnection patterns and overall different <...> plane behavior from most legitimate networks_.
   - Distinct
   - Control

### Lesson 9: Internet Security 4 Quiz

1. _In order to stop a prefix or AS-Path announcement attack, we need access to the <...>, such as IP prefixes and AS-paths_.
   - Control plane data
2. _In attacks where network traffic is dropped, manipulated or impersonated, the data accessed is located at the <...>_.
   - Data Plane
3. _Which attack disrupts the BGP characteristic to favor more specific prefixes_?
   - Sub-prefix hijacking
4. _ARTEMIS uses a configuration file and a mechanism for receiving BGP updates from routers and monitoring services to detect BGP hijacking attacks_.
   - True
5. _Prefix deaggregation and mitigation with Multiple Origin AS (MOAS) are independent from ARTEMIS_.
   - False

### Lesson 9: Internet Security 5 Quiz

1. _A Distributed Denial of Service Attack consists on the attacker sending a large volume of traffic to the victim through servers (slaves), so that the victim host becoming unreachable or in exhaustion of its bandwidth_
   - True
2. _IP spoofing is the act of setting a false IP address in the source field of a packet with the purpose of impersonating a legitimate server_.
   - True
3. _In a reflection attack, the attackers use a set of reflectors to initiate an attack on the victim_
   - True
4. _During a Reflection and Amplification attack, the slaves set the source address of the packets to the <...> IP address_.
   - Victim's
5. _What is the difference between a conventional DDoS and a Reflection and Amplification attack_?
   - In a DDos attack, the slaves send traffic directly to the victim as opposed to a reflector sending the traffic to the victim

### Lesson 9: Internet Security 6 Quiz

1. _Which mitigation technique uses fine-grained filters across AS domain borders, and attributes such as length and fragment can be used to match traffic_?
   - BGP Flowspec
2. _Which defense mechanism consists on a service that diverts the incoming traffic to a specialized server, where traffic is divided in either clean or unwanted traffic, and clean traffic is then sent to its original destination_?
   - Traffic Scrubbing Services
3. _BGP Blackholing stops the traffic closer to the destination of the attack_.
   - False
4. _BGP Blackholing is used to mitigate DDoS attacks_.
   - True
