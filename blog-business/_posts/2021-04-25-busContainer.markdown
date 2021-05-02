---
layout: post
title:  "Does my business need microservices architecture?"
date:   2021-05-02 21:01:54 +1100
category: Business
image: /images/kubernetes.png
image1: /blog-business/assets/images/container1.png
---

Containers, microservices architecture. I’m sure these buzz words are very familiar.  
There is an increase in popularity for adopting this new style of managing IT, and probably the most common reason you will hear is that it helps to ‘modernise’ (transform legacy systems to latest ones) and convert monolith applications to microservices.  
Well this sounds nice, and we hear business like the famous Netflix adopting this and seeing success.  
However, have we considered the ‘purpose’ of the conversion, and the caveats?

### Purpose and caveats:  ###
Yes microservices architecture definitely has its advantages. It could help with agility and faster time-to-market, create innovation, achieve better resilience and improve ROI and TCO (total cost of ownership). However it is not a silver bullet. As much as it will be very powerful in certain contexts, it is not necessarily a one-size-fits-all solution to anything. So we want to be clear ‘why’ we are doing microservices and shift our mindset from implementing this new technology then seeing some results, to finding a business case (inefficient processes need to be improved, faster time-to-market is essential etc).  
And yes, it also comes with some caveats. Such as? Like the high learning cost and commitment required to modernise processes and possibly even culture. In order to change from monolithic to container applications, codes need to be refactored so it won’t be a simple lift and shift, and depending on your environment this could be a 12-18 months project. It will certainly be worth it when it is all set up, however there needs to be right expertise and implementation in order to facilitate a smooth transitioning.

So all team members would need to be on-board, whether it be the business decision maker, operations team, developer team, security team and any other teams. The key question I personally feel is important is, **how much do we need to know?**  
Container architecture is a very deep concept. We don’t want to get too caught up, but we certainly need to have enough information to assess the fit for the business. This blog is serving as a starting point for key considerations from a business perspective, and I will write further technical blogs for people in roles who need the depth.

## Key considerations for microservices architecture: ##

### 1. The basic definition of microservices architecture and other key words ###  
Definition of microservices, as borrowed from [microservices.io](https://microservices.io/) (blog run by Chris Richardson who is also the founder of the original CloudFoundry.com):

> **_Microservices - also known as the microservice architecture - is an architectural style that structures an application as a collection of services that are:  
    Highly maintainable and testable  
    Loosely coupled  
    Independently deployable  
    Organized around business capabilities  
    Owned by a small team  
The microservice architecture enables the rapid, frequent and reliable delivery of large, complex applications. It also enables an organization to evolve its technology stack._**

So what does that mean? I would especially focus on the ‘loosely coupled’ feature. If services are tightly coupled, they are dependent such that failures in upstream services could cause failure in downstream services like a domino effect; which can be catastrophic. We wish to ‘de-couple’ the services in order to prevent outages from one service affecting another.

How do we de-couple them? **Containers!** (Yes containers and microservices are different). Containers are best described with metaphor or a container ship with services packages as one container, and can be moved around anywhere.  
How do we use containers? **Container platform like Docker!** (Docker is common but there are others like rkt). Docker allows you to run containers over linux OS on a docker engine. As long as you have a system running linux, the services can be run anywhere. And it’s very light weight too. Regardless of your technical involvement in the business, it would be good to reference the following diagram and get an idea of the light-weightedness:

![]( {{page.image1 | relative_url}})

Running the container platform manually could require further developer skills and efforts to manage. So how do we automate this? **Container ‘orchestration’ platform like Kubernetes!** Kubernetes automates the process of scaling, managing, updating and removing containers. We need containers in the first place to orchestrate, so docker enables containers and kubernetes orchestrates.

Kubernetes is open-source which means a lot of the features are DIY and community-driven. Various cloud vendors like IBM provide value-added offerings to give further support.  
How do we have a better experience with container orchestration with ease of use and further automation of workflows? Redhat Openshift! One key value of openshift revolves around the question: do you want to learn all Kubernetes commands and essentially manage your applications from the command line interface — or do you prefer to save yourself some time and deploy, run, and manage your applications from a simple web console in your browser?  
[OpenShift vs. Kubernetes for developers](https://developer.ibm.com/videos/openshift-vs-kubernetes-for-developers/)

### 2. What is good for microservices and what isn’t? ###  
- Considering microservices definitely is good if there’s a particular purpose to achieve, such as to deploy things faster, get new features out quicker and control scaling.  
- Transforming to a microservices architecture is a long-term steady change process so it is not ideal for IT reformation that needs quick results.  
- If the services used are already very small, then it would be hard to de-couple and make it even smaller, so it wouldn’t be suitable in this case. Moderate size services are more suitable  
- Using microservices would mean using distributed systems. This could bring about new complexities, so you would need to be on top of this with adequate staff expertise. Openshift could possibly simplify this

### 3. What Technical debt does my business have? ###  
In order to know what exact problem microservices will address, it would be good to know what problems exist. A good way is to assess the technical debt of the business. Technical debt is a metaphor similar to financial debt, where we make certain efforts such as when we need to deliver functionalities that otherwise would have taken less time. There is a good example in [The Hidden Cost Of Technical Debt](https://medium.com/serious-scrum/the-hidden-cost-of-technical-debt-1963b958e5ed), where an engineer has to spend 2 days extra to work on validating certain code as a result of poor quality of code. If this continues and accumulates, the high cost due to inefficiency becomes apparent.  
Key questions to ask: Is there lack of flexibility? Are processes slow? Is your DevOps working with the current process? Is the system experiencing frequent downtimes? How much effort is spent on dealing with these problems?


### 4. Therefore, what problems will the microservices architecture solve? ###
I have covered the importance of de-coupling services, automation with container orchestration platforms, identifying problems to be solved. Now we just have to put it together. The important point here is that the goals come first, and we have microservices as a tool to achieve that goal.  
In the following blog, there are real life examples of businesses that implemented microservices, however it was not an efficient design since it was focused on ‘implementing microservices for modernisation’, instead of goals like ‘deploying things faster’. That way we can truly unlock the benefits of microservices.

[It’s time to stop making “Microservices” the goal of modernization.](https://medium.com/ibm-garage/its-time-to-stop-making-microservices-the-goal-of-modernization-71758b400287)


### 5. Execution ###  
If you were to implement microservices, how will you do it? Eventually, sizing will be required to assess how many nodes (container-equivalent for Virtual Machines in a hypervised infrastructure) are required. The architecture and cost will be important to review too.  
In terms of the cost, it is not only the cost of the service, but important is the improvement in Total Cost of Ownership and how much operational cost can be saved as a result of a successful transformation.  
Remembering that it takes time to refactor the services, companies generally start small with a particular section of the business to be transformed first. It is also typical for businesses, once a small-part transformation is made, to set up load balancing and have some customers directed to the microservices version of the service. That way the service can be tested before it is fully implemented.  


References:  
[Monolith to Microservices + Event-Driven Architecture](https://sebalopezz.medium.com/monolith-to-microservices-event-driven-architecture-ff4284bf4ecf)

[ Kubernetes vs. Docker: A Primer](https://containerjournal.com/topics/container-ecosystems/kubernetes-vs-docker-a-primer/)

[Microservices and Distributed Systems](https://medium.com/@kenlynterai/microservices-and-distributed-systems-36a90d5d8ce)