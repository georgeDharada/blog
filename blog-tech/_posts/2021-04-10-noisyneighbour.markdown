---
layout: post
title:  "When do noisy neighbour effects kick in? How to avoid it?"
date:   2021-04-10 21:01:54 +1100
category: Tech
image: /images/networkingicon.png
image1: /blog-tech/assets/images/noisy1.png
---

The essence of public cloud is to have servers on demand, which could sometime mean you are sharing the host with another customer.
Will this impact you? And what can we do to avoid the 'noisy neighbour effect'?
Lets start by seeing when the noisy neighbour effects apply.

### What is the noisy neighbour effect and when does it apply?

Typically, virtual servers work in a way, the original hosting machine is hypervised to multiple virtual instances of servers, and a particular instance is available to be purchased as a virtual server (I call VSI from here).
So what happens to the rest of the servers in the host? Other customers use it.

It is also nice to know the term: CPU Steal Time
Definition from IBM:
    Steal time is the percentage of time a virtual CPU waits for a real CPU while the hypervisor is servicing another virtual processor.

So as simple as we put it, until particular work by other customers using the server is finished, there could be some wait for your VSI to process your tasks.

Next, lets talk about how the CPU works in this case.  
For virtual servers the CPU is virtualised and represented as 'vCPU'. However, it is not the case that the CPU is cut in half (both literally and technically).  
We cannot allocate 50% to one and 50% to another VSI if there were 2 VSI in the host, it is a little more complex.  
Behind the scenes, there are threads. Threads are CPU instructions and sometimes called processes. CPUs handle these instructions and even though the CPUs generally have multi-thread capabilities to handle multiple threads simultaneously, the boundaries are not clear cut. Hence a vCPU spike in one VSI may affect the performance of another VSI.

![]( {{page.image1 | relative_url}})

There's some good reading on this here:  
[Hyper-V Virtual CPUs Explained](https://www.altaro.com/hyper-v/hyper-v-virtual-cpus-explained/)  
[Understanding CPU Steal Time - when should you be worried?](https://scoutapm.com/blog/understanding-cpu-steal-time-when-should-you-be-worried)


### What is the impact of a noisy neighbour effect and what can I do about it?

In terms of impact, simply it could lower the performance of your server.  
How it is impacted can be measured by using monitoring tools, however as it is inconsistent and you have no visibility over how the other customers are using their VSI, it is unpredictable.  
So in essence, you will have to trade off your peace of mind and accept that there may be 'busy' times.  

If for example you are using VMware to hypervise your servers yourself, and if you are concerned about one of your VSIs affecting the other VSIs due to it's CPU usage, then you would have the administration tool to help with the monitoring and migration to isolated CPU-intensive servers. (like vMotion)

Netflix seems to have strategies to quickly spin up new VSIs and migrate over to that host if they see strong impacts of noisy neighbour effects. Of course that comes with a cost, and if not then we would need to bear with it.


### What if I need to avoid it?

FR1: Provide IaaS capabilities on the global cloud platform  
NFR: Have reliable performance that is not affected by noisy neighbours

Architecture decision: If your requirements include avoiding the effects, then the simple option is to go to a dedicated host:  
1. Virtual server dedicated host  
2. Bare metal server

With these options you will not face the noisy neighbour effects. Alternatively:

3. You can also hypervise the servers yourself with VMware, and control the effects internally. However in that case you will not suffer from other people's workload, but you may suffer from your own workloads.

If for example you are using VMware to hypervise your servers yourself, and if you are concerned about one of your VSIs affecting the other VSIs due to it's CPU usage, then you would have the administration tool to help with the monitoring and migration to isolated CPU-intensive servers. (like vMotion)

There's some good reading on this here:  
[What’s a “Noisy Neighbor,” and How Can ControlUp Shut Them Up?](https://www.controlup.com/resources/blog/entry/whats-a-noisy-neighbor-and-how-can-controlup-shut-them-up/)  
[Understanding the Impact of a Noisy Neighbor Using vRealize Operations](https://blogs.vmware.com/management/2016/11/understanding-impact-noisy-neighbor-using-vrealize-operations.html)


### Is my data performance affected too?

When reading and writing data, the noisy neighbour effects kicks in too.  
The reason why VSI storage does not typically offer IOPS measures is because various effects could influence the speed of the read and write.  
So what if you need constant and reliable data transfer? It would be best to use bare metal server for databases. (Or at least a dedicated VSI host).  
Just for storage needs, you can also use File or Block storage, which gives you a more exact IOPS measure for your storage.


### What are other benefits of bare metal server over virtual server?
With bare metal server you cango up to 10GB network uplink for a low latency network connection.  
Virtual servers only allow up to 1GB, so you have more control over the speed.

Further, recently IBM Cloud introduced 25GB network options for certain baremetal servers.  
For more information, refer to the following page:  
https://www.ibm.com/cloud/blog/announcements/newly-released-25gbe-standard-on-ibm-cloud-bare-metal-servers