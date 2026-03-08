# 2. OCI Introduction
## 3.1 OCI Architecture
### Transcript
Welcome to this lesson on OCI Architecture. In this lesson, we will cover the core constructs of OCI's physical architecture, starting with regions.

Region is a localized geographic area comprising of one or more availability domains. Availability domains are one or more fault-tolerant data centers located within a region but connected to each other by a low-latency, high-bandwidth network.

Fault domains is a grouping of hardware and infrastructure within an availability domain to provide anti-affinity. So think about these as logical data centers.

We looked at it in the previous lesson. Today, OCI has a massive geographic footprint around the world with multiple regions across the world. And we also have a multi-cloud partnership with Microsoft Azure. And we have a differentiated hybrid cloud offering called Dedicated Region Cloud@Customer.

But before we dive into the physical architecture, let us look at how do you choose a region. First thing is choosing a region, you choose a region closest to your users for lowest latency and highest performance. So that's a key criteria.

The second key criteria is data residency and compliance requirements. Many countries have strict data residency requirements, and you have to comply to them. And so you choose a region based on these compliance requirements.

The third key criteria is service availability. New cloud services are made available based on regional demand at times, regulatory compliance reasons, and resource availability, and several other factors. Keep these three criterias in mind when choosing a region.

So let's look at each of these in a little bit more detail. Availability domain. Availability domains are isolated from each other, fault-tolerant, and very unlikely to fail simultaneously.

Because availability domains do not share physical infrastructure, such as power, or cooling, or the internal network, a failure that impacts one availability domain is unlikely to impact the availability of others.

So as you can see in this graphic here, a particular region has three availability domains. One availability domain has some kind of an outage, it's not available, but the other two availability domains are still up and running.

We talked about fault domains a little bit earlier. What are fault domains? Think about each availability domain has three fault domains. So think about fault domains as logical data centers within availability domain. So as you can see in the picture here, we have three availability domains, and each of them has three fault domains.

So the idea is you put the resources in different fault domains, and they don't share single point of hardware failure, like physical servers, physical rack, top-of-rack switches, or power distribution units, you can get high availability by leveraging fault domains.

We also leverage fault domains for our own services. So, in any region, resources in at most one fault domain are being actively changed at any point in time.

This means that availability problems caused by change procedures are isolated at the fault domain level. And moreover, you can control the placement of your compute or database instances to fault domain at instance "launch" time. So you can specify which fault domain you want to use.

So what is the general guidance? The general guidance is we have these constructs like fault domains and availability domains to help you avoid single points of failure.

We do that on our own. So we make sure that the servers, the top-of-rack switch, all are redundant, so you don't have hardware failures, or we try to minimize those hardware failures as much as possible.

You need to do the same when you are designing your own architecture. So let's look at an example. You have a region. You have an availability domain.

And as we said, one AD has three fault domains, so you see those fault domains here. So first thing you do is when you create an application, you create this software-defined virtual network.

And then let's say it's a very simple application. You have an application tier. You have a database tier. So first thing you could do is you could run multiple copies of your application.

So you have an application tier, which is replicated across fault domains. And then you have a database, which is also replicated across fault domains.

Why do you do that? Well, it gives you that extra layer of redundancy. So something happens to a fault domain, your application is still up and running.

Now, to take it to the next step, you could replicate the same design in another availability domain. So you could have two copies of your application running, and you can have two copies of your database running.

Now, one thing which will come up is how do you make sure your data is synchronized between these copies? And so you could use various technologies like Oracle Data Guard to make sure that your primary and standby, the data is kept in sync here.

And so you can design your application, your architectures like these to avoid single points of failure. Even for regions where we have a single availability domain, you could still leverage fault domain construct to achieve high availability and avoid single points of failure.

Let's summarize what we learnt in this lesson. So we looked at region. Region comprises of availability domains. Availability domains comprise of fault domains.

So let's look at the inside-out view. So first, let's start with fault domain. Fault domain provide protection against failure within an availability domain.

Availability domain themselves provide protection from entire availability domain failures, particularly in the multi-AD region. And then you have this concept of region pair, where in every country we operate or most of the countries we operate, we have at least two data centers.

So you could use the second data center for disaster recovery or backup, or it also helps you to comply with data residency and compliance requirements. And then not only this, we also have SLAs on availability, management, and performance.

To recap, we looked at the physical architecture of OCI with regions, which are geolocations. We looked at availability domains. And then every availability domain has three fault domains.

So use these architectural constructs to design your applications which are highly available and avoid single points of failure. Thanks for watching.
## 3.2 Demo: OCI Console Walk-through
### Transcript
Hello, and welcome. In this demo, let us do a quick walkthrough of the OCI Console. So this is the OCI Console, and you can access it using this single URL, cloud.Oracle.com, and then you have to enter your tenancy name and your username and password. In the identity module, we will cover how to log in with your credentials to the Console. But here, let me do a quick walkthrough of the different features which the Console enables

So the first thing here is you can see this is the home page-- the dashboard-- some getting started links. There are some quick starts right here. And as you scroll down, you can see some launch-- you can launch some resources very quickly. Now, the one I want to-- area which I want to show you is the Service Navigation menu. Also, this icon here, the hamburger icon, you can access it using this hamburger icon.

So if you click on it, now you can see the various services categorized on the left-hand side here. So there is Compute, Storage, Networking, the core primitive Database, both Oracle and open-source, and several other services like Identity, Security, and Developer Services, et cetera. So these are the major categories of the services which we have available.

And then, if you click on, for example, Storage, you can access different storage services from this menu. So you can click on Object Storage, and there you can create object storage buckets and upload files. Now, at any point, if you are deep-- many layers deep into the individual services and you want to go back to the home page, you can click on the Oracle Cloud icon here, or you can click on the hamburger icon. So I can click on Oracle Cloud here, and now I'm back on my home page.

The second thing I want to show you here is around Search. So at any point, if you want to search for resources, you can just type the kind of resource you want to search for-- in this case, Compute-- and if I was running some compute instances, I would be seeing those on the left-hand side here. And on the right-hand side, you see Documentation, links to Marketplace, and links to some of the service menus.

I can also do something called an Advanced Resource Query. So, for example, if I want to see how many running instances I have in this account, I can-- there is a sample query, which we make available, and you can search here. And there are various queries you can write yourself. So that's the second thing I wanted to show you.

The third thing are the Regions. The Regions are the geographical locations where our data centers are located. So you can see my account-- my tenancy right now is subscribed to two regions in the United States. So Ashburn and Phoenix, and I can click on Manage Regions, and I can subscribe to any of the 41-plus regions which are available today.

So you can see the long list of regions here. And let's see, if I want to subscribe to another region in the US, like San José, I can just click on Subscribe here, and then I would be able to subscribe to this new region in San José. It's that simple.

At any point, because this is a global menu, you can switch regions. So I, right now, I'm in Ashburn. Suppose I want to create my resources in a different region like Phoenix. I can just do a global switch here, and now all my resources will be created in the Phoenix region. So that's the third thing.

The fourth thing is if you see this global menu on the top, there are announcements. Now, in the Cloud, we launch features and services at a very fast velocity. So how do you keep up with all the updates and announcements? And you can do so in Oracle Cloud's context using this announcement menu here.

So if I click here, you can see some announcements, which have come out in the last few months, scheduled maintenance, things like those. If I have to take any required actions, this is an area which gives me all that information.

The next icon here is around Help. Now, the console itself is designed in a way which is very user friendly, but if you need any help, whether it's around navigation or anything else, you can bring up this Help menu, and you have various options. Like you can visit the Support Center. You can actually create a Support Request. You can request a Limit Increase-- Service Limit Increase, et cetera. So it's designed to be a quick menu to give you the Help which you require.

Suppose this still doesn't-- still, you have questions, which doesn't get answered here, you can use this feature, which is the Live Chat Assistant. And what it does, this feature will assist you with any questions you might have here. So you can actually use this feature as well.

Another feature which is available here is around language. So you can change the console language from English to any other language of your choice, and there are various languages we support, as you can see here. So you can do that.

And then there are two Developer Services, which I really want to quickly talk about, which are around-- which is called Cloud Shell, one of them, and the other one is called Code Editor. The idea with Cloud Shell is we give you a small virtual machine running a bash shell, which you access to the OCI console.

And Cloud Shell comes with several preauthenticated utilities, like the CLI is installed there. Git is installed. Java is installed. Python is there. So the idea is if you are using the CLI, you don't have to do any local installation on your machine. Using this Cloud Shell, which is in the browser, you can run these commands very easily.

And the same is true with Code Editor. Code Editor basically gives a rich in-console editing environment that enables you to edit code and update service workflows and scripts without having to switch between the console and your local development environment. So this is a very convenient way to perform common code updates for various services, such as creating and deploying functions or Resource Manager Terraform scripts. So those could be done very seamlessly using Code Editor.

And then finally, if I go back to the home page, on the right-hand side, you can see some information like my tenancy name, and you can see your cost here. So you can see that I have a pay-as-you-go subscription. And out of the 31 days billing, my cost is around $20 right now.

And finally, if you want to see if any service is degraded or having any issues, you can click on this Health Dashboard, and this brings up all the services which we have in Oracle Cloud. And you can see the status of these services by different regions.

So hopefully, this gives you a good overview of the OCI Console and the various capabilities which are enabled through the console. I hope you found this demo useful. Thanks for your time.