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