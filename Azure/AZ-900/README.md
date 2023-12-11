# Azure AZ-900
###### Azure AZ-900 is the initial certification about Microsoft cloud provider. This document is a resume of the learning paths used to present and train the student to the certification.

###### Link to schedule certification:
> https://learn.microsoft.com/pt-br/certifications/exams/az-900

###### Link to learning path:
> https://learn.microsoft.com/pt-br/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/

###### Link to simulate test certification:
> https://pts.measureup.com/web/PBS/LMS/index.php?l=1&k=7701664&tam=1675704&role=1&course=at_test202205110604131652249053

---
## Introduction to cloud computing
###### Microsoft Azure is a cloud computing platform, with a large set os services to help build solutions to computing problems.
###### Cloud computing is the delivery of computing services over the internet. The most common serivces are:
* compute power
* storage service

### The shared responsibility model
###### The shared responsibility model is a concept apllied on cloud platforms that shares the tasks about maintaining the hardware, the operation system, security, and even softawares in the cloud.
###### Some responsibilites are always with the cloud provider, such as the physical security, power, cooling and network connectivity. In the other hand, some are always with the consumer, as the data that will be persisted inside a storage service. And some of them depends of the service type.
###### The most commom cloud service types are:
* (Iaas) Infrastructure as a service
* (Paas) Platform as a service
* (SaaS) Software as a service
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-cloud-compute/media/shared-responsibility-b3829bfe.svg" width="700px" />
</div>

### Cloud models
* **Private cloud** is a kind of evolution of a corporative datacenter. It is used by a single company as consumer, and may be very expansive. It is hosted in a dedicated datacenter.  
* **Public cloud** is built, controlled and maintained by a cloud provider. Anyone that buy a resource can use a public cloud.
* **Hybrid cloud** is a cloud that uses a public and private cloud in a inter-connected environment.
* **Multi-cloud** is a scenario that the consumer uses different cloud services from different cloud providers.

###### **Azure Arc** is a set of technologies that helps manage your cloud environment.

### Consumption-based model
###### A cloud provider typically uses a pay as you go pricing model. It means that you only pay for the services that you use. It is like you are renting someone else datacenter to run you app or storage data. To sign up for a cloud service is an OpeX cost, and it has a set of benefits, as you can see bellow:
* No upfront costs.
* No need to purchase and manage costly infrastructure that users might not use to its fullest potential.
* The ability to pay for more resources when they're needed.
* The ability to stop paying for resources that are no longer needed.
---
## The benefits of using cloud services
### High availability
###### A quality that represents a software that can handle with some troubles to keep up running.
### Scalability
###### It is the ability to ajust resources to meet demand. When you have a rush traffic and your systems are overloaded, a scalable system can increase resources like memory or even intances to keep the system running well. On the other hand, when your resources are underused, you can decrease your capacity by removing resources as far as you pay for what you use.
* **Vertical scaling** is a way to scale by adding processing power to your system, like adding RAM or more CPUs.
* **Horizontal scaling** is another way that you can scale by adding more resources (instances) to meet demand.
### Reliability
###### It is the ability to recover from failures and keep running. It is a part of the Azure concept a reliable infrastructure. As a datacenter stop running by a catastrophic event, Azure can transmit yout app to another one  with no action by the app support team.
### Predictability
###### The ability to previously know how much a solution will cost, or the performance of a service in Azure.
### Security and governance
###### You can control the resources to keep in line with the governance of your company or laws of a country, and update those templates as log as they change. At the same time, Azure has some security patterns providded to protect your resources from malicious components or attacts from the internet.
---
## Cloud service types
### Infrastructure as a Service
##### It is a kind of cloud service that you "rend" the hardware and be responsible for keep the OS pacthes, the network configuration, and so on.
##### It is a common scenario when you want to migrate your datacenter to the cloud, with no modification. It is known as "lift and shift" migration.
### Platform as a Service
##### _"Platform as a service (PaaS) is a middle ground between renting space in a datacenter (infrastructure as a service) and paying for a complete and deployed solution (software as a service)."_
##### In this model, the cloud provider is responsible for maintaining the operational systems, middleware, development tools and etc. You don't need to worry about OS and databases.
### Software as a Service
##### It is the most complete solution of a cloud service. You rent a fully developed application. You are responsible for the data that you put into the system and the devices that can connect to it.
---
## Azure Architecture and services / The core architectural components of Azure
###### The second learning path of Azure Fundamentals.
### Azure Accounts
##### Azure has an order to manage the resources in the cloud. First, you will need an Azure account, that can provide multiple subscriptions. A subscription is a way to join resources ou resources groups.
* Azure account
* Azure subscription
* Resource group
* Resources
##### Using Azure you can enjoy multiple free services and earn credits to start using produts. At the free account, you have access to some services for 12 months, a credit to use at other services and other services that are always free.
### Physical Infrastructure
* **Region** A physical area where a datacenter (or multiple datacentres) is.
* **Availability zone** Isolated datacenters within an Azure Region. They are connected through a dedicated network.
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/availability-zones-c22f95a3.png" width="700px" />
</div>

* **Region pair** A way to increase the resilience to an Azure Region. In a region pair, a region provides a backup to other one.
* **Sovereign Region** Special regions that serves legal propouse. They are isolated from Azure regions.
### Management infrastructure
* **Resource** The basic building block of Azure. Anything you create is a resource.
* **Resource Group** It is a group of resources. When you create a resource, you need to put it into a resource group. Resources groups can't be nested,and every resource can be only into a resource group.
* **Azure Subscription** It is a way to facilitate the logical organization of resources groups and manage billing. It is mandatory to use a subscription to create a resource in Azure. An Azure account can hava multiple subscriptions.
- Billing boundary is a subscription type that determines how an Azure account is billed for using Azure.
- Access controll boundary is a subscription type that applies access polices at the subscription level.
* **Management Groups** A organization scope above subscription level. It is a way to gather subscriptions that are related together.
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-core-architectural-components-of-azure/media/management-groups-subscriptions-dfd5a108.png" width="700px" />
</div>

---
## Azure compute and networking services
### Azure Virtual Machines
###### Azure VM is a compute service that enables you to create and use virtual machines in the cloud. It is an Infrastructure as a Service product. You can choose VMs when you need total control of the operation system. Using VMS gives you the flexibility of virtualization without having to buy and maintain the physical hardware. You can choose an image when creating a VM. An image is a template used to create a VM.
### Scale VMs in Azure
#### Virtual Machines scale sets
###### It is a tool to manage the scale of a group of VMs. The number of VMs can automatically increase or decrease in response to demand. It is possible to deploy a load balancer to make sure that your resources are beeing used efficiently.
#### Virtual Machines availability sets
* Update domain group defines VMs that can be updated at the same time
* Fault domain group defines a way to protect you against physical power or network failure.
### Azure Virtual Desktop
###### Azure Virtual desktop is a kind of service that enables you to manage and make available complete solutions of a desktop in the cloud. You can use Windows and specific services in it through any device, with security by separating data that is in the cloud from the local device. You can provide machines for personal use to complete teams, and manage access using Azure AD and RBAC.
### Azure Containers
###### Azure Conteiner is a PaaS solution that enables you to run applications with a container technology.
### Azure Functions
###### Azure functions is a servless solution to run a simple and fast task. When you don't want to manage your OS or any other infrastructure topic, your can develop the function code and run it in Azure. Functions scales automatically and can be trigged by a lot of other services, or HTTP request.
### Application Hosting Options
#### App Services
* Web apps
* API apps
* WebJobs
* Mobile apps
### Azure Virtual Network
###### Configuring Azure virtual networks and subnets gives you the capacity of controll the connection between your resources on Azure, such as the connection with your on premisses datacenter and filter and route network traffic.
* Isolation and segmentation
* Internet communications
* Communicate between Azure resources
* Communicate with on-premises resources
* Route network traffic
* Filter network traffic
* Connect virtual networks
### Azure Virtual Private Network
###### A VPN is a more security way to keep traffic through the internet. It uses a encrypted form to send sensive data from a network to another one.
### Azure ExpressRoute
###### You can use ExpressRoute when you don't want to put your data over the internet to traffic between your on premisses datacenter and the Azure infrastructure. Using Azure ExpressRoute you create a direct connection to Azure to use a high speed connection, secure and more stable communication to Azure services.
#### Benefits
* Connectivity to Microsoft cloud services across all regions in the geopolitical region.
* Global connectivity to Microsoft services across all regions with the ExpressRoute Global Reach.
* Dynamic routing between your network and Microsoft via Border Gateway Protocol (BGP).
* Built-in redundancy in every peering location for higher reliability.
### Azure DNS
###### You can use Azure DNS as a hosting service to resolve domain names by using Azure infrastructure.
---
## Azure Storage Services
### Storage Accounts
###### A storage account provides a unique namespace for your storage data. There is a lot of storage account types that determines the redundancy level to your data, such as specific tools to match your needs.
## Azure Storage Services
### Azure Sotrage Redundancy
#### Redundancy in the primary region
##### Locally redundant storage
###### LRS replicates your data three times within a single datacenter in the primary region. It is the lowest cost redundancy option. This option protects you from drive failures, but not from a datacenter disaster.
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-storage-services/media/locally-redundant-storage-37247957.png" width="700px" />
</div>

##### Zone-redundant storage
###### ZRS replicates your data within three datacenters separately. This mode protects you from datacenters disasters, and it has instantly re-routing of a data center becomes inaccessible.
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-storage-services/media/zone-redundant-storage-6dd46d22.png" width="700px" />
</div>

#### Redundancy in a secondary region
##### Geo-redundant storage
###### GRS replicates data three times in a single datacenter like LRS and replicates asynchronously to the secondary one.
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-storage-services/media/geo-redundant-storage-3432d558.png" width="700px" />
</div>

##### Geo-zone-redundant storage
###### GZRS replicates data three times like ZRS in the primary region, and then replicates asynchronously to the secondary one like LRS.
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-storage-services/media/geo-zone-redundant-storage-138ab5af.png" width="700px" />
</div>

##### Read access to data in the secondary region
###### You need to enable access to data when using GRS or GZRS. Data may not be updated during the RPO.
### Azure Storage Services
* Azure Blob Storage
* Azure Files
* Azure Queues
* Azure Disks
#### Benefits of Azure Storage
* Durable and highly available
* Secure
* Scalable
* Managed
* Accessible
#### Blob Storage
###### It is an object storage solution for the cloud. You can store a massive amount of data, such as text, images and binary data. It is unstructured data solution, that means there is no restriction for the data type you store in a blob. You can access blobs from HTTP or HTTPS protocol, and use libraries of a set of languages. There are different types of access tiers, such as hot access, cold access and archive.
#### Azure Files
###### It is a service that offers a fully managed file shares through the cloud.
#### Queue Storage
###### It is a service to put and consume a large amount of messages asynchronously.
#### Disk Storage
###### Storage service to be used for VMs on Azure.
### Azure Migration Options
#### Azure Migrate
###### It is a service that helps to migrate from an on-premises datacenter to the cloud.
#### Azure Data Box
###### It is a physical migration service to be used to transfer data from on-premises to the cloud.
### AzCopy
###### It is a command line tool to copy and manage blob or files in your data storage account.
### Azure File Sync
###### You can sync your data in a Windows Server with the cloud.
---
## Azure Identity, access and security
### Azure directory services
###### Microsoft Entra ID is the a directory service that allows you to sign in and access cloud aaplications that you develop and it helps you to maintain your on premisses AD deployment.
#### What Microsoft Entra ID does
* Authentication
* Single sign on
* Application management
* Device registration
###### You can connect your AD with Microsoft Entra ID using Microsoft Entra Connect. It allows you to synchronizes changes between both identity systems.

### Azure authentication methods
###### Azure has a set of authentication capabilities, such as passwords, multifactor, passwordless and SSO.
##### Password
###### Classic form to authenticate to a system. It is convenient, however it has low security.
##### Multifactor
###### It is not convenient, because you need to provide a password and another code as a second factor. Even so, it has a high level of security.
##### Passwordless
###### It is a convenient and high secure way to authenticate. The users can use something they have, such as a fingerprint or a code used in their authentication app.
##### SSO
###### Single sign on is a tool used to guarantee the authentication made in one system, and is trusted in subsystems.

### Azure external identities
###### Azure can interact to users and componentes outside Azure using Microsoft Entra External ID. It is possible to bring to Azure the entities from another systems.
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/azure-active-directory-external-identities-5a892021.png" width="700px" />
</div>

### Azure conditional access
###### Azure conditional access is a tool in Azure that helps IT administrators protect assets using signals from the users (where they are, when they are trying to access a resource). The signals change the behavior of the sign in attempt, for example.

### Azure Role-Based Access Control
###### RBAC is a model to keep access to resources using the principle of least privilege, where users only have authority to use/read/administrate resources if they really need to do it. With RBAC, users can assume roles that have a set of rules to keep their access.

### Zero trust model
###### The Zero Trust model is a security model that assumes that a breach can happen in the internal network, so the internal resources need to be protected. In the Zero trust model, you keep all the resources protected.
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/zero-trust-cf9202be.png" width="700px" />
</div>

### Defense in depth
###### Defense in depth is a strategy to protect your environment based in creating protection layers in different levels.
<div align="center">
<img src="https://learn.microsoft.com/en-us/training/wwl-azure/describe-azure-identity-access-security/media/defense-depth-486afc12.png" width="700px" />
</div>

### Microsoft Defender for Cloud
###### Microsoft defender is a service that is natively integrated with resources in Azure and helps IT administrators to monitor and act to keep the environment secure. Microsoft Defender has native protection in:
* SAAS
* Azure Data Services
* Networks
###### Microsoft Defender can also provide alerts and take actions automatically.

---
## Cost Management in Azure
### Factors that can affect cost
###### Azure shifts development cost from the capital expense (CapEx) to operational expense (OpEx). The factors that impact this cost are:
* Resource type
* Consumption
* Maintenance
* Geography
* Subscription type
* Azure Marketplace
