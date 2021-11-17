---
layout: post
title:  "How will a direct link improve latency of my network?"
date:   2021-11-17 21:01:54 +1100
category: Business
image: /images/networkingicon.png
---

Direct Link is IBM's cross connect solution that establishes a connection from your on-premise location directly to IBM Cloud. Vendors will be involved in the establishment of the connection, and IBM has multiple direct link offerings. This article is a quick summary of the basics of the offering.

Problems that Direct Link can address:
Increasing performance by reducing latency using Direct Link
• The IBM Cloud Direct Link service is a routed, OSI Layer-3 service.
• It offers a direct connection to the IBM Cloud private network backbone, this makes it secure
• Low latency and speeds up to 10 Gbps, suitable when you need to transfer a lot of data frequently
• Approximate latency: Latency is approximately 1.5 ms within the local area (or 0.5ms for Direct Link Dedicated Hosting)
• After securing a fast connection, possibly find new ways to use like backup

There are different ways to set up a direct link connection. The best way to get started is to open a ticket and seek assistance from a Cloud Design Engineer. For example if setting a connection between Boston and IBM's Dallas DC, some options (not limited to) are:
1.Cross connect from Boston to Dallas ( Need to check cost with the vendors)
2.Cross connect from Boston to Washington DC Point of Presence, then global routing to Dallas DC
3.Direct Link 2.0 (Higher cost, includes global routing by default, good for VPC)

Direct Link Exchange
•Uses data center providers
For eg:
•Dallas 13 -> CyrusOne
•Dallas 3 -> Equinix

Direct Link Connect
•Uses Telco carriers
For eg:
•Dallas 3 -> AT&T Netbond
•Dallas 4 -> Megaport

Direct Link Dedicated
•Available up to 10Gbps speed
•Single tenant

Direct Link Dedicated Hosting
•Lowest latency
•Manage your own rack space, BYO hardware

Steps involved:
1.Order direct link from IBM Cloud portal and required service from vendor
2.Work with sales engineer and network engineer over IBM Cloud ticket
3.Set up BGP connection, then connection is established

The whole process does takes multiple days, so it would be best to plan accordingly, work with your architect and the Cloud Design Engineer.

Reference:
[https://cloud.ibm.com/docs/direct-link](https://cloud.ibm.com/docs/direct-link)
[https://cloud.ibm.com/docs/dl?topic=dl-get-started-with-ibm-cloud-dl](https://cloud.ibm.com/docs/dl?topic=dl-get-started-with-ibm-cloud-dl)