---
layout: post
title:  "Trying out Red Hat Openshift for containerisation"
date:   2021-03-13 21:01:54 +1100
category: Tech
---
There is a free demo available for anyone to try out Red Hat Openshift.
Here is the link:
https://developer.ibm.com/openlabs/openshift

I gave it a try myself and was able to learn the following:

Lab1:
You will learn to deploy a node.js web application over an openshift cluster. Just a reminder that openshift is based on Kubernetes and orchestrates the flow of multiple nodes for you.
In the lab, sample code is provided so you just need to follow the instructions.
The nodes are provisioned in a matter of minutes and scaling (CPU and memory) can easily be done with some editing of YAML file.

Lab2:
You will learn to provision a small database. Another reminder here that in the containerised architecture, we use many small databases to serve particular purposes, instead of having one large DB.
You will bind the service and be able to see how the data flows in and out of the database.
In the example Cloudant is used, and you can also use a portal to check the contents while testing.

Lab3&4:
You will learn the various monitoring and logging tools.
Part of containerisation is that there will be small moving parts that are interdependent. It is important to know the health of individual components, and so monitoring and logging helps.

Lab5:
You will learn how to add a slightly more complicated architecture that includes AppID for authentication together with open source application JavaSpringboot. The main topic is on security, as it is crucial that we set up a robust and secure web application using openshift.


* There has been more updates in the labs, it would be worth going back and trying some more!