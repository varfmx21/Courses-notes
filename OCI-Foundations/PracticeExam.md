1. In Oracle Cloud Infrastructure, which component is responsible for controlling traffic between subnets within a virtual cloud network (VCN)?

   - Security Lists
   - Route Tables
   - Internet Gateways
   - Network Security Groups

   > **Respuesta:**

---

2. Which security feature prevents users from making risky or non-compliant changes to OCI resources?

   - OCI Cloud Guard
   - OCI Object Storage Lifecycle Policy
   - OCI Security Zones
   - OCI Load Balancer

   > **Answer: OCI Security Zones.** OCI Security Zones is the service designed to enforce security policies and prevent users from making risky or non-compliant changes. When you assign a compartment to a security zone, it applies a set of strict security policies (or "recipes"). Any attempt to create or modify resources in a way that violates these policies—such as making a storage bucket public or disabling encryption—is automatically denied.

---

3. Which is a key characteristic of an Oracle Cloud Infrastructure Block Volume?

   - It is automatically replicated within an availability domain for high durability.
   - It is used to store and manage object data.
   - It is a shared file system designed for high performance.
   - It is ephemeral and deleted when the associated instance is terminated.

   > **Answer: It is automatically replicated within an availability domain for high durability.** Oracle Cloud Infrastructure (OCI) Block Volumes are designed to provide highly durable and persistent block storage. To protect data from hardware failures, OCI automatically replicates Block Volumes across multiple storage servers within the same Availability Domain.

---

4. Which statement best describes Autoscaling for OCI Compute?

   - Autoscaling requires that you create only one VM in your deployment.
   - Autoscaling supports only scaling down resources, not scaling up.
   - Autoscaling automatically adjusts the number of running instances based on defined metrics.
   - Autoscaling forces you to stop all instances before resizing them.

   > **Respuesta:**

---

5. What is the primary purpose of setting up budgets in Oracle Cloud Infrastructure?

   - To set up billing accounts for OCI customers
   - To allocate resources across compartments
   - To automatically pause OCI services when spending reaches a certain threshold
   - To monitor and control spending on OCI services

   > **Respuesta:**

---

6. Which Oracle Cloud Infrastructure (OCI) offering allows you to run cloud services in your own data center while maintaining regulatory compliance?

   - MySQL HeatWave Database Service
   - Oracle Database Service for Azure
   - Oracle Database@Azure
   - OCI Dedicated Region

   > **Respuesta:**

---

7. What is the primary goal of distributing resources across multiple availability domains in Oracle Cloud Infrastructure?

   - To segregate resources based on project or department
   - To reduce latency for users in different geographic locations
   - To increase storage capacity for a region
   - To improve fault tolerance and high availability

   > **Answer: To improve fault tolerance and high availability.** In Oracle Cloud Infrastructure (OCI), Availability Domains (ADs) are isolated, fault-tolerant data centers located within a single geographic region. They do not share physical infrastructure like power or cooling. By distributing your resources (such as compute instances) across multiple Availability Domains, you ensure that if one AD experiences a localized failure or an outage, your application can continue running from the other ADs, thereby providing high availability and minimizing downtime.

---

8. Which type of Oracle Cloud Infrastructure networking gateway allows access to Oracle services within the same region without traversing the public internet?

   - NAT Gateway
   - Dynamic Routing Gateway
   - Service Gateway
   - Internet Gateway

   > **Answer: Service Gateway.** In Oracle Cloud Infrastructure (OCI), a Service Gateway enables resources within your Virtual Cloud Network (VCN) to access public OCI services (such as Object Storage) securely, without the traffic ever traversing the public internet.

---

9. In Oracle Cloud Infrastructure, which component of an IAM policy statement defines the user or group the policy applies to?

   - Action
   - Resource
   - Principal
   - Effect

   > **Answer: Principal.** In Oracle Cloud Infrastructure (OCI) Identity and Access Management (IAM), the Principal component of a policy statement specifies the entity—such as a user, group, dynamic group, or service—that the policy applies to and grants permissions to.

---

11. Which Oracle Cloud Infrastructure service is not designed for use with multiple cloud providers?

    - Oracle Database@Azure
    - Oracle Roving Edge Infrastructure
    - Oracle Interconnect for Azure
    - MySQL HeatWave Database Service

    > **Answer: Oracle Roving Edge Infrastructure.** Oracle Roving Edge Infrastructure is a hybrid cloud and edge computing solution designed to extend Oracle Cloud Infrastructure (OCI) services to remote, disconnected, or harsh edge locations via ruggedized devices. It serves as a direct extension of a customer's OCI tenancy rather than a service built to integrate multiple cloud providers.

---

12. What is the primary function of a Route Table in Oracle Cloud Infrastructure Networking Service?

    - To define rules controlling traffic flow between subnets
    - To define rules to route traffic from subnets to destinations outside the VCN
    - To connect a VCN to the public internet
    - To provide a private connection between a VCN and an on-premises network

    > **Respuesta:**

---

13. What is the main benefit of using Oracle Cloud Infrastructure Security Zones for resource management?

    - Managing IAM policies
    - Load balancing across regions
    - Enforcing best practice security configurations
    - Reducing network latency

    > **Answer: Enforcing best practice security configurations.** The main benefit of using Oracle Cloud Infrastructure (OCI) Security Zones is that they actively enforce strict security policies and best practices within specific compartments. Once a compartment is designated as a Security Zone, any attempt to create or manage resources in a way that violates Oracle's maximum security architecture—such as creating a public storage bucket or disabling encryption—is automatically prevented.

---

14. Which is NOT a component of an IAM policy statement in Oracle Cloud Infrastructure?

    - Encryption
    - Resource-type
    - Action Verb
    - Location

    > **Answer: Encryption.** In Oracle Cloud Infrastructure (OCI), Identity and Access Management (IAM) policy statements follow a specific syntax: Allow <subject> to <verb> <resource-type> in <location> where <conditions>. Therefore, Encryption is NOT a component of an IAM policy statement.

---

15. Which Oracle Cloud Infrastructure service continuously monitors your cloud resources and configurations to detect, assess, and remediate security risks?

    - Vault Service
    - Security Advisor
    - Cloud Guard
    - Security Zones

    > **Respuesta:**

---

16. Which Oracle Cloud Infrastructure service is designed to protect your web applications from various types of malicious attacks, such as SQL injection and cross-site scripting?

    - Cloud Guard
    - Web Application Firewall (WAF)
    - Vault Service
    - Security Zones

    > **Answer: Web Application Firewall (WAF).** In Oracle Cloud Infrastructure (OCI), the Web Application Firewall (WAF) is a security service specifically designed to monitor, filter, and protect web applications from malicious and unwanted internet traffic. It provides built-in protection capabilities to detect and block common vulnerabilities, including SQL injection (SQLi) and cross-site scripting (XSS), as outlined by OWASP standards.

---

17. How does Oracle Cloud Infrastructure's Bring Your Own License (BYOL) feature help customers save on costs?

    - By providing discounts on new software licenses purchased for OCI
    - By offering free software licenses for certain OCI services
    - By bundling software licenses with OCI services at a discounted rate
    - By allowing customers to use existing software licenses in OCI

    > **Answer: By allowing customers to use existing software licenses in OCI.** Oracle Cloud Infrastructure's Bring Your Own License (BYOL) feature enables customers to leverage their existing on-premises software licenses (such as Oracle Database or WebLogic) and apply them to OCI deployments.

---

18. Which type of load balancing policy is supported by Oracle Cloud Infrastructure Load Balancer?

    - Weighted Round Robin
    - Name Hash
    - Random
    - Most connections

    > **Answer: Weighted Round Robin.** Oracle Cloud Infrastructure (OCI) Load Balancer supports the Weighted Round Robin policy. This policy distributes incoming network traffic sequentially across backend servers based on a designated weight. Servers assigned a higher weight receive a proportionally larger share of the traffic, which is highly useful when backend servers have different processing capacities.

---

19. Which tool in Oracle Cloud Infrastructure allows you to visualize and analyze your cloud usage and spending patterns over time?

    - Budgets
    - Quotas
    - Usage Reports
    - Cost Analysis

    > **Answer: Cost Analysis.** In Oracle Cloud Infrastructure (OCI), the Cost Analysis tool provides an easy-to-use visualization dashboard that allows you to track, analyze, and optimize your cloud spending over time. It lets you view cost breakdowns by specific dates, tags, compartments, and services, making it easy to identify spending patterns and spot which resources are incurring the most costs.

---

20. In the Oracle Cloud Infrastructure Object Storage service, which storage tier is designed for rarely or seldom accessed data that can be restored within hours?

    - One Zone-Infrequent Access
    - Intelligent Tiering
    - Standard Storage
    - Archive Storage

    > **Answer: Archive Storage.** In the Oracle Cloud Infrastructure (OCI) Object Storage service, the Archive Storage tier is designed for data that is rarely or seldom accessed, such as long-term backups or compliance records. Because it serves as "cold" storage, the data is kept offline. When you need to access this data, you must submit a restore request, and the restoration process takes up to an hour before the data can be downloaded (restored within hours).

---

21. In the Oracle Cloud Infrastructure Block Volume service, which feature enables you to increase the size of a block volume without any downtime?

    - Volume Elasticity
    - Online Resizing
    - Volume Bursting
    - Dynamic Volume Resizing

    > **Answer: Online Resizing.** In the Oracle Cloud Infrastructure (OCI) Block Volume service, the Online Resizing feature allows you to expand the size of existing block and boot volumes dynamically without having to detach the volume from the instance. This enables you to increase storage capacity seamlessly on the fly with no downtime and without affecting your running applications.

---

22. Which data transfer type is generally free of charge in Oracle Cloud Infrastructure?

    - Egress data transfer to AWS or GCP
    - Egress data transfer to the Internet
    - Ingress data transfer
    - Egress data transfer to a different OCI region

    > **Answer: Ingress data transfer.** In Oracle Cloud Infrastructure (OCI), ingress data transfer—which is data being transferred into your OCI environment from the internet or other external sources—is always free of charge.

---

23. What is the main advantage of vertical scaling in the Oracle Cloud Infrastructure Compute service?

    - Increased fault tolerance
    - Enhanced performance with more OCPUs and memory
    - Reduced network latency
    - Improved load balancing

    > **Answer: Enhanced performance with more OCPUs and memory.** In the Oracle Cloud Infrastructure (OCI) Compute service, vertical scaling (also known as "scaling up" or "scaling down") involves changing the shape of an existing compute instance to increase or decrease its core count (OCPUs) and memory. The main advantage of vertical scaling is that it directly provides enhanced computing power and performance for an application without needing to change the architecture or add more instances.

---

24. Which statement about compartments in Oracle Cloud Infrastructure is NOT true?

    - Compartments are global resources.
    - IAM policies can be written to grant access to resources in specific compartments.
    - Compartments provide a way to store and manage encryption keys and secrets.
    - Compartments can be nested to create a hierarchy.

    > **Answer: Compartments provide a way to store and manage encryption keys and secrets.** This statement is NOT true. In Oracle Cloud Infrastructure (OCI), compartments are logical, structural containers used to organize and isolate cloud resources (such as instances, virtual cloud networks, and block volumes) for the purposes of access control and usage tracking. They do not function as a storage mechanism for sensitive data. Storing and managing encryption keys and secrets is explicitly the job of the OCI Vault service, not compartments.

---

25. In the Oracle Cloud Infrastructure shared security responsibility model, who is responsible for securing the customer's data, applications, and access control?

    - Oracle
    - Third-party vendors
    - Government agencies
    - The customer

    > **Answer: The customer.** In the Oracle Cloud Infrastructure (OCI) shared security responsibility model, security is divided between Oracle and the customer. This dynamic is commonly described as Oracle being responsible for the security of the cloud, and the customer being responsible for security in the cloud.

---

26. In Oracle Cloud Infrastructure, what is the main difference between a Load Balancer and a Network Load Balancer?

    - A Load Balancer works at the transport layer (layer 4), whereas a Network Load Balancer works at the application layer (layer 7).
    - A Load Balancer works at the application layer (layer 7), whereas a Network Load Balancer works at the transport layer (layer 4).
    - A Load Balancer supports only IPv4 addresses, whereas a Network Load Balancer supports both IPv4 and IPv6 addresses.
    - A Load Balancer is used for private networks, whereas a Network Load Balancer is used for public networks.

    > **Answer: A Load Balancer works at the application layer (layer 7), whereas a Network Load Balancer works at the transport layer (layer 4).** In Oracle Cloud Infrastructure (OCI), the Load Balancer service operates primarily at the application layer (Layer 7 of the OSI model). It is a reverse-proxy solution designed to inspect HTTP/HTTPS traffic, offering advanced routing based on content, SSL offloading, and integration with the Web Application Firewall.

---

27. How are compartment quotas applied in Oracle Cloud Infrastructure?

    - On a per-compartment basis
    - Globally, across all compartments
    - On a per-region basis
    - On a per-tenancy basis

    > **Answer: On a per-tenancy basis.** In Oracle Cloud Infrastructure (OCI), while quotas are applied to specific compartments to limit their resources, the quota policies themselves are actually defined and managed on a per-tenancy basis.

---

28. Which protocol is used by the Oracle Cloud Infrastructure File Storage service for file access?

    - iSCSI (Internet Small Computer Systems Interface)
    - NFS (Network File System)
    - FTP (File Transfer Protocol)
    - SMB (Server Message Block)

    > **Answer: NFS (Network File System).** The Oracle Cloud Infrastructure (OCI) File Storage service is a network-attached storage solution that primarily uses the NFS (Network File System) protocol—specifically NFS version 3.0, with support for newer versions like NFSv4.0 and NFSv4.1—for file access and sharing.

---

29. Which is a key difference between Security Lists and Network Security Groups in Oracle Cloud Infrastructure?

    - Security Lists encrypt data in transit, whereas Network Security Groups do not.
    - Security Lists are stateful, whereas Network Security Groups are stateless.
    - Security Lists support only ingress rules, whereas Network Security Groups support both ingress and egress rules.
    - Security Lists apply to subnets, whereas Network Security Groups apply to individual instance VNICs.

    > **Answer: Security Lists apply to subnets, whereas Network Security Groups apply to individual instance VNICs.** In Oracle Cloud Infrastructure (OCI), both Security Lists and Network Security Groups act as virtual firewalls to control traffic.

---

30. What is the function of a Dynamic Group in OCI IAM?

    - A group that stores audit logs for IAM security events
    - A group that allows policies to be assigned to compute instances and other OCI resources, instead of users
    - A group of users that automatically receives administrator privileges
    - A group that enforces two-factor authentication for high-security environments

    > **Answer: A group that allows policies to be assigned to compute instances and other OCI resources, instead of users.** In Oracle Cloud Infrastructure Identity and Access Management (OCI IAM), standard groups are used to organize human users. However, Dynamic Groups are used to logically group OCI resources—such as compute instances, functions, or API gateways—so that they can be treated as "principal" actors.

---

31. In OCI Networking, what is the role of a Dynamic Routing Gateway (DRG)?

    - To provide a path for traffic between a VCN and an on-premises network or another VCN
    - To provide a path for traffic between a VCN and the public internet
    - To enforce security rules on a group of cloud resources
    - To distribute incoming traffic to backend resources

    > **Answer: To provide a path for traffic between a VCN and an on-premises network or another VCN.** In Oracle Cloud Infrastructure (OCI) Networking, a Dynamic Routing Gateway (DRG) functions as a virtual router that provides a secure path for private traffic between your Virtual Cloud Network (VCN) and networks located outside of the VCN's region. This includes routing traffic to your on-premises data centers (via IPSec VPN or FastConnect) or to other peered VCNs in different regions.

---

32. In the Oracle Cloud Infrastructure Compute service, which feature enables users to migrate running instances between different physical servers?

    - Live Migration
    - Instance Evacuation
    - Instance Migration
    - Fault Domain Balancing

    > **Answer: Live Migration.** In the Oracle Cloud Infrastructure (OCI) Compute service, Live Migration is the feature that allows you to move a running virtual machine (VM) instance from one physical host server to another without interrupting its operation or causing any downtime. This is typically handled seamlessly by Oracle to maintain application availability during planned infrastructure maintenance, patching, or hardware optimization.

---

33. What type of storage is associated with instances in the Oracle Cloud Infrastructure Compute service?

    - Infrequent Access Storage
    - Object Storage
    - Block Storage
    - Archive Storage

    > **Answer: Block Storage.** In the Oracle Cloud Infrastructure (OCI) Compute service, Block Storage (specifically Block Volumes) is the primary type of persistent storage associated directly with compute instances. It behaves like a regular physical hard drive attached to a server. When you create an instance, it uses a block volume as its boot disk (containing the operating system), and you can attach additional block volumes for data storage.

---

34. Which attribute can be customized when creating an Oracle Cloud Infrastructure Compute flexible shape instance?

    - Operating system and disk type
    - Number of physical NICs and number of virtual NICs
    - Number of OCPUs and amount of memory
    - Instance shape and instance size

    > **Respuesta:**

---

35. Which type of scaling is achieved by adding or removing instances within an instance pool in Oracle Cloud Infrastructure Compute?

    - Diagonal scaling
    - Horizontal scaling
    - Proportional scaling
    - Vertical scaling

    > **Answer: Horizontal scaling.** In Oracle Cloud Infrastructure (OCI) Compute, horizontal scaling (also known as "scaling out" or "scaling in") is achieved by adding or removing compute instances within an instance pool to match demand. This is typically managed automatically using the Autoscaling feature.

---

36. Which is a key function of a Route Table in a VCN?

    - To provide encryption services for data at rest in the VCN
    - To store user credentials for access to OCI services
    - To direct network traffic to the correct destination
    - To define firewall rules that determine allowed network traffic

    > **Answer: To direct network traffic to the correct destination.** In an Oracle Cloud Infrastructure (OCI) Virtual Cloud Network (VCN), the key function of a Route Table is to define rules that route traffic from subnets to destinations outside of the VCN. Each rule specifies a destination CIDR block and a target gateway (such as an Internet Gateway, NAT Gateway, or Dynamic Routing Gateway) to act as the next hop for directing that network traffic.

---

38. What is the primary function of the Auto-Tiering feature in the Oracle Cloud Infrastructure Object Storage service?

    - Reducing storage costs by automatically moving objects between Standard and Archive tiers
    - Reducing storage costs by automatically moving objects between Standard and Infrequent Access tiers
    - Providing real-time usage analytics for all objects in the bucket
    - Eliminating storage fees for all objects

    > **Answer: Reducing storage costs by automatically moving objects between Standard and Infrequent Access tiers.** In the Oracle Cloud Infrastructure (OCI) Object Storage service, the Auto-Tiering feature continuously monitors the access patterns of your data. Its primary function is to optimize and reduce storage costs by automatically moving objects that have not been accessed for 31 days out of the performant Standard tier and into the more cost-effective Infrequent Access tier. If those objects are later accessed more frequently, Auto-Tiering automatically moves them back to the Standard tier without incurring any retrieval or prorated storage fees.

---

39. What is the term used to describe the combination of an instance's shape, base image, and metadata in the Oracle Cloud Infrastructure Compute service?

    - Instance Specification
    - Instance Profile
    - Instance Configuration
    - Instance Template

    > **Answer: Instance Configuration.** In the Oracle Cloud Infrastructure (OCI) Compute service, an Instance Configuration is a template that defines the settings to use when creating compute instances. It captures and saves the exact combination of an instance's shape (CPU and memory), base operating system image, networking, storage, and metadata so that you can easily replicate the exact same setup when launching new instances (particularly when using Autoscaling or Instance Pools).

---

40. What does "Auto-Tiering" mean in OCI Object Storage?

    - It disables file versioning when objects go unused.
    - It merges multiple buckets into a single bucket automatically.
    - It automatically renames all objects in a bucket every 30 days.
    - It moves data to lower-cost tiers based on access patterns.

    > **Answer: It moves data to lower-cost tiers based on access patterns.** In Oracle Cloud Infrastructure (OCI) Object Storage, Auto-Tiering is a feature that automatically monitors the data access patterns of your objects. If objects in the Standard storage tier are not accessed for 31 consecutive days, Auto-Tiering automatically moves them to the lower-cost Infrequent Access tier to save you money. If those objects are accessed again, they are automatically moved back to the Standard tier.