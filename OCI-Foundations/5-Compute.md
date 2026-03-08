# 5. Compute
## 5.1 Compute Introduction
### Transcript
Welcome to this module on OCI compute. Let's start with an introduction. So OCI Compute service provides you virtual machines and bare metal servers to meet your compute and application requirements. The three defining characteristics of this service include scalability, high performance, and lower pricing. In the next few slides, I will talk about each of these in a bit more detail.

So the first thing in the OCI Compute service is you have this notion of flexible shape. What does it mean? Well, it means you could choose your own course, your CPU processors. And you could also choose your own memory.

And as you can see the sliders here, you could choose a combination of CPU cores and memory. And there is a ratio there. But you have flexibility in choosing your own configuration.

Literally, there are thousands and thousands of configurations you can choose from. Now, what is the use of doing this? The use of doing this is could select the right machine type by using our flexible shapes. And in the cloud, there's this notion of t-shirt sizing.

So you have a small, medium, large kind of shapes. And your application has to fit those shapes. And either sometimes you overprovision or underprovision. And you have to go through that painful process of changing your machine types. We hope with these flexible shapes, you don't have to do that.

If you still want to use the traditional approach, we have virtual machines. We have bare metal servers. And we have dedicated host. And you could use either one of them or all of them.

Bare metal servers basically means you get a full machine, a full server, which is completely dedicated to you. Dedicated host basically means that you get a full, dedicated bare metal machine. But on top of that, you could run virtual machines.

What's the difference between dedicated host and VMs? Well, VMs, as you see in this slide here, are shared and multi-tenant, meaning the host can be running VMs from multiple customers. They have strong security isolation. So you don't have to worry about that.

But some customers want a dedicated host where they could run their own VMs. And they don't have VMs from any other customer running there. So that option is also provided by using dedicated host.

Not only this, but OCI is only one of the two cloud providers to provide you options on processors. So you can run AMD-based instances. You could run Intel-based instances. And you could also run ARM-based instances-- are really a powerful thing for mobile computing. The phones you are using today are probably running on ARM processors. Now, ARM is coming into the data centers.

So today, we are using Ampere Altra processor family. Ampere A1 instances are performed very well in many use cases. So as you can see on the screen here, we are using Nginx some price performance number. It's a good example of high-throughput workloads, like web servers, microservices, API gateways.

In ARM's testing of Nginx as a reverse proxy request per second, you can see here that Ampere A1, which is the processor we are using for ARM, had 32% better price performance than the equivalent AMD processor and 69% better performance than Intel processors. So this really talks about our industry-defining price performance capability, particularly with ARM processors.

And finally, on the pricing side, the service implements pay as you go pricing, we are 50% cheaper than any other cloud out there just to begin with. And not only that, you could use something like preemptible VMs to reduce your cost by more than 50% from your regular instances. Preemptible VMs are low-cost, short-lived VMs suited for batch jobs and fault-tolerant workloads.

These are similar to regular instances but priced 50% lower. So you can use them to reduce your cost further. So just to recap, very powerful service. The three defining characteristics we talked about-- this notion of scale, this notion of higher performance-- we saw an example of that-- and lower pricing provided by the compute service. I hope you found this lesson useful. Thanks for watching.
## 5.2 Instances Basics
### Transcript
Welcome to this lesson on instance basics. Let's look at some of the instance basics here. So when we say an instance, what we mean is a compute host. And it has several dependencies. So let's look at them.

So you have an Oracle Cloud region here. A region is comprised of multiple ADs. An AD is nothing but a data center, as you can see here. The first dependency the compute service has or compute hosts have is on Virtual Cloud Network. So in order to spin up a compute instance, you need a Virtual Cloud Network. As you can see here, you have a network divided into smaller portions called subnets. So you have a subnetwork here, and you need to create these before you can spin up a compute host.

Now you can spin up a compute host. It's a physical construct. Networking is a virtual construct. So how are they related? Within a compute host, you have a physical network interface card, and you virtualize that card. We virtualize that card-- give you this virtual NIC. And that virtual NIC is placed inside the subnet, as you can see here. And that's the association for the compute host. And that's where the private IP for the compute host comes from, because every compute host or VM you are running, or a bare metal machine, has a private IP address.

Now, there is another set of dependency the compute instances have, and that's to the boot volume and the boot disk and the block volumes. What do these mean? Well, each of these compute hosts you are spinning up has an operating system. And the image that's used to launch an instance determines its operating system and other software. So you have this concept of an image that comes from this network storage disk called a boot disk. So it doesn't stay on the compute host, it's actually living on the network somewhere.

And you also have data, like file systems, et cetera. You're working on the compute instances. They also live on the network. So there is the data disks and operating system disks together. There's a service called block volume service which the compute host uses to run its operating system and run its data disks. Now, these are remote storage, as you can see here. So just to recap, the compute control plane has dependency on the networking control plane and the block storage control plane.

There is one more feature which is really relevant when you are talking about compute instances, and that's live migration. We know that computers fail all the time. So how do we make sure that whatever compute host you are running is always up and running, itself? So we have this feature called live migrate. And the idea here is if one of the compute hosts goes down, there's a problem, we would migrate your VM to another host in our data center, and it will be transparent to you. There are multiple options you provide-- whether opt-in or opt-out-- you can choose from. But the idea is we migrate your virtual machines so you can live-migrate between hosts without rebooting. This keeps your applications running even during maintenance events. To achieve this in your own data centers is a not-so-trivial task, but we make that seamless within OCI.

So just to recap, in this lesson we looked at the basics of the control plane dependencies, and then we talked about live migration. I hope you found this lesson useful. Thanks for watching.
## 5.5 Scaling
### Transcript
Welcome to this lesson on scaling, a very important concept within Compute. So what is scaling? There are two kinds of scaling which is possible? One is called vertical scaling; one is called horizontal scaling. As the name signifies here, vertical scaling basically means, you are scaling up or scaling down instance shapes. Now, what can you scale? Well, you can scale the cores, You can scale memory. And some of the other characteristics scale accordingly.

The important thing to keep in mind here is, when you scale up or scale down, there is a downtime required because, likely, we take your machine, and we instantiate a new-- when you institute a new shape. It actually goes to another host. So there is some kind of downtime required. Keep that in mind when you do vertical scaling. There is another good practice here is, you stop your instance before you do any kind of vertical scaling.

There's another kind of scaling which is called Autoscaling, also referred to as horizontal scaling. Now, as you can see in the picture there, this basically means that you add more VMs of the same shape, or you take a bit more of the same shape. This enables large-scale deployment of VMs. There is scale-out, as you can see from the picture. You're going from one VM to four VMs. And there's also scaling. We are going from four VMs back to one VM. So both models support it.

Why is this so popular and powerful? The reason it is so powerful is, it gives you that scaling capability, but it also gives you that high availability. In this case, one virtual machine fails; others can still keep working, as you can see from the picture. And a thing which makes it really powerful is, you can match traffic demand by adding to removing VMs automatically.

So let's say you are operating a webstore. Suddenly you start getting more traffic. You could easily Autoscale. And you could add more VMs. The traffic goes down, you could take away those VMs. That's how it works. There is no extra cost for using Autoscaling.

So how does it work and in practice? There are three steps you have to follow to get Autoscaling. And it's super easy to do. First thing you do is, you have a running instance on which you want to do Autoscaling. So you create a template. And a template is called a config in OCI terminology. It's basically things like your operating system image, your metadata, the shape, the size, and some other characteristics, like storage, networking, et cetera.

So first you create a stamp. You have a running instance. You create a stamp of that running instance. The second step is you take that stamp, and then you create this thing called instance poo. And pool is basically a collection of those instances in advance. You create that.

And the idea here is, you can manage all of these instances as one unit. So you could stop all of them at the same time. You could start them, you could terminate them, and, to get high availability, you could put them in different availability domains on different data centers. So that's step number two.

And then step number three is, you take your instance pool, and then you write these Autoscaling rules on that. You start with a desired or initial size. There is a minimum size, and then there is a maximum size. And you write a rule. As you can see on the screen, if CPU or memory goes beyond a particular percentage threshold, add some instances. Or if it goes below some threshold, remove some instances. And Autoscaling is constantly monitoring your traffic. It's constantly monitoring your CPU usage. And it's looking at whether to add instances or remove instances.

So as you can see in this picture here, we started with an initial size of 2. And then, if the CPU goes beyond 70%, we have to add two more instances. And if it does, you have you end up with four instances. So Autoscaling not only helps you meet the traffic demand, but can also give you high availability. So that's a recap, a very powerful feature of Autoscaling. And then we also looked at another way of scaling, the vertical scaling. I hope you found this lesson useful. Thanks for watching.
## 5.6 Oracle Container Engine for Kubernetes (OKE)
### Transcript
Welcome to this lesson on Oracle Container Engine for Kubernetes also referred to as OKE. Let's get started. Before we dive deeper into OKE and look at all its details, first let's look at the difference between virtual machines and containers. Well, in case of virtual machines, we have an hypervisor like an ESXi and virtual machines running on top of the hypervisor.

Each virtual machine has its own operating system inside it, and then the libraries and the dependencies and the application. Now, in case of containers, we have a different a environment, so we have the underlying hardware, which is the same as in case of virtual machines, and then we have the operating system. And then we have what is referred to as a container runtime like Docker installed on the operating system.

Now this container runtime, in this case, Docker manages the containers that run with the libraries and the dependencies alone and of course, the application. But there is no operating system inside the containers. Now, why would we do that? What are the advantages?

Well, if you compare with virtual machines, in case of VMs, there is an extra overhead, which causes higher utilization of the underlying resources as there are multiple virtual machines running here, and there are multiple operating systems running here and they have their own kernels et cetera. So there is higher utilization here.

Now VMs also consume higher disk space as each VM is heavy and is usually gigabytes in size. They also take longer to boot up because every operating system has to boot up here. So those are some of the disadvantages with VMs, higher utilization bulkier, and take longer to boot up. In case of containers, because now we took out operating system from each of these containers here, they boot up faster because there is no operating system boot up time.

So they boot up usually in a matter of seconds compared to minutes for virtual machines, and there are also lightweight, usually megabytes in size because the whole operating system here can be heavy. So that's outside and so they are much faster to boot up and they are much more lightweight. So that's the advantage with containers, the smaller images et cetera.

The thing with containers is the main reason other than these advantages people use containers is because they are portable. So you can build your containers, you have a build file which goes with your image, and then you could deploy it anywhere. And the whole development and operations team can work in sync. And the portability really makes containers suitable for building Cloud native applications, microservices.

Once you create these containers, they need to have connectivity between them, they need to talk to each other. They also need to scale up or down based on the load. And there are several other things which these containers would need to do once you containerize your applications.

So how do you deploy them, manage them, connect them, scale them up and down? All this process of automatically deploying and managing containers is known as container orchestration. And Kubernetes is an open source system for automating deployment, scaling, and management of containerized applications.

So what are some of the advantages? Well, with using Kubernetes, you can run containerized applications of any scale with no downtime. You can self-heal applications, thereby providing resiliency. You can autoscale containerized applications, ensure optimal utilization, and then this whole orchestration simplifies deployment to a large extent.

So as you see here, you can use Docker to manage and build the containers. And then Kubernetes basically helps in orchestration, so containers can talk to each other, you can scale them up and down et cetera. Lots of advanced functionality you could do using a container orchestration system like Kubernetes.

So what is Container Engine for Kubernetes or Oracle Container Engine For Kubernetes, also referred to as OKE? Well, it's a fully managed, scalable, and highly available Kubernetes service. It's based on the open source Kubernetes system. It has a lot of features for developers, like one click cluster creation, CLI/API support, and then support for running these on Arm based and GPU based instances.

And it has a lot of DevOps advantages. There is autoscaling support, there is automatic Kubernetes cluster upgrades, there is self-healing cluster nodes. Some of the things core characteristics of Kubernetes, all those core characteristics, some I have listed here are supported in this managed environment.

So how does this work? Well, this is a very advanced topic. So I'm just going to cover it at a very high level. For more details, you should check out our other courses on DevOps and developer.

So the first thing is you start with nodes. A node is a machine on which Kubernetes is installed. They also refer to as worker node. Worker node is where containers are launched by Kubernetes. You see these worker nodes here, and we group them together and we create what is called as a node pool.

You also see this thing called pod here. A pod is a group of one or more containers with shared storage and network resources, and a specification file for how to run the containers inside the pod. So think about this as the smallest unit of compute within a managed Kubernetes environment. So now we have let's say this cluster here, and cluster of nodes and nodes have pods within them.

Now how do we manage the cluster? How do we schedule the containers? How do we manage high availability? And this is where the control plane comes into picture, the control plane nodes. And the control plane nodes basically manages the worker nodes and the pods in the cluster.

As you can see here, this control plane nodes is highly available and it's managed by Oracle, and the great thing is you don't really pay for this thing. The management is there is no charge for running the control plane nodes. Now the control plane component you see a lot of components here, kube-control manager, APIserver, etcd. Again, we're not going to cover all these in this foundational course.

But these components make decisions about the cluster, for example, how to schedule containers as well as detecting and responding to cluster events, scale up, scale down, resiliency, node failure, et cetera. Now you see a database like etcd, it's a key value store used for Kubernetes to back all the cluster data set stored here. And there are lots of other components and we have other courses where we go into a lot more detail than this here.

But this slide just gives you a quick overview of what is Oracle managed as far as OKE is concerned and what is customer managed here. The control plane nodes managed by us Oracle, and then customers can manage their own worker nodes where actually they are going to run their containerized application.

When creating a new cluster with OKE, you can specify the type of cluster to create. So there are two types of clusters. The first one is enhanced clusters. They support all available features and come with a financially backed Service Level Agreement SLA.

On the other hand, basic clusters support core functionality, but none of the enhanced features. They come with a service level objective SLO, but not a financially backed SLA like the enhanced cluster. So there are two clusters you can choose from.

Now, when you create a node pool for your Kubernetes cluster, you also have two options to create either a virtual node or a managed node. So think about virtual nodes as a serverless option. In here, the Kubernetes software is upgraded, security patches are applied while respecting application availability requirements, but it's done by Oracle. And you can only create virtual nodes and virtual node pools in enhanced clusters.

While on the other hand, the managed nodes, you are responsible for managing the nodes, and of course, you can configure them to meet your requirements. But you are also responsible for upgrading Kubernetes on managed nodes and for managing cluster capacity. And unlike virtual nodes, you can also create manage nodes in basic clusters as well as enhanced clusters.

So in summary, if you want a hands off serverless experience, you might prefer virtual nodes. On the other hand, if you need more control and flexibility and don't mind some extra management tasks, you might prefer managed nodes.

So this was just a quick overview of Oracle container engine for Kubernetes, also referred to as OKE. And in some of the other advanced courses we go into much more details. I hope you found this lesson useful. Thanks for your time.
## 5.7 Cointainer workloads in OCI
### Transcript
Hello and welcome. In this lesson, let us look at OCI Container Instances. So containers have become the favored method of packaging, deploying, and managing modern applications. Meet Alex. Alex wants to test his containerized application, but without deploying it on OK as the scale is not large. At the same time, the application he wants to containerize are running isolated web applications or RESTful APIs. He's looking for a simple, quick, and secure way to run containers without managing any servers.

When you want a simple way to run a containerized application without using Kubernetes, you can provision a virtual machine, install a container runtime, and run your applications on it, as is shown in the diagram here. However, this process still increases the operational complexity, as you need to manage the VMs and the servers, patch the operating system, and update the container runtime regularly. So what is the solution?

OCI has a capability called OCI Container Instances. And these container instances offer the quickest and most straightforward way to launch containers without the need to handle virtual machines or adopt more advanced services like OK. By eliminating the operational complexity, OCI Container Instances enable users to run containerized applications without having to manage any infrastructures. User only need to supply the container image for their applications and OCI takes care of the underlying container runtime and compute resources.

You can specify environment variables, resource limits, startup options, et cetera for each container. And you can even run multiple containers on one container instances. The containers are hosted on fully-managed compute infrastructure that is specifically designed for container workloads, providing robust workload isolation for enhanced security. So that's it. Think of container instances as a serverless offering where you can run containers without really worrying about the underlying infrastructure. I hope you found this lesson useful. Thanks for your time.
## 5.8 Serverless with Oracle Functions
### Transcript
Welcome to this module on Oracle Functions. Functions is a serverless offering. You might wonder, what is serverless. Let's look into it.

So as you look at the journey on one axis, if you plot abstractions and other axis you plot this control, and in sort of decreasing concern, it's sort of a journey where you start with a Bare Metal machine where you have the access to the full machine, then there is Virtual Machines where you take that big Bare Metal server and you divide it into smaller segments which could all be run independently of each other, so you have this VMs.

And then there is a movement towards Container, you took all the VMs were very heavy, they took a lot of time to boot up, they led to even to low resource utilization, and lots of other issues, they were not portable, et cetera.

So we took all that and then we created Containers, where you have a container runtime, the containers share the OS kernel, and they have a little bit weaker security isolation, but they have a good resource isolation in terms of CPU and memory.

So they could drive your overall resource utilization, and the same time they are portable, so they really help in DevOps adoption. You write once, you could deploy anywhere, right, and that's why containers became really powerful.

And then there is this journey towards Functions, where you really write your code in a particular runtime, and then you don't worry about servers, you don't worry about any of the infrastructure, you just provide the code and the cloud provider is responsible for executing that code.

And one of the greatest advantages here is it truly leads you to a consumption based pricing model where you are only billed for the time your function is running. So you go from pay-as-you-go pricing to a completely consumption-based pricing, and that's one of the reasons why Function's adoption is increasing day by day.

So let's look at Oracle Functions and what are the key characteristics of this particular service. So the first thing is its Function as a Service. So you write code and the code is executed. Some people also like to call it as Event Driven Architecture, so some kind of event happens when function is invoked.

In reality, the functions run inside a container. You are billed only for the duration the function runs and it's capable of highly parallel execution. Now one thing which is also relevant in Oracle's case is Oracle Functions is powered by the Fn Project Open Source engine.

So unlike some of the other cloud vendors out there, this particular service is built on the open source Fn engine, open source engine. And we talked about some of the things you see on the right-hand side, it's a truly consumption-based pricing model, the service is sort of autonomous, it scales, it's capable of highly parallel execution, and it's event driven. You invoke the function and the quadrants based on that invocation.

So how does it really work in reality? The process is really straightforward. Let me walk you through the process. At a high level, your uploaded code and configuration is packaged as a container image and stored in the OCI Registry. Then you set up trigger actions. You can invoke using CLI or API, or OCI events can trigger it. And then Oracle Functions then executes the code in response to the trigger or invocation, which can then invoke any number of other integrations with other OCI services or even external systems.

The thing which makes it really interesting is it's a truly consumption-based pricing model. You pay for code execution time only. The other time when the function is just sitting there and not being called, you pay nothing for that. And as I discussed, the Functions has invocation, it can be triggered either directly or through something like an OCI events, and then it has integration to other OCI Services.

Now this is a very simplified view. A lot of other details on how the service works. It's very powerful, a lot of advanced capabilities. Given it's a foundational course, this sort of helps you understand how Oracle Functions work.

And that's it, serverless. Next time somebody says serverless, there are server, remember, there are servers, they are running in the data center, but you don't care. You give us your code and the code is executed. Even though it's called serverless, there are always servers running in the data center. I hope you found this lesson useful. Thanks for watching.