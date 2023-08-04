# Lesson 10: Internet Surveillance And Censorship

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

- [Towards a Comprehensive Picture of the Great Firewall’s DNS Censorship](https://www.usenix.org/system/files/conference/foci14/foci14-anonymous.pdf)

- [Ignoring the Great Firewall of China](https://www.cl.cam.ac.uk/~rnc1/ignoring.pdf)

- [Global Measurement of DNS Manipulation](https://bees.ece.gatech.edu/papers/dns_usenix_2017.pdf)

- [Analysis of Country-wide Internet Outages Caused by Censorship](https://www.caida.org/publications/papers/2011/outages_censorship/outages_censorship.pdf)

- [Augur: Internet-Wide Detection of Connectivity Disruptions](https://frankli.ece.gatech.edu/papers/augur_oakland_2017.pdf)

- [Adapting Social Spam Infrastructure for Political Censorship](http://www.icir.org/vern/papers/kremlin-bots.leet11.pdf)

- [Five incidents, one theme: Twitter spam as a weapon to drown voices of protests](https://www.usenix.org/system/files/conference/foci13/foci13-verkamp.pdf)

## Section Quizzes

### Lesson 10: Internet Surveillance And Censorship 1 Quiz

1. _The Great Firewall of China injects fake DNS A records to block individual connections_.
   - False, injection of DNS A records serve to block access by domain name. Using TCP RSTs will allow blocking of individual connections
2. _The Great Firewall of China is likely managed by a single entity_.
   - True
3. _The Great Firewall of China may block content based on which of the following characteristics_?
   - All of the above, GFW operates in an on-path fashion, passively examining passing traffic. It may use any combinations of characteristics for filtering
4. _Packet dropping is a scheme used to censor content. Which of the following statements characterize packet dropping? Select all that apply_.
   - Low cost to implement
   - Might block content otherwise deemed appropriate
5. _The GFW can block a portion of a website using DNS poisoning_.
   - False
6. _Suppose a client in Cambridge makes a request to a website based in China. When does the GFW reset the connection_?
   - After the ACK sent by the client in Cambridge

### Lesson 10: Internet Surveillance And Censorship 2 Quiz

1. _Consider the variance of censorship methods used. Select the statement which correctly describes the situation_.
   - Censorship methods are inconsistent across ISPs making it difficult to measure DNS manipulation
2. _Current research methods for understanding DNS methods are scalable due to the number of volunteers participating_.
   - False
3. _The use of Open DNS resolvers resolves some of the ethical concerns associated with Internet censorship studies_.
   - True

### Lesson 10: Internet Surveillance And Censorship 3 Quiz

1. _Iris uses <...> obtain a dataset for machine learning_.
   - Open DNS Resolvers
2. _Suppose Iris is being used to detect DNS manipulation. Iris queries a global resolver for an IP addresses (consistency metric) and receives a DNS A record with a different IP address than the ones stored. Which of the follow statements are true_?
   - The response is inconsistent, but might not be classified as manipulated. The response is inconsistent, but will still be classified as _correct_ if the IP address satisfies an independent verifiability metric (e.g., the IP address presents a valid, browser-trusted certificate for the correct domain name)

### Lesson 10: Internet Surveillance And Censorship 4 Quiz

1. _Augur is used to identify DNS-based manipulations_.
   - False, Augur is a method and accompanying system that utilizes _TCP/IP side channels to measure reachability_(if there is any filtering) between two Internet locations without directly controlling a measurement vantage point at either location
2. _Suppose we are using Augur to detect filtering between two host, and that we have a scenario where no blocking occurs. The measurement machine sends a SYN-ACK to the reflector. What should happen_?
   - The return IP ID from the reflector to the measurement machine should increase by `2`
