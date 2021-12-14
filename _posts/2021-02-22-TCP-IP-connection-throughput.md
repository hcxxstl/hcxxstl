---
title: TCP/IP connection throughput
auther: terry
layout: post
categories: networking
excerpt_separator: <!--more-->
---

This post is about some basic concepts and the possible bottlenecks of the TCP/IP connection.
<!--more-->

## Concepts

### Round Trip Time (RTT)

$$ RTT = t_{sendData} + t_{recieveAck} $$

You can use `ping` command to check RTT. RTT = ping time.

RTT is often 2x end-to-end delay.

### Bandwidth-delay product (BDP)

$$ BDP = Bandwodth * Delay $$

A large BDP could be because of a high bandwidth, a high latency or both. BDP represents the size of unacknowledged data in the wire ("in flight").

Example:
$$
RTT = 1ms, BW = 10Gbits/s \\
BDP=10Mbits=1.25MB
$$

### Buffer

The amount of memory that sender/receiver can store buffer.

* The receiver side: The amount of data it can accept without acknowledging the sender.
* The transmitter side: The amount of data it can hold in memory without getting acknowledgement from receiver.

### Receive Window

The size of available buffer of receiver side. If the receiver can not egress the data as the speed of ingress, there will be some data not processed and occupy the buffer. Thus, the window size will become smaller. If the receiver can consume the traffic at line rate, the window size will not shrink.

* The window size should be proportional to the BDP. The send side should have the same window size as the receive side.
* The largest window size is usually 65535 (64K - 1) Bytes, which is due to that the window size takes 2 bytes in the TCP header (2^16 = 64k)
* With window scaling, a much larger size can be achieved. A scaling factor value is added to the TCP header. The scaling requires the capability on both sides confirmed during handshaking. A zero window size means the recieve buffer is full and can halt the transmission.

## Connection speed bottlenecks

### Window size

$$ Throughput \leq \frac{ RWIN }{ RTT }$$

Where the $RWIN$ is the recieve window.

### Path MTU

The larger the MTU the more data can be transmitted within a RTT. Of course, a larger MTU should cooperate with a larger window buffer.

A larger MTU will also lead to less head overhead, since the percentage of header bytes will be smaller.

### Loss rate

$$ Throughput \leq \frac{MSS}{ RTT \sqrt{P_{loss}} }$$

Where $MSS$ is maximum segment size, $ MSS = MTU - 40Bytes $, $P_{loss}$ is the probability of packet loss.

### Parallelism

A simple way to improve throughput is to open multiple TCP connection in parallel. The throughput of single connection is limited by the factors mentioned above. But with parallelism, we can scale up the throughput.

### Physical Capability

Apparently, the physical link will ultimately limit the throughput. This set the upper bound of throughput.

<!-- TODO: categorize bottlenecks -->

## References

* [TCP series #4: TCP receive window and everything you need to know about it, ACCEDIAN](https://accedian.com/blog/tcp-receive-window-everything-need-know/)
* [Difference between tcp recv buffer and tcp receive window size? StackExchange](https://serverfault.com/questions/445487/difference-between-tcp-recv-buffer-and-tcp-receive-window-size)
