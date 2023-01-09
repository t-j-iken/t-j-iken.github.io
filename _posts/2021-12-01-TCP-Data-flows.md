---
layout: post
title: "School Project: TCP Data Flows"
categories: misc
---

### Background

TCP is one of the main protcols for TCP/IP. TCP provides an ordered, and reliable, way of delivering and transmitting data. TCP is _connection orientated_, as in it establishes a connection between client and server before transmitting any data. Understanding how data is organized, encapsulated, and transferred throughout a network is vital in security.

Given a **.pcap** file of network traffic, build a TCP Summary table reporting properties of TCP flows.

### TCP Flows

A TCP Flow can be defined by the 4 tuple: `Source IP Address, Source Port, Destination IP, Destination Port`. A TCP flow begins with a packet with the `SYN` flag set, and ends with the `FIN` bit set. A flow with a `SYN` bit but no `FIN` bit is _incomplete_. 

Our table reports the following properties:

1. Name
2. Source IP
3. Source Port
4. Dest. IP
5. Dest. Port
6. Total packets in complete flows
7. Total packets in incomplete flows
8. Total bytes
9. Average bandwidth in Mbps.

Code and project available on GitHub.