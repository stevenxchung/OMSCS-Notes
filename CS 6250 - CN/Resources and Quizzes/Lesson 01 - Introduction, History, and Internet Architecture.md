# Lesson 1: Introduction, History, And Internet Architecture

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

- [How to Read a Paper](https://people.cs.umass.edu/~phillipa/CSE390/paper-reading.pdf)

- [How to read a research paper](https://www.cs.tufts.edu/comp/150PLD/ReadingPapers.pdf)

- [The Design Philosophy of the Darpa Internet Protocols](http://ccr.sigcomm.org/archive/1995/jan95/ccr-9501-clark.pdf)

- [The Evolution of Layered Protocol Stacks Leads to an Hourglass-Shaped Architecture](https://www.cc.gatech.edu/~dovrolis/Papers/evoarch.pdf)

### Book References

1. Kurose 1.5.1 (Edition 6): Layered Architecture
2. Kurose 1.5.2 (Edition 6): Encapsulation
3. Computer Networks: A Systems Approach - Edition 4, Section3 and 3.1 (Interconnecting hosts and networks)
4. Computer Networks: A Systems Approach - Edition 4, Section 3.2.1 (Learning Bridges)
5. Computer Networks: A Systems Approach - Edition 4, Section 3.2.2 (The looping problem and the spanning tree algorithm)

### Optional Readings

- [Brief History of the Internet (1997)](https://www.internetsociety.org/wp-content/uploads/2017/09/ISOC-History-of-the-Internet_1997.pdf)

- [Rethinking the design of the Internet](https://dspace.mit.edu/bitstream/handle/1721.1/1519/TPRC_Clark_Blumenthal.pdf?sequence=1&origin=publication_detail)

- [Active Networking and End-To-End Arguments](http://web.mit.edu/Saltzer/www/publications/endtoend/ANe2ecomment.html)

- [End-To-End Arguments In System Design](http://web.mit.edu/Saltzer/www/publications/endtoend/endtoend.pdf)

- [Internet Clean-Slate Design: What and Why?](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.98.8874&rep=rep1&type=pdf)

- [A Clean Slate 4D Approach to Network Control and Management](https://www.cs.princeton.edu/~jrex/papers/ccr05-4d.pdf)

- [Holding the Internet Accountable](https://conferences.sigcomm.org/hotnets/2007/papers/hotnets6-final71.pdf)

- [An Algorithm for Distributed Computation of a Spanning Tree in an Extended LAN](https://www.it.uu.se/edu/course/homepage/datakom/ht06/slides/sta-perlman.pdf)

## Section Quizzes

### Lesson 1: Introduction, History, And Internet Architecture 1 Quiz

_Some data link layer protocols, such 802.11 (WiFi), implement some basic error correction as the physical medium used is easily prone to interference and noise (such as a nearby running microwave). Is this a violation of the end-to-end principle_?

No, because violations of the e2e principle typically refer to scenarios where it is not possible to implement a functionality entirely at the end hosts, such as NAT and firewalls. In this question, we have a lower level protocol implementing error checking.

### Lesson 1: Introduction, History, And Internet Architecture 2 Quiz

_Which of the following are ramifications of the “hourglass shape of the internet”_?

- Many technologies that were not originally designed for the internet have been modified so that they have versions that can communicate over the internet (such as Radio over IP)
- It has been a difficult and slow process to transition to IPv6, despite the shortage of public IPv4 addresses

### Lesson 1: Introduction, History, And Internet Architecture 3 Quiz

_Which of the following statements are correct_?

The Spanning Tree Algorithm helps to prevent broadcast storms. Although it is still possible to have broadcast storms on the network (such as from a bad network card), STP prevents broadcast storms that result from having loops present in the network topology.
