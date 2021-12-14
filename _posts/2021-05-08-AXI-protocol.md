---
layout: post
title: AXI protocol
author: terry
categories: fpga
excerpt_separator: <!--more-->
---

This article explains the AXI protocol. Advanced eXtensible Interface (AXI) is a parallel high performance, synchronous, high-frequency communication interface. It is also a burst-based protocol. AXI is used a lot for on-chip communication.
<!--more-->

* Resources
  * [wiki](https://en.wikipedia.org/wiki/Advanced_eXtensible_Interface)

## Handshake

* Two handshake signals
  * xVALID: driven by source to inform that data is valid
  * xREADY: driven by receiver to show it is ready to receive data
* when both xVALID and xREADY is high, a transfer is occurred.
* **two rules (this is important!)**
  * source must not wait xREADY to assert xVALID
  * source must keep a high xVALID until a handshake occurs

## Channels

* Read Address channel (AR)
* Read Data channel (R)
* Write Address channel (AW)
* Write Data channel (W)
* Write Response channel (B)

![read_channel](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e1/AXI_read_channels.svg/885px-AXI_read_channels.svg.png)
![write_channel](https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/AXI_write_channels.svg/591px-AXI_write_channels.svg.png)

## AXI4

## AXI4-Lite

Being a subset of AXI4, AXI4-Lite fully compatible with AXI4 devices.

## AXI Stream

> The AXI4-Stream protocol defines a single channel for transmission of streaming data. The AXI4-Stream channel is modeled after the Write Data channel of the AXI4.

link

* [diference to AXI4](https://developer.arm.com/documentation/ihi0051/a/Comparison-with-the-AXI4-Write-Data-Channel/Differences-to-the-AXI4-write-data-channel)
