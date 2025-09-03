---
marp: true
theme: graph_paper
style: |
  img {
    background: transparent;
    border: none;
    min-width: 500px;
  }
footer: ACIT 2620 Principles of Enterprise Networking
author: Yves Rene Shema
---
<style scoped>
  h1, h2, p, footer {
    color: white
  }
</style>

![bg opacity:.9](../img/networking.jpg)

# ACIT 2620

## Principles of Enterprise Networking

By: Yves Rene Shema

---

## Objectives

* Course logistics
* Overview of networking concepts and terminologies
* Layered networking model 
* Project introduction 
* Packet capture

---

## Course logistics

### Software and equipment

* Software: Python 3, Virtualbox, Wireshark
* Equipment: 
  * Windows 10 or higher, preferably Pro or Education editions
  * Limited support for Mac, especially the new Apple Silicon generation (i.e. you may need to get a different computer for this course. Older Macs are fine.)
  * Linux: I'll suppose you know what you're doing

---

### Assessment


| Criteria | % | Comments |
| --- | --- | --- |
| Quizzes | 40 | Four equally weighted quizzes. No midterm |
| Project | 20 | Cumulative. 5 milestones | 
| Final exam | 40 | Practical, based on project |

* Quizzes are in person. If you miss a quiz, it's gone; there are no makeovers!
* Late project submissions (more than 1 week after deadline) will not be graded.
  
---

## Examples of networks

- Forget about computer networks for now

---

## Attributes of networks

- What attributes or characteristics make something a network

---

## What are computer networks made of

- Example:
  - The internet

---

# Definitions

---

## Network

* Collection of `nodes` connected by some type of transmission media or `link`, for the purpose of sharing services, devices or data (i.e. networked `resources`)

---

## Node

* Any device that can communicate over the network and is identified by a unique identifying number, known as its `network address`.

---

## Link

![transmission medium/link](../img/intro/link.png)

---

## Media concurrency and direction

![media concurrency](../img/intro/concurrency.png)

---

# Resource Control

---

## Client-server Networks

![client-server network width:60%](../img/intro/client-server.png)
  
---

## Peer-to-peer Networks

![p2p network](../img/intro/peer-to-peer.png)

---

## Types of Networks

* LAN
* WLAN
* PAN
* CAN
* MAN

---

* WAN
* SAN
* EPN
* VPN
* [Learn more](https://www.belden.com/blogs/network-types)

---

# Switching Methods

---

<style scoped>
  img {
    display: block;
    margin: 0 auto;
  }
</style>

## Circuit Switching

![circuit switching](../img/intro/circuit-switching.png)

---

<style scoped>
  img {
    display: block;
    margin: 0 auto;
  }
</style>

## Packet Switching

![packet switching](../img/intro/packet-switching.png)

---

<style scoped>
  img {
    display: block;
    margin: 0 auto;
  }
</style>

## Protocols

![how protocols work](../img/intro/protocol-depiction.png)

---

* Mutually agreed upon rules for communication
* Define the format, order of messages sent and received among network entities, and actions taken upon transmission, receipt, and timeout
* Govern all communication activity on the internet

---

## Example Protocols

---

<style scoped>
  section {
    border: 1em solid transparent;
  }
</style>

## Layered networking model

![bg right contain](../img/intro/dod-vs-osi.png)

---

## Layered why?

- Managing complexity: explicit structure allows identification and makes explicit the relationship of complex system's pieces
- Modularization: changing of an implementation of a specific layer's service is hidden from the rest of the system

---

<style scoped>
  section {
    border: 1em solid transparent;
  }
</style>

## Encapsulation

![bg right contain](../img/intro/encapsulation.png)

---

<style scoped>
  section {
    border: 1em solid transparent;
  }
</style>

## Protocol Data Units (PDU)


![bg right contain](../img/intro/layers-pdu.png)


---

## Wireshark

- A tool for capturing network traffic for analysis
- [Grab the installer](https://www.wireshark.org/download.html) and install it on your system

---

## Reading list

- This week
  - [OSI Model](https://www.oreilly.com/videos/networking-fundamentals/9780134645711/9780134645711-NETP_1_1_0_0/)
  - Optional reading:
    - [Wireshark: filtering while capturing](https://www.wireshark.org/docs/wsug_html_chunked/ChCapCaptureFilterSection.html)
    - [Capture filters](https://wiki.wireshark.org/CaptureFilters)
    - [Display filters](https://wiki.wireshark.org/DisplayFilters)

---

- Week Two (read/watch these before next class)
  - [Common Network Infrastructure devices](https://www.oreilly.com/videos/networking-fundamentals/9780134645711/9780134645711-NETP_2_2_0_0/)
  - [Network devices](cisco_network_essentials_ch10_network_devices.pdf)
  - [Network Topologies](https://www.oreilly.com/videos/networking-fundamentals/9780134645711/9780134645711-NETP_3_0_0_0/)
  - [Overview of networks](https://intronetworks.cs.luc.edu/current2/html/intro.html)
  - Optional (but highly recommended):
    - [Virtualbox Networking Modes](https://www.virtualbox.org/manual/ch06.html#networkingmodes)
    - [Linux command line (recommended for beginners)](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)