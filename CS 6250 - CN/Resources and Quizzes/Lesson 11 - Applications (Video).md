# Lesson 11: Applications (Video)

**Note**: lecture notes this semester will be somewhat limited and largely quoted from the lecture since the majority of the class is slide-based presentations. This file will contain mainly optional readings, quizzes, and extra in-depth materials (if necessary).

## Readings And Additional Resources

### Additional Readings

- [VoIP: A comprehensive survey on a promising technology](https://www.sciencedirect.com/science/article/abs/pii/S1389128609001200)

- [MPEG: A Video Compression Standard for Multimedia Application](https://web.stanford.edu/class/ee398a/handouts/papers/Gall%20-%20MPEG.pdf)

- [The JPEG Compression standard](https://ieeexplore.ieee.org/document/125072)

- [JPEG File Interchange Format](https://www.w3.org/Graphics/JPEG/jfif3.pdf)

- [Watching Video over the Web: Part 1: Streaming Protocols](https://ieeexplore.ieee.org/document/5677508)

- [A Quest for an Internet Video Quality-of-Experience Metric](https://www.cs.cmu.edu/~xia/resources/Documents/Balachandran-hotnets2012.pdf)

- [Confused, Timid, and Unstable: Picking a Video Streaming Rate is Hard](http://yuba.stanford.edu/~nickm/papers/Confused_Timid_and_Unstable_Picking_a_Video_Streaming_Rate_is_Hard.pdf)

### Book References

Kurose-Ross (7th Edition) Chapter 9.

## Section Quizzes

### Lesson 11: Applications (Video) 1 Quiz

1. _When streaming stored audio and video, the content starts playing within a few seconds of receiving data, instead of waiting for the entire file to download first_.
   - True
2. _Streaming audio and video is interactive and should have a continuous playout_.
   - True
3. _Streaming live audio and video is usually not interactive and is delay-sensitive_.
   - True
4. _Conversational voice and video over IP is a service that uses traditional circuit-switched telephony networks_.
   - False

### Lesson 11: Applications (Video) 2 Quiz

1. _The rounding of samples to a discrete number in a particular range is called quantization_.
   - True
2. _The only consideration when encoding VoIP is to use as little bandwidth as possible_.
   - False
3. _When using VoIP, all packets are transmitted, regardless of any end-to-end delay, to make sure that no message is unaccounted for_.
   - False
4. _Which service maintains a jitter buffer as a mechanism for mitigating jitter_?
   - VoIP

### Lesson 11: Applications (Video) 3 Quiz

1. _Most of the time, VoIP uses <...> to transmit audio_.
   - UDP
2. _Which of the following applications has less delay tolerance (i.e. a lower threshold in terms of when a packet is considered lost)_?
   - VoIP
3. _Which of the following services is the least sensitive to network delays? (i.e. more tolerant to network delays)_.
   - File transfer
4. _Which of the following services is the most tolerant to packet losses_?
   - VoIP
5. _Which of the following decreases the end-to-end delay when using VoIP_?
   - UDP
6. _Which of the following is more likely to result in packet losses when using VoIP_?
   - UDP
7. _When using Forward Error Concealment, the redundant data that is transmitted alongside the main transmission could be a copy of the original data divided into chunks or could also be a lower-quality version_.
   - True
8. _An advantage of using Interleaving is that there is no added latency_.
   - False
9. _Error concealment can be computationally cheap if a lost packet is simply replaced with a previous packet_.
   - True

### Lesson 11: Applications (Video) 4 Quiz

1. _Video delivery is tolerant to packet losses. Reliability of packet delivery is not that important_.
   - False
2. _Content providers store all the intelligence to download the video at the server_.
   - False
3. _What is the first item downloaded by a client’s video player_?
   - A manifest file
4. _Suppose that Alice is using a cloud service to listen to many MP3 songs, one after the other, each encoded at a rate of 128 kbps. Suppose that she downloads for 30 minutes (1800 seconds). How many MB of data are transferred during the 30-minute session? Round your answer to the nearest MB. (For simplification, assume 1 MB = 8,000 Kb)_.
   - `Size = (128 kbps * 1800 s) * (1 MB / 8000 kb) ~ 29 MB`
5. _Suppose that Bob is using a cloud service to watch video encoded at a rate of 2 Mbps. Suppose that his session lasts for 30 minutes (1800 seconds). How many MB of data are transferred during the 30-minute session? Round your answer to the nearest MB. (For simplification, assume 1 MB = 8,000 Kb)_.
   - `Size = (2000 kbps * 1800 s) * (1 MB / 8000 kb) = 450 MB`

### Lesson 11: Applications (Video) 5 Quiz

1. _One of the goals of quality of experience is to have high re-buffering_.
   - False
2. _Assume the available network bandwidth is 15 Mbps and the bitrate of the chunk is 3 Mbps. Determine the buffer-filling rate and the buffer-depletion rate_.
   - Buffer-filling rate: 5
   - Buffer-depletion rate: 1
3. _Consider a case where a video player experiences a bandwidth drop in a case of bandwidth overestimation with rate-based adaptation (see provided initial conditions). At time t = 25 seconds, the bandwidth drops to 300 kbps. The buffer occupancy at the time of the bandwidth drop was 15s. Calculate how long it takes to download this chunk_.
   - `Duration = 3 Mbps * 1000 * (5 s) / 300 kbps = 50 s`
