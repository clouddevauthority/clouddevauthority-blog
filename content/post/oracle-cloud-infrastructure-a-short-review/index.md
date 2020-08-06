---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Oracle Cloud Infrastructure"
subtitle: "A short review of Oracle Cloud and a comparison with other cloud platforms."
summary: "I had a chance to play around with Oracle Cloud for an week while learning to obtain the Architect Associate certification.
I always wondered about the Tier-2 cloud platforms and as a cloud architect was naturally curious to know how they compare with Azure and AWS.
TLDR; It has a few bright sparks in IAAS and not surprisingly in Oracle DB offerings but overall not developer friendly and severely lagging behind what Azure and AWS offers today."
authors: [pratik]
tags: [oracle]
categories: [Technology]
date: 2020-08-06T11:37:34+10:00
lastmod: 2020-08-06T11:37:34+10:00
featured: false
draft: false
toc: true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Oracle cloud console"
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

It was quite by chance that I noticed on twitter feed that Oracle was providing free exam vouchers for OCI certification during the extraordinary Covid pandemic period in 2020.
This post is a short review of OCI and my opinion on Oracle Cloud borne out of preparing for that certification exam. 
We all know that as of 2020 AWS is the leading public cloud computing platform followed by Azure and GCP, but there are still a few Tier-2 players like Oracle, Alibaba, IBM, Digital Ocean etc. 
I always wanted to know what these Tier-2 platforms offer and how they compare with the leading platforms. 
Moreover as a cloud architect it is always wise to learn broadly and so when the chance came to get the certificate on OCI I jumped in. 

<!-- {{% toc %}} -->

## Oracle Cloud - Overview
The free exam vouchers gave me a motivation to learn a bit more about Oracle cloud and how it compares against Azure. 
Right about the same time it came in the news that the most widely talked about video conferencing app in the pandemic period, [Zoom video has chosen Oracle cloud](https://techcrunch.com/2020/04/28/in-surprise-choice-zoom-hitches-wagon-to-oracle-for-growing-infrastructure-needs/) to scale up during the pandemic. 
That was surprising and interested me even more to learn about Oracle cloud.

I did get some self-learning experience with Oracle cloud and eventually cleared the certification exams. 
My overall impression is that OCI has a few bright sparks in IAAS and not surprisingly in Oracle DB offerings but overall it is not developer friendly and severely lagging behind what Azure and AWS offers today.

A list of main service categories from the cloud console is shown below. 
The full list is available [here](https://docs.cloud.oracle.com/en-us/iaas/Content/services.htm)

{{< figure src="img/oci-services.png" alt="OCI Service category list" >}}

### The Free Tier
Oracle provides a US $300 credit to use within 30 days after signing up. After that it gives a decent set of always free tier eligible services.
- 2 virtual machines with 1/8 OCPU and 1 GB memory each (OCPU is one CPU core with Hyperthreading).
- 2 Autonomous Oracle DBs each with 1 OCPU and 20 GB storage.
- 2 Block Volumes, 100 GB total. 10 GB Object Storage. 10 GB Archive Storage.
- 1 Load Balancer instance, 10 Mbps bandwidth.
- 10 TB outbound data transfer per month.
- 1 million notifications sent through https per month, and some more sundries.

## Oracle Cloud - Certifications
<div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="3d8ead6a-02b9-449c-b899-dc76bf6604cf" data-share-badge-host="https://www.youracclaim.com"></div><script type="text/javascript" async src="//cdn.youracclaim.com/assets/utilities/embed.js"></script>
<div data-iframe-width="150" data-iframe-height="270" data-share-badge-id="fa041d94-fd7d-42a1-96f8-a26559a4c994" data-share-badge-host="https://www.youracclaim.com"></div><script type="text/javascript" async src="//cdn.youracclaim.com/assets/utilities/embed.js"></script>

I only wanted to learn the basics to get an overview of Oracle cloud, so I registered for the Foundations and Architect Associate exams. 
Oracle provides free training courses with video on demand lessons and practice exam. 
I also signed up for the OCI free trial offer to play around with and create services, deploy simple code and just to get a general hang of the platform. 
The foundations exam is quite easy for anyone with some experience in cloud computing and just doing the free course is enough. 
You don't even have to get any experience with the cloud console. It was quite easy to pass.

For the Architect associate exam I actually followed the demos in the lessons to create services using the cloud console and tried to understand how it works. 
I did some monkeying around and created random services, changed features, observed the behaviours etc. 
Every cloud is different but there are many common concepts as well. With about a week of preparation I sat the exam and cleared it. 
It was harder than the foundations with 60 questions and some questions were not covered by the video lessons.

## Oracle Cloud - Review
I didn't get to explore all the services in Oracle cloud but I did play around with the most important services. 
The below is an opinionated review of what I found after a week in Oracle cloud and from the certification study lessons. 
I did not get real world experience in Oracle cloud but given my long cloud architecture experience in Azure and some experience in AWS I believe I am qualified to make this review.

Corey Quinn has written a [nice article](https://www.lastweekinaws.com/blog/why-zoom-chose-oracle-cloud-over-aws-and-maybe-you-should-too/) on why he thinks Zoom chose Oracle, primarily the extraordinarily cheap data transfer cost and my view is the same as well.

Superficially it has the most common services a cloud platform must have like VMs, Virtual Network, Load Balancer, Block/File/Object Storage, Kubernetes cluster, Serverless functions, Eventing, Streaming, Database etc. 
But as always the devil is in the details.

### What I liked
- The [pricing model](https://www.oracle.com/cloud/price-list.html#data-integration-platform) is very simple compared to some of the convoluted calculations required in Azure and AWS.
- Pricing for services is the same in all Regions !!. This is a revelation to me.
- Their networking price is astonishingly cheap. There is no inter-AD (Ad ~ AZ) data transfer cost, no cost for NAT or VPN gateway.
- Serverless Database services on Exadata system makes it simple and flexible for shops running large Oracle instances to move to cloud.
- Provides 2 always free Oracle DBs with up to 20 GB storage. Easiest way to learn SQL or build apps and test against relational DBs (like using Entity Framework). Azure and AWS doesn't have any always free RDBMS services.
- Bare metal instances (not available in Azure).
- I liked that Compartments (~ Azure Resource Groups) can be nested and IAM policies applied at higher levels than can be inherited as a cool feature. Wish Azure had nested RGs.
- The concept of Tag namespaces to categorise tags, ability to set pre-defined list of values for tags and mark some tags as cost tracking.
- Oracle has chosen to use Terraform for provisioning with stack definition instead of yet another proprietary way.

### What I didn't like
- It is as the name says primarily an Infrastructure cloud platform. The PAAS and Serverless services are very basic and rudimentary at best.
- It is not developer friendly. Just building and deploying a cloud function was convoluted with having to create subnets, policies, container registry etc. and I still didn't manage to call a simple HTTP triggered function from outside using curl. Apparently it requires signing the request and I couldn't find a worked example of how to do it.
- Comparing services like for like, it is easily apparent how far behind in features OCI is compared to Azure, AWS and GCP. You cannot build sophisticated solutions like in other cloud platforms.
- The only DB options are Oracle and MySQL (although was not available in Melbourne region). There is also a Oracle NoSQL Database that I have no idea about.
- The always free tier is Ok with 2 Vms, 2 Oracle DBs but no free cloud functions. I would have thought it would be least expensive to give away free serverless function invocations.
- The VM images are super locked down. I couldn't get to serve a html page from Apache within a Ubuntu VM even after setting up Internet Gateway and firewall rules. Little did I know that there are iptables rules setup by default that block traffic and I don't have enough Linux knowledge to change those rules. For a beginner developer it would be very frustrating.
- The console logs out after about 30 mins of inactivity which I found very annoying.
- It is painful to use the CLI as all resources have to specified by an unique Id (OCID) which are humongous like *ocid1.instance.oc1.ap-melbourne-1.anwwkljr5sb2gwickzbwwdfmcuvjt2z2qul4thl5v5vgiw4xpjfxgsnvfm3a-*

## Conclusion
In my opinion Oracle cloud is suitable for primarily IAAS solutions especially if your workload heavily depends on massive Oracle DB instances. 
Big enterprise software like Peoplesoft, SAP etc. or even legacy applications that are built to on top of Oracle with heavy use of PL/SQL can definitely benefit from the Autonomous Exadata DBs. 
The Serverless Oracle DB on shared or dedicated Exadata system, that Oracle calls Autonomous Databases can be scaled vertically massively in both CPU and storage. 
The price for network traffic is very cheap and it is worthy of consideration if you are streaming a lot of data like Zoom. 
It also offers massive Bare metal machines with NVMe drives which you can choose to use if you have an use case for such workloads.

Another possibility is if your workloads have a dependency on Oracle DB then connect a OCI region with Azure using FastConnect & ExpressRoute dedicated network circuits to get the best of both clouds. 
Only certain OCI regions have this Azure interconnect capability. 
The compute and apps can run on Azure while the Oracle DBs runs on OCI.

It has some features that I wish Azure could borrow like nested Resource Groups, Tag namespaces and always free RDBMS service.

Apart from that I didn't find OCI a developer friendly cloud and even though it has comparable services by name, feature against feature it is lagging behind Azure or AWS by about 5-8 years. 
Basic things like autoscaling VMs and adding them to a Load Balancer is not possible. 
The cloud console experience is very basic, it doesn't even show a dashboard of your running services when first logging in and there is no way to create one. 
The cloud shell is very basic, with no built in editor and no way to upload or download files. 
In short Oracle requires massive investment and time to even catchup with Azure or AWS and by that time those platforms will be miles ahead.