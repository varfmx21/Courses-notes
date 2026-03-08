# 4. Networking
## 4.1 VCN Introduction
### Transcript
Welcome to this module on OCI networking. Let's start with an introduction. So what is a Virtual Cloud Network? At its core, it's a private software defined network you create in Oracle Cloud. It's used for secure communication. Whether instances talking to each other, instances talking to on-premises environments, or instances talking to other instances in different regions, you would use Virtual Cloud Network.

It lives in an OCI region. Like we said, it's a regional service. It's highly available, massively scalable, and secure. And we take care of these things for you. So before we dive deep into the VCN and all the characteristics and all the features it has, let's look at some of the basic stuff.

So the first thing is VCN has an address space. In this case, you see this address space is denoted in a CIDR notation. CIDR stands for classless interdomain routing. This is a foundation score. So we're not getting into the details of how you create these CIDR notations. But you can read up more on the web. Or you could pull up a subnet calculator, and you can get all the details.

So you can see here, the VCN has an IP addressing range. And what that means is you have an address range. You take that range. And you can break it down into smaller networks which are called subnetworks. And these subnetworks are where you would instantiate your compute instances.

So in this example as you can see, the 10.0.0.0/16 network is broken down into 256 smaller networks, a couple of which are shown on the screen-- the public subnet 10.0.1.0/24 and the private subnet. And as I said, your instances get spun up in these subnets.

So if you spin up a web instance, it gets an IP address as shown. If you spin up a DB instance, you get an IP address-- private IP address as shown. And this IP address is used for all communication going forward. So talking about communication, what different mechanisms exist inside a VCN? So first, there is a notion of internet gateway. This is a gateway which is massively scalable, highly available, and is used for communication to anything on the internet.

So if you have a web server which wants to talk to other websites on the web being able to be accessed publicly, you would use an internet gateway. So going to the internet and coming back from the internet. You also have this highly available, massively scalable router called NAT gateway.

And it is used for providing NAT as a service. So what this means is the traffic is unidirectional. It can go from your private subnets to the internet. But users from the internet cannot use the NAT gateway to reach your instances running in a private subnet. So the idea with the NAT gateway is to enable outbound communication to the internet, but block inbound communications or connections initiated from the internet.

Then we have another router which is called Service Gateway. And the idea is it lets resources in VCN access public OCI services such as object storage, but without using an internet or NAT gateway. So these are the three scenarios-- Internet gateway for internet, NAT gateway also for internet but unidirectional, and Service gateway for accessing OCI public services, which are available on the internet but accessing them in a secure manner.

And then the other construct is called Dynamic routing gateway. This is a virtual router that provides a path for private traffic between your VCN and destinations other than the internet. So what can these destinations be? Well, this can be your on-premises environment.

Just to recap, VCN-- your software defined networking, highly scalable, secure, highly available. And you have various mechanisms, various routers to enable the communication, whether it's going to the internet or it's going to your on-premises environment. Thanks for watching.
## 4.3 VCN Routing
### Transcript
Welcome back to this lesson on OCI routing. As you can see from this graphic here, we have this concept of a route table. VCN uses route tables to send traffic out of the VCN to the internet, to on-premises networks, or to peered VCN, and we look at each of these scenarios.

Route tables consist of a set of route rules. Each rule specifies a destination CIDR block and a route target. Think about route target as the next hop for the traffic that matches that destination CIDR block.

Now, one thing to keep in mind is traffic within the VCN subnet is automatically handled by the VCN local routing. So you see a public subnet and a private subnet here. There is no routing needed for routing the data. There's no entry in a route table needed for routing that data between the public subnet and the private subnet. That's taken care by VCN itself.

So how does this work in reality? As you can see here, I have a private subnet and a public subnet and I'm showing you the route table only for the private subnet just for illustration purposes. And as you can see here, there are two kinds of data movement happening from the private subnet.

We are leveraging the NAT gateway. Probably there is a database running here, so you're using a NAT gateway to go and get some patches from the internet. So you can see that green arrow going all the way from the NAT gateway to the internet.

And then the second part is you are using a Dynamic Routing Gateway. That's kind of a virtual router you use for on-premises communication, and it's going through on-premises environment. Maybe you are running a DNS server on premises where the database needs to get its DNS resolved.

Now, if you look at the route table entries, we have two entries there. There's a CIDR notation, decision CIDR, and there's a route target. The first one says 0.0.0.0/0 and goes to NAT gateway. The second one has a CIDR block for on-premises network.

So how does this work in reality? Well, what happens is the route table looks at both the routes and the route which is more specific or gets priority. We also sometimes refer to as the longest prefix match. So if you look at these two CIDR blocks, the /16 is bigger or more specific than /0, so that takes priority.

So first, the traffic goes through the Dynamic Routing Gateway to your on-premises environment, your DNS servers. And then the traffic which is not destined for your on-premises environment goes to the internet through the NAT gateway, and hopefully to get a patch in this example. So this is a very quick illustration, but hopefully it shows you how the route table works.

Now, there's also one scenario we haven't talked about earlier which is peering. If you have multiple networks, how do they talk to each other? So there are two scenarios which are possible here.

If the networks are within the same OCI region, they can talk to each other through a mechanism called local peering. And you can see here we have this concept of a local peering gateway. That's kind of a virtual router which lets you manage that communication.

If the two networks are in two different OCI data center regions, then you have the same concept, a similar concept, but it's a remote peering now. And instead of using local peering, now you're using the Dynamic Routing Gateways. Remember we talked about Dynamic Routing Gateways used for on-premises communication, anything which is not for internet. So this is also a use case for Dynamic Routing Gateway enabling communication between networks in different regions.

Now, one thing you might look at that picture and say this is great if there are two networks talking to each other within a region. Pretty straightforward to use something like a local peering gateway. What happens if you have let's say, 10 of those VCNs? Or God forbid, if you have 300 of those VCNs, how are you going to communicate?

In a real complex environment, this is a possibility. This is a reality. Many customers struggle with a lot of networks. And so how does that communication happen in case you have large number of networks?

So in this case, what we have done is we have launched a newer version of DRG. It's called DRG v2. And what it does is you no longer need to maintain point-to-point connectivity using a local peering gateway, instead the VCNs can communicate using DRG. And this feature also lets you scale up to 300 VCNs on a single DRG. If this option is not enough, you can always connect an extra DRG through a remote peering connection. So the idea is to simplify and scale this experience using this DRG v2.

So to wrap up, in this section, we looked at OCI routing and how VCN uses route tables so to send traffic out to the VCN, to the internet, to on-premises network, or to a peered VCN. Thanks for watching.
## 4.4 VCN Security
### Transcript
So within VCN, you have this concept of security list. Think about security list as firewall rules associated with a subnet and applied to all instances inside the subnet. So what does it look like? The security list consists of rules that specify the type of traffic allowed in or out of the subnet. This applies to a given instance, whether it is talking with another instance in the VCN or a host outside the VCN.

And you can see a couple of entries here. These rules can be stateful or stateless. Stateful means that if traffic is allowed in a particular port, allowed in, it is always allowed out from that port, and vice versa.

So you can see here a couple of examples. Traffic is coming in at port 80, and the traffic is coming in from anywhere on the web. So that's 0.0.0.0/0. That's the source. Can be anywhere. Protocol is TCP. And it's coming at port 80. That's web traffic.

And the second rule says the traffic is going from the first subnet to the second subnet. So you see the source is the IP, the CIDR block for the first subnet, and it's actually the egress traffic. So it's the source for the second subnet, the private subnet. And the traffic is going on port 1521. That's Oracle database port.

And you can see, similarly for the private subnet, you have their own firewall rules. And in this case, it's saying that because it's a private subnet, you don't want any kind of web traffic. So the only rule here is the traffic coming from the public subnet, from the web server, so that the source CIDR is 10.0.1.0/24 and the port is 1521, right? So this is how you would define security lists within an OCI VCN service.

Now, there's also another concept, which is called network security groups, or NSG. These are very similar construct as security list, but the key difference is these apply only to a set of virtual network interface cards in a single VCN. And another big difference here is NSGs can be the source or destination in the rules. Contrast this with the security list rules where you specify a CIDR, only a CIDR, as the source or destination.

So as you can see here in this example, the egress traffic, the source is NSG B. So that's the NSG which is attached to my database. Similarly for the second network security group, you can see that the source is the first network security group. That's NSG A.

Also one thing to keep in mind-- that as you leverage network security groups, because they apply to individual VNICs, now you could have two instances in a single subnet, and they can have different security constructs. So one can have NSG with different kind of rules, and the other instance, you can see, has an NSG-- in this case, we say NSG C. It has different sets of rule. Right? So you could have that kind of scenario enabled by using network security groups.

So that's it. Just to recap, there are two mechanisms to create these firewall rules in OCI VCN. One is a security list, and the other is network security groups. Thanks for watching.
## 4.5 Load Balancer
### Transcript
Welcome back to this lesson on OCI Load Balancer service. Let me just quickly talk about why you would use Load Balancer. You would use Load Balancer to achieve high availability and also achieve scalability.

So typically the way Load Balancer works is, they're also referred to as Reverse Proxies, you would have a Load Balancer, which would be used access by multiple clients, various clients. And these clients would hit the Load Balancer, and the Load Balancer would proxy that traffic to the various backend servers. So in this way, it not only protects the various backend servers, but also provides high availability. In case a particular backend server is not available, the application can still be up and running. And then it also provides scalability because if lots of clients start hitting the Load Balancer, you could easily add more backends or more backend servers.

And there are several other advanced capabilities like SSL termination and SSL passthrough and a lot of other advanced features. We're not getting to those because it's a foundational course. But hopefully that gives you a good idea of what a Load Balancer does-- I mean, benefits of using a Load Balancer.

So the first type of Load Balancer we have in OCI is a layer 7 Load Balancer. Layer 7 basically means it understands HTTP and HTTPS. That's the OSI model. And then there are various capabilities available here.

So the first thing is the Load Balancer comes in two different shapes. One is called a flexible shape where you define the minimum and the maximum and you define the range. And your Load Balancer can achieve any kind of-- support any kind of traffic in that particular range, going from 10 Mbps all the way to 8 Gbps.

The second kind of shape is called dynamic where you predefine the shapes. So you have micro, small, medium, large, and you predefine the shape. And you don't have to warm up your Load Balancer. If the traffic comes to that particular shape, the Load Balancer automatically scales.

You can always do a public and a private Load Balancer. Public means Load Balancer is available on the web. Private means your multiple tiers, like a web tier, can talk to your database tier and balance the traffic between them, but both tiers don't have to be public.

A Load Balancer is highly available, highly scalable by design, and it has lots of advanced features layer 7. Things like Content-Based Routing are supported. And there's lots of other SSL features, other capabilities, which this is being a foundational course, we're not getting into those. But has lots of rich features.

The second kind of Load Balancer we have in OCI is called the Network Load Balancer. And as the name specify, Network Load Balancer operates at layer 4, layer 3, and layer 4 so it understands TCP, UDP, also supports ICMP. Again, like HTTP Load Balancer, it has both public and a private option, so you could create a public Network Load Balancer or a private Network Load Balancer. It's highly available, highly scalable, all those features are supported.

Now, why would you use Network Load Balancer or a HTTP Load Balancer? The primary reason you would use it is it's much faster than HTTP Load Balancer. It has much lower latency. So if performance is a key criteria for you, go with Network Load Balancer.

On the contrary, the HTTP Load Balancer has higher level intelligence because it can look at the packets, it can inspect the packets, and it gets that intelligence. So if you're looking for that kind of routing intelligence, then go with HTTP Load Balancer.

So just to recap, OCI provides you both layer 3 and layer 4 Network Load Balancer as well as layer 7 HTTP Load Balancer with lots of advanced features. Thanks for watching.
## 4.6 Demo: Load Balancing
### Transcript
Welcome to this demo on OCI load balancer. In this particular demo, this is the scenario or the topology we are going to use. So you see a VCN here with two subnets, a public subnet and a private subnet, and two web servers. And these web servers are instantiated inside the private subnet, meaning they don't have public IP address. And that's OK because the load balancer is in the public subnet. And these web servers act as backends to the load balancer.

So this is the setup we are going to run for this demo. So let's get started. The first thing we need to do is to create a Virtual Cloud Network. So I'll click on Networking, click on Virtual cloud network, and bring up the VCN wizard to create the Virtual Cloud Network. So I can see there are no networks here. And I'm in the sandbox compartment.

So click on Start VCN Wizard. And I'm going to use this particular setup, VCN with internet connectivity. So click on Start VCN Wizard. Let's provide a name for the VCN. So let's say this is my load balancer VCN. And sandbox compartment is fine. And it's giving me a CIDR block for the VCN and the subnets. I'm OK with these CIDR blocks. And I'll go hit Next and click Create.

And now my VCN will get created. Now, one thing, if you recall from the diagram, we need to do is to modify the security list because we need to add a rule in the security list which will allow traffic on port 80 because that's where the web servers are running on those compute instances. So I'll come here. And then I'll hit Security Lists for this one. And the default security list is the one which is used with the public subnet. So I'll click on Default Security List here.

And you can see it has these ingress rules right now. So there's traffic on port 22, which is allowed, and there are a couple of ICMP traffic rules which are there. So I'll click on Add Ingress Rule. And I'll say for the source I have acquired 0 IP address, meaning traffic coming from all networks, all IP addresses. And the destination port is port 80. So click that. And then I'll add this ingress rule. So now we have modified the security list to allow traffic to come to port 80.

So the next step for us is to go ahead and create a couple of compute instances, web servers, where we will install Apache. And these will act as backends to the load balancer. So I'll click on the navigation menu and click on Compute. And I'll go ahead and instantiate a couple of instances, which will act as the backend for the load balancer.

So it gives me a default name. I'll say this is my web server 1. Sandbox compartment is fine. OK with all the availability domains, all these options. Image and shape look OK. And right here, under Networking, it picks up the load balancer VCN we just created. But instead of putting this in a public subnet, we are going to choose Private subnet. And remember, this will ensure that these web servers don't get a public IPv4 address. And we are also not going to SSH into these machines. So we'll say No SSH is fine here.

And then right below, under advanced options, we have an option to provide a startup script. So we'll just put the startup script here. And the startup script is pretty straightforward. It's a bash script. It's basically installing Apache. And it's saying that it's changing the home page, saying that I'm web server 1 or something. And you can read more on what startup scripts do. So I'll click Create here with these options. And my instance will get created.

As the first instance is getting created, let's go ahead and create another instance, which will be my web server 2. So I'll click on Create Instance. And we'll call this web server 2. All the default options look good. For networking, we will again choose a private subnet. And basically, this will mean that-- let me just-- all right.

So private subnet, it will ensure that they don't get a public IPv4 address. Click No SSH. And right here, like web server 1, we'll provide a startup script. But this time, we will change this to say web server 2. Just making sure all the options look good. It's still private subnet here, load balancer. And web server 2 is fine. So hit Create.

And this will take literally a few seconds, 20, 25 seconds. And both my web servers will be up and running. And as soon as the web servers are up and running, we'll go ahead and provision a load balancer and put these web servers as backend to the load balancer. So if I click Instance here, I can see that the web servers are-- one web server is already running. And the second web server is getting provisioned.

So as this is happening, let's go ahead and click on Networking. And click on Load balancer here. And hopefully, by the time we hit creating the load balancer, those web servers are up and running. So you can see here, there are no load balancers. So I can click on Create load balancer. And it gives me option to create a layer 4 load balancer, also referred to as network load balancer, or a layer 7 load balancer. So I'm OK with creating a layer 7 load balancer. So click on that. And click on Create load balancer.

And here, it's a workflow which again is quite simple. It just walks you through the steps required to create a load balancer. So we're interested in creating a public load balancer. We'll have an ephemeral IP address under the bandwidth. Just choose the default options, which are provided here. And for the network, it's important. Now we pick the public subnet because the load balancer is actually instantiated in the public subnet. So this looks fine. Click Next.

And for the load balancer algorithm, there are multiple options. So there is weighted round robin, there is IP hash, and least connections. In our case, we will choose weighted round robin. And basically, what this means is the policy distributes incoming traffic sequentially to each server in a backend set list.

So right here is the place where we add the backends. And click on Add backends. And here, you can see both web server 1 and web server 2 are running. So I'll just click them and add them as backends. And that's it. My backends are added.

And if you scroll down, all these default values, I'm just going to leave them as is. So basically, this is saying that we are performing some health check to confirm the availability of backend servers. And the health check is performed using HTTP protocol at port 80. That's where my web server is running. So all this looks good. Click Next.

And the last step is to configure a listener. Listener is a logical entity that checks for incoming traffic on the load balancer's public IP address because we are running a web server. So we are going to use HTTP. And we are going to use port 80. So that's the value we are going to use. And we're going to-- it's a basic demo, so we are going to disable any kind of logging here. And I'll hit Submit.

And literally, again, this will take less than a minute. And the load balancer will be up and running. And once the load balancer is up and running, we'll test it. And one thing to note would be right now, you see the backend set health as pending because it is instantiating the load balancer. It's bringing the backend. Once all the setup is complete, you will see that this status will change from pending to OK. And the color will change to green.

So let me hit pause here, give it a couple of minutes or less than a minute and come back, and the load balancer will be up and running. And as you can see here, it took literally 30 seconds or so. And the load balancer is up and running. And now, the backend set health has also turned green. It says OK. And I can pick this public IP address and paste it in my browser window and bring up the backend sets-- the backends we just provisioned.

So it says connection is not secure. Of course, we did HTTP. And right here, you can see it says-- let me zoom in a little bit more. You can see it says Hello World! My name is web server 2. If I refresh the browser again, it says web server 1, web server 2, web server 1, web server 2. So this is weighted round robin in action.

And you can get a lot of information about the load balancer, all the metrics, the backend set, health check, et cetera. There's a lot of advanced functionality there. So this is how simple it is to create a load balancer. We created one with two backend sets. It's quite straightforward process. So hope you found this demo useful. Thanks for watching.