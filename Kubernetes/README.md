# Kubernetes
###### Kubernetes is a container orchestrator that solves problems of vertical and horizontal scalability. It creates and manages a cluster of machines, distributing computational power among them. Kubernetes is capable of running containers on different machines within the cluster, replacing failed containers, and adding new machines to the cluster when necessary. It also allows for automatic restart of applications in case of failures. Kubernetes is a container orchestrator that solves scalability problems and offers various functionalities to facilitate application management.

###### Kubernetes goes beyond being just a container orchestrator, having various ready-to-use resources to solve different types of problems, such as pods, ReplicaSets, Deployments, and Volumes.

* Pods encapsulate the containers and are the basic unit of execution in Kubernetes.
* Persistent Volume is a Kubernetes resource to handle data persistence.
* Kubernetes manages a cluster with machines called master and nodes. The master is responsible for coordinating and managing the cluster, while the nodes run the applications.
* The main components of the Control Plane are the API, Controller Manager, Scheduler, and ETCD. On the nodes, we have Kubelet and KubeProxy.
* The API is responsible for maintaining communication between Kubernetes components.
* Kubectl is the tool used to communicate with the API and manage cluster resources.

