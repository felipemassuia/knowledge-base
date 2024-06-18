# Kubernetes
###### Kubernetes is a container orchestrator that solves problems of vertical and horizontal scalability. It creates and manages a cluster of machines, distributing computational power among them. Kubernetes is capable of running containers on different machines within the cluster, replacing failed containers, and adding new machines to the cluster when necessary. It also allows for automatic restart of applications in case of failures. Kubernetes is a container orchestrator that solves scalability problems and offers various functionalities to facilitate application management.

###### Kubernetes goes beyond being just a container orchestrator, having various ready-to-use resources to solve different types of problems, such as pods, ReplicaSets, Deployments, and Volumes.

* Pods encapsulate the containers and are the basic unit of execution in Kubernetes.
* Persistent Volume is a Kubernetes resource to handle data persistence.
* Kubernetes manages a cluster with machines called master and nodes. The master is responsible for coordinating and managing the cluster, while the nodes run the applications.
* The main components of the Control Plane are the API, Controller Manager, Scheduler, and ETCD. On the nodes, we have Kubelet and KubeProxy.
* The API is responsible for maintaining communication between Kubernetes components.
* Kubectl is the tool used to communicate with the API and manage cluster resources.

###### The Kubernetes manages a cluster, which consists of master nodes (responsible for coordinating the cluster) and worker nodes (responsible for running applications). Within the master node, we have components such as the API, Controller Manager, Scheduler, and ETCD, each responsible for different functions. On the worker nodes, we have Kubelet (responsible for executing pods) and KubeProxy (responsible for communication between nodes). The API is the central point of communication, receiving commands from the outside world and interacting with other components. To communicate with the API, we use the kubectl tool, which allows us to create, read, update, and delete cluster resources in a declarative or imperative manner.
---
### Pods
###### Pods are the basic unit of execution in Kubernetes, not individual containers like with Docker. A pod can contain one or more containers that share the same IP address and network namespace. This allows containers within the same pod to communicate easily via localhost. When a container within a pod fails, the entire pod is terminated and Kubernetes creates a new pod to replace it. Pods are ephemeral, meaning they can be created and destroyed at any moment by Kubernetes. The main advantage of pods is that they enable simplified communication between containers that are part of the same pod.

#### Usefull commands
> k run nginx-pod --image=nginx:latest
> k get pods --watch
> k describe pod nginx-pod

