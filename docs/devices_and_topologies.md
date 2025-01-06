---
marp: true
theme: graph_paper
footer: ACIT 2620 Principles of Enterprise Networking
author: Yves Rene Shema
---

<!--
_color: rebeccapurple
-->
![bg opacity:.5](../img/networking.jpg)

# ACIT 2620

## Principles of Enterprise Networking

By: Yves Rene Shema

---

## Objectives:

* Recap of OSI Model
* Survey of networking devices
* Overview of common network topologies
* Project setup

---

## OSI Model Recap

(7) **Application**: domain specific messages
(6) **Presentation**: data formatting (e.g. encryption, compression, character encoding)
(5) **Session**: organizing of messages into "visits"
(4) **Transport**: multiplexing, segmentation, re-assembly
(3) **Network**: routing datagrams between networks, global addressing
(2) **Data-Link**: communication on shared medium
(1) **Physical**: signals across medium (bits)

---

## Broadcast Domain vs Collision Domain

A broadcast domain is a group of nodes sharing the same transmission medium (i.e. LAN or simply `network`). When these nodes are not connected through a switch (or bridge), the network constitutes a single collision domain.

---

## Network Devices

Define the function and uppermost OSI layer implemented by the following devices:

* Network Interface Controller/Card
* Hub
* Bridge
* Switch

---

* Router
* NAT Router
* Wireless Access Point (WAP)
* Firewall

---

## Network Topologies

* Bus
* Ring
* Star
* Mesh
* Hybrid

---

## Reading List

Read this before next class:

- [Ethernet Fundamentals](https://www.oreilly.com/videos/the-complete-cybersecurity/9780136173717/9780136173717-SPTT_00_08_05_00/)
- [Ethernet Basics](https://intronetworks.cs.luc.edu/current2/html/ethernet1.html)
- Optional:
  - [VIM basics](https://www.howtoforge.com/vim-basics) (or just type `vimtutor` in a linux terminal and follow along)
  - [A `tcpdump` Tutorial with Examples](https://danielmiessler.com/study/tcpdump)