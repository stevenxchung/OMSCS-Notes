# Lesson 11: Applications (Video)

> The following questions and prompts are intended to check your understanding of the content. The exam may cover **ANY** content from the modules. The only exception being those pages marked “optional”.

## Study Questions

### Compare the bit rate for video, photos, and audio

- The first defining property for video is high bit rate, generally somewhere between _100 kbps to over 3 Mbps_, depending on the quality of the video
- Photo bit rates are typically around _320 kbps_
- Audio bit rates are the lowest, typically around _128 kbps_

### What are the characteristics of streaming stored video?

- First, streaming stored video is... **streamed**! That means that the video starts playing _within a few seconds_ of receiving data, instead of waiting for the entire file to download first
- It’s also _interactive_, which means that the user can pause, fast forward, skip ahead or move back in the video, and then see the response within a few seconds
- Streaming stored video should also have _continuous playout_, which means that it should play out the same way it was recorded without freezing up in the middle
- Generally, streaming stored video files are stored on a _CDN_ rather than just one data center. This type of multimedia application can also be implemented with the _peer-to-peer model_ instead of the client-server model

### What are the characteristics of streaming live audio and video?

- Streaming live audio and video is very similar to streaming stored video or audio, and use similar techniques, with some important differences. Since these applications are live and broadcast-like, there are generally many _simultaneous users_, sometimes in very _different geographic locations_
- They are also _delay-sensitive_, but not as much as conversational voice and video applications are - generally, a _ten second delay_ is ok

### What are the characteristics of conversational voice and video over IP?

- **VoIP** stands for “Voice over IP”, which is like phone service that goes over the Internet instead of through traditional circuit-switched telephony network. These kinds of calls or video conferences often involve _three or more participants_
- Since these calls and conferences are real-time and involve human users interacting, these applications are _highly delay-sensitive_. A short delay of less than 150 milliseconds isn’t really noticeable, but a longer delay, such as over 400 milliseconds, can be frustrating as people end up accidentally talking over each other
- On the other hand, these applications are _loss-tolerant_. There are techniques that can conceal occasional glitches, and even if a word in the conversation gets garbled, human listeners are generally able to ask the other side to just repeat themselves

### How does the encoding of analog audio work (in simple terms)?

- Analog audio by nature is represented as a _continuous wave_, but digital data by nature is _discrete_. Therefore, all digital representations of analog audio are only _approximations_
- Generally speaking, audio is encoded by taking many (as in, thousands) of _samples per second_, and then _rounding_ each sample’s value to a _discrete_ number within a particular range (this “rounding” to a discrete number is called **quantization**)

### What are the three major categories of VoIP encoding schemes?

- The three major categories of **encoding schemes** are _narrowband_, _broadband_, and _multimode_ (which can operate on either), and they come with different characteristics and tradeoffs
- For VoIP, the important thing is that we want to still be able to understand the speech and the words that are being said, while at the same time still using as little bandwidth as possible

### What are the functions that signaling protocols are responsible for?

- In traditional telephony, a **signaling protocol** takes care of how calls are set up and torn down. Signaling protocols are responsible for four major functions:
  1. **User location**: the caller locating where the callee is
  2. **Session establishment**: handling the callee accepting, rejecting, or redirecting a call
  3. **Session negotiation**: the endpoints synchronizing with each other on a set of properties for the session
  4. **Call participation management**: handling endpoints joining or leaving an existing session.
- VoIP also uses signaling protocols, just like telephony, to perform the same functions. The **SIP (Session Initiation Protocol)** is just one example of a signaling protocol used in many VoIP applications

### What are three QoS VoIP metrics?

- **QoS (Quality of Service) metrics**: how we measure the quality of service. There are three major QoS metrics for VoIP:
  1. End-to-end delay
  2. Jitter
  3. Packet loss

### What kind of delays are including in "end-to-end delay"?

- The first QoS metric is **end-to-end delay**, which is basically the total delay _from mouth to ear_. This includes delay from:
  - The time it takes to _encode_ the audio (which we discussed earlier)
  - The time it takes to put it in _packets_
  - All the normal sources of network delay that network traffic encounters such as _queueing delays_
  - _Playback delay_, which comes from the _receiver’s_ playback buffer (which is a mitigation technique for delay jitter, which we’ll be discussing next)
  - _Decoding delay_, which is the time it takes to reconstruct the signal
- End-to-end delay is the accumulation of all of these sources of delay, and VoIP applications are sensitive to these delays
- Since delays are so impactful for VoIP, VoIP applications frequently have _delay thresholds_, such as at 400 ms, and discard any received packets with a delay greater than that threshold. That means that packets that are delayed by more than the threshold are effectively lost.

### How does "delay jitter" occur?

- Between all the different buffer sizes and queueing delays and network congestion levels that a packet might experience, _different voice packets_ can end up with _different amounts of delay_. One voice packet may be delayed by 100 ms, and another by 300 ms. We call this phenomenon jitter, packet jitter, or **delay jitter**
- It turns out that jitter is problematic for VoIP, because it interferes with reconstructing the analog voice stream. With large jitter, we end up with more _delayed packets_ that end up getting discarded, and that can lead to a gap in the audio. Too many dropped sequential packets can make the audio unintelligible

### What are the mitigation techniques for delay jitter?

- The main VoIP application mechanism for mitigating jitter is maintaining a buffer, called the **jitter buffer** or the play-out buffer. This mechanism helps to _smooth out and hide the variation in delay_ between different received packets, by buffering them and playing them out for decoding at a _steady rate_
- There’s a tradeoff here, though. A _longer jitter buffer_ reduces the number of packets that are discarded because they were received too late, but that _adds to the end-to-end delay_. A _shorter jitter buffer_ will not add to the end-to-end delay as much, but that can lead to _more dropped packets_, which reduces the speech quality

### Compare the three major methods for dealing with packet loss in VoIP protocols

- See below

### How does FEC (Forward Error Correction) deal with the packet loss in VoIP? What are the tradeoffs of FEC?

- **FEC (Forward Error Concealment)** comes in a few different flavors, but in general, FEC works by _transmitting redundant data_ alongside the main transmission, which allows the receiver to replace lost data with the redundant data. This redundant data could be a copy of the original data, by _breaking the audio into chunks_ and cleverly using exclusive OR (XOR) with $n$ previous chunks
- This redundant data could also be a lower-quality audio stream transmitted alongside the original stream - similar to how a spare tire in a car may be of lower quality than the normal tires, but enough to get by in the case of a flat tire. Regardless of which method is used, there’s a _tradeoff_:
  - The _more redundant data_ transmitted, the _more bandwidth_ is consumed. Also, some of these FEC techniques require the receiving end to receive more chunks before playing out the audio, and that _increases playout delay_

### How does interleaving deal with the packet loss in VoIP/streaming stored audio? What are the tradeoffs of interleaving?

- **Interleaving** _does not transmit ANY redundant data_, and so it _does not add extra bandwidth requirements_ or bandwidth overhead. Interleaving works by _mixing chunks of audio together_ so that if one set of chunks is lost, the lost chunks aren’t consecutive
- The idea is that many smaller audio gaps are preferable to one large audio gap. (We note that the human ear is pretty intolerant of audio gaps, and ideally audio gaps should be under 30 ms)
- The _tradeoff_ for interleaving is that the receiving side has to _wait longer_ to receive consecutive chunks of audio, and that _increases latency_. Unfortunately, that means this technique is limited in usefulness for VoIP, although it can have good performance for streaming stored audio

### How does error concealment technique deal with the packet loss in VoIP?

- **Error concealment**, is basically “guessing” what the _lost audio packet_ might be. This is possible because generally, with really small audio snippets (between 4 ms and 40 ms), there’s some _similarity_ between one audio snippet and the next audio snippet. This is the same principle that makes audio compression possible
- One really simple version of error concealment is to simply _repeat a packet_ - _replace the lost packet_ with a _copy of the previous packet_ - and hope that will be good enough. This solution is _computationally cheap_, and works pretty well in a lot of cases
- Another version of error concealment is to use the audio before and after the lost packet and _interpolate_ (that is, make a calculation to guess) an _appropriate packet to conceal the lost packet_. This is a better solution than packet repetition, but it is more _computationally expensive_

### What developments lead to the popularity of consuming media content over the Internet?

- Various enabling technologies and trends have led to this development of consuming _media content_ over the Internet:
  1. The _bandwidth_ for both the core network and last-mile access links have _increased_ tremendously over the years
  2. The _video compression technologies_ have become more _efficient_. This enables to stream high-quality video without using a lot of bandwidth
  3. Finally, the development of _Digital Rights Management_ culture has encouraged content providers to put their content on the Internet

### Provide a high-level overview of adaptive video streaming

1. The video content is first _created_ - say in a professional studio like this lesson or using a smartphone by a user. The raw recorded content is typically at a high quality
2. It is then _compressed_ using an _encoding algorithm_
3. This encoded content is then _secured using DRM_ and hosted over a server
4. Typically content providers have their own data centers such as Google or use third-party CDNs to _replicate_ the content over _multiple geographically distributed servers_. This makes sure that the content can be delivered in a _scalable_ manner
5. The end-users _download_ the video content over the Internet
6. The downloaded video is _decoded_ and _rendered_ on the user’s screen

### (Optional) What are two ways to achieve efficient video compression?

1. Within an image - pixels that are nearby in a picture tend to be similar - known as **spatial redundancy**
2. Across images - in a continuous scene, consecutive pictures are similar - known as **temporal redundancy**

### (Optional) What are the four steps of JPEG compression?

- See lecture

### (Optional) Explain video compression and temporal redundancy using I-, B-, and P-frames

- See lecture

### (Optional) Why is video compression unable to use P-frames all the time?

1. When a scene changes, the frame becomes _drastically different_ from the last frame and even if we are using the difference, it is almost like encoding a fresh image. This can lead to _loss in image quality_
2. In addition, it also _increases the decoding time_ in case a user skips ahead in the video as it will need to download all frames in between the last I-frame and the current frame to decode the video

### (Optional) What is the difference between constant bitrate encoding and variable bitrate encoding (CBR vs VBR)?

- **CBR (constant bitrate encoding)**: the output size of the video is fixed over time
- **VBR (variable bitrate encoding)**: the output size remains the same on an average, but varies here and there based on the underlying scene complexity

### Which protocol is preferred for video content delivery - UDP or TCP? Why?

- Let us think about what will be a good transport protocol to deliver. Note that the video needs to be _decoded at the client_. This decoding might fail if some data is lost. For instance, if an I-frame is lost partially, we may not be able to obtain the RGB matrices correctly. Similarly, if an I-frame was lost, P-frame can not be decoded. Therefore, we need a transport protocol that ensures that the _data is delivered reliably_ over the Internet which is a best-effort network
- Thus, between UDP and TCP, content providers ended up choosing _TCP_ for video delivery as it provides _reliability_. An additional benefit of using TCP was that it already provides _congestion control_ which is required for effectively sharing bandwidth over the Internet

### What was the original vision of the application-level protocol for video content delivery and why was HTTP chosen eventually?

- The original vision was to have _specialized video servers_ that remembered the state of the clients. These servers would control the sending rate to the client. In the case, client paused the video, it would send a signal to the server and the server would stop sending video. Thus, all the intelligence would be stored at a _centralized point_ and the clients, which can be quite diverse, would have to do minimal amount of work
- Another option was to use the already existing _HTTP protocol_. In this case, the server is essentially stateless and the intelligence to download the video will be _stored at the client_. A major advantage of this is that content providers could use the already _existing CDN infrastructure_. Moreover, it also made bypassing middleboxes and firewalls easier as they already understood HTTP. Because of the above advantages, the original vision was abandoned and content providers ended up using _HTTP_ for video delivery

### Summarize how progressive download works

- Instead of downloading the content all at once, the client tries to _pace_ it. This can be done by sending byte-range requests for part of the video instead of requesting the entire video. Once the video content has been watched, it sends _request for more content_. Ideally, this should be enough for streaming without stalls
- Thus, downloading video content over the Internet takes time which _depends on the network throughput_
- We know that Internet is best-effort and throughput over the Internet is variable. This can lead to unnecessary stalling if the client is doing pure streaming i.e., downloading the video content just before it is to be played To account for these variations, _client pre-fetches_ some video ahead and stores it in a _playout buffer_. The playout buffer is usually defined in terms of number of _seconds of video that can be downloaded in advance_ or in terms of _size in bytes_. For example, the video buffer can be 5 seconds. Once the video buffer becomes full, the client will wait for it to get depleted before asking for more content. Streaming in this manner typically has two states:
  1. **Filling state**: this happens when the _video buffer is empty_ and the client tries to fill it as soon as possible. For instance, in the beginning of the playback, the client tries to download as fast as possible until the buffer becomes full
  2. **Steady state**: _after the buffer has become full_, the client waits for it to become lower than a threshold. After which, the client sends a request for more content. The steady state is characterized by these _ON-OFF patterns_

### How to handle network and user device diversity?

- A single-bitrate encoded video is **not** the best solution given the diversity in streaming context. Instead, content providers _encode their video at multiple bitrates_ chosen from a set of pre-defined bitrates. Specifically, the video is _chunked into segments_ which are usually of equal duration. Each of these segments is then encoded at multiple bitrates and stored at the server. The client request while requesting for a segment also specifies its _quality_. This is known as **bitrate adaptation**
- It is important to realize that video content is _downloaded by the video player at the client_. You might ask how does the client know about the different encoding bitrates that are available, and how does it know about the URL of each of the video segments? At the beginning of every video session, the client first downloads a _manifest file_, again over HTTP. The manifest file _contains all the metadata information_ about the video content and the associated URLs.

### How does the bitrate adaptation work in DASH?

- The video player at the client-side downloads the video content using HTTP/TCP over the network. Moreover, the client _dynamically adjusts the video bitrate_ based on the network conditions and device type. This is known as **DASH (Dynamic Streaming over HTTP)** where dynamic streaming signifies the dynamic bitrate adaptation
- A video in DASH is divided into _chunks_ and each chunk is _encoded into multiple bitrates_. Each time the video player needs to download a video chunk, it calls the _bitrate adaptation function_, say $f$. The function $f$ that takes in some input and outputs the _bitrate of the chunk_ to be downloaded
- The bitrate adaptation algorithm at the _client_ adapts the video bitrate or essentially the _quality of video chunks_ to download based on its _estimation of the network conditions_
- There can be _different functions_ for bitrate adaptation that take into account _different kinds of input_

### What are the goals of bitrate adaptation?

- A bitrate adaptation algorithm essentially tries to optimize the user’s viewing quality of experience. A good **QoE (Quality of Experience)** is usually characterized by the following:
  1. _Low or zero re-buffering_: users typically tend to close the video session if the video stalls a lot
  2. _High video quality_: the better the video quality, better the user QoE. A higher video quality is usually characterized by high bitrate video chunk
  3. _Low video quality variations_: a lot of video quality variations are also known to reduce the user QoE
  4. _Low startup latency_: startup latency is the time it takes to start playing the video since the user first requested to play the video. Players typically fill up the video buffer a little before playing the video
- It is interesting to note that the different metrics characterizing QoE are _conflicting_. For instance, in order to have a high video quality, the player can download the higher bitrate chunks. However, it can lead to re-buffering if the network conditions are not good. Similarly, to avoid re-buffering, player can change either download the lowest bitrate, which leads to a low video quality, or change the video bitrate as soon as it notices a change in the network conditions, which leads to high video quality variations
- The goal of a good bitrate adaptation algorithm then is to consider these _trade-offs_ and _maximize_ the overall user QoE

### What are the different signals that can serve as an input to a bitrate adaptation algorithm?

- **Network throughput**: The first signal that can facilitate the selection of bitrate is the _network conditions_ or more specifically the network throughput. Ideally, you would want to select a bitrate that is equal or lesser than the available throughput. Bitrate adaptation using this signal are known as _rate-based adaptation_
- **Video buffer**: the _amount of video in the buffer_ can also enable to decide the video bitrate of the next chunk. For instance, if the video buffer is full, then the player can possibly afford to download high-quality chunks. Similarly, if the video buffer is low, the player can download low-quality chunks so as to quickly fill-up the buffer and avoid any re-buffering. Bitrate adaptation based on the video buffer is known as _buffer-based adaptation_

### Explain buffer-filling rate and buffer-depletion rate calculation

- The **buffer-filling rate** is essentially the _network bandwidth divided by the chunk bitrate_. For example, assume the available bandwidth is 10 Mbps, and the bitrate of the chunk is 1 Mbps. Then, in 1 second we can download 10 s of video. Thus the buffer-filling rate is 10. Now, the buffer-depletion rate or the output rate is simply 1. This is because 1 s of video content gets played in 1 s
- In order to have a stall-free streaming, clearly the buffer-filling rate should be _greater_ than the buffer-depletion rate. In other words, $C(t)/R(t) > 1$ or $C(t) > R(t)$
- However, $C(t)$ is the future bandwidth and there is _no way of knowing it_. A good estimate of the future bandwidth is the bandwidth observed in the past. Therefore it uses the _previous chunk throughput_ to decide the bitrate of the next chunk

### What steps does a simple rate-based adaptation algorithm perform?

- A simple rate-based adaptation algorithm has the following steps:
  1. **Estimation**: the first step involves _estimating the future bandwidth_. This is done by considering the throughput of the _last few downloaded chunks_. Typically, a smoothing filter such as moving average, or the harmonic mean is used over these throughputs to estimate the future bandwidth
  2. **Quantization**: where the _continuous throughput_ is mapped to _discrete bitrate_. Basically, we select the maximum bitrate that is _less_ than the estimate of the throughput, including a factor in this selection

### Explain the problem of bandwidth over-estimation with rate-based adaptation

- Under the case when the bandwidth changes rapidly, the player _takes some time to converge_ to the right estimate of the bandwidth

### Explain the problem of bandwidth under-estimation with rate-based adaptation

- As the _bitrate becomes lower_, the _chunk size reduces_. This further aggravates the problem. In the presence of a competing flow, a _smaller chunk size_ would _lower the probability_ for the video flow to get its fair share. Thus, the player ends up _further underestimating_ the network bandwidth and picks up _even a lower bitrate_ until it converges
- Note that this problem happens because of the _ON-OFF behavior in DASH_. Had it been two competing TCP-flows they would have gotten their fair share. While we have seen this problem for DASH and a competing TCP flow, it can also happen in _competing DASH players_ leading to an unfair-allocation of network bandwidth
