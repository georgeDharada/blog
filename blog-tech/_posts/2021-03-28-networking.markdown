---
layout: post
title:  "How do I design my network with IBM Cloud? Basics"
date:   2021-03-28 21:01:54 +1100
category: Tech
image: /images/networkingicon.png
image1: /blog-tech/assets/images/network1.png
image2: /blog-tech/assets/images/network2.png
image3: /blog-tech/assets/images/network3.png
image4: /blog-tech/assets/images/network4.png
image5: /blog-tech/assets/images/network5.png
---

The question for today is, what is the best networking architecture for my workload?  
Today I will use an example company to try to explain how you can choose a good architecture for you.


## Scenario 1 Just trying out a BMS
Lets say there is GeorgieCorp, which currently has no cloud.
GeorgieCorp wants to just try the baremetal server to get the feels, not for production but for testing.

FR1: Provide IaaS capabilities on the global cloud platform  
NFR: None  
(FR=Functional requirement, NFR=Non-Functional requirement)

![]( {{page.image1 | relative_url}})

### Reference architecture:

This would not be a practical scenario, but the bare minimum is to have a bare metal server with public and private connection.

![]( {{page.image4 | relative_url}})

Clients can access the server through public IP, so it is important to disable the public network connection to avoid unwanted connection from outside.  
Company users can also connect through public network until it is disabled. Ideally, you would use the private network to connect.  
Company users can use SSL VPN to connect to the private network for operational purposes.  
Public network should be enabled only after enough security measures like firewalls and load balancers are put into place.


---
**The Theory**

In IBM Cloud, every server is given a public IP and private IP.

#### Public Network
Allows the server to connect to the public internet. You have the option to have only Private network connection for a server, and no public network connection. That helps to reduce vulnerability.

Even if your server has public network, you can disable it from the portal.
As aforementioned, anybody could access through the public network, so do ensure you have security tools in place.
You can get a public vlan and subnet, 

> **_FUN FACT:_** For communication between servers in the same Data Center (even if different cloud account), the communication does not go out to the internet, and it is done within the DC. For communication between servers in different DCs, it still does not go out to the internet; it will communicate within the same AS (Autonomous System)

#### Private Network
IBM Cloud has a large private network which connects all the servers.
Only segments of the private network are allocated with vlans to users.
A server in a particular vlan cannot access other vlans in other cloud accounts.

![]( {{page.image2 | relative_url}})

> **_FUN FACT:_**  VLAN uses the separation technique with broadcast domain

By default, servers in a particular VLAN cannot access servers in another VLANS even in the same cloud accounts. You can enable VRF to the vlans can communicate with each other (open a ticket to request).

![]( {{page.image3 | relative_url}})

> **_FUN FACT:_**  Before, IBM had the option of enabling VLAN spanning. Now this is not offered and replaced with VRF. The biggest reason is because VPC (virtual private cloud) does not support VLAN spanning. VRF is a pre-requisite for having Direct Link.

> **_FUN FACT:_**  IBM Cloud data centers are connecting with each other with various internet carriers using public peer exchange: [Public peering](https://cloud.ibm.com/docs/overview?topic=overview-public-peering)


#### How to actually connect to the network?

How do you connect to the network? You have 3 options:
* Through the public network:
   - Internet connection through public network. SSH / HTTPS
   - Use a gateway device like Virtual Router Appliance (VRA) and set your own VPN
* Through the private network:
   - SSL VPN (free service provided by IBM)
   - IPSEC VPN (paid service by IBM)
* Through private network on a private direct connection
   - Direct Link


---


## Scenario 2 Set up basic firewall for public access, and access through VPN for operational purpose
GeorgieCorp decides to add some basic firewall and set up connection from public and private connections.

FR1: Provide IaaS capabilities on the global cloud platform  
FR2: Protect internet facing workloads with network firewall services  
FR3: Ability to access workloads for operational purposes securely using VPN over internet  
NFR: None

### Reference architecture:

![]( {{page.image5 | relative_url}})

Architecture Decisions:  
AD1: Baremetal server for IaaS capabilities  
AD2: SSL VPN for secure connection through private network  
AD3: Hardware firewall for protection with internet facing workloads

The most basic is the hardware firewall that can be added onto a bare metal server.
The baremetal server is ordered with public and private network connectivity, so through the public network people can access via public IP address through firewall. The private IP address can be used to connect to the server via the VPN.


There is room for further enhancements using the VRA and direct link. More updates will be made on this blog post

This is an 'agile' blog post. More details will be added




