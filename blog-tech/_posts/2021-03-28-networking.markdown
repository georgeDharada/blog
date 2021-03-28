---
layout: post
title:  "How do I design my network with IBM Cloud? Basics"
date:   2021-03-28 21:01:54 +1100
category: Tech
image: /images/networkingicon.png
image1: /blog-tech/assets/images/network1.png
image2: /blog-tech/assets/images/network2.png
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
In IBM Cloud, every server is given a public IP and private IP.
IBM Cloud has a large private network which connects all the servers.
Only segments of the private network are allocated with vlans to users.
A server in a particular vlan cannot access other vlans in other cloud accounts.
By default, it also cannot access other vlans in the same cloud accounts. You can enable VRF to the vlans can communicate with each other.

![]( {{page.image2 | relative_url}})
---

> **_NOTE:_**  The note content.


This is an 'agile' blog post. More details will be added




