# Lesson 2: Transport And Application Layers

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

[CUBIC: A New TCP-Friendly High-Speed TCP Variant](https://www.cs.princeton.edu/courses/archive/fall16/cos561/papers/Cubic08.pdf)

### Book References

- Kurose-Ross (6th Edition) Sections: 3.1.1, 3.2, 3.3, 3.4, 3.5.5, 3.6.
- Peterson Section 6.3

### Optional Readings

- [Congestion Avoidance and Control](https://ee.lbl.gov/papers/congavoid.pdf)

- [A Protocol for Packet Network Intercommunication](https://www.cs.princeton.edu/courses/archive/fall06/cos561/papers/cerf74.pdf)

- [End-to-End Internet Packet Dynamics](https://web.archive.org/web/20171116191315/http://signallake.com/innovation/CerfKahnMay74.pdf)

- [Data Center TCP (DCTCP)](https://people.csail.mit.edu/alizadeh/papers/dctcp-sigcomm10.pdf)

- [TIMELY: RTT-based Congestion Control for the Datacenter](https://conferences.sigcomm.org/sigcomm/2015/pdf/papers/p537.pdf)

- [Design, implementation and evaluation of congestion control for multipath TCP](https://www.usenix.org/legacy/events/nsdi11/tech/full_papers/Wischik.pdf)

- [Sizing Router Buffers](https://web.archive.org/web/20210120232627/http://yuba.stanford.edu/techreports/TR04-HPNG-060800.pdf)

## Section Quizzes

### Lesson 2: Transport And Applications Layers 1 Quiz

_As we have seen, UDP and TCP use port numbers to identify the sending application and destination application. Why don’t UDP and TCP just use process IDs rather than define port numbers_?

> Process IDs are specific to operating systems and therefore using process IDs rather than a specially defined port would make the protocol operating system dependent. Also, a single process can set up multiple channels of communications and so using the process ID as the destination identifier wouldn’t be able to properly demultiplex, Finally, having processes listen on well-known ports (like `80` for HTTP) is an important convention.

### Lesson 2: Transport And Applications Layers 2 Quiz

_UDP and TCP use 1’s complement for their checksums. But why is it that UDP takes the 1’s complement of the sum – why not just use the sum? Exploring this further, using 1’s complement, how does the receiver compute and detect errors? Using 1’s complement, is it possible that a 1-bit error will go undetected? What about a 2-bit error_?

> To detect errors, the receiver adds the four words (the three original words and the checksum). If the sum contains a zero, the receiver knows there has been an error. While all one-bit errors will be detected, but two-bit errors can be undetected (e.g., if the last digit of the first word is converted to a `0` and the last digit of the second word is converted to a `1`).

### Lesson 2: Transport And Applications Layers 3 Quiz

_TCP utilizes the Additive Increase Multiplicative Decrease (AIMD) policy for fairness. Consider other possible policies for fairness in congestion control would be Additive Increase Additive Decrease (AIAD), Multiplicative Increase Additive Decrease (MIAD), and Multiplicative Increase Multiplicative Decrease (MIMD)_.

> In AIAD and MIMD, the hosts communicating over the network will oscillate along the efficiency line, but will not converge as was shown for AIMD. MIAD will converge just like AIMD. But none of the alternative policies are as stable. The decrease policy in AIAD and MIAD is not as aggressive by comparison to AIMD and won’t address congestion control as effectively. The increase policy in MIAD and MIMD is too aggressive.

### Lesson 2: Transport And Applications Layers 4 Quiz

_Explain how in TCP Cubic the congestion window growth becomes independent of RTTs_.

> The key feature of CUBIC is that its window growth depends **only** on the time between two consecutive congestion events. One congestion event is the time when TCP undergoes fast recovery. This feature allows CUBIC flows competing in the same bottleneck to have approximately the same window size independent of their RTTs, achieving good RTT-fairness.
