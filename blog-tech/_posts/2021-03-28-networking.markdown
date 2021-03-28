---
layout: post
title:  "How do I design my network with IBM Cloud? Basics"
date:   2021-03-28 21:01:54 +1100
category: Tech
image: /images/networkingicon.png
image1: /blog-tech/assets/images/network1.png
image2: /blog-tech/assets/images/network2.png
image3: /blog-tech/assets/images/network3.png
---

The question for today is, what is the best networking architecture for my workload?
Today I will use an example company to try to explain how you can choose a good architecture for you.

Lets say there is GeorgieCorp, which currently has no cloud.
Having no cloud footprint yet helps to see things from a clear slate:
![]( {{page.image1 | relative_url}})

Then we have one bare metal server created.
We upload some of the applications onto the server.
How do we now communicate with this server?



---
**The Theory**

In IBM Cloud, every server is given a public IP and private IP. Lets look at the Private network.

#### Private Network
IBM Cloud has a large private network which connects all the servers.
Only segments of the private network are allocated with vlans to users.
A server in a particular vlan cannot access other vlans in other cloud accounts.

![]( {{page.image2 | relative_url}})

> **_FUN FACT:_**  VLAN uses the separation technique with broadcast domain

By default, servers in a particular VLAN cannot access servers in another VLANS even in the same cloud accounts. You can enable VRF to the vlans can communicate with each other.

![]( {{page.image3 | relative_url}})

> **_FUN FACT:_**  Before, IBM had the option of enabling VLAN spanning. Now this is not offered and replaced with VRF. The biggest reason is because VPC (virtual private cloud) does not support VLAN spanning. VRF is a pre-requisite for having Direct Link.

How do you connect to the private network? You have 3 options:


#### Public Network

---



Problem 1:


Reference Architecture:




This is an 'agile' blog post. More details will be added




