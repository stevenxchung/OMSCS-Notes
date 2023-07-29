# Lesson 5: Router Design And Algorithms (Part 1)

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

- Varghese, Network Algorithmics, Sections: 1.1.2, 2.3.2, Chapter 11.
- [Survey and Taxonomy of IP Address Lookup Algorithms](https://pdfs.semanticscholar.org/71d9/018e900f99ff60653b3769160131e775873f.pdf)

### Book References

Kurose-Ross (6th Edition) Sections: 4.3.

## Section Quizzes

### Lesson 5: Router Design And Algorithms (Part 1) 1 Quiz

1. _The data plane functions of a traditional router are implemented in <...>_.
   - Hardware
2. _The control plane functions of a traditional router are implemented in <...>_.
   - Software
3. _Which plane operates on a shorter timescale_?
   - Data
4. _Classify each function as an operation of either the data plane or control plane_.
   - Computing paths based on a protocol $\rightarrow$ Control Plane
   - Forwarding packets at Layer 3 $\rightarrow$ Data Plane
   - Switching packets at Layer 2 $\rightarrow$ Data Plane
   - Running protocols to build a routing table $\rightarrow$ Control Plane
   - Running the Spanning Tree Protocol $\rightarrow$ Control Plane
   - Decrementing Time To Live (TTL) $\rightarrow$ Data Plane
   - Computing an IP header checksum $\rightarrow$ Data Plane
   - Running a protocol/logic to configure a middle box device for load balancing $\rightarrow$ Control Plane
   - Forwarding packets according to installed rules in a middlebox device $\rightarrow$ Data Plane
5. _Which, if any, of the following types of switching can send multiple packets across the fabric in parallel_?
   - Interconnection network/crossbar

### Lesson 5: Router Design And Algorithms (Part 1) 2 Quiz

1. _Given that the router uses longest prefix matching. Determine the output link for packet with given destination IP address. Type the letter of the output link_.
   - B
   - B
   - A
   - C
2. _Determine the mask for the address `192.168.0.1/24`_.
   - `255.255.255.0`

### Lesson 5: Router Design And Algorithms (Part 1) 3 Quiz

_For each prefix look up, determine the node we return_.

- `a`
- `b`
- `c`
- `a`
- `e`
- `h`

### Router Design And Algorithms (Part 1) 4 Quiz

_Consider expanding each prefix with stride length 3, so that we construct a fixed length multi-bit trie. Which of the following prefixes are associated with P3? Select all that apply_.

- `110*`
- `100*`
- `111*`

### Router Design And Algorithms (Part 1) 5 Quiz

1. _Construct the following variable-stride multibit trie. Based on the above database, fill in the nodes (eg n1, n2, n3, etc.) with the corresponding nodes from the database (a, b, c, etc.)_.
   - n1 $\rightarrow$ `none`
   - n2 $\rightarrow$ `a`
   - n3 $\rightarrow$ `a`
   - n4 $\rightarrow$ `d`
   - n5 $\rightarrow$ `d`
   - n6 $\rightarrow$ `none`
   - n7 $\rightarrow$ `none`
   - n8 $\rightarrow$ `c`
   - n9 $\rightarrow$ `c`
   - n10 $\rightarrow$ `e`
   - n11 $\rightarrow$ `none`
   - n12 $\rightarrow$ `f`
   - n13 $\rightarrow$ `g`
   - n14 $\rightarrow$ `h`
   - n15 $\rightarrow$ `i`
   - n16 $\rightarrow$ `b`
   - n17 $\rightarrow$ `none`
2. _A multi-bit trie is <...> than a uni-bit trie representing the same prefix database and requires <...> memory accesses to perform a lookup_.
   - Shorter
   - Fewer
3. _Multi-bit tries can support an arbitrary number of prefix lengths_.
   - False, to use a given multi-bit trie, _the prefix set_ must be transformed into an _equivalent set_ with the prefix lengths allowed by the new structure
