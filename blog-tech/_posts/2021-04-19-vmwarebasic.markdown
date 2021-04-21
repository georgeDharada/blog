---
layout: post
title:  "Which VMware option should I go with for my use case?"
date:   2021-04-19 21:01:54 +1100
category: Tech
image: /images/vmware.png
image1: /blog-tech/assets/images/vmware1.png
image2: /blog-tech/assets/images/vmware2.png
image3: /blog-tech/assets/images/vmware3.png
image4: /blog-tech/assets/images/vmware4.png
---

Any company utilising IT would need to have a Data Center to manage IT infrastructure.
However, Data Center management can get complex and costly as we are scaling. If we add a little here and there, eventually we will lose track of how it all works together.
Not only that, today there is more pressure to increase IT services but keep the budget the same, businesses are pressured to reduce costs somehow.  
That’s where VMware comes in!

Read more in [What is Data Center Virtualisation](https://www.vmware.com/products/datacenter-virtualization.html)

### Give me a quick summary of Data Virtualisation! -> ###  
Data Virtualisation gives the benefit of eliminating silos with modern IT infrastructure management, brings operation efficiency and allows you to go on the cloud to help modernise.  
The way it works, it will provide the ability to hypervise and create multiple VMs; this helps management become easier. It also helps abstract away the Compute, Storage and Network layer by decoupling physical layers and letting you manage the logical layers (logical network etc) so you can repurpose on demand.  
This reduces capital expense by maximising utilisation. It also helps reduce downtime by using live migration features, and has more add-ons that add further value.

![]( {{page.image1 | relative_url}})

### Ok, great, what options are available? And what is the difference between ESXi, vSphere and vCenter? -> ###  
My best 1 sentence summary is: ESXi is the hypervisor, vSphere is a product suite and manages VMs over ESXi generally single host, vCenter allows for management of VMs over multiple hosts.

> **_FUN FACT:_**  ESXi is essentially the type-1 hypervisor, that splits the server into multiple VMs. Initially ESX was released in 2001, which was loaded with linux as base OS, and it was upgraded to ESXi include remote command line interface to make it very lite and reduce attack surface. vSphere was released in 2009 along with vCenter, starting with version4.0. The command line interface for ESXi looks yellow and black like below:

![]( {{page.image2 | relative_url}})

If starting with a basic use case to incorporate hypervising technology, then vSphere will be where to start.  
Licenses can be obtained through VMware, whether as vSphere licenses, or Storage vSAN, Network NSX licenses.  
With vSphere, you get a HTML5 client where you can do operations like adding new VMs.

![]( {{page.image3 | relative_url}})

> **_FUN FACT:_**  vSphere HTML5 is the standard for the client today, and before it used to be managed with a web client that ran on flash. However flash is EOS so it was depreciated.

With vCenter, you would need additional license but it brings the following benefits:  
1. Analyze and remediate issues quickly with visibility into vSphere virtual infrastructure.  
2. Deliver the security and availability of vSphere through automated proactive management features such as automated load balancing and out-of-the-box automation workflows.  
3. Extend virtualization capabilities using third-party ecosystem solutions.  
4. Solve problems faster with best in class VMware Log Management  
5. Migrate VMs from one host to the other using vMotion (vSphere can migrate, but not while VM is running and it requires shared storage)  
6. Good for Disaster Recovery and High Availability too!

In other words, you can still use vSphere without the vCentre, however you will not get the added benefits of DR and HA etc. So vCenter is recommended.  
You can connect to vCenter Server with a vSphere client, and instead of one host you can see multiple hosts at once. To enable vCenter, you would need to install the vCenter Server Appliance (vCSA), which can sit on top of a VM in vSphere.  

> **_FUN FACT:_**  There used to be vCenter Server for Windows, which VMware said farewell too: https://blogs.vmware.com/vsphere/2017/08/farewell-vcenter-server-windows.html. vCSA is the standard today.


Here’s another question. **I have VMware workloads on-prem and want to get it on cloud. What is the easiest way?**

### Lift and Shift ###
If you wish to minimise the efforts required to refactor (rewrite parts of code or operation in order to migrate), then the best solution is to ‘lift and shift’. Fortunately, IBM Cloud offers the option to lift and shift existing VMware workloads directly onto IBM Cloud’s bare metal servers.  
This is something no other cloud providers have, since with other providers there are some form of refactoring involved and so you need to take into account additional costs.

More on the advantage of using IBM Cloud for lifting and shifting VMware workloads:  
[Lift and shift seamlessly with IBM Cloud for VMware Solutions](https://imaginenext.ingrammicro.com/b2b-tech-talk/lift-and-shift-seamlessly-with-ibm-cloud-for-vmware-solutions)

IBM Cloud VMware solutions are enterprise-grade, hybrid and developer-ready, secure to the core and AI-powered. By starting the journey to cloud, this will also open new paths to integrating with cloud native applications!  
Further benefits:  
1. Flexible scaling of workloads according to business needs  
2. You control the full stack from software to hardware for your vSphere, therefore meeting strict permission and compliance regulations. You can even lift and shift your whole operation processes!  
3. Utilise fast global network for free with private network  
4. Proven with over 2000 companies enjoying the benefit  
5. For vSphere and vCenter solutions, these are single tennant devices, unlike other cloud vendors who offer multi-tenanted offering for VMware, which means you are subject to the noisy neighbour effect

There are 3 main VMware offerings on IBM Cloud: **vSphere on IBM Cloud (VSS), vCenter Server on IBM Cloud (VCS) and VMware Solutions Shared (VCD)**. Following diagram shows the level of management whether IBM-managed, or customer-managed:

![]( {{page.image4 | relative_url}})

You can deploy new instances of vSphere or vCenter, and especially the vCenter is a very powerful tool that would automate a week-worth of deployment effort and give you a multiple host VMware workload in a very short time.  
It is also possible to Bring Your Own License, or you can purchase licenses through IBM Cloud and pay as you go with monthly billing. Further, the HCX option allows you to migrate data very easily from your on-prem environment.

Other additional information:  
If you have a vSphere instance, you can order vCenter licenses for free over the portal and configure it over one VM on vSphere. Simply navigate to the portal to Classic Infrastructure -> Manage -> VMware licenses.

More insight into how the vCenter looks over IBM Cloud:  
[VMWare vCentre Onboarding on the IBM Cloud](https://www.youtube.com/watch?v=BbtQ1UWhxT4)

VMware Solutions Shared allows you to have most of the resources managed by IBM, so that you can focus on managing the VMs.

For those that are more advanced:  
VMware addons like Spectrum Protect Plus for Backup and Zerto for DRS can be configured
It is possible to manage VMware on other cloud providers with IBM.
Stretch clusters bring additional flexibility around HA: [What is VMware Stretched Cluster?](https://www.vladan.fr/what-is-vmware-stretched-cluster/)
