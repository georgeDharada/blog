---
layout: post
title:  "Mini-demo: How can I optimise storage by using IBM Cloud object storage?"
date:   2021-08-28 21:01:54 +1100
category: Tech
image: /images/icos.png
image1: /blog-tech/assets/images/icos1.png
image2: /blog-tech/assets/images/icos2.png
image3: /blog-tech/assets/images/icos3.png
image4: /blog-tech/assets/images/icos4.png
image5: /blog-tech/assets/images/icos5.png
image6: /blog-tech/assets/images/icos6.png
image7: /blog-tech/assets/images/icos7.png
image8: /blog-tech/assets/images/icos8.png
image9: /blog-tech/assets/images/icos9.png
image10: /blog-tech/assets/images/icos10.png
image11: /blog-tech/assets/images/icos11.png
image12: /blog-tech/assets/images/icos12.png
image13: /blog-tech/assets/images/icos13.png
---


### Intro
I recently helped my customer successfully optimise their storage using IBM's storage solutions. During the process, we had over 40TB of data lifted off the baremetal servers, and onto ICOS (IBM Cloud Object Storage). The result was amazing! High availability, ease of access, resilience and of course reduction in costs. I have realised though that often organisations are too busy with operations that taking additional time to reconsider the current architecture may be difficult.  
The demonstration I did to help show the value of ICOS has been very helpful to the customer, so I decided to take a moment to document it here, I hope this helps for you too!

Quick definition on object storage:  
ICOS is IBM's Object Storage solution, and it is especially useful for storing unstructured data for archiving purposes. As this is a technical blog, I will keep explanation to minimum and get started with the demonstration.  
[About Object storage](https://www.ibm.com/cloud/object-storage)

Did you know? If you have an IBM Cloud account, you can provisiong Lite instances of ICOS for free!
In this demo you can try to get your own instance up and running, or just get a picture of how it looks in the portal when you use ICOS.

Firstly, go to the catalogue to find ICOS:  
![]( {{page.image1 | relative_url}})

Pick the Lite instance during order. Once it is provisioned, it will take you to the introduction page:  
![]( {{page.image2 | relative_url}})

If you navigate to the 'buckets' page, you will see the following page. You can do all your administration here. In the beginning you will have 0 buckets:  
![]( {{page.image3 | relative_url}})

Lets go and create a bucket. Click on the arrow for 'Customize your bucket' for full options:  
![]( {{page.image4 | relative_url}})

The bucket name will have to be unique across the whole ICOS system. It's a good practice to use multiple words separated by -.  
Pick the resiliency depending on storage requirements. Single Site is best if you have certain data that cannot leave a particular geography, but has no resilience.  
Regional has replication across Multi Zone Regions in the same location. Cross Region has best resiliency, with replication across geographies (it's good to understand your budget too!)  
![]( {{page.image5 | relative_url}})

There are several storage classes. Standard is best for high access workloads, and has no charges for data retrieval. Vault is in between and Cold vault is best for long term archiving, which is low cost but has charges for retrieval. Generally the long term archiving tiers would take longer to retrieve the data. Smart tier is a great tier that will automatically allocate data into the correct tier depending on frequency of access, and help reduce cost. One note is that a bucket cannot be changed to a different storage class, but you can create other buckets and move across data using command tools like rclone:
![]( {{page.image6 | relative_url}})

There are a few more options for the bucket, and once you have chosen the right configuration, your bucket is created! An additional setup I recommend is the service credentials. By adding service credentials you can access content in the bucket externally and securely.  
![]( {{page.image7 | relative_url}})

When creating new credentials, click Advanced options, and check Include HMAC Credential to be ON.  
![]( {{page.image8 | relative_url}})

Check the access key id and secret access key: 
![]( {{page.image9 | relative_url}})

You can use 3rd party tools like Cyberduck to securely connect to the ICOS bucket by entering the access key id and secret access key as follows. ICOS uses the same interface as Amazon S3, so you can select that when prompted the type of storage. For server, enter the endpoints as found [here](https://cloud.ibm.com/docs/cloud-object-storage?topic=cloud-object-storage-endpoints).  
![]( {{page.image10 | relative_url}})

I was able to connect to the bucket from Cyberduck. I can perform basic operations like adding file, retrieving etc.
![]( {{page.image11 | relative_url}})

Other useful features include the aspera high speed upload. You can do this if you are uploading large files from the portal. From the bucket after you click upload, select transfer type to be Aspera high speed upload, it will be blazingly fast! You will need to follow instructions and download the aspera client to use it.  
![]( {{page.image12 | relative_url}})

Another useful feature is rclone, which is a tool that you can use on the commandline to move data from a bucket to another bucket. Generally you cannot move objects between buckets, so features like this help when you need to move data around. This feature supports any Object storage not just IBM, so for example if you have object storage on other cloud vendors it is possible to move it to ICOS too:  
![]( {{page.image13 | relative_url}})

That's it for the demonstration!
There are more things to keep in mind including the following:  
* User permissions  
* Changing to the paid plan if you wish to convert to real workloads  
* Using API and commandline tools

I hope this served as a good intro to ICOS! :)  

### Reference and good reads/watch:

[Page to create object storage instance on IBM Cloud](https://cloud.ibm.com/objectstorage/create)

[IBM Cloud Object Storage webinar](https://www.youtube.com/watch?v=GtN5J05-c7Q&t=2896s)

[Access Management](https://www.youtube.com/watch?v=oLA10kqmpw8)

[Getting started with the IBM Cloud CLI](https://cloud.ibm.com/docs/cli?topic=cli-getting-started)
 
[Storing large objects with CLI](https://cloud.ibm.com/docs/cloud-object-storage/basics?topic=cloud-object-storage-large-objects)
 
[Using the AWS CLI:](https://cloud.ibm.com/docs/cloud-object-storage?topic=cloud-object-storage-aws-cli)
 
[IBM Cloud Object Storage CLI](https://cloud.ibm.com/docs/cloud-object-storage-cli-plugin?topic=cloud-object-storage-cli-plugin-ic-cos-cli&locale=en)
 
[IBM Cloud CLI Quick Reference (includes the slack communication channel at the bottom for questions)](https://cloud.ibm.com/media/docs/downloads/IBM%20Cloud%20CLI%20quick%20reference.pdf)