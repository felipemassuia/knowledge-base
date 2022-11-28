# Docker
###### Docker is a tool created to provide a simpler way to configure and run applications and intire simulations of operational systems trought the concept of **container**.
###### A container is an instance of an image, wich is a descriptions of a configuration to run an application. Each container is a process inside the original system and it has some caracteristics to keep the integrity of it. The list below shows some of this concepts, known as "namespaces".
* PID Keep the isolation of the processess inside the container
* NET Keep the network isolation
* IPC Keep the isolation between process and shared memory
* MNT Keep the isolation of the file system
* UTS Keep the kernel isolation
---
### The problem
###### There is a long way trought the computing study to get to the container concept. At first, we used to run our applications directily inside a physical machine. But this kind of implementation has a big problem:
> How can I run 3 apps at the same time? (for example, a Java process running at 80 port and a Nginx at 80 too)
###### Our first attempt is to run in 2 machines, but it is very expensive and a lot of companies tried to find alternatives to this situation.
###### So, the **virtualization** born up.
